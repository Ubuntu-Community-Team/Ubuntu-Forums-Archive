---
title: "Forgot root password, authentication lock busy"
date: 2007-12-26
forum: Absolute Beginner Talk
---

### Post by ben22 on 2007-12-26
Hi,

I forgot my password. I did the following to recover:

- edited the Kernel line in the booting menu for the recovery mode. I added " single init=/bin/bash"
- rebooted
- I see "root@(none):/#" - I enter "passwd" - I get the msg "Authentication token lock busy"

How can I change the password?

How can I see all the users that exist on the system?

cheers,
Ben

---

### Post by overdrank on 2007-12-26
> **ben22 said:**
> Hi,

I forgot my password. I did the following to recover:

- edited the Kernel line in the booting menu for the recovery mode. I added " single init=/bin/bash"
- rebooted
- I see "root@(none):/#" - I enter "passwd" - I get the msg "Authentication token lock busy"

How can I change the password?

How can I see all the users that exist on the system?

cheers,
Ben

Maybe this will help
[https://help.ubuntu.com/community/LostPassword?highlight=%28password%29](https://help.ubuntu.com/community/LostPassword?highlight=%28password%29)

---

### Post by PmDematagoda on 2007-12-26
Sorry can you make your problem a bit clearer? Did you assign a password for the root account and forget it or did you forget the password to your own account?

---

### Post by ben22 on 2007-12-26
- I forgot my own password - I think the user was Ben

and I think I also assigned a password to root - which I forgot too

---

### Post by taurus on 2007-12-26
Just boot into recovery mode from GRUB menu and assign a new password for Ben.

```
passwd Ben
```
Remember, Unix/Linux is CaSe SenSiTive so Ben is not the same user as ben.

---

### Post by ben22 on 2007-12-26
what is GRUB - How do I get there?

---

### Post by ben22 on 2007-12-26
> **taurus said:**
> Just boot into recovery mode from GRUB menu and assign a new password for Ben.

```
passwd Ben
```
Remember, Unix/Linux is CaSe SenSiTive so Ben is not the same user as ben.

How do I get to GRUB?

How do I know the user is called Ben not ben benn or bennn? Where can I see existing users?

---

### Post by PmDematagoda on 2007-12-26
GRUB is the boot-loader for Linux, when you boot the PC you should see a list like this:-

```
Ubuntu 7.10

Ubuntu 7.10(Recovery Mode)

Memory Test
```

Select the Recovery Mode entry and press enter. If you do not see GRUB while booting, press Esc to bring it up.

To see the list of users, do:-

```
ls /home
```

But may I ask you something. How is it that you do you not know your own user name?

---

### Post by taurus on 2007-12-26
Do you see a menu about your kernel when you turn on your machine?  That's your GRUB menu.  There should be an option that says (recovery mode).  That's what you want to boot.  And if you are not sure what your username is, look at the output of this command after it boots into the recovery mode.

```
ls -la /home
```

---

### Post by ben22 on 2007-12-26
> **PmDematagoda said:**
> GRUB is the boot-loader for Linux, when you boot the PC you should see a list like this:-

```
Ubuntu 7.10

Ubuntu 7.10(Recovery Mode)

Memory Test
```

Select the Recovery Mode entry and press enter. If you do not see GRUB while booting, press Esc to bring it up.



I used GRUB then and tried "passwd Ben" it did not work **- I get "authentication lock busy"**

---

### Post by taurus on 2007-12-26
Highlight the recover mode option and wait for it to finish booting.  Then at the prompt, post the output of this command here.

```
ls -la /home
```

---

### Post by ben22 on 2007-12-26
According to your suggestion I started now in recovery mode (The Kernel had at the end "single" written).

When I come now to the command line it asks me: "Live root password for maintenance or type control -D to continue") - It seems I have to enter a root password.

BUT I DONT KNOW A ROOT PASSWORD

---

### Post by ben22 on 2007-12-26
Can NOBODY help!!!! I am desperate!!!

---

### Post by thenailedone on 2007-12-26
> **ben22 said:**
> Can NOBODY help!!!! I am desperate!!!

... I would have to think that GNU/Linux would never have been seen as "secure" if getting your hands on the root password was that easy...

Good luck but understand that your predicament sounds slightly fishy to say the very least...

---

### Post by Martje_001 on 2007-12-26
> **ben22 said:**
> According to your suggestion I started now in recovery mode (The Kernel had at the end "single" written).

When I come now to the command line it asks me: "Live root password for maintenance or type control -D to continue") - It seems I have to enter a root password.

BUT I DONT KNOW A ROOT PASSWORD
Press CTRL+D.

Otherwise: Boot up from a live-cd. Mount your harddisk. Chroot to it and reset your password.

---

### Post by ben22 on 2007-12-27
> **Martje_001 said:**
> Press CTRL+D.

Otherwise: Boot up from a live-cd. Mount your harddisk. Chroot to it and reset your password.

What do I exactly have to do? What does "mount" mean? I also have windows on my computer and don't want to delete the partition.

THANK YOU

Please post the exact steps.

---

### Post by Martje_001 on 2007-12-27
```
1. Boot up a live cd, or separate linux install.

2. Mount your hardy drive somewhere (replace **** with name of drive, e.g. hda1 or sda2 etc.)

[I]sudo mkdir /media/hardy
sudo mount /dev/**** /media/hardy
[/I]
3. chroot into your gutsy drive.

[I]sudo chroot /media/hardy su
[/I]

```
and then ***sudo passwd [user]***.

---

### Post by h3rt3q on 2008-01-16
or if u dont want to use live cd  u can just replace the **ro** to **rw** in the grub menu so it looks like this,

rw single init=/bin/bash

i have the same problem and this works for me.. =)

---

