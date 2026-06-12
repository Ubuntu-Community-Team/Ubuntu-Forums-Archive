---
title: "Speed issues"
date: 2005-12-23
forum: Absolute Beginner Talk
---

### Post by petef on 2005-12-23
Im trying to make the change at home to ubuntu Linux from windows XP. I have a Pentium 4 machine with 384mg of ram a 40gb hard drive. The machine\OS runs much slower than win xp any suggestions on how to speed things up ? 

I tried copying about 600 picture files from a CD backup I had created which took about 20mins this was much longer than on XP ?

Also open office seems very slow to start up ?

Please help as I really like linux and am trying to convince other people\the company I work for to make the change but I know these speed issues will be a concern.

Thanks

Pete

---

### Post by Perfect Storm on 2005-12-23
You need the right kernel to your Pentium 4:

```
sudo apt-get install linux-686
```

reboot


Also what graphic card do you have?
Which application did you use for backups?

---

### Post by petef on 2005-12-23
Thanks for the reply Aftificial Intelligence.

It's onboard Intel I think Im at work at the moment and can't remember off the top of my head.

It was just a copy to a CD not an actual backup the files were all fairly small jpeg's.

I also have it running at work on a celeron 1.4ghz with 160mg of ram would I also need to run the same command for this as it is also slow.

Cheers

Pete

---

### Post by Perfect Storm on 2005-12-23
For Disc burning/data etc. I can recommend Gnomebaker or nerolinux (commercial)

To get gnomebaker:
```
sudo apt-get install gnomebaker
```
(remember to setup your source list to get this application).

If you have nero 6 serial code you can get nerolinux for free.

---

### Post by petef on 2005-12-23
Sorry I don't think I made myself clear. I burned the disk on Windows XP then on Ubuntu\Linux copied the folder from the CD onto the Linux machine this is what took about 20mins. 

Should I also use your previous command on a celeron machine.

Thanks for your help.

Pete

---

### Post by Perfect Storm on 2005-12-23
I think the commanline is much faster when coping instead of gui.

or it could be that the DMA isn't enable on your DVD/CD-disc.
Read more here: [http://doc.gwos.org/index.php/DMA](http://doc.gwos.org/index.php/DMA)



Aye, you need to install linux-686 for your celeron.

The thing to really speed up ubuntu/linux is getting install the graphic driver. Be best to buy a GF card, not the best of them are required. I don't have the knowledge of onboard graphic cards.

---

### Post by petef on 2005-12-23
Yeah I may try the copy again using the command line see how quick that runs.

Will have a look around to see if I can find a suitable driver for the graphics card.

Happy Christmas and New year to you.

Cheers

Pete

---

### Post by Nameless on 2005-12-23
[QUOTE=Artificial Intelligence]You need the right kernel to your Pentium 4:

```
sudo apt-get install linux-686
```

[/QUOTE]

I've got an old P4, is the above correct for all P4s?  

Is this something that I will not let me boot if I install it and its not the right kernal?  I'd like to avoid that doing that again if I can.  Maybe a better question is, is there a way to verify that this will work for me before I try it?

---

### Post by fordfan753 on 2005-12-23
As I understand it the 686 kernel can be used for any PIV, PIII, and just about any later celeron, as well as most AMD K6 and K7 processors, although for the K7 I still always use the K7 kernel.

---

### Post by Nameless on 2005-12-23
[QUOTE=fordfan753]As I understand it the 686 kernel can be used for any PIV, PIII, and just about any later celeron, as well as most AMD K6 and K7 processors, although for the K7 I still always use the K7 kernel.[/QUOTE]

When I initially installed Ubuntu I did a dual install (with XP) with the i386 install disc.  Would I simply install the 686 kernel over what I currently have using the above command?

---

### Post by Perfect Storm on 2005-12-23
No kernel linux-686 will be install next to linux-386. So you can choose to boot up in 386 or 686. You will automatically boot up with the newest installed kernel.

If you're are saticfied with linux-686 you can safly remove linux-386.

---

### Post by fuscia on 2005-12-23
try bum (boot up manager), as well. using it to shut off a bunch of stuff i didn't need gave me the most noticable change in speed.

---

### Post by jbmalone on 2005-12-23
Is there anyway to check which Linux kernal I am running?  I have a P4, and don't know if I am running 686.

---

### Post by fordfan753 on 2005-12-23
[QUOTE=jbmalone]Is there anyway to check which Linux kernal I am running?  I have a P4, and don't know if I am running 686.[/QUOTE]

```
uname -a
```

---

