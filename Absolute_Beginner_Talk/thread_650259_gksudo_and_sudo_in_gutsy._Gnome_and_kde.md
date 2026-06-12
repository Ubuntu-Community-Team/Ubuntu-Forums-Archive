---
title: "gksudo and sudo in gutsy. Gnome and kde"
date: 2007-12-26
forum: Absolute Beginner Talk
---

### Post by candtalan on 2007-12-26
I am using gutsy 7.10, both kubuntu and ubuntu-desktop(s) at different times, and have just discovered that with 7.10 ubuntu the command
sudo gedit /boot/grub/menu.1st  starts gedit, but seems to provide an empty file.

I have just become aware of the difference of sudo and gksudo :-) 
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)
so I am now aware that I should be using 
gksudo gedit /boot/grub/menu.1st
which of course works fine.

I mostly use kubuntu desktop and would choose actions>edit as root   from the context menu rather than use command line, so I have only just discovered this.

Why does 7.10 have this behaviour? My guess is that it is to save me from myself - a good thing, because I would probably not have known otherwise........ 
Also I notice that apparmor is being used in 7.10 and it has to do with some hardening maybe it is this involved in this sort of thing?

---

### Post by LaRoza on 2007-12-26
> **candtalan said:**
> I am using gutsy 7.10, both kubuntu and ubuntu-desktop(s) at different times, and have just discovered that with 7.10 ubuntu the command
sudo gedit /boot/grub/menu.1st  starts gedit, but seems to provide an empty file.

I have just become aware of the difference of sudo and gksudo :-) 
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)
so I am now aware that I should be using 
gksudo gedit /boot/grub/menu.1st
which of course works fine.

That is because you have the file name wrong, it is /boot/grub/menu.lst the letter "L" in lowercase.

You can also use "ALT + F2" to run commands.

Ubuntu doesn't have a root account by default. If you enabled it (not a good idea) you wouldn't have to do this.

---

### Post by shafin on 2007-12-26
Thanks for the link.

---

### Post by candtalan on 2007-12-26
> **LaRoza said:**
> That is because you have the file name wrong, it is /boot/grub/menu.lst the letter "L" in lowercase.
 Hey! (LOL) I always thought it was strange to have a numeral ('one') in a filename like that! Somehow I had believed it was  .1st   And there I was with such a good theory too!
:-)  

It means I have never edited this file actually from a cl, but always until now from gui in kde!

---

### Post by LaRoza on 2007-12-26
> **candtalan said:**
> Hey! (LOL) I always thought it was strange to have a numeral ('one') in a filename like that! Somehow I had believed it was  .1st   And there I was with such a good theory too!
:-)  

It means I have never edited this file actually from a cl, but always until now from gui in kde!

It is often mangled. The most common error is using "menu.list".

Such is life :)

---

### Post by Frank Golden on 2007-12-26
? ? > so I am now aware that I should be using 
gksudo gedit /boot/grub/menu.1st
which of course works fine.
So how come the same typo works with the gksudo command?

---

### Post by LaRoza on 2007-12-26
> **Frank Golden said:**
> ? ? 
So how come the same typo works with the gksudo command?

It creates a file, but doesn't open the correct one. It runs.

---

### Post by candtalan on 2007-12-26
> **Frank Golden said:**
> ? ? 
So how come the same typo works with the gksudo command?
I checked back - carefully - and it does not. :-(
It was me being innocently convinced that it was in fact '.1st' and to save typing it at that time  I did a copy paste action when it worked, and I was not at that stage actually looking for any typo. In fact I was convinced (wrongly) that the commands were all '.1st' and were also all entered correctly!

It shows just  how 'blind' beliefs can be! It maybe explains why the earth was flat for such  along time..... :-)

---

### Post by LaRoza on 2007-12-26
> **candtalan said:**
> 
It shows just  how 'blind' beliefs can be! It maybe explains why the earth was flat for such  along time..... :-)

The old testament of the Bible (in Isaiah, I think) the earth is refered to as a "sphere suspended in nothingness", quite consistant with what we know now.

---

### Post by philinux on 2007-12-26
Then we've got sources.list just to confuse the issue. :)

---

