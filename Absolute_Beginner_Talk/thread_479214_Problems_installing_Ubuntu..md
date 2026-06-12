---
title: "Problems installing Ubuntu."
date: 2007-06-20
forum: Absolute Beginner Talk
---

### Post by tim_tim on 2007-06-20
Hi, I'm new to linux and new to this forum, I've been looking over this forum every once and a while to see if i could find anyone with the same problem I'm having. I just downloaded Ubuntu 6.06 LTS desktop edition off of the ubuntu website. I burned it to two cd and a dvd. I've been trying to install it in this old pc i have in my sitting in my living room, its an HP it has about 258mb or something close to that. It has an intel celeron cpu, i don't remember much after that. Its not that old, maybe a few years.

What my main problem is, when i boot it up i get the normal little ubuntu screen that says install or run ubuntu and all of that but when i actually chose to run it it says something like installing...something something and then i can here the disk spinning really fast and then it goes black and my totally computer restarts with the same "install or run ubuntu" screen and i've tried all of the options but the only one that seems to actually do anything is memory test. and the other weird thing is when i choose to check disk for defects it does the same thing as the rest of the options. anyway I'm wondering if anyone noes what the problem might be?? and how i could fixing it? I really want to get ubuntu working on that computer, it has been a thing I have wanted to do for a while now. If this has been a repeating topic on this board I'm very sorry. Thank you for your time I hope someone can help.

---

### Post by foxmulder881 on 2007-06-20
We need information about the specs of your system. It sounds like the Ubuntu doesn't like a piece of your h/ware.

What else can you tell us about you system specs?

---

### Post by NeoLithium on 2007-06-20
If it has 256MB of RAM, which is what I'm guessing, you might be best off with Xubuntu, as it uses XFCE as a window manager, and will run a lot smoother on a computer with that amount of RAM.  As well, the Desktop CD's run the live version off the computers' RAM, so it would be better to use the Alternate Install CD, which doesn't try to run the desktop off your CDRom and Memory :)

---

### Post by atria on 2007-06-20
Try booting with the second option (failsafe)

---

### Post by tim_tim on 2007-06-20
> **NeoLithium said:**
> If it has 256MB of RAM, which is what I'm guessing, you might be best off with Xubuntu, as it uses XFCE as a window manager, and will run a lot smoother on a computer with that amount of RAM.  As well, the Desktop CD's run the live version off the computers' RAM, so it would be better to use the Alternate Install CD, which doesn't try to run the desktop off your CDRom and Memory :)


i always here about this "alternate install cd" what is it?? and where can i find??(sorry for these newbie questions) and as far as specs go, i don't really know i stated the only ones knew i'll get back to you soon and tell tell you them. and i'll check into xubuntu. Thanks again, and you guys reply really fast, its amazing.

---

### Post by atria on 2007-06-20
The alternate install cd differs from the normal cd because the alternate install cd does not contain a livecd environment. Basically you do a ubuntu installation without booting into a full featured desktop.

Download it from [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

Check "Check here if you need the alternate desktop CD. This CD does not include the Live CD, instead it uses a text-based installer." to download the alternate install CD.

> Thanks again, and you guys reply really fast, its amazing.
Welcome to the community ;)

---

### Post by tim_tim on 2007-06-20
alright i got xubuntu downloaded and burned to a disk and i still have a problem. when i go to "start xubuntu i get an error says on the bottom of the screen 

 Int 14: cr2 cf000000 err 00000000 EIP c020c384 cs 00000000 flags 00010007

Stack: c00f70a0 c037108c 00000002 c00f7dao 00000000 00000000



does anyone know the problem???

thanks.

---

### Post by hyper_ch on 2007-06-20
did you do a disk check?

---

### Post by tim_tim on 2007-06-20
yea, and i got that error thing. I don't really understand it. I know it is NOT the disk because I'm running it right now and I'm writing this reply on my main PC in my room off the live cd. I can't believe its running so good and its using a disk and my ram. I was considering at first just putting it on my main pc that im using right now but i do a lot of video editing/animation and design/ web stuff and i kind of need all the room. I still might consider it, is it possible to just install linux to an external and then when ever i want to use it i just turn the external on and have a dual boot? My only idea about that other pc is there is some hardware that it doesn't work with, idk though. i'll just wait for more replies.

---

### Post by molly_001 on 2007-06-20
> **tim_tim said:**
> tim_tim writes:

alright i got xubuntu downloaded and burned to a disk and i still have a problem. when i go to "start xubuntu i get an error 

does anyone know the problem???



thanks.



You need to test your RAM memory with MemTest86 or from the LiveCD just choose at the main menu the option for testing RAM memory.  Let it run several hours.

---

