---
title: "help me partition my harddrive! omg extreme n00bz00r! O.O"
date: 2008-02-15
forum: Absolute Beginner Talk
---

### Post by Countra on 2008-02-15
omg heeelp! i must create a partition to be able to install linux. But i cant! O.O
yes, im pretty much a noob i would say- but anyways, i used GParted and it didnt work(the field is empty and i dont get many options) and yeah.. Sux to be me. lol
nah, sux to be a noob! (which i am i would say)
my system is 32-bit, linux ubuntu feisty fawn(i think.. :P) :confused:
heeeeeelp!!!!!! **OMG HELPZOOOR!!!**

---

### Post by jimbob on 2008-02-15
How did you run Gparted - do you have the stand-alone CD?

---

### Post by fiestytom on 2008-02-15
if you have the live cd, use that and under the administrative settings go to "gparted"

i'm a n00b too, don't worry

---

### Post by Countra on 2008-02-16
ok, i admit it- my opening post was a little to "not-so-serious"> i mean, i didnt even explain the situation completely. So now im gonna! :P
> 
How did you run Gparted - do you have the stand-alone CD?
I have a Live CD> and GParted is in the adminstration options in "System"(its named Partitition Editor and when you open it, after a long time of "scanning all drives..." it becomes open for work. But there are no options for creating a new partition to install this OS on. omg)

---

### Post by forestpixie on 2008-02-16
I've had a few oddities with the livecd gparted - try getting the gparted [livecd]("http://gparted-livecd.tuxfamily.org/") - download it, burn it as an iso and then you can boot with it

---

### Post by Countra on 2008-02-17
huh? I allready have GParted, it came boundled as a software with ubuntu. what i want to do is to create a partition where i can install ubuntu from the live cd.
but i can not. when GParted has "scanned all drivers..." completely, then afterwards, the is no option to create a *new* partition.(btw, why do i have to create one anyways? why doesent ubuntu let me install the OS directly on the hardrive without partitate it? :S)

---

### Post by aashay on 2008-02-17
Assuming you have free space on the drive right click it and select new. Make a ext3 partition here. If you dont have free space, delete, resize, move other partitions around to make space

---

### Post by maniac_X on 2008-02-17
> **Countra said:**
> when GParted has "scanned all drivers..." completely, then afterwards, the is no option to create a *new* partition. When you are in the Partition Editor, click on the representation of the partiton and it will then show options in the pull down menu...or you could also right click on the partition representation. You will know you have chosen the partition because a dotted line will then highlight around the partition you picked.

> 
(btw, why do i have to create one anyways? why doesent ubuntu let me install the OS directly on the hardrive without partitate it? :S)
 Tha partition is WHERE it is installed. If you don't make room for it, then ther is no place to install it :) It's like you want a piece of pie but you didn't bring your plate to get it :lolflag:

You could of course run it from the CD but that would be silly because it runs sooo much better by actually installing it to the drive :)

Free up some empty space on your drive by shrinking the Windows partiton. Give it at least 15GB if you are just checking things out right now. Then when you install, **choose CAREFULLY** from the install options!! There should be one to use empty space. Double check because this is the area where lotsa newbies accidently install using the whole harddrive option and you do not want todo that if you still want to keep Windows for now.

---

### Post by Bartender on 2008-02-17
Countra -
When someone expends the effort to offer advice, take it.  Like forestpixie said, the stand-alone partitioner is a better tool than the one included on the installCD.  There are a couple of reasons for this but just trust us, OK?
If you want to take a screenshot of your existing partitions, it's much easier to do that with the installer CD.  Just plug in a thumb drive, check at the desktop to make sure it's recognized, then go back to the partitioner, click on Applications>Accessories>Take Screenshot and save it to your thumbdrive.  Then post back with a picture.
But if you want to actually do some partitioning, it's best to use the stand-alone CD.
[http://gparted-livecd.tuxfamily.org/](http://gparted-livecd.tuxfamily.org/)

As to your question about why doesn't Ubuntu let you install without partitioning, well, that's just how it is.  #1, you can't put two operating systems in the same space, and #2 Windows NTFS file system and Linux ext3 file system certainly aren't going to share the same space.

Even if you auto-install Linux, it's still making different partitions for itself.  

Do you have an old PC or an old HDD you can play with?  Things will go much smoother if you practice a little bit with a system that doesn't matter.  

Also google "partitioning with GParted" or similar - there are various tutorials that will give you an idea of how to go about it.

---

### Post by maniac_X on 2008-02-17
I also agree with Bartender and others here, the GParted Live CD is better to use. I always use that when I mess around with my partitions. It's also a bit faster than the Ubuntu Live CD in loading up.

---

