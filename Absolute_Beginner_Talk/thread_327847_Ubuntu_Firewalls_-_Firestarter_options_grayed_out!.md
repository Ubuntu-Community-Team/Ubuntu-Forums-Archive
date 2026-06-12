---
title: "Ubuntu Firewalls - Firestarter options grayed out!"
date: 2006-12-29
forum: Absolute Beginner Talk
---

### Post by thespaugh on 2006-12-29
Hi - 

I've a newly installed ubuntu box that I'd like to open for my internal (local) network - i.e. port 631. 

I've used firestarter before on my other ubuntu box without a hitch but on this one I can't get firestarter options/preferences to allow me to add a policy. The add policy address buttons are grayed out! I've removed and reinstalled firestarter with out avail. I then installed guarddog and it's options are grayed out too! 

Since neither program allows me to open this new box up there must be a conf file or something on the machine that's preventing this. 

Can someone please, please, please help me???

---

### Post by adamonline on 2006-12-29
Have you tried right clicking and selecting "add"?  I uninstalled Firestarter last night, so I can't verify, but iirc that's how I added my policies.

---

### Post by thespaugh on 2006-12-29
Yes - I've tried right and left clicking but the Add, Edit, Remove Rule and Apply policy button are all grayed out. It's as if I don't have permissions to edit the security policy? I'm running the program as sudo.

---

### Post by thespaugh on 2006-12-29
Ok -  I feel dumb - I right clicked in the white areas in the bottom half of the window, right under allow connections. 

That worked.... :oops:

---

### Post by adamonline on 2006-12-29
After reading that last post, my first thought was that you didn't have permissions, but you beat me to it =)

I'm thinking, maybe, that you don't have iptables installed?  That would be odd, since I believe  Ubuntu Server and Ubuntu comes with iptables.

Type **iptables -h** in your terminal, if you have it, it will display the iptables help information.

If you don't have it, I don't know how to install it, sorry =)

iirc, iptables stores its information in an editable file.

You can learn about iptables here, I believe this is where I read about said editable file: [https://help.ubuntu.com/community/IptablesHowTo](https://help.ubuntu.com/community/IptablesHowTo)

I'd refresh my own knowledge and look it up for you, but I'm stuck on the computer and have to leave soon! =O  Must... Leave... Computer...

For all I know, I'm barking up the wrong tree, but it's worth a shot verifying that you have all the files Firestarter uses, in case it doesn't automatically create them.

Also, check the firestarter man; probably **man firestarter** at console, but I dunno for sure if that's the command... I've gotten a loooong way with reading man pages =)

GL!

-ADAM

---

### Post by adamonline on 2006-12-29
> **thespaugh said:**
> Ok -  I feel dumb - I right clicked in the white areas in the bottom half of the window, right under allow connections. 

That worked.... :oops:

lol I want my five minutes back on that last post! ;)

Hah, just kidding, I hope I helped, and if so I'm glad I did =)

-ADAM

---

