---
title: "how much memory?"
date: 2007-04-02
forum: Absolute Beginner Talk
---

### Post by cap10kirk on 2007-04-02
how do i find out how much memory my box has? While on the subject, how do I look up my cpu speed?

Thanks for the help,
kirk

---

### Post by bikeboy on 2007-04-02
There are other methods but 2 really quick ones are:

```
free -m
```

```
cat /proc/cpuinfo
```

One disclaimer, if your cpu is throttling you might not get an accurate indication of speed from that. If so, do something intensive and run it while that's happening.

---

### Post by RKCole on 2007-04-02
Got there just about ten seconds before me, bikeboy.

Those are the quickest ways I know of to find this type of information.

Also, if you're interested in space on yoru hard drive, you can run:

```

df -h

```

df standing for disk free space, and -h for "human-friendly" output...at least that is what I was taught in college.

Take care.

---

### Post by bikeboy on 2007-04-02
> **RKCole said:**
> Got there just about ten seconds before me, bikeboy.


Hehe, don't you hate that?

Good bit of extra info with df though, nice work :)

---

### Post by cap10kirk on 2007-04-02
that is good info. But I have one question. I have 2 pieces of ram memory sticks in my box. One is 512k the other is 256k. When I run

free -m
the output is this:

 total           used       free     shared         buffers     cached
Mem:           250         245          4                    0          2         66
-/+ buffers/cache:        176         73
Swap:         1474         18       1456


Does that output seems correct?

thanks again,
Kirk

---

### Post by Warpnow on 2007-04-02
```


                  total        used       free     shared         buffers     cached
Mem:           250         245          4            0                  2         66
-/+ buffers/cache:      176        73
Swap:         1474         18       1456


```

code tags are you're friend. Looks like A) You have very little RAM (256mb) on your system and B) What you have is being used pretty quickly. I'm nowhere near an expert, but you might want to consider upgrading to 2 sticks of 512 or something. I'd check what you're board can handle (google its serial numbers and find a manual).

Ram is a very easy to do upgrade that can make a fair bit of difference. Its also what most store bought pcs lack because most inexperienced buyers only look at cpu and HD space, and maybe its various drives. If you game, you definitely need decent ram, or all you're games will lag like crap.

---

### Post by bikeboy on 2007-04-02
The output seems incorrect (assuming the hardware is working), I would expect 768mb or therabouts.

Perhaps try a different way of looking at memory. Cut and paste this into a term: ```
cat /proc/meminfo | grep MemTotal
```

You should see something around 768000k. If not, try rebooting Ubuntu and choosing the Memtest86+ option.

edit: in response to Warpnow, 256mb (as per output) is quite low but even 512mb is plenty. If the 2 sticks work right there is no need to upgrade the ram in this case, the expense of 2x512mb sticks would be unnecessary IMHO.

---

### Post by Warpnow on 2007-04-02
I believe getting 2 different size RAM sticks to work together is unccomon, or such is what I've been told. I've heard that they're very sensitive and unless they're the same model number they're not likely to work together.

If all else fails I'd remove the 256k that way it reads the 512 instead.

It really depends what you do with your pc. If your a casual desktop user you're probably fine with 512, but being a person who enjoys tasks such as video editting as well as running a game server (at the same time usually) I upgraded my 512 to 2 gigs and saw a huge difference in the speed of my machine.
 
No computer's perfect for one person. Its what you do that matters.

Edit: Ram is cheap. I got my 2 sticks of 1 gig for about $115 shipped and this was over a year ago (though I waited several weeks for a good deal).

Edit edit: My suggestion for 2 sticks of 512 was when I thought he had 256mb total. IF he can get both sticks to work that'd be fine, yeah. Especially for somene not planning on doing to many memory-intense things.

---

### Post by jvc26 on 2007-04-02
It may be worth removing the 256 one, and running the same test with the 512 only (or seeing whether the system is able to boot at all) as it looks like the two are not sitting well together and as a result you're only being able to access the RAM from one of the sticks. Either that or the 512 on is broken.
Il

---

### Post by bikeboy on 2007-04-02
> **Warpnow said:**
> I believe getting 2 different size RAM sticks to work together is unccomon, or such is what I've been told. I've heard that they're very sensitive and unless they're the same model number they're not likely to work together.

For dual channel yes, buying a matched pair (2 identical chips in one pack) is best. Otherwise it doesn't really matter. I added a 512mb stick to a friend's PC yesterday and it played nicely with the existing 2x128mb.

---

### Post by cap10kirk on 2007-04-02
I had to remove the 256mb from the box. The box is sensitive. My box has 3 memory slots, so I put two 512mb in it, right next to each other. The box only recognized one of them. A buddy told me to put one in the 1st slot, and one in the 3rd slot. That did the trick. The box recognized both of the sticks.

Thanks for your help fellas,
Kirk

---

### Post by RKCole on 2007-04-02
Good to hear that things are running smoothly now, cap10kirk.  I need to upgrade my RAM when I can finally afford it (who knows when that will be on my budget...).  I've been running on 256MB since 2004...

Speaking of which...Warpnow, bikeboy...have any RAM to spare? :)

Take care, guys.

---

### Post by airtonix on 2007-04-02
yeah you need to refer to your motherboard manual regarding use of ram sticks...

this isnt a problem with ubuntu as it will affect windows as well. ergo its a hardware thing

my mother board manual specifically dictates what quantities and the placement of ram i can use on my mobo.

---

### Post by bikeboy on 2007-04-02
> **RKCole said:**
> 
Speaking of which...Warpnow, bikeboy...have any RAM to spare? :)


If only, I have 384mb total. Not much better off than you :(

Glad you got it going cap10kirk, sometimes the bios can be picky.

---

### Post by loyeyoung on 2007-06-02
Here's a trick that gives you much more detailed information about your memory. 

lm-sensors has a script that will give you detailed, bank-by-bank analysis of each memory stick you have, including manufacturer, model number, design characteristics, etc. 

There are many helpful hardware detection and monitoring features of lm-sensors. Personally, I install it on every computer I build, unless I have compelling reasons not to. 

First, install lm-sensors using your favorite package manager (Synaptic, Adept, or aptitude). 

Next, you'll need to acquire root privileges. Open your favorite terminal (Konsole, xterm, console, etc.) and type:
# sudo -s
Type your password when prompted. You are now the root user. Feel the power. 

Then,
# sensors-detect
Follow the instructions. Most folks can just accept the defaults. Let it write the modules it needs to /etc/modules. If you can reboot without causing a stir, do so. If you are working on a server that you can't reboot, then for each module that sensors-detect told you it needs, run "modprobe [module-name]", replacing "[module-name]" with the name of the module. In other words, use modprobe to insert each module into the kernel. NOTE: INSERT THE MODULES IN THE ORDER THAT sensors-detect LISTED THEM.

Next, 
# sensors -s
# cd /usr/share/doc/lm-sensors/examples/eeprom
# ./decode-dimms.pl | less

If you want the output saved to a text file on your desktop:
# sudo ./decode-dimms.pl > ~/Desktop/DIMMs-de-facts.txt

Happy Trails,

Loye Young
[http://www.iycc.net](http://www.iycc.net)
Laredo, Texas

---

