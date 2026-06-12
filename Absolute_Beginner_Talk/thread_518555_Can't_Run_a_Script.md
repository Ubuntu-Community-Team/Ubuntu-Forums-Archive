---
title: "Can't Run a Script"
date: 2007-08-06
forum: Absolute Beginner Talk
---

### Post by BrokenBelief on 2007-08-06
I know I'm going to feel like such an idiot the moment I get the answer to this, but here goes.  I'm just trying to use a simple script to install Mupen64.  The code I'm trying to use is:

```
sudo sh <Location of script>
```

But, when I enter:

```
sudo sh /aaron/Desktop/Mupen64-Script-thegreenblob.sh
```

I just get:

```
sh: Can't open /aaron/Desktop/Mupen64-Script-thegreenblob.sh
```

I've tried all variations.  Wrapping the location in <> like the example, trying just /Mupen64-etc.  I don't understand what I'm doing wrong.  It seems like it should be so simple.

---

### Post by roncrump on 2007-08-06
> **BrokenBelief said:**
> 
```
sudo sh /aaron/Desktop/Mupen64-Script-thegreenblob.sh
```
.

Are you sure that is the right path to the shell script?

By default you would expect the user directory, aaron, to be within the /home partition such that:
```
sudo sh /home/aaron/Desktop/Mupen64-Script-thegreenblob.sh
```
should work.

This could be abbreviated to:
```
sudo sh ~/Desktop/Mupen64-Script-thegreenblob.sh
```

Your problem doesn't look like its permission related, but remember that the script has to be made executable too:
```
chmod +x ~/Desktop/Mupen64-Script-thegreenblob.sh
```
would make it executable by the owner of the script (see "man chmod" for more information).

Hope this helps.

Ron.

---

### Post by mevets on 2007-08-06
ron is right. To add on though, you should know that gnome-terminal and most other modern terminals support drag and drop. This would have inserted the correct path without you having to worry about it being correct. And also, you can mark the file as an executable through the GUI. Right click the file > Properties > Permissions > Checkbox next to execute.

---

### Post by BrokenBelief on 2007-08-06
> **mevets said:**
> ron is right. To add on though, you should know that gnome-terminal and most other modern terminals support drag and drop. This would have inserted the correct path without you having to worry about it being correct. And also, you can mark the file as an executable through the GUI. Right click the file > Properties > Permissions > Checkbox next to execute.

Yeah.  ron was right.  I don't know.  I inputed /home/aaron/Desktop/etc. and I thought everything was correct.  When I tried ~/Desktop/etc. it worked perfectly without a hitch.  But, considering that I now know about the drag and drop and the executable checkbox, something good came of this.  I understand a bit better, even if it is something trivial.

---

