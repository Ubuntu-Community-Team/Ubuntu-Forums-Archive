---
title: "what does commenting out mean when editing file"
date: 2007-02-23
forum: Absolute Beginner Talk
---

### Post by rggavubt on 2007-02-23
I am reading a MPD forum on how to edit a media player daemon mpd.conf file and the following is said on editing one line of mpd.conf :


I'll try commenting it out, and see what happens.


What does comment or commenting out a line setting mean.......help!

The line being edited reads :  bind to address  "localhost"

I believe they are getting rid of "localhost" setting by commenting it out???? :confused:

---

### Post by Spr0k3t on 2007-02-23
To comment out a line, you would need to put a hash mark in the front of it.

This line is not commented out.
#This line is commented out.

Hope this helps.

---

### Post by rggavubt on 2007-02-23
> **Spr0k3t said:**
> To comment out a line, you would need to put a hash mark in the front of it.

This line is not commented out.
#This line is commented out.

Hope this helps.

Thanks for the reply....that was easy, but I never saw where anyone explained what that meant.

---

### Post by Spr0k3t on 2007-02-23
You learn a lot when you read the comments of .conf files.  I first started working with hashing out lines like this when I was setting up apache servers.  it's like the // for comments.

---

### Post by Bachstelze on 2007-02-23
Yep, the purpose of comments is to put text in a file without modifying what the file actually does. It can be used to disable temporarily a part of the config file or to put text explaining what a line does.

---

### Post by Patrick K on 2007-02-23
If you are familiar with the dos file "autoexec.bat" it uses "rem" (remark) to comment out a line. Some files use a (;) semicolon. Soooo, you need to follow the conventions of the file you are working on.

---

### Post by e_james on 2007-02-23
What confuses me is that some linux scripts seem to have "active" comments and perhaps 2 layers of comments e.g. 

#like this line
##and like this line

---

### Post by rggavubt on 2007-02-23
> **Patrick K said:**
> If you are familiar with the dos file "autoexec.bat" it uses "rem" (remark) to comment out a line. Some files use a (;) semicolon. Soooo, you need to follow the conventions of the file you are working on.

It has been a long, long time but I remember editing the autoexec.bat file in DOS.  Brings back old memories.

---

### Post by Bachstelze on 2007-02-23
> **e_james said:**
> What confuses me is that some linux scripts seem to have "active" comments and perhaps 2 layers of comments e.g. 

#like this line
##and like this line

This is used in the GRUB config file for example, you have lines like this :

```
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=/dev/hda7 ro

```

The reason for this is that these lines are used by the Debian Automagic GRUB update, that can atomagically generate new GRUB entries when you add kernel images in /boot - in this case, it's the default kernel boot options that will be put in all the automagic entries. But this cannot be used without a # because it would confuse GRUB when it reads from that file to display your GRUB menu. So it has a single # and "real" comments, that are parsed by neither the grub update script nor GRUB itself have two.

---

