---
title: "can't start desktop"
date: 2007-03-08
forum: Absolute Beginner Talk
---

### Post by tjk on 2007-03-08
Something has happened to (k,x)ubuntu so that I can't start the desktops.  

When I boot I get to the session manager screen and it then drops to the command prompt.  I have tried replacing the xorg.conf with a backup -- as the last thing that I did was change the monitor settings.  But in reality I haven't rebooted the system in weeks, and I know that much has changed since my last boot.  

I currently am using xubuntu that I reinstalled from the command line using "sudo aptitude install xubuntu-desktop".  However, this setup doesn't recognize the installed packages in the /usr/bin directory, nor does it see my home directory (and data files).  But I have verified that all data/applications still exist and I can even start any program from within the file manager. (However, when I start a program like kmail, it does not see the settings/emails that I have, yet they still are there.)

Any ideas on how I can get my old system working again would be greatly appreciated. (or if not that, how I can get the current system to recognize all my data/apps/settings/etc)

---

### Post by Ferri on 2007-03-08
If the problem is in your xorg.conf you may try:
```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by tjk on 2007-03-08
> **Ferri said:**
> If the problem is in your xorg.conf you may try:
```
sudo dpkg-reconfigure xserver-xorg
```

I actually have tried that option -- so I believe that the xorg.conf can be ruled out as the problem.

---

### Post by tjk on 2007-03-08
Further  to my situation...

I was reading in a different thread about how someone removed the "quiet" and "splash" words from their grub line and replaced it with vga=791.  Well, this is weird because I tried it (and although I was given a text logon screen),  and I  was able to start xubuntu -- the best part was that it recognized all my files and applications.  Why would this be?  HOWEVER,  there was a downside in that I could not access the  internet.  So now I am back to using the live CD. 

Maybe  I've messing things up worse then they were before... hopefully not.  But I  don't know why this small change would have this kind of effect.  Can anyone  use this information to help me restore my original desktops (I was running  Xfce, gnome and mostly KDE).

---

### Post by ThunderNWTP on 2007-03-08
use the live CD and backup any data you need.

then consider reinstalling

---

### Post by tjk on 2007-03-08
> **ThunderNWTP said:**
> use the live CD and backup any data you need.

then consider reinstalling

I've been dreading this possibility.  I've spent hundreds of hours setting up applications and tweaking settings and now this.  I have to say that after using Linux for about half a year now, I question the statement that Linux is more stable then windows...  I have reinstalled several times something that I don't ever recall doing in Windows.  Will I switch back to Wndows?  Probably not ... because there are still some benefits to running Linux (part of which is the responsiveness of this forum/community).

But it can be very frustrating at times like this.

**One last question:**  Would anyone recommend deleting various files/directories and  then just reinstalling over the existing files (I'm not sure that you can do this with LiveCD as you have to format the root directory)?  I guess that I would like to think that I can at least preserve all the applications that I have installed...

---

