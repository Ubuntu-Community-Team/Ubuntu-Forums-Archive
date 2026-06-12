---
title: "Formatting with Ubuntu?"
date: 2007-05-09
forum: Absolute Beginner Talk
---

### Post by PartyTaco on 2007-05-09
So I bought a new 160 gb hard drive. Its not formatted and I don't want to format it to windows since I have my other hard-drive setup with windows. Is there someway I can format it for linux? All I have is maxblast, which won't work with linux at all. I need some software or website telling me how. 

Thank you.

---

### Post by ubuntu27 on 2007-05-09
You mean you want to install Ubuntu Linux on your second hard drive? Yes, you can do that.

Here is a guide for you:

[http://www.psychocats.net/ubuntu/iso](http://www.psychocats.net/ubuntu/iso)

[http://www.psychocats.net/ubuntu/index.php](http://www.psychocats.net/ubuntu/index.php)

---

### Post by candtalan on 2007-05-09
there are several ways to do what you ask.
The method I like for myself is to use gparted which is available as a download iso which runs as a live cd.

see [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)

hth

later comment - ah! yes your post may be asking about install of ubuntu onto the spare hard drive - yes this
 is very easy when using the ubuntu ive CD.

---

### Post by Skrynesaver on 2007-05-09
Once you have the disk partitioned as you want it you can make an ext3 filesystem on any partition with mkfs.ext3
```

mkfs.ext3 /dev/hdb1

```

---

### Post by PartyTaco on 2007-05-09
Well, I was going to try and just use 80 gigs of it for ubuntu, but I was unable to figure out how to make it only partition(or format?) just 80 gigs. So I went ahead and am currently doing the whole hard drive.

---

