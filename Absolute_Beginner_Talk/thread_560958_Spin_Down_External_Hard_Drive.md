---
title: "Spin Down External Hard Drive"
date: 2007-09-27
forum: Absolute Beginner Talk
---

### Post by themacmonk on 2007-09-27
I'm trying to figure out how to spin down my external Lacie hard drive.  I remember seeing a terminal command for it but have been unsuccessful at finding it. 

I put my MacBook to sleep an noticed that the external drive was still spinning the next morning.  Also, when I try to eject it won't let me do so.

Thanks!

---

### Post by HermanAB on 2007-09-27
First figure out what the drive device is:
$ sudo mount

Then set the sleep time (it is not seconds, see 'man hdparm'):
$ sudo hdparm -S 5 /dev/whatever

Cheers,

Herman

---

### Post by themacmonk on 2007-09-27
I tracked down the drive device and followed your instructions but it didn't work.  Here's what I get

[I]/dev/sdb6 on /media/disk-1 type hfsplus (rw,noexec,nosuid,nodev)
~$ sudo hdparm -S 150 /dev/sdb6

/dev/sdb6:
 setting standby to 150 (12 minutes + 30 seconds)
 HDIO_DRIVE_CMD(setidle1) failed: Invalid argument[/I]

Any thoughts?  Thanks!

---

### Post by justinw28 on 2007-11-14
I've been having the same problem.

Any help appreciated.

Thanks

---

### Post by noahsark1126 on 2007-12-11
I'm having the exact same issue.  I can use hdparm on any partition in my internal hard drive, but it doesn't recognize the external at all.

Any ideas?

---

### Post by Biggy on 2007-12-18
i'm having the same problem...

any help plzz ....???

---

### Post by Biggy on 2007-12-18
nobady help me !!!!!

---

### Post by Biggy on 2007-12-18
!

---

### Post by anubhavrocks on 2007-12-18
> **themacmonk said:**
> I tracked down the drive device and followed your instructions but it didn't work.  Here's what I get

[I]/dev/sdb6 on /media/disk-1 type hfsplus (rw,noexec,nosuid,nodev)
~$ sudo hdparm -S 150 /dev/sdb6

/dev/sdb6:
 setting standby to 150 (12 minutes + 30 seconds)
 HDIO_DRIVE_CMD(setidle1) failed: Invalid argument[/I]

Any thoughts?  Thanks!

Post the output of 
```
sudo hdparm -Ii /dev/sdb6
```

---

### Post by Biggy on 2007-12-18
> **anubhavrocks said:**
> Post the output of 
```
sudo hdparm -Ii /dev/sdb6
```

/dev/sdb:
 HDIO_GET_IDENTITY failed: Invalid argument
 HDIO_DRIVE_CMD(identify) failed: Invalid argument

what i have to do ??? 

help

---

### Post by Biggy on 2007-12-18
?

---

### Post by anubhavrocks on 2007-12-18
Check if your external drive is /dev/sdb?You can check that by connecting it to your machine and issuing the mount command

---

### Post by Biggy on 2007-12-18
> **anubhavrocks said:**
> Check if your external drive is /dev/sdb?You can check that by connecting it to your machine and issuing the mount command

ok i reconnect my drive in machine (mount) command ,and i see /dev/sda1

i try again this command : sudo hdparm -Ii /dev/sda1 and this :  sudo hdparm -S 5 /dev/sda1

but the same error :

/dev/sda1:
 setting standby to 5 (25 seconds)
 HDIO_DRIVE_CMD(setidle1) failed: Invalid argument
------------------------------------------------------------------------
any idea ...!!?

---

### Post by anubhavrocks on 2007-12-18
Please post the output of 
```
sudo hdparm -Ii /dev/sda1
```

---

### Post by Biggy on 2007-12-19
> **anubhavrocks said:**
> Please post the output of 
```
sudo hdparm -Ii /dev/sda1
```

/dev/sda1:
 HDIO_GET_IDENTITY failed: Invalid argument
 HDIO_DRIVE_CMD(identify) failed: Invalid argument

---

### Post by Biggy on 2007-12-20
help...

---

### Post by anubhavrocks on 2007-12-21
After you attach your drive,give the following commands and post their complete outputs
1.mount  
2.dmesg
3.lsusb

---

### Post by Biggy on 2007-12-21
ok after atach my drive and give the follow commands,result here :

biggy@Biggy-UAC:~$ lsusb
Bus 005 Device 007: ID 059f:1010 LaCie, Ltd 
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 002 Device 003: ID 1110:9041 Analog Devices Canada, Ltd (Allied Telesyn) 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 004: ID 1310:0001 Roper Class 1 Bluetooth Dongle
Bus 001 Device 005: ID 045e:0084 Microsoft Corp. 
Bus 001 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000 [/CODE]

---

### Post by Biggy on 2007-12-21
.....!!!

---

### Post by anubhavrocks on 2007-12-21
External USB drives generally have an ability to spin down themselves after a period of inactivity.You should unmount the drive and check if your drive spins down after some time.In case your drive DOES NOT  spin down,you can use sg3-utils to spin down the drive manually,

sudo apt-get install sg3-utils
Once you install this package check for
sg_start
Consult the manpage for sg_start for more details.

---

### Post by cprise on 2008-01-12
I wrote this script to automatically handle standby / spindown of any external drives connected to the system...

```
#!/bin/bash

declare -a DID
declare -a DSTATUS
declare -a DTIME
declare -a DOFF


interval=$1
sleepval=120
buspath=/sys/bus/scsi/devices

while [ true ]; do
thetime=`date +%s`

for scsidev in $( ls --format=across $buspath ); do
   if devenum="$( ls ${buspath}/${scsidev} | grep 'block:' )"; then
      devdir=$buspath/$scsidev/$devenum
      read devsize < ${devdir}/size
      read devremove < ${devdir}/removable

      if [ $devremove -eq 0 ] && [ $devsize -gt 0 ]; then # device is the right type
         read newstat < ${devdir}/stat
         hhit=0; listlen=${#DID[@]}  #; echo $listlen $scsidev

         for ((i=0;i<$listlen;i++)); do
            if [ ${DID[$i]} = $scsidev ]; then
               if [ "${DSTATUS[$i]}" = "$newstat" ]; then
                  if [ $[ ${thetime} - ${DTIME[$i]} ] -ge $interval ] \
                  && [ ${DOFF[$i]} -eq 0 ]; then
                     sg_start --pc=5 /dev/${devenum:6} # put into sleep mode
                   # sg_start --stop /dev/${devenum:6} # alternate method
                     echo stop /dev/${devenum:6}
                     DTIME[$i]=$thetime
                     DOFF[$i]=1
                  fi
               else
                  DSTATUS[$i]=$newstat
                  DTIME[$i]=$thetime
                  DOFF[$i]=0
               fi
               hhit=1; break
            fi
         done
         if [ $hhit -eq 0 ]; then   # add new drive to watch list
            DID[$listlen]=$scsidev
            DSTATUS[$listlen]=$newstat
            DTIME[$listlen]=`date +%s`
            DOFF[$listlen]=0
         fi
      fi
   fi
done
sleep $sleepval
done
```

Save it with a name like 'scsi-idle, set the execute bit, then you run it like this:
```
$ sudo ./scsi-idle 1500
```
The above would cause external drives to spin-down after 25-27 min of inactivity. Even though 25 min (1500 sec) is specified, the internal delay loop can add a couple minutes to the reaction time.

The sg3-utils package is required for this script.

Enjoy!

---

### Post by dcstar on 2008-01-12
> **Biggy said:**
> /dev/sda1:
 HDIO_GET_IDENTITY failed: Invalid argument
 HDIO_DRIVE_CMD(identify) failed: Invalid argument

Those hdparm commands do not work on drives accessed via the SCSI sub-system (all "sd" drives).

This is also an issue with some kernel builds that start using the internal IDE drives as "sd" drives (instead of "hd", which can be a real pain.......)

---

### Post by Biggy on 2008-01-12
sudo: ./scsi-idle: command not found

---

### Post by cprise on 2008-01-12
> **Biggy said:**
> sudo: ./scsi-idle: command not found

You have to set the execute bit on the scsi-idle file before you can execute it. You can do this by changing permissions from the GUI, or from the CLI with '$ chmod +x scsi-idle'

---

### Post by dcstar on 2008-01-12
> **cprise said:**
> You have to set the execute bit on the scsi-idle file before you can execute it. You can do this by changing permissions from the GUI, or from the CLI with '$ chmod +x scsi-idle'

And you can add this script to your /etc/rc.local file so it loads automatically at boot up, I have these lines in mine:
```

# Spin down any external SCSI drives after "X" seconds:
/home/dc/local-run/scsi-idle 900 &
```

---

### Post by cprise on 2008-01-12
I have created a [Help page]("https://help.ubuntu.com/community/ExternalDriveStandby") for it. Some further elaboration (which I'm not good at) would be nice... :)

---

### Post by Biggy on 2008-01-17
> **cprise said:**
> I have created a [Help page]("https://help.ubuntu.com/community/ExternalDriveStandby") for it. Some further elaboration (which I'm not good at) would be nice... :)

thank you cprise

---

### Post by Svamberg on 2008-04-04
Hi,
I am beginneng user for Ubuntu 7.10.
Help me please with install for your "Spin Down External HDD script" with in several basic steps.
Thank you,
Lubos

---

### Post by abhiroopb on 2008-05-11
I use sbackup, and backup all of my data to an external hard drive. As such I need to keep it mounted. Is there anyway to spin down a mounted external hard drive connected by usb?

---

### Post by cprise on 2008-05-13
Yes, the above script (or the sg_start command contained within it) can spin down your USB drive if your drive's USB adapter handles the necessary commands. I have one external USB case that responds to none of the spindown commands.

FWIW the --stop command does seem slightly more universal then the --pc=5 command, so you may want to adjust the script by commenting the line with the --pc=5 command and un-commenting the line with --stop.

Since I posted the script, I've also verified that it works with not only Firewire and USB, but also with SCSI, SATA and eSATA as well.

---

### Post by peterroots on 2008-05-13
If found this in a magazine article, which may help - it works for me
you need to install pmount and hdparm first

create a text file eg ejecthd.sh in your home folder or somewhere similar

add the following

#!/bin/bash
exec 2>&1
pumount $1 || umount $1
sdparm --command=sync $1
sdparm --command=stop $1

set the file to executable by typing
    sudo chmod +x ejecthd.sh

check what you drive is by pointing the mouse at it's icon on the desktop or right click it and select properties

type the following
   ./ejecthd.sh /dev/sdb1
obviously use the device name of your hard drive.  this should unmount your drive and spin it down.  This was in Linux format (I think) and I have removed a bit that suppressed error messages

---

### Post by mawe3661 on 2008-06-02
I tried the script on ubuntu server 8.04 and it does spin down the drive, but it won't spin up again when I access it. Even worse, dev/sdb and dev/sdc have been removed. That was the devices the disks were associated with before. So I cannot even manualy remount them... Any tips? Whats the difference between sdparm and sg_start?

---

### Post by peterroots on 2008-06-05
on kubuntu 7.10 and ubuntu 8.04 desktop editions this works but having ejected the disc I don't try to re access it (the point being I want to remove it from the usb port). On plugging it back into the usb port the drive is detected and spins up as expected.
I have not need, and can't see the point in spinning down the drive and leaving it plugged in (but happy to accept you may want to do this).
I have no idea of the difference between spdarm and sg_start - sorry I have not tried the latter as the former solved my problem and did the same on my wifes Edubuntu desktop so have not investigated further.

---

