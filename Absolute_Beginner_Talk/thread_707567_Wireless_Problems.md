---
title: "Wireless Problems"
date: 2008-02-25
forum: Absolute Beginner Talk
---

### Post by Mowcius on 2008-02-25
I have a BT Home hub 9a8c and i am trying to connect to it using a 3 com wireless PC card in atime laptop...

Everything is working fine on ubuntu, it finds the router but i don't know what type of code it is...

I have tried it on passphrase but it doesn't want to work

the cose on the back is 10 characters long

any ideas?

Mowcius

---

### Post by Cha1n5aW on 2008-02-25
try this, worked for me...
[http://ubuntuforums.org/showthread.php?t=684495]("http://ubuntuforums.org/showthread.php?t=684495")

---

### Post by Mowcius on 2008-02-25
I am not familiar with code

any other ideas?

Mowcius

---

### Post by 01000111 on 2008-02-25
Sadly the default setting of most routers is WEP rather than WPA, so select:

WEP
64-bit
and just enter the given value as Key 1


01000111

---

### Post by Mowcius on 2008-02-25
I have a code for it and it's 10 characters so shall i try that in WEP 64-bit?

Mowcius

---

### Post by Cha1n5aW on 2008-02-26
> **Mowcius said:**
> I am not familiar with code

any other ideas?

Mowcius


Its really not hard, I'm not very familiar with "code" either, but for your needs it consists of typing 8 lines in a terminal window. I'm actually working on a script file that can be run to do the job rather than typing it out, if I get it working send me a reminder & I'll send you the file.  You can follow that thread here...
[http://ubuntuforums.org/showthread.php?t=705027]("http://ubuntuforums.org/showthread.php?t=705027")
And if your if you're up for typing out 8 lines in terminal, here is what you would need to type

```

sudo ifconfig wlan0 down
sudo dhclient -r wlan0
sudo ifconfig wlan0 up
sudo iwconfig wlan0 essid "NETWORKNAMEHERE"
sudo iwconfig wlan0 key YOUR10DIGITWEPKEYHERE
sudo iwconfig wlan0 mode Managed
sudo dhclient wlan0

```

This works every time for me, hopefully I can get my script to work soon.  These commands must be typed out in that exact order for it to work.  Until I get the script to work, I just keep a text file to cut & paste the commands from. (shift+ctrl+v to paste into terminal window).

Hope that helps, else you can always try someting called WICD, I've heard of it, but never tried it myself.

- Shawn

*these commands are assuming the "logical name" of your wireless device is the default "wlan0"

---

