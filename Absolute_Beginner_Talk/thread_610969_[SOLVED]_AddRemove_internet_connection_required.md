---
title: "[SOLVED] Add/Remove internet connection required"
date: 2007-11-12
forum: Absolute Beginner Talk
---

### Post by fenixphire07 on 2007-11-12
Hey i just installed Ubuntu 7.10, and have set up a PPP0E broadband connection via a thread i found on a different site.

That let me connect to the internet thru firefox but is stopping me from adding programs from the Applications > Add/Remove facility.

when i try to add a OSS i get this error: (See Screenshot attached)

i am connected to the net.

PLS HELP ME..

ps. sudo apt-get update gives this msg

Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/main Translation-en_US
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/restricted Translation-en_US
Reading package lists... Done

thanks in advance

---

### Post by mikewhatever on 2007-11-12
Well, it looks like apt-get reads the repositories successfully. The errors are about those from CD. What do you get from
> sudo apt-get install alsa-oss

---

### Post by mcduck on 2007-11-12
> **fenixphire07 said:**
> ..

ps. sudo apt-get update gives this msg

Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/main Translation-en_US
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/restricted Translation-en_US
Reading package lists... Done


Well, that is quite a small output from 'sudo apt-get update'. It doesn't even mention any of the repositories there..

Could you run 'cat /etc/apt/sources.list' (in a terminal, you can find it in Applications/Accessories/Terminal) and post the output here? Since you need PPPoE to connect to Internet, the installer probably wasn't able to connect and therefore disabled all repositories in your sources.list file..

And in case you didn't know it yet, you can copy/paste from a terminal by selecting the text you wish to copy, and the just middle-click with mouse to paste it. (I just thought this might be a nice thing to mention, so you don't need to type all the text by hand.. :))

---

### Post by sirgazil on 2007-11-12
Hello **fenixphire07**!

I had the same problem and here is how I got rid of it:

**1.** Go to** System > Administration > Synaptic Package Manager**.
**2.** In **Synaptic** go to the **Settings** menu and select **Repositories**.
**3.** In that window enable all the check boxes you want. This options allow you to choose different repositories to download the software you need.

In the end it was just a repositories thing, not a problem with the internet connection.

That solved the problem for me. I hope it works for you too! :)

---

### Post by fenixphire07 on 2007-11-12
hey Sirgazil and everyone else,

WOW, i must say the ubuntu forums are making me a believer. :D Thanks Sirgazil and everyone else

ya now that i made those changes its updating them. But so those who come to this for answers dont leave puzzled, in Ubuntu 7.10 the configurations has been named as settings, and the repositories refered to are actually the check boxes. Click what you want downloaded off the net. basically everything :)

it probably happened coz i was trying to install something and it asked for the Ubuntu CD, must have then set these repositories to update only off the CD. 

THANK YOU ALL

PS: if you want to connect to ur PPPOE WAN internet connection, just type in pppoeconf and follow the onscreen instruction..

I'm a newbie on my way to being an Oldbie...

---

### Post by sirgazil on 2007-11-13
> WOW, i must say the ubuntu forums are making me a believer.  Thanks Sirgazil and everyone else

Glad to hear that! :)

> ya now that i made those changes its updating them. But so those who come to this for answers dont leave puzzled, in Ubuntu 7.10 the configurations has been named as settings, and the repositories refered to are actually the check boxes. Click what you want downloaded off the net. basically everything 

Sorry for that! My interface is in Spanish. I edited my last post! :)

---

