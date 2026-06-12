---
title: "Does Ubuntu have Vista-style prefetching?"
date: 2007-09-05
forum: Absolute Beginner Talk
---

### Post by anandus on 2007-09-05
Hi,

I've got Ubuntu and I'm very happy with it!
But one thing I noticed is that Ubuntu only uses 300Mb~400Mb of memory, which is a waste as I have 2Gb.

One of the things I loved about Vista is Superfetch, it really speeded things up.

Can I get something similar for Ubuntu?
Because it would be a waste to let this 1,5Gb unused.

Note:
This is *not* about Vista being a memory-hog or something like that, so please no discussions about that.. 
I really appreciated the fact that my memory is being used in vista ánd speeding up my system.

---

### Post by schorsch on 2007-09-05
When running linux the memory that is not used by the OS or by applications is used for file system caching ....so your 1.5 GB are not wasted but used in a different way as in Vista, I think ... I do not know Vista at all

---

### Post by asmoore82 on 2007-09-05
> **Given enough time and _Money_, Micro$oft will eventually re-invent UNIX.**

[https://wiki.ubuntu.com/CriticismFAQ#head-2f1e29146f06374fea151b13a51413bb52c11ea3](https://wiki.ubuntu.com/CriticismFAQ#head-2f1e29146f06374fea151b13a51413bb52c11ea3)

---

### Post by irish_flu on 2007-09-05
> **anandus said:**
> 

Note:
This is *not* about Vista being a memory-hog or something like that, so please no discussions about that.. 
I really appreciated the fact that my memory is being used in vista ánd speeding up my system.

I have an old programmer buddy who likes to say "unused RAM is wasted RAM".  :)

---

### Post by Lycaon on 2007-09-05
I personally don't know what superfetch does exactly, but i think you got something with this lil tool: preload

As the name suggests it fetsches common used or predicted binary data from applications and swaps it into the memory. So the program will load faster etc.

And this is the original discription:
> preload monitors applications that users run, and by analyzing this data, predicts what applications users might run, and fetches those binaries and their dependencies into memory for faster startup times.

Note that installing preload will not make your system boot faster and that preload is a daemon that runs with root priviledges.

 Homepage: [http://preload.sourceforge.net/](http://preload.sourceforge.net/)


install:
> sudo apt-get install preload

---

### Post by anandus on 2007-09-05
> **Lycaon said:**
> I personally don't know what superfetch does exactly, but i think you got something with this lil tool: preloadBasically thát's what Superfetch does.
It analyses the programs a user uses (and also the time of day or sequence of use) and tries to predict what to put in memory.
So I think this 'preload' comes very close :)
> As the name suggests it fetsches common used or predicted binary data from applications and swaps it into the memory. So the program will load faster etc.

And this is the original discription:


install:I'll try it out!
What is the general experience with this? Does it work? :)

PS. Thanks for your help all!

---

### Post by irish_flu on 2007-09-05
Hey, that's pretty neat.  I had not heard of this package.

---

### Post by sysdrum on 2007-09-05
down side to the vista way of doing prefetch is that it sets up a time table and then makes that memory unavaible in that time table for anything but what it thinks you are going to do. so sometimes you get a blue screen if you push the system past the ram limited (and it thinks there is not ram left)
I know most people will say but wait what about disk caching well vista uses that the same way that is where the problem lies, windows sub systems build a basic memory flow point and if the flow point drops or raises past it set precache it crashes. normal basic users never have to worry about that issue because 90 percent of them are only using 35 percent of there system. but gamer and/or any power user knows more ram means less crashes. So yes precache is good for most people faster system so on and so forth.

but if you are a power user or a gamer you will want to have atleast 512 free at all times. because the system will need it to do what you want when you want at random.

vista (any lvl aka price)

standerd user 
processor 2.8ghz or better
Ram 2gig 400 ddr
80gig hdd 133 ata
stardard video card that is vista complaint

Power user
processor dual core 2.8ghz or better
3gig 533 ddr2
os 80gig hdd sata
data storage/backup 250gig hdd sata
workstation card

Gamer
processor quad core 3.0ghz or better
4gig 533 or better ddr2
os 250gig hdd sata2
games 250 gig sata2
data storage/backup 500gig sata2
high end video card

ubuntu

standard user
processor 1.7ghz
ram 1gig
os 79gig swap 1gig ata 66/100/133
cheap video card

power user
processor dual core 2.8ghz or better
2gig 533 ddr2
os 80gig hdd sata
data storage/backup 250gig hdd sata
workstation card (nvidia recomended)

gamer 
ummm ?? there are games for linux?

---

### Post by Lycaon on 2007-09-05
Well i use it for about 4 months now, i can notice some difference. But i am using an old laptop with less ram etc. So the difference that i CAN experience is not to big. But a friend of mine with 2 gig ram and decent proc etc. "feels" the difference it makes very good. Try out your self and post your experience, im curious:D

---

### Post by afonic on 2007-09-05
> **anandus said:**
> Hi,

I've got Ubuntu and I'm very happy with it!
But one thing I noticed is that Ubuntu only uses 300Mb~400Mb of memory, which is a waste as I have 2Gb.

One of the things I loved about Vista is Superfetch, it really speeded things up.

Can I get something similar for Ubuntu?
Because it would be a waste to let this 1,5Gb unused.


Just install:

sudo apt-get install prelink preload

---

