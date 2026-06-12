---
title: "Jumpdrive?"
date: 2005-12-26
forum: Absolute Beginner Talk
---

### Post by insub2 on 2005-12-26
i have a SanDisk Cruzer Micro 512mb that i don't know how to use with ubuntu.  i tried just pluggin it in and nothing happens.  is there something else?

---

### Post by bscbrit on 2005-12-26
You plugged in the computer?  Well, in that case you would at least have to insert a CD and reboot it.

You 'plugged in' the CD?  Did you try rebooting with the CD in the drive?

Or do you mean something else when you say 'plugged in'?

You might also want to try reading this: 

[http://www.catb.org/~esr/faqs/smart-questions.html](http://www.catb.org/~esr/faqs/smart-questions.html)

---

### Post by bscbrit on 2005-12-26
Aaah! Its a USB drive and not a computer.  My link is probably even more relevant.  And that is also called a 'jump drive'?  OK, USB memory stick or pen, external USB drive etc I recognised, but not a maker's name, until I Googled for it.

OK, plug the USB drive back in and wait 10 seconds.

Please show me the output of 

lsusb

i.e. in a terminal, type 'lsusb<enter>' :p

---

### Post by insub2 on 2005-12-30
```
insub2@awesome:~$ lsusb
Bus 005 Device 001: ID 0000:0000
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 004: ID 04b8:080d Seiko Epson Corp.
Bus 001 Device 001: ID 0000:0000
```

---

### Post by bscbrit on 2005-12-30
Insub2

Thanks for your response but, since my post 4 days ago I have started 2 weeks holiday in the UK.  I will be back on this forum to help by mid January if no-one else jumps in;  I hope they do.

But my first guess is that it hasn't recognised your jumpdrive - but you knew that, hence your original question.  Sorry I cannot be more specific at the moment but I am using a friend's computer and he is paying dial-up rates!

---

### Post by cwaldbieser on 2005-12-30
[QUOTE=insub2]```
insub2@awesome:~$ lsusb
Bus 005 Device 001: ID 0000:0000
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 004: ID 04b8:080d Seiko Epson Corp.
Bus 001 Device 001: ID 0000:0000
```[/QUOTE]
Hmm, it does not appear that your jump drive is being detected on the USB bus-- unless the Seiko Epson Corp. entry is the drive.  

Do you have a USB hub, or are you plugging it directly into a port on the PC?  Is there another port you can try?  Try the "lsusb" command before and after plugging/unplugging and see if there appear to be any changes in the output.

---

### Post by insub2 on 2006-01-01
Seiko Epson Corp is my printer.  i plugged the jumpdrive into a usb port on my mother board.

with the jumpdrive unplugged and running |susb there are no differences.

---

