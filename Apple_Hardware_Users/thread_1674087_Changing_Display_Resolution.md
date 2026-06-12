---
title: "Changing Display Resolution"
date: 2011-01-23
forum: Apple Hardware Users
---

### Post by DaleH on 2011-01-23
I've installed Ubuntu 10.10 on a G4 ("Mystic" dual 450 processor).
The Display preferences limit me to 600x800 pixels on a monitor.
My montior is a Dell E209WFP 20” Monitor with an optimal resolution of 1680x1050. 
My card is an ATY Rage128Pro.

I've done a search here on Display resolution and tried to make sense of the suggestions but they are beyond my comfort level (i.e. manually editting my /etc/X11/xorg.conf file with terminal).

My machine is a dual boot with another drive containing OSX 10.2.8 so I don't want to do anything that might mess with the card itself. I also would like to get an understanding of this preference adjustment so I can change monitors with minimum hassle, and perform the same procedure on other computers I wish to install Ubuntu onto.

---

### Post by linuxopjemac on 2011-01-23
[http://www.mintppc.org/forums/viewtopic.php?f=10&t=113&hilit=dell&start=10](http://www.mintppc.org/forums/viewtopic.php?f=10&t=113&hilit=dell&start=10)

---

### Post by DaleH on 2011-01-23
I have no idea what to do with any of the material at the other end of this link:

        http://www.mintppc.org/forums/viewto...=dell&start=10[/URL]


"ok, let's try to fabricate an xorg.conf file then" 
Huh?.

Dale

---

### Post by linuxopjemac on 2011-01-23
You have to create a /etc/X11/xorg.conf with the content in that link.
Hang on. I will add a file...

---

### Post by linuxopjemac on 2011-01-23
in the terminal (CTRl-alt-F1 for example):
```
wget http://mac.linux.be/files/tmp/cube.txt
sudo mv cube.txt /etc/X11/xorg.conf
sudo reboot
```

---

### Post by DaleH on 2011-01-24
> **linuxopjemac said:**
> in the terminal (CTRl-alt-F1 for example):
```
wget http://mac.linux.be/files/tmp/cube.txt
sudo mv cube.txt /etc/X11/xorg.conf
sudo reboot
```
OK, thanks.

I copied the three lines in your reply into Terminal on my Ubuntu Mac.

   wget [http://mac.linux.be/files/tmp/cube.txt](http://mac.linux.be/files/tmp/cube.txt)
   sudo mv cube.txt /etc/X11/xorg.conf
   sudo reboot

Terminal wants my password but will not respond to my keyboarding. All I have is a blinking block.

BTW, I visited the link in the text and saw the data beginnng "Section Device; Identifier ATI Rage 128 GL"

Is this what I could have pasted into Terminal directly?
Could I change the references to the graphics card and screen resolution figures (1680x1050) if I had another card/monitor combination to work with?

Until I get Terminal to take my keyboard input, I'm stuck.

Suggestions?

Dale

---

### Post by linuxopjemac on 2011-01-24
boot into single user mode, then you have a terminal
at the boot: prompt if you startup your Mac in Yaboot you type:
```
Linux 1
```

Then you do the trick as mentioned before
and then CTRL-D to resume booting

---

