---
title: "MacBook 6,1 - No Sound with ALSA - Karmic  (9.10)"
date: 2010-03-27
forum: Apple Hardware Users
---

### Post by Coburn64 on 2010-03-27
Howdy guys.

I'm having serious problems with my Apple Macbook 6,1 running Ubuntu 9.10. I have read that PulseAudio is lame and troublesome, and I have uninstalled it and installed eSound and ALSA (and the alsa tools) instead. (please don't say to reinstall pulseaudio.... :/)

I have the latest 2.6.31 kernel installed, linux-image-2.6.31-20-generic and also have installed the backports version of alsa.

When I go to GNOME ALSA Mixer, it will detect my Sound Card, which is a "Cirrus Logic CS4206" card. However, no mixer settings will appear.

aplay -l results in the following:
> 
*** List of PLAYBACK Hardware Devices ***


aplay results in the following:
> 
ALSA lib pcm_dmix.c:1008: (snd_pcm_dmix_open) unable to open slave
aplay main:590: audio open error: No such file or directory


alsamixer results in the following:
> 
No mixer elems found


The rest of the system is quiet as a mouse. No bongs, dings or bleeps anywhere.

Any help is greatly appeariated. I need the problem fixed ASAP, as I do my web development on Ubuntu and I need a fully working system.

Thanks all! :)

---

### Post by linuxopjemac on 2010-03-27
I would start with installing the alsa-backport
```
sudo apt-get install linux-backports-modules-alsa-karmic-generic
```

you might have to edit your /etc/modprobe.d/alsa-base.conf to have
```
options snd-hda-intel add model=mb31 power_save=10 power_save_controller=N
```
at the end of the said file

to edit:
```
sudo nano /etc/modprobe.d/alsa-base.conf
```
if you are finished
CTRL-X and "y" to save

---

### Post by dearingj on 2010-03-27
I found that the ALSA backport used to work until a kernel update was released earlier this month on my Macbook Pro 5,3. I don't know why the update would have caused such a problem, but the solution that worked for me was to upgrade to Ubuntu 10.04 beta.

---

### Post by Coburn64 on 2010-03-27
No dice. I added those lines that linuxopjemac suggested, but after I did that in knocked out my Mixer settings (nothing at all in ALSA Mixer now)!

Here's my alsa-base.conf:

[http://pastebin.ca/1854235](http://pastebin.ca/1854235)

Looks like I'm never buying apple again... :|

EDIT: ALSA will reload the modules successfully, but alsamixer returns:

> 
alsamixer: function snd_ctl_open failed for default: No such device


---

### Post by alexmurray on 2010-03-27
I dont think the MacBook 6,1 has the same audio codec as the mb31 - in fact linuxopjemac on your website you have a page which says to use mb5 model not mb31 - [http://mac.linux.be/content/karmic-koala-macbook-61](http://mac.linux.be/content/karmic-koala-macbook-61) - so I would suggest perhaps trying that instead.

---

### Post by Coburn64 on 2010-03-27
Changed the parameters, and rebooted.

Now when I reboot, I have a problem. Xorg hangs. I think it may be wanting ALSA to startup, but it's not responding (?).

The logo will light up, and blink as it starts up, then my screen flickers as Xorg loads the Nvidia drivers, and then it's a black screen. Pressing Power button will either 1) cause the top of the screen to turn red/blue with really scrunched up blocky text and then shutdown after a few moments or 2) Xorg will respond and kill itself, and then shutdown.

Booting into recovery mode, launching normal mode from the recovery menu and logging in through the console will work fine, then typing startx will bring gnome back from the dead. Running *sudo alsa force-reload* will reload the modules without fault. BUT this error lingers around: 

> 
alsamixer: function snd_ctl_open failed for default: No such device


:confused:

---

### Post by linuxopjemac on 2010-03-28
Thank you Alex, I forgot that page. I have to update the Intel wiki Sound page...

[updated page]("http://mac.linux.be/content/sound-problems")

---

### Post by filipefumaux on 2010-04-07
I've got same problem. 
Already did everything possible. 
Complile Alsa, download it using apt-get.
Nothing of theses things works.

Any idea?

---

### Post by linuxopjemac on 2010-04-07
I would take kernel 2.6.31.19 and try [this]("http://mac.linux.be/content/karmic-koala-macbook-61"), change
```
sudo apt-get install linux-backports-modules-alsa-2.6.31-17-generic
``` 
into
```
sudo apt-get install linux-backports-modules-alsa-2.6.31-19-generic 
```
I heard positive stories about that kernel.

---

### Post by filipefumaux on 2010-04-07
> **linuxopjemac said:**
> I would take kernel 2.6.31.19 and try [this]("http://mac.linux.be/content/karmic-koala-macbook-61"), change
```
sudo apt-get install linux-backports-modules-alsa-2.6.31-17-generic
``` 
into
```
sudo apt-get install linux-backports-modules-alsa-2.6.31-19-generic 
```
I heard positive stories about that kernel.

I tried linux-backports-modules-alsa-2.6.31-20-generic 
Doesnt work.
Im trying now 31-17-generic.
After I'll try to download and compile on my machine

---

### Post by filipefumaux on 2010-04-07
> **filipefumaux said:**
> I tried linux-backports-modules-alsa-2.6.31-20-generic 
Doesnt work.
Im trying now 31-17-generic.
After I'll try to download and compile on my machine
Tried to install 31-19 but installation does not work, but its appear on grub. 
Sound is working with 31-17 and 31-19, but only in headphones.
I ran **alsamixer** to put everything to works fine.
so use ```
sudo apt-get install linux-backports-modules-alsa-2.6.31-17-generic
``` or ```
sudo apt-get install linux-backports-modules-alsa-2.6.31-19-generic
```
Now, after install this, I got a new kernel and video driver stops to work right. Im trying to install driver again.
Wifi stopped too, but Ill try the first steps.
Everything back to work.
My Mac its a iLinux (ubuntu) 100%

---

### Post by Old Codger on 2010-08-12
When you go to GNOME ALSA mixer, unmute the second speaker to the right of master. It worked for me.

---

### Post by kurosudiro on 2010-09-05
> **Old Codger said:**
> When you go to GNOME ALSA mixer, unmute the second speaker to the right of master. It worked for me.

that's correct ,but I have to upgrade my kernel on 
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.32.19-lucid/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.32.19-lucid/)
kurosudiro@kurosudiro-laptop:~$ uname -r
2.6.32-02063219-generic

because, the default karmic kernel still wont detect souncard :D

---

