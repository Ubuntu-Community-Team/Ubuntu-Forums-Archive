---
title: "Stuck in the process of in download"
date: 2011-05-14
forum: Apple Hardware Users
---

### Post by STARRISON on 2011-05-14
First thing you should know is...I'm not that much of a nerd. I'm  probably the person most least familiar with code, terminal, commands, etc. in this  forum. I'm just someone who is really interested in Ubuntu and I am  stuck in the process of downloading it.

I am on Step 2: Burn your CD or create a USB drive
I am creating it as a USB stick and I am using a Mac to create it.
**I am stuck on Step 9:** Execute sudo dd if=/path/to/downloaded.img  of=/dev/rdiskN bs=1m (replace /path/to/downloaded.img with the path  where the image file is located; for example, ./ubuntu.img or  ./ubuntu.dmg).

No matter what I replace "/path/to/downloaded.img" this is what I'm face with:
[IMG]http://i1205.photobucket.com/albums/bb425/STARRISON/Picture2-1.png[/IMG]

I have dug through google to find what I'm doing wrong and I just can't find it. this is my last resort.

---

### Post by wojox on 2011-05-14
if = your in file. So what ever you have saved your ubuntu image as you need to read with the actual name. You also need to right directory.

Go into that directory you saved it and list the files. :P

---

### Post by Thewhistlingwind on 2011-05-14
I'm not very familiar with the mac file system, but maybe your not giving a full filepath? Where is the image currently?

---

### Post by STARRISON on 2011-05-14
> **wojox said:**
> if = your in file. So what ever you have saved your ubuntu image as you need to read with the actual name. You also need to right directory.

Go into that directory you saved it and list the files. :P

*Terminal-Oblivious 16 year old alert*
ok, the thing is... I'm not too sure what a directory is. would it be where the image/dmg is saved?

---

### Post by Thewhistlingwind on 2011-05-14
> **STARRISON said:**
> *Terminal-Oblivious 16 year old alert*
ok, the thing is... I'm not too sure what a directory is. would it be where the image/dmg is saved?

Directory = File

Example: /home/username/whatever_file_your_image_is_under/the_name of_the_image

---

### Post by STARRISON on 2011-05-14
> **Thewhistlingwind said:**
> Directory = File

Example: /home/username/whatever_file_your_image_is_under/the_name of_the_image

uhm..help me a little. but I still managed to get something wrong.
This is what I tried:
[IMG]http://i1205.photobucket.com/albums/bb425/STARRISON/Picture6.png[/IMG]

Because this what I did to try to guess what to put in:
[IMG]http://i1205.photobucket.com/albums/bb425/STARRISON/Picture7.png[/IMG]

---

### Post by Thewhistlingwind on 2011-05-14
Try moving it to a folder that isn't desktop? Also, be careful with dd, you can erase your disk with that.

---

### Post by STARRISON on 2011-05-14
> **Thewhistlingwind said:**
> Try moving it to a folder that isn't desktop? Also, be careful with dd, you can erase your disk with that.

I moved it to the downloads folder, but the same thing still happened.
I am not familiar with dd, its just that it was a part of the instructions Ubuntu had on their website.

---

### Post by Thewhistlingwind on 2011-05-14
> **STARRISON said:**
> I moved it to the downloads folder, but the same thing still happened.
I am not familiar with dd, its just that it was a part of the instructions Ubuntu had on their website.


My best guess would be a bad sector or something, try some of the options to keep going even if theres bad sectors/parts on the disk?

And yeah, if you mess up the if= and of= it'll erase your disk. Some people say that dd stands for "disk destroyer" because in the older days it was one of the easiest ways of losing your data.

---

### Post by STARRISON on 2011-05-14
> **Thewhistlingwind said:**
> My best guess would be a bad sector or something, try some of the options to keep going even if theres bad sectors/parts on the disk?

And yeah, if you mess up the if= and of= it'll erase your disk. Some people say that dd stands for "disk destroyer" because in the older days it was one of the easiest ways of losing your data.

ok, what exactly are these options/how to do them?

Alright, I'll make sure I have things right so dd doesn't screw up everything..

---

### Post by Thewhistlingwind on 2011-05-14
> **STARRISON said:**
> ok, what exactly are these options/how to do them?

Alright, I'll make sure I have things right so dd doesn't screw up everything..

I can paste from the man pages, but the mac has them too, right? man <Your command here> will help.

---

### Post by STARRISON on 2011-05-14
> **Thewhistlingwind said:**
> I can paste from the man pages, but the mac has them too, right? man <Your command here> will help.

ok, I put in 
man sudo dd if=/home/lindanuanlaoong/downloads/ubuntu.img.dmg of=/dev/diskN bs=1m

and this is what I got:
[IMG]http://i1205.photobucket.com/albums/bb425/STARRISON/Picture8.png[/IMG]
 But I'm not too sure what all that means, I'm not really at all familiar with Terminal, commands, etc. but I really want to learn...

---

### Post by Thewhistlingwind on 2011-05-14
Sudo and dd are different commands, you want to just put in man dd.

Anyway, read the page, it will have options you can give using a dash. Example; arp -a will give the computers on your network.

---

### Post by wojox on 2011-05-15
STARRISON I"m going to asked this be moved the apple forum for better assistance. As you can tell neither I nor Thewhistlingwind are proficient with mac's. :P

---

### Post by uRock on 2011-05-15
Moved to Apple User's.

Please do not post oversized images. You can upload your screenshots via the attachments too when creating your posts.

Regards,
uRock

---

