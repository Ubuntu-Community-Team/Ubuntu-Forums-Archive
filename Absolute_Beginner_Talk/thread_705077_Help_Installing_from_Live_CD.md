---
title: "Help Installing from Live CD"
date: 2008-02-23
forum: Absolute Beginner Talk
---

### Post by bmfgeorgin2 on 2008-02-23
hey can I ask one question?

people tell me to make the partition 10gb (min) to 20 gb. I was gonna make mine like 18. But the smalled it goes for me is 42 gb.
[B]
At 48% (the smallest it goes) its at 42gb. I also do not know how to do it manuelly
[/B]
This is a pic of the step im on.




[IMG]http://apcmag.com/system/files/images/xp_ubuntu_07.preview.jpg[/IMG]


Thats not my actual pic but thats just the step. How Do I make that 18 gb?

---

### Post by bmfgeorgin2 on 2008-02-23
anyone? i need help

---

### Post by dcstar on 2008-02-23
> **bmfgeorgin2 said:**
> anyone? i need help

Abort the installation and use the Partition Manager tool in the Live CD to make any changes before you start the installation.

---

### Post by mikewhatever on 2008-02-23
It says 'the new partition size (5.8 GB), a lot smaller then 42.

---

### Post by bmfgeorgin2 on 2008-02-23
read the note

---

### Post by bmfgeorgin2 on 2008-02-23
> **dcstar said:**
> Abort the installation and use the Partition Manager tool in the Live CD to make any changes before you start the installation.

where is the manager found on the live cd ?

sory 4 bad typin im on my psp rite nao

---

### Post by Yoke &amp; Chung on 2008-02-23
You slide the bar to indicate the size you want. I would actually suggest you partition your hard disk first using the LiveCD, and after that then install Ubuntu. 

Select "System" --> "Adminstration" --> "Partition Editior". 

You can resize your partition here, and during installation when you reach the same screen again, select "use the largest continuous free space" option.

Good luck!

---

### Post by bmfgeorgin2 on 2008-02-23
Ok thanks.

Ill try it when my bro stops playing runescape >_>

(Im not putting solved yet because I havent tried it yet)

---

### Post by bmfgeorgin2 on 2008-02-23
I just want to install ubuntu dual-booting to xp.

Can someone show me how to use the partition editor under System/Administration?

Its confusing I want:

     Swap: 1gb
    /boot: 200mb
    /partition: 18gb


But I donot find these options under the editor. Please Help

---

### Post by neurostu on 2008-02-23
I haven't used the Partition manager on the Ubuntu Live CD. But I have used GParted (I think they are very similar). 
-What you need to do is select your XP partition (its NTFS) and then resize it. Shrink it down so that there is about 20gb of free space. 

-Then create a new partition format it in ext3 and set that to 19gb, set the mount point of that partition to "/"

-Finally create another partition of size "1gb" and format it as swap.  You really don't need to create a boot partition. The ubuntu install cd will take care of the boot issues for you.

So in the end you will have 3 partitions, 1 - XP (formated NTFS) 2 - Ubuntu (formated ext3) 3 - Swap (formatted swap).

Hope this helps!

ps. If you are thinking about writing files in Ubuntu that are going to be read in XP I would recommend a 4th patition (formatted NTFS) of a couple gigabytes. XP can sometimes freak out if the partition where the system files are contained is written to by linux so the 4th partition will prevent this. Also XP does not have the drivers to read an ext3 formatted partition so it won't be able to access your ubuntu files.

 A lot of people do this, some people don't, it isn't required but it might be worth setting up if you are wanting to transfer files from ubuntu to XP.

---

### Post by neurostu on 2008-02-23
If you can't figure out how to do this with the Ubuntu Live cd. Download the GParted live cd and use that. It might take some time to figure it out, but it is pretty easy to use and should be that difficult for you to figure out.

---

