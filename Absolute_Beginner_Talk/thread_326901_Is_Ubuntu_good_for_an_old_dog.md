---
title: "Is Ubuntu good for an old dog?"
date: 2006-12-28
forum: Absolute Beginner Talk
---

### Post by dbbd8 on 2006-12-28
I have an old computer I want to setup as a samba server.
I have never used Ubuntu, but heard a lot about it.

I'd like to know if people think Ubuntu will run well on an old computer:
AMD Athlon (i686)
256MB RAM
Riva TNT graphics

I plan to disconnect the monitor after I complete the installation, and would
like an unattended boot. I'm not interested in a desktop, but rather a file server. 
On the other hand, I'd like very simple setup, and I understand Ubuntu has that!

Appreciate constructive inputs,
Dan

---

### Post by pseudonym on 2006-12-28
If you're going to go headless you will have no problems at all. If you do want a GUI at some later stage, may I recommend [Xubuntu]("http://xubuntu.org/home") over the other Ubuntu variants. It's much more lightweight and is designed to run on older hardware. I even use it on my new machine because I'm addicted to the speed :)

---

### Post by ButteBlues on 2006-12-28
Absolutely!

I have the XFCE desktop and Ubuntu running on an old 300 MHz PII with 96 MB RAM! :P

You could install the server CD, and if you want, xubuntu-desktop package as well for XFCE desktop (which is very light).

---

### Post by K.Mandla on 2006-12-28
> **a simple façade said:**
> Absolutely!

I have the XFCE desktop and Ubuntu running on an old 300 MHz PII with 96 MB RAM! :P

You could install the server CD, and if you want, xubuntu-desktop package as well for XFCE desktop (which is very light).
Ditto that. An Athlon is not an old dog yet. :) I use Openbox on 6.10 on a 300Mhz P2 as well, and it's a little slow on the start, but after that it's just fine.

---

### Post by dupa on 2006-12-28
> **dbbd8 said:**
> I have an old computer I want to setup as a samba server.
I have never used Ubuntu, but heard a lot about it.

I'd like to know if people think Ubuntu will run well on an old computer:
AMD Athlon (i686)
256MB RAM
Riva TNT graphics

I plan to disconnect the monitor after I complete the installation, and would
like an unattended boot. I'm not interested in a desktop, but rather a file server. 
On the other hand, I'd like very simple setup, and I understand Ubuntu has that!

Appreciate constructive inputs,
Dan

you can absolutely use Xubuntu on it (if you want a GUI environment)
if you just need a fileserver it's better if you use "Ubuntu Server" distribution.

Have good time.

---

### Post by louieb on 2006-12-28
My P3 433 256M  now hosts a web server, and ftp file server for my home network. Install when very easy and setup wasn't hard either. Ran almost out of the box just had to change some permissions  on the web server.
Installed on server. (all installed through aptitude)
[LIST]
[*]Ubuntu lamp server (static ip address)
[*]proftpd
[*]openssh-server
[*]midnight commander (mc)[/LIST]The other machines on the network have an ftp client. and connect to to server via ip address. I was surprised at how easy it was.
Administration of the server    is via terminal and ssh on Linux or through putty on XP.

---

### Post by dbbd8 on 2006-12-28
Thanks for the answers. 
I'm getting the 6.10 server version.

Dan

---

### Post by TheWizzard on 2006-12-28
> **dbbd8 said:**
> I have an old computer I want to setup as a samba server.
I have never used Ubuntu, but heard a lot about it.

I'd like to know if people think Ubuntu will run well on an old computer:
AMD Athlon (i686)
256MB RAM
Riva TNT graphics

I plan to disconnect the monitor after I complete the installation, and would
like an unattended boot. I'm not interested in a desktop, but rather a file server. 
On the other hand, I'd like very simple setup, and I understand Ubuntu has that!

Appreciate constructive inputs,
Dan

i have my amd athlon as main computer + file server running kde. it runs smooth and fast :D   much better than winxp on my 1 year old pc at work. 
games are the only reason to buy a newer one. 

nb: athlon is NOT i686 and you should use the k7 kernel.

---

### Post by dbbd8 on 2006-12-30
I've installed 6.10 server, added ssh-server, and samba, configured a samba share, and it all works.

However, it works too slow.
When I play an mp3 file off the share, on an XP system, it plays fine as long as there's
no other access through samba. If another access, even browsing is concurrent,
playing becomes jerky. I also increased the player buffer size, to no avail.

I don't know if the problem is ubuntu performance, disk access, or network performance.
I find no vstat nor iostat in ubuntu, and I don't know how to measure performance in order to figure out what makes it slow.

I want to install the XFCE and verify the Ubuntu itself plays mp3 well, but cannot figure out how.

Being a newbie is hard.
Dan

---

### Post by hyper_ch on 2006-12-30
Installing Xfce
> 
sudo aptitude install xubuntu-desktop


---

### Post by pseudonym on 2006-12-30
> **dbbd8 said:**
> I want to install the XFCE and verify the Ubuntu itself plays mp3 well, but cannot figure out how.
Hi Dan,

while it is certainly possible to install xfce on your server, it isn't really necessary if all you want to do is test sound playback. You can do that all on the command line - ```
sudo apt-get install alsa-base alsa-utils mpg321
``` 
This will install the minimum needed to play mp3. Provided you aren't using an ISA sound card in that machine, ALSA should configure itself. You can set your volumes and whatnot with - ```
alsamixer
sudo alsactl store (to save the settings)
```
Then you can play an mp3 by typing - ```
mpg321 filename.mp3
```
As far as disk access goes, there is the 'hdparm' utility, which is probably installed by default, but if it isn't, just type - ```
sudo apt-get install hdparm
```
Then run these commands to test the speed - ```
sudo hdparm -d /dev/hd* (to verify dma is turned on)
sudo hdparm -t -T /dev/hd* (speed test, should be run 3 times)
```
I don't think disk access will be world-shattering on that machine, but if it's painfully slow you can use hdparm to tweak a few parameters. See 'man hdparm'.

I can't help with network testing, though I'm sure there are others here who can.

HTH :)

---

### Post by TheWizzard on 2006-12-30
> **dbbd8 said:**
> 
However, it works too slow.
When I play an mp3 file off the share, on an XP system, it plays fine as long as there's
no other access through samba. If another access, even browsing is concurrent,
playing becomes jerky. I also increased the player buffer size, to no avail.

I don't know if the problem is ubuntu performance, disk access, or network performance.
I find no vstat nor iostat in ubuntu, and I don't know how to measure performance in order to figure out what makes it slow.


this has probably to do with your samba settings. 
- check the logfiles in /var/log/samba. search for files with the ip-address of your windows client. you may need to increase the detail level of the logging. 
- [http://www.google.nl/search?q=samba+optimization](http://www.google.nl/search?q=samba+optimization)
- [www.samba.org](www.samba.org)

ps. i have the same problem, but i only use windows like once a month. from ubuntu i can access my samba server without problems.

---

