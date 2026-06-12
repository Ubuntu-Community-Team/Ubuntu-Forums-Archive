---
title: "Installed new video card, Ubuntu won't start"
date: 2007-05-22
forum: Apple PPC Users
---

### Post by joshjani on 2007-05-22
I got a new to me 16mb ATI card for my beige G3. Works great on the Mac side, but Ubuntu hung before starting up.

I'm sure I have to reconfigure xserver. I could do that with this:

sudo dpkg-reconfigure xserver-xorg

But I don't know how/when to get to where I could type that as I have to use BootX to boot to Linux from Mac OS. In other words, how do I get to a shell/terminal before linux boots?

Please help- I don't wanna use Mac OS!:(

Thanks-

JC

---

### Post by joshjani on 2007-05-22
I'm going to reply to my own question, with more questions!

If I put in my Ubuntu CD, use BootX to boot to it, I'd have to go through a whole re-install to get a new kernel that included what I need for the new ATI card. Then I would have to copy that kernel to the Kernels Folder as well as the initrd again- the whole sticky step that I just figured out two days ago to get the darn thing going.

Is there a way I can just open the kernel in a text editor and add information for the ATI card? Or is there a kernel argument I can use in BootX?

I almost can't bear the thought of re-doing that install!

JC

---

