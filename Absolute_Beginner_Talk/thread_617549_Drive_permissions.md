---
title: "Drive permissions"
date: 2007-11-19
forum: Absolute Beginner Talk
---

### Post by DarthNemesis on 2007-11-19
Hey all :D First post ;)

I installed ubuntu last night and tried to wok with my NTFS partitioned drive that has all my pics on it and junk. I couldn't delete any folders or files even being logged in as root. I couldnt chmod anything either

Is this something that I can overcome? The biggest problem will be me needing to add files later down the road. If I can't chmod the drive to allow me to write to the disk, I'm pretty much up the creek.

---

### Post by schorsch on 2007-11-19
First of all: Which version of Ubuntu is installed, Feisty (7.04) or Gutsy (7.10)?

---

### Post by DarthNemesis on 2007-11-19
> **schorsch said:**
> First of all: Which version of Ubuntu is installed, Feisty (7.04) or Gutsy (7.10)?

Thanks for the reply...I'm using 7.10

---

### Post by taurus on 2007-11-19
How do you mount that ntfs partition?  Do you mount it through /etc/fstab?

Can you post the outputs of these two commands here?

```
sudo fdisk -l
cat /etc/fstab
```

---

### Post by erginemr on 2007-11-20
> **DarthNemesis said:**
> Thanks for the reply...I'm using 7.10

Hello, 

Now that you are using Gutsy, there is a new config tool in Gutsy, under Applications Menu -> System Tools -> ntfs-config

Or you can sun it with Alt+F2 and then:
gksu ntfs-config

There you can enable writing to both your internal and external NTFS drives.

---

