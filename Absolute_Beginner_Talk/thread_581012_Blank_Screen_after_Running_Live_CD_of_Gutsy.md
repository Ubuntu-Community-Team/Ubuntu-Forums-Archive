---
title: "Blank Screen after Running Live CD of Gutsy"
date: 2007-10-19
forum: Absolute Beginner Talk
---

### Post by Bennett2005 on 2007-10-19
Hello Ubuntu Users,

I'm wondering if anyone could help me with a problem I had while trying to start Ubuntu off the live CD.

 downloaded 7.10 last night and gave the live CD a shot this morning.  After selecting the 'Live CD/Install' on the disc, I saw a 'Loading Linux Kernal' status bar, then a couple lines of text (kernal is alive, etc).  After that, I got a big "No Signal" message on my monitor and the monitor went to standby.

I"m using an ATI X700 series graphics card, and a ViewSonic 19" LCD (if that matters).
I downloaded the x64 version of Ubuntu because I'm using an AMD 64 4.2 processor
2 Gig of ram in the system
1 Granola bar and 1 cup of coffee (not decaf)

Anyone have an idea of why it's not loading properly off the live disk?  I actually downloaded the ISO twice to make sure it wasn't due to a faulty download, but the same thing happened with both.

Thanks in advance :)

---

### Post by orange2k on 2007-10-19
It is, I believe, a known bug in Gutsy on some configurations. You can look it up in Launchpad...
Just look for Gutsy and usplash...

Not sure if there is a workaround, but it seems that the boot process goes fine and eventually you can get to the login screen...

---

### Post by Bennett2005 on 2007-10-19
> **orange2k said:**
> It is, I believe, a known bug in Gutsy on some configurations. You can look it up in Launchpad...
Just look for Gutsy and usplash...

Not sure if there is a workaround, but it seems that the boot process goes fine and eventually you can get to the login screen...

Thanks Orange2k!

I'm a total newb at this, could you explain what Launchpad is, or post a link?

---

### Post by orange2k on 2007-10-19
> **Bennett2005 said:**
> Thanks Orange2k!

I'm a total newb at this, could you explain what Launchpad is, or post a link?

Launchpad is a system used by Ubuntu developers (all contributers including translators) and users.
It is used for bug-tracking, too.

Link:

[https://launchpad.net/ubuntu](https://launchpad.net/ubuntu)

---

### Post by Ramza001 on 2007-10-19
This seems similar to the problem i had, you can check the threads i was looking for help in for any useful information.

[http://ubuntuforums.org/showthread.php?t=555986](http://ubuntuforums.org/showthread.php?t=555986)

[http://ubuntuforums.org/showthread.php?t=555752](http://ubuntuforums.org/showthread.php?t=555752)

---

### Post by Bennett2005 on 2007-10-19
> **Ramza001 said:**
> This seems similar to the problem i had, you can check the threads i was looking for help in for any useful information.

[http://ubuntuforums.org/showthread.php?t=555986](http://ubuntuforums.org/showthread.php?t=555986)

[http://ubuntuforums.org/showthread.php?t=555752](http://ubuntuforums.org/showthread.php?t=555752)

It does sound very similar, I'll have to work on this when I get out of the office today.

Regarding the post from Mobad (thanks Mobad)


""" Originally Posted by mobad View Post
Heh you have the same video card I have... and the same problem I had.

Should be an easy fix.

Step 1: Ctrl + Alt + F2 and you should get something that asks for you user name.
Step 2: Type in your username and password.
Step 3: Type "sudo nano /etc/X11/xorg.conf" (without quotes) You will need to type your password.
Step 4: Look through the file and find a line like " Driver "ati" "
Step 5: Change the "ati" to "radeon"
Step 6: Hit Ctrl + X then "Y" then enter.
Step 7: Type "sudo /etc/init.d/gdm restart" (without quotes) You may need to type your password.

Are you just hitting Ctrl + Alt + F2 at the blank screen to bring up a command prompt?  Am I understanding that correctly?

I'll have to wait to get home to really dig into it.  Making me itchy to get out of here early.  :)

---

### Post by Chuck58 on 2007-10-19
This is similar to the problem I've been having with the 32 bit version on live CD. I downloaded twice from different mirrors. I get the opening screen with the little bar that moves back and forth, but when Ubuntu is fully loaded, my monitor goes to standby. 

Ubuntu and Kubuntu 7.04 work perfectly.

---

### Post by nhioi on 2007-10-19
im having the same issues on the amd64 version, however my card is a 8800gtx (nvidia)

---

### Post by mmmfottrell on 2007-10-19
Thanks for the reply on my post. Did you also try going through the restricted drivers manager and checking if your card support is there? 

With mine my card is there, but it comes up with an error. Might be an easy fix for your problem though.

---

### Post by picopir8 on 2007-10-19
It sounds like the blank screen is preventing you from installing, correct?

If so, at the boot menu, hit F6 to edit the boot command.  Then remove "splash" or replace it with "nosplash".  That should get you to boot up.  Selecting the "save graphics mode" or whatever should also fix it, though I think a few people still have problems with that.

Once you get it installed, you will need to hit escape when you first boot. then hit "e" to edit the boot command and again remove "splash" or replace it with "nosplash".  Hit enter to accept the changes then "b" to boot

After you boot up, enable "nvidia-glx-new" in the restricted drivers manager, you should boot just fine from then on, though you still wont see the splash screen.  If you do still freeze, then you will need to edit the grub command so it never uses the splash option (at least until the bug is fixed).

I must say, small bugs like this really irk me.  It is very minor but causes big headaches for people because its so unexpected.  It also gets me "those looks" from my wife whenever I mention how much easier Ubuntu is compared to Windows.  On the bright side, this only affects some 64  bit users but still annoying.  If it were not for these my wife would also be a convert.

---

### Post by Bennett2005 on 2007-10-19
> **picopir8 said:**
> It sounds like the blank screen is preventing you from installing, correct?

If so, at the boot menu, hit F6 to edit the boot command.  Then remove "splash" or replace it with "nosplash".  That should get you to boot up.  Selecting the "save graphics mode" or whatever should also fix it, though I think a few people still have problems with that.

Once you get it installed, you will need to hit escape when you first boot. then hit "e" to edit the boot command and again remove "splash" or replace it with "nosplash".  Hit enter to accept the changes then "b" to boot

After you boot up, enable "nvidia-glx-new" in the restricted drivers manager, you should boot just fine from then on, though you still wont see the splash screen.  If you do still freeze, then you will need to edit the grub command so it never uses the splash option (at least until the bug is fixed).

I must say, small bugs like this really irk me.  It is very minor but causes big headaches for people because its so unexpected.  It also gets me "those looks" from my wife whenever I mention how much easier Ubuntu is compared to Windows.  On the bright side, this only affects some 64  bit users but still annoying.  If it were not for these my wife would also be a convert.

Thanks!  If I'm using an ATI card and not nvidia, do I need a seperate command instead of the "nvidia-glk-new"?

Totally agree with you about the little bugs like this one, but I'm resolved to be patient and see what the general experience is like.  It stinks that I can't get my foot in the door to see what it's like without something like this popping up right away though. :)

---

### Post by picopir8 on 2007-10-19
Ooops sorry!  Nope, DO NOT install the nvidia driver if you have ATI.  Most people I know having problems have Nvidia, and I forgot this affects other cards.

Once you boot up, make sure you are using the correct driver for your card.  The problem does "go away" for most people after they are installed and have the correct driver.  I put that in quotes because you still will not see the splash screen but you will at least boot (screen goes black at boot and eventually comes back at the login screen).  However, for some people, if  the screen goes black it never comes back.  In that case, you will need to edit the grub boot command to remove the splash screen and put up with all the text being displayed until a fix is posted.

---

### Post by mmmfottrell on 2007-10-19
hey friend. i installed my respective ATI driver from the restricted drivers manager, but am still having the same problem. other recent posts have stated the same problem with what i think are regular dell factory vid cards so it may just be a glitch with 7.10 at the moment for some people. 

i tried that cmd stuff but it doesnt seem to be working properly. let me know if you find a solution and i will do the same.

---

### Post by mmmfottrell on 2007-10-20
Any luck?

---

### Post by DeanFX on 2007-10-20
> **Bennett2005 said:**
> It does sound very similar, I'll have to work on this when I get out of the office today.

Regarding the post from Mobad (thanks Mobad)


""" Originally Posted by mobad View Post
Heh you have the same video card I have... and the same problem I had.

Should be an easy fix.

Step 1: Ctrl + Alt + F2 and you should get something that asks for you user name.
Step 2: Type in your username and password.
Step 3: Type "sudo nano /etc/X11/xorg.conf" (without quotes) You will need to type your password.
Step 4: Look through the file and find a line like " Driver "ati" "
Step 5: Change the "ati" to "radeon"
Step 6: Hit Ctrl + X then "Y" then enter.
Step 7: Type "sudo /etc/init.d/gdm restart" (without quotes) You may need to type your password.

Are you just hitting Ctrl + Alt + F2 at the blank screen to bring up a command prompt?  Am I understanding that correctly?

I'll have to wait to get home to really dig into it.  Making me itchy to get out of here early.  :)


I tried this, nothign comes up in the black screen if i press ctl+alt+F2, or F1, or anything....it shows a blinking cursor fora half a second, and then stays blank.

Any other ideas?

---

### Post by pacsum on 2007-10-20
Here's the fix:
> To fix the no boot splash I did the following

1) Change the resolution in /etc/usplash.conf to 1024x768
2) Add vga=791 to the kernel line in /boot/grub/menu.lst
3) sudo update-initramfs -u -k `uname -r`
Thanks to **fcumok**

---

### Post by misfitpierce on 2007-10-20
Mine got stuck 1 time I hit CTRL+ALT+F1 and it started up... Only did first time I installed on other machine though. dunno

---

### Post by Bennett2005 on 2007-10-21
I didn't really get a chance to work on this until last night.

One thing I did notice:  When the screen goes black I lose USB support.  It actually happens when the initial live CD is loaded, I can't choose any menu options.  

Thinking that had to be something more than just a video problem, I downloaded  normal, non 64bit versions of kubuntu and ubuntu.  They both fired right up, no problems, 1400x800 res, sound, etc.

So now I'm wondering if my system configutation just isn't right for the 64 bit version of 7.10, but I'm also not sure how much I really care to dig into it right now.  I'm going to install the normal version and run with it for awhile.

Thanks for the feedback everyone, it's really appreciated.

---

