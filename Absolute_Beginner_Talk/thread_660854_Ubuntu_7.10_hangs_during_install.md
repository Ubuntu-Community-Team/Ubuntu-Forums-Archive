---
title: "Ubuntu 7.10 hangs during install"
date: 2008-01-07
forum: Absolute Beginner Talk
---

### Post by chris_labonte on 2008-01-07
I'm an absolute beginner & sorry for the long post.

I'm trying to install Ubuntu 7.10 on a Sony Vaio PCG w/ Pentium4 256mb

Ubuntu will load up on the Machine and run in disk mode (VERY SLOWLY) but it hangs when I try to install it onto my machine.  Eventually (after about 4 hours) I can get to the 'choose time zone' window but then I get the following error message 'OAFIID:GNOME_FastUserSwitchApplet'

I did look this up online and got the following advice 

[http://ubuntuforums.org/archive/index.php/t-619767.html](http://ubuntuforums.org/archive/index.php/t-619767.html)

And I believe I followed this advice correctly (remember i'm an absolute beginner)  But the problem still occurs.  

Other info...

Prior to the install I wiped the hard drive with 'Dban disk wipe' because the Microsoft software was failing to intal (and I hate microsoft).   I have checked Ubuntu install CD and it says that it is fine.

Please help THANKS

---

### Post by hyper_ch on 2008-01-07
Well, for intallation I normally advice to use the alternate install cd. It's not as pretty but it offers more options (especially full encryption of the filesystem for paranoids like me) ;)

The DesktopCD isn't just as good for installation but by running it you can find out how well your hardware is supported.

P.S.: With 256mb ram it will not be breezing fast, I'd suggest to add a little more ram...

---

### Post by chris_labonte on 2008-01-07
Thanks! I'm back from work and downloading the text version now.  I'll let you (and everyone waiting with baited breath) know if/how it works.

---

### Post by chris_labonte on 2008-01-13
Resolution! in case others are having similar problems here is what happened & what I did

Burned Ubuntu Alt Install ISO -Much faster and better way to install I think
It ran but showed error when it came to DHCP protocol 
I figured this was simply because my computer was not plugged into network so I clicked past this warning but...

when trying to install the software I got an error message
´/vmlinuz kernel on partition'  and
'root=/dev/sdal'

I did not know what this stuff meant and could not find specific help so I plugged my DSL cable  in and tried again,  and it worked.

So... I needed to have my computer plugged into my DSL in order for it to work,

Hopefully someone will find this helpful & thanks for helping!

---

### Post by hyper_ch on 2008-01-14
that is strange... the exacte error message would help.

---

