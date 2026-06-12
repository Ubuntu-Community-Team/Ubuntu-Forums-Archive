---
title: "System Crashes / Won't load past login"
date: 2007-01-31
forum: Absolute Beginner Talk
---

### Post by pope8 on 2007-01-31
Hi,
  I'm new to using Ubuntu.  I installed version 6.10 using the live setup (everything worked perfect and I really liked the OS, enough to dump my hard drive with the plan to use it as my main OS).  After reboot, the login screen appeared.. I entered my u:p in, but the screen only made it to a "light colored" brown "something", where I was able to do nothing other then move my cursor.  If I leave it here, my computer will just shut itself off after a few mins.  I am able to [ctrl+alt+bkspace] to the login screen and [ctrl+alt+F1], but it tends to crash for no reason during these as well.  If I play around with the menu, once in every few tries, I'm able to get other part of the gnome desktop loaded (usually just the background), but on occasion I get the fully working environment.  After about 20-30 mins, I'll get a crash here as well.  I haven't ever used Linux as my personal OS.. I have to assume something is wrong with the installation (though I've re-installed many times now).  I can run the live-dvd and use the OS for hours at a time with no problems.  Does anyone have a clue what is wrong.  I desperately need to get my notebook working so I can get some .cpp files finished, debugged and sent off ASAP.  Any help will be great.

POPE

---

### Post by mid_night gypsy on 2007-01-31
pope8,
 I am kinda at a lost with this one.It's sounds like it's xorg related.Oddly,I had a simalar problem it was fix by changing the speed of my dvd-rw,That's fix my half-boots,locks-ups. Try ctrl+alt F1 login (if you can) and type   sudo dpkg-reconfigure -phigh xserver-xorg after that type  startx
 hope this helps gypsy

---

### Post by pope8 on 2007-01-31
I set the graphics card to ATI using your command.. tried startx -> was given a Fatal server error: Server is already active for display 0.  If this server is no longer running, remove /tmp/.X0-lock and start again... along with a bunch of other Server error jargin.  I went on a long shot and tried to remove the file that was mention.  Wasn't a "permitted" operation.. so I'm assuming it is write-protected.

Any other suggestions?

EDIT-> just did a reboot.  The settings have changed, only noticable by the resolution change.  When I tried logging in, it started the GNOME bar, and then just stops and stays that light brown color.  Sometimes I get a light gray box at the top left of my screen.  This is very frustrating.

---

### Post by mid_night gypsy on 2007-01-31
pope8,
 Run those commands again,But choose vesa as your graphic driver.This is what the live dvd/cd
uses. And if this works you can use this webpage to download the envy script(easy and installable .deb file) for your ATI driver.    [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)
 gypsy

---

### Post by pope8 on 2007-01-31
Same thing happens.  I enter user name, then my password.  The gnome menu comes up.. the icons load until "nautalus" (spelling may be off), desktop picture loaded, but nothing else.  If I leave it there, a warning for my laptop battery appears.. but nothing else.  Any other suggestions?

---

### Post by mid_night gypsy on 2007-01-31
pope8, 
 Well,You could try installin' Dapper or you could try the alt. install cd (boring text install, real easy) for Edgy.Some people have had trouble with Edgy and or ATI,But the alt. install cd seems to help.
gypsy

---

### Post by pope8 on 2007-01-31
I'll attempt the reinstall using the text installer.  I used the OEM installer before and had problems.  I'm not sure how to install dapper or edgy (though I've seen them in quite a few other posts) and assumed they were lower end..  I'll have to look them up.  I'll let you know what happens after this installation.

---

### Post by pope8 on 2007-01-31
tried the installation.  At 99% my computer shut down.  I restarted and ejected the disc.. I got a loading error.

GRUB Loading stage1.5.

GRUB loading, please wait...
Error 15

I have no idea how to fix the problem.  I hate this.

---

### Post by mid_night gypsy on 2007-02-01
pope8
 Sometimes,linux can be a pain.Please don't give up!Maybe try a Dapper install.best of luck.
gypsy

---

### Post by pope8 on 2007-02-01
/bump -> any other suggestions?

-> Just noticed something else that doesn't seem right.  The login sounds are fine, but as GNOME is loading.. the music only plays about 1/4-1/2 and then stops..

---

### Post by tyler_roach on 2007-02-01
Try this:
When you come to the login screen select Sessions > Failsafe Terminal, then login. Hopefully, that should bring up a command prompt somewhere on the sreen. When it does, enter the following (in successive lines):

sudo dpkg-reconfigure gnome-desktop-data
sudo dpkg-reconfigure gnome-control-center
sudo dpkg-reconfigure gnome-menus
sudo dpkg-reconfigure gnome-system-tools
sudo dpkg-reconfigure gnome-applets
sudo dpkg-reconfigure gnome-session

Let me know if that doesn't work.

---

### Post by pope8 on 2007-02-01
Nope.. still crashing and not loading for me..

---

### Post by shareMenaPeace on 2007-02-01
Had a slightly diffrent prob and

[HTML]killall gnome-panel[/HTML] worked.

Also would be good if you can say what error you read when the install broke at 99%?

---

### Post by pope8 on 2007-02-01
I tried using Kubuntu today as well.  I keep getting a sound server error.  I'm wondering if that is what is crashing during ubuntu as well.. since it lags after the sound stops working.  Might be a long shot here.. but I really want this OS up and running so I can get some work done.

---

### Post by tyler_roach on 2007-02-02
Look at this thread, same problem:

[http://ubuntuforums.org/showthread.php?t=351109&goto=newpost](http://ubuntuforums.org/showthread.php?t=351109&goto=newpost)

If the sound sever error you're getting with KDE is something like "cpu overload, aborting.." Then it's a fixable quirk with KDE, and has nothing to do with Gnome crashing.

---

### Post by pope8 on 2007-02-02
yeah.. that is the error I was getting.  If I enabled the sound server.. instant crash.  The only reason I assumed maybe it was similar is because it was crashing other desktop apps before the system crash occurred.  I assumed that it may have been a sound issue and not a GNOME issue.  I am a member of a local UNIX user group, and I've done plenty of GNOME fixes, etc; with no positive results.  I like the Kubuntu a bit, so I guess I'll just use this for a while, though I was hoping to work with the GNOME environment a bit... ahh well.. Hopefully I'll get some time to look at this issue in the future.

---

### Post by tyler_roach on 2007-02-02
You should be able to rectify that error message in KDE by going to K Menu > System Settings> Sound System > Hardware , and changing the audio driver. My sound card happens to work with  the Threaded Open Sound System driver.

---

