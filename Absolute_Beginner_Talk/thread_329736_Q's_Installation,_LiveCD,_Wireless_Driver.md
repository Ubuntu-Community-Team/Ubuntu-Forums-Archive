---
title: "Q's: Installation, LiveCD, Wireless Driver"
date: 2007-01-02
forum: Absolute Beginner Talk
---

### Post by itstabish on 2007-01-02
Hi,

I've read the "Read me First" files to make sure I'm not bothering anyone by posting something that's already been done before but I'm human so I might've skipped it. Show a brother some ubuntu love :)

Okay well I'm running a Dell Inspiron 6400. I have a wireless network card. First of all, is it possible to have the wireless netgwork card detected using the LiveCD? Will I be able to access the internet? It doesnt seem to be working. Secondly, If I want to install Ubuntu, is it possible to make a new partition from the freespace on my NTFS partition? How do I do this. I tried to use the gnome partition maker from the LiveCD but It didnt work.

I hope someone can answer my questions. Please let me know if there's anything you need to help me.

Thank you SOOO much!

And thank you ALL for Ubuntu :)

---

### Post by michaeljustman on 2007-01-02
If your disk is partitioned with NTFS you cannot resize it with gparted. You'll need a third party windows application like Partition Magic to do it.

Not sure if there is a free equivilent for Partition Magic though.

Linux doesn't always play nice with wireless off the bat and most likely if the LiveCD didn't see your wireless card, you'll have to play with it when it's installed. ndiswrapper worked wonders on my machine.

---

### Post by itstabish on 2007-01-02
That was quick thanks alot :)

I kind of thought all that too. What's ndiswrapper? IS it in the liveCD?

---

### Post by spockrock on 2007-01-02
ndiswrapper is not on the live, disc.

ps gparted can resize ntfs partitions, dont use partition magic, it doesnt play nice with linux.  safest bet is use the gparted on the edgy live disc, or the gparted live disc.

---

### Post by itstabish on 2007-01-02
What's edgy or gparted live disc?

---

### Post by spockrock on 2007-01-02
sorry edgy, is the name of the latest Ubuntu release, 6.10.  Kinda like how osx names thier releases tiger, or leopard.

basically gparted on the 6.10 (Edgy Eft) live disc will and should resize ntfs partitions.  The Gparted live disc, is a just a disc that lets you run gparted, which is a hard drive app, that will let you resize, delete, create partitions.

[gparted live disc](http://gparted.sourceforge.net/livecd.php)

---

### Post by itstabish on 2007-01-02
Thank you so much, you're so helpful :) Really appreciate it :) I downloaded the version of ubuntu onto my pc 2 days ago to be precise and burnt it as a bootable. so im guessing i have edgy, correct? I wonder why the partitioning didnt work ?

---

### Post by spockrock on 2007-01-02
umm....that I am not too sure why, however if you want try the gparted live disc, and see if that helps. I have used both the gparted live disc, and the live disc to resize an ntfs partition.

Btw nice laptop....

---

### Post by itstabish on 2007-01-02
Lol. Thanks. its got a core 2 duo, with 256 ati, 2gb ram, 120 i think is the hdd size cant rmr. god knows what else. :P okay ill try the partitioning again. BTW I have norton ghost for my windows restoring provided by dell i hope repartitioning doesnt mess it up! what do u think?

---

### Post by michaeljustman on 2007-01-02
I've never had problems with Partition Magic before, but thanks for the heads up.

I know that ndiswrapper isn't on the disk... I don't believe that's what I was saying.

I've never been able to resize my NTFS partitions with gparted... what am I doing wrong?

---

### Post by spockrock on 2007-01-02
> **itstabish said:**
> Lol. Thanks. its got a core 2 duo, with 256 ati, 2gb ram, 120 i think is the hdd size cant rmr. god knows what else. :P okay ill try the partitioning again. BTW I have norton ghost for my windows restoring provided by dell i hope repartitioning doesnt mess it up! what do u think?

I am sorry, that I cannot answer, it might it might not.  If the partitioning does not work, then try a third party app like, partition magic, or acronis.  I myself prefer acronis over partition magic, but I have had negative experiences with partition magic.

> **michaeljustman said:**
> I've never had problems with Partition Magic before, but thanks for the heads up.

I know that ndiswrapper isn't on the disk... I don't believe that's what I was saying.

I've never been able to resize my NTFS partitions with gparted... what am I doing wrong?

unfortunatly I am unsure how you went about doing this, I always manually setup my partitions, I am just kinda anal like that, and that way I an automated process doesnt destroy one of my many data partitions.

---

### Post by itstabish on 2007-01-02
Thanks alot mate, really appreciate it. You guys are AWESOME BEYOND THE BONE! Ubuntu :)

---

### Post by michaeljustman on 2007-01-02
Okay my bad... gparted does resize ntfs...

I'm the same... I partitioned before I installed anything on my HD, and the last time I had to change my NTFS partitions' size I used ntfsresize from the command line.

---

### Post by itstabish on 2007-01-02
Last question. How long will it take to repartition? I dont want to do it now if it'll take long cuz im sleepy/

---

### Post by michaeljustman on 2007-01-02
Depends on how big of a change your making to the disk, but I think if you're shrinking your windows partition it shouldn't take too long... just make sure you defrag it before you start. You'll save some time because it won't have to move so much from the end of the partition to the beginning... IMHO.

---

### Post by itstabish on 2007-01-02
thought so. thanks alot mate really appreciate it. i'll start tomorrow morning. Hopefully, will have everything running by tomorrow evening. Much appreciated :) love you guys! :)

---

### Post by itstabish on 2007-01-04
Okay, so something happened. I made an extra partition to install Ubuntu on. I don't know however, what I should set it as, i.e. should I set it as extended partition, logical partition, primary partition or what? And then after I'm done with that, it gives me 3 drop down menus and 3 boxes in front of them. I can't remmeber what they're about but they're something like sda1 sda2 or whatever. Please help me out.

---

### Post by itstabish on 2007-01-04
Oh, btw, now it shows 3 CD drives in windows and I dont even HAVE 3 CD drives. Its a laptop.

---

