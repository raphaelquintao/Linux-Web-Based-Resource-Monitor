#!/bin/sh
echo "Content-type: text/html"
echo ""
echo "<html><head><title>Monitor Module"
echo "</title></head><body>"
echo "<h1 id="hostname">$(hostname -s)</h1>"

echo "<h2>Distro</h2>"
echo "<pre id="distro_alt"> $(cat /proc/version) </pre>"
echo "<pre id="distro_id">$(lsb_release -a | grep 'Distributor ID')</pre>"
echo "<pre id="distro_desc">$(lsb_release -a | grep 'Description')</pre>"
echo "<pre id="distro_release">$(lsb_release -a | grep 'Release')</pre>"
echo "<pre id="distro_codename">$(lsb_release -a | grep 'Codename')</pre>"

echo "<h2>Uptime</h2>"
echo "<pre id="uptime"> $(uptime) </pre>"

echo ""
echo "<h2>Memory Info</h2>"
echo "<pre id="memory"> $(free -m) </pre>"

echo "<h2>Disk Info:</h2>"
echo "<pre id="disk"> $(df -Ph) </pre>"

echo "<h2>CPU Load</h2>"
echo "<pre id="cpu_load"> $(top -n 2 -b -d 0.3 | grep Cpu |tail -1) </pre>"

echo "<h2>Top Process</h2>"
echo "<pre id="top_process"> $(top -n 1 -b -d 0.3 ) </pre>"

echo "<h2>CPU Model</h2>"
echo "<pre id="cpu_model"> $(cat /proc/cpuinfo | grep 'model name' |tail -1) </pre>"

echo "<h2>CPU Cores</h2>"
echo "<pre id="cpu_cores"> $(cat /proc/cpuinfo | grep 'cpu cores' |tail -1) </pre>"


echo "<h2>Users</h2>"
echo "<pre id="users"> $(w) </pre>"
# echo "<pre id="users_alt"> $(cat /etc/security/limits.conf) </pre>"

echo "<h2>Temperature</h2>"
echo "<pre id="temp"> $(sensors) </pre>"

echo "<h2>IP</h2>"
echo "<pre id="temp"> $(/sbin/ifconfig) </pre>"


echo "<center id="date">$(date)</center>"
echo "</body></html>"




