---
title: "Image a HDD and transfer wirelessly"
date: 2008-03-05
forum: Absolute Beginner Talk
---

### Post by Ramzy on 2008-03-05
Howdy everyone,

Just recently i received a laptop (i'm a repair man / IT guy) from a user complaining that the system was running 'very slowly'.

Long story short, the user is running Vista, and has some how managed to severely screw everything up... And by screw everything i'm, i'm talking about notepad taking 45 seconds to open.

Now, we charge by the hour, and after discovering that it took Norton Ghost / Acronis True Image 3 hours to to barely even image a few MB's, we decided to stop.

A friend of mine suggested i try Ubuntu Live CD... And i must say, i'm extremely surprised at how it just 'works' (more so since it's running from a CD). And, all of the freezing issues are not apparent in Ubuntu.

Anyway, the user has requested that i back up his data, then format / re-install Vista. So i was wondering if anyone would be able to help me with my little issue (i've heard you guys have a great community).

I need to image parts of the users HDD, then transfer them wirelessly to my storage server.

Wireless is working just fine at the moment... So the only thing i need to do now is image parts of the users HD. (I've already mapped a network storage device)

Is this possible from the Live CD? Or must i partition and install Ubuntu?

Cheers.

---

### Post by guilly on 2008-03-05
I know there is a linux version of norton ghost out there... (the name escapes me right now) However, I would be a little conerned running a backup from a live cd. Remember everything you install from the live cd is loaded into memory. That's just my opinion though. To answer your question look for norton ghost on linux, you should be able to install it and run a back up I would think.

---

### Post by ruy_lopez on 2008-03-05
You should be able to use the LiveCD, assuming you can set up wireless.

Imaging process:

On the server
```

nc -l -p 9999 > image.dd

```

On the client, to initiate transfer
```

dd if=/dev/hdaX bs=1024 | nc <servaddr> <servport> -q 1

```

where X is the number of the partition you want to image (it might be /dev/sdaX). Experiment with different block sizes (bs=1024) to achieve optimal transfer speeds.

Once you have the image on the server, to mount an ntfs partition image and browse.
```

modprobe loop
losetup /dev/loop0 image.dd
mkdir /media/client_backup
mount -t ntfs -r /dev/loop0 /media/client_backup

```

"-r' mounts the image read-only, to protect the image from changing.

---

### Post by guilly on 2008-03-05
I may have read wrong but it doesn't seem like he wants to image an entire partition anymore. Only parts of it, MyDocuments,MyPictures etc...

---

### Post by ruy_lopez on 2008-03-05
> **guilly said:**
> I may have read wrong but it doesn't seem like he wants to image an entire partition anymore. Only parts of it, MyDocuments,MyPictures etc...

In that case, it's even easier:

Mount the client's drive in the LiveCD, browse to a directory you want to backup:

On the server:
```

mkdir backup
cd backup
nc -l -p 9999 | tar xv

```

On the livecd, inside the directory to backup
```

tar c * | nc -q 1 <servaddr> 9999

```

EDIT: If you want to create a tar.gz archive:

Server:
```

nc -l -p 9999 > backup.tar.gz

```

Client:
```

tar czv * | nc -q 1 <servaddr> 9999

```

---

