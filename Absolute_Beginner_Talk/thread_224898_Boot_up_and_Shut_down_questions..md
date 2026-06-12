---
title: "Boot up and Shut down questions."
date: 2006-07-28
forum: Absolute Beginner Talk
---

### Post by Scintillement on 2006-07-28
When I boot up my machine I see the Alienware splash screen followed by something about a GRUB starting. Afterwards there is a black screen with "Ubuntu" in orange in the center and a status bar beneath it. Under that a list begins with things such as "loading drivers   ok" and "reading files   ok" and various other things that I can't recall. I can't write that fast.

Is it normal for it to do this every time I boot the machine?

After that I get the "log on" screen, where I put in my username and password.

When shutting down I get the same black screen with orange logo and text. this time it has messages about unloading and ending things, all followed by OK. Except something about a bittorrent tracker. There is no "OK" after that. I don't use bit torrent, nor do I even know how. Is that normal?

Should it be loading and unloading all these things each time I boot up and shut down my machine?

Sorry if this is a silly question, I just get paranoid about things some times.

---

### Post by littlemazeton2 on 2006-07-28
Thats completely normal :), don't worry.

---

### Post by kinematic on 2006-07-28
yes...it should be loading and unloading all those "things" when you boot/reboot/shutdown....how else would you be able to boot/reboot/shutdown ;) 
the difference is that you don't see what get's loaded and unloaded with windows....it's a big secret you know :rolleyes: 
this way you can identify at what stage something goes wrong if an error occurs ;) 
there's also a detailed bootlog that lets you see what exactly happens when you boot...it's in /var/log and it's called dmesg or in a terminal:sudo dmesg.

---

### Post by Indras on 2006-07-28
If there's stuff in your bootup process that you're not using (like bittorrent), you should get BUM.  The Boot-Up Manager.  Look around the forums, you should be able to find instructions on how to install and use it.

---

### Post by deadgobby on 2006-07-28
Yep, it is the normal shut down process. Nothing to be worry about. Heck, when I was running 5.10 Breezy. I hit the off button and the pc would shut down auto. Dapper though does not do that. It just way to keep the Kernal healthy and happy. 
Gobby

---

