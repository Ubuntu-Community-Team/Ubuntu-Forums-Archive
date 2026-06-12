---
title: "can't get anything to work"
date: 2007-03-31
forum: Absolute Beginner Talk
---

### Post by outer_space on 2007-03-31
I tried the ubuntu live cd at school and it seemed to work ok with the wireless G connection where I was.  But at home on my linksys wireless B connection it will not work, Ive been playing with it and changing settings all morning.  Finally at this time it is an open wireless connection with no fancy options enabled.  My network thing is called 'lo' and whenever I try to use the internet it sends and receives a few packets and cant get any web pages.

Also, my bluetooth cellphone internet connection does not work at all, but there is the device in device manager.  I have no clue what to do.  My computer freezes at bootup if my wireless is turned off.  Should I give up and how do I get this grub thing off my computer?  I am absolutely disappointed and I don't think ubuntu is desktop ready like Ive heard.

---

### Post by teaker1s on 2007-03-31
I use
gnome-obex-server
it must be started from menu to use bluetooth.

wireless if you open up terminal and if you are using a usb wireless dongle
```
lsusb
``` post output

failing that if you really want to get windows back
boot recovery console of xp cd and
```
fixmbr
```

---

### Post by outer_space on 2007-03-31
Thanks for the help but it says I can't install that because I have a i386 machine.  So thanks for telling me how to restore windows.

---

### Post by teaker1s on 2007-03-31
odd, I have 386i machine running amd k7 kernel

---

### Post by outer_space on 2007-03-31
Seems like alot of stuff isnt i386 compatible.  Maybe its because I have core duo.

---

### Post by teaker1s on 2007-04-01
okay core duo - there have been some issues with as it's new, I would recommend that you start a new thread along the lines of 
"ubuntu core duo install help"
The reason I suggest this is I only have single core 386i/k7 and amd 64 experience, I think that with a little help from another core duo user-ubuntu could work well for you
you may also consider putting your hardware as a signature in your profile so others can see what you have:popcorn:

---

### Post by outer_space on 2007-04-01
My desktop is amd64 3400, I imagined lots of problems with 64 bit linux so I never considered putting it on my desktop.   For my core duo laptop I got wireless to work by making the router wep encrypted and entering the encryption key.  I will switch away from windows I hope if I can get eclipse, scilab, eagle cad, and cellphone as modem to work.

---

### Post by teaker1s on 2007-04-01
apart from flash I've found amd 64bit great, I would suggest that you have either a duel boot or one computer as a linux computer-take things gently and you will find that once past the teething troubles ubuntu/linux is very reliable

---

