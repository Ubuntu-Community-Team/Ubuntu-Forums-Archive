---
title: "Really Need help"
date: 2007-03-06
forum: Absolute Beginner Talk
---

### Post by nevertheless on 2007-03-06
Hey, I'm really new to the linux based system and everything else. I'm at the beggining of the process also. I want to try the live cd on my computer but it won't work. I'm sure my computer can handle it to because I have a good processor (AMD) and 3 gigs of RAM but I must be doing something wrong. 
             I burned the iso file on a cd and nothing happens when a reboot my computer. What am I doing wrong. Also when I get to load up ubuntu on my computer can somebody tell me how to install beryl(twirling of the cube...etc.) and use windows xp and ubuntu at the same time. I read alot of these posts but I really don't understand it. Somebody help, I would really appreciate it!!!
(I know I'm a newb, you don't have to tell me)

---

### Post by HasratUSA on 2007-03-06
Change your BIOS settings and make it to boot from your CD/DVD drive. Hit F12 or whatever key it tells you to press during boot-up to enter the bios settings page.

---

### Post by halitech on 2007-03-06
ok, first, which version did you download? (live cd, alternate install cd, dvd version?)

2. what sped did  you burn the cd at?

3. is your system set to boot from the cd?

far as beryl goes, wait till you get the system running first. gotta learn to walk before you can run ;)

---

### Post by dasunst3r on 2007-03-06
It sounds like you burned a CD containing the .iso file.  What you should do is to use your CD burning program's "burn image" command to burn the CD.

---

### Post by nevertheless on 2007-03-06
ummmm I think I downloaded the live CD. I went to ubuntu.com and went to the newest release and downloaded from north america and it came out to be an iso file
2. I'm burning at 40X
3. How do you set it to boot from cd??
Thanx for all the help I really appreciate it

---

### Post by Duck2006 on 2007-03-06
> I'm burning at 40X

Try burning at X4

---

### Post by newlinux on 2007-03-06
before you go any further you need to confirm that you downloaded tand properly burned he right .iso (live CD). Then make sure you burned the CD properly. what program are you using to burn the CD? Make sure you are burning the iso as the CD as opposed to burning the iso to the CD as a file. Burn it slowly to make sure it writes nicely. Once you have those done for sure - and if you find it still does nothing, take a look at your BIOS settings. BIOS are often different in exact layout, so it will be hard for anyone without your computer to give you explicit instructions. You'll probably need to look for a boot menu or something similar, and set it to boot from CD first.

---

### Post by nevertheless on 2007-03-06
Ok...I am now running ubuntu from my live CD... I was burning the actual file...OOPS
Now that I've got this running smoothly can somebody tell me how to install beryl and which one to install
(nvidia gforce graphics card 256 mb) Thanks again

---

### Post by Amenemhet on 2007-03-06
Be warned...beryl is still beta, ie: use at your own risk...I have quite a few mates who love it...alas they are re-installing once a week...

---

### Post by HasratUSA on 2007-03-06
> **Amenemhet said:**
> Be warned...beryl is still beta, ie: use at your own risk...I have quite a few mates who love it...alas they are re-installing once a week...

Are they reinstalling once a week beryl or the whole OS? :confused:

---

### Post by nevertheless on 2007-03-06
Yea I've read the forums and I see it's still in process to becoming a final release. I'm willing to take the risk. I also want to partition my hardrive to have windows xp still installed too. I know I'm asking for to much at one time but I just want to install beryl and work from there.
Any help would be great

---

### Post by jem7v on 2007-03-06
XFCE 4.4 (i.e., the real thing, not the version included in Xubuntu 6.06 and 6.10 but which will be in the Xubuntu 7.04 release 6 weeks from now...) has video compositing installed already for pretty transparent windows and the likes, but it doesn't do the wobble or all the ridiculous plugins associated with Compiz and Beryl. I prefer it very much for that reason, and also because it works consistently for me... and I'm running an old system. 750mhz Duron, 384mb ram, Geforce2 MX 400 32mb with the non-legacy NVidia driver.  I never got window transparency to work Properly in Compiz with this machine, but it runs fine in XFCE.

It might be a simpler option for a beginner than trying to set up Beryl or Compiz, since it's already mostly set up... you just have to turn it on and make sure you have the proper video drivers installed.

(You'd also probably want to wait 6 weeks for Xubuntu 7.04 to come out proper instead of running a Beta of it or compiling XFCE 4.4 manually in 6.06/6.10)


(And in case you're wondering what I'm talking about with XFCE:
Ubuntu = Ubuntu Linux + Gnome Desktop
Kubuntu = Ubuntu Linux + KDE Desktop
Xubuntu = Ubuntu Linux + XFCE Desktop)

---

### Post by maniacmusician on 2007-03-06
> **nevertheless said:**
> Yea I've read the forums and I see it's still in process to becoming a final release. I'm willing to take the risk. I also want to partition my hardrive to have windows xp still installed too. I know I'm asking for to much at one time but I just want to install beryl and work from there.
Any help would be great

There is a guide at wiki.beryl-project.org. However, that's a little confusing sometimes, so I wrote my own little guide that you can follow if you'd like. 

However, you have to install the proprietary drivers first. you can use the envy script created by Albert Milone ([http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html) ).

After you do that, I'll post up my little beryl how-to.

PS: may I ask, why you're using Xubuntu? Do you have an excessively slow machine? Don't get me wrong, Xubuntu is a great system, but for newbies, I usually direct them to more full-fledged DEs like Gnome or KDE.

---

### Post by nevertheless on 2007-03-06
I went to the site you provided and it says error or something. I'm really not sure what I'm suppose to download there. Were are the download link located at?

---

### Post by nevertheless on 2007-03-06
I'm using ubuntu not xubuntu. I installed this because this was the only one I really about.
P.S. My computer is defnately not slow. Pretty much up to the tee when it comes to tecnology.

---

### Post by maniacmusician on 2007-03-06
[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

Are you saying that link doesn't work for you? It's working perfectly for me. From that page, you're supposed to download the Envy script, which will install the nvidia drivers for you.

thanks for the clarification on what you're using; I dunno why I assumed you were using Xubuntu. I guess the long days are catching up with me :)

But yeah, that link should be working. You need to install nvidia drivers with the Envy script located on that page.

edit: If you still can't access that page, try this direct link to the file: [http://albertomilone.com/ubuntu/nvidia/scripts/envy_0.9.0-0ubuntu1_all.deb](http://albertomilone.com/ubuntu/nvidia/scripts/envy_0.9.0-0ubuntu1_all.deb)

The installation should go fine, but it may wipe out your GUI; certain amount of risk with every step, I suppose. If it does wipe out your GUI, make sure you have a text-based browser to help you get around. (To install a text-based browser, use this command: sudo apt-get install links2            To use the text based browser after installing it, use this command: links2)

---

### Post by nevertheless on 2007-03-06
Ok I just installed it. Everything worked fine. Now whats the next step. 
The suspense is killing me!!!

---

### Post by maniacmusician on 2007-03-07
sorry I got engaged in another thread. So many people with wireless problems! Here is my little guide to Beryl. I don't know if anyone's tried it yet, but it looks foolproof to me :) I guess you're the guinea pig. Make sure you read all the directions carefully.

If you want a **stable** Beryl, follow Step 1. and then Step 3. If you want the **bleeding edge** Beryl (updated every few days, sometimes every day), follow steps 2 and 3. **Warning: Steps 1 and 2 are exclusive of each other. You must pick one of them, you can't do them both.**  Also, this is for Edgy Eft. It probably won't work on Dapper Drake or Feisty Fawn.

Step One:
> 
Add the following repository to /etc/apt/sources.list:
[QUOTE]deb [http://ubuntu.beryl-project.org/](http://ubuntu.beryl-project.org/) edgy main
Then add the keys for the repos:
> sudo echo && wget [http://ubuntu.beryl-project.org/root@lupine.me.uk.gpg](http://ubuntu.beryl-project.org/root@lupine.me.uk.gpg) -O- | sudo apt-key add -
Then, 
> sudo apt-get update && sudo apt-get dist-upgrade
And then, 
> sudo apt-get install beryl emerald emerald-themes
[/QUOTE]

Step Two (Unstable Beryl)
> 
Add the following repositories to /etc/apt/sources.list:
[QUOTE]deb [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) edgy beryl-svn
deb-src [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) edgy beryl-svn

Then add the keys for the repos,
> wget [http://download.tuxfamily.org/3v1deb/DD800CD9.gpg](http://download.tuxfamily.org/3v1deb/DD800CD9.gpg) -O- | sudo apt-key add -
Then,
> sudo apt-get update && sudo apt-get dist-upgrade
And then, 
> sudo apt-get install beryl emerald emerald-themes
[/QUOTE]

Step Three (Configuring your system to optimize Beryl)
> 
Open /etc/X11/xorg.conf. Find Section "Modules" and put a # in front of dri like so:
[QUOTE]Section "Module"
 ....
#             Load    "dri"
....
EndSection

Find the Section "device" (where your driver is) further down in the document, and add these two options:
> Section "Device"
....
        Option "AddARGBGLXVisuals"
        Option "AllowGLXWithComposite" "True"
....
EndSection

Now scroll down to the very end of the document and paste in this part:
> Section "Extensions"
        Option "Composite" "Enable"
EndSection
[/QUOTE]

Now, you want it to start every time you log in, probably. So here's the way to do that (if you're using Gnome):
> System > Preferences > Sessions > "Startup Programs" Tab
Click "Add"
Type in "beryl-manager"

Then either restart your computer, or restart the  X server (Ctrl + Alt + Backspace).

Some notes:
-You may want to install beryl-plugins-unsupported for some extra plugins.

-You may want to disable "Sync to VBlank" in Beryl Settings Manager" for improved performance

I think that's all correct. Enjoy.

---

### Post by HasratUSA on 2007-03-07
Okay, after reading your post (I'm referring to you, musician) I'm, for say, inspired to go ahead and risk installing Beryl, which is something I always wanted to do but backed off after seeing numerous posts in numerous sites, IRC rooms and forums that it's unstable, can crash X to such an extent that the victim might have to reinstall the whole OS and blah blah blah...!

The question is: if something goes wrong or I want to uninstall it, what would I have to do? I'm running Edgy 6.10 on KDE. Gnome is something I never use, although it's still there in my PC.

---

### Post by maniacmusician on 2007-03-07
> **HasratUSA said:**
> Okay, after reading your post (I'm referring to you, musician) I'm, for say, inspired to go ahead and risk installing Beryl, which is something I always wanted to do but backed off after seeing numerous posts in numerous sites, IRC rooms and forums that it's unstable, can crash X to such an extent that the victim might have to reinstall the whole OS and blah blah blah...!

The question is: if something goes wrong or I want to uninstall it, what would I have to do? I'm running Edgy 6.10 on KDE. Gnome is something I never use, although it's still there in my PC.
Nah, it's usually never that bad.

To un-install beryl, you simply do "sudo apt-get remove beryl beryl-core emerald-themes", and it will remove Beryl. Then you should do "sudo apt-get autoremove" to take care of leftover dependencies. Then, remove the Beryl repos from sources.list. Remember, if you ever get stuck without X, just use the links2 text browser. It's great.

Oh, and if you're going to install it on KDE, the last step is a little different. To have it start when you log in to KDE, you have to use this command: 
> ln -s /usr/bin/beryl-manager ~/.kde/Autostart/beryl-manager

---

### Post by nevertheless on 2007-03-07
ok before I really install ubuntu to becoming my OS how do I partition part of hardrive to use windows xp and ubuntu at the same time. Just in case ubuntu crashes I always want a backup . Thanx again, I'm really starting to get this stuff!!!

---

### Post by steven8 on 2007-03-07
I let gparted do the work for me.  It will take half of your free space for Ubuntu, shrink the xp partition for you, and will put grub right where it's supposed to be.  xp will be kind of mad the first time you boot to it.  it'll make you run chkdsk.  This is no biggie.  For me, the second time I booted xp, after the chkdsk, it claimed to find some new piece of hardware and installed the software, and made me reboot again.  I've had no troubles since.  The option will be at the top of the grub menu for ubuntu, and it should boot up with no problem.

*PLEASE* - make sure you pay attention during the install when it asks you to set passwords and a username.  You will need these to boot into Ubuntu.

Have fun!

---

### Post by maniacmusician on 2007-03-07
> **steven8 said:**
> I let gparted do the work for me.  It will take half of your free space for Ubuntu, shrink the xp partition for you, and will put grub right where it's supposed to be.  xp will be kind of mad the first time you boot to it.  it'll make you run chkdsk.  This is no biggie.  For me, the second time I booted xp, after the chkdsk, it claimed to find some new piece of hardware and installed the software, and made me reboot again.  I've had no troubles since.  The option will be at the top of the grub menu for ubuntu, and it should boot up with no problem.

*PLEASE* - make sure you pay attention during the install when it asks you to set passwords and a username.  You will need these to boot into Ubuntu.

Have fun!
I think he's already installed Ubuntu...and beyl as well, I believe.

---

### Post by newlinux on 2007-03-07
He mentioned he was running it from the liveCD. He said he installed something but I'm not sure if he meant the OS or something else. Just in case... Before you install Ubuntu, I recommend you look at:

[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

and

[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

---

### Post by nevertheless on 2007-03-07
Ok...I'm going to officially install ubuntu and use a dual boot so I can windows and ubuntu. After this I will ask more questions concerning the cube and other things I am interested in. Thanks for all the help but I'm sure I'm not done annotying yaw for now!!:lolflag:

---

### Post by HasratUSA on 2007-03-07
Hey Musician,
I installed the stable version of Beryl. It's working and so far so good. Thanks

---

### Post by nevertheless on 2007-03-07
ok my last question for today is this....
how do you have ubuntu and windows xp run at the same time??? I saw it on a video and this would really optimize my computer...thanks again

EDIT: What do I install to watch videos on firefox because windows media player wouldn't work because I'm running on a linux system right?? What do I install then?? Don't be afraid to leave a list of things I need to install :)

---

### Post by HasratUSA on 2007-03-07
> **nevertheless said:**
> ok my last question for today is this....
how do you have ubuntu and windows xp run at the same time??? I saw it on a video and this would really optimize my computer...thanks again

Duh I'm feeling too bored. 

By the way Musician, soon I'm going to upload a video of me using Beryl to Youtube and send you the link. I hope you'd watch it although it would be nothing new to you :)

---

### Post by nevertheless on 2007-03-07
^^bump..somebody give me some assistance I'm really lost

---

### Post by maniacmusician on 2007-03-07
> **nevertheless said:**
> ok my last question for today is this....
how do you have ubuntu and windows xp run at the same time??? I saw it on a video and this would really optimize my computer...thanks again

EDIT: What do I install to watch videos on firefox because windows media player wouldn't work because I'm running on a linux system right?? What do I install then?? Don't be afraid to leave a list of things I need to install :)

As to your first question, you would use a virtualization software. My personal recommendation is VirtualBox ([http://www.virtualbox.org](http://www.virtualbox.org) )

To watch videos and stuff in Linux, I believe you want the package "mozilla-mplayer". That should take care of most of your needs, I think. 

> **HasratUSA said:**
> Duh I'm feeling too bored. 

By the way Musician, soon I'm going to upload a video of me using Beryl to Youtube and send you the link. I hope you'd watch it although it would be nothing new to you :)

Sure thing :) Enjoy your wonderful Beryl. [checks off that the instructions for the stable version work]

---

