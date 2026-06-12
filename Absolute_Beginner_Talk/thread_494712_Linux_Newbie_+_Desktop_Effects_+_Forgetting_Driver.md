---
title: "Linux Newbie + Desktop Effects + Forgetting Drivers = Blank Screen! (Help needed)"
date: 2007-07-07
forum: Absolute Beginner Talk
---

### Post by ZipperInt on 2007-07-07
So, after getting help installing Ubuntu 7.04  yesterday, I was all excited to try out different features, one of which was 'desktop effects'. After(foolishly)  ignoring the warning message that it was not completely stable, I enabled desktop effects and immediately got a blank grey/white screen. My system is completely functioning, I just can't tell what is going on - all I can see is the cursor and a blank background.

The drivers I have installed obviously don't support the desktop effects option, so I need to turn it off. Being the Linux rookie that I am though, how do I go about doing this if I can't see use the GUI? I can access the command line by either loading the recovery mode, or by using the xterminal at the login screen, but I don't know where to find the file that can help me, and what I need to do once I find it.

Thanks!

---

### Post by shearn89 on 2007-07-07
This is known as the "white screen of death" or WSD. Its a common occurence when trying to get Beryl working. I think (as i tried it myself and got a similar result) when you click on "enable desktop effects" and got a white screen you could have pressed escape, and it would have cancelled it for you. I'll just do a quick search and try and find a solution now that you've left the dialog window...

---

### Post by overdrank on 2007-07-07
> **ZipperInt said:**
> So, after getting help installing Ubuntu 7.04  yesterday, I was all excited to try out different features, one of which was 'desktop effects'. After(foolishly)  ignoring the warning message that it was not completely stable, I enabled desktop effects and immediately got a blank grey/white screen. My system is completely functioning, I just can't tell what is going on - all I can see is the cursor and a blank background.

The drivers I have installed obviously don't support the desktop effects option, so I need to turn it off. Being the Linux rookie that I am though, how do I go about doing this if I can't see use the GUI? I can access the command line by either loading the recovery mode, or by using the xterminal at the login screen, but I don't know where to find the file that can help me, and what I need to do once I find it.

Thanks!

Hi when you load ubuntu to the blank screen you should be able to just restart x with the key ctrl,alt,backspace all at the same time, then login in to then gnome safe session, you can do this by choosing the options in the lower left corner of the login in screen hope this helps,:popcorn:

---

### Post by shearn89 on 2007-07-07
okay - just found this:

get to a terminal, and type ```

sudo mv /etc/X11/xorg.conf ~/xorgbackup
sudo gedit /etc/X11/xorg.conf
```
then add this to that file:
```

Section "Extensions"
           Option "Composite" "Disable"
EndSection

```
then save, quit, and restart to get back to the GDM login. Hopefully you should now get a normal desktop.

---

### Post by ZipperInt on 2007-07-07
Thanks for the replies!

Using Gnome failsafe mode still gives me the problem, so I tried the code above. Unfortunately, I somehow managed to delete my xorg.conf file and was unable to replace it with the backup, so I ended up using "dpkg-reconfigure -phigh xserver -a", which worked, but was overkill for what I needed (xserver-xorg was what I wanted). 

I now have  a working GUI, but was wondering if I deleted things using the "dpkg-reconfigure" command - I can't seem to find the 'Composite' extension anymore.

---

