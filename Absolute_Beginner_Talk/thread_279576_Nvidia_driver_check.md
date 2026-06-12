---
title: "Nvidia driver check"
date: 2006-10-18
forum: Absolute Beginner Talk
---

### Post by whiterabbit on 2006-10-18
After every fresh install, I usually go through the usual apt steps just to install required codecs and drivers.  Today I thought, what the hell, I'll give Automatix a try. Anyway, all is well and it seems to have done an excellent job.

Considering the current nvidia driver exploit, does Automatix2 install the "nv" drivers or the affected "nvidia" drivers. I'm a little concerned about this. Any help is appreciated, thank you.

On a side note, is there a command line query that'll tell me which drivers I have installed(for future reference)?

EDIT UPDATE:

I checked /etc/X11/xorg.conf and it seems that I do have the nvidia drivers installed...

Section "Device"
    Identifier     "NVIDIA Corporation NV28 [GeForce4 Ti 4200 AGP 8x]"
    Driver         "nvidia"
EndSection

I've heard that changing "nvidia" to "nv" should fix the issue.  Can anybody confirm this?

---

### Post by velo on 2006-10-18
I think Automatix installs the "nvidia" drivers - the open source "nv" drivers are already installed in your normal Ubuntu installation so installing them would not make much sense.

I don't know a command which lists all your installed Drivers, but to quickly see your active display driver (among others, but you can easily spot "nv" or "nvidia"), you could do
```
cat /etc/X11/xorg.conf|grep Driver
```
which just outputs the lines of your xserver configuration file containing the string "Driver".

*EDIT:*
Just saw your edit, my reply was a little bit slow: Yes, you are right. Changing nvidia to nv enables the open source driver. But remember that you might encounter performance issues (3D acceleration, etc).

---

### Post by whiterabbit on 2006-10-18
Ah, that's a great command.  Thank you.  As you've probably missed, I'd already checked xorg.conf and I've confirmed that the nvidia drivers are installed.  

So it'd make sense to just change "nvidia" to "nv" followed by a reboot of x, right?

---

### Post by _simon_ on 2006-10-18
Be aware that the nv drivers do not have 3D hardware acceleration which is needed for Games and Compiz / Beryl etc.

I assume automatix is installing the stable nvidia drivers (1.0-8774), the latest beta drivers (1.0-9625) fix the exploit.

x86 
[http://www.nzone.com/object/nzone_downloads_linux_display_x86_1.0-9625.html](http://www.nzone.com/object/nzone_downloads_linux_display_x86_1.0-9625.html)

AMD64 / EM64T
[http://www.nzone.com/object/nzone_downloads_linux_display_x86_64_1.0-9625.html](http://www.nzone.com/object/nzone_downloads_linux_display_x86_64_1.0-9625.html)

---

### Post by 5-HT on 2006-10-18
> **whiterabbit said:**
> 
just change "nvidia" to "nv" followed by a reboot of x, right?

Yup, but you'll loose 3d accel (only provided for by the nvidia driver).

---

### Post by whiterabbit on 2006-10-18
Just saw your edit velo, sorry about the mix up. :P The only issue I'm having atm is that I'm currently upgrading the distro via apt so I can't modify and restart just yet.

---

### Post by xpod on 2006-10-18
> After every fresh install, I usually go through the usual apt steps just to install required codecs and drivers. Today I thought, what the hell, I'll give Automatix a try. Anyway, all is well and it seems to have done an excellent job.


I recall the thread from last night giving someone the advice to change the "nv" over to nvidia.....should be fine
Automatix\2 is still one of the first things i install 5 or 6 installs later
The drivers from automatix are one of the few things i havent had from it.:D

Edit..currently using the beta ones myself in beta edgy with beta beryl`s and it all seems to work even beta than my dapper:-D ....Could`nt get the 3d stuff working right in gnome but could in kde...in dapper

---

### Post by whiterabbit on 2006-10-18
How about after the exploit is patched.  Will I be able to just reinstall the drivers via apt?  

Sorry about the silly questions guys. It's kinda hard when I don't know what to search for.  Better to get all the questions answered than not.  I really do appreciate the help.

EDIT: Just read _simon_'s links.  My internet's running like a snail atm.

---

### Post by xpod on 2006-10-18
> Sorry about the silly questions guys. It's kinda hard when I don't know what to search for. Better to get all the questions answered than not. I really do appreciate the help.
Reply With Quote

No such thing as a stupid question m8......just stupid answers.
I cant really help with advice much as i just stumble along following "how to`s" and copying and pasting.....

If something goes wrong then i try and find out whats wrong,fix it...ask.
Failing all that it takes me about an hour to re-insatll and get back to whence i was.
Go back and look at some of my first threads if you want to see stupid "seeming" questions....only been on a pc a few months so ALL my questions are usually stupid....."seeming";)

EDIT...no need to go "back" and look...lol

---

### Post by whiterabbit on 2006-10-18
> **xpod said:**
> I recall the thread from last night giving someone the advice to change the "nv" over to nvidia.....should be fine
Automatix\2 is still one of the first things i install 5 or 6 installs later
The drivers from automatix are one of the few things i havent had from it.:D

Edit..currently using the beta ones myself in beta edgy with beta beryl`s and it all seems to work even beta than my dapper:-D ....Could`nt get the 3d stuff working right in gnome but could in kde...in dapperI'm a gnome user myself but I don't use beryl.  Will the upgrade to edgy(which I'm currently doing) automatically remove the nvidia driver anyway?

> **xpod said:**
> No such thing as a stupid question m8......just stupid answers.
I cant really help with advice much as i just stumble along following "how to`s" and copying and pasting.....

If something goes wrong then i try and find out whats wrong,fix it...ask.
Failing all that it takes me about an hour to re-insatll and get back to whence i was.
Go back and look at some of my first threads if you want to see stupid "seeming" questions....only been on a pc a few months so ALL my questions are usually stupid....."seeming";)

EDIT...no need to go "back" and look...lolThat's my net playing up again.  So slow but I'm trying to get this upgrade up and running ASAP.  Anyway, thank you.  Honestly, the Ubuntu community is the most helpful linux circle I've ever been involved with.  I've tried a few distros over the last month or so and the tech support in these forums is second to none.  Thank you.

---

### Post by velo on 2006-10-18
Thanks, _Simon_, I didn't know the beta driver (which I'm already running) fixed that. Nice.

> **whiterabbit said:**
> Just saw your edit velo, sorry about the mix up. :P The only issue I'm having atm is that I'm currently upgrading the distro via apt so I can't modify and restart just yet.
No Problem, glad I could help. 

The binary Nvidia package (the .bin file) does offer an uninstall option (I think running it with --uninstall does that - but check the readme to be sure). Just keep the file around.
After doing that you should be able to reinstall the packages with no problems.

EDIT: Boy, my English skills are way too slow for this thread. I don't think an upgrade removes the nvidia drivers. It just upgrades them if there's a newer version in the edgy repository.

---

### Post by xpod on 2006-10-18
All i did was follow the guides here for beryl and stuff on my edgy and my dapper....kde & gnome.

It`s got the lot i think

[http://ubuntuforums.org/showthread.php?t=263851](http://ubuntuforums.org/showthread.php?t=263851)

EDIT...you need to use the beta drivers i think to use edgys built in capabilities

---

### Post by xpod on 2006-10-18
> EDIT: Boy, my English skills are way too slow for this thread. I don't think an upgrade removes the nvidia drivers. It just upgrades them if there's a newer version in the edgy repository.

Your "English" skills are better than mine m8 so i reckon your doing ok;)

---

### Post by whiterabbit on 2006-10-18
Again, thanks for the help guys.

Ok, so here's the plan.  

1. Complete dist-upgrade.

2. Change to "nv" drivers in xorg.conf

3. Uninstall installed nvidia drivers (I have no idea how)

4. Install the new beta nvidia drivesr (I have no idea how)

5. Go back to step 3 if things don't work out

6. Post here in a fit of confusion if step 5 doesn't work

That sound about right?

---

### Post by xpod on 2006-10-18
If you used A2 for the nvidia drivers then it uninstalls simply now too.
I followed the full beta driver\beryl "how to" in the link i gave you and never had to change the "nv" bit over.....just had to follow the instructions and it was suprisingly easy:D 

Not sure about your "dist-upgrade as i just DL the edgy cd last friday and installed to a  second hd...boy it did\does some upgrading\updating though.
300 to start and over a 100 since.

---

### Post by whiterabbit on 2006-10-18
I think it's all done.  There were some really intense issues with x after the upgrade but all is good now.  

I uninstalled the nvidia drivers by sudo apt-get remove nvidia-glx and managed to install the beta drivers not long after.  Everything seems to be going well now so thanks for the help guys.

---

### Post by whiterabbit on 2006-10-18
Irrelevant post.

---

