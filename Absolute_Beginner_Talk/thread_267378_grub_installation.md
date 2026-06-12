---
title: "grub installation"
date: 2006-09-28
forum: Absolute Beginner Talk
---

### Post by Compact on 2006-09-28
I have installed Ubuntu in a extended partition. In the other partition there is windows installed. The problem is that Ubuntu installer have not installed the GRUB loader and I cannot boot Ubuntu. Any solution?

---

### Post by bulldog on 2006-09-28
Yes there is.

Boot the live cd and do the folowing,

When you get to the desktop open a terminal and enter. 


```
sudo grub
```


This will get you a "grub>" prompt (i.e. the grub shell). At grub>. enter these commands


```
find /boot/grub/stage1
```

This will return a location. If you have more than one, select the installation that you want to provide the grub files.
Next, THIS IS IMPORTANT, whatever was returned for the find command use it in the next line (you are still at grub>. when you enter the next 3 commands)


```
root (hd?,?)
```

Again use the value from the find command i.e. if find returned (hd0,1) then you would enter root (hd0,1)

Next enter the command to install grub to the mbr


```
setup (hd0)
```

Finally exit the grub shell


```
quit
```

That is it. Grub will be installed to the mbr.

---

### Post by Compact on 2006-09-28
Thank you for your reply, but I followed the exactly instructions without errors and the grub menu is not shown when the computer boot. Why?

---

### Post by bulldog on 2006-09-28
Then you made a mistake somewhere I suppose.

Did you enter your right hdd and root partition?

This has worked for me several times without a hitch,so it should do for you.

Do you have a safety in your BIOS that hold back writing to the MBR?

Did GRUB already work or is it never been installed at all.

---

### Post by bodhi.zazen on 2006-09-28
Bulldog: You're not still touchy 'bout your mail box are you? :confused:

(Peeks out from behind monitor) :tongue:


Nice how to by the way. O:)

---

### Post by bulldog on 2006-09-28
> **bodhi.zazen said:**
> Bulldog: You're not still touchy 'bout your mail box are you? :confused:

(Peeks out from behind monitor) :tongue:


Nice how to by the way. O:)

Nope,never was,came home late and had a quick look at the forums.
Great surprise I had a pm from a topic completely unknown to me.
So I take a look what was going on..................and saw your post,then I knew :D :D

---

### Post by bodhi.zazen on 2006-09-28
Well then you should know....

I bet you collar in yet another post, and lost.... :shock:

(Hides) #-o

---

### Post by Compact on 2006-09-29
It's solved. There was an error with the hdd number. Thank you very much for your help!

---

### Post by bulldog on 2006-09-29
Glad to hear it worked at last.

I worried if things where changed and I didn't know.:D

---

