---
title: "Power Mac G3 &amp; G4 (PPC) Install"
date: 2010-09-09
forum: Apple Hardware Users
---

### Post by techgrl on 2010-09-09
What is the best distro & instruction set to install Linux on Power Macs? I have Blue/White G3's and Gray/White G4's. I also have a ton of little blue/white cube iMac G3's.

Our company upgraded a department's hard/software and we are left with an entire room of old MACS that I want to re-purpose and give away.

In order to get OS9 off of these relics and make them usable, I am trying Ubuntu 7 (alt CD) and Debian.

I get so far in the install and end up getting stuck on random black screens.

My favorite so far is: initramfs.

I would take any advice you have to offer.

Thank you in advance.

---

### Post by oswaldkelso on 2010-09-09
You'll be wanting Debian squeeze/testing then with minitube for youtube if you giving them away. I'd recommend the xfce-lxde install very easy for new users and light.

[http://cdimage.debian.org/cdimage/weekly-builds/powerpc/iso-cd/debian-testing-powerpc-xfce+lxde-CD-1.iso](http://cdimage.debian.org/cdimage/weekly-builds/powerpc/iso-cd/debian-testing-powerpc-xfce+lxde-CD-1.iso)

---

### Post by techgrl on 2010-09-09
Thank you. I am downloading it now. I am a Mac/WIN tech with sparse Linux experience here and there. In bursts during a project, then nothing for a year. I start the learning process over with each new burst.

I appreciate the input.

---

### Post by barbaGNU on 2010-09-09
Frugalware PPC or CRUX PPC are a good choice too.

---

### Post by techgrl on 2010-09-10
There are random RAM allotments for the stockpile of machines I am working with. I try to make sure they have 512MB, but it's old PC133 or 100, so if I haven't been pack-ratting, some will likely have 128MB.

The Squeeze install went wonderfully. Smooth. BUT...BUT, upon first launch I have a display issue. I can see a very pixel-filled bottom white bar where the taskbar should be, but that is where it freezes. I am parked there right at this moment, as a matter of fact. Stuck.

I have tried Control F1 to get into an editor to modify resolution allowances, but honestly, I don't know exactly how to force it into a terminal session.

After that, I THINK I use the gedit command somehow to USE the editor. Any suggestions?

---

### Post by linuxopjemac on 2010-09-10
which Mac? (everymac.com)

---

### Post by oswaldkelso on 2010-09-10
I would say you need 256mb min. 
If you need to sort you xorg.conf gather as much info on the monitors as possible first. Then search :) If you cant find a xorg.conf ready made You'll need to build one your self.

to get a terminal:
ctl+alt F1


[http://forums.debian.net/viewtopic.php?f=10&t=52787](http://forums.debian.net/viewtopic.php?f=10&t=52787)
[http://forums.debian.net/viewtopic.php?f=16&t=26577](http://forums.debian.net/viewtopic.php?f=16&t=26577)
[http://wiki.debian.org/XStrikeForce/HowToRandR12](http://wiki.debian.org/XStrikeForce/HowToRandR12)

And read the links in my sig it'll give you a very good basis for GNU/Linux on PPC

---

### Post by techgrl on 2010-09-10
I have now had 2 of the Power Mac G4's install seamlessly, only to kick the bad display upon first launch.

---

### Post by techgrl on 2010-09-10
AND...to get a terminal:
ctl+alt F1

Not able to make that happen.

At black screen I bang the **** out of the keys and nothing. Is there a secret?

---

### Post by techgrl on 2010-09-10
Here is what I see...

---

### Post by Chipmunkor on 2010-09-10
[Look in my thread]("http://ubuntuforums.org/showthread.php?t=1567584") maybe something from there will help you

---

### Post by linuxopjemac on 2010-09-11
boot Linux with:

```
Linux 1
```

in single user mode and you can edit xorg.conf

---

### Post by CodeJoker on 2010-09-11
You probably have NVIDIA Geforce MX graficcards in your Macs.
The X-Server from debian-testing apparently doesn't support those at the moment.
@linuxopjemac: So even with access to a console - editing xorg.conf wouldn't do the trick.
@techgrl: Please give the latest stable version "Lenny" a try.

---

### Post by CodeJoker on 2010-09-11
Uups, sorry, I forgot to mention that even with debian "Lenny" you will probably end up in a text console if you have Geforce cards. If this happens to you, do the following:
1. Log in as root.
2. Type the following five lines:

Xorg -configure
mv /etc/X11/xorg.conf /etc/X11/xorg.conf.old
cp /root/xorg.conf.new /etc/X11/xorg.conf
init 1
init 2

After that, gdm should pop up and you ought to be able to log straight into gnome.
Since your machines appear to be short of RAM (below 256 MB) any lightweight windows-manager would be preferable. You can use synaptics to install e.g. lxde or icewm.

With at least 192MB of RAM you should consider xubuntu 10.04 "Lucid Lynx".
(BTW: RAM for this machines is REALLY cheap nowadays.)
For a test you can perhaps plug the RAM-module from one of your machines as addition into another machine to double that machines memory space. With two 128MB modules xubuntu 10.04 will do a very nice job.
Here is the link:

[http://cdimage.ubuntu.com/xubuntu/ports/releases/lucid/release/](http://cdimage.ubuntu.com/xubuntu/ports/releases/lucid/release/)

Good Luck!

---

### Post by oswaldkelso on 2010-09-12
Looks like the xserver-xorg-video-nouveau is in squeeze

[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=558788](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=558788)

That said most machines around that time G3 changing to G4 didn't come with the nvidia driver by default but ati > *Originally configured with an ATI Rage 128 Pro graphics card with 16 MB of SDRAM. Also available with a NVIDIA GeForce2 MX video card


Also I'm not sure  if techgl means G4 cube's or old G3 imac's
> I also have a ton of little blue/white cube iMac G3's.

More info required on both those points.

Re: CTL+AlT F1 not working. Are the keyboards Apple? and when setup was US used?

---

### Post by techgrl on 2010-09-13
I have G3/G4 Power Mac towers as well as single unit/monitor combo older G3 iMacs.

---

### Post by CodeJoker on 2010-09-17
Hi techgrl!

On your PowerMacs with G4 CPUs I recommend Xubuntu 10.04.
With at least 192 MB of RAM Xubuntu will work fine.
I lack experience with G3-machines, sorry, but I doubt that you will
find any Open OS for these that installs out of the box.
There has been a Slackware-version for PowerMacs called "Slackintosh".
Even though not up to date it's very slick and will probably install on your G3 machines.
But neither Debian "Lenny" nor "Slackintosh" usually runs without some twiggling.
Hmm, with 192 MB or more Xubuntu might also run well (and out of the box!) on G3s,
but as I said - I have no experience with G3s.

Greetings,

CJ

---

