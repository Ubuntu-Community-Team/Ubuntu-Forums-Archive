---
title: "grub confusion"
date: 2010-07-06
forum: Apple Hardware Users
---

### Post by nourathar on 2010-07-06
dear community members,

i installed ubuntu 10.04 next to os x and managed to get it to work. I was rather proud since I'm a complete Linux newbie, was installing things and getting to like Linux. Now it seems that after every software update, or after restarting when being promted to do so, I do not get past grub.
At the moment I get stuck at the point where it says "GRUB _" with a flashing cursor (not a shell, pressing keys does not seem to have an effect).
I've learned how to start up from a live cd and chroot into the system on my HD and previously have gotten things to work by running update-grub in that way, but this second time also that doesn't seem to work.

When browsing around it seems there are various grub folders and I'm getting the feeling there's perhaps too many of them and that perhaps I'm updating an instance that is not the right one. Is that possible or am I being paranoid ? 
exactly where is the boot/grub folder that is being used ? is that boot/ directory in the same directory as the etc/ directory containing etc/default/grub ?
and how do those location look when you've 'chrooted' into your system ? I guess I'm also sort of confused by what the root is when you chroot and how that relates to the root when you start up normally from the HD.

I do remember that I installed grub on /dev/sda3 and that later in a moment of confusion I also installed it on /dev/sda
I use rEFIt and now I see two linux penguins, one saying 'start up from HD', the other saying 'start up from Partition 3'. The partition 3 one worked at some point, the HD one never did anything. Can it be that rEFIt is conflicting with the GRUB I installed on /dev/sda ?

can somebody please explain what the preferred state of affairs is and point a way how to get there ?

thanks !

---

