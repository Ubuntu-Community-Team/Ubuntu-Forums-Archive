---
title: "Completely new to Ububtu"
date: 2006-03-05
forum: Absolute Beginner Talk
---

### Post by Henry Rayker on 2006-03-05
I've used linux before, but in a very controlled environment (just compiler work for classes in school).

A little background on me, as this is my first post (skip it if you want):
I am a Computer Engineering major at a major university in the United States. I felt that I should learn to use linux as most of the companies at which I will be seeking employment use linux for its security. I chose Ubuntu because, for one, I heard it was one of the less technically difficult to learn, but it also has a wide hardware support base. Additionally, I liked the release schedule and the user base (I lurked around the forums of the top couple distros).

Now on to my problem:
I just bought a laptop (my first laptop) and wanted to use Ubuntu. I had a kind of silly problem though. In the setup screens, the screen was...shifted. What I mean to say is the top part of the screen started about an inch down the screen and the content went off the bottom. Some of the bottom of the screen was displayed (scrunched up) at the top of the screen.

Now, I got Ububtu installed and everything with a minimal amount of trouble, but any time I shut down, the screen shifts again (the black screen with all the 

performing x process                     [ok]
performing y process                     [ok]

business (I'm sorry. I don't know what this is all called.))

First, what is this screen called? I can't find anything about it without knowing a proper term for it. Secondly, do any of you know of a fix. Keep in mind that, while in Ubuntu, all is right with the world. There is no shifting.

Additionally, my laptop has a wide screen. Initially, I thought this was the problem, but now that it works fine in the OS, I don't know.

Thanks for any help you can give and I'm sorry for my lack of knowledge in this aspect.

---

### Post by kaamos on 2006-03-05
You could try to add vga=XXX to your kernel boot options and see if that helps. Don't know if it can do widescreen and how the possible scaling is done, but could be worth a shot.

Applications->Accessories->Terminal
```
sudo gedit /boot/grub/menu.lst
```
find section similiar (default is 386 instead of 686-smp here) to this and add the vga.
> title		Ubuntu, kernel 2.6.12-10-686-smp 
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.12-10-686-smp root=/dev/hda3 ro **vga=835** quiet splash rootflags=data=writeback
initrd		/boot/initrd.img-2.6.12-10-686-smp
savedefault
boot

save the file, reboot and cross fingers. :)

Here is a list of some vga values:
> 
# VESA framebuffer console @ 1024x768x64k
# vga=791
# VESA framebuffer console @ 1024x768x32k
# vga=790
# VESA framebuffer console @ 1024x768x256
# vga=773
# VESA framebuffer console @ 800x600x64k
# vga=788
# VESA framebuffer console @ 800x600x32k
# vga=787
# VESA framebuffer console @ 800x600x256
# vga=771
# VESA framebuffer console @ 640x480x64k
# vga=785
# VESA framebuffer console @ 640x480x32k
# vga=784
# VESA framebuffer console @ 640x480x256
# vga=769

I think "vga=ask" could work also.

Good luck.

---

### Post by Henry Rayker on 2006-03-05
That actually did the trick perfectly. Thanks a lot!

Is there a way I could add 1280*800 resolution to the list of screen resolutions. There was an option in the setup, but I forgot...*embarrassed*

EDIT: I got that taken care of, but do I need a new vga number for that resolution? Where would I find those?

---

### Post by TrendyDark on 2006-03-05
YOu'll have to reconfigure xorg and add it to the list during that process.

```
sudo dpkg-reconfigure xserver-xorg
```

---

