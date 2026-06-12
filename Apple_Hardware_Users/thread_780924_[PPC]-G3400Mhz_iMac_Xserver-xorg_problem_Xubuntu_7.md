---
title: "[PPC]-G3/400Mhz iMac Xserver-xorg problem Xubuntu 7.10"
date: 2008-05-03
forum: Apple Hardware Users
---

### Post by shgadwa on 2008-05-03
This is a apple G3 PPC iMac computer, 400Mhx, 512MB ram and a 40GB hard drive.

Because of so many problems with this imac while trying to get 8.04 to work, I went with xubuntu 7.10 which appears to also have problems.

I checked the date, that is right. I typed in "free -m" to find out how much ram it actually has. it has like 503MB with a rather large swap drive. I did update and upgrade it "sudo apt-get update" I also edited the /etc/X11/xorg.conf file according to what they said online.....I did all I can think of doing and I still get this message saying that the Xserver-xorg failed to start because

/etc/gdm/failsafeXserver: lines 47: [: Too Many arguements
Warning: could not retrieve EDID because get-edid is not installed. 

How do i go about this????

Also, as someone else suggested, I did do a server install of 8.04 and also of 7.10. the 8.04 on did just what it did before and the 7.10 one did the same thing...had the xserver error.

Also, I like the idea of doing a server install and adding what I need after that. Do I just need to install the desktop environment or is there more to it than that?

---

### Post by abtabt on 2008-05-04
the best way is to install server (i belive that)
[http://cdimage.ubuntu.com/ports/releases/hardy/release/](http://cdimage.ubuntu.com/ports/releases/hardy/release/)
then
apt-get update
then
apt-get upgrade
then 
apt-get install xorg icewm icewm-theme menu synaptic
now you have a start 
 
do restart
type init 6
then when have boot up 

type startx (its starts upp icewm)
if blackscreen 
check the xorg file
nano /etc/X11/xorg.conf
and post it
good luck

---

### Post by shgadwa on 2008-05-06
Well Well,

I did a fresh install of 8.04 and did everything you said to do. I 'properly' configured the xorg.conf file. I upgraded and updated it. The date is set right. Also, it is icewm -theme not icewm-theme. that worked.

I typed in startx. and it loads and says a few errors, like no screens found, failed to start xserver, reconfigure /etc/X11/xorg.conf, report bugs as some link they give me.

I think by now I must have reinstalled different (or the same) OSes about 20 times on this computer, with no luck. What now????? 

There was someone I read on this forum some while back, that got Hardy working on their 333Mhz imac...please tell me how as I do not get it.

Shawn

---

### Post by oswaldkelso on 2008-05-06
This is how I set up my xorg on my debian system. I realise ubuntu has a newer xorg so I'm not sure if it will work for you but you can try it ayor.

try sudo nano /etc/X11/xorg. and edit the file manualy or

To setup the X Window System.

CODE:

# dpkg-reconfigure xserver-xorg

NOTE: here are my settings for the UK. Yours will differ depending on your location.

ATI,ok,ok,ok,yes,auto detect keyboard,yes,ok,ok,pc105,ok,ok,imps/2,yes (I have a 3 button mouse with scroll wheel, if you have a "puck" play hockey with it as you really need a 3 button mouse in linux).yes,enter imac,1024x768,Advanced, change settings to 58-62 for vertical and 75-117 horizontal (this is important X Windows will fail if left at the default).yes,24.

NOTE:EMAC: If you have an emac when you get to Advanced, change settings to 71-73 for vertical and 70-140 horizontal. Also although emacs support screen resolutions 1280x960 and 1152x870 only 1024x768 ever shows up?. The resolution seems "small" so I'm not sure whats up. Just make sure 1024x768 is selected as I understand debian will choose the highest resolution available.

NOTE: if anything fails rerun and tweak with.

CODE:

# dpkg-reconfigure xserver-xorg

---

### Post by shgadwa on 2008-05-06
hmmm I am getting tired of this. Seems as if Linux is not for PPC. I tried the d[kg-reconfigure xserver-xorg but I always get this warning saying the data is important and to back up and or something like that...nothing more.

I think i will buy an older Dell laptop and put 8.04 on it. Unless someone else knows of anything else Ic an try to do. I also lost my 6.04 Cd which though that one was not current, it worked a lot faster than openSUSE.

---

### Post by oswaldkelso on 2008-05-06
> **shgadwa said:**
>  Seems as if Linux is not for PPC. 

Linux runs fine on ppc I have debian on an imac 333 and emac usb 1 model. I also have 5 edit: 6 distros on a g4 tower Debian testing, Ubuntu hardy, Fedora 8, Slackintosh 12, yellowdog 6 and suse 10.3, All run fine some better than others some easier to use, some faster. But they all have  different types of user in mind. 

The thing is, with the freedom that Linux gives both the user and developer, they may all do things slightly differently. Because they all have the option of doing what they think is best. It can make it hard for a new user to learn.  Pick a distro stick with it and learn from it. I tried fedora 9 and suse 11 both failed, they're  both beta that's OK. Do what I did install the latest version that works. Hardy is bound to be a bit buggy its only been out a few days. Try another distro or a slightly older version until you become more comfortable and confident around your system.
Just don't come back raving about how great it is:lolflag:

---

### Post by stream303 on 2008-05-06
hmm.. you have installed the 8.04 server but have problems with startx.  This is no guarantee, but perhaps installing a login manager like xdm might help:

```
sudo apt-get install xdm
```

---

### Post by abtabt on 2008-05-07
Can you post the xorg.conf then maybe we can help you

nano /etc/X11/xorg.conf

PS OBS VARNING WARNING

and the old thing too recon the xsever 

sudo dpkg-reconfigure -phigh xserver-xorg

or 
sudo dpkg-reconfigure xserver-xorg

DONT WORK SOME TIMES (Spec on hardy)

but post your xorg.conf file

and wait too install any login manager 

i have hardy on imac 333mz 96mb 

to check only the xserver you only type X then the xserver will start

but you need a corect xorg.conf file

---

