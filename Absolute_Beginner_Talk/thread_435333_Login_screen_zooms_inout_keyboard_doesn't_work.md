---
title: "Login screen zooms in/out keyboard doesn't work"
date: 2007-05-06
forum: Absolute Beginner Talk
---

### Post by kushko on 2007-05-06
Hi, I just installed Ubuntu 7.04 with the live CD.

When I booted off the CD it worked fine. If I try booting off the hard drive, everything seems to work fine.

But once it starts up and arrives at the login screen, any key I hit caused causes the screen to zoom in and then zoom out as I press the keys.

Any ideas?

Kevin

---

### Post by raja on 2007-05-06
Pretty weird!
That happens with any key?
What video card do you have?

---

### Post by kushko on 2007-05-06
Pretty much any key. The only time it works is if I turn on NUM Lock. then the keypad works.

Kevin

---

### Post by raja on 2007-05-06
I really dont have any idea what the problem is here. Supposing the problem is with gdm, a workaround may be to install kubuntu-desktop and use kdm for the login. Might work - but again, doesnt solve the basic problem, whatever it is.
To try this, you do Ctrl-Alt-F1, then log in with your username and password. Then type ```
sudo aptitude install kubuntu-desktop
```

---

### Post by kushko on 2007-05-07
I'm using an ATI 7000 card with a P4 1.6GHz on an ABit BL7 with 768MB of RAM.

It took a few tries to get the OS installed and bootable. I can boot off the CD fine (that's what I've just done).

The detailed symptoms are that it "rotates" through 7 different screen resolutions and then returns back to my original 1280 x 1024. I used my monitor info screen to see the screens:
1280 x 1024
User Defined
User Defined
800 x 600
User Defined
User Defined
1024 x 768
back to 1280 x 1024.

It doesn't seem to do anything with the space bar. I tried a different keyboard, but it was the same. Since the keyboard works fine with the CD boot and with the WinME I have installed on a separate HD, it's not the keyboard.

Kevin

---

### Post by raja on 2007-05-07
Once you can log in to text mode, you can try to create a new xorg configuration with ```
sudo dpkg-reconfigure -phigh xserver-xorg
``` Might work.

---

### Post by kushko on 2007-05-07
Thanks, I can get to the console and login there.

I'll try your suggestion tonight when I get home.

kevin

---

### Post by kushko on 2007-05-08
Well that helped... kind of. 

It doesn't switch resolutions now. After the first try, I set it to only use one resolution. But none of the keys except for the keypad keys and the caps lock are accepted by the login screen.

Kevin

---

### Post by tophor on 2007-07-30
Same prob....any fixes? If I login to just the terminal it works fine. But the gui will zoom/change reses if I touch any key on my keyboard. I'm going to try update and restart using just my mouse.

---

### Post by tophor on 2007-07-30
I updated with Update Manager to all the latest stuff from 7.04. I also activated the restricted nvidia drivers. It was still changing my res after hitting any of the keyboard buttons. I restarted and it was still going on. Anybody?

---

### Post by kushko on 2007-07-30
I ended up totally uninstalling and then restarting from scratch.

The second install had no problems.

Kev.

---

### Post by tophor on 2007-07-30
I will try this.....YES....This I will try. Thanks a ton.

---

