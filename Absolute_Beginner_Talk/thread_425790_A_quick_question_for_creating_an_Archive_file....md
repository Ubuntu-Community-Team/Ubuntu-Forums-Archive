---
title: "A quick question for creating an Archive file..."
date: 2007-04-27
forum: Absolute Beginner Talk
---

### Post by crimesaucer on 2007-04-27
Hello, I tried to create an archive like this:

```
tar cvf Milk.tar Theme_xfce-milk
```

I was hoping to have it as a folder with another folder in it, and another folder in that one, like this:

/xfce-milk/Xfce-milk/gtk-2.0

When I made the Milk.tar it had all of the files and images, but I lost my directory folders like the gtk-2.0 and the Xfce-milk folder

I know I did something wrong since this is my first time compressing, so can someone tell me the correct command and options.

Thanks.


EDIT- also, do I need to have any permission settings if I am archiving a gtk-2.0 theme to be uploaded onto xfce-look.org?

---

### Post by uchuunoyanushi on 2007-04-28
If you own the file you're tarring, you should have the permissions you need to tar it.

```
man tar
```

gives you a list of options and instructions on using the file.

If Theme_xfce-milk is a directory, you need to put a / before it, like:

```
tar -cvf Milk.tar /Theme_xfce-milk 
```

Just make sure you are in the directory one level up from the directory you want to tar.  Additionally, you might want to add the -z or -j option to gzip or bzip the file.  If you do, edit the file name to .tar.gz or .tar.bz2 respectively.

---

### Post by Najand on 2007-04-28
> **uchuunoyanushi said:**
> If you own the file you're tarring, you should have the permissions you need to tar it.

```
man tar
```

gives you a list of options and instructions on using the file.

If Theme_xfce-milk is a directory, you need to put a / before it, like:

```
tar -cvf Milk.tar /Theme_xfce-milk 
```

Just make sure you are in the directory one level up from the directory you want to tar.  Additionally, you might want to add the -z or -j option to gzip or bzip the file.  If you do, edit the file name to .tar.gz or .tar.bz2 respectively.

Well, I believe that this command does not work at all:
[COLOR="Red"]```
[COLOR="Red"]tar -cvf Milk.tar /Theme_xfce-milk[/COLOR] 
```[/COLOR]
Well, it is clear that the directory /Theme_xfce-milk does not exist.... "/Theme_xfce-milk" means a directory on the root filesystem and it is not for sure one level up from the directory you want to tar. 
Maybe you wanna say something like: 
[COLOR="Blue"]```
[COLOR="Blue"]tar -cvf Milk.tar ./Theme_xfce-milk[/COLOR] 
```[/COLOR]

---

### Post by uchuunoyanushi on 2007-04-28
> **Najand said:**
> Maybe you wanna say something like: 
```
tar -cvf Milk.tar ./Theme_xfce-milk 
```

Yes.  Sorry, that's what I meant.

---

### Post by crimesaucer on 2007-04-28
Thanks, I'll try that.

---

### Post by crimesaucer on 2007-04-28
It worked perfectly when I extracted it with full path, thanks.

This is what I archived and uploaded:

[http://www.xfce-look.org/content/show.php?content=57138](http://www.xfce-look.org/content/show.php?content=57138)

---

