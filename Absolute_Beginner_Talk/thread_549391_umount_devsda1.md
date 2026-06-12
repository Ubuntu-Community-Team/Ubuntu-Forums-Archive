---
title: "umount /dev/sda1"
date: 2007-09-12
forum: Absolute Beginner Talk
---

### Post by tech9 on 2007-09-12
I am having a hard time backing up my system - due to not being able to unmount sda1...

I was reading some other posts. It warns against setting partitions as SCSI. When I first setup ubuntu, I took the defaults SCSI.

Should I have not setup the partition this way?

Is there a way to change it to hda1 for IDE?

Even trying to creating an image with clonezilla... I got errors telling me that the drive is mounted and cannot be backed up.

Please advise,

Thanks,

T9

---

### Post by bwhitaker on 2007-09-12
Do you know what is on /dev/sda1, or more specifically what it's mounted as?

```

$ mount

```

---

### Post by psusi on 2007-09-12
Assuming that is your root partition; you can't silly, you are using it.  

You will have to boot from some other disk/partition ( maybe the livecd? )

---

### Post by tech9 on 2007-09-12
> **psusi said:**
> Assuming that is your root partition; you can't silly, you are using it.  

You will have to boot from some other disk/partition ( maybe the livecd? )

I realize that this is the root partition, but shouldn't I be able to back everything up with clonezilla (bootable CD)?

---

### Post by bwhitaker on 2007-09-12
How are you doing the clonezilla setup? 

We use clonezilla at work, on a drbl server.  To use it we pxe boot into it over the network.  I know that It can work other ways but it needs exclusive access to your partition or drive.

---

### Post by tech9 on 2007-09-12
> **bwhitaker said:**
> Do you know what is on /dev/sda1, or more specifically what it's mounted as?

```

$ mount

```


yes, its my linux system partition

thanks, for the response BTW

---

### Post by tech9 on 2007-09-12
> **bwhitaker said:**
> How are you doing the clonezilla setup? 

We use clonezilla at work, on a drbl server.  To use it we pxe boot into it over the network.  I know that It can work other ways but it needs exclusive access to your partition or drive.

I am just trying to setup a samba share to write to which keeps failing, and I even tried creating the image directly to the local drive, but I guess it's mounted so that didn't work

---

### Post by psusi on 2007-09-12
Why not just use rsync to copy all your files over the network?

---

### Post by tech9 on 2007-09-12
> **bwhitaker said:**
> Do you know what is on /dev/sda1, or more specifically what it's mounted as?

```

$ mount

```

wrong user, sorry...

---

### Post by bwhitaker on 2007-09-12
You do have clonezilla in the correct mode, right?


When you're booted into the clonezilla livecd can you get to a shell and maybe unmount the drive?

---

### Post by bwhitaker on 2007-09-12
> **psusi said:**
> Why not just use rsync to copy all your files over the network?

Yeah, I would suggest doing this instead of using a disk imaging utility like clonezilla.

---

### Post by tech9 on 2007-09-12
> **psusi said:**
> Assuming that is your root partition; you can't silly, you are using it.  

You will have to boot from some other disk/partition ( maybe the livecd? )

Also, tried the PE environment with clonezilla...silly:)

---

### Post by tech9 on 2007-09-12
> **psusi said:**
> Why not just use rsync to copy all your files over the network?

I am not familiar with rsync. I know it's installed. Is this a command I need to run, or is there a GUI interface.

Thanks!

T9

---

### Post by tech9 on 2007-09-12
nevermind... I looked it up - Thanks for the tips!

---

