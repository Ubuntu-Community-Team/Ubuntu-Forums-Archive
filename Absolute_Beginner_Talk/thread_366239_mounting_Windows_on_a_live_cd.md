---
title: "mounting Windows on a live cd"
date: 2007-02-20
forum: Absolute Beginner Talk
---

### Post by ForceUser on 2007-02-20
Hi I tried installing Ubuntu yesterday and was having problems so I went to start-up my computer into Windows and gave me a "0 active" error. I looked and my Windows partition in the installer and it says it's unmounted. I also tried mounting it but none of the code worked or anything. It's a ntfs filesystem and it says the name is /dev/sda2.

---

### Post by bodhi.zazen on 2007-02-20
```
sudo mount /dev/sda2 /mnt
```

---

### Post by ForceUser on 2007-02-20
> **bodhi.zazen said:**
> ```
sudo mount /dev/sda2 /mnt
```

I did that and added the ntfs part and it just gave me a list of commands for mounting, by the way I already did this [http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_mount.2Funmount_Windows_partitions_.28NTFS.29_manually.2C_and_allow_all_users_to_read_only]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_mount.2Funmount_Windows_partitions_.28NTFS.29_manually.2C_and_allow_all_users_to_read_only")
and it still says "0 active".

---

### Post by bodhi.zazen on 2007-02-20
Perhaps I am misunderstanding your question then ...

Are you asking how to mount your windows (ntfs) partition in Ubuntu ?

Or are you asking how to fix a problem you are having booting windows ?

"0 active" ~ is this an Ubuntu error message or a windows error message ?

---

### Post by ForceUser on 2007-02-20
> **bodhi.zazen said:**
> Perhaps I am misunderstanding your question then ...

Are you asking how to mount your windows (ntfs) partition in Ubuntu ?

Or are you asking how to fix a problem you are having booting windows ?

"0 active" ~ is this an Ubuntu error message or a windows error message ?

Well the problem is my Windows partition is unmounted so both questions. The "0 active" error is something I get when I start up my computer basically saying none of my drives are mounted.. Mainly the first question though.

---

### Post by bodhi.zazen on 2007-02-20
> **ForceUser said:**
> Well the problem is my Windows partition is unmounted so both questions.

So what exactly happens when, in a terminal, in Ubuntu, you type :

```
sudo mount /dev/sda2 /mnt
sudo ls -a /mnt
```

Error message ??

> The "0 active" error is something I get when I start up my computer basically saying none of my drives are mounted.

By "when I start up my computer" do you mean reboot ?

When do you get this error message ? before grub ? when boot Ubuntu ? when booting windows ??

---

### Post by ForceUser on 2007-02-20
> **bodhi.zazen said:**
> So what exactly happens when, in a terminal, in Ubuntu, you type :

```
sudo mount /dev/sda2 /mnt
sudo ls -a /mnt
```

Error message ??

[COLOR="Blue"]No it just lists a few programs I have in Windows and still says the partition is unmounted.  [/COLOR] 

By "when I start up my computer" do you mean reboot ?

[COLOR="Blue"] Yeah. [/COLOR] 

When do you get this error message ? before grub ? when boot Ubuntu ? when booting windows ??

 [COLOR="Blue"]I get it as soon as I reboot and it tries to boot into Windows. [/COLOR]

---

### Post by bodhi.zazen on 2007-02-20
If the command ```
sudo ls -a /mnt
``` lists programs, well it looks like the partition is mounted then.

Can you post the exact output from your terminal ?

==================================

Second, if you are having trouble booting windows, that is a different problem ...

I would start a new thread asking for help booting windows, be sure to post /boot/grub/menu.lst

---

### Post by ForceUser on 2007-02-20
> **bodhi.zazen said:**
> If the command ```
sudo ls -a /mnt
``` lists programs, well it looks like the partition is mounted then.

Can you post the exact output from your terminal ?

==================================

Second, if you are having trouble booting windows, that is a different problem ...

I would start a new thread asking for help booting windows, be sure to post /boot/grub/menu.lst

Well I got it working now for some reason, I guess I just didn't apply the action. Thanks for the help.

---

### Post by ForceUser on 2007-02-20
> **ForceUser said:**
> Well I got it working now for some reason, I guess I just didn't apply the action. Thanks for the help.

Wait nevermind I tried to boot into Windows and got the same error (0 active) and I went back into Linux and it says Windows isn't mounted even though I already mounted it..

---

### Post by bodhi.zazen on 2007-02-20
Well ...

First, it sounds as if you are having problems booting windows and I doubt a thread titled 

"mounting Windows on a live cd"

is going to get the attention / assistance you need.

================================

Second, yes if you reboot the live CD you need to remount your windows partition.

---

