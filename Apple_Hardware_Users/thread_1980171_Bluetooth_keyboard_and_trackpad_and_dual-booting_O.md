---
title: "Bluetooth keyboard and trackpad and dual-booting OS X"
date: 2012-05-14
forum: Apple Hardware Users
---

### Post by pbhedlund on 2012-05-14
Hi,

I am pretty frustrated with getting my Apple wireless keyboard and Magic Trackpad to reconnect on reboot if I have used it in OS X in between.

When I boot into OS X I simply tap on the devices and the system asks if I want to connect them. I answer yes and that's it.

In Ubuntu 12.04 I have to go into the Bluetooth settings and completely remove the devices from the list of know devices. Then completely turn them off and then start the discovery process. This may or may or may not work after one or more attempts. Frequently dialogs for entering PIN codes are shown below the main window. Frequently the device blinks for a second in the discovery dialog and then disappears. Often when I am able to click continue the only message I get is that setup failed.

What to do? Batteries are new enough and the setup never fails in OS X. The system is a MacBook Air 3,2.

Any tips greatly appreciated.

---

### Post by eivindsm on 2012-05-16
Sorry, not tips. This has been an issue since 11.10:
[http://ubuntuforums.org/showthread.php?t=1874245](http://ubuntuforums.org/showthread.php?t=1874245)

I still use my cheap plastic usb keyboard and mouse when I swap OS

---

### Post by nushoin on 2012-05-20
The Wiki has some info:

[https://wiki.ubuntu.com/Multitouch/AppleMagicTrackpad#Problem:_Pairing_does_not_persist_between_reboots_on_Maverick_.2810.10.29]("https://wiki.ubuntu.com/Multitouch/AppleMagicTrackpad#Problem:_Pairing_does_not_persist_between_reboots_on_Maverick_.2810.10.29")
[https://wiki.ubuntu.com/Multitouch/AppleMagicTrackpad#Known_issues]("https://wiki.ubuntu.com/Multitouch/AppleMagicTrackpad#Known_issues")

Also, see here:
[http://askubuntu.com/questions/68939/issues-with-bluetooth-connections-in-11-10]("http://askubuntu.com/questions/68939/issues-with-bluetooth-connections-in-11-10")

It is really a shame that these problems have existed for about two years already and have not been solved yet.

---

### Post by pbhedlund on 2012-05-20
Here is a new bug report [https://bugs.launchpad.net/ubuntu/+source/bluez/+bug/1001825](https://bugs.launchpad.net/ubuntu/+source/bluez/+bug/1001825).

---

### Post by ZeroFossilFuel on 2012-06-25
I too have a problem bluetooth mouse that's been busting my chops for some time now. It remains stored in the devices list and even remains paired. But many times to actually get it to work I have to give it a swift kick by re-enabling Input Services from the Blueman device list. Now I'm reading it's because I'm dual booting? I am not liking what I'm reading.

Asus EeePC 1018P, dual boot Win7 Home and Xubuntu 12.04.

---

### Post by pbhedlund on 2012-06-25
> **ZeroFossilFuel said:**
> Now I'm reading it's because I'm dual booting? I am not liking what I'm reading.

Quite possibly so. You could try the script posted in comment #8 of [https://bugs.launchpad.net/ubuntu/+source/bluez/+bug/1001825](https://bugs.launchpad.net/ubuntu/+source/bluez/+bug/1001825), but be sure to read the following comments also.

---

### Post by zerosly on 2013-01-24
Linux newbie here, but after ~6 hours of searching the internets I finally found a solution. 

1.  Pair device(s) to Linux

2.  Pair device(s) to Mac OS X

3.  Run the attached script in Linux

Note:  The script is assuming the OS X disk is mounted and its name is Macintosh HD. Change 10:9A:DD:7E:10:E2 to the MAC address of your Magic Mouse or Magic Trackpad. The script will work for the wireless keyboard and the Magic Mouse or Magic Trackpad. Any device not paired with OS X will be removed from linux.

After rebooting from linux the keyboard will not be paired during the boot process. If OS X is your default boot option just let it boot then reboot and you will be able to use startup keys.

---

### Post by mackgb on 2013-02-03
> **zerosly said:**
> Linux newbie here, but after ~6 hours of searching the internets I finally found a solution. 

1.  Pair device(s) to Linux

2.  Pair device(s) to Mac OS X

3.  Run the attached script in Linux

Note:  The script is assuming the OS X disk is mounted and its name is Macintosh HD. Change 10:9A:DD:7E:10:E2 to the MAC address of your Magic Mouse or Magic Trackpad. The script will work for the wireless keyboard and the Magic Mouse or Magic Trackpad. Any device not paired with OS X will be removed from linux.

After rebooting from linux the keyboard will not be paired during the boot process. If OS X is your default boot option just let it boot then reboot and you will be able to use startup keys.

I have tried to do it the way its explained above, however thats what i am receiving 

maciej@maciej-iMac:~$ #!/bin/sh
maciej@maciej-iMac:~$ cd /var/lib/bluetooth
maciej@maciej-iMac:/var/lib/bluetooth$ for i in *; do
>     cd "$i"
>     plutil -i /media/angel/Macintosh\ HD/private/var/root/Library/Preferences/blued.plist -o /dev/stdout |
>     perl -0777 -MMIME::Base64 -ne 's|\s||g; $s = $_; while ($s =~ m|<key>(..-..-..-..-..-..)</key><data>(.*?)</data>|g) { $mac = uc($1); $key = uc(unpack("H*",reverse decode_base64($2))); $mac =~ s/-/:/g; $pinlength = 6; $pinlength = 4 if $mac eq "7c:d1:c3:bd:e7:34"; print "$mac $key 0 $pinlength\n"; }' |
>     tee linkkeys
>     cd ..
> done
tee: linkkeys: Permission denied
maciej@maciej-iMac:/var/lib/bluetooth$ service bluetooth restart
stop: Rejected send message, 1 matched rules; type="method_call", sender=":1.88" (uid=1000 pid=4370 comm="stop bluetooth ") interface="com.ubuntu.Upstart0_6.Job" member="Stop" error name="(unset)" requested_reply="0" destination="com.ubuntu.Upstart" (uid=0 pid=1 comm="/sbin/init")
start: Rejected send message, 1 matched rules; type="method_call", sender=":1.89" (uid=1000 pid=4367 comm="start bluetooth ") interface="com.ubuntu.Upstart0_6.Job" member="Start" error name="(unset)" requested_reply="0" destination="com.ubuntu.Upstart" (uid=0 pid=1 comm="/sbin/init")
maciej@maciej-iMac:/var/lib/bluetooth$

---

### Post by Brian_Marple on 2013-10-08
Did this ever get resolved? Anybody have success with zerosly's instructions?

I'm just getting started with Ubuntu and would like to get this bluetooth issue taken care of.

Thanks

---

### Post by wilbertcr on 2014-01-16
Don't have an apple, so cannot test it, but the error you're getting is because of permissions. Just do sudo su before running the script and it should run, whether it works or not, I can't tell.

---

### Post by pierreyves.gueniff on 2014-05-14
> **Brian_Marple said:**
> Did this ever get resolved? Anybody have success with zerosly's instructions?

I'm just getting started with Ubuntu and would like to get this bluetooth issue taken care of.

Thanks
Yes it worked for my Magic Mouse with minor changes to the script. See more instructions on this page:
[https://bugs.launchpad.net/ubuntu/+source/bluez/+bug/1001825](https://bugs.launchpad.net/ubuntu/+source/bluez/+bug/1001825)

---

### Post by Ariel_Abreu on 2015-04-26
Umm, yeah, of course you must change the line ```
/media/angel/Macintosh\ HD
``` to ```
/media/<username>/Macintosh\ HD
``` (<username> being your username), and you must ```
sudo apt-get install libplist-utils
``` and ```
plutil -i (blah, blah)
``` becomes ```
plistutil -i (blah, blah)
```

---

