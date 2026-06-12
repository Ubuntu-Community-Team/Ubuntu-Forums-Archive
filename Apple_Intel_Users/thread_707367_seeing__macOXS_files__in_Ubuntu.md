---
title: "seeing  macOXS files  in Ubuntu"
date: 2008-02-25
forum: Apple Intel Users
---

### Post by lex1 on 2008-02-25
The first thing to do is 

diskutil disableJournal volumeName

what is the next part mount? if so am i miounting the OSX partirtion?



lex1

---

### Post by cyberdork33 on 2008-02-25
> **lex1 said:**
> The first thing to do is 

diskutil disableJournal volumeName

what is the next part mount? if so am i miounting the OSX partirtion?
I've already posted this for you:
[http://gentoo-wiki.com/HOWTO_hfsplus](http://gentoo-wiki.com/HOWTO_hfsplus)

> This command will show a common way to mount both wrapped and unwrapped hfsplus partitions.  ```
mount -t hfsplus /dev/sda3 /mnt/ipod
```"Mount" literally means that you are placing a filesystem on a certain partition and "mounting" it (or attaching it) to a location in your directory tree. for instance, when you plug in a usb drive, it is "mounted" on a folder in /media. Then all the files on the usb drive are accessible inside that folder.

So you will need to mount your OS X partition somewhere. You can make a folder in your home folder if you want, and alter the above command as needed for your specific configuration:
```
mount -t hfsplus /dev/sdXY /path/to/folder
``` X and Y should be replaced with the appropriate letter and number for your partition, and "/path/to/folder" is the folder path where you want to mount it.

---

### Post by aletheianalex on 2008-02-25
I'll tell you the careless, non-technical method that somehow worked for me... i searched in Synaptic for everything that said HFS, Apple, macintosh, and Mac OS, searched through the descroptions for all relevant programs and  installed them.  When I rebooted, the disks showed up in my file manager.

---

### Post by lex1 on 2008-02-25
Thanks for your post cyberdork33 makes it clearer. Just a thought do you have issue this command every time you load ubuntu ? surely not?


aletheianalex: thanks for your post. Sounds like fun, you just must have hit on one lucky package.

lex1:popcorn:

---

### Post by cyberdork33 on 2008-02-25
> **lex1 said:**
> Thanks for your post cyberdork33 makes it clearer. Just a thought do you have issue this command every time you load ubuntu ? surely not?No, you can add an entry to the /etc/fstab to have it mount at bootup, but I wouldn't recommend that. Only mount it when you need to use it, and unmount it when you are done (with the umount command). Linux doesn't play all the nice with HFS+.

---

### Post by lex1 on 2008-02-27
I have been having difficulty following the fsplus complie

could i just do it from the linux sude with 

mkfs.hfsplus -v "iPod" /dev/sdXn?


lex1

---

### Post by cyberdork33 on 2008-02-27
> **lex1 said:**
> I have been having difficulty following the fsplus complie

could i just do it from the linux sude with 

mkfs.hfsplus -v "iPod" /dev/sdXn?

lex1
I have no idea what you are doing.

You should not need to use mkfs. That is what you use to create a filesystem on a partition... i.e. format it.

if you need to add a line to you fstab file:
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)

otherwise you just need to mount the partition. No compiling is needed.

---

### Post by lex1 on 2008-02-27
thanks for the post

I was getting mixmed up with HFSPLUs

you gave me the example in a esrlyer post thanks.

i will try to see what i can do.

just on a final note i can ssh into unbuntu no problems.

but not into OSX even though i have enabled remote login.( not at the same time you understand)

lex1

---

### Post by cyberdork33 on 2008-02-27
> **lex1 said:**
> but not into OSX even though i have enabled remote login.( not at the same time you understand)
If you don't specify a username, it tries to use the same name as the user logged into the client, and I think you have to use the OS X shortname. you can specify like this:
```
ssh osxusername@OSXIPAddress
```

---

### Post by lex1 on 2008-02-28
tahnks for your post

andyp@myipadress times out.

also regarding the triple boot when grubs comes up on ubuntu i cannot move the curser with the mouse. its been like that from the start i did mention it in a post before.

lex1

---

### Post by cyberdork33 on 2008-02-28
> **lex1 said:**
> andyp@myipadress times out.Then you are not using the correct IP, or you do not have ssh enabled on the machine. A timeout more likely indicates the latter. You are using your local IP address, (i.e. 192.168.x.x) not your Internet IP.

> **lex1 said:**
>  also regarding the triple boot when grubs comes up on ubuntu i cannot move the curser with the mouse. its been like that from the start i did mention it in a post before.Grub does not use a mouse, you have to use the keyboard.

---

### Post by lex1 on 2008-02-29
i am doing andyp@mydyanmicipaddress  and remote is enabled.

sorry i ment the keyboard not the mouse(secound part of question)


lex1:popcorn:

---

### Post by cyberdork33 on 2008-02-29
> **lex1 said:**
> i am doing andyp@mydyanmicipaddress  and remote is enabled.

sorry i ment the keyboard not the mouse(secound part of question)
Did you install opennssh-server?

The keyboard problems was fixed in Apple firmware updates that occurred awhile back... My iMac used to be like that too. Sometimes moving the keyboard to a different port will fix it too if you are still having the issue even with the firmware updates.

---

### Post by lex1 on 2008-03-03
no not on the imac but i will

sort of off toptic is it possible to use a usb to boot into into a imac say the usb has is bootable and has a rescue iso on it?

lex1:popcorn:

---

### Post by cyberdork33 on 2008-03-03
> **lex1 said:**
> sort of off toptic is it possible to use a usb to boot into into a imac say the usb has is bootable and has a rescue iso on it?Depends on what you are trying to boot. Mac tools seem to work fine, but linux on USB seems to have issues.

I saw you have iMac in your signature, so I assumed that is the hardware you were working with.

---

