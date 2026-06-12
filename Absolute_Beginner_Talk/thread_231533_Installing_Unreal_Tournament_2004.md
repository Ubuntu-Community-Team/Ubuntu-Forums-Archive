---
title: "Installing Unreal Tournament 2004"
date: 2006-08-07
forum: Absolute Beginner Talk
---

### Post by WPAStrangla on 2006-08-07
What exactly Should I run when installing UT 2k4? I tried running the Linux-Installer.sh, a screen popped up, and dissapeared.


[[IMG]http://img244.imageshack.us/img244/8701/screenshotup5.th.png[/IMG]](http://img244.imageshack.us/my.php?image=screenshotup5.png)

---

### Post by davebgimp on 2006-08-07
Did you check the Ubuntu gamers forum on this site? It's a good place to start looking.

---

### Post by Shay Stephens on 2006-08-07
copy the linux-install.sh file to the desktop or some place handy, change the permission to allow execute, and then run the sricpt.  Easy breezy :-)

---

### Post by WPAStrangla on 2006-08-08
I followed your instructions but it then said 

Failed Permissions
"No write Permission to /usr/local/games"

What am I doing wrong?

---

### Post by davebgimp on 2006-08-08
It's a permissions issue. Since /usr/local/games/ exists outside of /home/, it is owned by root. You can either change where you install it to a place in you own home folder or perhaps try running the install as root using sudo. Last ditch, you can change the permissions on /usr/local/games/ to give your user account write access.

---

### Post by Perfect Storm on 2006-08-08
[http://gaming.gwos.org/index.php?option=com_content&task=view&id=75&Itemid=63](http://gaming.gwos.org/index.php?option=com_content&task=view&id=75&Itemid=63)

---

### Post by BooDa on 2006-09-25
Ok I'm gonna carry on this topic because I seem to be having a problem with the install as well.
I can get the installation to run under su, and it starts to install, but it then asks for the second CD, so I try to eject the first cd on the GUI desktop and it says that it is busy. So I open up another term program and get into su mode and try to unmount the cd that way, nope it says it's busy too. So the only way I can get the cd out from this point is to cancel the installation.....counter productive I think](*,)
Any ideas?

---

### Post by BooDa on 2006-09-26
Ok then........ I guess I'll post this in the gaming section:-k

---

### Post by Perfect Storm on 2006-09-26
Try copy the installer script to the hard drive and run the script from there.

---

### Post by buffy^ on 2006-09-26
Do you have a pin?

If so slide in the hole by the side of the drive and "pop" out comes the CD

---

### Post by coolbian57 on 2006-09-26
I don't know about you but this game owns.  

I really don't have any insights on the issue however.  I have little experience with Linux yet.  

Just thought a fellow UT player should post :D

---

### Post by Brascocampbell on 2006-11-05
here is what i did:
i too had the permission problems as well,so i did this when it asked where to put the game
i put it in my /home/scott/ folder like this:
/home/scott/UT2004
it then asked if i wanted a symbolic link,and i answered yes,and then it asked
for the path to that as well,so i filled that path exactly as i did before.
as for ejecting the cd,you can right click the cd icon on the desktop and then eject it,and put the next cd in(it will automount in most cases) then click re try.as you do this when installing the next cd it will pop up a window with the contents of the cd,just close that out and ignore it.this is my all time favorite game,and i have installed it on suse,and fedora core,and ubuntu.all are similar,but so far this one is easiest.i went through a lot of steps to get the nvidia 3d grapihics working,but not sure what i did to enable it,but i have been there and gotten through that before.

---

### Post by Death_Sargent on 2007-04-27
> **Shay Stephens said:**
> copy the linux-install.sh file to the desktop or some place handy, change the permission to allow execute, and then run the sricpt.  Easy breezy :-)

That fix worked for me (running Fiesty)

Just remember before running chmod it "a+x"
```
Death_Sargent@Death_Sargent-laptop:~$ chmod a+x /home/Death_Sargent/Desktop/linux-installer.sh
Death_Sargent@Death_Sargent-laptop:~$ /home/Death_Sargent/Desktop/linux-installer.sh
Copying to a temporary location...
Verifying archive integrity... All good.
Uncompressing Unreal Tournament 2004 for GNU/Linux 3186......................................................................



```

I just dragged and dropped the installer onto my desktop from a nautilus (default gnome file manager) onto my desktop

Before you ask how i got my local user name like that I just edited it for security reasons

---

### Post by firebird84 on 2007-04-28
How do I get the bloody thing to run in th center of one monitor?  I run a dual monitor setup (twinview) and it's as though the ut2k4 window is centering itself on the right edge of the right monitor.  I can't figure out how to play my favorite game :(.

---

### Post by MCMcButtah on 2007-04-30
I have this exact same problem. I think it might have to do with metamodes. If I can get it to work
i'll post the solution here.

---

### Post by MCMcButtah on 2007-05-01
Well I tried a million different combos in my xorg.conf and nothing worked. The best I was able to do was in metamodes have "NULL, 1920x1200" which shuts off the unused monitor but unreal 2004 is still 1/2 across the screen on my main display.

Just a  note that this is not limited to only unreal tournament 2004, but many full screen things. Such as the visualization plugs for amarok will be 1/2 across my primary display. Anyone have any ideas?

---

### Post by Absolut139 on 2007-10-04
Can't seem to get this working.  Tried a couple things, maybe ya'll could point me in the right direction.  I chmod a+x before executing the script and got this error:
rick@rick-desktop:~/Desktop$ ./linux-installer.sh
Copying to a temporary location...
Verifying archive integrity...Error in MD5 checksums: f9a3c76dee8651520db812e5e285d178 is different from 34d72f0a4c06f7da084a8a1653a0bae4

I have no idea whats going on...I'm a complete linux beginner, please help.

---

### Post by Absolut139 on 2007-10-05
Well after a little more research I can see that my linux-installer.sh file is apparently not valid because it doesn't pass the MD5 checksums.  For some reason the UT2004 dvd i got doesn't have the linux-installer.sh file so i followed a link in this forum, maybe its a bad file.  does anyone know where i can find linux-installer.sh or if this is actually the problem i'm having.  Thanks.  I really want to stay with linux but i'm having so much trouble installing.  i wish i had stayed in computer science class :confused:

**Fixed problem

---

### Post by wililupy on 2008-04-26
I have a totally unrelated question...

Has anyone been able to successfully run UT2004 on 8.04? 

The first problem I had was that I was missing the DirectFB libraries. Come to find out that they are no longer a 0.9 but an official 1 now. So I made symbolic links to the old names so that unreal would work, and now I have a problem where the mouse lags behind. I can't even get the game to start up from the main menu beucase when I go to click on Multiplayer, the mouse cruises right past it and goes to the other side of the screen, even though I am not moving the mouse. 

I never had this issue when I ran 7.10, what gives?

---

### Post by nukecoder on 2008-05-07
I'm having the exact same issue as wililupy.  The mouse seems to have a mind of it's own and just zooms past then seems to reset at the bottom right of the screen.  Anyone have any idea on how to fix this?

---

### Post by -gabe-noob- on 2008-06-20
I'm just trying to get it to run :O

---

