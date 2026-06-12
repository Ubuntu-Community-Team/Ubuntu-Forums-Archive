---
title: "messed up my permissions"
date: 2007-04-23
forum: Absolute Beginner Talk
---

### Post by SVWander on 2007-04-23
This morning I messed up my permissions trying to make my system more secure and in the process locked myself out of using sudo . . . I have been looking through Linux Pocket Guide and online to try to figure out how to fix this problem. The menu item in Administration to change users is of course no longer listed . . . in the terminal I get this message:

 tim is not in the sudoers file.  This incident will be reported.
tim@tim-desktop:~$ 

What command will clear up this very STUPID MISTAKE!!!?

I feel like such a dummy.

---

### Post by taurus on 2007-04-23
Did you play around with /etc/sudoers?  What exactly did you do because if I know a little more, maybe I can give you some solutions?

---

### Post by SVWander on 2007-04-23
> **taurus said:**
> Did you play around with /etc/sudoers?  What exactly did you do because if I know a little more, maybe I can give you some solutions?

I was trying add a user and went to System/Administration/Users and Group. I believe I added a user and changed the password. I know there must be away of recovering from this mess using commands in the terminal . . . but I getting nervous and confused . . . tim

---

### Post by lakersforce on 2007-04-23
Booting up in safemode gives you automatic root access and you should be able to correct the mistakes you made.

---

### Post by Najand on 2007-04-23
Use the live CD, open a terminal and then type:
```

sudo mkdir /media/directory
sudo mount -t ext3 <YOUR UBUNTU DEVICE> /media/directory

```
If you don't know the device name, use "sudo fdisk -l" command to find out.
Then
```

sudoedit /media/directory/etc/sudoers

```
See if you have the following line in it:
```

%admin ALL=(ALL) ALL

```
If you don't have it, add it to your file.
Then go to /media/directory/etc/group file:
```

sudoedit /media/directory/etc/group

```
and add your username at the end of line starts with admin.
For example if your username is "foo" it should be like:
```

admin:x:112:foo

```
Save it and reboot your computer.

---

### Post by SVWander on 2007-04-23
and add your username at the end of line starts with admin.
For example if your username is "foo" it should be like:
```

admin:x:112:foo

```
Save it and reboot your computer. [/QUOTE]

I followed your instructions and was able to do all the commands without any problem. But when I rebooted I still don't have the System/Administration/Users and Group menu item. The line before editing it read:
```

admin:x:4:tim, tim2    which I changed to: admin:x:112:tim  I deleted the tim2 

```

Since I didn't know what the 112 number referred to I went ahead and used it. Is that the problem now. I feel better about being able to correct this problem now. But I still have sooo much to learn.

tim

---

### Post by Najand on 2007-04-24
> **SVWander said:**
> and add your username at the end of line starts with admin.
For example if your username is "foo" it should be like:
```

admin:x:112:foo

```
Save it and reboot your computer. 

I followed your instructions and was able to do all the commands without any problem. But when I rebooted I still don't have the System/Administration/Users and Group menu item. The line before editing it read:
```

admin:x:4:tim, tim2    which I changed to: admin:x:112:tim  I deleted the tim2 

```

Since I didn't know what the 112 number referred to I went ahead and used it. Is that the problem now. I feel better about being able to correct this problem now. But I still have sooo much to learn.

tim

You should use you own value (group number):
```

admin:x:4:tim

```

---

### Post by SVWander on 2007-04-25
> **Najand said:**
> You should use you own value (group number):
```

admin:x:4:tim

```

Thanks guys! I was able to get control over my system again with your help. I still have lots to learn about the subject and about keeping my system secure. Tim

---

