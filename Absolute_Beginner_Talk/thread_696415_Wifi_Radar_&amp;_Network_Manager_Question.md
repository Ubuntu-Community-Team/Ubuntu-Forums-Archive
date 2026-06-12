---
title: "Wifi Radar &amp; Network Manager Question ??"
date: 2008-02-14
forum: Absolute Beginner Talk
---

### Post by jake85 on 2008-02-14
hi,

i a noob when it comes to ubuntu (well linux, this is my 1st time using it) , i've only had it for 2 days now and i've already had to reinstall it 3 times coz i keep breaking it to a point that the only thing to do is to start again.

my question is :

if i install Wifi Radar will Network Manager stop working or uninstall ?? this might be a dumb question but reason why i asking is that last time i install a wifi tool to try and connect to my AP Network Manager got uninstalled and my LAN card stopped work even after i reinstall NM.

so this time i dont want to stuff things up coz im really starting to enjoy ubuntu now.

oh btw, reason why i want to try and use Wifi Radar instead of NM is coz i cant connect to my router using NM, i've tried manual setup using WEP and WPA settings, but still it will not connect.

im using a Compaq Presario B1959TU Laptop ( Broadcom wifi chipset 43xx)

any help is greatly appreciated.

---

### Post by Herman on 2008-02-14
:) Hello jake85,
Here's how I got my Broadcom 43xx working, [HOWTO: Broadcom 43xx based wireless cards the EASY way]("http://ubuntuforums.org/showthread.php?t=405990&highlight=BCM4318")

> i a noob when it comes to ubuntu (well linux, this is my 1st time using it) , i've only had it for 2 days now and i've already had to reinstall it 3 times coz i keep breaking it to a point that the only thing to do is to start again.
 Yeh, me too, the best thing to do is install two copies of Ubuntu. It's FREE after all, we can install as many copies as we want. Then keep one system as your 'good' system and be careful with it.
Anything you aren't sure of or you want to test to see how it works, (strange new commands or software and so on), boot into your experimental installation and it doesn't matter if you wreck it. You won't care because all your good files and settings will be in your 'good' installation. :idea:

I see you're from Sydney. 
Sydney Australia or Sydney Nova Scotia? 
If you're from Sydney Australia you might be a Bigpond customer. I have a special sources.list for Bigpond users so we can download all the software and updates without it being counted as 'usage' on our Bigpond ADSL accounts. Someone in Bigpond must like Ubuntu too. :)
See my  [COLOR=#000066][Bigpond sources.list]("http://users.bigpond.net.au/hermanzone/p5.htm#Bigpond_sources.list")[B].

[/B][/COLOR]>  if i install Wifi Radar will Network Manager stop working or uninstall ?? I don't thinks so.

Regards, Herman :)

---

### Post by jake85 on 2008-02-14
thanks for the reply

> Hello jake85,
Here's how I got my Broadcom 43xx working, HOWTO: Broadcom 43xx based wireless cards the EASY way

i tried that, did not work. i followed that and thats when i lost my wifi and Ethernet card from ubuntu.

strange thing is that i can scan for wifi ap's but i cant connect ????? via NM.

> I see you're from Sydney.
Sydney Australia or Sydney Nova Scotia?
If you're from Sydney Australia you might be a Bigpond customer. I have a special sources.list for Bigpond users so we can download all the software and updates without it being counted as 'usage' on our Bigpond ADSL accounts. Someone in Bigpond must like Ubuntu too.
See my Bigpond sources.list. 

yeah im from Sydney Aus. but i dont use telstra (rip off :lolflag: ). im with exetel... there ok sometimes.

> the best thing to do is install two copies of Ubuntu  how ??? u mean on a different partition ?

---

### Post by Herman on 2008-02-14
Yeah, just make another partition somewhere for another Ubuntu install, if you have enough spare hard drive space of course.
You'll need maybe five gigabytes or so spare, but it you have lots of space you could allow more. 
You won't need to make another swap area, they can both use the same swap partition.

I make mine both equal sizes, half and half. I use one partition for experiments sometimes and sometimes for trying out the newest version of Ubuntu. If something goes wrong with the experimental one or if I just get sick of it I just delete it and install again, it doesn't matter, there are no files in it or anything precious.  Then after a while if I decide to I make the experimental system better than my 'good' system (because I've learned more), so then I move all my files and stuff into that and use the other one for an experimental system instead. 
It's possible to learn about the software a lot quicker when we don't have to be worried about it and scared to try things. Most things turn out okay anyway. 

Regards, Herman :)

---

### Post by jan quark on 2008-02-14
hey jake85

welcome to ubuntu, good choice

unfortunately the Broadcom chipset is the hell on earth in linux, because broadcom just do not want to make the drivers open, so they have to be reverse engineered and not always they work

it would be good to know the exact model of your wlan chip

sp type this into the terminal
system > accessories > terminal
```

lspci
```

```
sudo lshw -C network
```

and post the output here

if you have a bcm4311 than you can try to enable it with this small guide
[http://laiconic.quotaless.com/tutorial1.html](http://laiconic.quotaless.com/tutorial1.html)

if not ... we will see

---

### Post by Herman on 2008-02-14
When you are installing a second Ubuntu system in the same computer, the Ubuntu installer will automatically detect the other system, and make a boot entry for it in your new GRUB menu, so you'll be able to boot either one easily.
Your new system will also 'mount' your old one, so you'll be able to 'see inside' it and copy files in and out of it, and so on. There will usually be an icon on the desktop for that.

Regards, Herman :)

EDIT: Hey, hello jan quark! :) :) :)

---

### Post by ThePinkWitch on 2008-02-14
> **Herman said:**
> :) Hello jake85,
Here's how I got my Broadcom 43xx working, [HOWTO: Broadcom 43xx based wireless cards the EASY way]("http://ubuntuforums.org/showthread.php?t=405990&highlight=BCM4318")

 Yeh, me too, the best thing to do is install two copies of Ubuntu. It's FREE after all, we can install as many copies as we want. Then keep one system as your 'good' system and be careful with it.
Anything you aren't sure of or you want to test to see how it works, (strange new commands or software and so on), boot into your experimental installation and it doesn't matter if you wreck it. You won't care because all your good files and settings will be in your 'good' installation. :idea:

I see you're from Sydney. 
Sydney Australia or Sydney Nova Scotia? 
If you're from Sydney Australia you might be a Bigpond customer. I have a special sources.list for Bigpond users so we can download all the software and updates without it being counted as 'usage' on our Bigpond ADSL accounts. Someone in Bigpond must like Ubuntu too. :)
See my  [COLOR=#000066][Bigpond sources.list]("http://users.bigpond.net.au/hermanzone/p5.htm#Bigpond_sources.list")[B].

[/B][/COLOR] I don't thinks so.

Regards, Herman :)

Oh cool I'm from Adelaide, Australia. Hi  guys :biggrin:

---

