---
title: "ubuntu PC -&gt; ubuntu Server"
date: 2007-07-29
forum: Absolute Beginner Talk
---

### Post by MicronXD on 2007-07-29
I just finished installing the home PC version of ubuntu... i meant to do server.... any way i can easily switch it over without reinstalling with the server disc?

---

### Post by MicronXD on 2007-07-29
any1?/bump

---

### Post by MicronXD on 2007-07-29
any1?/bump

---

### Post by backinthecity on 2007-07-29
I'm not really sure about that. I do know during the installation process you can set up a DNS server or a LAMP server during the process so i'm not sure how you'd get that. I would recommend just downloading the server .iso. You can always add a gui (which is frowned upon by server admins/ It just kills your resources.) 

I did the same thing as you a while back. I searched up and down and couldn't find a way around just downloading the server iso and just reinstalling...

sorry i couldn't help
good luck
-Drake

---

### Post by MicronXD on 2007-07-29
thx

---

### Post by upthelum on 2007-07-29
You could try downloading ubuntu server from [here]("http://www.ubuntu.com/").
Its not hard to install.

---

### Post by erito on 2007-07-29
Actually it depends on what you want.  You can always add server related stuff (Mysql and its components, BIND, Apache, etc) onto your desktop simply by using synaptic or apt-get.  

I think that the only real difference between the LAMP and the Desktop install is whats initially installed.  You can add Desktop related components to a server and you can add server related components to the desktop.  I could be wrong though on that one though ;-)

erito

---

### Post by MicronXD on 2007-07-29
> **upthelum said:**
> You could try downloading ubuntu server from [here]("http://www.ubuntu.com/").
Its not hard to install.

-.- I already D/L'd that

.... and just finished installin it now... but now i want the GUI... any1 know how i can install the GUI? lol... damn... 

stupid-a55 web tech classes never taught this shtuff

---

### Post by MicronXD on 2007-07-29
> **erito said:**
> You can add Desktop related components to a server and you can add server related components to the desktop.  I could be wrong though on that one though ;-)

erito

how?

---

### Post by Alterios on 2007-07-29
The Easiest way to install a light desktop on your server is to install XFCE. You just type in "sudo apt-get install xubuntu-desktop" without the quotations. If you want Gnome it's "ubuntu-desktop", and for kde it's "kubuntu-desktop". I would stick with XFCE though. There are many other choices but those are the 3 basic choices and the easiest to install.

---

