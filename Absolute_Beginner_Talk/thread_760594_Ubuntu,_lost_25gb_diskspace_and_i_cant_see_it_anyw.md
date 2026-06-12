---
title: "Ubuntu, lost 25gb diskspace and i cant see it anywhere??"
date: 2008-04-20
forum: Absolute Beginner Talk
---

### Post by lozbritt on 2008-04-20
I have a 90gb diskdrive and on gparted it says i have 40gb free and 50 used, but when i view the whole file system in nautilus it tells me i have 11gb used and i don't no where the other 39 gb is?

Thanks in advance.

---

### Post by LaRoza on 2008-04-20
```

sudo fdisk -l

```

Run this command and give the results.

Nautilus is only able to give the size of the partition you are viewing.

---

### Post by Hieronymus on 2008-04-20
Or just install gparted, this way you can use the gui to do all your partition operations.

Jeroen

---

### Post by lozbritt on 2008-04-20
ive used gparted as i said above :) and this is the results from fdisk:


Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb8f0ffa4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       11787    94679046   83  Linux
/dev/sda2           11788       12161     3004155    5  Extended
/dev/sda5           11788       12161     3004123+  82  Linux swap / Solaris

I don't understand that though lol, thanks.

---

### Post by Hieronymus on 2008-04-20
What do you not understand? What do you need explained?

Jeroen

---

### Post by lozbritt on 2008-04-20
right i have the 3 partitions extended and the swap which take about 4 gbs all together. The other partition has the rest of my hard drive space, however when i view all my files through nautilus (which i am presuming is the main partition as there are only the 3) it says that i have 10gb taken up by the partition but when i look at the partition through gparted it shows that 50gbs has been taken. Therefore i have lost 40gb of space and it is not on the main partition as this shows it only has 11gbs on so i want to find the other 40gb...Thanks again.

---

### Post by Hieronymus on 2008-04-20
Ok, you have just 2 partitions at the moment:

Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       11787    94679046   83  Linux
/dev/sda2           11788       12161     3004155    5  Extended
/dev/sda5           11788       12161     3004123+  82  Linux swap / Solaris

sda1, this is the bootable dis, probably your /
sda5, this is your swap

the sda2 is just the logical disc on which the sda5 is connected, this is not a real disc.

Is this an answer to your question?

Jeroen

---

### Post by lozbritt on 2008-04-20
no, my '/' is supposed to be around 90gbs, which it is.

when i view all the files on '/' it shows that i have used 11gbs of the 90.

however it tells me i only have 40gbs free, when i surely should have 80gbs free?

therefore somewhere i have lost 40gbs of space and it isnt taken up in '/' so i dont no where that space has gone?

Do you understand what my problem is now (that i have lost 40gbs of space which is not taken up by my files)?

---

### Post by natirips on 2008-04-20
As you open Nautilus, look at the bottom of the window, it should say how much disk space you still have free (ready to use).

Edit: ignore this post.

---

### Post by Hieronymus on 2008-04-20
Yes, I do understand. This is strange. And when you open gparted you also can't find the lost space iow there is no unallocated space left to deal with?

Jeroen

---

### Post by lozbritt on 2008-04-20
Yes i know, it tells me i have 36.5 gbs free, but i should have 80gbs free because i have only used 11gbs on '/' and its not on any of the other partitions?

---

### Post by Hieronymus on 2008-04-20
Ok, so no unallocated space...strange. I'm afraid I can't help you out any further. I'm out of options

Sorry, 

Jeroen

---

### Post by lozbritt on 2008-04-20
Thanks anyway, anyone else?

---

### Post by Arwen on 2008-04-20
In my 7.04 there is an option in Applications->first option->Disk analyse or sth similar,you could try it and see if it shows anything helpful..

---

### Post by lozbritt on 2008-04-20
yeah that is what i used to view the drive and it shows 45gb used when i only have 11gb of my files, so the only other option i can think is that ubuntu installation took up 34gbs but obviously that's stupid :)

---

### Post by Arwen on 2008-04-20
I have faced similar problem in a friend's old pc which run XP, we checked the disk for errors 
and the program found too many bad sectors.I can't tell if it's your case(hope it's not) but I can't think sth to sort it out,sorry :-(
I hope you get an  answer - I'd like to know what could cause such a weird problem.

---

### Post by lozbritt on 2008-04-20
do you know any programs in ubuntu to look for bad sectors? thanks.

---

### Post by Arwen on 2008-04-20
Yep, [badblocks]("http://ubuntuforums.org/showthread.php?t=707029") but it won't repair anything..
You could wait for  while,maybe someone will come up with a solution.

---

### Post by 1scorpio on 2008-04-20
I don't know if this will help but it did for me . there is a good web page that explains some of what you are asking and more
check it out
http://www.psychocats.net/ubuntu/[/URL]


helpful post?
don't forget to thank posters  ___________>

---

### Post by volkswagner on 2008-04-20
testdisk may be of help.  Check out my tread, it helped me.  I may be of use to you, at least good to know.

[http://ubuntuforums.org/showthread.php?t=724156]("http://ubuntuforums.org/showthread.php?t=724156")

---

### Post by zvacet on 2008-04-20
@** lozbritt**

Is it possible that just Ubuntu partition was scaned ans in that case result is correct.Under places>computer do you see your windows as separate volume?

EDIT: It tell you how much space you used on that partition,so rest is unused(in the same partition).

---

### Post by lozbritt on 2008-04-20
hi, i don't have windows, i only run Ubuntu. In places -> computer, i see filesystem and my cd drive. 

However, this is strange, when i look at properties of the filesystem it tells me i have 56gb in use, but when i open the filesystem and select all the files and folders and look at the properties it tells me that it totals 10.5gb, so i dont know how the filesystem can total 50 when the files inside it only total 10...

Thanks for your help

---

### Post by zvacet on 2008-04-21
> I have a 90gb diskdrive and on gparted it says i have 40gb free and 50 used,

Does this mean that you leave 40GB as unallocated space?

> i dont know how the filesystem can total 50 when the files inside it only total 10...

Total 50GB mean that is size of your partition,and on that partition you have 10GB used space.

---

### Post by lozbritt on 2008-04-21
OK, first i mean it is telling me i have 40gb unallocated space but i should have 80gb allocated space so this is wrong. 

Secondly,the 50gb is not the size of the partition that is how much space i have allocated on my filesystem. I only have the one partition totalling around 90gb...

The problem is that ubuntu is telling me i have 50gb out of the 90gb as allocated space. But this is impossible! when i open the filesystem i am using 11gb as allocated space. So out of the 50gb that is supposed to be allocated i can only account for 11gb of it. So 39gb is being used somewhere and i dont no where it is to clear it??

---

### Post by WorldTripping on 2008-04-21
This is my only guess..

Have you emptied the 'Deleted Items' ?

Sorry can't be more use .

---

### Post by lozbritt on 2008-04-21
Yeah, i have done that. Thanks.

---

### Post by lozbritt on 2008-04-21
i will try and break this down.

If i go to places ---> computer, it shows me my cd drive and 'filesystem'.

If i right click 'filesystem' and go to properties it tells me its a 90gb partition. It also tells me i have 40gb free space and 50gb i have used.

but i am pretty sure i have not used 50gb of space! 

So, i open up 'filesystem', select all the files and folder (as root with hidden files on) and select the properties of everything on filesystem, however this totals only 10.3gb!! 

So i dont no how the filesystem has 50gb allocated space when the files and folder in the filesystem only come to 11gb of that space.

so where on earth is the other 39gb of space that i am supposed to be using...

Hope that makes it clearer.

---

### Post by WorldTripping on 2008-04-21
Looks like this might be a bug that's fixed in Hardy.

[https://bugs.launchpad.net/nautilus/+bug/8764]("https://bugs.launchpad.net/nautilus/+bug/8764")

---

### Post by lozbritt on 2008-04-21
I don't think so because it also tells me i am using 50gb in gparted as well. But i know for a fact that i don't have 50gb worth of files on my harddrive, i might just format and reinstall...

---

### Post by 3rdalbum on 2008-04-21
Maybe the "used space" is due to all the (actually non-existant) files in /proc? Do you have big files in /tmp?

Also, do you have any external volumes mounted? This can skew the readings.

---

