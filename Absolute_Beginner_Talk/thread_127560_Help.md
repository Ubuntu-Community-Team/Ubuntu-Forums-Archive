---
title: "Help"
date: 2006-02-09
forum: Absolute Beginner Talk
---

### Post by spandon on 2006-02-09
Hi,
Have installed ubuntu 5.10, and am very pleased with the result with one big exception, that is I cannot get a printer to work with it.
I checked the web to find out what printers sre supported, and found that Samsung support Linux, have downloadable drivers and support it in their user manuals and setup disk.
So today I puchased a Samsung ML1610 laser printer, to use with ubuntu (Linux).
First problem was that the cd autorun would not work, so I then downloaded 

the latest driver from the Samsung web, extracted the files to a folder I named "printer" in my home directory.

I started up terminal with the following result:
$ cd printer
~/printer$
I then followed Samsung's instaructions:
./setup.sh ( this is supposed to start the setup terminal)
I then got a login prompt - I entered my password - I then got a flashing cursor but nothing else happened.
Could anyone please advise what I did wrong and what I need to do now?
Don

---

### Post by el3ktro on 2006-02-09
When you plug in your printer & turn it on and when you go to the System Settings and add a new printer, isn't your Samsung printer detected? I have an Kyocera FS-1010, and I just had to plug it in, add a new printer and that was it.


Tom

---

### Post by spandon on 2006-02-09
[QUOTE=el3ktro]When you plug in your printer & turn it on and when you go to the System Settings and add a new printer, isn't your Samsung printer detected? I have an Kyocera FS-1010, and I just had to plug it in, add a new printer and that was it.


Tom[/QUOTE]
My printer is not listed, but recognised.
it needs the driver that I have downloaded Installed
Thanks
Don

---

### Post by carlosqueso on 2006-02-09
I'd try "sudo ./setup.sh" I think its trying to get you to use your root account, which is disabled in ubuntu.

---

