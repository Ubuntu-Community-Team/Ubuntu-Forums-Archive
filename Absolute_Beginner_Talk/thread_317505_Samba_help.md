---
title: "Samba help"
date: 2006-12-12
forum: Absolute Beginner Talk
---

### Post by ducamie on 2006-12-12
Hi, I'm a complete noob at linux. I have a microsoft pc and a xubuntu pc on a network through a hub.

I've managed to get samba half working, I can dump files onto the linux machine from the xp machine, and I can mount the C drive of the xp machine on linux I can see the files, (upto a certain point) and then the folders appear empty even though they're not (I can get as far as 'documents and settings', then the user folders appear empty). Also when I restart the linux machine, the mount I had made disappears and I have to mount it again. Alls I really want to be able to do is listen to my music off the microsoft computer on the xubuntu machine.

Which rasies another problem, because once I manage to get the mount to stick, and the folders to not appear empty anymore, my folder I want to get to is private and passworded on the microsoft computer, so will I be able to get around this without removing the password? If not, its not a huge problem.

Thanks for reading.  :)

---

### Post by Cabldevil on 2006-12-12
have you added the mount command in fstab yet?  if not everytime you reboot you will have to mount from the command line again.

---

### Post by xabbott on 2006-12-12
*The Sharing option is not available for the Documents and Settings,  Program Files, and WINDOWS system folders. In addition, you  cannot share folders in other user's profiles.*

Taken from Windows XP Home help file.

---

### Post by ducamie on 2006-12-12
Cool, thanks.

So if i mount the right directory and add it to fstab that should work right.

So if i used smbmount //winbox/c /mnt/win

What command should I use? Would it be somthing like this? smbmount //winbox/c/documents and settings/oliver/mnt/win

I dont see that working lol, how would I do it correctly.

---

### Post by Cabldevil on 2006-12-12
[http://ubuntuforums.org/archive/index.php/t-7686.html]("http://ubuntuforums.org/archive/index.php/t-7686.html")

That should get you up to speed.  Odd but I share out my documents but that is on xp pro  with no issues

---

### Post by ducamie on 2006-12-12
Thankyou thankyou thankyouu :p 

im so happy, ive got the documents shared, the only thing im having troube is getting them to stick with fstab. im not sure what to put in..

what do i do if the command i used was:

sudo smbmount //home/christian /mnt/winstuff

also my screen keeps going black every half hour or so randomly for a split second. do you know what it might be?

---

### Post by ducamie on 2006-12-12
anyone? id love to wrap this up tonight. ive been struggling with it all day.

---

### Post by ducamie on 2006-12-12
anyone? after editing the fstab file and restarting 7 million times im getting rather agrivated with it.

---

### Post by ducamie on 2006-12-12
ohhhh

youre breaking my balls here

---

