---
title: "iPod trouble"
date: 2009-05-27
forum: Apple Hardware Users
---

### Post by ayako0chan on 2009-05-27
I have an 4 GB Ipod nano, which has been able to automatically connect until today. Now, when I connect, not only does it not appear on my desktop, it appears as an USB drive in "Computer". When I double click on it, a message appears saying:
Unable to mount location
Can't mount file
I am not even able to open it with any software (amarok, gtkpod, rhythmbox). What can I do to fix this?

---

### Post by double.emms on 2009-05-28
I think I have exactly the same problem.  Everything was copacetic (even after I upgraded to Jaunty) and then one day, I added some songs to my ipod, unmounted it, and the next time I plugged it in, nothing.  

I've been struggling with this for a few days now, and I'm still not sure what the deal is.  I ran dmesg | tail after plugging it in to pull the /dev id and tried to mount it manually via command line, only to discover that it had already been automounted to /media/IPOD just like always.  

Thing is, it doesn't show up in Rhythmbox, Amarok, or the Disk Mounter Applet, and under the computer tab in Nautilus it just shows up as USB Drive (though it does have a portable music player icon), and when you double click it you get "Can't mount file".  If you right click and hit eject you get "An application is preventing the volume 'IPOD' from being ejected."

---

### Post by double.emms on 2009-05-28
When mounted, I can manually navigate to /media/IPOD and access the contents, and from the command line I can issue a sudo eject successfully, but this still does not make it recognized by Nautilus/Rhythmbox/Amarok/Diskmount.  

Also, each time after you manually eject and then reconnect it, the /dev/sdx is incremented by one letter.

---

### Post by ayako0chan on 2009-06-01
Yes, this is the exact same problem as mine.

---

### Post by smitty96 on 2009-06-04
I have the same problem, I think it was caused because I didn't unmount it. I'm going to connect to a.... A.... This is hard for me.... A... Windows computer... *phew* Glad I got that over with. Anyway, I'll let you guys know if it starts mounting again. Stay tuned! :popcorn:

---

### Post by smitty96 on 2009-06-04
It worked! I'm not sure of how exactly to fix it without Windows, but if you have a friend that uses Windows, just plug it in and eject it, it should be fine! :)

---

### Post by ayako0chan on 2009-06-05
That's odd... I tried doing that, but it didn't work....
I'll try again though.  Maybe I didn't do something right....

---

### Post by smitty96 on 2009-06-05
Really? It worked fine with my Nano. What kind of iPod do you have? If it's anything but the Touch, I think this will work. The Touch is totally different, and I don't think it works very well with Linux anyway.

---

### Post by Stenrad on 2009-06-05
> **smitty96 said:**
> Really? It worked fine with my Nano. What kind of iPod do you have? If it's anything but the Touch, I think this will work. The Touch is totally different, and I don't think it works very well with Linux anyway.

The Touch doesn`t work too badly with Jaunty. Just install a program called iFuse and you`re good to go. I have been able to play music and watch videos directly from mine. :D

---

### Post by ayako0chan on 2009-06-06
> **smitty96 said:**
> Really? It worked fine with my Nano. What kind of iPod do you have? If it's anything but the Touch, I think this will work. The Touch is totally different, and I don't think it works very well with Linux anyway.

I have an iPod nano too, but when I connected it before, it didn't even appear as a hard drive on Windows.  It appeared as one on a Mac, though.  But then again, the computer I used was extremely bad, so I'll try again on another Windows...

---

### Post by loveandequality on 2009-06-07
x

---

### Post by loveandequality on 2009-06-07
Yea my touch also works good with iFuse the only thing is i have to jailbreak and istall VLC player beacuse i cant find another way to put songs but this is good soince in 6 months or less they are going to make iFuse even better becuase right now is only for developers so when is polish you wont have to jailbreak and i dont have to use VLC player but VLC takes all formats even oog and all viedeo formats is as easy as drag and drop but be careful dont put folders since for some reason i cant erase them only songs and movies alone and you can erase folders via SSH that is the only way i foind. So if you dont have Wi-fi in your computer de WARNING about the FOLDER. Also if you try to put songs in a encrypted folder all the songs in your touch will be ERASE it happen to me.

websit it tells you what to do:[http://matt.colyer.name/projects/iphone-linux/index.php?title=Create_A_Trace](http://matt.colyer.name/projects/iphone-linux/index.php?title=Create_A_Trace)

PS>your touch will be reconize as iphone and there will be 2 just 1 works tho.

---

### Post by whiteman on 2009-06-07
I have downloaded a book, an audiobook. It has two large mp3s. BUT it will only allow one of them to be put on the ipod. So I installed gtkpod. Seems like a pretty good porogram. I dont care for AMarok. It is just too confusing.Rhythmplayer  is better. Itunes beats em all. But HOW do you designate rhythmplayer top be your default "player" for gtk[pod. What dir is it in? I justcant find it anywhere. This is one. thing that bothers me about Ubuntu. I am totally without windows. I have complete Ubuntu computer so I either fix it here or I dont fix it. MAde the plunge.

---

### Post by smitty96 on 2009-06-07
> I have an iPod nano too, but when I connected it before, it didn't even appear as a hard drive on Windows. It appeared as one on a Mac, though. But then again, the computer I used was extremely bad, so I'll try again on another Windows...Hard drive? You mean a removable disk? I still don't know why it didn't work. Was it Windows XP? I used mine on XP, it might not work on older Windows.

> I have downloaded a book, an audiobook. It has two large mp3s. BUT it will only allow one of them to be put on the ipod. So I installed gtkpod. Seems like a pretty good porogram. I dont care for AMarok. It is just too confusing.Rhythmplayer is better. Itunes beats em all. But HOW do you designate rhythmplayer top be your default "player" for gtk[pod. What dir is it in? I justcant find it anywhere. This is one. thing that bothers me about Ubuntu. I am totally without windows. I have complete Ubuntu computer so I either fix it here or I dont fix it. MAde the plunge.I was trying to figure that out too, but I was just trying to get gtkpod to play music, since it doesn't right now when I click "play song". :/

---

### Post by ayako0chan on 2009-06-07
> **smitty96 said:**
> Hard drive? You mean a removable disk? I still don't know why it didn't work. Was it Windows XP? I used mine on XP, it might not work on older Windows.

Yeah, it was a recent version of Windows.  Maybe vista?  Don't really know.  And yes, a removable disk.

---

### Post by smitty96 on 2009-06-09
Hmmm, I think Vista should've worked. Maybe it's not the same problem, then. What version of Ubuntu do you have? That probably matters more than the version of Windows.

---

### Post by ayako0chan on 2009-06-09
> **smitty96 said:**
> Hmmm, I think Vista should've worked. Maybe it's not the same problem, then. What version of Ubuntu do you have? That probably matters more than the version of Windows.

I have Ubuntu 9.04 - the Jaunty Jackalope.

---

### Post by ayako0chan on 2009-06-10
I managed to get my hands on a Windows XP and disconnected it, but it still does not work on my Ubuntu.  It didn't even show up on an iTunes....

---

### Post by ertayone on 2009-06-22
I'm having the exact same problem with a 16gb iPod nano. Plugging it into a Windows and a Mac has been no help.

---

### Post by prettymess on 2009-06-24
I have the same problem, as well, with a 30gb iPod video.

---

