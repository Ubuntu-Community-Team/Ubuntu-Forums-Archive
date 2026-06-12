---
title: "Swap File"
date: 2008-04-02
forum: Absolute Beginner Talk
---

### Post by madmatrixz3000 on 2008-04-02
How do I setup my swap file back after I deleted it for space.  Now I want to make a 1.5Gb one.

---

### Post by bumanie on 2008-04-02
Either use gparted from within ubuntu or boot with the gparted live cd and use that.

---

### Post by stefangr1 on 2008-04-02
You first have to create a new swap partition, like the above poster described. To make the system use it, you subsequently have to edit your /etc/fstab .

Warning: I'm not sure if the system is going to boot if can't find the swap space after editing your fstab, so be careful!

---

### Post by ByteJuggler on 2008-04-02
It is also possible to swap to a file, like windows does, if you don't want to mess with creating a swap partition etc.

Do the following:

1.) Create a sufficiently large swap file, e.g. say (1536 * 1MB = 1.5GB approx):

```
sudo dd if=/dev/zero of=/swapfile bs=1MB count=1536
```

This basically says, "copy from /dev/zero to file /swapfile, using 1MB blocks, a count of 1536 blocks of data."  /dev/zero can be thought of as an infinitely large file containing zero's throughout.  The rsult of the above command is therefore a 1.5GB file called /swapfile containing all zero's.

2.) Make it into valid swapspace ("format" it, if you like):

```
sudo mkswap /swapfile
```

3.) Turn it on/make it active:

```
sudo swapon /swapfile
```

You can then see it's active by issuing the "free" command:

```
free
```

If you want to have it automatically activated at boot, then you'll also need to add an entry in the fstab file for this swap space.  Post back if you need help with that.

---

### Post by madmatrixz3000 on 2008-04-02
thx i found that somewhere else as well and already got the setup

---

