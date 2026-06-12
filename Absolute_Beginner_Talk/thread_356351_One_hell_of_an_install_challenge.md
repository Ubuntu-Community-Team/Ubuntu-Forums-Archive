---
title: "One hell of an install challenge"
date: 2007-02-08
forum: Absolute Beginner Talk
---

### Post by akao79 on 2007-02-08
So here's my situation. Try and stay with me.

I've got a toshiba portege 3500 tablet pc. It's a wonderful device, it's lightweight and does everything i would need in a laptop. Few problems though, it's got no cdrom, no floppy drive and can't boot from usb.   It will only boot from a toshiba brand pcmcia cd rom that i'm not buying because all i need it for is to install an OS, i would prefer to not shell out $50 for that. 

The windows install on it got corrupted and would boot into a bsod continously.   Why not try ubuntu?  What i figured would be a possible solution was to install ubuntu 6.10 using an older Sony laptop that has a cd rom and then transfer the hard drive back to the tablet.  

Problem is that when it is back in the tablet the hard drive gives me a X windows corruption error and just boots into the command prompt.   However the hard drive boots up just fine if i put it back into the Sony laptop that was used to install ubuntu, full gui and everything.  I'm guessing that this is a matter of hardware config and what i'm wondering is if it's possible to fix the windows x configuration from the command prompt.  

If that's not possible is there a way to copy the live cd to the hard drive and then have the hard drive install ubuntu from itself.   I looked through the install notes and nothing appeared to be there to indicate this.

 I don't have the detailed error laid out in front of me currently but i could get it if necessary.  I am a complete and utter newbie to Ubuntu and linux in general, but i could learn linux given the time.  I can get around the dos prompt no problem, so a command prompt doesn't worry me, just need some starting points here for linux.

Thanks in advance

---

### Post by aberry5555 on 2007-02-08
it is indeed possible to do so, try this:

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

this will recreate your xorg.conf (xserver configuration file) and, as long as you dont have an ati gfx card, it should be OK.

***P.S.***

Considering you're new to all this I'll explain that a bit more :p the "sudo" part is the part that avoids you having to use an administrator's account to do everything. Anything that requires administrators privilages you do with "sudo" (which will ask you for your account password).

the xorg.conf contains information about your mouse devices, your graphics card devices and other things required to run a GUI, so if it's set up for another PC you're gonna get errors. 

The reason I said "as long as it isnt running ATI is because Ubuntu, unfortunately, has problems with installing ATI as standard, but you can get around it if you need to fairly easily.

I'm sure if you can get around the MSDOS prompt then you can figure out Ubuntu, though it is a little more complicated than a microsoft prompt, because most everything up to a couple of years ago, and still today, even, was done in a console window.

---

### Post by akao79 on 2007-02-08
Thanks aberry! That worked like a charm. i've been strugglign with this laptop for a long time, glad to see it up and running again. Now i just need to deal with the wireless card.  It's too bad there isn't a point system here to reward people who help out.

---

### Post by aberry5555 on 2007-02-09
No problem, If you need help with your wireless I can probably help out a little. 

First of all go to the ndiswrapper website ( [http://ndiswrapper.sourceforge.net/](http://ndiswrapper.sourceforge.net/) ) and download the newest version of ndiswrapper. Because of the poor support for wireless chipsets in Linux this program was developed to "wrap" windows wireless drivers so that they could be used in Linux. 

Once you have the program you should go and find the drivers, hopefully as actual driver files rather than a .exe (they should come in a set of two files, one with an extension I can't remember and the other should be a .inf). If it is a .exe file there are ways to release the drivers but it's much easier not to have to do that so look for the actual drivers first :p.

Once you have these follow the instructions on this page: [http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation](http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation)

Though once piece of advice which this doesn't give is, after you've extracted the files, place the folder in /etc and also remember to do everything with a "sudo". 

If you can't find the .inf files then post back and I'll explain how it might be possible to extract them from the .exe file.

---

