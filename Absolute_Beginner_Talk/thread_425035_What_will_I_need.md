---
title: "What will I need?"
date: 2007-04-27
forum: Absolute Beginner Talk
---

### Post by And1945 on 2007-04-27
Hi guys!

I finaly (almost) have everything to install Ubuntu on my "old" computer, I was just wondering what drivers I will need. I know that my network adapter (onboard) might need a driver, everything I can find afterwards, so that doesnt matter, but I will need a driver for that, the question is, if Ubuntu reconizes it and installs it itself.

It is as I said an onboard NIC, on an MSI motherboard K7N2 Delta2 Platinum.

Will it install itself, or will I need a driver for it?

Thanks in advance.

---

### Post by ImpelGD on 2007-04-27
Don't have information on that myself, but have you [checked here]("https://wiki.ubuntu.com/HardwareSupport")?

---

### Post by And1945 on 2007-04-27
Now I have. It isnt listed.

---

### Post by Schalken on 2007-04-27
Use the 7.04 desktop livecd. If it fails to boot into the livecd there may not be enough memory, in which case you need the "alternate" desktop cd. Remember to back up all data on the hard drive that you need before proceeding with install.

Basic things such as onboard NIC are usually supported, but the only way to know for sure whether Ubuntu will work on certain hardware is to test it on said hardware.

So give it a shot.

---

### Post by Cypher on 2007-04-27
On the contrary, your on-board Ethernet is indeed supported. Check [here]("https://wiki.ubuntu.com/HardwareSupportComponentsWiredNetworkCardsNvidia"). You have the nForce2.

---

### Post by And1945 on 2007-04-27
Enough memory? It has 1024mb DDR3200 ram.

Just giving the specs for the computer here.
AMD 3200+ 32bit
MSI K7N2 Delta2 Platinum
1024 PC3200 Geil Ram
200GB WD 2mb cache
ATi 9800XT 256mb

Hmm, old computer, nah... just slower than my new one.

Thanks.

---

### Post by And1945 on 2007-04-27
> **Cypher said:**
> On the contrary, your on-board Ethernet is indeed supported. Check [here]("https://wiki.ubuntu.com/HardwareSupportComponentsWiredNetworkCardsNvidia"). You have the nForce2.
Sweet. the motherboard was just not listed in there.

I will be having no problems then. I will install Ubuntu later today then, just have to get a D-Sub cable.

thanks guys!

---

### Post by deadgobby on 2007-04-27
That is a good system. You have a AMD chip and it seems a ATI card. 
AMD set up
[https://help.ubuntu.com/community/Installation/32bitonAMD64](https://help.ubuntu.com/community/Installation/32bitonAMD64)
 As for the ATI card. I think if installing feisty you may be fine. You may need to edit the xorg.conf, but I hoope some one can shed little light on that.
Gobby

---

### Post by Cypher on 2007-04-27
> **And1945 said:**
> Sweet. the motherboard was just not listed in there.

I will be having no problems then. I will install Ubuntu later today then, just have to get a D-Sub cable.

thanks guys!
That list doesn't describe general things like Motherboards, but rather specific hardware. So if you figure out which chip you have exactly, that guide is useful. :)

---

### Post by And1945 on 2007-04-27
> **deadgobby said:**
> That is a good system. You have a AMD chip and it seems a ATI card. 
AMD set up
[https://help.ubuntu.com/community/Installation/32bitonAMD64](https://help.ubuntu.com/community/Installation/32bitonAMD64)
 As for the ATI card. I think if installing feisty you may be fine. You may need to edit the xorg.conf, but I hoope some one can shed little light on that.
Gobby
Do I need to install drivers? The system is not intended for any gaming what-so-ever. As long as it can display something, im kinda happy.

> **Cypher said:**
> That list doesn't describe general things like Motherboards, but rather specific hardware. So if you figure out which chip you have exactly, that guide is useful. :)
Ahhh, okay. I actually didnt realize that. Sorry, kinda new to all of this. Tried Red Hat some year ago... that didnt go well, but Linux has come a LONG way since then. Someday Microsoft will have some problems if you ask me.
:guitar:

---

### Post by Cypher on 2007-04-27
I don't think you'll need drivers, the stock ATI drivers might just work, but you will get better performance by installing specific drivers. But that you can leave for when you've gotten everything up and running..

---

### Post by And1945 on 2007-04-27
Okay, I will then.

Actually I am installing Ubuntu right now. Was a little weird having to think about swap /home and / all of a sudden.

3GB for swap and /, and the rest of 200gb hdd for the system, that should do it.

---

### Post by Cypher on 2007-04-27
Uhh..what is the rest of the system?? 3GB for SWAP is too much and not enough for "/"..

---

### Post by And1945 on 2007-04-27
Well, too late for that now.

Anyways. I have downloaded the ATI drivers, but how do I install them? I know this is a dumb question, its a .run file, it just says it cant run it with UTF-8 or western. Whatever that means. Is there any special place I should go to, to install this? I just double clicked on it.

Character coding that is.

---

### Post by Cypher on 2007-04-27
So you got Ubuntu installed? Can you show us the output of "df" and "mount"..

Go to the place where you downloaded the ATI driver and try "./<file-name>.run". If tha spits an error out at you.
Do
```

chmod 755 <file-name>.run
./<file-name>.run

```

---

### Post by And1945 on 2007-04-27
> **Cypher said:**
> So you got Ubuntu installed? Can you show us the output of "df" and "mount"..

Go to the place where you downloaded the ATI driver and try "./<file-name>.run". If tha spits an error out at you.
Do
```

chmod 755 <file-name>.run
./<file-name>.run

```
I must say, that I have _no_ idea of what you are writing about. Usually I understand something, but you have lost me completely, remember, I am totaly green when it comes to linux.

---

### Post by And1945 on 2007-04-27
I just right clicked on it, and put a mark in "allow to run as program", the only place it did something was in "run in console", but didnt really do anything besides unpacking it, I suppose.

---

### Post by Cypher on 2007-04-27
Hehe..you know I gotta start thinking more like a Desktop user. I seem to revert to my Linux command background for everything..:)

Anyway, If it did unpack files, can you use browse over to that directory and see if there is anything else of interest in that folder now??

---

### Post by And1945 on 2007-04-27
I dont know if it did... it shows some kind of error message right before it closes, I dont if it unpacks it or just tests it.

---

### Post by Cypher on 2007-04-27
Ahh..so then the Terminal it is..:)

Try Application->Accessories->Terminal and "CD" over to the directory where you download the .RUN file and try the commands that I had previously talked about, and with the console not going away we can figure out what the problem is..

---

### Post by And1945 on 2007-04-27
> **Cypher said:**
> Ahh..so then the Terminal it is..:)

Try Application->Accessories->Terminal and "CD" over to the directory where you download the .RUN file and try the commands that I had previously talked about, and with the console not going away we can figure out what the problem is..
Is .Run files made for console execution?

---

### Post by And1945 on 2007-04-28
There isnt any easier way to install .Run files?

---

### Post by And1945 on 2007-04-28
> **Cypher said:**
> So you got Ubuntu installed? Can you show us the output of "df" and "mount"..

Go to the place where you downloaded the ATI driver and try "./<file-name>.run". If tha spits an error out at you.
Do
```

chmod 755 <file-name>.run
./<file-name>.run

```
Syntaz error: Bad substitution it says.

---

### Post by And1945 on 2007-04-28
Now I downloaded the newest, just for the fun of it, but tells me this:
> Detected version of X does not have a matching 'x720' directory
You may override the detected version using the following syntax:
     X_VERSION=<xdir> ./ati-driver-installer-<ver>-<arch>.run [--install]

I understand what it is telling me, I just dont understand what it wants me to write, the most logical for is:
>  x710 ./ati2.run
I renamed the file so something more simple to work with.

I really hope someone can help me. This 1024x768 resolution on a 22" monitor is annoying.

Thanks.

---

