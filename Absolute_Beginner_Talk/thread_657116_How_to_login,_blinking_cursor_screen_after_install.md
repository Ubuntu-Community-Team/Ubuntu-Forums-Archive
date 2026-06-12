---
title: "How to login, blinking cursor screen after installing Ubuntu 7.10"
date: 2008-01-03
forum: Absolute Beginner Talk
---

### Post by arai on 2008-01-03
i installed Ubuntu 7.10 using Ubuntu free CD. After successful installation and restart  when I select Ubuntu to load the screen goes blank. I am unable to login or use the operating system.

So what do I do to login and use Ubuntu 7.10?

I use dual boot windows XP and Ubuntu 7.10. Windows works perfectly normal. Please note that Grub is installed and I am able to see option to load win / linux. The only thing is linux ubuntu is not working. It is continuously showing blinking "-" screen.

please help me use Ubuntu. thanks.

---

### Post by PPAAUULL on 2008-01-03
What you could do is flip it into command mode I think ctrl-alt-f1 something like that then type ```
sudo killall gdm
sudo gdm
``` and see if your login screen shows up then. I know that the blinking cursor problem sometimes shows up for me when xorg isn't configured right. If that is the case I can help you fix that.

---

### Post by lswest on 2008-01-03
switching to a command line interface is ctrl+alt+f1 to ctrl+alt+f6 (f7 gives you the GUI)  and you can also try running ```
pidof X
kill [pid from the command above]
sudo startx 
```

if that doesn't work paste the output of ```
cat /etc/X11/xorg.conf
```

---

### Post by arai on 2008-01-03
when the loading image came i pressed ctrl + alt + f1. Then it showed this

Starting up...
Loading, Please wait...

After that nothing happened. I tried to enter the commands but to no use.

---

### Post by PPAAUULL on 2008-01-03
No wait till the blinking cursor comes up or is that when it did come up?

---

### Post by lswest on 2008-01-03
hmm it should have loaded and asked for a log in, next time try hitting esc to get to the terminal log in.

---

### Post by arai on 2008-01-03
this time i left the gui loader to load. after few seconds the gui vanished and the blinking screen came. 

So I pressed ctrl + alt + f1

then i could see this 

```

[63.104111] usb1-1: device not accepting address 2, error - 71
[63.819536]8139cp 0000:05:04.0: This (id 10ec:8139 rev 10) is not an 8139+ compatible chip
[63.819575] 8139cp 0000:05:04.0: Try the "8139too" driver instead.
*Reading files needed to boot...
*setting preliminary keymap...

```then nothing happend.

so i pressed ctrl + alt + del (twice) and the pressed the restart button in the computer. Only then it restarted.

please note that i had used ubuntu 6.10  in the same system configuration before and it used to work fine.

---

### Post by javahollic on 2008-01-03
One thing to wathc is having USB disk devices plugged in during boot (flash keys/ usbdisks etc) It can hang boots indefinitely, until you remove the offending devices (you can plugin them in after the login screen gets shown).

try booting into single user mode (just to show it can 'start'), hit ESC at boot , press e on the linux line, edit the line starting with 'kernel' (use cursors /home/end to navigate), remove the 'quiet splash' bit at the end and add 'single'.  Press return to save your changes,

hit return on the boot option to boot.  You should lots of useful information (to us!) scrolling up the screen, if you get a login prompt you are done, and can then progress diagnosing the Xwindows config....

---

