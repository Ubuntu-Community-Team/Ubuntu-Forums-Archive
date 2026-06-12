---
title: "!! partition disk"
date: 2006-11-18
forum: Absolute Beginner Talk
---

### Post by Frugoo Scape on 2006-11-18
When i try to partition a hard disk it gives me an error. :evil: 
---
     [CENTER]Failed to create a file system [/CENTER]
The fat16 file system creation in partition #1 of Ide1 master (hda) failed.
    [CENTER]Go back         continue[/CENTER]
-----
I tryed all i think of but i still get this error. I have tryed all the posible formats for it. :-k 

Could you give me some help? :confused:

---

### Post by turbojugend_gr on 2006-11-18
Are you sure that this particular drive is not mounted?? WHat tools are you using to format that drive?

---

### Post by Frugoo Scape on 2006-11-18
i am using the one that is provided by the cd. And i think i have selected every monted option

---

### Post by turbojugend_gr on 2006-11-18
Do you mean you are trying to install ubuntu? And do you mean you are using the manual patitioning option?

If yes, you should not use fat partitions for "/" "/home" "/usr" "swap" etc. Ext3 filesystem is a nice choice. Fat32 should be used for windows-ubuntu share partitions (containg your multimedia files for instance.

PLZ be more accurate when asking for help so others can provide better help.

As soon as you make clear what the situation, you 'll see your problems solved, hopefully.

Best Regards, TJ.

---

