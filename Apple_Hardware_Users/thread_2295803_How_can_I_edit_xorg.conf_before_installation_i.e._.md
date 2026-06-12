---
title: "How can I edit xorg.conf before installation i.e. on DVD image?"
date: 2015-09-21
forum: Apple Hardware Users
---

### Post by aurora72 on 2015-09-21
Hello

I hope I'm in the right section of the forum. 

I have installed "Lubuntu 14.04.2 LTS "Trusty Tahr" - Release powerpc" to run my PowerPC Mac mini. It runs fine except one thing:

Its graphics acceleration settings causes the computer to hang up after I boot into the desktop screen and usually after 10-15 seconds. 

To prevent that hangup from happening, after the boot I quickly open the xorg.conf file and I disable acceleration by editing the device section like that:

Option  "NoAccel" "True" radeon.agpmode=-1

Now the problem is that it happens during the installation, too: At the section where I'm asked on  which partition to install Lubuntu. 

Only if I pass that section very fast  (selecting all those partition settings, takes time) I can espace any hangup from happeining but mosy of the time I get caught into a hangup and I have to restart installation all over; and that takes time too.  

So I think I need to edit the xorg.conf file before installation, i.e. on the installation DVD's image but I don't how to do that. I've browsed the contents of the DVD and searched for the xorg.conf but it couldn't be found. I guess it's compressed into some sub-image files. How can I do it? Thanks.

---

### Post by rsavage on 2015-09-21
> **aurora72 said:**
>  To prevent that hangup from happening, after the boot I quickly open the xorg.conf file and I disable acceleration by editing the device section like that:Option  "NoAccel" "True" radeon.agpmode=-1eh?

Where on earth did you get that from? 

And there is no xorg.conf on an ISO, so what image are you using, 'cos it ain't official?

---

### Post by este.el.paz on 2015-09-21
[URL="https://wiki.ubuntu.com/PowerPCFAQ#How_do_I_make_a_yaboot_parameter_permanent.3F"]https://wiki.ubuntu.com/PowerPCFAQ#How_do_I_make_a_yaboot_parameter_permanent.3 

[/URL]

aurora:

Even if your mac mini isn't PPC, you can look through the PowerPCFAQ, written by a very knowledgeable person, to help with problems that come up with installs . . . .  I put this link to that boot param section, but you could read around and see what works for you.  Check if you can enter the "boot parameters" that work to fix your problem. 

If you are using dual-boot set up you can enter boot params on the second Yaboot screen, if not, then try to add them into the yaboot.conf file . . . .  Once that is working for you then you can set up your xorg.conf, if you need it.  Hope that isn't too much waffle . . . .

e.e.p.

---

### Post by aurora72 on 2015-09-22
> **rsavage said:**
> eh?

Where on earth did you get that from? 

And there is no xorg.conf on an ISO, so what image are you using, 'cos it ain't official?

Sorry for late reply, Ubuntu Forums didn't alert through e-mail.

It's Lubuntu 14.04.2 LTS "Trusty Tahr - Release powerpc; I must have got it from lubuntu.net

Yes you're right, there's no xorg.conf on the ISO but after I install from that ISO into harddisk , there's that xorg.conf file, so it must be buried inside that ISO.

That looks promising. I will work on it and see if I can make it.

> **este.el.paz said:**
> [URL="https://wiki.ubuntu.com/PowerPCFAQ#How_do_I_make_a_yaboot_parameter_permanent.3F"]https://wiki.ubuntu.com/PowerPCFAQ#How_do_I_make_a_yaboot_parameter_permanent.3 
[/URL]
aurora:

Even if your mac mini isn't PPC, you can look through the PowerPCFAQ, written by a very knowledgeable person, to help with problems that come up with installs . . . .  I put this link to that boot param section, but you could read around and see what works for you.  Check if you can enter the "boot parameters" that work to fix your problem. 

If you are using dual-boot set up you can enter boot params on the second Yaboot screen, if not, then try to add them into the yaboot.conf file . . . .  Once that is working for you then you can set up your xorg.conf, if you need it.  Hope that isn't too much waffle . . . .

e.e.p.

That looks promising. I'll work on it and see if I can make it.

---

### Post by rsavage on 2015-09-22
The only way you'll have an xorg.conf is if you've used a boot parameter with the live ISO that generates one, you've downloaded one, you've written one, or you've run the configure command.  There is no xorg.conf anywhere, because it is considered old fashioned and unnecessary.

---

