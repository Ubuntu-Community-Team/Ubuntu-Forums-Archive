---
title: "Can't access new disk drive"
date: 2006-09-04
forum: Absolute Beginner Talk
---

### Post by rc-edens on 2006-09-04
I added a second disk drive to my Ubuntu 6.06 box, but after searching for hours have not discovered how to do what I thought should be simple: Make Ubuntu see this new drive so that I can make some directories on it. 

This drive is /dev/hdc1 and is formatted as ext3. It shows up as an icon under "Computer" in the file manager, but I can't do anything with it.

Can someone help me with how to access it?

Thanks,
RC

---

### Post by Iarwain ben-adar on 2006-09-04
Hi,
what do you mean "shows up, but can't do anything with it" ?

Does it give you any error or something like that?


Iarwain

---

### Post by rc-edens on 2006-09-04
When I double-click its icon, a message pops up saying: **Unable to mount the selected volume.** An under the Show more details arrow it says: **error: device /dev/hdc1 is not removable.** and **error: could not execute pmount.**

---

### Post by taurus on 2006-09-04
You need to mount it first before you can use it.  Open a terminal, Applications -> Accessories -> Terminal, and do

```

sudo mkdir /media/harddrive
sudo mount -t ext3 /dev/hdc1 /media/harddrive
df -h

```

---

### Post by rc-edens on 2006-09-04
> sudo mkdir /media/harddrive
sudo mount -t ext3 /dev/hdc1 /media/harddrive
df -h

Thank you, Taurus, that worked perfectly!

---RC

---

### Post by taurus on 2006-09-04
And if you want to mount it automatically upon boot, then you need to edit /etc/fstab and add an entry for it...

```
gksudo gedit /etc/fstab
```
Now, add this line to the end of it.

```

/dev/hdc1   /media/harddrive   ext3   defaults   0   2

```

---

### Post by DrMilo on 2006-09-05
> **taurus said:**
> And if you want to mount it automatically upon boot, then you need to edit /etc/fstab and add an entry for it...

```
gksudo gedit /etc/fstab
```
Now, add this line to the end of it.

```


/dev/hdc1   /media/harddrive   ext3   defaults   0   2

```

I have had the identical problem and your instructions have got me further than anything else but doing what you suggest doesn't enable read/write permissions. Do you have any advice for that?

---

