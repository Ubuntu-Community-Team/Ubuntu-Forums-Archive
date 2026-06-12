---
title: "can't open Live CD on Computer"
date: 2006-04-23
forum: Absolute Beginner Talk
---

### Post by RAV TUX on 2006-04-23
when I try to load the live Breezy CD this is what happens:

[http://img156.imageshack.us/img156/6206/img11642zw.jpg](http://img156.imageshack.us/img156/6206/img11642zw.jpg)
[http://img156.imageshack.us/img156/2386/img11650sh.jpg](http://img156.imageshack.us/img156/2386/img11650sh.jpg)
[http://img156.imageshack.us/img156/5449/img11660fu.jpg](http://img156.imageshack.us/img156/5449/img11660fu.jpg)
[http://img178.imageshack.us/img178/6796/img11679me.jpg](http://img178.imageshack.us/img178/6796/img11679me.jpg)
[http://img178.imageshack.us/img178/7320/img11687dg.jpg](http://img178.imageshack.us/img178/7320/img11687dg.jpg)

on the last image it just hangs there and I have to restart.

:-k

---

### Post by dermotti on 2006-04-23
run ** sudo dpkg-reconfigure xserver-xorg ** and select **vesa **as your driver

Then run  

**ps -e | grep gdm**


you should see something like

5678 GDM

then run **sudo kill 5678**   (5678 could be any number on yours system)

then run 

**GDM**

---

### Post by joshuapurcell on 2006-04-23
[QUOTE=yozef]when I try to load the live Breezy CD this is what happens:

[http://img156.imageshack.us/img156/6206/img11642zw.jpg](http://img156.imageshack.us/img156/6206/img11642zw.jpg)
[http://img156.imageshack.us/img156/2386/img11650sh.jpg](http://img156.imageshack.us/img156/2386/img11650sh.jpg)
[http://img156.imageshack.us/img156/5449/img11660fu.jpg](http://img156.imageshack.us/img156/5449/img11660fu.jpg)
[http://img178.imageshack.us/img178/6796/img11679me.jpg](http://img178.imageshack.us/img178/6796/img11679me.jpg)
[http://img178.imageshack.us/img178/7320/img11687dg.jpg](http://img178.imageshack.us/img178/7320/img11687dg.jpg)

on the last image it just hangs there and I have to restart.

:-k[/QUOTE]Are you using a USB keyboard? I ask this because I had a minor problem with the Live CD while using a USB keyboard. Here are some steps that may help:

1.Restart the computer, and hit the escape key when the prompt comes up to enter the GRUB menu.
2.Once you are in the Grub menu, select the boot option that says 'Recover' at the end of the line (this will boot you into single user mode).
3.After the bootup process is complete you will be left at a command prompt, and now you can check some logs to see what the problem is. Use these commands:```
root@localhost:~#more /var/log/gdm/\:0.log
root@localhost:~#more /var/log/messages
```
*Look for any line in the first log that starts with EE (the messages log may also have some info on the error). Post the errors you find here.*

4.You can also try to manualy start X by typing this at the command prompt: **startx**. This also is beneficially because it will printout the log in your current terminal while trying to start X on the terminal located at F7.

Post with some more information when you get it.

---

### Post by RAV TUX on 2006-04-23
[QUOTE=dermotti]run ** sudo dpkg-reconfigure xserver-xorg ** and select **vesa **as your driver

Then run  

**ps -e | grep gdm**


you should see something like

5678 GDM

then run **sudo kill 5678**   (5678 could be any number on yours system)

then run 

**GDM**[/QUOTE]

ok silly question: at what point do I type in the sudo command prompt?

I tried booting the live CD and plugging in what you said at the last image above...nothing went in...

I should also say I am trying to run live CD for version 5.10  for 64-bit PC

I have 64 bit (Intel EM64T) Dual core processor

:-k

---

### Post by RAV TUX on 2006-04-23
:confused: :confused: :confused: :confused: :confused: :confused:

---

### Post by joshuapurcell on 2006-04-23
[QUOTE=yozef]ok silly question: at what point do I type in the sudo command prompt?

I tried booting the live CD and plugging in what you said at the last image above...nothing went in...

I should also say I am trying to run live CD for version 5.10  for 64-bit PC

I have 64 bit (Intel EM64T) Dual core processor

:-k[/QUOTE]
You would have to either boot up using the recovery mode kernel (using the instructions in my post above) or get to a terminal at some point after booting up with the normal kernel (if that is possible). I believe that once the X server fails to start and displays the errors that you have screenshots of, it will exit to a terminal window. If that's the case, then you can run the **sudo dpkg-reconfigure xserver-xorg** command as dermotti said. I would shutdown the gdm service first though (if it is even still running) by this command:```
sudo /etc/init.d/gdm stop
```This command does the same thing as dermotti's suggestion for using **ps -ef | grep gdm**, only it uses the built-in function of the gdm service.

Following these commands will hopefully reconfigure your X server without worrying about finding the cause of your current problem. Looking through the logs as mentioned in my first post would give you and idea of why you are having this problem. Either way should get the issue resolved.

---

### Post by RAV TUX on 2006-04-24
[QUOTE=joshuapurcell]You would have to either boot up using the recovery mode kernel (using the instructions in my post above) or get to a terminal at some point after booting up with the normal kernel (if that is possible). I believe that once the X server fails to start and displays the errors that you have screenshots of, it will exit to a terminal window. If that's the case, then you can run the **sudo dpkg-reconfigure xserver-xorg** command as dermotti said. I would shutdown the gdm service first though (if it is even still running) by this command:```
sudo /etc/init.d/gdm stop
```This command does the same thing as dermotti's suggestion for using **ps -ef | grep gdm**, only it uses the built-in function of the gdm service.

Following these commands will hopefully reconfigure your X server without worrying about finding the cause of your current problem. Looking through the logs as mentioned in my first post would give you and idea of why you are having this problem. Either way should get the issue resolved.[/QUOTE]


I will try your way the other way just didn't seem to work.

:-k

---

### Post by RAV TUX on 2006-04-25
[QUOTE=joshuapurcell]Are you using a USB keyboard? I ask this because I had a minor problem with the Live CD while using a USB keyboard. Here are some steps that may help:

1.Restart the computer, and hit the escape key when the prompt comes up to enter the GRUB menu.
2.Once you are in the Grub menu, select the boot option that says 'Recover' at the end of the line (this will boot you into single user mode).
3.After the bootup process is complete you will be left at a command prompt, and now you can check some logs to see what the problem is. Use these commands:```
root@localhost:~#more /var/log/gdm/\:0.log
root@localhost:~#more /var/log/messages
```
*Look for any line in the first log that starts with EE (the messages log may also have some info on the error). Post the errors you find here.*

4.You can also try to manualy start X by typing this at the command prompt: **startx**. This also is beneficially because it will printout the log in your current terminal while trying to start X on the terminal located at F7.

Post with some more information when you get it.[/QUOTE]


I think the problem here is the GRUB menu doesn't come up. The computer in question here only has XP on it.](*,)

---

### Post by catlett on 2006-04-25
> .Restart the computer, and hit the escape key when the prompt comes up to enter the GRUB menu.

To further illuminate a pretty clear message, when you start the computer and the FIRST prompt comes up. DO NOT hit enter hit ESCAPE. This will take you to a Grub menu. You then want recovery mode. Which will log you in single user mode, where you can type in the commands.

---

### Post by RAV TUX on 2006-04-25
[QUOTE=catlett]To further illuminate a pretty clear message, when you start the computer and the FIRST prompt comes up. DO NOT hit enter hit ESCAPE. This will take you to a Grub menu. You then want recovery mode. Which will log you in single user mode, where you can type in the commands.[/QUOTE]

ok please be patient I am a absolute beginner, posting in absolute beginner talk...

so here is what happened...

1. I restarted the computer...the following screen came up:
[http://img180.imageshack.us/img180/9354/img11758ru.jpg](http://img180.imageshack.us/img180/9354/img11758ru.jpg)

if you notice I only have 2 options(well that I know of)
F2 or F12

I first tried hitting the "Esc" key at this point:
[http://img200.imageshack.us/img200/9554/135149193fdf22e1860b7mf.jpg](http://img200.imageshack.us/img200/9554/135149193fdf22e1860b7mf.jpg)

this is what came up:
[http://img143.imageshack.us/img143/4989/img11707xv.jpg](http://img143.imageshack.us/img143/4989/img11707xv.jpg)

nice? right.

2. so I restarted the computer again..then at this screen:
[http://img180.imageshack.us/img180/9354/img11758ru.jpg](http://img180.imageshack.us/img180/9354/img11758ru.jpg)
I hit "F12"

which brought me to this screen:
[http://img183.imageshack.us/img183/5145/img11765yu.jpg](http://img183.imageshack.us/img183/5145/img11765yu.jpg)
I selected "onboard or USB CD-ROM drive

which brought me to this screen:
[http://img183.imageshack.us/img183/4111/img11805gu.jpg](http://img183.imageshack.us/img183/4111/img11805gu.jpg)

so I hit the "Esc" key here:
[http://img200.imageshack.us/img200/9554/135149193fdf22e1860b7mf.jpg](http://img200.imageshack.us/img200/9554/135149193fdf22e1860b7mf.jpg)

this is what happened:
[http://img183.imageshack.us/img183/6055/img11829am.jpg](http://img183.imageshack.us/img183/6055/img11829am.jpg)
nothing. (should I have pressed F1 for advanced help?)

so I came this far thought I would try once again, I hit enter:
[http://img140.imageshack.us/img140/6386/img11835ff.jpg](http://img140.imageshack.us/img140/6386/img11835ff.jpg)
this comes up again:
[http://img183.imageshack.us/img183/6101/img11846cy.jpg](http://img183.imageshack.us/img183/6101/img11846cy.jpg)
[http://img140.imageshack.us/img140/641/img11858tl.jpg](http://img140.imageshack.us/img140/641/img11858tl.jpg)

then once again I am stuck here:
[http://img259.imageshack.us/img259/1284/img11863do.jpg](http://img259.imageshack.us/img259/1284/img11863do.jpg)
I tried hitting the "Esc" key again, tried typing in startx again I wasn't able to type anything in.

[http://img200.imageshack.us/img200/9554/135149193fdf22e1860b7mf.jpg](http://img200.imageshack.us/img200/9554/135149193fdf22e1860b7mf.jpg)

Please look at the screen shots...I know I must be missing something?

everybody talks about the GRUB menu, I am not sure what you mean.
let me clarify I know what you mean and on my older computer that I been using Ubuntu on since about Oct 2005...I have no problems...

I am just trying to run the live CD on the new computer(before I do an install)...XP Sp2 

Here is the info on my new computer(relatively new, newer then my old one):

processor info:
[http://img247.imageshack.us/img247/464/img11773tl.jpg](http://img247.imageshack.us/img247/464/img11773tl.jpg)

As you can see I have an Intel (EM64T) so I have been using the Live CD version 5.10 for 64-bit PC

memory info:
[http://img267.imageshack.us/img267/1176/135156682b984aff54fb0vj.jpg](http://img267.imageshack.us/img267/1176/135156682b984aff54fb0vj.jpg)

PCI info:
[http://img247.imageshack.us/img247/8058/img11793fg.jpg](http://img247.imageshack.us/img247/8058/img11793fg.jpg)

](*,)

Thank you in advance for everybodies help...I really would like to get Ubuntu running on this computer.
(dual boot XP/Ubuntu...and eventually a triple boot to another Linux distro...maybe and eventually be free from the shackles of windows)

Also I want to run QTparted or Gparted off the live CD to partition my disk before I do the install....but I first have to get the live CD to work.

---

### Post by RAV TUX on 2006-04-26
I know it might take a bit to review my above post...but any help in this matter would be greatly appreciated.

:mrgreen:

---

### Post by RAV TUX on 2006-04-26
:confused: :confused: :confused:

---

### Post by RAV TUX on 2006-04-26
still in need of help....please.

---

### Post by BoyOfDestiny on 2006-04-26
[QUOTE=yozef]still in need of help....please.[/QUOTE]

Poor guy, is there an option to boot with vga or vesa?

If you can, I'd really recommend the dapper beta livecd...

[http://www.ubuntu.com/testing/dapperbeta](http://www.ubuntu.com/testing/dapperbeta)

Not the solution you want, but seriously, Dapper has improved by leaps and bounds...

---

### Post by RAV TUX on 2006-04-26
[QUOTE=BoyOfDestiny]Poor guy, is there an option to boot with vga or vesa?

If you can, I'd really recommend the dapper beta livecd...

[http://www.ubuntu.com/testing/dapperbeta](http://www.ubuntu.com/testing/dapperbeta)

Not the solution you want, but seriously, Dapper has improved by leaps and bounds...[/QUOTE]

OK sounds good, do you know if there is a bittorrent download available?

Then the only other hurdle I have is learning how to burn ISO to CD, I have tried ISOrecorder with no luck, I think there may be a problem because I am running a 32 bit version of XP Sp2 on a 64bit computer. I also have sonic but the whole burning CD's process is new to me. I downloaded SUSE on Bittorrent, which I would like to set up as dual boot but I really would prefer Ubuntu to be my primary OS.

Thanks for the response your suggestion is refreshing...
If worse comes to worse I may wait for the official Dapper CD's to be delivered.

---

### Post by catlett on 2006-04-27
The x server can't start means your not going to have a gui. The point to hit escape was at the Ubuntu screen where it says press enter. Next time try and press F2 for the options. Here [http://www.ubuntu.com/download](http://www.ubuntu.com/download) is the download site. It is only for breezy but I would recommend trying the 32bit version. I've seen people post saying you can run 32 on 64 machiunes and it might be advisable because it has better support for different hardware.
I couldn't easily find the bittorent for Dapper but later I'l hunt around. For now try Googling it.
Also if you get into that page with the option to see the output, do it.That's what the more advanced people here need to see. They can't really diagnose the problem without knowing what the computer was running and what didn't work.
It is easier to fix this problem if you installed (believe it or not). If you install and the xserver didn't start, you would still have the OS and a command line to work with. From there you could run the configuration again and pick another driver (presumably vesa).
I have to go but I feel guilty that a left an impolite post so when I get home from work I'l try doing a little homework on the live cd options and your configuration.
Good luck.

PS Her is a cd burning howto [https://wiki.ubuntu.com/BurningIsoHowto](https://wiki.ubuntu.com/BurningIsoHowto)

---

### Post by RAV TUX on 2006-04-29
OK so here is how far I have come:
I downloaded and burned an ISO image of Ubuntu Dapper 6.06 beta live-CD 64bit
(I am successfully running Dapper 6.06 beta on my old 32bit computer! and I love it!)

(I tried both the 32-bit and 64-bit of version 5.10 with the same results)

anyway I did make progress but still not working, I was however finally able to access the sudo command line thingy...

ok so here is what I did per specifications(but I did diverge a bit)

I typed in:

sudo dpkg-reconfigure xserver-xorg

I selected

auto detect

then I selected the auto detected (driver?)

ati

then led to more info:

ATI Technologies, Inc R480 [Radeon X850XT Platinum (PCIE)]

after that I tried several things

sudo /etc/init.d/gdm stop
sudo /etc/x11/xorg.conf

nothing

(I didn't try ps-e|grep gdm)

should I try this?

screenshots to come.
:-k

---

### Post by RAV TUX on 2006-04-29
[QUOTE=yozef]OK so here is how far I have come:
I downloaded and burned an ISO image of Ubuntu Dapper 6.06 beta live-CD 64bit

(I tried both the 32-bit and 64-bit of version 5.10 with the same results)

anyway I did make progress but still not working, I was however finally able to access the sudo command line thingy...

ok so here is what I did per specifications(but I did diverge a bit)

I typed in:

sudo dpkg-reconfigure xserver-xorg

I selected

auto detect

then I selected the auto detected (driver?)

ati

then led to more info:

ATI Technologies, Inc R480 [Radeon X850XT Platinum (PCIE)]

after that I tried several things

sudo /etc/init.d/gdm stop
sudo /etc/x11/xorg.conf

nothing

(I didn't try ps-e|grep gdm)

should I try this?

screenshots to come.
:-k[/QUOTE]


ok here are the screenshots I promised:

[[IMG]http://img88.imageshack.us/img88/8800/img11889dw.th.jpg[/IMG]](http://img88.imageshack.us/my.php?image=img11889dw.jpg)

[[IMG]http://img139.imageshack.us/img139/1480/img11890yj.th.jpg[/IMG]](http://img139.imageshack.us/my.php?image=img11890yj.jpg)

[[IMG]http://img88.imageshack.us/img88/7287/img11907os.th.jpg[/IMG]](http://img88.imageshack.us/my.php?image=img11907os.jpg)

[[IMG]http://img87.imageshack.us/img87/3092/img11916hc.th.jpg[/IMG]](http://img87.imageshack.us/my.php?image=img11916hc.jpg)

[[IMG]http://img87.imageshack.us/img87/3865/img11926zc.th.jpg[/IMG]](http://img87.imageshack.us/my.php?image=img11926zc.jpg)

[[IMG]http://img87.imageshack.us/img87/4154/img11930fk.th.jpg[/IMG]](http://img87.imageshack.us/my.php?image=img11930fk.jpg)

---

### Post by RAV TUX on 2006-04-29
please help.

---

### Post by RAV TUX on 2006-05-01
:confused: :confused: :confused: :confused: :confused: :confused: 

It still isn't happening. Any clues? anybody?

---

### Post by Sandlst on 2006-05-03
When reconfiguring the xserver, try not using autodetect for your driver, try manually selecting 'vesa' - and to test it out, either type in ```
sudo /etc/init.d/gdm restart
``` Or```
startx
```Also, after you did select ati, did you attempt the above commands?  You can use them to test out any config options after you reconfigure.
Good Luck!

---

### Post by RAV TUX on 2006-05-08
[QUOTE=Sandlst]When reconfiguring the xserver, try not using autodetect for your driver, try manually selecting 'vesa' - and to test it out, either type in ```
sudo /etc/init.d/gdm restart
``` Or```
startx
```Also, after you did select ati, did you attempt the above commands?  You can use them to test out any config options after you reconfigure.
Good Luck![/QUOTE]


ok when I tried to manually select "versa" it would do the funky thing upon scroll down.(screen would jumble and would not let me scroll down to select versa)

I did do startx and I believe I posted a screenshot of the results.

I am not at home now but I remember I wrote a note to post here That "RAID" or is "RIAD" failed...my notes and computer in question are home and I am not. I will look again when I get home.

I really want to get Ubuntu working on that computer.

I have tried a few different distros and the only one that even was able to boot at all was Scientific Linux but my mouse and sound didn't work. I believe Scientific Linux is built on Red Hat?
[https://www.scientificlinux.org/](https://www.scientificlinux.org/)

I will try Musix when I get home,
[http://www.musix.org.ar/en/index.html](http://www.musix.org.ar/en/index.html)

...but again I really would rather run Ubuntu more so then any other OS.

---

### Post by RAV TUX on 2006-05-09
[QUOTE=yozef]ok when I tried to manually select "versa" it would do the funky thing upon scroll down.(screen would jumble and would not let me scroll down to select versa)

I did do startx and I believe I posted a screenshot of the results.

I am not at home now but I remember I wrote a note to post here That "RAID" or is "RIAD" failed...my notes and computer in question are home and I am not. I will look again when I get home.

I really want to get Ubuntu working on that computer.

I have tried a few different distros and the only one that even was able to boot at all was Scientific Linux but my mouse and sound didn't work. I believe Scientific Linux is built on Red Hat?
[https://www.scientificlinux.org/](https://www.scientificlinux.org/)

I will try Musix when I get home,
[http://www.musix.org.ar/en/index.html](http://www.musix.org.ar/en/index.html)

...but again I really would rather run Ubuntu more so then any other OS.[/QUOTE]


I actually got Musix to load everything worked but I couldn't connect to the internet with Firefox, pretty cool distro btw....I posted for help to their forum but the english language forum is very limited.

If anybody here knows how to enable the internet connection it would be a great help Musix seems to be based in Debian like Ubuntu.
:-k

---

### Post by RAV TUX on 2006-05-11
If anybody here knows how to enable the internet connection it would be a great help Musix seems to be based in Debian like Ubuntu.
:-k[/QUOTE]

I actually got Musix to work, I also goy Kinneret to work also.

I have burned a CD of Yoper and now I'm going to try Morphix and Gnoppix(based on Ubuntu).:mrgreen:

(I still love Ubuntu, hopefully the official Dapper release will work on my EM64T  when released)

---

### Post by KillrBuckeye on 2006-05-11
Do you still want to run Ubuntu with the LiveCD?  I had the same problem when trying to use the LiveCD, and it happens because the graphics drivers included on the LiveCD are too old to support our video hardware.  My card, the 7900GT, wasn't even supported in Linux until a month ago.  Anyhow, I was able to use the LiveCD by doing the following:

When you first boot the LiveCD and are prompted for the type of boot, type in "live-expert" instead of doing the default boot.  It will ask you A LOT of questions, but you can just use the default autodetected answers by pressing enter at each prompt.  When it gets to the point where it's configuring your video hardware, do NOT select the option for autodetection.  Instead, choose "No" and then select the VESA driver from the list.  Then continue through the rest of the prompts using the default answers.

This should enable the X server to start up just fine.  I hope this works for you!

---

### Post by RAV TUX on 2006-05-11
[QUOTE=KillrBuckeye]Do you still want to run Ubuntu with the LiveCD?  I had the same problem when trying to use the LiveCD, and it happens because the graphics drivers included on the LiveCD are too old to support our video hardware.  My card, the 7900GT, wasn't even supported in Linux until a month ago.  Anyhow, I was able to use the LiveCD by doing the following:

When you first boot the LiveCD and are prompted for the type of boot, type in "live-expert" instead of doing the default boot.  It will ask you A LOT of questions, but you can just use the default autodetected answers by pressing enter at each prompt.  When it gets to the point where it's configuring your video hardware, do NOT select the option for autodetection.  Instead, choose "No" and then select the VESA driver from the list.  Then continue through the rest of the prompts using the default answers.

This should enable the X server to start up just fine.  I hope this works for you![/QUOTE]


WOW most clear and awesome advice, I will try just as you have stated. I am currently using Morphix and the installation was easy without event and everything just works. I do love Ubuntu and I have been wanted to do a triple boot on this computer. perhaps XP/Ubuntu/Morphix. 

The Morphix version I am running uses Gnome which I love also. I have to say I am quite impressed.

this isn't an official release of Morphix, yet:
[http://www.morphix.org/index.php?option=com_content&task=view&id=39&Itemid=59](http://www.morphix.org/index.php?option=com_content&task=view&id=39&Itemid=59)
Morphix 0.5-pre4 Gnome is only stable by live CD which can be downloaded here:
[http://prdownloads.sourceforge.net/morphix/MorphixCombined-HeavyGUI-0.5-pre4.iso?download](http://prdownloads.sourceforge.net/morphix/MorphixCombined-HeavyGUI-0.5-pre4.iso?download)
MorphixCombined-HeavyGUI-0.5-pre4.iso

when and if you try this you'll find it quite similar to Ubuntu, I guess that is why I like it.

I tried loaded the live Ubuntu Dapper CD and still failure. I will not give up, but for now the live CD of 
"Morphix 0.5-pre4 Gnome" will do nicely.

---

