---
title: "Is there an Ubuntu equivalent of Daemon Tools?"
date: 2007-07-04
forum: Absolute Beginner Talk
---

### Post by Eggnog on 2007-07-04
Or is there already a way to mount an ISO and I'm just too dense to know what that is?  Probably the latter.

---

### Post by lbelloq on 2007-07-04
IIRC it's something like:

sudo mount -t iso9660 /folder/image.iso /media/folder

---

### Post by overdrank on 2007-07-04
> **Eggnog said:**
> Or is there already a way to mount an ISO and I'm just too dense to know what that is?  Probably the latter.

HI maybe this link will help
[http://www.cucirca.com/2006/11/23/how-to-mountunmount-iso-images-without-burning-them/](http://www.cucirca.com/2006/11/23/how-to-mountunmount-iso-images-without-burning-them/)
Good luck!

---

### Post by nalinde on 2007-07-04
"Is there an Ubuntu equivalent of Daemon Tools?" - Oh yes there is...  :-D acually it's "built in" in GNU/Linux
There is alot of alternatives...
If you run Kubuntu i think there's a built in alternative in Konquer? so you just have to right click on th iso and mount it as a "drive".
I ubuntu there is one grafical alternative i'am awere of thats named Gmount-iso. But as it states in the program text "This is a frontend to the 'mount -o loop -t iso9660 foo.iso /mountpoint' command"
I also think there is a lot of nautilus scripts that will do this for you like in konquer. Have a look at [this page]("http://g-scripts.sourceforge.net/cat-filesysmgt.php").

But i guess the esiest way is to run the mount option in "CLI mode" run **man mount** to find ount more

---

### Post by lbelloq on 2007-07-04
Oooh, nice. I kinda like when a good app has a good GUI to use it.

---

### Post by trak87 on 2007-07-04
```
sudo mount yourcdimage.iso -r -t iso9660 -o loop /media/yourmountpoint
```

---

