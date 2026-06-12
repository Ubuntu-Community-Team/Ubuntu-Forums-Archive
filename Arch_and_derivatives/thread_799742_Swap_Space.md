---
title: "Swap Space"
date: 2008-05-19
forum: Arch and derivatives
---

### Post by Dr Small on 2008-05-19
When I installed Arch, I setup 1GB of Swap space, and conky is all the time telling me that I am using 0b of it.

Does swap space actually get *mounted* to the filesystem, or is it just used? (I forget). My main goal is to shrink my swap space down to about 256MBs (or eliminate it completely) and use this space for a separate partition.

(I have 1GB {technically 800MBs} of RAM and I am only ever using 150MBs of it.)

So, what would be the safest way of shrinking or eliminating my swap space? I was thinking about using the Gparted LiveCD, but if you all have any other suggestions, I am willing to take you up on them. :)

Dr Small

---

### Post by will1911a1 on 2008-05-19
It's just used, not mounted, but it still has to be visible.

I'll have to get back to you on a way to shrink it.

---

### Post by will1911a1 on 2008-05-19
Looks like gparted should do the trick according to what I've read.

---

### Post by Dr Small on 2008-05-19
Yeah, I figured it would.
Well, I'm off to shrink it, and hopefully setup an encrypted filesystem on the space I have left :)

---

### Post by will1911a1 on 2008-05-19
> **Dr Small said:**
> Yeah, I figured it would.
Well, I'm off to shrink it, and hopefully setup an encrypted filesystem on the space I have left :)

Good luck. :)

---

### Post by prshah on 2008-05-19
> **Dr Small said:**
> When I installed Arch, I setup 1GB of Swap space, and conky is all the time telling me that I am using 0b of it.

Does swap space actually get *mounted* to the filesystem, or is it just used? (I forget). 

(I have 1GB {technically 800MBs} of RAM and I am only ever using 150MBs of it.)

So, what would be the safest way of shrinking or eliminating my swap space? I was thinking about using the Gparted LiveCD, but if you all have any other suggestions, I am willing to take you up on them. :)
Dr Small

In reverse order;

No need to use the live CD. Give the command ```
sudo swapoff -a
```, then use gparted, shrink it, and give the command ```
sudo swapon -a
``` You can also use "swapoff/swapon" by right clicking your swap partition in GParted.

You will need about 1.1 times your RAM for swap if you are using the hibernate feature, because that's where hibernation data is stored. The extra 10% is to make allowances for future bad sectors. With disk space so cheap nowadays, it's a nice idea to have ample swap space, rather than try to economize on it. There's no need for more, though. And you can shrink/dispense with it if you don't need/use hibernate.

Swap gets "mounted" with the swapon command. Actually, there is no real mounting involved; but swapon will "activate" the swap. However, you cannot make changes to the swap while it is "activated"/"mounted".

---

### Post by Dr Small on 2008-05-19
Thanks for that kind note, prshah. I could not have done without it! I was just going to write in and say that my swap was not being recognized now, but you cleared that up before I got back :) Thanks.

I had to remove /dev/sda2, (my swapspace) because Arch had already setup 4 primary partitions, so by shrinking sda2, I could not create a new partition.

So instead, I deleted sda2, recreated it as an Extended partition and created my swap space and the rest of the disc space for the other partition.

Now that *that* is done... Time to get my hands dirty with encrypting that other partiton :)

Thanks for all your help!
Dr Small

---

### Post by will1911a1 on 2008-05-19
Thanks for the post, prshah, I learned something. :)

---

### Post by handy on 2008-05-19
I love it when other people know what they are doing!

---

### Post by Dr Small on 2008-05-19
I got truecrypt installed and everything went honky dory. By the way, I never knew truecrypt came with user interface! I always had to use Forcefield on Ubuntu, but with Truecrypt on Arch, everything works much smoother.

The only problem, is I have to manually unmount /media/truecrypt1 before it will allow me to unmount it in truecrypt. That is just odd.

Dr Small

---

### Post by K.Mandla on 2008-05-20
I'm late to the party, but I rarely allocate more than 256Mb to swap. And then I knock down swappiness to zero, so it doesn't ever really get used. I'm strange that way, I guess.

---

### Post by Dr Small on 2008-05-20
Besides hibernation, when does swap actually get used? after all of my RAM is used? If so, I could completely eliminate swap space, as it is never used and I rarely use over half of my RAM.

---

### Post by Barrucadu on 2008-05-20
I keep swap at 512MB, just in case Arch and Openbox decides to consume over 2GB of RAM. I also set my swappiness to 0. Nice and zippy :)

---

### Post by ch_123 on 2008-05-20
> **Dr Small said:**
> Besides hibernation, when does swap actually get used? after all of my RAM is used? If so, I could completely eliminate swap space, as it is never used and I rarely use over half of my RAM.

Its a bit like virtual memory in Windows, if you push your PC you will start to see it getting used. Then again, I have never seen more than a few percent of it being taken up (on Conky) and none at all since I upgraded to 3GB of RAM. I might cut down on the swap space I have given from 1GB to 256MB

---

### Post by K.Mandla on 2008-05-20
> **Barrucadu said:**
> I keep swap at 512MB, just in case Arch and Openbox decides to consume over 2GB of RAM. I also set my swappiness to 0. Nice and zippy :)
Have you ever seen that happen? I mean, where you actually used more than 2Gb of memory at a time? I'm not being critical, I'm genuinely curious. I have 512Mb in this machine and I can honestly say I've never used more than probably 256Mb at a time, according to free -m and htop. I can't figure out what people are doing that takes up so much memory. :???:

---

### Post by handy on 2008-05-20
This brings up an interesting point for Mac owners who have to deal with the partitioning problems associated with Apple's implementation of the GPT partitioning scheme.

I don't believe I need a swap file at all on my 1Mb RAM iMac.  I don't work with video or sound files or play with 3D modeling.

How do I configure swappiness in Arch?

---

### Post by Barrucadu on 2008-05-21
> **K.Mandla said:**
> Have you ever seen that happen? I mean, where you actually used more than 2Gb of memory at a time? I'm not being critical, I'm genuinely curious.
No, but I do seem to use a lot of RAM, here's the top few lines of top:

```
top - 08:36:27 up 2 days, 21:57,  1 user,  load average: 0.18, 0.52, 0.65
Tasks:  74 total,   3 running,  71 sleeping,   0 stopped,   0 zombie
Cpu(s): 13.0%us,  1.7%sy,  0.0%ni, 85.0%id,  0.3%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   2075764k total,  1807012k used,   268752k free,   169036k buffers
Swap:   530136k total,        0k used,   530136k free,  1334088k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                                                                                                   
 9712 root      20   0 83240  58m 7160 R  8.0  2.9 303:53.25 Xorg                                                                                                      
 9806 barrucad  20   0  127m  66m  17m S  2.0  3.3 121:56.96 deluge                                                                                                    
22630 barrucad  20   0  296m  92m  16m S  1.7  4.6   6:39.30 opera                                                                                                     
22649 barrucad  20   0 99.0m  46m  18m S  1.3  2.3   0:55.41 /usr/bin/quodli                                                                                           
 9778 barrucad  20   0 37940  20m 9672 S  1.0  1.0  26:19.45 python                                                                                                    
 2539 root      15  -5     0    0    0 S  0.3  0.0   0:11.44 kjournald                                                                                                 
22707 barrucad  20   0 21920  13m 7744 R  0.3  0.7   0:03.55 sakura                                                                                                    
30863 barrucad  20   0  2132 1036  816 R  0.3  0.0   0:00.02 top                                                                                                       
    1 root      20   0  1656  556  488 S  0.0  0.0   0:02.38 init                                                                                                      

```

My guess is that Linux likes to spread out a bit when there is a lot of memory available, I can think of no other explanation why I could run the same programs just as quickly (well, a little slower) on 256MB of RAM on my laptop.

> **handy said:**
> How do I configure swappiness in Arch?
There is probably a better way but this is how I do it, stick the following line in /etc/rc.local:

```
echo 0 > /proc/sys/vm/swappiness
```

That 0 can be anything between 0 and 100, 0 being "use no swap thank you very much", and 100 being "swap out everything".

---

### Post by handy on 2008-05-21
> **Barrucadu said:**
> 
```
echo 0 > /proc/sys/vm/swappiness
```

That 0 can be anything between 0 and 100, 0 being "use no swap thank you very much", and 100 being "swap out everything".

Thanks Barrucadu, that worked.

Though it would not do accept the command with sudo, I had to log out of Openbox & into the root account for it to work.

---

### Post by Barrucadu on 2008-05-21
I know, it's a bit strange that it doesn't work with sudo. If I ever need/want to change my swappiness I just su into root, no need to restart anything.

---

### Post by handy on 2008-05-21
> **Barrucadu said:**
> I know, it's a bit strange that it doesn't work with sudo. If I ever need/want to change my swappiness I just su into root, no need to restart anything.

I have been doing so many three finger salutes out of x followed by startx, to check changes I've made to the openbox settings lately that it has become a habit!

It all happens so fast that it gives the illusion of being instantaneous too, which is nice. :-)

---

### Post by Barrucadu on 2008-05-21
Ooh, weird! I just noticed that according to conky I am using ~100MB of RAM, and according to free/top I am using ~1500MB of RAM. Which to trust, which to trust...

Further investigation reveals that this is because conky doesn't take into account cached memory, or buffers. For some reason, I have just over 1300MB cached.

---

