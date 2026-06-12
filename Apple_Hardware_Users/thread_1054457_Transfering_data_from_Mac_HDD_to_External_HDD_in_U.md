---
title: "Transfering data from Mac HDD to External HDD in Ubuntu 8.04 LIVE Disc"
date: 2009-01-29
forum: Apple Hardware Users
---

### Post by soulcleaver on 2009-01-29
Ok, I am extremely new to Ubuntu, and my mac partition recently crashed. I have wanted to give Ubuntu another shot (I tried a while back...) Anyways, I need to get my music/pictures/etc... to my external hard drive before I can format my disc and boot up Ubuntu.

I can open my "Macintosh HDD" (that is what its called) and i can navigate to the users folder, but it says I dont have the appropriate permissions to access it. 

Is there a way to get myself access? Just if your curious, I am running on an Aluminum iMac, so it is an intel dual core. If some of you more advanced users could help me out, it would be wickedly appreciated. I really dont want to lose ...everything...  My external is more than big enough to hold the entire "Macintosh HDD" so, if it is necessary, I can copy the whole HDD. I would prefer to select a destination though. Keep in mind, Im like a guy at a fancy restaurant in a foreign country, and I dont speak the language. Be very very detailed please. Thank you so much everyone!

---

### Post by tiresia on 2009-01-29
Did you see your mac partition having started your mac with an ubuntu live cd, or you have a second hard disk on your mac?
If you are in ubuntu run in a terminal ```
gksudo nautilus
```

---

### Post by soulcleaver on 2009-01-29
No, I opened my "Home" folder and had to click on it on the left side to ...mount... it. Correct me if my word use is wrong. Once I opened it, then It had shown up on the desktop. I did the command you had in your reply, and it came up with a root folder, and 1 folder called "Desktop" was in it.

---

### Post by Bölvaður on 2009-01-29
Can you give us a detailed walk from when you turn on the computer and until you get that error with the permissions.

The solution is like he said, "gksudo nautilus" but we need more info to tell you exactly what you need to do.

(but as a test you can press Alt+F2 and type in "gksudo nautilus" and then type in your password which gives you permission to do whatever you want, and try find /media/MachintoshHDD or what ever it is called)

---

### Post by soulcleaver on 2009-01-29
Ok, I used the alt+f2 and did the gksudo nautilus and it let me access the folders I needed, but when I try to copy them, it gives me an error message. By the way, I dont see where I have to put in a password... or what password I have to use.

"Error while copying.
The file "Music" cannot be handled because you do not have permissions to read it.


My startup operations are...

> Power Button
> Hold option to load ubuntu disc
> hit "English"
> hit use without harming current set up
> Open "MYBOOK" (my external HDD)
> Click "Macintosh HDD" on left side of open window
> "Macintosh HDD" pops up on desktop

that is where im stuck with my problem described above.

---

### Post by Bölvaður on 2009-01-29
I cannot see why this would happen if you would use nautilus with super user rights, did you only use the window that popped up when you wrote that?

Btw are you comfortable with the terminal (you may have used it on the mac, all the people I know that has macs use the terminal there VERY often)

---

### Post by soulcleaver on 2009-01-29
Ok, how do I use super user rights? And when I do nautilus I use the windows that pops up. Unfortunatly, I am not very comfortable with terminal (sorry).

---

### Post by tiresia on 2009-01-29
You don't need to press alt+f2 
Do like this:

> Power Button
> Hold option to load ubuntu disc
> hit "English"
> hit use without harming current set up

*Don't mount anything!*
Go to Applications > Accessories > Terminal
There you run 'gksudo nautilus'
(Nautilus is the File Browser - like Finder in MacOSX, that you open with gksudo to get super user rights)

Open a second window if you need, from inside nautilus (File > New Window)
On the left side you will see listed all your disks.
Click on the icon of your HD's to mount them.
Now you should be able to access and copy everything you want.

---

### Post by soulcleaver on 2009-01-29
Perfect, that worked awesomely Tiresia, thank you both for your help! I will let you know if I have any other problems! Thank you both so much!

---

### Post by tiresia on 2009-01-29
Please, mark the thread as solved, if you don't have questions anymore

---

### Post by soulcleaver on 2009-01-29
Ok, here is an addition. I can transfer very small files, but when I try to move music files or anything like that, it starts to transfer, but then just stops... I have no idea why.

---

### Post by tiresia on 2009-01-29
Can you see a message in the terminal? (I forgot to tell you, not to close the terminal, otherwise Nautilus will close)
Does it says you that it can't read some files?

---

### Post by soulcleaver on 2009-01-29
There is nothing that is showing up in terminal, the transfer rate is saying 0 kb/sec, and if it does start transfering, it is like 4 MB/sec. Im not sure what is going on.

---

### Post by tiresia on 2009-01-29
That's strange. What are you trying to copy? A folder or a file?

---

### Post by soulcleaver on 2009-01-29
Ok, it is giving me an error... 


Error while copying "file name"

There was an error copying the file into /media/MYBOOK/Trial

Error reading from file: Input/output error

---

### Post by soulcleaver on 2009-01-29
I am transfering folders (containing files (obviously)) music in this case.

---

### Post by tiresia on 2009-01-29
It is just a big file, or a folder? It is safer to control each file, if the files are very important for you. 
If it is a folder, make a folder with the same name in the destination HD, and try to copy single files, just to understand which file is giving you a problem.

How is the Destination HD formatted? Are you using fat32?

---

### Post by soulcleaver on 2009-01-29
I will try to run it that way, and yes my external is fat32, should I be able to transfer smaller folders? the one I am attempting is 118GB, and that is just my music, I have a few others around this size aswell that need transfering.

---

### Post by tiresia on 2009-01-29
The fat32 File System has a limit of 4GB. You can't copy there a file that is bigger than 4GB.

---

### Post by soulcleaver on 2009-01-29
Can I reformat it to something that can accept a larger ammount? NTFS is decent isnt it?

---

### Post by tiresia on 2009-01-29
It depends. How do you want to access it afterwards? From a Mac or from Ubuntu?
If you want to access it from Ubuntu, choose ext3.

From a mac, you should use HFS+ (but you can't do it with gParted).
 
The easiest solution for you, at this point is to make several folders, and copy there a group of file.

---

### Post by cyberdork33 on 2009-01-30
> **tiresia said:**
> The fat32 File System has a limit of 4GB. You can't copy there a file that is bigger than 4GB.
that is for a single file just for clarification.... as long as all the individual files are smaller than 4GB, then there should not be any problem.

parted magic can format an HFS+ partition.

---

