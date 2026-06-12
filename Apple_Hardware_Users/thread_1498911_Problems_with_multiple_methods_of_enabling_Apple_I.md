---
title: "Problems with multiple methods of enabling Apple Isight on Ubuntu"
date: 2010-06-01
forum: Apple Hardware Users
---

### Post by Singlish on 2010-06-01
As the title says, i'm having problems with many of the tutorials i came across on the web. I've tried many, and will display 2 shows of my non-existent skills. **The titles are hyperlinked, so you can see what was *supposed* to happen.**

**[1. Getting the file from Tiger]("http://www.icram.de/content/ubuntu-910-macbook-using-apples-isight-camera-howto") (Personal Favorite)**
[INDENT][COLOR="DarkGreen"]singlish@Singlish-Linux:/$ ls
bin      dev         initrd.img.old  mnt   sbin     tmp      vmlinuz.old
boot     etc         lib             opt   selinux  usr
cdrom    home        lost+found      proc  srv      var
Desktop  initrd.img  media           root  sys      vmlinuz[/COLOR]

[COLOR="Lime"]singlish@Singlish-Linux:/$ sudo mkdir /MacOS [/COLOR]

[COLOR="DarkGreen"]singlish@Singlish-Linux:/$ sudo chmod -R ug+rw /MacOS[/COLOR]

[COLOR="Lime"]singlish@Singlish-Linux:/$ cd /MacOS[/COLOR]

[COLOR="DarkGreen"]singlish@Singlish-Linux:/MacOS$ sudo cp /media/Singlish/AppleUSBVideoSupport .[/COLOR]

[COLOR="Lime"]singlish@Singlish-Linux:/MacOS$ ls
AppleUSBVideoSupport[/COLOR]

[COLOR="DarkGreen"]singlish@Singlish-Linux:/MacOS$ sudo apt-get install isight-firmware-tools
Reading package lists... Done
Building dependency tree       
Reading state information... Done
isight-firmware-tools is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 11 not upgraded.[/COLOR]
 
[COLOR="Red"]This is the part were it doesn't open. Other then that, no problems.[/COLOR]
[/INDENT]

**[2.Newest Super Quick 2-Step Install]("http://ubuntuforums.org/showthread.php?t=225621")**

[INDENT][COLOR="Green"]singlish@Singlish-Linux:~$ wget [http://www.shiftingheat.com/packages/isight/isight_install.sh](http://www.shiftingheat.com/packages/isight/isight_install.sh)
--2010-06-01 22:38:33--  [http://www.shiftingheat.com/packages/isight/isight_install.sh](http://www.shiftingheat.com/packages/isight/isight_install.sh)
Resolving [www.shiftingheat.com](www.shiftingheat.com)... 67.205.2.217
Connecting to [www.shiftingheat.com|67.205.2.217|:80](www.shiftingheat.com|67.205.2.217|:80)... connected.
HTTP request sent, awaiting response... 200 OK
Length: 626 [application/x-sh]
Saving to: `isight_install.sh'

100%[======================================>] 626         --.-K/s   in 0.002s  

2010-06-01 22:38:34 (302 KB/s) - `isight_install.sh' saved [626/626][/COLOR]

[COLOR="Red"]singlish@Singlish-Linux:~$ sh sight_install.sh
sh: Can't open sight_install.sh[/COLOR]
[/INDENT]

Yea... the colors and indents took some time...
Bonus popcorn question! :popcorn:
How do i enable the audio input on my Macbook?...

---

### Post by tenuki on 2010-06-01
Answer probably differs depending on which Macbook model you have. Could you post output of:

```
sudo dmidecode -s system-product-name
```

Once you have that, you might find the answer already in the community documentation:

[https://help.ubuntu.com/community/MacBook](https://help.ubuntu.com/community/MacBook)

if not, let us know.

---

### Post by Singlish on 2010-06-01
> **tenuki said:**
> Answer probably differs depending on which Macbook model you have. Could you post output of:

```
sudo dmidecode -s system-product-name
```

Once you have that, you might find the answer already in the community documentation:

[https://help.ubuntu.com/community/MacBook](https://help.ubuntu.com/community/MacBook)

if not, let us know.

Thank you, i have fixed the problem. The reason why the Firmware installation tool did not respond, was because i didn't purge it from the system. I have also successfully created the script. Thank you very much! :popcorn:

I now have problems with my Mic. Which i have tested with the sound recorder.

---

