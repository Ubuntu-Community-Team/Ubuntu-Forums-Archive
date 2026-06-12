---
title: "Desktop visual problems"
date: 2008-02-15
forum: Absolute Beginner Talk
---

### Post by Lewray on 2008-02-15
Hi, I'm an absolute beginner to Linux  and have taken it upon myself to give it a blast and see what all the fuss is about!

I've recently downloaded the Ubuntu 7.10 and installed it onto an old desktop. 

The problem I'm having is that the logon screen for some reason only takes up the top left quarter of the monitor & when I log in, although the background image covers the whole monitor, the task bar and menu bar are positioned similarly to the login screen (at the top and bottom of the top left corner of the monitor).

Is this an in-OS preference/setting which I can change from within the various menus or is it an error in locating the correct drivers for the monitor ( after installation the OS seems to have selected 'Generic, plug & play' as the monitor brand/type).

I'd really appreciate any pointers/suggestions anyone can provide.

---

### Post by spiderbatdad on 2008-02-15
Not sure...except possibly a bios settings issue with pci, vga. You said an older pc...that could mean a lot of things. 512 RAM is minimum recommendation for 7.10. You might consider the alternate cd. I have seen this issue before. Can't recall the post. Hang in there. You will likely receive the help you seek.

---

### Post by billgoldberg on 2008-02-15
I would start by downloading all the updates.

Then navigate to:

system - administration - restriced drivers managment

and take a look if there is something you can install (graphics card, ...)

then reboot

That being said, the machine could be to old for ubuntu 7.10.

You could try out xubuntu or use enlightment instead of gnome (you don't need to reinstall the os, some simple commands will install them, google for it)

---

### Post by macogw on 2008-02-15
Well, the monitor doesn't need drivers, but the video card does :p  I've got a few questions so we can help get this set up right:
1) What's the video card?  If you don't know specifically, just paste the output from putting this command in the terminal (Applications -> Accessories -> Terminal) ```
lspci
```
2) What resolution do you want on the screen?
3) What does the file /etc/X11/xorg.conf look like?  Paste it here, please.

---

### Post by rucadulu on 2008-02-15
try running from the command line:sudo dpkg-reconfigure xserver-xorg

Let the program auto detect your video card and then finish answering the questions and then reboot. If you still have the issue after doing this rerun the program and manually select your video card set it to **vesa** finish the answering the questions then reboot and see if this resloves the issue.

---

### Post by Lewray on 2008-02-16
Thanks for the input so far.:)

I may have caused some confusion when I said it was my old comp.  It still has at least a Gig of RAM and running an AMD Athlon 64 3500+    (I think!) so ..although its getting on for 3 years old it can still hold its own.

I removed the graphics card recently due to a previous fault. The onboard graphics is an ATI Radeon Sapphire card ... umm the device manager on linux is giving the code 
RS480 (Radeon XPress 200G series).

**macogw:**
I've run the lspci code in terminal, only to be reminded that I haven't gotten to the point of setting up the wireless internet connection on that machine yet (another challenge, most likely for another thread!), nor will the machine allow immediate use of my USB memory stick.   So unfortunately, short of retyping the output of that command I cant get the info to the PC I'm using now!

If I havent provided the info you need about the video card could you be more specific about the info you need from that output please macogw?

2) How can I view this file?  I've tried   Places->Search for files        and I've also tried entering it into the Terminal, only to be informed that my Permission is denied!:confused:

**billgoldberg:**
So the lack of internet conneciton I have just mentioned means downloading updates is not immediately accessible. Should this take priority do you think?

**rucadulu:**
I ran the "sudo dpkg-reconfigure xserver-xorg"  command, but have to say there was a reasonable amount of questions I didn't know. So will get hold of the info off the net and attempt it again when I might be able to complete it correctly!

---

