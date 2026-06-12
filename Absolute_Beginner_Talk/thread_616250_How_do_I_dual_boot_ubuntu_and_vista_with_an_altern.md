---
title: "How do I dual boot ubuntu and vista with an alternate CD"
date: 2007-11-18
forum: Absolute Beginner Talk
---

### Post by bikerjeg on 2007-11-18
Ok so the Live CD version was not able to run on my system so I want to try to install ubuntu with the alternate CD. I tried searching for a tutorial but it doesn't seem anything is up to date with the latest version of ubuntu and the alternate CD version. My ultimate goal is to have a dual boot system with ubuntu running on a separate partition from my vista home premium. I have already used vista's utility to create some space for my ubuntu install and I have also defragged my hard disk. I have yet to try booting from the alternate cd since I read that it may delete Vista. Anyone know what I should do so I can avoid deleting vista and just installing on a separate partition which I have already prepared? Better yet is there a tutorial or guide out there that is up to date on dual booting and installing with an alternate cd?

---

### Post by meierfra on 2007-11-18
Check out [Hermanzone]("http://users.bigpond.net.au/hermanzone/")

---

### Post by bikerjeg on 2007-11-18
yeah thanks for that but I already installed and I had run into that tutorial previously very informative.

the only problem I am still trying to work around is that th GUI for ubuntu doesn't load. I tried installing with the Alternate CD because I was having the same issue with the Live CD not being able to load the GUI version. I now have linux installed but after I select it from the GRUB boot menu it starts loading but then it loads to a blank screen and nothing happens. I read this could be due to some display settings. I do have a widescreen laptop but how can I change the settings so ubuntu will load on my computer? In case it helps I'm trying to do the install on a Pavilion dv6470us

---

### Post by meierfra on 2007-11-18
I'm not an expert in this area, but you might try 

```
sudo dpkg-reconfigure xserver-xorg
```

This will ask you a bunch of questions. Just accept the defaults (unless you have a good reason not to)

As a video-driver choose "vesa". It's not a particular good driver, but it works in almost all cases.

---

### Post by louieb on 2007-11-18
> **bikerjeg said:**
> Better yet is there a tutorial or guide out there that is up to date on dual booting and installing with an alternate cd?

Just an FYI: the alternate CD uses the Debian installer its been around since before I started playing with Linux a couple of years ago and hasn't changed much.   The Illustrated dual boot link meierfra gave is a good one.

>  the only problem I am still trying to work around is that th GUI for ubuntu doesn't load.

If meierfra suggestion of sudo dpkg... doesn;t work might want to play with cheat codes. Heres a couple of lists.
[BootOptions - Ubuntu Documentation]("https://help.ubuntu.com/community/BootOptions")
[Cheat Codes - Knoppix Documentation Wiki]("http://www.knoppix.net/wiki/Cheat_Codes")

Good luck.

---

### Post by bikerjeg on 2007-11-18
> **meierfra said:**
> I'm not an expert in this area, but you might try 

```
sudo dpkg-reconfigure xserver-xorg
```

This will ask you a bunch of questions. Just accept the defaults (unless you have a good reason not to)

As a video-driver choose "vesa". It's not a particular good driver, but it works in almost all cases.

How do I configure this? I tried going into command line interface but it gives me an unrecognized command error

I also tried ctrl+ alt+f1 but that doesn't work and neither does escape once I am in the blank screen. I would like to know where I  should put the command in or how I can get into a command interface. Thanks

---

### Post by louieb on 2007-11-18
Do you get the GRUB menu?
What happens when you choose recovery mode?
You should get a prompt that look something like ```
root@computer#
```at that point what happens when you enter 
```
 dpkg-reconfigure xserver-xorg
```

(you are the root user at this point so you don't need sudo)
Yes it will ask some questions for the most part just accept the default.  
When the video questions come up choose vesa  when  your finished type ```
reboot
``` and see what happens.

---

### Post by bikerjeg on 2007-11-18
yes I get the grub menu but when I choose the recovery mode it just gets stuck loading when it's checking for hardware drivers.

I tried entering c at the grub menu which took me to some kind of command interface but it gave me an error 27 saying that the command was not recognized. Is there another way I can get into the command interface you are referring to?

---

### Post by louieb on 2007-11-19
When you entered **c** at the grub menu that take you to the GRUB prompt. That is a place to enter GRUB command only - not what you need.

The computer hanging when you select recovery mode is not good news.  Just wondering did you get any error messages during the install. Like > some file being corrupted - do you want to continue?IF yes then you need to burn another CD and try the install again. 
If not then unplug any USB devices and try again, 
If that doesn't work  then  Ubuntu Linux is probably not going to work on that computer. 
The only other thing I can suggest is to try some different boot options
[BootOptions - Ubuntu Documentation]("https://help.ubuntu.com/community/BootOptions")
[Cheat Codes - Knoppix Documentation Wiki]("http://www.knoppix.net/wiki/Cheat_Codes") 

Ubuntu has good hardware detection,  but sometimes fails. Try Knoppix or DSL. Both like Ubuntu are Debian based and IMHO are better at hardware detection. At least you'll find if Linux can run on your PC.

---

### Post by bikerjeg on 2007-11-19
i'm pretty sure I did not get any errors during the install.

the same thing happens when I try running the livecd too. is there any way to boot from the live cd and enter the command terminal and try fixing it?

I'm really lost as to what I can do or why the install does not work.

---

