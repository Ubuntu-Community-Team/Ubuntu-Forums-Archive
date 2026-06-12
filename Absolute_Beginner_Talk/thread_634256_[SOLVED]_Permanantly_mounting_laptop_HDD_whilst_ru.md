---
title: "[SOLVED] Permanantly mounting laptop HDD whilst running Gutsy from USB HDD"
date: 2007-12-07
forum: Absolute Beginner Talk
---

### Post by Jeztastic on 2007-12-07
Hi,

my internal laptop partitions seem to be mounting badly. I'm a total n00b, so not sure if this is usual. They are present, however, they do not reappear as icons on the desktop until I use them for something else. This also means my desktop wallpaper does not re-appear. Is this usual? Is there a workaround? 

I'm aware I can do without desktop icons, and import the desktop jpg into my ubuntu drive, but... You know, it's not right...

Thanks,

Jez

---

### Post by Crashmaxx on 2007-12-07
First of all, it sounds like you have a rather odd setup. How are you mounting these drives now?

Second, could you post the results of this command:
```

sudo fdisk -l

```

and this one:
```

cat /etc/fstab

```

Those output what physical drives you have and how you have them mounted. Thanks.

---

### Post by Jeztastic on 2007-12-07
Hi, it's late and I'm not running Ubuntu right now so I can't run the commands. I have a laptop with a 120 gb hard drive, in two partitions for Vista. I then have gutsy on a 40 gb hard drive which is connected by USB.

I just clicked 'mount' on the the drives in Gutsy's file system to mount them. Is there more to it than that? I assume they are mounted as I now have the option to 'unmount' when I right click them.

---

