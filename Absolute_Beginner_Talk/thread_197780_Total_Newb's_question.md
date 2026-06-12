---
title: "Total Newb's question"
date: 2006-06-16
forum: Absolute Beginner Talk
---

### Post by t-force on 2006-06-16
Hi all,

As I ended up with two HDs in my PC, I thought I'd be bold and give the whole Linux thing a try (or a re-try, but the last time I tried was about 10 years ago, when X was still a thing of the future, and it frightened the life out of me!).

So, I've d/led Ubuntu 6.06, and I've installed it without any difficulty. I've managed to tell Grub that Win XP should be my default OS, as I'm a big games fan. My biggest problem is that I can't get my Wireless card to talk to my router.

I've got a D-Link DWL-G650+ PCI card, which works absolutely fine in Windows, and a D-Link DSL-604+ ADSL Wireless router. I've followed the wireless trouble shooting guide wiki as best I can, and I've disabled WEP for the time being, but my card absolutely point blank refuses to see the router. If I do the iwlist scan command, there's nothing. Now, the troubleshooting guide talks about booting with pci=noacpi as a kernel option, but it's this that I'm completely clueless about. How do I change kernel options? Is there an equivalent of config.sys/autoexec.bat or win.ini (sorry to use MS terms there) that I need to edit, or is it a question of halting the boot process and then selecting various options?

Any help is much appreciated.

---

### Post by gardara on 2006-06-16
are you sure you have the right driver for your card?

---

### Post by t-force on 2006-06-16
As sure as I can be - Ubuntu tells me I'm using acx_pci. As I said, what I'm really trying to work out is how to change my kernel options when booting up.

---

### Post by Splittor on 2006-06-16
Did you try Ndiswrapper?  I don't know much about this card but I have a similar D-Link card with an Atheros core and it works out of the box.

Here's a link that I found with someone experiencing a similar problem:

[http://ubuntuforums.org/archive/index.php/t-75709.html]("http://ubuntuforums.org/archive/index.php/t-75709.html")

---

### Post by t-force on 2006-06-16
Whoops! Just realised I gave the wrong model number for the card - what I've got is a DWL-G520+ PCI card - I've got the 650 in my laptop, and that's not the issue. A 520+ card it is!! As I said, anyone know how I go about changing kernel options when booting up?

---

### Post by t-force on 2006-06-17
Bump! Can anyone help?

---

