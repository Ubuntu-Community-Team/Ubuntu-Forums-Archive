---
title: "Grub loading problem/recent update, etc"
date: 2007-06-28
forum: Absolute Beginner Talk
---

### Post by unklelar on 2007-06-28
Ever since I did an update earlier today, my Ubuntu 6.06 won't load. I can't even get the live disk to work. All I get are a bunch of error messages I don't understand and a white screen with strange cryptics. There is also no internet connection. I've had Linux for 7 months without a lick of trouble, so I'm really caught off guard.

I don't mind a fresh installation, but my delimma is about 1200 songs I have downloaded for my mp3. Is there any way I can recoup these songs? Jeez what a mess. This is like a bad windows nightmare all over again.

Any suggestions most appreciated.

---

### Post by starcraft.man on 2007-06-28
Ok... I'm not sure what the problem is. No amount of updates to Ubuntu installed on your system though can affect how the Live CD boots. Assuming your booting to it properly from the BIOS, I assume its scratched or otherwise damaged, try on other computer and/or burn another copy. I don't know why the internet fails either....

[URL="http://ubuntuforums.org/showthread.php?t=224351&highlight=grub"]
Now, if its just a GRUB problem, here is how to reinstall GRUB from the Live CD (assuming you fix that).
[/URL]

If that fails, boot up into Live CD (again, I hope ya can fix that, there isn't any software issue that can stop you from booting it...) [Mount the partitions]("http://www.psychocats.net/ubuntu/mountlinux"), and copy them off to wherever you can.

---

### Post by unklelar on 2007-06-28
Thanks, Starcraft.man. I tried both your suggestions to no avail--it couldn't find any grub file. And I successfully went through your mounting the partitions suggestions. Only it told me my storage options were invalid. 

I was able to find another live disk which worked, but still no internet. And I don't know where my "unallocated" 57GB disk vanished to. Any other tips most welcome!

My head hurts real bad.

---

### Post by alienexplorers on 2007-06-28
If you can boot from a live CD boot it.  When it is running start Terminal.  In terminal type:
> sudo grub
Then enter the following code
> find /boot/grub/stage1
You will get an output like (hd#,#)
Then enter:
> root (hd#,#)
setup (hd#)
The # sign is indicative of you drive and partition.
In the last command "setup (hd#) only use the drive number.
Exit grub with quit.
reboot system

---

