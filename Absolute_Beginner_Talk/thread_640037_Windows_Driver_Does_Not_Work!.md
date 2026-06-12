---
title: "Windows Driver Does Not Work!"
date: 2007-12-13
forum: Absolute Beginner Talk
---

### Post by Dr.Vista on 2007-12-13
I have Ubuntu 7.04 Wubi. I have a broadcom card. Here is some info on it. I need the driver for this Card. Thank You in advance. Ive tried a tot of diffrent ways to install it. Could you guys help me?
I don't get the instructions for NDISwrapper! Could someone explain it? Please! :'( :(


```
05:02.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.
11g Wireless LAN Controller (rev 02)
        Subsystem: Hewlett-Packard Company Unknown device 1355
        Flags: bus master, fast devsel, latency 64, IRQ 20
        Memory at c0204000 (32-bit, non-prefetchable) [size=8K]

```

---

### Post by rockinlinux on 2007-12-14
im not sure about your wireless card but have you looked in your restricted drivers to make sure its just not enabled?

---

### Post by siciliancasanova on 2007-12-14
What are you having trouble with in NDISWrapper?

Where to find it?
How to install it?
How to load your driver?

---

### Post by Drate on 2007-12-14
Congratulations, you officially have the worst imaginable wireless card to be used with Ubuntu.

Here is what I used to fix Edgy [http://ubuntuforums.org/showthread.php?t=381770]("http://ubuntuforums.org/showthread.php?t=381770"), but it never quite fixed Feisty (well, it almost would but then I reboot and NEVER got it back), but it absolutely worked to fix a clean Edgy install.  Maybe somebody else watching this thread could adapt it as necessary for Feisty?

By the way, you just have to copy the listed driver files to some directory or anoth on your system, then run ndiswrapper -i /path/to/filename.inf .  Anyhoo, have fun.

---

### Post by lswest on 2007-12-14
i have a broadcom 4311 card, and the bcmwl5 drivers work for me, might be worth a shot for you too.

---

### Post by rustybronco on 2007-12-14
> **Drate said:**
> Congratulations, you officially have the worst imaginable wireless card to be used with Ubuntu.
Really? 
[http://ubuntuforums.org/showthread.php?t=595442&highlight=dynex](http://ubuntuforums.org/showthread.php?t=595442&highlight=dynex)
[http://ubuntuforums.org/showpost.php?p=3749742&postcount=4](http://ubuntuforums.org/showpost.php?p=3749742&postcount=4)
[http://ubuntuforums.org/showpost.php?p=3749763&postcount=5](http://ubuntuforums.org/showpost.php?p=3749763&postcount=5)

and yes I also used a wireless card with the same chipset (belkin), at least until my daughter dropped her laptop with the card in it.
the above belkin card was on 7.10, using it in 7.04 it took some work.

---

### Post by siciliancasanova on 2007-12-14
I have the exact same card as his and mine worked out of the box with the restricted driver in Gutsy.

When I was on Feisty I went the route he did with NDISwrapper

---

### Post by ingram on 2007-12-14
That was probably my favorite thing about Gutsy.  Was so much easier to setup the card using that restricted driver.

---

### Post by Dr.Vista on 2007-12-14
So what do I do?

---

### Post by Dr.Vista on 2007-12-14
> **rockinlinux said:**
> im not sure about your wireless card but have you looked in your restricted drivers to make sure its just not enabled?
I checked there and it does not appear. BTW I don't ubderstand the part where you install NDISwrapper and where you install the driver. If any could help me solve it that would be cool! I will add you to my buddy's list!

---

### Post by siciliancasanova on 2007-12-14
First of all you're on Feisty, so don't worry about the restricted drivers part.  Post your guide or steps here for NDISwrapper.  If it's a guide, you should just be copying and pasting commands into the terminal.

---

### Post by Dr.Vista on 2007-12-14
> **siciliancasanova said:**
> First of all you're on Feisty, so don't worry about the restricted drivers part.  Post your guide or steps here for NDISwrapper.  If it's a guide, you should just be copying and pasting commands into the terminal.

Its this guide. [http://ubuntuforums.org/showthread.php?t=112526](http://ubuntuforums.org/showthread.php?t=112526)

I don't understand the whole guide! Is there a easier way to do this?

---

### Post by rustybronco on 2007-12-15
Have you tried this first? [http://ubuntuforums.org/showpost.php?p=3749742&postcount=4](http://ubuntuforums.org/showpost.php?p=3749742&postcount=4)

---

### Post by Dr.Vista on 2007-12-15
> **rustybronco said:**
> Have you tried this first? [http://ubuntuforums.org/showpost.php?p=3749742&postcount=4](http://ubuntuforums.org/showpost.php?p=3749742&postcount=4)

I already did and it does not appear there.

---

### Post by RobotoWorks on 2007-12-15
As one of the first posters said "Congrats, you have the worst imaginable card to be used with Ubuntu. It is highly unlikely you will get it to work. I tried to get help with my card, Sierra Wireless AirCard 875, and came close, but it never worked. So instead, I got a DSL modem and used that to get internet on Ubuntu.
You may find away to get it to work, but why spend all that time and stress, when you could go to Best Buy and buy a modem for $20?

---

### Post by Dr.Vista on 2007-12-15
My card is compatible! Is that I don't know how to use the NDISwrapper.

---

### Post by Dr.Vista on 2007-12-15
> **Dr.Vista said:**
> My card is compatible! Is that I don't know how to use the NDISwrapper.

So? Guys I really need help! Please!

---

### Post by Dr.Vista on 2007-12-15
Never Mind I decided that Ubuntu is not working for me so I am using Windows.

---

### Post by Drate on 2007-12-17
You honestly couldn't find any tutorials on NDISwrapper?  Put your necessary driver files *.inf and *.sys in some folder on your hard drive, and the type ndiswrapper -i /path/to/file.inf then ndiswrapper -m .

I said as much in my reply to you before and the link I provided.  Seriously though, you couldn't find any tutorials on ndiswrapper?  This was on the first set of results when googling ndiswrapper: [http://www.linuxquestions.org/linux/answers/Networking/NdisWrapper_The_Ultimate_Guide/]("http://www.linuxquestions.org/linux/answers/Networking/NdisWrapper_The_Ultimate_Guide/")

Anyway, sorry you feel you are better off with Vista, one must keep in mind, we are all volunteers out here, but I've gotten better overall tech support with these volunteers than any of the proffessionals I've called elsewhere.

---

### Post by Dr.Vista on 2008-01-05
> **Drate said:**
> You honestly couldn't find any tutorials on NDISwrapper?  Put your necessary driver files *.inf and *.sys in some folder on your hard drive, and the type ndiswrapper -i /path/to/file.inf then ndiswrapper -m .

I said as much in my reply to you before and the link I provided.  Seriously though, you couldn't find any tutorials on ndiswrapper?  This was on the first set of results when googling ndiswrapper: [http://www.linuxquestions.org/linux/answers/Networking/NdisWrapper_The_Ultimate_Guide/]("http://www.linuxquestions.org/linux/answers/Networking/NdisWrapper_The_Ultimate_Guide/")

Anyway, sorry you feel you are better off with Vista, one must keep in mind, we are all volunteers out here, but I've gotten better overall tech support with these volunteers than any of the proffessionals I've called elsewhere.
Im made it work. No need for futher comments.

---

### Post by khanoftartary on 2008-01-06
Hey, okay, I'm having the same problem with my wireless card (Linksys WMP54G). I've been searching for an answer to this problem for a week and can't get anything. Everyone seems to think that the problem is in using ndiswrapper. There is no problem using ndiswrapper, the problem is installing ndiswrapper. I cannot use synaptic! I am not connected to the internet on my ubuntu machine, and I have to download it from this computer and move it over. I have to have very good and simple instructions for installing ndiswrapper from a tarball, the instructions in the installation file DO NOT WORK!! The installation file instructs the followng commands: >  make uninstall
make
login as root and run:
make install  

Only **Make Uninstall** works; both of the other commands produce massive amounts of errors. Now could someone please help me; this problem has lasted long enough that it's beginning to interfere with my work.

---

