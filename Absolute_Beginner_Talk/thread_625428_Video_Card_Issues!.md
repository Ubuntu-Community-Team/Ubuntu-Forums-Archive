---
title: "Video Card Issues!"
date: 2007-11-28
forum: Absolute Beginner Talk
---

### Post by Misfitsman805 on 2007-11-28
ok well i have a problem with my video card setup!
I want to just run 2 displays on my agp card which is a nvidia geforce 7800 GS CO
but the problem is i have 2 video cards which equal 3 displays in total,
so one is pci and the other is agp
when i start up it automatically switches to the pci as the main video card
and then i do not get any video from the agp video card,(which i would like as my default card and display)
is there anyway of disabling the pci video card in linux?

hope someone can help with this problem

AMD Athlon Xp 1800+
1GB drr memory
nvidia geforce 7800 gs co
ati 3d rage pro turbo pci
ubuntu 7.10
win xp pro
80 gb maxtor
500 gb maxtor
30 gb ibm travel star

---

### Post by x64Jimbo on 2007-11-28
Just thinking outside the box here... have you tried removing the PCI card? If you're not going to use it, you might as well not even have it in the PC, right?

---

### Post by Misfitsman805 on 2007-11-28
yeah i wish it were that easy though lol
i use 3 displays in win xp,works out nice in there.

thank you for the response though.

---

### Post by overdrank on 2007-11-28
> **Misfitsman805 said:**
> yeah i wish it were that easy though lol
i use 3 displays in win xp,works out nice in there.

thank you for the response though.

Hi and have you tried to set the primary graphics in bios? Maybe it has a option to set the agp as them main video.

---

### Post by Misfitsman805 on 2007-11-28
> **overdrank said:**
> Hi and have you tried to set the primary graphics in bios? Maybe it has a option to set the agp as them main video.


Hi there! yeah i have tried that and the weird thing is it will display ubuntu booting up on the agp card then once it gets to the main login screen it switches it right back over to the pci video card.

---

### Post by x64Jimbo on 2007-12-01
What this tells me is that the xorg.conf file is still referring to the secondary card as the primary. Try having a new xorg.conf file generated...
sudo dpkg-reconfigure xserver-xorg

---

### Post by Misfitsman805 on 2007-12-02
> **x64Jimbo said:**
> What this tells me is that the xorg.conf file is still referring to the secondary card as the primary. Try having a new xorg.conf file generated...
sudo dpkg-reconfigure xserver-xorg

alright ill give that a try and post an update on what happens
thanks a lot.

---

### Post by Misfitsman805 on 2007-12-03
*UPDATE*

well i got it to run on my agp card using the sudo dpkg-reconfigure xserver-xorg command,got the nvidia drivers loaded. but i cant get it to save the xorg.conf file.
a little help would be nice

---

### Post by x64Jimbo on 2007-12-03
Whenever you run that command, it saves a new copy of the xorg.conf file. I believe it may even back up your old one.

---

