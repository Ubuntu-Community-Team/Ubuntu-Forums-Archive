---
title: "Another Error 17 problem"
date: 2006-07-01
forum: Absolute Beginner Talk
---

### Post by gobbluth on 2006-07-01
Hello, I am not completely new to Linux, but definitely completely new to installing it on my own computer. I'm running a Dell Inspiron 9300 laptop with Dapper loaded onto my external USB hard drive.

It had been working fine for a while, no problems at all, except that when I would attempt to boot into Windows from GRUB with the external drive still attached, I would get an error (I forget what error). The last change I made before this error started happening was that I changed the line in /etc/menu.lst that corresponded to where to boot Windows from (I believe I changed it to hd(1,0)).

Now whenever I attempt to start my laptop with the external drive attached (I have my BIOS set to boot from the USB device first) immediately I get an Error 17. I have tried putting the install CD in and going into rescue mode, but when I attempt to reinstall GRUB to /dev/sdb (sdb is my external drive) it refuses to reistall and I get an error. Sorry for the long post, thanks in advance to anyone who can provide insight. Ubuntu rocks!

---

### Post by gobbluth on 2006-07-02
Not particularly trying to bump this, just asking for help with a possible solution I'm close to. I'm trying to get into my /boot/grub/menu.lst file to undo the change I did to see if that corrects the problem, but when I attempt to run vi in the shell that rescue mode creates for me, I get an error that opens vi but prevents me from moving the cursor at all or performing any commands. Any ideas on what the problem could be now? Thanks!

---

