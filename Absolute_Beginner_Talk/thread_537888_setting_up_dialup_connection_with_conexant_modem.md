---
title: "setting up dialup connection with conexant modem"
date: 2007-08-29
forum: Absolute Beginner Talk
---

### Post by ccclairee on 2007-08-29
I read the help files and installed the driver from Dell.
I used the scanModem tool, though I don't know what do to with the data?

my modem is a Conexant D850 56K V.9x DFVc Modem (COM3)

when I run ```
sudo wvdialconf /etc/wvdial.conf
``` I get an error saying no modem detected. When I try to install gnome-ppp it says E: file not found, or something very similar.

How do I dial up? I want to start using ubuntu!

---

### Post by oilchangeguy on 2007-08-29
"How do I dial up? I want to start using ubuntu!"

dial-up is fast becoming outdated. if you're in the US, most phone and cable companies now offer entry level highspeed packages. with pricing at or near that of dial-up. but with MUCH faster speeds. you owe it to yourself to graduate to highspeed, you'll be glad you did.

---

### Post by ccclairee on 2007-08-29
I live in a very rural area where highspeed is very expensive.

I'd like to have a highspeed connection, but this is not possible right now. I just need help using what I have now, until I can upgrade.

---

### Post by odzk on 2007-09-16
dial up is getting outdated but not all users can avail dsl, there are still millions of people using dial up, i wonder if ubuntu or linux will find ways how to connect to the internet using dial up because its really important for me to connect to the internet not to mention dial up is very common and very very basic.

if ubuntu cannot support dial up then they will be losing millions of people from using it, I myself am getting tired of looking for a solution that can take me less than a minute to setup in a windows.

---

### Post by jessejazza on 2007-09-28
No body has actually answered the question.

Yes, dial-up is outdated but useful to be able to connect if one's broadband connection gets a fault. I also use a modem to send FAXES  - also outdated in some folk's opinion BUT are secure whereas email IS NOT.

I actually have the same modem and i'll be setting it up during the next couple of weeks. The easy solution is to get an internal hardware modem which are a similar price to software modems. Quite why software modems became popular i don't know - as they are slower than hardware.

I'll see and be back in touch.

---

### Post by lord_zerg on 2007-09-28
the data of scanmodem tells you what driver you should download.
you will need to download that driver and compile it.
check this wiki, there is a section on conexant modems
[https://help.ubuntu.com/community/DialupModemHowto](https://help.ubuntu.com/community/DialupModemHowto)

---

