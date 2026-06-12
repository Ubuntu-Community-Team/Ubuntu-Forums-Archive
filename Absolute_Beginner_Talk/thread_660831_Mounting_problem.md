---
title: "Mounting problem??"
date: 2008-01-07
forum: Absolute Beginner Talk
---

### Post by taekr on 2008-01-07
Hi, 

I have a problem. 

I have a external storage called 'Back up Storage'. 

I don't know when I start having this problem..  I assume it might be after I installed Gmount-iso (not sure.. just guess). 

Originally, I only had two things under /media. 
sda3
cdrom 

Hm.. not sure whether cdrom was cdrom1 or cdrom0 or just cdrom..  but I remeber I have a cdrom mounted in /media. 
sda3 is a partition of the laptop harddisk I made for downloading purpose. 

Anyways, when I connect my external harddisk to my laptop, 'Back up Storage' was mounted in /media. 

But I don't know since when..   Now I see 6 things are mounted under /media even though the external harddrive is not connected. 

They are :
Back up Storage
Back up Storage_
cdrom
cdrom0
cdrom1
sda3 


and when I attach my external harddisk, instead of being mounted as 'Back up Storage', it is mounted as 'Back up Storge__' 

I tried to unmount 'Back up Storage' by 'sudo umount "Back up Storage"..  but it's no use. 

what is going on??  I know cdrom0 and cdrom1 are for Gonome-ISO. But what's wrong with the other two?? How can I delete them and have everything back to where it was?

---

### Post by hyper_ch on 2008-01-07
If it's mounted as 
```

Back up Storge__

```

Then you'll have to umount it as such:

```

sudo umount '/media/Back up Storge__'

```

---

### Post by taekr on 2008-01-07
What about 'Back up Storage' and 'Back up Storage_'


When I do 

```

sudo umount '/media/Back up Storage_' 

```

It says it is not mounted.. therefore can't unmount it. 

Can I delete them - 'Back up Storage' and 'Back up Storage_'????.  

I know I can unmount 'Back up Storage__' because it is for the external harddisk.

What I want is to get rid of 'Back up Storage' and 'Back up Storage_' from /media

---

### Post by hyper_ch on 2008-01-07
Well, if it says it's not mounted, then it's not mounted I tend to think.

I still fail to see the problem.

---

### Post by vanadium on 2008-01-07
I think you are having an issue with the fact that the volume name of your external drive contains spaces. Ubuntu automatically uses the volume label, if available, to name the mount point for an external drive. This is very convenient as it allows you to have your drive always mounted with the same and descriptive name. You should probably rename your volume label such that it does not contain spaces. I would go for "Back_up_Storage" instead of "Back up Storage".

How you change the volume label of a drive is dependent on the file system. This help page [https://help.ubuntu.com/community/RenameUSBDrive](https://help.ubuntu.com/community/RenameUSBDrive) explains how it is done.

---

### Post by taekr on 2008-01-07
> **hyper_ch said:**
> Well, if it says it's not mounted, then it's not mounted I tend to think.

I still fail to see the problem.

The problem is that 'Back up Storage' and 'Back up Storage_' shouldn't be in /media.. (when external harddisk is not attached). 

when the harddisk is attached, then i have another one --> 'Back up Storage__' 

thus ending up having 

1. 'Back up Storage'
2. 'Back up Storage_'
3. 'Back up storage__'

I'd like to get rid of number 1 and 2. That's all..

---

### Post by taekr on 2008-01-07
> **vanadium said:**
> I think you are having an issue with the fact that the volume name of your external drive contains spaces. Ubuntu automatically uses the volume label, if available, to name the mount point for an external drive. This is very convenient as it allows you to have your drive always mounted with the same and descriptive name. You should probably rename your volume label such that it does not contain spaces. I would go for "Back_up_Storage" instead of "Back up Storage".

How you change the volume label of a drive is dependent on the file system. This help page [https://help.ubuntu.com/community/RenameUSBDrive](https://help.ubuntu.com/community/RenameUSBDrive) explains how it is done.

Thank you a lot.  I will rename it without a space. But can I get rid of #1 and #2?

---

### Post by hyper_ch on 2008-01-07
why don't you remove those then?

---

### Post by hyper_ch on 2008-01-07
```

sudo rmdir '/media/Back up Storage'

```
and
```

sudo rmdir '/media/Back up Storage_'

```

rmdir will only remove folders that are empty - just to be sure.

---

### Post by taekr on 2008-01-07
> **hyper_ch said:**
> ```

sudo rmdir '/media/Back up Storage'

```
and
```

sudo rmdir '/media/Back up Storage_'

```

rmdir will only remove folders that are empty - just to be sure.

Wow...!!  ^ ^ 

it was a so simple problem. I did it and worked. 

Well, I have been using ubuntu only for about 1 month.  i'm learning a lot.

I never thought it is a folder. I thought it was a device or something. 

Anyways thanks a lot. I'm learning a lot.

---

### Post by hyper_ch on 2008-01-07
Devices are normally in /dev

also

```

ls -al

```
should tell yu whether it's a file or directory or something else :)

Life would be boring if we knew everything already ;)

---

