---
title: "Issues with partitions"
date: 2007-12-11
forum: Absolute Beginner Talk
---

### Post by BigFoofieMan on 2007-12-11
Alright so when i boot to Ubuntu, it will sometimes automatically detect/show/let me access my windows partition (/dev/sda1/) but other times it wont let me to. Its random, because most times it will last for a long time.

Is there some way so i can have it always available?

---

### Post by taurus on 2007-12-11
Make sure you shutdown your windows cleanly before you boot into Ubuntu.  Hibernate your windows will cause problems mounting it under Ubuntu.  However, you can still mount it by hand using the force option.

---

### Post by BigFoofieMan on 2007-12-11
Yea Windows is completely shutdown unless my brother isnt doing it. I'll make sure to urge him to shut it down all the way if he isnt. 
Could you help me with the command because im new at this :-D

---

### Post by taurus on 2007-12-11
Yes, ask him to shut down windows cleanly if he is using it.

What partition is your windows?  If you're not sure, post the output of this command from a terminal.

Applications -> Accessories -> Terminal
```
sudo fdisk -l <-- That is a lower case letter l, not number 1.
```

---

### Post by BigFoofieMan on 2007-12-11
/dev/sda1

Thanks alot for your help btw!

---

### Post by taurus on 2007-12-11
Try this first.

```
sudo mkdir /media/sda1
sudo mount -t ntfs-3g /dev/sda1 /media/sda1
```
If there is an error message, post the whole thing here.

---

### Post by BigFoofieMan on 2007-12-11
sudo mkdir /media/sda1 
Gave me:
cannot create directory `/media/sda1': File exists

while
sudo mount -t ntfs-3g /dev/sda1 /media/sda1

Gave me:

Failed to mount '/dev/sda1': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sda1 /media/sda1 -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sda1 /media/sda1 ntfs-3g defaults,force 0 0




Im thinking its removable hardware thing or he didnt close it properly.

---

### Post by taurus on 2007-12-11
You have to use the **force** option to mount it for now until you boot into windows and shut it down cleanly.

```
sudo mount -t ntfs-3g /dev/sda1 /media/sda1 -o force
ls -la /media/sda1
```

---

### Post by BigFoofieMan on 2007-12-11
Do you think i should restart, boot windows first then cleanly close and then see if its working first?

Or is it not going to matter either way?

Okay, thanks alot. I saw your update and that answers my question.

It was nice of you to help me, i never knew this community was so helpful!

---

