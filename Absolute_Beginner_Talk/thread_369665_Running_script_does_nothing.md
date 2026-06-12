---
title: "Running script does nothing?"
date: 2007-02-24
forum: Absolute Beginner Talk
---

### Post by cknight on 2007-02-24
So I'm trying to run a script related to loading firmware onto my AccessRunner DSL modem.  When I execute the script using '$invoke-rc.d cnxadslctl start' nothing happens except that I'm back on the command line: '$'.  No errors or anything. Looking at the script below, shouldn't I at least get the 'Starting script' to appear on the console?  What am I missing here?

```
#!/bin/bash
# Modified by Patrick Mackinlay (SpaceSurfer Ltd.)
# patrick@spacesurfer.com
#
# chkconfig: 345 09 91
# description: This is the boot/shutdown script for the Conexant AccessRunner
# ADSL modem.

# Source function library.
#. /etc/init.d/functions

echo "Starting script"
# See how we were called.
case "$1" in
start)
# if the driver is not already loaded then
# Load the module

if [ ! -f /var/lock/subsys/cnxadslctl ]; then
echo " Starting AccessRunner "
modprobe pppoatm
modprobe CnxADSL \
CnxtDslVendorId=0x14F1 \
CnxtDslArmDeviceId=0x1610 \
CnxtDslAdslDeviceId=0x1611 \
CnxtDslPhysicalDriverType=1

# Initialize the firmware and start training
# echo "Download Starting."
/etc/Conexant/cnxadslload /etc/Conexant

RETVAL=$?
if [ $RETVAL -eq 0 ] ; then
touch /var/lock/cnxadslctl
/usr/sbin/pppd
fi
else
echo -n "AccessRunner already loaded"
fi
echo
;;

stop)

PPPUP=`ps aux | grep -v grep | grep pppd`
if [ -n "$PPPUP" ]; then
echo -n "Killing pppd: "
killall /usr/sbin/pppd
sleep 5
echo
fi

if [ -f /var/lock/cnxadslctl ]; then
echo -n "Stopping Conexant AccessRunner:"

if grep -q "\[pppoatm\]" /proc/ksyms; then
rmmod pppoatm
fi
killall -q cnxadslload
rmmod CnxADSL
rm -f /var/lock/subsys/cnxadslctl
fi
echo
;;
status)
cat /proc/net/atm/CnxAdsl:0 | more
;;
*)
echo "Usage: $0 {start|stop|status}"
exit 1
esac

exit 0
```

---

### Post by tgalati4 on 2007-02-24
Try sudo yourscript.

Since you are trying to install modules into the kernel via modprobe, that would require sudo priviledges at least.

---

### Post by cknight on 2007-02-25
Yep, tried sudo as well.  Same thing.  I wouldn't have thought it mattered though since the first executable script command (as far as I can tell) is echo?  This is doing my brain in!

---

### Post by joegiampaoli on 2007-02-25
Check if the script is executable, easiest way is RMB on the file, Properties>Permissions and click to activate Owner, Group and Users in "Executable" section. Also when you run the script try running it with a ./ before the script name, for example:

sudo ./script.sh

---

### Post by tgalati4 on 2007-02-25
sudo chmod +x yourscriptthatisgivingyouheadache.sh

---

### Post by cknight on 2007-02-25
lol, thanks y'all.  Indeed,  I was missing executable permission from the script name.  Damn windows background...

Still strikes me a curious that the terminal doesn't spit out something like 'Hey dummy, you're trying to execute something which you don't have execute permission on'.

---

### Post by tgalati4 on 2007-02-25
It's a security feature of Linux.

Any external script or newly-compiled program will require:
sudo chmod +x mynewcheesyprogram.sh

and to execute it:

./mynewcheesyprogram.sh

This requires root access and prevents a script from running in its own directory by forcing operation from the parent directory.  If a malicious script has root access then your system is already hosed.  So by default any script or new executable binary has execution turned off.  This is the Linux version of "Deny or Allow"

I'm glad we got it figured out.  I was worried that I was caught in the Ballmer Reality Distortion Field.

---

