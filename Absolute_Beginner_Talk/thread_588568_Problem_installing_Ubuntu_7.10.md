---
title: "Problem installing Ubuntu 7.10"
date: 2007-10-23
forum: Absolute Beginner Talk
---

### Post by Popple3 on 2007-10-23
So, I've got a Gutsy Live CD, verified it and all is good. Went to go install it but then I was stumped when I came to step 4 of the installer. I selected manual as I have already partitioned my hard drive for Ubuntu. This is the screen I get:

[IMG]http://i119.photobucket.com/albums/o142/Popple3/install.png[/IMG]

When I click forward, it comes up saying that I haven't defined a partition for the root, but there is no option to do this. Help..... Please...

---

### Post by stixguy on 2007-10-23
Click "Edit Partition". You'll see a drop dwon for mount point. Select "/" from that list.

HTH!

---

### Post by ItsMitsHere on 2007-10-23
i wonder where is your /dev/sda4?

never mind!!! when you created an ext3 partition a dialog box should have appeared in which you selected ext3 from a drop-down menu. in the same dialog box there is another drop-down menu just below the first one where you assign your mount point. select / in that menu and you should be ready to rock!!!

i hope this helps...

---

### Post by jspangler on 2007-10-23
Also make sure to click edit for your home partition and set that as /home, so that it doesn't put the home directory on your system partition.

It'smitshere: /dev/sda4 is probably an extended partition.

EDIT: I see now that you have no previous home partition!! So on that part, nevermind.

---

### Post by ItsMitsHere on 2007-10-23
> **jspangler said:**
> Also make sure to click edit for your home partition and set that as /home, so that it doesn't put the home directory on your system partition.

It'smitshere: /dev/sda4 is probably an extended partition.

thanx buddy! i'm linux nub, but with u guys helpin' around, i will be learning fast as a jet :) :) :)

---

### Post by Popple3 on 2007-10-23
Thanks! I cant believe I missed that. I guess I was just thrown off by the difference from 6.06 (the last version I used)

---

