---
title: "cant connect  to repoubuntusoftware.info"
date: 2007-08-31
forum: Absolute Beginner Talk
---

### Post by khelu on 2007-08-31
i live in shanghai and i think my isp doesnt allow me to connect to repoubuntusoftware.info so is there any other way to get those updates from other places please help

---

### Post by BobCFC on 2007-08-31
By *updates* do you  mean that you already have it installed and you want a different repository?    I think there is a mirror for package updates here:

> Ccals repo is online for those that would like to add it:

```
sudo gedit /etc/apt/sources.list
```


```
deb http://uu.enarel.eu/repo/ feisty all
```

It supports both feisty and amd64, give ccal a big thanks he has made this all happen.


(I found this information from page 90 (lol)  of the [main thread]("http://ubuntuforums.org/showthread.php?t=461378"))




If you mean that you wan to download the latest DVD .iso then here are the download details copied form the web page:

> 
Downloads

     Please use torrent or mirror first, if you would like to provide a mirror please contact me on Ubuntu Forums, additional mirrors coming soon.

Filesize: 1.9 GB (2,083,522,560 bytes)
MD5SUM: a4b8f312737cb2bab78cd22190e1bd49

[Torrent]("http://www.tuxdistro.com/torrents-details.php?id=464")

[Torrent]("http://linuxtracker.org/torrents-details.php?id=4411")

[Europe Mirror]("http://uu.enarel.eu/iso/ubuntu-ultimate-1.4-dvd.iso")

[Main Download Server]("http://downloadubuntusoftware.info/ubuntu-ultimate-1.4-dvd.iso")




If you are still having trouble you might want to investigate [TOR]("https://help.ubuntu.com/community/TOR") which is a way of hiding TCP traffic and making it anomymous (although it will be alot slower obviously).  I have not tried it but I believe it works well.


Good luck mate...


UPDATE:   After reading that thread a bit it might be that the ccal repo is for the new Ubuntu Ultimate 1.4 *Gamers Edition* that was released yesterday sorry..   It might still work.. you will have to look at the sever and the rest of the big main thread.

---

### Post by khelu on 2007-08-31
thanx it did help and up n running now eventhouh i had some prob with nvidia kernels.

But unfortunately new problem, when i enable compiz from desktop effect, after few seconds everything is just back to how it was before, copiz doesnt seems to work even after enabling desktop effects, there arent any effects:D 

would be glad if anyone could help
\thanx

---

### Post by BobCFC on 2007-09-01
It sounds like the OpenGL nvidia driver isn't set up or something.. which 3D card do  you have, does ultimate edition install the drivers for you?

If you try and launch compiz fusion from the terminal it should print out any error messages.

I think you can check if GL is set up by typing: glxinfo


it prints out alot of stuff but if I scroll back it says

direct rendering: Yes
server glx vendor string: NVIDIA Corporation
server glx version string: 1.4
...

A good way to tell if opengl is working is to try some 3D GL-screensavers, they are usually jerky if not set up.

You might want to open a new thread with more information if you still get stuck. (the graphics guys won't look at a title called 'cant connect to repoubuntusoftware.info')

---

