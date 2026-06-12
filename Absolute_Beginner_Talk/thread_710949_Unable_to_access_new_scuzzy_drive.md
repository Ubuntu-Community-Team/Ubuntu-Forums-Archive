---
title: "Unable to access new scuzzy drive?"
date: 2008-02-29
forum: Absolute Beginner Talk
---

### Post by peaceforall on 2008-02-29
Hello,  I added a second drive and here is my fdisk -l readout.  Can you help me figure out how do access this drive?  I'm a little burnt toast with Linux today.  After lots of checking also could not find and easy way to share hardrives on two seperate linux boxes. Lots of command line mumbo jumbo.  



Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x82168216

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       37824   303821248+  83  Linux
/dev/sda2           37825       38913     8747392+   5  Extended
/dev/sda5           37825       38913     8747361   82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/sdb doesn't contain a valid partition table

---

### Post by talsemgeest on 2008-02-29
First you need to format the hard drive.

Go to add/remove programs and install gnome partition editor.

Then go to system>administration>partition editor.
Select your NEW hard drive and click format. Choose whatever format you want (I suggest ext3) and go ahead.

After a reboot your harddrive should be mounted under the /media/ directory.

Hope this helps :)

---

### Post by peaceforall on 2008-02-29
Thanks for the tip. It's formatted, however I can't see it?,

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x82168216

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       37824   303821248+  83  Linux
/dev/sda2           37825       38913     8747392+   5  Extended
/dev/sda5           37825       38913     8747361   82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0002650e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60801   488384001    5  Extended

How can I see it in pcman file manager?

---

### Post by taurus on 2008-02-29
You only created an extended partition on it.  I suggest you fire up gparted again.  Then delete that extended partition and everything else on it and create a primary partition as /dev/sdb1.  Now, you should format that /dev/sdb1 to whatever filesystem you want to use.

---

### Post by mister_pink on 2008-02-29
You probably need to add it to your fstab to get it mounted automatically. To manually mount:
```
cd /media
sudo mkdir whatever
sudo mount /dev/sdb1 whatever
```
To add it to your fstab
```
sudo cp /etc/fstab /etc/fstab.bak
gksudo gedit /etc/fstab
```
Then add something like this to the file:
```
/dev/sdb1 /media/whatever    ext3    defaults 0       1
```
Obviously replace "whatever" with what you want to call the drive, like "data".

Edit: Yeah, do what ^ he said first! Didn't actually read that properly. An extended partition is for sort of containing other partitions, as drives cant have more than 4 primary ones.

---

### Post by peaceforall on 2008-02-29
Ok. Deleted, formatted as ext3, computer would not boot, blank screen, unplugged 500gig, restarted compluter, deleted again, formated as linux primary and here is what it says:

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x82168216

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       37824   303821248+  83  Linux
/dev/sda2           37825       38913     8747392+   5  Extended
/dev/sda5           37825       38913     8747361   82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0002650e

Still not showing up in pcman file manager?

---

### Post by taurus on 2008-02-29
Okay, why don't you do that from a terminal then.

```
sudo cfdisk /dev/sdb
```
You will see a list of commands and one of them is **n** for new partition.  Hit n and then choose primary and 1--/dev/sdb1.  Now, you need to make sure it is Linux partition by pressing t and then number 83.  82 is swap so don't pick that.  Save the change and exit with w.

Now, if you run this command again,

```
sudo fdisk -l
```
you would see /dev/sdb1 as a Linux partition and you need to format it to ext3 before you can use it.

```
sudo mke2fs -j /dev/sdb1
```

---

### Post by peaceforall on 2008-02-29
Here's what I get when I type in cfdisk.  Not seeing an "n" anywhere?  



cfdisk (util-linux-ng 2.13)

                              Disk Drive: /dev/sdb
                       Size: 500107862016 bytes, 500.1 GB
             Heads: 255   Sectors per Track: 63   Cylinders: 60801

    Name        Flags      Part Type  FS Type          [Label]        Size (MB)
 ------------------------------------------------------------------------------
    sdb1                    Primary   Linux swap / Solaris            500105.25 











     [Bootable]  [ Delete ]  [  Help  ]  [Maximize]  [ Print  ]
     [  Quit  ]  [  Type  ]  [ Units  ]  [ Write  ]

                 Toggle bootable flag of the current partition

---

### Post by taurus on 2008-02-29
> **peaceforall said:**
> Here's what I get when I type in cfdisk.  Not seeing an "n" anywhere?  



cfdisk (util-linux-ng 2.13)

                              Disk Drive: /dev/sdb
                       Size: 500107862016 bytes, 500.1 GB
             Heads: 255   Sectors per Track: 63   Cylinders: 60801

    Name        Flags      Part Type  FS Type          [Label]        Size (MB)
 ------------------------------------------------------------------------------
    sdb1                    Primary   Linux swap / Solaris            500105.25 











     [Bootable]  [ Delete ]  [  Help  ]  [Maximize]  [ Print  ]
     [  Quit  ]  [  Type  ]  [ Units  ]  [ Write  ]

                 Toggle bootable flag of the current partition

Okay, go into Type and change it from Linux swap to Linux filesystem, 83.  Write it and get out.  Then, format it to ext3.

---

### Post by peaceforall on 2008-02-29
Can do. What is and where is Type?

---

### Post by taurus on 2008-02-29
> **peaceforall said:**
> Here's what I get when I type in cfdisk.  Not seeing an "n" anywhere?  



cfdisk (util-linux-ng 2.13)

                              Disk Drive: /dev/sdb
                       Size: 500107862016 bytes, 500.1 GB
             Heads: 255   Sectors per Track: 63   Cylinders: 60801

    Name        Flags      Part Type  FS Type          [Label]        Size (MB)
 ------------------------------------------------------------------------------
    sdb1                    Primary   Linux swap / Solaris            500105.25 











     [Bootable]  [ Delete ]  [  Help  ]  [Maximize]  [ Print  ]
     [  Quit  ]  [  **[COLOR="Blue"][SIZE="4"]Type[/SIZE][/COLOR]**  ]  [ Units  ]  [ Write  ]

                 Toggle bootable flag of the current partition

Hit the Tab key to highlight the menu at the bottom.  Then, use the arrow keys to navigate around.

---

### Post by peaceforall on 2008-02-29
Found "Type" and doing as you instructed. I'll let you know how it goes.  Thank you.

---

### Post by peaceforall on 2008-02-29
Did as you instructed, rebooted, and here is what fdisk says:

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x82168216

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       37824   303821248+  83  Linux
/dev/sda2           37825       38913     8747392+   5  Extended
/dev/sda5           37825       38913     8747361   82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0002650e

Still not able to see this new drive in pcman file manager?

---

### Post by talsemgeest on 2008-03-01
You still need to add it to your fstab file for it to mount

---

### Post by mister_pink on 2008-03-01
It still doesnt seem to be formatted correctly. This should be pretty easy to do in gparted, I cant think whats going wrong at all? Is that really all you get from fdisk -l? When you've got it right there should be a line that reads something like "/dev/sdb1 number number 32 linux" or something similar. Try gparted again, it should be quite self explanitary. 

You should just have to select it in the drop down menu on the right, right click it and delete anything thats already there, then right click, select new, change ext2 to ext3 and the other defaults should be fine. Click Add then apply.

---

### Post by peaceforall on 2008-03-01
Mr. Pink.  Thank you.  Now we are getting somewhere.... almost done.  Sdb1 now shows up in my file manager.  When I attempt to mount it I get an error message that says unable to mount.  Here is my fdisk printout:

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x82168216

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       37824   303821248+  83  Linux
/dev/sda2           37825       38913     8747392+   5  Extended
/dev/sda5           37825       38913     8747361   82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0002650e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60801   488384001   83  Linux

---

### Post by taurus on 2008-03-01
What about

```
sudo mkdir /media/sdb1
sudo mount -t ext3 /dev/sdb1 /media/sdb1
df -h
```

---

### Post by peaceforall on 2008-03-01
Getting even closer. Here is my readout:

df -h

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             286G   35G  237G  13% /
varrun                1.5G  216K  1.5G   1% /var/run
varlock               1.5G     0  1.5G   0% /var/lock
udev                  1.5G   92K  1.5G   1% /dev
devshm                1.5G     0  1.5G   0% /dev/shm
lrm                   1.5G   34M  1.4G   3% /lib/modules/2.6.22-14-generic/volatile
/dev/sdb1             459G  199M  435G   1% /media/sdb1

It looks like I can get onto the drive now via pcman.  When I attempt to create a new file I get an error code that says: "The file cannot be created"?

---

### Post by taurus on 2008-03-01
You need to change the ownership of /media/sdb1 from root to your login name so you can write to it without using sudo/gksudo.

_Assuming_ your login name is **peace**, run

```
sudo chown -R **peace**:**peace** /media/sdb1
ls -la /media
```

---

### Post by peaceforall on 2008-03-01
Did as you said and now I'm getting "unable to mount" error when I attempt to mount 500gig drive?

Here your readout:

ls -la /media
total 20
drwxr-xr-x  5 root root 4096 2008-03-01 10:53 .
drwxr-xr-x 21 root root 4096 2008-02-24 18:59 ..
lrwxrwxrwx  1 root root    6 2008-02-24 18:50 cdrom -> cdrom0
drwxr-xr-x  2 root root 4096 2008-02-24 18:50 cdrom0
lrwxrwxrwx  1 root root    7 2008-02-24 18:50 floppy -> floppy0
drwxr-xr-x  2 root root 4096 2008-02-24 18:50 floppy0
-rw-r--r--  1 root root    0 2008-03-01 10:53 .hal-mtab
drwxr-xr-x  2 root root 4096 2008-03-01 09:47 sdb1

---

### Post by taurus on 2008-03-01
Okay, let's try this again.

Post the output of this command.

```
df -h
```
If you see /dev/sdb1 mounted to /media/sdb1 from the list, then run

```
sudo chown -R **peace**:**peace** /media/sdb1
```
_Assuming_ **peace** is your login name.  So, you need to replace **peace** from the command above with your _actual login name_.

Then post

```
ls -la /media
```

---

### Post by peaceforall on 2008-03-01
Here the text from df -h: 

/dev/sda1             286G   41G  231G  15% /
varrun                1.5G  220K  1.5G   1% /var/run
varlock               1.5G     0  1.5G   0% /var/lock
udev                  1.5G  104K  1.5G   1% /dev
devshm                1.5G     0  1.5G   0% /dev/shm
lrm                   1.5G   34M  1.4G   3% /lib/modules/2.6.22-14-generic/volatile


The new drive is no longer mounted.  The only way I know how to mount it is via pcman file manager.

---

### Post by taurus on 2008-03-01
What's wrong with mounting from a terminal or you can add an entry in /etc/fstab so it will be mounted automatically each time you boot?

```
sudo mount -t ext3 /dev/sdb1 /media/sdb1
df -h
```

---

### Post by peaceforall on 2008-03-01
Joe, Thank you!  It works now.... Nothing wrong with terminal, I like it, didn't know what lingo to use in terminal. Now I know.  I'll have to send you some of our Oregon kiwis, peaches or oranges. Thanks again.

---

### Post by peaceforall on 2008-03-01
Lastly.  This is my second time using the forum.  How do I show we completed and solved this mystery?

---

