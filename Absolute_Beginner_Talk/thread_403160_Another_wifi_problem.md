---
title: "Another wifi problem"
date: 2007-04-06
forum: Absolute Beginner Talk
---

### Post by awiggin on 2007-04-06
Hello,

I am trying to follow the directions from the ubuntu documentations page to fix my wifi problem.

When it says:

user@ubuntu:~$ sudo apt-get install linux-headers-`uname -r`  
user@ubuntu:~$ sudo ln -s /usr/src/linux-headers-`uname -r` /lib/modules/`uname -r`/build

What am I supposed to type when it says 'uname -r' ?  

I am a total newbie and I am pulling my hair out on this wireless thing.  I have a disk that has the Linux drivers for my Gigafast USB wifi adapter 748-CUI, (the zd1211 drivers).  BUt I have no idea how to unzip, untar or unpack that box from the disk and install it onto my computer.

Thanks in advance!

-Lance

---

### Post by jpkotta on 2007-04-06
You're supposed to type exactly that, verbatim.  The grave accents '`' will cause whatever text is inside them to be run as a command, then the output of the command replaces the grave accents and the command.  

```
echo `uname -r`
```
is equivalent to 
```
echo 2.6.15-27-686
```
on my machine.  uname gives information about the kernel.

To unzip, use the unzip command:
```
unzip file.zip
```
To untar, use the tar command:
```
tar zxvf file.tar.gz
```
```
tar jxvf file.tar.bz2
```
You can also use the GUI archive manager from the file manager.

---

### Post by awiggin on 2007-04-07
To untar, use the tar command:
```
tar zxvf file.tar.gz
```
```
tar jxvf file.tar.bz2
```
You can also use the GUI archive manager from the file manager.[/QUOTE]

I have been able to untar a driver found online and now it is saved in the following directory:

/lib/firmware/zd1211

But all I did was untar the package and copy it into that location.  What do I do after that?  My computer still doesn't recognize my wifi adapter.

I keep thinking I am at the last step, and then nothing happens...again.  Grrr.

---

### Post by bobplano on 2007-04-07
i think you need to use ndiswrapper and 'wrap' the drivers so linux can use them if you don't have ndiswrapper you can get them from [here]("http://sourceforge.net/project/showfiles.php?group_id=93482"). then you need to compile it (if you can use synaptic to get it that would be easier). then you need to open a terminal and go to where the drivers are and use

```
sudo ndiswrapper -i *driver's name*
```

to check and see if your computer recognizes the adapter type in

```
 ndiswrapper -l
``` 

and it should say something like "driver installed"

---

### Post by awiggin on 2007-04-07
I tried that - no go.

It told me it was the wrong driver.

Perhaps I am going about this the wrong way.  Maybe I should go look for a wifi adapter that works well with Ubuntu / Linux.

Any suggestions (either to solve the "wrong driver" problem or how to find a good wifi adapter?

THanks,
Lance

---

### Post by jpkotta on 2007-04-08
If the wifi card supports Linux (as you say in the first post), then surely it comes with instructions.  Can you post them?

---

