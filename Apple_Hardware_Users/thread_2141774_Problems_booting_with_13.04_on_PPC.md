---
title: "Problems booting with 13.04 on PPC"
date: 2013-05-03
forum: Apple Hardware Users
---

### Post by canhoto on 2013-05-03
Hi. I've been trying to load live cd's with 13.04 on my PowerPC  mac. I've tried with Kubuntu and Lubuntu lice cd's. However, after the splash  screen, booting freezes on a black screen with some messages, where the  last one states "Stoping mount network filesystems". 

The only thing I can do is to enter a terminal prompt with Ctrl+Alt+F1.

I currently have  Kubuntu 12.04 installed on the machine, and that works well. I should add that the same problem has happened once when I tried to upgrade from 12.04 to 12.10 (which, at that time, forced me to reinstall 12.04).

Any help?

---

### Post by michiganmac on 2013-05-03
> **canhoto said:**
> Hi. I've been trying to load live cd's with 13.04 on my PowerPC  mac. I've tried with Kubuntu and Lubuntu lice cd's. However, after the splash  screen, booting freezes on a black screen with some messages, where the  last one states "Stoping mount network filesystems". 

The only thing I can do is to enter a terminal prompt with Ctrl+Alt+F1.

I currently have  Kubuntu 12.04 installed on the machine, and that works well. I should add that the same problem has happened once when I tried to upgrade from 12.04 to 12.10 (which, at that time, forced me to reinstall 12.04).

Any help?

Lubuntu 13.04 PPC requires one to enter boot parameters at the yaboot prompt in order to boot the Live CD, depending on the video card you're running. I have booted it successfully with Radeon cards in a Sawtooth, MDD and iBook G4. What video card are you running? 

FYI, so far, I have been unsuccessfull in booting regular Ubuntu 13.04 on any of my Powermacs.

---

### Post by canhoto on 2013-05-03
> **michiganmac said:**
>  What video card are you running? 


I have a NVIDIA GeForce 6200. What boot parameters should I insert?

---

### Post by michiganmac on 2013-05-04
> **canhoto said:**
> I have a NVIDIA GeForce 6200. What boot parameters should I insert?

OK, here's what works on my Sawtooth, with an nVidia gForce4 MX 64MB card installed. I used a usb flash drive attached to a USB 2 PCI card, and was connected to the internet via ethernet cable. I don't know if it will work for your nVidia card--that's a flashed pc card, right? Anyway, I just verified it works with mine. I was able to boot to the live desktop and everything ran normally. 

I got some of this from the "Known Problems" wiki. 

At the yaboot prompt, type:

     live video=offb:off nouveau.modeset=0 single

This will freeze the screen or give a blank screen. Mine freezes at the screen when the video card is recognized. That's ok. You have to judge when the machine has finished booting, which can be longer than you think. I waited until the flash drive stoppped blinking fast for at least 60 seconds. For the next step, you will not be able to see what you're typing, so take it slow so you make no mistakes.

Now type:

     modprobe nvidiafb mode_option=1920x1080-32

Substitute your monitor's screen resolution (where I typed 1920x1080-32). When you hit the return key, you will find yourself in a terminal screen. 

Now type this:

     start lightdm

In 30 seconds or so, you should be looking at the booted desktop.

I know this sounds complicated, but it's really only three steps:

     live video=offb:off nouveau.modeset=0 single

     modprobe nvidiafb mode_option=1920x1080-32

     start lightdm

This worked perfectly for me. I hope it works for you. Please let us know. Good luck!

---

### Post by gusduenas on 2013-05-04
Ok Michigan Mac, I did as you told here and it went ok.
I put my resolution 1680x1050-32 it says is a 32 bit color so I went direct to the start screen and then to the desktop, everything good so far, but I cannot install the system. Even though I have an extra internal hd with 150GB of free space (the original HD of the g5 i have)
I have a g5 dual 2.0ghz 1gb memory and nvidia geforce 6600 PCIe so what is making this program don't want to install it? someone help me :(

Gus

---

### Post by michiganmac on 2013-05-04
> **gusduenas said:**
> Ok Michigan Mac, I did as you told here and it went ok.
I put my resolution 1680x1050-32 it says is a 32 bit color so I went direct to the start screen and then to the desktop, everything good so far, but I cannot install the system. Even though I have an extra internal hd with 150GB of free space (the original HD of the g5 i have)
I have a g5 dual 2.0ghz 1gb memory and nvidia geforce 6600 PCIe so what is making this program don't want to install it? someone help me :(

Gus

Hi Gus. I'm sorry, but the instructions I wrote above are what worked for me when installing Lubuntu 13.04 on a Powermac G4. I don't have a G5, or any experience on a G5. Hopefully, someone else will be able to help you with that.

---

### Post by gusduenas on 2013-05-04
thanks man, but do install lubuntu on the mac g4...but why it is stalling or not even completing the installation on mac g5.... strange ins't.

---

### Post by canhoto on 2013-05-04
> **michiganmac said:**
> OK, here's what works on my Sawtooth, with an nVidia gForce4 MX 64MB card installed. I used a usb flash drive attached to a USB 2 PCI card, and was connected to the internet via ethernet cable. I don't know if it will work for your nVidia card--that's a flashed pc card, right? Anyway, I just verified it works with mine. I was able to boot to the live desktop and everything ran normally. 

I got some of this from the "Known Problems" wiki. 

At the yaboot prompt, type:

     live video=offb:off nouveau.modeset=0 single

This will freeze the screen or give a blank screen. Mine freezes at the screen when the video card is recognized. That's ok. You have to judge when the machine has finished booting, which can be longer than you think. I waited until the flash drive stoppped blinking fast for at least 60 seconds. For the next step, you will not be able to see what you're typing, so take it slow so you make no mistakes.

Now type:

     modprobe nvidiafb mode_option=1920x1080-32

Substitute your monitor's screen resolution (where I typed 1920x1080-32). When you hit the return key, you will find yourself in a terminal screen. 

Now type this:

     start lightdm

In 30 seconds or so, you should be looking at the booted desktop.

I know this sounds complicated, but it's really only three steps:

     live video=offb:off nouveau.modeset=0 single

     modprobe nvidiafb mode_option=1920x1080-32

     start lightdm

This worked perfectly for me. I hope it works for you. Please let us know. Good luck!

Great! It worked!

I was really astonished about how quick Lubuntu can be - even when running from a CD!

The question is: if I install it, will I have to make all this at each boot?

Thanks!

---

### Post by gusduenas on 2013-05-04
hey let me know if you can install it, so far the installer crashes at 88% of the files being copied, using Kubuntu 13.04 on g5 ppc with nvidia geforce 6600 256mb, also rekong crashes too, and firefox is not installing...any ideas, let me know if you can install it.

---

### Post by michiganmac on 2013-05-04
> **canhoto said:**
> Great! It worked!

I was really astonished about how quick Lubuntu can be - even when running from a CD!

The question is: if I install it, will I have to make all this at each boot?

Thanks!

Great! Glad to see it worked. 

I've never done a full install on the Sawtooth with the nVidia card. I've only done full installs with Radeon 9000 Pro and Radeon 9800 Pro cards. I only installed the nVidia card to test the live CD for you. 

With Radeon cards, once the full installation is done, the computer boots normally with no extra boot parameters needed. I think it will work the same way for the nVidia cards, but I can't say for sure because I haven't actually done it. So, you'll just have to try it and see.

If you go ahead with the full installation, check the option box that allows the installer to automatically download updates from the internet while it is doing the installation. If it works for you, let us know, and then mark the thread as solved.

Nice job, and good luck with the full installation!

---

### Post by gusduenas on 2013-05-04
any ideas why the installer crashes at 80% and why rekong crashes?

Gus

---

### Post by canhoto on 2013-05-05
> **gusduenas said:**
> any ideas why the installer crashes at 80% and why rekong crashes?

Gus

I didn't try to install Kubuntu 13.04 yet. But I noticed that rekonq crashes even from the live cd.
I never use Rekonq (I use Firefox), but maybe you should check the logs.

---

### Post by canhoto on 2013-05-05
> **michiganmac said:**
> Great! Glad to see it worked. 

I've never done a full install on the Sawtooth with the nVidia card. I've only done full installs with Radeon 9000 Pro and Radeon 9800 Pro cards. I only installed the nVidia card to test the live CD for you. 

With Radeon cards, once the full installation is done, the computer boots normally with no extra boot parameters needed. I think it will work the same way for the nVidia cards, but I can't say for sure because I haven't actually done it. So, you'll just have to try it and see.

If you go ahead with the full installation, check the option box that allows the installer to automatically download updates from the internet while it is doing the installation. If it works for you, let us know, and then mark the thread as solved.

Nice job, and good luck with the full installation!

Ok, I'll try that later today and I will let you know. Btw, how do you mark the thread as solved with this new design of the forums? I tried that with a previous post and I couldn't find the way to do it. I thought it was in the "thread tools", but apparently not.

---

### Post by gusduenas on 2013-05-05
> **canhoto said:**
> Ok, I'll try that later today and I will let you know. Btw, how do you mark the thread as solved with this new design of the forums? I tried that with a previous post and I couldn't find the way to do it. I thought it was in the "thread tools", but apparently not.
Let me know if suceed, so far rekong crashes and firefox didn't install at all....stuck without installing anything.....any Help will be appreciated

---

### Post by gusduenas on 2013-05-05
well at this time I cannot get the installation, don't you know how can I get the logs to see what is wrong with it also do you why it this thing didn't let me to do the installation? pretty weird right?

---

### Post by gusduenas on 2013-05-05
BTW firefox finally installed and I'm writing from it.

---

### Post by canhoto on 2013-05-05
> **michiganmac said:**
> Great! Glad to see it worked. 

I've never done a full install on the Sawtooth with the nVidia card. I've only done full installs with Radeon 9000 Pro and Radeon 9800 Pro cards. I only installed the nVidia card to test the live CD for you. 

With Radeon cards, once the full installation is done, the computer boots normally with no extra boot parameters needed. I think it will work the same way for the nVidia cards, but I can't say for sure because I haven't actually done it. So, you'll just have to try it and see.

If you go ahead with the full installation, check the option box that allows the installer to automatically download updates from the internet while it is doing the installation. If it works for you, let us know, and then mark the thread as solved.

Nice job, and good luck with the full installation!

Well, unfortunately it doesn't boot. I did the full clean installation of Lubuntu. I rebooted and, after a short blank screen (the one that you have when you start from the live cd with the booting parameters), then some messages on a black screen and finally... a black screen. It's all that I have now. I can't even write the boot parameters at booting, I think I don't have a choice to do it. Any help?

---

### Post by canhoto on 2013-05-06
> **michiganmac said:**
> Great! Glad to see it worked. 


With Radeon cards, once the full installation is done, the computer boots normally with no extra boot parameters needed. I think it will work the same way for the nVidia cards, but I can't say for sure because I haven't actually done it. So, you'll just have to try it and see.



Can you tell me what do you have in yaboot.conf? Do you have any special boot options regarding the graphics card?

I tried to change the yaboot.conf file with the booting parameters of the live cd (well, adapting them) but I always end up with the blank screen where you can write "blind" with the live cd, but where nothing happens. My lest trial was removing all special parameters from yaboot.conf (running ybin -v afterwards), but I still have the white screen.

---

### Post by canhoto on 2013-05-06
.

---

### Post by michiganmac on 2013-05-06
> **canhoto said:**
> Can you tell me what do you have in yaboot.conf? Do you have any special boot options regarding the graphics card?

I tried to change the yaboot.conf file with the booting parameters of the live cd (well, adapting them) but I always end up with the blank screen where you can write "blind" with the live cd, but where nothing happens. My lest trial was removing all special parameters from yaboot.conf (running ybin -v afterwards), but I still have the white screen.

I only have experience booting the live CD with a nVidia card in the Sawtooth. Remember, that was your original question. I have no experience with a full install--except with a radeon card. So, this is technically "above my pay grade". 

However, I did some checking and there may be a workaround for your problem on this page:

[https://help.ubuntu.com/community/Lubuntu/Documentation/FAQ/PPC](https://help.ubuntu.com/community/Lubuntu/Documentation/FAQ/PPC)

Read through the workaround. I think you could start at Step #3 because you already have a complete installation. This is what I would try, but I don't like giving recommendations for things I haven't actually performed myself. 

As always, if you attempt this, please report what you find. Good luck.

---

### Post by michiganmac on 2013-05-06
I just noticed the link in Step 6 of the work-around points to a blank page. Without it, the work-around isn't going to help. I reported the problem to the lubuntu-qa mailing list. Hopefully, someone on there can fix it.

---

### Post by canhoto on 2013-05-06
> **michiganmac said:**
> I just noticed the link in Step 6 of the work-around points to a blank page. Without it, the work-around isn't going to help. I reported the problem to the lubuntu-qa mailing list. Hopefully, someone on there can fix it.

Yes, I noticed. I created a Xorg.conf file with the basic parameters, even so. I ended up with just a splash screen, then nothing (not even the ability to go to a CLI with Ctrl+Alt+F1). Then I added ```
nouveau.modeset=0
``` to the yaboot.conf to see if it changed anything, but it didn't.

So, I think I will wait for the fixing of the link you suggested, my last chance before giving up and returning to good old 12.04.

Anyway, thanks for your great help! If you have any news about the broken link, please tell me.

---

### Post by canhoto on 2013-05-06
I removed everything from yaboot.conf (except "quiet splash"). I disabled 3d acceleration in xorg.conf and replaced the "nouveau" driver for a "fbdev" one.
Still the same. Afterwords I set the driver to be "nouveau" again, keeping the 3d acceleration disabled.

Nothing changed: I have a pretty splash screen and then a "no signal" message on my monitor.

---

### Post by str8bs on 2013-05-07
@ michiganmac Kudos for going above and beyond trying to help a fellow community member!

@ canhoto A couple things you could try.

I don't currently know of a workaround to get nouveau working with acceleration. There have been a lot of upstream changes lately. If that is important to you, you may want to stick with 12.04 for now.

Following on the method michiganmac suggested to boot the live installer from where I think you are now:
1. Remove "splash quiet" from yaboot appends. This won't fix anything, buy you may be able to glimpse an error message before it goes blank.
2. Remove any xorg.conf files created.
3. Follow [this link]("https://wiki.ubuntu.com/PowerPCFAQ#How_do_I_load_a_kernel_module.3F") and replace the line "radeonfb mode_option=1024x768-32@60" with "nvidiafb mode_option=whatever resolution you used to boot the installer"
I would go all the way through the steps to sudo update-initramfs -u as that will give you your screen sooner. (If it works. :) )
4. Boot with ```
Linux video=offb:off nouveau.modeset=0
```
If that works, you can append the commands to yaboot.

Alternatively, If you can boot to a GUI but just poor color using video=ofonly nouveau.modeset=0, you should be able to create a simple xorg.conf using FBDEV.
Good luck.

---

### Post by canhoto on 2013-05-07
> **str8bs said:**
> @ michiganmac Kudos for going above and beyond trying to help a fellow community member!

@ canhoto A couple things you could try.

I don't currently know of a workaround to get nouveau working with acceleration. There have been a lot of upstream changes lately. If that is important to you, you may want to stick with 12.04 for now.

Following on the method michiganmac suggested to boot the live installer from where I think you are now:
1. Remove "splash quiet" from yaboot appends. This won't fix anything, buy you may be able to glimpse an error message before it goes blank.
2. Remove any xorg.conf files created.
3. Follow [this link]("https://wiki.ubuntu.com/PowerPCFAQ#How_do_I_load_a_kernel_module.3F") and replace the line "radeonfb mode_option=1024x768-32@60" with "nvidiafb mode_option=whatever resolution you used to boot the installer"
I would go all the way through the steps to sudo update-initramfs -u as that will give you your screen sooner. (If it works. :) )
4. Boot with ```
Linux video=offb:off nouveau.modeset=0
```
If that works, you can append the commands to yaboot.

Alternatively, If you can boot to a GUI but just poor color using video=ofonly nouveau.modeset=0, you should be able to create a simple xorg.conf using FBDEV.
Good luck.

Great! Now it's up and running! Thank you!
Just one tiny question: where in the yaboot.conf file should I add the parameters?

---

### Post by str8bs on 2013-05-07
> **canhoto said:**
> Great! Now it's up and running! Thank you!
Just one tiny question: where in the yaboot.conf file should I add the parameters?

Good work! Put whatever you are typing after Linux at the boot: prompt in the append section. Same place you saw "quiet splash"  and then sudo ybin -v.
Enjoy 13.04.

---

### Post by gusduenas on 2013-05-08
hi how can I make a simple xorg.conf file for a geforce 6600 in a mac g5?

Gus

Please forgive me for bothering you guys but i'd love to have kubuntu up and running installed on my g5

---

### Post by str8bs on 2013-05-08
> **gusduenas said:**
> hi how can I make a simple xorg.conf file for a geforce 6600 in a mac g5?

Gus

Please forgive me for bothering you guys but i'd love to have kubuntu up and running installed on my g5

If after install, you CAN boot into low color using video=ofonly nouveau.modeset=0, press <ctl><alt><F1> to get to a prompt and login.
sudo nano /etc/X11/xorg.conf
make it look like this:
```

     Section "Device"
     Identifier "GoofyApple"
     Driver "FBDEV"
     EndSection

     Section "Monitor"
     Identifier "Wonka"
     EndSection

     Section "Screen"
     Identifier "Willy"
     Monitor "Wonka"
     DefaultDepth 24
     EndSection
```

press <ctl><o> and enter to save, then <ctl><x> to exit back to prompt
sudo shutdown -r now

---

### Post by gusduenas on 2013-05-08
Hi Man, I have a problem right now, I have the Kubuntu 13.04 installed and it won't boot to my osx at all, it will redirects me again to the yaboot screen...do you know why is that?
and this time if a type the l on the yaboot and linux in the other prompt I will go directly to the black screen, so do you think that maybe doing the Kernel thing and the xorg.conf is the way to go and once I have this thing made it will boot again to osx...thanks.

Gus

---

### Post by str8bs on 2013-05-09
@gusduenas 
With all due respect, I recommend you pick a single thread, preferably your own, and work through the issues. It is unlikely that others are going to read through multiple threads and be able to determine the state of you installation and what steps you have taken. It also makes it difficult for others to read through threads that have unrelated information sprinkled throughout. Please review the section on posting tips here. [http://ubuntuforums.org/misc.php?do=showrules](http://ubuntuforums.org/misc.php?do=showrules)

You can also find many questions answered in [https://wiki.ubuntu.com/PowerPCFAQ](https://wiki.ubuntu.com/PowerPCFAQ) and [https://wiki.ubuntu.com/PowerPCKnownIssues](https://wiki.ubuntu.com/PowerPCKnownIssues)

Good luck.
Str8

---

### Post by michiganmac on 2013-05-18
> **canhoto said:**
>  <snip> Btw, how do you mark the thread as solved with this new design of the forums? I tried that with a previous post and I couldn't find the way to do it. I thought it was in the "thread tools", but apparently not.

I just started a new thread, and I noticed there is a "Prefix" box right above the topic entry area. Clicking on that box reveals a menu of options, one of which is "mark solved". I'm just guessing, but it is probably only visible to the person whom started the thread.

---

