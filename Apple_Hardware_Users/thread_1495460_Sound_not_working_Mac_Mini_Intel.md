---
title: "Sound not working Mac Mini Intel"
date: 2010-05-28
forum: Apple Hardware Users
---

### Post by jarkinber on 2010-05-28
Hello,

I have just done a fresh single-boot install of lucid Linux and my sound is not working. I own a Mac Mini Intel 3,1 and i have already tried this command: ```
sudo gedit /etc/modprobe.d/alsa-base.conf
``` and added this line to the bottom of the file: options snd-hda-intel model=imac24 but the sound still doesn't work.

Please could someone help me, as i really want to be able to use sound!:confused:

---

### Post by linuxopjemac on 2010-05-28
Did you unmute all channels afterwards ?

```
alsamixer
```

toggle with "m"

---

### Post by jarkinber on 2010-05-28
Well this  is what alsamixer looked like after i pressed 'm' on every section, please tell me if this is right?
sorry im a noob so youll have to download the picture..
[http://www.mediafire.com/?ny2njtnjmy3]("http://www.mediafire.com/?ny2njtnjmy3")
thankyou!!

---

### Post by linuxopjemac on 2010-05-29
All your channels are unmuted now. If it does not work, then you could try the alsa backport module for your kernel.

---

### Post by jarkinber on 2010-05-29
How would i do that?

---

### Post by linuxopjemac on 2010-05-29
```
sudo apt-get install linux-backports-modules-alsa-generic
```

---

### Post by jarkinber on 2010-05-29
i tried that in terminal but the error returned was: ```
 Couldn't find package linux-backports-modules-alsa-generic 
```

---

### Post by linuxopjemac on 2010-05-30
try 
```
sudo apt-get install linux-backports-modules-alsa-lucid-generic
```

if that does not work, just search in synaptics package manager for alsa and see if you find a suitable backports module. I don't exactly know what kernel you use.

---

### Post by jarkinber on 2010-05-30
Thank you this did work and it installed. But what do i do next?
Oh by the way i am running Lucid Linux Ubuntu 10.04 on a 3,1 mac mini.

---

### Post by linuxopjemac on 2010-05-30
Reboot, unmute channels which are muted and check if you have sound.

---

### Post by macalan on 2010-05-30
I had the same issue and this site helped a lot. [http://monespaceperso.org/blog-en/2010/05/02/upgrade-alsa-1-0-23-on-ubuntu-lucid-lynx-10-04/]("http://monespaceperso.org/blog-en/2010/05/02/upgrade-alsa-1-0-23-on-ubuntu-lucid-lynx-10-04/")

---

### Post by jarkinber on 2010-05-31
Thankyou macalan, i followed the instructions on that website very carefully, but it didn't work. the alsa version is still the same! everything seemed to work properly, but i still haven't got sound.

---

### Post by linuxopjemac on 2010-05-31
If you find out what audio card is in your book you might want to try t he options for macs with a similar setup:

[http://mac.linux.be/content/sound-problems](http://mac.linux.be/content/sound-problems)

The solutions are for Karmic Koala though....

Specs site:
[http://www.everymac.com](http://www.everymac.com)

---

### Post by jarkinber on 2010-05-31
well, the entries on that website are for macbook and imac and i dont think will work with my mac mini... oh well, i'll try it anyway.

---

### Post by linuxopjemac on 2010-05-31
If you have a very recent alsa you might want to try  the model macmini3

[http://mailman.alsa-project.org/pipermail/alsa-devel/2010-February/025259.html](http://mailman.alsa-project.org/pipermail/alsa-devel/2010-February/025259.html)

it's in 1.0.23
[http://www.alsa-project.org/main/index.php/Changes_v1.0.22_v1.0.23](http://www.alsa-project.org/main/index.php/Changes_v1.0.22_v1.0.23)
>     - ALSA: hda - Add Macmini 3,1 support 
    BugLink: [https://bugs.edge.launchpad.net/ubuntu/+source/linux/+bug/343989](https://bugs.edge.launchpad.net/ubuntu/+source/linux/+bug/343989) 
    Add a model quirk for the NVIDIA based Macmini hardware, aka Macmini 3,1. The 
    pinout is almost identical to the mb5 quirk, except for no microphone and 
    the line-in mixer controls being on a different index. Everything works in 
    2ch mode, but as I am not sure what needs to be changed for 6ch mode, or 
    whether the Mac Mini's chip supports 6ch mode, I have simply duplicated 
    the code from the mb5 quirk for the mac mini chmode management. The new 
    model parameter for this quirk is "macmini3". 

---

### Post by jarkinber on 2010-05-31
sorry im a noob how do install it????

---

### Post by linuxopjemac on 2010-05-31
Reading from your former post it seems that you already tried to install 1.0.23...

> Thankyou macalan, i followed the instructions on that website very carefully, but it didn't work. the alsa version is still the same! everything seemed to work properly, but i still haven't got sound.

Try again. Note this:
> For Ubuntu change please &#8220;sudo make install&#8221; to &#8220;sudo checkinstall&#8221; or &#8220;sudo checkinstall -D &#8211;install=no&#8221;! There are other comments. Try to read them. You will get it to work I'm sure.

just edit the /etc/modprobe.d/alsa-base.conf file and add at the end:
```
options snd-hda-intel model=macmini3 power_save=10 power_save_controller=N
```

with:
```
sudo nano /etc/modprobe.d/alsa-base.conf
```
CTRL-X and "y" to save.

---

### Post by jarkinber on 2010-06-01
i tried that, didn't work. terminal says checkinstall: command not found
and same with the other commands so i just used make install again, but my driver version is still 1.0.22.1. thankyou for all your help so far! please tell me if you know anything else!

---

### Post by jarkinber on 2010-06-01
I tried those commands but terminal said it couldnt find command: checkinstall. i tried installing it again, but now it cant even find alsamixer now. ```
 $ alsamixer
cannot open mixer: No such file or directory 
```
i am soo confused about all of this!!
Thankyou everyone for all of your help and please continue because i really want to get my sound working.

---

### Post by ZeroLinux on 2010-06-01
> **jarkinber said:**
> i tried that, didn't work. terminal says checkinstall: command not found

sudo apt-get install checkinstall

BTW, Why do you try to install in a such complicated way?
Just do this:
1) Add repository: ppa:ubuntu-audio-dev/ppa
In terminal: sudo add-apt-repository ppa:ubuntu-audio-dev/ppa
Or through menu Software Sources 
2) Reload
In terminal: sudo apt-get update
3) Get to know you kernel 
In Terminal: uname -a
4) Install appropriate kernel
In Terminal: sudo apt-get install linux-alsa-driver-modules-2.6.32-22-generic (it was in my case I mean 2.6.32-22)
5) reboot
In Terminal: sudo shutdown -r now

if you want to have alsamixer back:
In terminal: sudo apt-get install alsa-utils

---

### Post by jarkinber on 2010-06-02
i don't understand what you mean by 'install appropriate kernel' but i tried all of this, nothing has changed, still 1.0.22.1. i even tried installing alsa mixer, but it said it was already installed, so i uninstalled it, re-enstalled it, still says mixer: command not found when i typed in alsamixer.
and when i used checkinstall, it failed installing. it got to installed deb file: failed. this is really annoying!! i hope this has worked for other people, but im not having any luck.

---

### Post by jarkinber on 2010-06-02
ok. ive decided to re-install ubuntu and give a fresh start because i think i may have tinkered with the files and will try again when i have a fresh install. Thanks Guys!

---

### Post by linuxopjemac on 2010-06-02
You might want to instal a linix 2.6.33 kernel from synaptics package manager,...

---

### Post by jarkinber on 2010-06-02
:)> **linuxopjemac said:**
> You might want to instal a linix 2.6.33 kernel from synaptics package manager,...
awesome. will do as soon as i can.

---

### Post by linuxopjemac on 2010-06-02
I think that the Mac Mini 3,1 has good audio as of 2.6.34...
[http://mac.linux.be/content/kernel-2634-released](http://mac.linux.be/content/kernel-2634-released)
> The Mac Mini 3,1 will have better sound support as well, it will have its own code in the ALSA configuration: macmini3.
[http://git.kernel.org/?p=linux/kernel/git/torvalds/linux-2.6.git;a=commitdiff;h=e458b1fadf9239d1fdb165ff4c4ea0d807041bec](http://git.kernel.org/?p=linux/kernel/git/torvalds/linux-2.6.git;a=commitdiff;h=e458b1fadf9239d1fdb165ff4c4ea0d807041bec)


If it is true what they say there, then the option mb5 would work too in etc/modprobe.d/alsa-base.conf

---

### Post by jarkinber on 2010-06-03
> **ZeroLinux said:**
> sudo apt-get install checkinstall

BTW, Why do you try to install in a such complicated way?
Just do this:
1) Add repository: ppa:ubuntu-audio-dev/ppa
In terminal: sudo add-apt-repository ppa:ubuntu-audio-dev/ppa
Or through menu Software Sources 
2) Reload
In terminal: sudo apt-get update
3) Get to know you kernel 
In Terminal: uname -a
4) Install appropriate kernel
In Terminal: sudo apt-get install linux-alsa-driver-modules-2.6.32-22-generic (it was in my case I mean 2.6.32-22)
5) reboot
In Terminal: sudo shutdown -r now

if you want to have alsamixer back:
In terminal: sudo apt-get install alsa-utils
Once i did this with a clean install, it worked!! My sound is working!!!! But i still dont know how to install the new kernel, but if someone could tell me that would be even better!!

---

### Post by jarkinber on 2010-06-03
Thread Solved! :)

---

### Post by linuxopjemac on 2010-06-03
Finally. Enjoy. It found a place on my [sound wiki]("http://mac.linux.be/content/sound-problems").

---

### Post by jarkinber on 2010-06-03
awesome thanks. Could you please tell me how install the latest kernel?

---

### Post by linuxopjemac on 2010-06-03
do you really need it ? Never change a winning team. If everything works, I would leave it as it is.

If you insist, choose a kernel from the synaptics package manager.

[https://help.ubuntu.com/community/SynapticHowto](https://help.ubuntu.com/community/SynapticHowto)

---

### Post by ZeroLinux on 2010-06-03
> **jarkinber said:**
> Thread Solved! :)
Pleasure to help.

---

### Post by ZeroLinux on 2010-06-03
> **jarkinber said:**
> But i still don't know how to install the new kernel, but if someone could tell me that would be even better!!
If you followed instructions you have the latest at the moment. It will be updated automatically, because you have a right repository added. You don't need to worry.

---

