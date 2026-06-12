---
title: "second internal hard drive install"
date: 2007-09-25
forum: Absolute Beginner Talk
---

### Post by jgrf77 on 2007-09-25
I am a relatively new user to ubuntu (running xubuntu) and have run out of space on my hard drive.  I have got a 2nd which i think i have wired in correctly but am now unsure what to do to be able to use it.

Any help will be greatly appreciated

thanks

jgrf77

---

### Post by odiseo77 on 2007-09-25
In order to see if the HD is properly installed, open a terminal an type:

```
sudo fdisk -l
```

This will output your current disk(s) and partitions (and the partitions' formats). Then all you have to do is to add the partition you want to use to /etc/fstab and make the mount point for it inside /media.

I think on Edgy you must add the partition's UUID in your /etc/fstab in order to use it, so, in a terminal type:

```
sudo vol_id -u /dev/YOUR_PARTITION_HERE
```

This will return the partition's UUID, then all you have to do is to edit your/etc/fstab and make an entry like this one:

```
UUID=YOUR_PARTITION'S_UUID_HERE /media/YOUR_PARTITION_MOUNT_POINT       ext3(or whatever partition type it is)       auto,utf8,umask=007,uid=your_user_name,gid=your_user_name 0       0
```

EDIT: Oh, I almost forget; you have to create the mount point for your partition:

***sudo mkdir /media/partition_name***

Then mount it:

***sudo mount /media/partition_name***

Greetings.

---

### Post by jgrf77 on 2007-10-02
Thank you very much for all that.  Afraid we´re going to have to slow it down a bit.  All this terminal stuff is greek to me.

here is what happened.

justin@Justinotronic:~$ sudo fdisk -l

Disk /dev/hda: 6448 MB, 6448619520 bytes
255 heads, 63 sectors/track, 784 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1         747     6000246   83  Linux
/dev/hda2             748         784      297202+   5  Extended
/dev/hda5             748         784      297171   82  Linux swap / Solaris

Disk /dev/hdd: 3400 MB, 3400040448 bytes
128 heads, 63 sectors/track, 823 cylinders
Units = cylinders of 8064 * 512 = 4128768 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1               1         823     3318304+  83  Linux
justin@Justinotronic:~$ 

er.....now what? :).................i took a stab in the dark and did

justin@Justinotronic:~$ sudo vol_id -u /dev/hda1
e27259bb-3123-4bb5-9977-c47bab38da33

and then in case i wanted the other one

/dev/hda2: unknown volume type
justin@Justinotronic:~$ 

Not sure which 1 of these two (hope it isn´t the second one because that unknown volume type doesn´t look too promising) i am to use for the next step and being scared of wiping everything i thought i better play it safe and ask for your wise advice. next step is.......?

thanks, justin

---

### Post by odiseo77 on 2007-10-02
Ok, the partition you want to add is /dev/hdd1, which is on your second HD (/dev/hdd). So, in order to get the partition's UUID, you must open a terminal and type:

```
sudo vol_id -u /dev/hdd1
```

When you have this partition's UUID, simply edit /etc/fstab and add it this way:

```
UUID=YOUR_PARTITION'S_UUID_HERE /media/hdd1   ext3  auto,utf8,umask=007,uid=your_user_name,gid=your_user_name 0       0
```

Then, make sure to create its mount point:

```
sudo mkdir /media/hdd1
```

And finally, mount it:

```
sudo mount /media/hdd1
```

Greetings, and hope this can be of help.

---

### Post by jgrf77 on 2007-10-04
ok thanks for that last post.

Not sure how to enter the appropriate details into the code.

Here´s what happened.

justin@Justinotronic:~$ sudo vol_id -u /dev/hdd1
e2cc0a2a-0459-4ffa-a39c-06f246e60d4a
justin@Justinotronic:~$ e2cc0a2a-0459-4ffa-a39c-06f246e60d4a/media/hdd1   ext3  auto,utf8,umask=007,justin,justin 0       0
bash: e2cc0a2a-0459-4ffa-a39c-06f246e60d4a/media/hdd1: No such file or directory
justin@Justinotronic:~$ 

my username is ´justin´ and  UUID is ´e2cc0a2a-0459-4ffa-a39c-06f246e60d4a´

Any chance you´d be able to put it all together for me so i can just copy and paste it into the terminal?

thanks a lot 

justin

---

### Post by ronald.higgins on 2007-10-04
:)

What you need to do is open up a terminal <click Applications->Accessories->Terminal>.

Now you need to edit a file called fstab that is located in /etc/ .
To do this first you need Super User permissions so we'll type "sudo" before the command.
We also need an editor to edit the file, in this case "gedit".

Put them all together now, in the terminal type:

sudo gedit /etc/fstab <hit enter>

At the bottom of the file copy in the line with the vol_id you got earlier and follow the rest of the instructions :)

---

