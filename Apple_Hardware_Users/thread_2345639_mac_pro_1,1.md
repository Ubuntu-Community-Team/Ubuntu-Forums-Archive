---
title: "mac pro 1,1"
date: 2016-12-06
forum: Apple Hardware Users
---

### Post by yaboo on 2016-12-06
Hi All

I guess this has been asked about a billion times now.

I have downloaded the ubuntu 14.04.5 desktop amd64+mac iso and burnt it to a dvd.

I am able to boot the dvd, use gparted and go through the motions of installing ubuntu upon my mac pro 1,1.

When it comes time to install grub upon the disk it fails and any other disk I try fails also. Is there some secret sauce/magic to install grub upon the macpro 1,1.

Another question. I have a non mac nvidia 570 gtx card. Will this work under the macpro like osx where the boot screen is black till a login prompt has been made?

Joseph

---

### Post by yaboo on 2016-12-06
Hi I have been able to install ubuntu server no issues and boot the macpro 1,1 When I install ubuntu 14.04.5 dvd the unit seems to just hang when trying to boot.

Is there same secret kernel sauce I need to add.

Joseph

---

### Post by yaboo on 2016-12-07
Another update, I am able to install 14.04.5 server upon the machine and boot. Could I from there do a install to make it a desktop distro?

---

### Post by yaboo on 2016-12-07
I have been able to do a upgrade to 16.10. I had to modify the /etc/default/grub to allow it to boot upon the upgrade.

I added my nvidia 570gtx card and seem not to get a command prompt. I can still ssh into the server.

Is there a way to get the nvidia card working with the command prompt. 

I am downloading ubuntu 12.04 amd+mac desktop and see if this iso works. It seems desktop 16.04.5 does not work for mac.

I will keep plodding along. Eventually I will blog about this as there seems not to be any information in one single area.

---

### Post by yaboo on 2016-12-07
I am able to boot with the nvidia 570gtx card. The machine takes a total of five minutes .

Able to update to 16.10.

Now compiled a list of packages on my ubuntu laptop and transfered it over to the macpro 1,1

See if installing all the packages as the laptop turns it into a desktop unit.

---

### Post by yaboo on 2016-12-08
I am going to try 12.04 amd64+mac iso and see if this works. It maybe faster and easier just to upgrade than to configure all the hardware in the long run.

---

### Post by yaboo on 2016-12-11
Ok I tried the 12.04 desktop iso and it failed at thegrub install. I re-installed 14.04.5 server iso and just upgraded to 16.10. Added ubuntu-desktop, sound works, nvidia drivers added. So far so good. Just need to be able to configure the network card from the desktop. I am so far not able to add a mouse via the bluetooth.

---

