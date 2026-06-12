---
title: "Help in installing Ubuntu"
date: 2007-06-01
forum: Absolute Beginner Talk
---

### Post by mAkKoOo210 on 2007-06-01
[FONT=Comic Sans MS]Hi guys, 
I need some help in installing Ubuntu 7.04.
I launched my Live Cd and went through the process of installation. There, as you know, there are three options:
[/FONT][LIST]
[*][FONT=Comic Sans MS]Guided. Formatting the entire HD[/FONT]
[*][FONT=Comic Sans MS]Guided. Using the largest continuous free space[/FONT]
[*][FONT=Comic Sans MS]manually edit partition table[/FONT][/LIST][FONT=Comic Sans MS](I hope I wrote it correctly, I used the Italian language).
So, even if I did a backup of my data, it have been hard for me to Format the entire disk and to totally renounce to Windows Xp. I know it is a bad OS, but I'm attached to it :oops:...
The main point is: I'd like to have the two OS together for a while, just to "get in touch" with Ubuntu :D 
Then I decided to try with the second option (even didn't understanding what it was), but it occur an error. I don't remember it perfectly, but it was, more/less:
> the disk has not free space enoughWell, my HD is so partitioned: 
C: where I install programs and Windows
D: for my data
G: 7,95 GB that I don't use.

I would like to use it as a partition where to install Ubuntu at first. It is formatted NTFS.
Well, How can I do to install there Ubuntu (someone told me that it is enough space)?
The "manually edit partition table" scares me...is it possible to use the second option?
If not, some saint would help me in using the third option?
Thank you:)


P.S. Sorry if my english is so bad but I'm Italian, it is not my mother languageO:)[/FONT]

---

### Post by bigken on 2007-06-01
you must defrag windows a couple of times 1st and backup any important data
to make your partitions you could use the gparted live cd its very easy and straight forward


or in the live cd partition editor select the third option and select g and delete it then create 
2 partitions 1 for the os and 1 for your swap file the best size for a swap file is 
twice you ram ie 512=1gig

---

### Post by mAkKoOo210 on 2007-06-01
Ok, I'm getting gparted. What do I have to do with it, once I've got it? Do I have to change the File system in my 7,95Gb partition?

---

### Post by darren1270 on 2007-06-01
Hmmm... I know it's late here in the US but you want to try and install on your HD G:  ?????

---

### Post by mAkKoOo210 on 2007-06-01
I have only an HD. It has three partitions, one is G: and, because I don't use that space, I'd like to install there Ubuntu.:)

---

### Post by mendingo84 on 2007-06-01
Ciao,

First of all, if you're planning Ubuntu as your secondary OS, you should break that unused 7.95GB partition into 2, using PartitionMagic or whatever you want. One of 1 GB which you will use as SWAP, and the rest of 6.95GB for the OS. When you'll get to installing, you'll have to use the Manual Configuration Option in order to place your OS on that specific partition. But it has a very easy to use interface. Don't be scared :).

By far, this is not the best solution in general. But i think it is the appropriate one for you.

Forzza Juve! ;)

---

### Post by mAkKoOo210 on 2007-06-01
Ciao:)
The last time I tried to use the third option, I had some errors, and I was getting angry by Ubuntu:P
Well, I think I can try again:
Can't I use the tool in the live Cd that allows me to re-partition the existing partitions?
And, then, what do I have to do? there are some options that I don't understand

---

### Post by mendingo84 on 2007-06-01
It's safer to repartition using GParted since you were downloading it :) (It does the same as PartitionMagic, but for free :D). After that, when installing, and getting to the stage of partitioning, you would select Manual Configuration (or anyhow that third option is called) and after that:  you should have listed 4 partitions, of which, one will be of 1GB and one of 6.95GB. You will be able to select what to do with those partitions ( a drop-down menu will be present for each partition). For the one with 1GB select the  "SWAP" option, and for the one with 6.95GB select the "/" option. The "/" means root...you'll get to understand that later :)

---

### Post by mAkKoOo210 on 2007-06-01
> **mendingo84 said:**
>  and for the one with 6.95GB select the "/" option. The "/" means root...you'll get to understand that later :)
yes, it was there that I had some problems with the previous version of Ubuntu, it didn't recognise the "/" command O.o
Well...I think I will try again!:)
Another question: what is the difference between the Gparted Live Cd and the program itself?

---

### Post by mendingo84 on 2007-06-01
Basicly, ... none! :)

But are you sure you want to edit your partitions meanwhile accessing resources in one of them? What if you resize your windows partition while running it? Now that would be a mess :). It is safer to resize using LiveCD's .  Good luck with your Ubuntu installation. :popcorn:

---

### Post by mAkKoOo210 on 2007-06-01
I understand:D
Well, I'm downloading gparted.
Stay tuned^_^

---

### Post by mAkKoOo210 on 2007-06-01
Hey guys
I did it!!!!
Wow, I'm so happy^_^
Now I'm writing from Windows Xp just 'cause I couldn't set the internet connection, but I'm going to look into the forum and the guides how-to^_^
Thank you all!

---

