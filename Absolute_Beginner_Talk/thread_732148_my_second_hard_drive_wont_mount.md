---
title: "my second hard drive wont mount"
date: 2008-03-22
forum: Absolute Beginner Talk
---

### Post by cowboyup02119 on 2008-03-22
hello to all!!!

i just killed vista because i got the blue screen of death six times, while installing and doing updates....

i install everything in my first hard drive and did all the updates and got all the drivers...thanks to developers who including everything in the updates you all are awesome!

i have a second hard drive 500GB with only media on operating system on it. when i go to places>computer

i can see my second hard drive but when i click to open it says CANNOT MOUNT VOLUME.
> UNABLE TO MOUNT THE VOLUME "MEDIA FILES" thats the name of second hard drive, i have like 10 GB of music and over 200GB of DVD's saved there. is there any way to recognize it and use my media on there...

thanks to all you can help and god bless!
__________________

---

### Post by manishtech on 2008-03-22
Please paste the output of the command
[INDENT]ls /dev/*d*
[/INDENT]This command is to see how many partitions you have on your second hard disk...
first * is to match **h** or **s** and second * to match **b** or **c**

---

### Post by drubin on 2008-03-22
I assume that drive **was** used for windows or at least in windows ?

Try installing  ntfs configuration tool.  It should be under the add/remove programs. 

That might help.

---

### Post by jan quark on 2008-03-22
please also post the result of this terminal command
```

sudo fdisk -l
```

---

### Post by manishtech on 2008-03-23
I think it would be better if you also post the output of df command, this tells which partitions are mounted.
So now you have to post the output of three commands

[COLOR=DarkRed]ls /dev/*d*[/COLOR]

[COLOR=DarkRed]sudo fdisk -l[/COLOR]

[COLOR=DarkRed]df[/COLOR]

---

