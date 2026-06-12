---
title: "Accessing My Hard Drive"
date: 2007-08-07
forum: Absolute Beginner Talk
---

### Post by rangerman007 on 2007-08-07
:confused:hi all
i have an acer laptop that  appears to have a software issue & will not load windows so i bought an external usb hard drive caddy with the hope of accessing via another pc but for some reason when i view the drive in "my computer" it shows both an E & F drive which are one of the same but i cannot access the E drive which is the larger partition & where all my files are,F access is no problem but only has what appear to be setup files,the E drive prompts me with the message "format drive now " yes/no ,i have looked at another drive via the external caddy & it is fine,i noticed that one drive is FAT32 & another is NTFS:confused: but the drive i am trying to get access to shows nothing,all i want is to save all my family pictures but cannot seem to find a way in...anyone help please

---

### Post by Inxsible on 2007-08-07
are you saying you are trying to access the drives thru an Ubuntu install or LiveCD or Windows or something else altogether?

---

### Post by annda on 2007-08-07
are you talking about accessing the drive in windows? if so, i can't help you...

if it's linux, plug in the drive and see if it pops up on your desktop. if it doesn't, what happens whaen you type this command in the terminal (applications>accessories):

```
sudo fdisk -l
```

that way we will see how to mount ("connect") the disk and copy the contents.

---

### Post by rangerman007 on 2007-08-07
i have windows XP installed....am i in the wrong arena for support?:popcorn:

---

### Post by annda on 2007-08-07
> **rangerman007 said:**
> i have windows XP installed....am i in the wrong arena for support?:popcorn:

hmm, yes. most of us ubuntu linux users have experience with windows but windows support is not what we do here.

if you use an [ubuntu live cd]("http://www.ubuntu.com/getubuntu/download") to rescue your files, i'm sure we can help.

---

### Post by jmnormand on 2007-08-07
this is not a windows forum but its a problem all systems run into.  since you can access the acer partition (the small fat32) it means your drive is physicaly alright.  there is likely something wrong with the file system on the main partition.

first thing to try is from windows go to start -> run and enter "chkdsk e: /f" (with out quotes)

if that doesnt fix it your best bet is to go to [www.grc.com](www.grc.com) and buy spinrite ($90).  not cheap but im guessing your data is worth more than that to you, and the program is worth it.  im just about certain this will fix your problem but if it doesnt you may be out of luck im afraid.

also if anyone has any free suggestions besides spinrite id like to try some out.

---

