---
title: "ipod wont copy files"
date: 2008-03-21
forum: Absolute Beginner Talk
---

### Post by asnd16 on 2008-03-21
I am using Amarok and when I transfer the files they are in the music folders on the ipod but do not appear on the ipod when I unplug and try and view them. . or play them.   Any I ideas?  the playlists do not show but when remounting they appear.  . I just purchased the ipod so I think its the latest version.

---

### Post by Linux_Man on 2008-03-21
Did you unmount the iPod? Because if not that could cause that if you just pulled the cord.

---

### Post by komori on 2008-03-21
Update to Gutsy and install libgpod3. Then run

sudo lsusb -v | grep -i Serial

Copy the 16 number string that you'll get and open /iPod_Control/Device/SysInfo with gedit. Add the following line and save

FirewireGuid: 0x935894375987

where the random numbers after "0x" are the 16 number string you copied before.

---

### Post by asnd16 on 2008-03-21
Yeah . . .well apparently libgpod3 is for hardy. .  I tried another approach for that and still did not work.  I think I will just upgrade Hardy and see what happens . . I have been meaning to do it anyway. .

---

### Post by komori on 2008-03-21
It works on Gutsy!

---

### Post by szandor on 2008-03-21
> **asnd16 said:**
> Yeah . . .well apparently libgpod3 is for hardy. .  I tried another approach for that and still did not work.  I think I will just upgrade Hardy and see what happens . . I have been meaning to do it anyway. .

buck up little camper. libgpod3 has been backported for gutsy users. just do a google search for the libgpod3 package and install it manually. you may even be able to find a repo by now.

edit: this may help: [http://ppa.launchpad.net/ipod-touch/ubuntu/pool/main/libg/libgpod/libgpod3_0.6.0-3~ppa1_i386.deb](http://ppa.launchpad.net/ipod-touch/ubuntu/pool/main/libg/libgpod/libgpod3_0.6.0-3~ppa1_i386.deb) which is from [http://www.soccio.it/michelinux/2008/01/27/gtkpod-09912-backport-for-ubuntu-gutsy-gibbon/](http://www.soccio.it/michelinux/2008/01/27/gtkpod-09912-backport-for-ubuntu-gutsy-gibbon/)

> **komori said:**
> It works on Gutsy!

i guess i should get around to finally trying out ipod in linux. thanks for the status on libgpod.

---

### Post by asnd16 on 2008-03-22
Yeah now I see the backports . . .its ok Hardy works great!!! Except the firefox . . and flash audio. . .but other than that I got it working great in HArdy.

---

