---
title: "Ubuntu 12.04 can't install apps after getting OpenGL working"
date: 2013-06-10
forum: Apple Hardware Users
---

### Post by Dukenukemx on 2013-06-10
I install 12.04 on my PowerBook G4 and everything went smoothly, until I got opengl working.  Following [this link](https://wiki.ubuntu.com/PowerPCKnownIssues) to get hardware acceleration working worked out just fine.  Except I can't install software.  In terminal complains about dependencies.  These dependencies.  

 libgl1-mesa-glx
 libgl1-mesa-glx-dbg
 libgles2-mesa
 libgles2-mesa-dbg
 libglapi-mesa-dbg
 libglu1-mesa
 libglu1-mesa-dev

I've tried "sudo apt-get update" and "sudo apt-get -f install" and have no luck.  What can I do to fix this?

---

### Post by rkmugen on 2013-06-11
Exactly which steps on this page ([https://wiki.ubuntu.com/PowerPCKnownIssues](https://wiki.ubuntu.com/PowerPCKnownIssues)) did you follow?

---

### Post by Dukenukemx on 2013-06-11
**No userspace mode setting 3d hardware acceleration**

---

### Post by rkmugen on 2013-06-11
I think you'd have better results if you downloaded ALL 4 .deb files and made extra certain that they are all of the same version.  I'd imagine that looking at such a long list of packages can be a serious strain on the eyes.... so I collected the links to the exact files you'd need.  Just click and download them all to a folder.

   
[LIST]
[*][http://ports.ubuntu.com/pool/main/m/mesa/libgl1-mesa-dri_7.11-0ubuntu3.2_powerpc.deb](http://ports.ubuntu.com/pool/main/m/mesa/libgl1-mesa-dri_7.11-0ubuntu3.2_powerpc.deb)
[*][http://ports.ubuntu.com/pool/main/m/mesa/libgl1-mesa-glx-dbg_7.11-0ubuntu3.2_powerpc.deb](http://ports.ubuntu.com/pool/main/m/mesa/libgl1-mesa-glx-dbg_7.11-0ubuntu3.2_powerpc.deb)
[*][http://ports.ubuntu.com/pool/main/m/mesa/libglapi-mesa_7.11-0ubuntu3.2_powerpc.deb](http://ports.ubuntu.com/pool/main/m/mesa/libglapi-mesa_7.11-0ubuntu3.2_powerpc.deb)
[*][http://ports.ubuntu.com/pool/main/m/mesa/libglu1-mesa_7.11-0ubuntu3.2_powerpc.deb](http://ports.ubuntu.com/pool/main/m/mesa/libglu1-mesa_7.11-0ubuntu3.2_powerpc.deb)
[/LIST]
 
Open up a terminal window and navigate to the folder.  Then type this into your terminal to install them all at the same time:
```
sudo dpkg -i *.deb
```

Finally, reboot.
```
sudo reboot
```

If that doesn't work out, just post back here with the results.

---

### Post by Dukenukemx on 2013-06-11
I reinstalled Ubuntu 12.04 and downloaded your files and got the same thing.  

Did you want me to download "libgl1-mesa-glx-dbg_7.11-0ubuntu3.2_powerpc.deb"?  Though when I run "sudo apt-get -f install" it just complains about  "libgl1-mesa-glx-dbg".  I got the 8.04 version of that file and the error seems to be gone.  Though I haven't tried to get 3D working yet.

**EDIT**

Made changes to yaboot.conf and xorg.conf and still unknown comes up for graphics.

---

### Post by rkmugen on 2013-06-11
I guess I'm a little out of my league since I don't own a G4-based Mac.  However, I do not believe you need libgl1-mesa-glx-[SIZE=3][COLOR=#ff0000]_**dbg**_[/COLOR][/SIZE]_7.11-0ubuntu3.2_powerpc.deb.  Also, I think the problem lies in the combination of packages that you have installed, prior to attempting to downgrade MESA to 7.11.x.  I don't believe any changes you make in  either "yaboot.conf" or "xorg.conf" would have any bearing over the mix of packages involved in downgrading MESA.

I'm using an iMac G3 and Ubuntu 12.04 and I was actually able to install all 4 of those files I listed (with nothing else).  And right after I rebooted, I made sure to "pin" them (or "lock" them) in the Synaptic package manager.

Anyone else here have other suggestions?

---

### Post by Dukenukemx on 2013-06-12
Well I didn't pin them.  I didn't have Synaptic package manager.  How do you pin then exactly?

**EDIT**

Got it to work, I figured out that you need to lock the files with Synaptic Manager.  Which doesn't come installed in 12.04 and had to get it before dealing with the mesa files.  Getting 1226 FPS with Glxgears.  Gotta thank zeroti, [his thread still comes in handy to this day.](http://ubuntuforums.org/showthread.php?t=1460926&page=2&p=9194781#post9194781)

Oh BTW thanks for your help.

---

