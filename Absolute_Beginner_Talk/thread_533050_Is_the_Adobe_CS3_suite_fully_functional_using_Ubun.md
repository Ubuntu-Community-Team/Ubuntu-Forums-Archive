---
title: "Is the Adobe CS3 suite fully functional using Ubuntu + rdesktop???"
date: 2007-08-23
forum: Absolute Beginner Talk
---

### Post by Ashok0 on 2007-08-23
Hi,

Right now I'm using Windows Vista but I've been debating if Ubuntu would be a worthwhile switch.  I tried Ubuntu quite some time ago but ended up deleting it due the a lack of support for the CS3 suite.  I'm afraid I don't care much for Inkscape or GIMP, and CS3 is a necessity for me.  I'm also not to keen on relying on a cumbersome VM like vmware. 

However, I read that Ubuntu 7 has an experimental "seamless Windows" mode where you can run Windows applications like they are Linux apps.  I have a Core 2 Quad Q6600 with 2GB of RAM and a GeForce8800GTS 320mb.  Would I be able to run CS3 at close to native speeds using Ubuntu + rdesktop?  Would Ubuntu be a good fit for me, or should I just continue to use CS3 natively in Vista???

---

### Post by moffa on 2007-08-23
Well I can say it doesn't work with wine.  I haven't seen anything about this seamless windows mode but maybe someone else could help.

---

### Post by Golyadkin on 2007-08-27
I think that the seamless Windows mode you mean is actually a VirtualBox or VMware virtual machine running Windows XP or Vista, which has CS3 installed on it. The point is to create a shortcut in your Ubuntu menu that starts the virtual machine in a window with the program fullscreen in that window, using guest additions to make the mouse work without explicitly granting focus. Then using the folder sharing functionality you can let CS3 open and save files from your Ubuntu partition. 

There is an extensive guide somewhere here on the forums, check it out.

---

### Post by cmat on 2007-08-27
If you make adobe photoshop portable I've read that it will work in WINE quite well. 

This is CS2 but it worked for me. Maybe it will work with CS3? 

[http://luiscosio.com/how-to-adobe-photoshop-cs2-on-ubuntu-10-steps](http://luiscosio.com/how-to-adobe-photoshop-cs2-on-ubuntu-10-steps)

---

