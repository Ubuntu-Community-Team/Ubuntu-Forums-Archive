---
title: "LINUX newbie screwd up ubuntu 7.04 with nvidia drivers instal :p advice required"
date: 2007-09-02
forum: Absolute Beginner Talk
---

### Post by xtzc on 2007-09-02
so,i instaled ubuntu 7.04 on my pc yesturday and today i,ve tryed to install the nvidia driver so i can install the beryl gui(please excuse me if i'll get the termes mixed up..like i said ..linux newbie here;)) )
found the tutorial on how to instal the drivers on some webpage(if its alowed ill post it)did what it sayd and after that i restarted my pc and when it tryed to boot up ubuntu i got a blue screen with gibberish on the sides and in the middle of the screen some sord of message that told me : x server is configured wrong..
now i'm stuck at this...

anyone please give some advice in newb terms..
i'll give a beer:))
regards

---

### Post by Paul820 on 2007-09-02
You need to ask in the beginners section of the forums, you will get answered there rather than testimonials. Linky: [http://ubuntuforums.org/forumdisplay.php?f=73]("http://ubuntuforums.org/forumdisplay.php?f=73")

---

### Post by Technophobia on 2007-09-02
when you get the blue screen hit ctrl+alt+f2

type 

sudo dpkg-reconfigure xserver-xorg

pick your settings

reboot

---

### Post by xtzc on 2007-09-03
tried that and still doesnt work,at the firs conf screen i have to select the chipset used,tried nvidia and then i tried nv i thought it might work bcause my 6600 has a nv43 gpu,the next settings were about monitor,keybord and mouse..
anyone any ideas???
i have a leadtek a6600gt tdh 20'th anniversary edition 128Mb gddr3 128 bits..
tnx alot

---

### Post by agemon on 2007-09-03
i install nvidia driver by 'following the following' :
> 
If you wish to install the NVIDIA Linux graphics driver on a Debian GNU/Linux or Ubuntu system that ships with Xorg 7.x, please ensure that your system meets the following requirements:

    * development tools like make and gcc are installed (use sudo apt-get install build-essential)
    * the linux-headers package matching the installed Linux kernel is installed
    * the pkg-config and xserver-xorg-dev packages are installed
    * the nvidia-glx package has been uninstalled with the --purge option and the files /etc/init.d/nvidia-glx and /etc/init.d/nvidia-kernel do not exist

If you use Ubuntu, please also ensure that the linux-restricted-modules or linux-restricted-modules-common packages have been uninstalled. Alternatively, you can edit the /etc/default/linux-restricted-modules or /etc/default/linux-restricted-modules-common configuration file and disable the NVIDIA linux-restricted kernel modules (nvidia, nvidia_legacy) via:

    DISABLED_MODULES="nv nvidia_new"

Additionally, delete the following file if it exists:

    rm -f /lib/linux-restricted-modules/.nvidia_new_installed


then run sudo ./NVIDIA-dirver-blablabla
and it has worked every time.
You can try to restore the xorg.conf.backup from /etc/X11 
```

sudo cp /etc/X11/xorg.conf.backup /etc/X11/xorg.conf

```
And if it doesn't work, make 'a backup to the backup': 
```

sudo cp /etc/X11/xorg.conf.backup /etc/X11/xorg.conf-mybackup

```
follow the instructions again and reinstall the driver (you can also try deleting xorg.conf before reinstalling, but make sure you have the backup).
Hope it helps && best of luck !

---

### Post by xtzc on 2007-09-03
tnx.i'm tring this right away..will post back in a few mins with the result..
regsrds

---

### Post by hyper_ch on 2007-09-03
The restricted driver manager did not help?

---

### Post by xtzc on 2007-09-03
i started ubuntu
 got the blue screen
crtl alt f2 ,loggent in as root
this comand doesnt work(nothing happens)  rm -f /lib/linux-restricted-modules/.nvidia_new_installed

rstore comand does nothing

sudo cp /etc/X11/xorg.conf.backup /etc/X11/xorg.conf

this alsaw does nothing..

sudo cp /etc/X11/xorg.conf.backup /etc/X11/xorg.conf-mybackup

i tjink i hav to resintal all over:(

---

### Post by agemon on 2007-09-03
the commands shouldn't say anything, i think you can try reinstalling the driver now:
from the folder that you have downloaded it:
```

sudo ./NVIDIA-Linux-x86_64-100.14.11-pkg2.run (replace this with the actual name)

```
or, of course, you can reinstall the whole system, your choice (but that probably won't help much you'll still have to install the nvidia driver)...

---

### Post by eye208 on 2007-09-03
> **xtzc said:**
> found the tutorial on how to instal the drivers on some webpage(if its alowed ill post it)did what it sayd and
Those tutorials are causing more harm than good these days. In Ubuntu 7.04 both the proprietary video drivers and Beryl can be activated with just a few mouse clicks. Unless your video card is very special or requires the very latest drivers, there is no need to touch the command line at all.

---

### Post by agemon on 2007-09-03
> **eye208 said:**
> Those tutorials are causing more harm than good these days. In Ubuntu 7.04 both the proprietary video drivers and Beryl can be activated with just a few mouse clicks. Unless your video card is very special or requires the very latest drivers, there is no need to touch the command line at all.
umm.. i don't know about your card, but if i don't have the drivers installed, not even ubuntu's default desktop efects won't work :confused:, and i have a nvidia 7300 gt
anyway, the tutorial i have posted earlier was from the nvidia forums:
[http://www.nvnews.net/vbulletin/showthread.php?t=72490](http://www.nvnews.net/vbulletin/showthread.php?t=72490)

---

### Post by xtzc on 2007-09-03
i reinstaled ubuntu.:) seemed much easyer than to mess my head up with all those long string comands:)..still looking 4 a way to install my A6600 gt tdh...if anyone knows the GOOD way to do it please post it..
regards

---

### Post by eye208 on 2007-09-03
> **agemon said:**
> umm.. i don't know about your card, but if i don't have the drivers installed, not even ubuntu's default desktop efects won't work :confused:, and i have a nvidia 7300 gt
anyway, the tutorial i have posted earlier was from the nvidia forums:
[http://www.nvnews.net/vbulletin/showthread.php?t=72490](http://www.nvnews.net/vbulletin/showthread.php?t=72490)
I have a GeForce 7 too (7900 GS). I installed the driver and switched to Beryl using the tools provided in the system menu. There was no need to touch the command line.

I know it _can_ be done using the command line as well. But why confuse new users right from the start? It's no surprise many people still consider Linux "difficult" with all those tutorials around. IMHO the easiest ways to achieve things should be pointed out foremost, because the first impression is a lasting one.

---

### Post by hyper_ch on 2007-09-03
> **xtzc said:**
> i reinstaled ubuntu.:) seemed much easyer than to mess my head up with all those long string comands:)..still looking 4 a way to install my A6600 gt tdh...if anyone knows the GOOD way to do it please post it..
regards

Did you try the restricted driver manager?

---

### Post by xtzc on 2007-09-03
its fine now,agemon asisted me though the whole process...nvidia drivers are instaled and working.
tnx alot guyz..

---

### Post by overdrank on 2007-09-03
> **xtzc said:**
> its fine now,agemon asisted me though the whole process...nvidia drivers are instaled and working.
tnx alot guyz..

Hi glad to hear you have it working but could you post what you did to correct it so that others may learn from it? Thanks :)

---

### Post by xtzc on 2007-09-03
whoooaa..i dont even know where to start...agemon passed all the comands..i'l ask him to post tthe exact procedure:P
regards

---

### Post by agemon on 2007-09-03
hello, the comands are from my previous post: they can be found on the nvidia forums here: [http://www.nvnews.net/vbulletin/showthread.php?t=72490](http://www.nvnews.net/vbulletin/showthread.php?t=72490)
i think this thread can be closed (or marked as solved). 10x !
:popcorn:

---

