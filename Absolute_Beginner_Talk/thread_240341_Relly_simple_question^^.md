---
title: "Relly simple question^^"
date: 2006-08-20
forum: Absolute Beginner Talk
---

### Post by Charkel on 2006-08-20
Ok so in the terminal. 
cd yourdirectory/ <- Go forward to the directory.
But how do i go back one step or if i wanna navigate to another hdd? Please help. I have access to my regular windows drive so i wanna access some programs with wine from the terminal. So i have to navigate to my 'c:\ drive'

---

### Post by taurus on 2006-08-20
If you want to move one directory up, then do

```
cd ..
```

---

### Post by Charkel on 2006-08-20
Thx man. And with my supersmart brain i manage to figure out that if you go back as far as possible and the write cd media/ and then cd /hda1 i can access my 'c:\ drive'. Yay me ^^
And thx again

---

### Post by anaconda on 2006-08-20
Yep..
Or you coud just write

cd /media/whatever

And it would go to /media/whatever no matter where you were before moving there

---

### Post by MaximB on 2006-08-20
well...I'm sure you already know the "ls" command
it's like "dir" in DOS
in linux we use 2key commands most of the time ;)

---

### Post by Charkel on 2006-08-20
> **MAXDDARK said:**
> well...I'm sure you already know the "ls" command
it's like "dir" in DOS
in linux we use 2key commands most of the time ;)
Yeh i knew that ^^

---

### Post by Haegin on 2006-08-20
There are two ways for you to specify a directory from the terminal:

1. The absolute path method
You start at the root of the file-system and follow the directory down so for example to get to the "Desktop" folder within your home folder you would use:
```

/home/<username>/Desktop (where <username> is your username)

```
and to get to /media/usbdisk you just use:
```

/media/usbdisk

```

2. The relative path method
You specify the directory relative to the directory you are currently in so (assuming you are in your home folder which is default when you open the terminal) to get to "Desktop" you just use
```

Desktop

``` (notice there is no slash at the beginning)
and to get to /media/usbdisk you use:
```

../../media/usbdisk

```

As you can see the relative method is sometimes quicker and sometimes a lot slower but regardless of which method you use tab completion can really speed things up. Just try typing ```
/home/<username>/Des
``` and then press tab and watch in wonder as it fills in the rest of the folder name. If it doesn't work (because you have two folders beginning with "Des" then press tab again to list all the different possible folders beginning with "Des".

Isn't the terminal wonderful!

---

### Post by baylorbear on 2006-08-20
A site that REALLY helped me get started:
[http://www.linuxcommand.org/](http://www.linuxcommand.org/)

---

