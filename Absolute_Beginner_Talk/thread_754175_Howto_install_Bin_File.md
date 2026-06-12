---
title: "Howto install Bin File?"
date: 2008-04-13
forum: Absolute Beginner Talk
---

### Post by discman37 on 2008-04-13
Trying to install Google Earth on Ubuntu 7.10. This is in a Bin file. How do i install the Google Earth Bin file. Beginner here. Thanks!!!

---

### Post by Souls-hunteR on 2008-04-13
Make the file executable, then run it. To make file executable, use:
```

chmod +x file_name

```

---

### Post by ibutho on 2008-04-13
The following should work from a terminal
```
chmod +x somefile.bin
./somefile.bin

```
The first command makes the bin file executable and the second runs it.

---

### Post by cotcot on 2008-04-13
Try [[COLOR="Red"]this[/COLOR]]("http://tombuntu.com/index.php/2007/11/28/how-to-install-google-earth-in-ubuntu/")

---

### Post by rfruth on 2008-04-13
sh <bin file> just like the docs say [http://earth.google.com/support/bin/answer.py?hl=en&answer=44713](http://earth.google.com/support/bin/answer.py?hl=en&answer=44713)
((no need for chmod))

---

### Post by diablo75 on 2008-04-13
All you need to do to install Google earth is download the bin, open a terminal, and type

```
sh ./GoogleEarthLinux.bin
```

or whatever the filename is.  I think that's right.

The rest of the chmod stuff above...I've never had to do to install Google Earth...

Cheers!

---

### Post by discman37 on 2008-04-13
I've opened a terminal and input your answer and got this:chmod: cannot access `somefile.bin': No such file or directory

My guess is i have to change Directory.. I have downloaded the Earth file to my descktop. Can someone help?

---

### Post by lswest on 2008-04-13
do this:
```
sh ~/Desktop/GoogleEarthLinux.bin
``` and it should work.

---

### Post by ibutho on 2008-04-13
> **discman37 said:**
> I've opened a terminal and input your answer and got this:chmod: cannot access `somefile.bin': No such file or directory

My guess is i have to change Directory.. I have downloaded the Earth file to my descktop. Can someone help?

somefile.bin has to be changed to the actual filename which is GoogleEarthLinux.bin.

---

### Post by sisco311 on 2008-04-13
Right click on the file and select Open With Other Application and type sh in the Use a custom command box.
or
type:
```
sh 
```
in the terminal(it's a space after sh) and drag and drop the bin file in the terminal
o'h and press Return(Enter)

---

### Post by diablo75 on 2008-04-13
Todays terminal command is "cd" and "ls"

cd  means "Change Directory" if I'm not mistaken, and ls means list.

When you first open a terminal window, you are actually sitting in your home folder.  Type ls and hit enter, and you'll see all the files and folder in your Home folder.

You'll notice that one directory/folder shown is your Desktop.  Change directories by typing:

cd Desktop

It's case sensitive too.  All linux terminal commands are.

Now that you're in your desktop, you should be able to type in the command in my previous post, and be on your way.

---

### Post by discman37 on 2008-04-22
> **lswest said:**
> do this:
```
sh ~/Desktop/GoogleEarthLinux.bin
``` and it should work.

Thanks for helping me!!!

---

