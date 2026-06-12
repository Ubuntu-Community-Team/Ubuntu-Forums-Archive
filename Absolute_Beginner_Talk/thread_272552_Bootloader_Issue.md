---
title: "Bootloader Issue"
date: 2006-10-06
forum: Absolute Beginner Talk
---

### Post by scottbraun4571 on 2006-10-06
Hi,

Ive had ubuntu and windows xp dual booting for awhile now, using the grub bootloader. I had to reformat my windows drive and reinstall xp once again. Now my grub menu appears to be gone, and I cant find a way to get into linux. Anybody have a quick answer to how to get this back.

Thanks in advance,

Scottie

---

### Post by bulldog on 2006-10-06
Yes boot in the live cd and do the following commands it install grub on your hdd.

Boot into the live Ubuntu cd. This can be the live installer cd or the older live session Ubuntu cds.

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

### Post by Kateikyoushi on 2006-10-06
This is what you need to follow.

[Restore grub from live cd.]("http://http://www.ubuntuforums.org/showthread.php?t=224351&highlight=live+cd+grub")

---

### Post by Drakkor on 2006-10-06
Huh? Bulldog's advice is the easiest way to do it, except at the end where it says: ```
quit
``` should be ```
exit
```

---

### Post by bulldog on 2006-10-06
Quit works fine by me :D and

grub> exit

Error 27: Unrecognized command

---

### Post by Scheater5 on 2006-10-06
Just as a side note, these are the easiest and clearest (and most error-proof) instructions for this common problem I have found.  Congrats Bulldog.  Recently I helped someone with this exact problem, and I Was trying to find these instructions... If the person I helped who had wireless and fan problems with a Dell Inspiron sees this and still hasn't fixed the problem yet, these are the instructions I was refering to.  I'm bookmarking this page and pointing all with this problem to it.  You explain the bit about finding the harddisk in the most apropiate of terms (I myself don't completly understand how this works, and nor do most people with this problem - if we understood, we probably wouldn't need this help - and so most of the other instructions on the net are nigh useless).  Kudos Bulldog

---

### Post by bulldog on 2006-10-06
A simple way to do is copy my post into a gedit document and store it on your computer.

I have a text file which I copy and paste when somebody comes along with this problem.

So I have less to type everytime :D

---

### Post by Drakkor on 2006-10-06
Yeah,Bulldog,you're right, I thought "quit" would take you out of the terminal,it just goes back to the terminal command line,and then you can type "exit" to quit the terminal. :p

---

### Post by danbuffington on 2006-10-20
I followed the instructions exactly, and nothing happened. The returned hard drive was (hd0,0). This was after a fresh install.

[scratching head]

What now?

---

### Post by ReaderRat on 2006-10-20
[[color=BLUE]**GRUB HowTo**[/color]](https://help.ubuntu.com/community/GrubHowto)
&  [http://users.bigpond.net.au/hermanzone/p15.htm#hidethemenu](http://users.bigpond.net.au/hermanzone/p15.htm#hidethemenu)

---

