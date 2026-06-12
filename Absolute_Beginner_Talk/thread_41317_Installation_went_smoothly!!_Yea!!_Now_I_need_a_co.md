---
title: "Installation went smoothly!! Yea!! Now I need a couple answers please.."
date: 2005-06-13
forum: Absolute Beginner Talk
---

### Post by Insomniac on 2005-06-13
Hi,

Im a newbie and after trying to install FC3, which went bad, I was discouraged. I turned to Ubuntu and all it took was one shot and boom! I got a whole new operating system! Very nice. Painless installation.

First off, how do I configure my wireless or how can I get the drivers? Could you provide a link if possible? Please note, in network setup it can identify my address and it is listed as active, but I cannot get online - it says disconnected.

Second, the system seems somewhat sluggish when opening applications or closing them. Im coming from Vindoze and I am wondering if what Im experiencing is normal.

Third, does Linux create the swap drive automatically, or do I have to do that? I wish to transfer certain files from Vindoze to Ubuntu and toy with them there.

Fourth, can you provide a link for commands and information pertaining to toying wth the OS? I wish to explore the system, disect, and possibly improve it while developing positive attributes.

Fifth, which compiler are you using for developing.. I like DevC++, is it compatible? Any pages you can link to pertaining to this area?

Im so siked I finally installed a working Linux distro and I just wanna have more fun! Ive been trying for months so this is a big accomplishment for me even though it was a snap and maybe Ubuntu is made that way.. don't care.. now on the next stage.

Thank you

---

### Post by meat on 2005-06-13
A good start would be [here](http://www.ubuntuguide.org/) 

For your wireless problems, I would check out the Hoary 5.04 networking forum under hardware and just look at the problems other people are having.  I believe they have provided some good links in the posts answering questions.  You may get some help here, but you should tell us your network card brand and chip.

Have fun :)

---

### Post by Insomniac on 2005-06-13
[QUOTE=meat]A good start would be [here](http://www.ubuntuguide.org/) 

For your wireless problems, I would check out the Hoary 5.04 networking forum under hardware and just look at the problems other people are having.  I believe they have provided some good links in the posts answering questions.  You may get some help here, but you should tell us your network card brand and chip.

Have fun :)[/QUOTE]

Thanks meat, 

My brand and chip is in my sig.

---

### Post by poofyhairguy on 2005-06-13
[QUOTE=Insomniac]
First off, how do I configure my wireless or how can I get the drivers? Could you provide a link if possible? Please note, in network setup it can identify my address and it is listed as active, but I cannot get online - it says disconnected.[/QUOTE]

Does it show up at all in the "networking" tool?

[QUOTE=Insomniac]Second, the system seems somewhat sluggish when opening applications or closing them. Im coming from Vindoze and I am wondering if what Im experiencing is normal.[/QUOTE]

Its Gnome. Metacity is a little slow to the eye. There are ways around it on the forum...

[QUOTE=Insomniac]Third, does Linux create the swap drive automatically, or do I have to do that? I wish to transfer certain files from Vindoze to Ubuntu and toy with them there.[/QUOTE]

The default install creates a swap drive. The ubuntuguide.org will help you move over the Windows files.

[QUOTE=Insomniac]Fourth, can you provide a link for commands and information pertaining to toying wth the OS? I wish to explore the system, disect, and possibly improve it while developing positive attributes.
[/QUOTE]

[http://www.linuxdevcenter.com/linux/cmd/](http://www.linuxdevcenter.com/linux/cmd/)

[http://www.er.uqam.ca/nobel/r10735/unixcomm.html](http://www.er.uqam.ca/nobel/r10735/unixcomm.html)

[http://www.unixguide.net/linux/linuxshortcuts.shtml](http://www.unixguide.net/linux/linuxshortcuts.shtml)

Remember that there is no root in Ubuntu. If you need to use the root user in the terminal either add the word "sudo" to the beginning of the line or go "sudo -s" and do whatever you want.

[QUOTE=Insomniac]Fifth, which compiler are you using for developing.. I like DevC++, is it compatible? Any pages you can link to pertaining to this area?[/QUOTE]

I like the best free compiler- the GCC

[http://gcc.gnu.org/](http://gcc.gnu.org/)

It is what ever program in Ubuntu is compile with. If you want compiling tools, enter this in terminal:

sudo apt-get install build-essential

---

### Post by Insomniac on 2005-06-13
Ok, I don't know what I did.. but all of a sudden Im in! I got net access in Ubuntu! I didn't do anything. When it wasn't working earlier I went back to Vindoze to gain net access and do some research. Having printing out some papers from the links you guys posted I finally, just now, logged back into Ubuntu, and wham! I can connect. Maybe the reboot did something? 

Thanks poof! very detailed.  ;-) 

This is awesome! I love having some control, even though Im still new. 

Cheers \\:D/

---

