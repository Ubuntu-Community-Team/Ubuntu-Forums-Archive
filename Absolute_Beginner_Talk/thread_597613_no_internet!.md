---
title: "no internet!"
date: 2007-10-30
forum: Absolute Beginner Talk
---

### Post by number1pbefan on 2007-10-30
Hello all, I just installed Ubuntu 7.04 yesterday, and I can't seem to get it on the internet.  I am dualbooting Win XP Pro with Ubuntu, and XP can get online, but my Ubuntu copy isn't.  I have a MSI [K8M890M2-V]("http://global.msi.com.tw/index.php?func=proddesc&prod_no=246&maincat_no=1&cat2_no=171&cat3_no=6") motherboard, with built-in ethernet.

---

### Post by Pumalite on 2007-10-30
What kind of connection to Internet do you have?

---

### Post by number1pbefan on 2007-10-30
I am connected to the internet through my university, so therefore it's just standard ethernet cable from my computer to the wall.

---

### Post by johnny9794 on 2007-10-30
In bios "reboot keep hitting delete key" goto your onboard settings in bios and enable lan boot rom option, hit F10 to save and exit and then you may have internet.

This is what i had to do.

---

### Post by Pumalite on 2007-10-30
You are probably connected through a proxy. See if above instructions work.

---

### Post by Crafty Kisses on 2007-10-30
> **number1pbefan said:**
> Hello all, I just installed Ubuntu 7.04 yesterday, and I can't seem to get it on the internet.  I am dualbooting Win XP Pro with Ubuntu, and XP can get online, but my Ubuntu copy isn't.  I have a MSI [K8M890M2-V]("http://global.msi.com.tw/index.php?func=proddesc&prod_no=246&maincat_no=1&cat2_no=171&cat3_no=6") motherboard, with built-in ethernet.

Try to ping a website.
```
ping website name
```

---

### Post by Factory on 2007-10-30
Do you need to put in a username / password to access your university?

---

### Post by ed-koala on 2007-10-30
I had a similar problem duel booting XP and Ubuntu.  The problem was that Windows was shutting down my modem on it's shutdown, and Ubuntu wasn't getting it back up.

I fixed it by going into Windows modem setting and made sure all the "wake to" options were enabled, solved the problem instantly.

Just another example of Microsoft not playing fair. lol

---

### Post by number1pbefan on 2007-10-30
I don't need a username/password to access the internet, and I don't know if I connect through a proxy, so I'll try the instructions johnny9794 said.

Also, I had dual-booted Ubuntu 7.04 and XP before and the internet worked right when I installed Ubuntu, but Alas, I got a virus in XP. 

I only had XP because for one of my classes, the homework is online, and it needs XP and IE to work. =(

---

### Post by lespaul_rentals on 2007-10-30
You need to work from the ground up, or Layer 1 of the OSI model to the top.

Is your cable plugged in?
Does your Network Manager see a connection?
In Manual Configuration, do you have DHCP enabled?
Are there any DNS hosts or default gateways that are incorrect?
Do you need a certain MAC address to connect?
Do you need to set your browser (Firefox I'm assuming, as it's the default Ubuntu browser) to a proxy?

---

### Post by number1pbefan on 2007-10-30
> **lespaul_rentals said:**
> You need to work from the ground up, or Layer 1 of the OSI model to the top.

Is your cable plugged in?
Does your Network Manager see a connection?
In Manual Configuration, do you have DHCP enabled?
Are there any DNS hosts or default gateways that are incorrect?
Do you need a certain MAC address to connect?
Do you need to set your browser (Firefox I'm assuming, as it's the default Ubuntu browser) to a proxy?

Yes the cable is plugged in, and in Ubuntu it sees the wired LAN connection, I do need a specific MAC address, but those don't change between Windows and Ubuntu would they?

I did try setting it to have DHCP enabled...also I tried using a static IP by using the IP address and DNS and gateway information from XP.

---

### Post by ed-koala on 2007-10-30
By your post I'm assuming if you boot into Windows your internet works fine ...

If so, check to see if your Ethernet light goes out after switching to Ubuntu.  If it does, you have the same problem I had.  See my post to resolve.

Just added this cause I didn't see you mention if you tried that fix yet :)

---

### Post by number1pbefan on 2007-10-30
Internet works now, thanks to johnny's suggestion :)

Thanks all!

---

