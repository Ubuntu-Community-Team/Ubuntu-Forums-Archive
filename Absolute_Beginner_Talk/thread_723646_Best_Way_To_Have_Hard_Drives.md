---
title: "Best Way To Have Hard Drives"
date: 2008-03-13
forum: Absolute Beginner Talk
---

### Post by Literati on 2008-03-13
Alright, so this is more of an ask for advice, and obviously, how to go about executing said advice.

I have two harddrives:

80GB
400GB

Ubuntu is installed on the 80GB, and I've JUST put in the 400GB drive. 
In my BIOS, I have them set up 80GB as Master, and 400GB as slave.

I want to know (I have hardly anything in home or whatnot, so feel free to tell me to move / delete ANYTHING, I'll do it) what the best way to set these two drives up is.

My 80GB is mounted, and my 400GB, when I go into Computer, is no where to be found. (I know it's hooked up, as the BIOS saw it) 

Where do I begin, what do you recommend :)
Thank you very much for the input!

---

### Post by taurus on 2008-03-13
Is there a partition with a filesystem on the second harddrive, 400GB?  Open a terminal and post the output of this command here.

Applications -> Accessories -> Terminal
```
sudo fdisk -**[COLOR="Blue"]l[/COLOR]**
```
That is a lower case letter L, not number 1.

---

### Post by Literati on 2008-03-13
sudo fdisk -l

Disk /dev/sda: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc7b5c7b5

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9777    78533721   83  Linux
/dev/sda2            9778        9964     1502077+   5  Extended
/dev/sda5            9778        9964     1502046   82  Linux swap / Solaris

Disk /dev/sdb: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/sdb doesn't contain a valid partition table

---

I tried running fdisk /dev/sdb
But no luck.

---

### Post by Literati on 2008-03-13
Anyone have any ideas?

---

### Post by gtrtx on 2008-03-13
did you do sudo  fdisk /dev/sdb ?

the key being sudo.....

---

### Post by Literati on 2008-03-13
I was able to get it using GParted.

Now, how do you guys suggest I set up the new partition? 
Should I leave any room before or after? 
What Filesystem should I format it as? 

Any suggestions would be appreciated :)

---

### Post by ruy_lopez on 2008-03-13
Format the drive as ext3. Since you have 400gb, you can leave room, in case you decide you need it for something else. If you don't need it, you can always expand later.

---

### Post by Literati on 2008-03-13
> **ruy_lopez said:**
> Format the drive as ext3. Since you have 400gb, you can leave room, in case you decide you need it for something else. If you don't need it, you can always expand later.

It really doesn't bother me if I have more than one partition, or leave room.
Ubuntu is the ONLY OS I'll be running on this computer.
I'll upgrade it to 8.04 when that gets released, but that's it.
There will be no Windows on this, no other distros. Nothing.

I think the main thing is.
I don't exactly understand what it MEANS to partition your harddrive.
I mean, how will a partition affect my files?
If I make this /home partition someday, what happens to my old home in the / folder?
I'm just not sure what it all means for me as a user.

---

### Post by ruy_lopez on 2008-03-13
> **Literati said:**
> If I make this /home partition someday, what happens to my old home in the / folder?
I'm just not sure what it all means for me as a user.

Is your home currently a partition? Show the output from "df -h".

If your /home is just a folder inside the root partition / (and not a partition in its own right) when you create the new /home you will copy everything. The old home is then emptied, and the /home folder becomes a mountpoint for the new /home partition. As a user, it'll be no different.

---

### Post by theRightNee on 2008-03-13
i think what you mean is will your home folder and/or files be affected by partitioning the harddrive? there answer (if you use gparted) is no, at least as far as i know. i've done it several times ( i have one HDD, very cheap =]) and i have not found any issues with making a partition on a harddrive already in use...hope this helps =]

---

### Post by Literati on 2008-03-13
> **ruy_lopez said:**
> Is your home currently a partition? Show the output from "df -h".

If your /home is just a folder inside the root partition / (and not a partition in its own right) when you create the new /home you will copy everything. The old home is then emptied, and the /home folder becomes a mountpoint for the new /home partition. As a user, it'll be no different.

No, it's certainly not.

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              74G  3.2G   67G   5% /
varrun                252M  204K  252M   1% /var/run
varlock               252M     0  252M   0% /var/lock
udev                  252M   84K  252M   1% /dev
devshm                252M   28K  252M   1% /dev/shm
lrm                   252M   34M  218M  14% /lib/modules/2.6.22-14-generic/volatile

---

### Post by ruy_lopez on 2008-03-13
Basically it's up to you what you do with the 400gb drive.

For starters, I'd partition the drive and mount it somewhere like /media/testmount, just to check it works okay.

---

### Post by Literati on 2008-03-13
> **ruy_lopez said:**
> Basically it's up to you what you do with the 400gb drive.

For starters, I'd partition the drive and mount it somewhere like /media/testmount, just to check it works okay.

Okay, I did that and called it Home (Just for familiarity)
But I can't seem to create folders in it?

---

### Post by ruy_lopez on 2008-03-13
> **Literati said:**
> Okay, I did that and called it Home (Just for familiarity)
But I can't seem to create folders in it?

Run "fdisk -l" again. Look for "/dev/sdbX" where X is a number.

Then create a mountpoint:
```

sudo mkdir /media/testmount

```

Mount the new drive (using the correct device from above):
```

sudo mount -t ext3 /dev/sdbX /media/testmount

```

Test the mount works by running "df -h". It should show "/dev/sdbX" on the same line as "/media/testmount". 

copy your /home to the partition.
```

sudo cp -rp /home/* /media/testmount/

```

umount the partition:
```

sudo umount /media/testmount

```

Mount again as /home
```

sudo mount -t ext3 /dev/sdbX /home

```

Log out and log back in again (don't reboot yet). Verify everything is normal. Run "df -h" and verify that "/dev/sdbX" is now on same line as "/home".

Once you are satisfied everything is okay, create an entry in /etc/fstab for the new /home. This is so /home mounts automatically in future.

```

/dev/sdbX       /home        ext3        defaults        2 2

```

---

### Post by Literati on 2008-03-13
That worked BEAUTIFULLY! 
To me, it doesn't feel like anything's changed at all, I mean, even the "places" button brings me to what is now "home" :) That was very painless. Thank you ver much!

I don't know if you'd be able to help me, but I do have two other questions.
If you can answer them, great, if not, that's okay, and thanks again! :)

First, My Network was wroking flawlessly just a few hours ago. And then after I logged out/reset, I'm completely unable to see any of the other networked computers on Ubuntu. My Windows computers can see (but not access) Ubuntu. What changed??

Secondly, I have Transmission startup when I open a new session (log in) but it opens in a weird position, so that the topbar (That I can grab and move) is UNDERNEATH the "Applications/Places/System" toolbar. Is there a way to either move this, or have it run itself without opening a window?

---

### Post by ruy_lopez on 2008-03-13
> **Literati said:**
> First, My Network was wroking flawlessly just a few hours ago. And then after I logged out/reset, I'm completely unable to see any of the other networked computers on Ubuntu. My Windows computers can see (but not access) Ubuntu. What changed??

Changing the /home shouldn't do anything to the network. In my experience, Places->Network is a little flaky.

I think I'll quit while ahead. Best of luck.

---

