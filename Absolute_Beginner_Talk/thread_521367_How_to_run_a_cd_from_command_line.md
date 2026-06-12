---
title: "How to run a cd from command line?"
date: 2007-08-09
forum: Absolute Beginner Talk
---

### Post by uberhaxor??? on 2007-08-09
How to run a CD from the command line in Ubuntu Server edition?

---

### Post by splintercellguy on 2007-08-09
What kind of CD is it and what are you trying to do?

---

### Post by uberhaxor??? on 2007-08-09
Its Damn Small Linux liveCD. I burned it in Nero with  the option "Burn Image to Disc". It worked on an older box, but doesn't work during boot-up. So I am trying to run it from the command line.

---

### Post by splintercellguy on 2007-08-09
I'm not sure if DSL can be started in such a manner, maybe you need to change BIOS boot order? If you can start in such a way, I guess you would mount /dev/cdrom somewhere and run whatever it is you have to run?

---

### Post by Hospadar on 2007-08-09
It's going to be mounted in /media/<something>  I'm not sure if server addition automatically mounts stuff, so you may have to do it manually with something like ```
sudo mount /dev/<the name of your drive> /media/<where you want to mount>
```You don't have to mount to /media but that's the preferred place to mount drives

Edit, yeah you'll need to actually boot off the cd, changing the boot order will be the way to go.

---

### Post by uberhaxor??? on 2007-08-09
What's monting and all that? I know its an irritating question. My BIOS  is set to boot from CD first. The whole point of installing DSL is to check whether my onboard ethernet adapter works at all.

---

### Post by splintercellguy on 2007-08-09
Mounting is basically making the device usable by attaching it to a mount point. Perhaps your burn was bad and that's why DSL didn't boot.

---

### Post by uberhaxor??? on 2007-08-09
I tried the following thing:

> sudo mount /dev/d/media/hda2

---

### Post by deadgobby on 2007-08-09
If you used the same CD to install on a older box. The CD should be good right ;>) ! Is the CD reading at the boot of the system and you get a command prompt? If you get the command prompt. did you simply type in 
install
 All so did you test the CDROM if it was working with the older O/S if any at all? It may be the simple task of cleaning the CDROM or installing a new/swap out CDROM device.

 
Gobby

---

### Post by uberhaxor??? on 2007-08-09
It was a re-burn anyway. It showed up and then it said couldn't find the KNOPPIX file system. But anyway. How do i test a connection to the net in ubuntu server.

---

### Post by EndPerform on 2007-08-09
> **uberhaxor??? said:**
> What's monting and all that? I know its an irritating question. My BIOS  is set to boot from CD first. The whole point of installing DSL is to check whether my onboard ethernet adapter works at all.

Why not do:

```
ifconfig
```

From the command prompt.  That will tell you right away if any network cards have been detected.  You should see your card as eth0.

---

### Post by uberhaxor??? on 2007-08-09
it didn't work. I think its checking stuff on local network. How do you use wget?

---

### Post by EndPerform on 2007-08-10
> **uberhaxor??? said:**
> it didn't work. I think its checking stuff on local network. How do you use wget?

I thought you had wanted to know if your card was there, and ifconfig would show that.

  Wget is simple:
```
wget http://path/to/file
```

Or even more simply, just try pinging somthing:
```
ping yahoo.com
```

Then hit Ctrl-C to end it.

---

