---
title: "Broke my Ubuntu install, need way to replace original xorg.conf file"
date: 2007-08-25
forum: Absolute Beginner Talk
---

### Post by LingLing1337 on 2007-08-25
Hey all, I just edited my xorg.conf file so that i could run Beryl with my Intel card. Along with that, I replaced the splash screen with Gnome splash screen manager. Now, when I try to boot Ubuntu it says that it couldn't load the x server gui or whatever and sends me to a text command prompt. I'm currently running from the LiveCD. What can I do to fix this? Please help!!!


EDIT: Can I replace my xorg.conf from the liveCD? If so, please give me step by step instructions, this is my first day on Linux.

EDIT: Just found this quote: "
Wow, I can't believe it... I was finally able to boot to a $ prompt! Then I did a "sudo vi /etc/X11/xorg.conf" and decided I didn't want to risk destroying the file even more, so I hit "F1" (on a hunch that it would give me help with Vim). It did, and in the instructions I found a note about editing system files, saying that if I wanted I could type one line of text at the $ prompt to update my xorg.conf file with a fresh one from the Internet.

I did. Then I rebooted. So did Ubuntu, in all its fully-functioning glory! I feel like such a geek now!"

What is the command to replace the corrupted xorg with a fresh one? Please help!

---

### Post by forestpixie on 2007-08-25
have a look a for backups

in a terminal (accessories >terminal) 

dir /etc/X11/xorg*

and post the output

---

### Post by jfinkels on 2007-08-25
To go through a text based reconfiguration process for xserver, in a terminal enter:```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by forestpixie on 2007-08-25
> What is the command to replace the corrupted xorg with a fresh one? Please help!


sudo dpkg-reconfigure xserver-xorg

Edit - yep that one :)

Edit edit - in future if you're going to change something like xorg - make a backup 

sudo cp /etc/X11xorg.conf /etc/X11xorg.bak

If you then need to go back to the original

sudo mv /etc/X11/xorg.bak /etc/X11xorg.conf

---

### Post by sumguy231 on 2007-08-25
> Edit edit - in future if you're going to change something like xorg - make a backup 
Actually, I'm pretty sure dpkg-reconfigure xserver-xorg backs up your xorg.conf before replacing it. I think it typically names the backup 'xorg.conf.<year><month><date>' or something like that.

---

### Post by LingLing1337 on 2007-08-25
Thank Science! Reconfiguring xserver-xorg worked. THanks everyone!

---

### Post by forestpixie on 2007-08-25
yes I think so too - it was more of a gentle nudge towards doing backups before changing files like xorg.conf :)  - if you look at first thread a backup would have saved him/her

---

