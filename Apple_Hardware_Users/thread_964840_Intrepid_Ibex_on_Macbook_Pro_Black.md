---
title: "Intrepid Ibex on Macbook Pro Black"
date: 2008-10-31
forum: Apple Hardware Users
---

### Post by Kooothor on 2008-10-31
\o/

I successfully upgraded to Ibex on my Macbook.
I just had to add "Windows List" to my gnome panel, and change the theme back.

But basically, that's it ! It works like a charm :)

ENJOY !

---

### Post by Kooothor on 2008-11-04
Small problem :

The applesmc module doesn't load at boot (and yes, it is in /etc/modules)
Coretemp is okay, but applesmc nope... :(

---

### Post by cyberdork33 on 2008-11-04
interesting. Do you get an error when you try to load it manually?

```
sudo modprobe applesmc
```

PS Please determine your MacBook Pro's version number and use it to identify what Mac you have in the future...

[https://wiki.ubuntu.com/MactelSupportTeam/CommunityHelpPages](https://wiki.ubuntu.com/MactelSupportTeam/CommunityHelpPages)

---

### Post by Kooothor on 2008-11-05
No, I get no problem loading it.

	Product Name: MacBook4,1
	Product Name: Mac-F22788A9

It's annoying cause each morning I have to reload it manually.... :(
And also edit the fan1_min speed wich by default is far too low.

dmesg show me that applesmc is successfully loaded at boot.
Then it is unloaded (whyyyyyyyyyyyyyyyyyy)

```
[   15.235830] applesmc: Apple MacBook detected:
[   15.235834] applesmc:  - Model with accelerometer
[   15.235835] applesmc:  - Model without light sensors and backlight
[   15.235836] applesmc:  - Model with 10 temperature sensors
[   15.292862] applesmc: device successfully initialized (0xe0, 0x00).
[   15.292866] applesmc: device successfully initialized.
[   15.293547] applesmc: 1 fans found.
[   15.296886] input: applesmc as /devices/platform/applesmc.768/input/input13
[   15.344173] applesmc: driver successfully loaded.
[   17.599980] applesmc: wait status failed: 5 != 0
[   17.635808] applesmc: wait status failed: 5 != 0
[   26.924421] applesmc: wait status failed: 5 != 0
[   26.960253] applesmc: wait status failed: 5 != 0
[   27.580424] applesmc: driver unloaded. :(

```

---

### Post by kosumi68 on 2008-11-05
> **Kooothor said:**
> 

	Product Name: MacBook4,1
	Product Name: Mac-F22788A9

Your model is not properly supported in applesmc. Please run this script

[http://ubuntuforums.org/attachment.php?attachmentid=85996&d=1224442499](http://ubuntuforums.org/attachment.php?attachmentid=85996&d=1224442499)

as root, and report the output here, so we can add it. The script is from this thread [http://ubuntuforums.org/showthread.php?t=924096&highlight=wait+status+applesmc](http://ubuntuforums.org/showthread.php?t=924096&highlight=wait+status+applesmc), which has already been used several times.

Thanks!

---

### Post by Kooothor on 2008-11-05
Here is the output of the script :
[http://pastebin.com/m60f6c15](http://pastebin.com/m60f6c15)

I've already added the patch provided on the thread you're refering to. (it was to get rid of the "failed status" messages). But it was with previous kernel.

In hardy it was all fine, but in Intrepid I think something deactivate the loading of applesmc at boot.... :(

---

### Post by kosumi68 on 2008-11-05
Ok, here is a version with macbook4 support for testing. Please install and test using this script: [http://ubuntuforums.org/attachment.php?attachmentid=85861&d=1221901854](http://ubuntuforums.org/attachment.php?attachmentid=85861&d=1221901854). If you want to be included as Tested-by in the upstream patch, send me a private message with name and email. Thanks!

---

### Post by AleXit on 2008-11-05
Thank you kosumi68 ! Your package works very well on my system:
```
[  368.134234] applesmc: Apple MacBook 4 detected:
[  368.134248] applesmc:  - Model with accelerometer
[  368.134253] applesmc:  - Model without light sensors and backlight
[  368.134259] applesmc:  - Model with 10 temperature sensors
[  368.135228] applesmc: device has already been initialized (0xe0, 0xf8).
[  368.135234] applesmc: device successfully initialized.
[  368.136194] applesmc: 1 fans found.
[  368.138312] input: applesmc as /devices/platform/applesmc.768/input/input12
[  368.172123] applesmc: driver successfully loaded.

``````
ale@MacBook:~/Desktop$ ./applesmc-test.sh 
accelerometer: present, readable, output: (-14,7,268)
fan:           present, readable, output: 2300
light:         not present
leds:          not present
temperatures:  present,
 temperature:           readable, output: 48500
 temperature:           readable, output: 31500
 temperature:           readable, output: 51000
 temperature:           readable, output: 49000
 temperature:           readable, output: 53250
 temperature:           readable, output: 48500
 temperature:           readable, output: 65000
 temperature:           readable, output: 62000
 temperature:           readable, output: 49250
 temperature:           readable, output: 49000
performance:   reading all temperatures
 fail frequency:        0
 reads per second:      62
```

Now I would like to increase fan1_min speed, but I cannot set it permanently...
```
root@MacBook:~# echo 3000 > /sys/devices/platform/applesmc.768/fan1_output 
root@MacBook:~# cat /sys/devices/platform/applesmc.768/fan1_output 
2024
root@MacBook:~# echo 3000 > /sys/devices/platform/applesmc.768/fan1_min
root@MacBook:~# cat /sys/devices/platform/applesmc.768/fan1_min
1932
```How can I get that?
Many Thanks,
Alessandro

---

### Post by kosumi68 on 2008-11-06
> **AleXit said:**
> 
Now I would like to increase fan1_min speed, but I cannot set it permanently...
```
root@MacBook:~# echo 3000 > /sys/devices/platform/applesmc.768/fan1_output 
root@MacBook:~# cat /sys/devices/platform/applesmc.768/fan1_output 
2024
root@MacBook:~# echo 3000 > /sys/devices/platform/applesmc.768/fan1_min
root@MacBook:~# cat /sys/devices/platform/applesmc.768/fan1_min
1932
```How can I get that?

Looks related to this post: [http://ubuntuforums.org/showpost.php?p=6098357&postcount=7](http://ubuntuforums.org/showpost.php?p=6098357&postcount=7)

---

### Post by Kooothor on 2008-11-06
> **kosumi68 said:**
> Ok, here is a version with macbook4 support for testing. Please install and test using this script: [http://ubuntuforums.org/attachment.php?attachmentid=85861&d=1221901854](http://ubuntuforums.org/attachment.php?attachmentid=85861&d=1221901854). If you want to be included as Tested-by in the upstream patch, send me a private message with name and email. Thanks!

Ok, thanks kosumi68, here is the output :
[http://pastebin.com/m6ceaa81f](http://pastebin.com/m6ceaa81f)

I'll try to reboot and see if it works in an hour or so.

---

### Post by kosumi68 on 2008-11-06
> **AleXit said:**
> 
[/code]```
ale@MacBook:~/Desktop$ ./applesmc-test.sh 
accelerometer: present, readable, output: (-14,7,268)
fan:           present, readable, output: 2300
light:         not present
leds:          not present
temperatures:  present,
 temperature:           readable, output: 48500
 temperature:           readable, output: 31500
 temperature:           readable, output: 51000
 temperature:           readable, output: 49000
 temperature:           readable, output: 53250
 temperature:           readable, output: 48500
 temperature:           readable, output: 65000
 temperature:           readable, output: 62000
 temperature:           readable, output: 49250
 temperature:           readable, output: 49000
performance:   reading all temperatures
 fail frequency:        0
 reads per second:      62
```


Upstream patch: [http://lkml.org/lkml/2008/11/6/86](http://lkml.org/lkml/2008/11/6/86)

---

### Post by kosumi68 on 2008-11-06
> **Kooothor said:**
> Ok, thanks kosumi68, here is the output :
[http://pastebin.com/m6ceaa81f](http://pastebin.com/m6ceaa81f)

I'll try to reboot and see if it works in an hour or so.

The dkms package installer does not reload the module, so in order to take effect, you need to do that manually. I already sent the patch - it seems the two of you had the same problem. :-)

---

### Post by Kooothor on 2008-11-06
> **kosumi68 said:**
> The dkms package installer does not reload the module, so in order to take effect, you need to do that manually. I already sent the patch - it seems the two of you had the same problem. :-)

Yeah, after reboot applesmc is still deactivated during the boot (after being successfully loaded...)
BUT : good thing is I don't have anymore "wait status failed" in dmesg AND all the temperature are read out correctly each time ! :D \o/


EDIT : I've found why my applesmc is deactivated, I had modified something in rc.local (rmmod applesmc and insmod with the patched one)
So now I've done some editing and all should be fine ! :D

---

### Post by AleXit on 2008-11-06
> **kosumi68 said:**
> Looks related to this post: [http://ubuntuforums.org/showpost.php?p=6098357&postcount=7](http://ubuntuforums.org/showpost.php?p=6098357&postcount=7)
The fan behaviour is very strange:
```
root@MacBook:~# echo 0 | sudo tee -a /sys/devices/platform/applesmc.768/fan1_manual
0
root@MacBook:~# echo 3000 | sudo tee -a /sys/devices/platform/applesmc.768/fan1_min
3000
root@MacBook:~# cat /sys/devices/platform/applesmc.768/fan1_min
2208
root@MacBook:~# cat /sys/devices/platform/applesmc.768/fan1_min
1932
root@MacBook:~# sensors | grep Exhaust
Exhaust  :  1801 RPM  (min =    1 RPM)
root@MacBook:~# echo 1 | sudo tee -a /sys/devices/platform/applesmc.768/fan1_manual
1
root@MacBook:~# echo 3000 | sudo tee -a /sys/devices/platform/applesmc.768/fan1_min
3000
root@MacBook:~# cat /sys/devices/platform/applesmc.768/fan1_min
1932
root@MacBook:~# sensors | grep Exhaust
Exhaust  :  1935 RPM  (min = 1932 RPM)
root@MacBook:~# sensors | grep Exhaust
Exhaust  :  1928 RPM  (min = 1932 RPM)
root@MacBook:~# cat /sys/devices/platform/applesmc.768/fan1_min
1
root@MacBook:~# sensors | grep Exhaust
Exhaust  :  1929 RPM  (min =    1 RPM)
root@MacBook:~# sensors | grep Exhaust
Exhaust  :  1935 RPM  (min = 4140 RPM)
root@MacBook:~# cat /sys/devices/platform/applesmc.768/fan1_min
4692
root@MacBook:~# sensors | grep Exhaust
Exhaust  :  1929 RPM  (min = 5060 RPM)
```
So, it seems fan is indipendent (or it doesn't read) from fan1_min value... :confused:

---

### Post by Kooothor on 2008-11-06
Your fan is gone crazy !

---

### Post by kosumi68 on 2008-11-06
> **AleXit said:**
> 
So, it seems fan is indipendent (or it doesn't read) from fan1_min value... :confused:

Do you have a MBP41 with two fans, or the MB41 with one fan?

---

### Post by AleXit on 2008-11-06
> **kosumi68 said:**
> Do you have a MBP41 with two fans, or the MB41 with one fan?
I have a MB41 with one fan (early 2008 )

---

### Post by kosumi68 on 2008-11-06
What could it be except user-space interference. I would boot the machine in single-user mode (rescue mode), and do the experiment from there.

---

### Post by AleXit on 2008-11-06
> **kosumi68 said:**
> What could it be except user-space interference.Maybe some daemon related to acpi/power management which get control of the fan?:confused:
Thank you for your help, guy ;)

---

### Post by dxlr8r on 2008-11-11
Running Ubuntu 8.10 on Mac Pro (early 2008) with "2.6.27-7-generic" and I also get:

```
sudo modprobe applesmc
FATAL: Error inserting applesmc (/lib/modules/2.6.27-7-generic/kernel/drivers/hwmon/applesmc.ko): No such device

```

When is this thing gonna work? :confused:

---

### Post by kosumi68 on 2008-11-11
> **dxlr8r said:**
> Running Ubuntu 8.10 on Mac Pro (early 2008) with "2.6.27-7-generic" and I also get:

```
sudo modprobe applesmc
FATAL: Error inserting applesmc (/lib/modules/2.6.27-7-generic/kernel/drivers/hwmon/applesmc.ko): No such device

```

When is this thing gonna work? :confused:

Is that a MacPro you have there? In that case it is most likely completely unsupported by applesmc, which is quite a different problem. Check out this link to get it supported: [http://ubuntuforums.org/showthread.php?t=924096](http://ubuntuforums.org/showthread.php?t=924096)

---

