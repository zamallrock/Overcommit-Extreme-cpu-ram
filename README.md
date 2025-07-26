# Overcommit-Extreme-cpu-ram

`Allow Memory Overcommit`
```
cat /proc/sys/vm/overcommit_memory
```
`If 0 add result = 1`
```
echo 1 > /proc/sys/vm/overcommit_memory
```
`add Permanent overcommit`
```
echo "vm.overcommit_memory=1" >> /etc/sysctl.conf
sysctl -p
```
`Strict mode if overcommit error`
```
echo 2 > /proc/sys/vm/overcommit_memory
echo 150 > /proc/sys/vm/overcommit_ratio
```
`Overswap Extreme Memory`
```
fallocate -l 32G /swapfile
chmod 600 /swapfile
mkswap /swapfile
swapon /swapfile
```
`Overcommit CPU, RAM, dan Swap test`
```
apt install cpulimit stress -y
```
`Run stress test`
```
stress --cpu 16 --io 6 --vm 6 --vm-bytes 4G --timeout 180
```
