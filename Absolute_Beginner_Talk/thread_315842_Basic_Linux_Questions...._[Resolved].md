---
title: "Basic Linux Questions.... [Resolved]"
date: 2006-12-09
forum: Absolute Beginner Talk
---

### Post by Kevin-WI on 2006-12-09
Here's the deal...

My friend has been bothering me to try Ubuntu forever. He sends me articles on why its better than XP, screenshots and on and on. Finally, I broke down and ordered a live CD, but finally couldn't wait for it to arrive so I burned my own. I ran it, and it was really cool, but, I have some trouble installing it so I quit and ran back to my Windows so I could get some help.

1) First off, my computer has a master 30GB and a slave 30GB hard drives. My goal is to keep the master for Windows, for running iTunes, Microsoft Outlook (I need the calender feature) and certain games (Yeah, I know about WineX, but don't want to fool around with it this early in my Linux "lifetime".) and give the slave one to Linux. When I was in ubuntu, and was looking at the partition app, I could only see one hard drive. Is there anything I was doing wrong?

2) I have a 20" LCD monitor, and in Windows, I like to run at 1600x1200 resolution, but I was shocked in Ubuntu when the highest was 1024x768. I assume this is because I'm not running NVIDIA's Linux drivers for my video card, but is there anything else I'm doing wrong.

Help is appreciated, thanks.

---

### Post by igknighted on 2006-12-09
As for #2, once you install and are using the proper drivers you should be able to get the same resolution as Windows, don't worry.  As far as the second HD, I would try cable-select instead of master/slave, but can you see it in windows now?  If not, it may not work or may just not be installed properly.

---

### Post by Kevin-WI on 2006-12-09
Thanks for the advice on #2.

Has for the drive, I can see it and use in Windows, and I'm running apps off it (in Windows) right now, Firefox and others. I'm going to reformat it, then go ahead with the Ubuntu installation, and see if it can partition it then.

Before, I just was playing around with the partition app, I wasn't actually in the installation process, but I'm going to go ahead and attempt the full installation.

---

### Post by igknighted on 2006-12-09
When you do the install it should be on the list, you might have to select it from a drop-down menu though, as it may try to use the master.  Just make sure you know which drive you're formatting ;-)

---

### Post by aysiu on 2006-12-09
If you're really determined to run Ubuntu, good for you. It'll be an interesting learning experience. My two cents, though--if you really want iTunes, Outlook, and Windows-only games, I think you're better off with Windows. You don't buy a bicycle to replace an SUV.

If, however, you're willing to use Rhythmbox or Banshee instead of iTunes and Evolution instead of Outlook... and explore Cedega as a possibility, I think exploring Ubuntu would be a worthwhile endeavor. Dual-booting is a pain: user's happily working on Firefox in Ubuntu. "Oh, I wonder what's coming up on my calendar... better reboot into Windows..."

---

### Post by Kevin-WI on 2006-12-09
Thanks for your thoughts, asyiu.

The reason I'm really not sold on switching my box 100% to Ubuntu is, I use iTunes mainly to put music on my iPod, and to buy music through the iTunes music store (yeah, yeah, I know, what a narc), and my subscriptions to various podcasts. Its those features that keep me from using something else, personally, iTunes 7 is the slowest app I run on my Windows box.

Has for Outlook, I use it ONLY for its calender. I've tried Sunbird, and I really like it, but the problem is the appointments, and recurring appointments I have set up in Outlook. I've herad nightmare stories about importing from Outlook to other calender apps.

Games, I'd be willing to try to run them in Ubuntu, but, the idea of my betting my enjoyment of a $50+ PC game on how well an unofficial patch or WineX will run it is a bit uncomfortable, but, I hear most games run good with WineX or what not.

---

### Post by aysiu on 2006-12-09
Kevin-WI, I totally understand what you're saying. That's why I recommend sticking with Windows. If that's what suits your needs, Ubuntu isn't going to replace that.

If, however, you just want to learn Ubuntu for the hell of it, I think you will end up learning a lot.

By the way, Evolution has a calendar integrated with it (much like Outlook). If you are going to give Ubuntu a shot, you should look into its native email client. Thunderbird and Sunbird aren't quite there, as you noticed.

I think ultimately, if you're determined to make the migration, however slowly, this is what will wind up happening (it may take months, maybe even over a year or two):

1. You will learn to love Rhythmbox, AmaroK, or Banshee for managing your iPod, and you will just stop using the iTunes music store and start buying CDs again and ripping them.

2. You will find Evolution to be just fine as a replacement for Outlook.

3. You'll play more console games or dual boot just for the games.

Dual booting for games is less than ideal, of course, but it's better than dual booting for games, email, calendaring, and music.

I don't want to stop you from using Ubuntu. I think using and learning Ubuntu is a wonderful thing. I just want to let you know what you're getting into. I think you should read [Is Ubuntu for You?](http://ubuntuforums.org/showthread.php?t=63315), and if you think it is for you, I will be the first one to help you get up and running (though there will be many others as well chipping in).

Whether you just run the live CD, install Ubuntu as a dual boot and rarely use it, or end up doing a full migration from Windows to Ubuntu, we as a community welcome you and will help you with whatever we can.

---

### Post by Kevin-WI on 2006-12-09
OK...

For now, I'm going to dedicate my 30 gig slave drive to Ubuntu and play around with the OS and see if I could get used to using it day in and out.

I'll experiment with the music apps and Evolution, and then I might live with dual booting or migrate to Ubunutu.

---

### Post by randiroo76073 on 2006-12-09
As far as calendars, I don't use onboard, my email & caledar are on Google.  Ya, Google can go down, but so can onboard apps[horror stories about Outlook/Outlook Express]
I think once you install & get Ubuntu setup "your way" the experience will leave you wanting more :)

---

### Post by aysiu on 2006-12-09
All right. Sounds like you're on board for at least a test run.

In answer to your questions.

#1. The partitioning program that comes with the Ubuntu installer is called GParted, and it does this funny thing where it has a drop-down menu for drives, so you will see only one drive at a time. See the attached screenshot for a demonstration.

#2. Usually, Ubuntu's hardware detection is pretty good, but I've also had some screen resolution woes. There's usually an easy fix for it, and it usually has nothing to do with needing NVidia drivers. Of course, you may end up installing the NVidia drivers, anyway, just to get better performance or to eventually install some eye candy like [Beryl](http://www.youtube.com/results?search_query=beryl+ubuntu&search=Search) or [Compiz](http://www.youtube.com/results?search_query=compiz+ubuntu&search=Search).

[This post](http://ubuntuforums.org/showpost.php?p=129379&postcount=21) has a whole host of suggestions for how to get your screen resolution where it needs to be. Unfortunately, Ubuntu (unlike SuSE) hasn't gone completely point-and-click for screen resolution troubleshooting.

---

### Post by Drakkor on 2006-12-09
Well said,aysiu, as usual,you have helped me tremendously with Ubuntu,and I thank you for that. That being said, I shall not be upgrading to Vista,as alot of people won't, and consider XP the end of the line for me with windows products
however, I do think that dual-booting with XP/Ubuntu will make the transition
alot easier, and it's fun learning about Linux ! Long live Ubuntu !!!! :p

---

### Post by victorbrca on 2006-12-09
> **Drakkor said:**
> Well said,aysiu, as usual,you have helped me tremendously with Ubuntu,and I thank you for that. That being said, I shall not be upgrading to Vista,as alot of people won't, and consider XP the end of the line for me with windows products
however, I do think that dual-booting with XP/Ubuntu will make the transition
alot easier, and it's fun learning about Linux ! Long live Ubuntu !!!! :p


  Well said!!! I installed Ubuntu on my laptop last Tuesday... I have to say that I haven't been able to stay away from it since them!!!! :)


Vic.

---

### Post by seijuro on 2006-12-09
Kontact for KDE also has calendar feature. In some cases I agree with the dual boot is a pain comment but if you arrange things right it doesn't have to be just make sure all of your primary daily use stuff is on one or the other and have a jump drive or FAT32 partiton so you can easily share files back n foreth it really simplifies dual boot systems.

---

### Post by Drakkor on 2006-12-09
Yeah,it brings the joy of computing back !  :D

---

### Post by aysiu on 2006-12-09
> **seijuro said:**
> Kontact for KDE also has calendar feature. In some cases I agree with the dual boot is a pain comment but if you arrange things right it doesn't have to be just make sure all of your primary daily use stuff is on one or the other and have a jump drive or FAT32 partiton so you can easily share files back n foreth it really simplifies dual boot systems.
Just to clarify, my comment about dual booting being a pain mainly had to do with the actual rebooting, not the sharing of files:

Use Ubuntu for this task.
Reboot.
Use Windows for that task.
Reboot.
Use Ubuntu for another task.
Etc.

---

### Post by edu65 on 2006-12-09
> **Kevin-WI said:**
> Here's the deal...

2) I have a 20" LCD monitor, and in Windows, I like to run at 1600x1200 resolution, but I was shocked in Ubuntu when the highest was 1024x768. I assume this is because I'm not running NVIDIA's Linux drivers for my video card, but is there anything else I'm doing wrong.


If you happen to have a DELL 2007FP monitor, you may want to take a look at this thread:

[http://ubuntuforums.org/showthread.php?t=303452](http://ubuntuforums.org/showthread.php?t=303452)

See also:

[http://voltaire.nfshost.com/blog/2006/08/07/dell-2007fp-and-xorgconf/](http://voltaire.nfshost.com/blog/2006/08/07/dell-2007fp-and-xorgconf/)

Good luck!

---

### Post by seijuro on 2006-12-09
> **aysiu said:**
> Just to clarify, my comment about dual booting being a pain mainly had to do with the actual rebooting, not the sharing of files:

Use Ubuntu for this task.
Reboot.
Use Windows for that task.
Reboot.
Use Ubuntu for another task.
Etc.

Yes I understood what you meant, what I was saying was that it doesn't have to be that way if you have all of your most used things on one or the other then you only need to reboot because you have the weekend off and you want to kill your buddy's on some online game for 48 hours, etc.

---

### Post by Kevin-WI on 2006-12-09
Well, I'm writing this in Ubuntu right now.

I jumped right into the partitioner and just played around with the tool until I figured out how it worked and successfully paritioned my drive the way I want. (For those playing at home, I have dual 40GB, not 30GB).

Anyway. The screen resolution is still not where I want it, but I'm working on that.

So far, so good. The installation was amazing. It was like installing a Google app on Windows XP, rather than installing a whole OS.

Has for dual booting, one of my family members has a Mac Pro, and dual boots between XP and Mac OS X, so I know all about dual booting and how long it can be.

---

### Post by Drakkor on 2006-12-09
Congrats !! :KS  Happy Ubuntuing,lol !

---

### Post by riven0 on 2006-12-09
> **Kevin-WI said:**
> Anyway. The screen resolution is still not where I want it, but I'm working on that.


You may be able to fix the screen resolution with the official graphics drivers. You should try that first before anything else. It'll give you better performance, too.

---

### Post by aysiu on 2006-12-09
Post your monitor information here, and we'll try to help you out.

---

### Post by Kevin-WI on 2006-12-09
My monitor is a Samsung SyncMaster 204B

Thanks for the help, guys.

---

### Post by aysiu on 2006-12-09
First, let's try to get your screen resolution sussed out.

Log out of Ubuntu. Press Control-Alt-F1. This will take you to a virtual terminal. Type: ```
sudo nano -B /etc/X11/xorg.conf
``` This will allow you to edit your graphical configuration file while also making a backup copy of the old one. 

There should be a section somewhere in the middle called **Monitor**. If that section has two lines with *VertRefresh* and *HorizSync* in them, replace those with these. If not, add these. ```
HorizSync 30-81
VertRefresh 56-75
``` Then save the file (Control-X, Y, Enter).

Press Control-Alt-F7. This will take you back to the login screen. Then press Control-Alt-Backspace. This will reset the X server (graphical server) so your new settings can take effect.

If that works, you may also want to know that someone on these forums apparently had trouble getting the correct refresh rate at first, but posted a solution [here](http://ubuntuforums.org/showthread.php?p=869373&highlight=syncmaster#post869373).

P.S. *HorizSync* and *VertRefresh* should be on their own lines. For example, this is the relevant section from my /etc/X11/xorg.conf file (This is from my Ubuntu installation--**don't use these settings on yours**. I'm just posting this as an example of what the format looks like): ```
Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        HorizSync       28-64
        VertRefresh     43-60
EndSection
```

---

### Post by Kevin-WI on 2006-12-09
OK, did all that.

It added a new resolution, 832x624, but its not the 1600x1200 I wanted...

I'll try that other solution you linked to.

---

### Post by Kevin-WI on 2006-12-09
Hmmm, I made that fix, but I can't seem to find this so called "modeline" where to input the variables that that calculator gave me, so any help would be appreciated.

---

### Post by Paul133 on 2006-12-09
Aysiu, I reboot just for the games. I don't see it as too much of a pain and usually I stick with Ubuntu. What I like about Ubuntu is that it's Linux, and as a result, it's easy to learn python, bash, and the CLI on. DOS is nothing, UNIX is so much more powerful. That's what I like about Ubuntu, that and all the free software. But, I boot into Windows for the games, and I don't see it as too much of a pain.

---

### Post by aysiu on 2006-12-09
Hm.

That's odd.

Can you try running this command? And then doing the Control-Alt-Backspace? Some of the questions you may not know the answer to. If so, just go with the defaults. But answer the other questions as best you can. ```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by Kevin-WI on 2006-12-09
Yep, I just ran that. And did all the stuff. No 1600x1200.

---

### Post by riven0 on 2006-12-09
I'm telling you, it may be better just to install the official drivers. :D 

For nvidia: > sudo aptitude install nvidia-glx

For ati, [look here]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI"). Or [here]("http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide") for edgy.

---

### Post by Kevin-WI on 2006-12-09
No luck...

Does it matter that I'm running 6.06 and not the newer Ubunut?

---

### Post by riven0 on 2006-12-09
> **Kevin-WI said:**
> No luck...

Does it matter that I'm running 6.06 and not the newer Ubunut?

Well, first I guess it's best to ask what is your graphics card? 

As for running 6.06, I don't really think this will make a difference, but someone correct me if I'm wrong.

---

### Post by aysiu on 2006-12-09
Maybe this might help?
[ xorg.conf for a Samsung SyncMaster 204B LCD monitor](http://marc.abramowitz.info/archives/2006/06/28/xorgconf-for-a-samsung-syncmaster-204b-lcd-monitor/)

---

### Post by Kevin-WI on 2006-12-09
> **aysiu said:**
> Maybe this might help?
[ xorg.conf for a Samsung SyncMaster 204B LCD monitor](http://marc.abramowitz.info/archives/2006/06/28/xorgconf-for-a-samsung-syncmaster-204b-lcd-monitor/)

I'll try that right now....

---

### Post by aysiu on 2006-12-09
> **Kevin-WI said:**
> I'll try that right now....
Just keep in mind that not all of that xorg.conf will apply, since that person has a different graphics card.

---

### Post by Kevin-WI on 2006-12-09
This is interesting...

I type this in the console to go to my xorg.conf file...

```
sudo nano -B /etc/x11/xorg.conf
```

And its competely blank and says New File, at the bottom.

---

### Post by aysiu on 2006-12-09
> **aysiu said:**
> Just keep in mind that not all of that xorg.conf will apply, since that person has a different graphics card.
Someone else blogged a solution to Samsung SyncMaster 204B. I don't know why this monitor is so problematic and why there are so many different approaches to getting it to work:
[http://userpages.umbc.edu/~zelenyd1/#200608060115](http://userpages.umbc.edu/~zelenyd1/#200608060115)

---

### Post by aysiu on 2006-12-09
> **Kevin-WI said:**
> This is interesting...

I type this in the console to go to my xorg.conf file...

```
sudo nano -B /etc/x11/xorg.conf
```

And its competely blank and says New File, at the bottom.
It's case-sensitive.

```
sudo nano -B /etc/x11/xorg.conf
``` is different from ```
sudo nano -B /etc/X11/xorg.conf
```

---

### Post by Kevin-WI on 2006-12-10
Well... THAT was fun.

I compared my xorg to his, and they were pretty similar. When I got to the Monitor section, I just added a single Modeline line, the one for 1600x1200. I go to reset the graphical server, and I get about 5 error messages and I'm kicked back to the command line. I restart my machine, and put to the command line, so I'm writting this with my live cd.... :(

Well, from here I assume I have to restore my backup coppy (I think it automatically made one, right?)

---

### Post by aysiu on 2006-12-10
Yes. It should be called /etc/X11/xorg.conf~

Once you're at the command-line, you can type ```
sudo cp /etc/X11/xorg.conf~ /etc/X11/xorg.conf
``` to restore it. You can also uses the command I gave you earlier in order to recreate the /etc/X11/xorg.conf file: ```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by Kevin-WI on 2006-12-10
Hmmm, thanks, and no thanks...

I tried to go to the virtual terminal, and all the font was "squeezed" up in about the top two inches of the screen. I couldn't read anything.

I think this prooves Ubuntu isn't for me. I knew Linux was the "Wild West" in regards to no official support and getting your hands dirty in the command line, but this is frusterating.

---

### Post by aysiu on 2006-12-10
Well, if you want to give up, that's cool.

If you want to take a break and continue this later, I'll try to offer any help I can.

By the way, there were two blogs I linked to that had "solutions" for this monitor. Which one did you try? Or did you try both?

And did you already install the Nvidia drivers?

---

### Post by Kevin-WI on 2006-12-10
Eh, ok. I was just frusterated. I'll hang in here.

I went to the terminal and tried to type the first one, but, alas, all the font was illegiable since it was "crunched" into the top 1.5 inches of the monitor. I am running through a live CD, and in video recovery mode, if that makes a difference.

---

### Post by aysiu on 2006-12-10
I'm not sure what "video recovery mode" is.

I think your best bet is to boot up without the live CD and run these commands ```
sudo dpkg-reconfigure xserver-xorg
sudo /etc/init.d/gdm start
``` The first command should get you at least a working screen resolution, if not your ideal. The second command will restart your display manager. Once that's up and running, let's work on getting those Nvidia drivers installed. We might be able to make some progress from there.

I understand how frustrating this is, believe me.

---

### Post by Kevin-WI on 2006-12-10
hmmm, video recovery mode or something to that effect... when I put in the live CD, it was the second opitions.

anyway, I'll get on your commands.

---

### Post by S1NGH on 2006-12-10
> **Kevin-WI said:**
> hmmm, video recovery mode or something to that effect... when I put in the live CD, it was the second opitions.

anyway, I'll get on your commands.

you mean the second boot process from the live CD, graphical interface right?

---

### Post by Kevin-WI on 2006-12-10
> **S1NGH said:**
> you mean the second boot process from the live CD, graphical interface right?

Yeah... that was it.

Anyway, I went in and entered the reconfigure command, and, then, it says that the X server is disable, and when I properly reconfigure it, I should reactivate GRM something.

---

### Post by S1NGH on 2006-12-10
alright, once you have configured your X server, you should be also do get a graphical display the Gnome Display Manager (GDM) upon entering this command:

what happens when you type in this command?
sudo /etc/init.d/gdm start

---

### Post by Kevin-WI on 2006-12-10
Yahoo! I finally fixed everything.

I got really mad last night and tried to uninstall Ubuntu. Big mistake. I put in my live CD, then started the installation process and cleared out the linux partition, but then cancelled the installation and took out the live CD. When I started up this morning, my BIOS wouldn't recongize my keyboard and mouse. When I got that settled, my MBR was all messed up due to my improper removal.

So, I put my Live CD back in, reinstalled Ubunutu, and went to the config thing for Xserver, and suddenly, I realized something...

In the one page where it gives you a list of resolutions, I was hitting enter on 1600x1200, which takes you the next page, I wasn't hitting the space key to select 1600x1200. I reboot, and, now, Ubuntu is running in 1600x1200.

Thanks for all your help guys, I feel a bit dumb for such causing such a fuss for such a simple problem.

---

### Post by aysiu on 2006-12-10
I don't think you should feel dumb at all. For the longest time, I didn't know how to work the text-based GUI either. (Why would you think Space Bar means select?)

No, the truth is that Ubuntu needs to step up to SuSE standards when it comes to graphical configuration of screen resolution/video card issues. Right now they're working on something for Feisty (the next release) called [Bullet Proof X](https://blueprints.launchpad.net/distros/ubuntu/+spec/bullet-proof-x), which means you'll never end up the way you did in [post #38](http://ubuntuforums.org/showpost.php?p=1866842&postcount=38), with just a command-line.

Well, I'm glad it finally worked for you eventually. Welcome to Ubuntu!

---

