---
title: "Kernel Update &amp; Nvidia drivers."
date: 2006-03-19
forum: Absolute Beginner Talk
---

### Post by Pelham123 on 2006-03-19
Hi there.

Recently made the jump from M$ and I must say its all gone pretty well, largely thanks to all the HOWTOs, etc from this site ;) 

One question though...

The update list that pops up after I login contains a fairly long list of updates including a Linux Kernel Image 2.6.12-9.386 entry. If I update this, will this affect my Nvidia driver (1.0-8178 )?

I did try RH FC3 many months ago and had all sorts of command line hair-pulling with kernel versions and installing drivers. I am loathed to update anything to do with the kernel when all is going well, but the update list does contain quite a few apps etc that I wouldn't mind getting. But I'm thinking some will probably be tied into the new kernel version. Just need to know if both the kernel version and Nvidia drivers are compatible? Or will I need to re-install drivers?

Thanks

(Automatix...\\:D/  too cool \\:D/ )

---

### Post by hobbit1983 on 2006-03-19
Pelham123,

I would accept all the updates that are suggested including the kernel image.  I use the Nvida packages that are in the standard repos for my graphics card.

Occaisionally after updating the linux image I lose 32 functionality.  No issues really entering the command

sudo nvidia-glx-config enable

This brings my card back to life
Hope this helps

---

### Post by Pelham123 on 2006-03-19
Went without any problems :) - thanks for the reply though

---

### Post by ububaba on 2006-03-20
[QUOTE=Pelham123]Went without any problems :) - thanks for the reply though[/QUOTE]
****


I updated the kernel and the last thing I did was to install nVidia, very strictly
following the instructions which you have provided. (Scouts honour). When I did
a restart all went fine to the point when you hear the jingle. But when the login
screen should appear, it went blank and black. The login screen is apparently
there waiting but is unseeable due to some conflict between Ubuntu's own default 
values and nVidia's graphics. I thought better to seek advice from the gurus on 
the forum than foul up further by loging in Safe Mode. 

Obviously I am writing this, thanks to the services provided by world's poorest
guy who lives in Seattle. I wish my life was not as rosy as his.

---

