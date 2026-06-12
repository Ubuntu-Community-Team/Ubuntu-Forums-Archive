---
title: "Dual Boot issue"
date: 2006-07-18
forum: Absolute Beginner Talk
---

### Post by InkyUK on 2006-07-18
Ok Hi i guess...

I am a total Ubuntu and Dual boot n00b!!!

I am trying to dual XP and Ubuntu 6.06 i have an 80GB hard disk and i have XP installed on a 30GB NTFS partition all went fine with that.

I have a SWAP partition 1472 MB (Double my RAM)

And then i have the rest as a ext3 partition for ubuntu. Looks like this [http://img160.imageshack.us/my.php?image=screenshotxb5.png](http://img160.imageshack.us/my.php?image=screenshotxb5.png)

i hear that i need to flag boot the Ubuntu partition how? :???: 

before posting this i tryd to install 3 times the Ubuntu partition but it stops at 76%% all the time!!!!! every time!!!! ](*,)  i try WHY does anyone no have i done something wrong? could it be as i havent flagged it wouldnt of thought so my self but maybe...

any suggestions would be greatly recived.

Thanks is advance all :)

InkyUK

---

### Post by starscalling on 2006-07-18
looks ok....
though personally i recommend setting 6-8 gigs for / and the extra for /home
[but thats neither here nor there]
do properties on that partition there /dev/hda3
make sure that its selected as primary partition
make sure that its selected as bootable

ubuntu should see the windows and offer to boot it as the isntall process finishes btw :)

---

### Post by InkyUK on 2006-07-18
[http://img144.imageshack.us/my.php?image=screenshot1bu5.png](http://img144.imageshack.us/my.php?image=screenshot1bu5.png)

thats what it looks like


where do i select it as bootable ? :???:  :???:

---

### Post by drosophyllum on 2006-07-18
I was a smart dual boot noob. I have a 80gig hd, when i started i simply made a 10 gig partition and left the rest as free space. hee hee! I instaled windows in the 10 gig partition and when the ubuntu installer got to the partitioning part I just clicked use free space under the delete entire hard drive option. Simple Instant Genius.

Hope I helped!!!!!

---

