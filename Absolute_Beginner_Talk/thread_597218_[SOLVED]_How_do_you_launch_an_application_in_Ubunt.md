---
title: "[SOLVED] How do you launch an application in Ubuntu?"
date: 2007-10-30
forum: Absolute Beginner Talk
---

### Post by eamann on 2007-10-30
Hi!

Sorry for asking what will seem such an elementary question!

I used Synaptic to download (and install?) a financial application called **Beancounter** but I cannot launch it. I have found a whole series of Beancounter files, mainly in the Usr/Bin and Usr/Share folders, but double-clicking on these does not launch the programme. (In other words, I am looking for an "exe" file as in Windows...)

Not being able to launch Beancounter, I used the Applications/Add-Remove menu to install **GnuCash** but I cannot find the application! I thought it would add itself to the applications list, but it's not there (or at least I cannot see it). Neither is it on the desk. Can anyone tell me where installed applications are listed?

Thanks!

Eamann

---

### Post by Nano Geek on 2007-10-30
Both of those programs should be under **Applications** in the top left corner and then **Office**.

---

### Post by eamann on 2007-10-30
Thanks for reacting!

> Both of those programs should be under Applications in the top left corner and then Office

Encouraged by your answer, I edited the Applications / Office menu and sure enough I found two new but unselected icons. (How can I get Applications to show new programmes automatically? I do not see any "preferences" menu.)

Unfortunately, when I click on GnuCash, a little window opens at the bottom of the page saying "Starting GnuCash" but then it disappears and GnuCash is nowhere to be seen. 

When I click on the second new icon, which is not called Beancounter but Invest Chart, that is all I get - a chart, that is, a bit of the application, but not the home page of the application.

Any further suggestions?

Best wishes,

Eamann

---

### Post by black_magician on 2007-10-30
> **eamann said:**
> 

I used Synaptic to download (and install?) a financial application called **Beancounter** but I cannot launch it. I have found a whole series of Beancounter files, mainly in the Usr/Bin and Usr/Share folders, but double-clicking on these does not launch the programme. (In other words, I am looking for an "exe" file as in Windows...)




There is no GUI built into beancounter, so the way to launch it is to open a terminal(Applications -> Accessories -> Terminal) and type "beancounter" (without quotes).

this link may help you learn more about it.
[http://dirk.eddelbuettel.com/code/beancounter.html](http://dirk.eddelbuettel.com/code/beancounter.html)

---

### Post by eamann on 2007-10-30
Thanks Black-Magician!

I was able to launch Beancounter following your instructions, but since it has no GUI I am not interested in using it.

Have you any idea why GnuCash seems to abort?

Best wishes,

Eamann

---

### Post by steve.horsley on 2007-10-30
Try launching it from the command line. It may print a useful error message before dying.

---

### Post by eamann on 2007-10-31
I hadn't thought of using Terminal. It's a reflex I have yet to acquire. Here's the error message I got when I tried to launch GnuCash. 

How do I go about changing the permissions for GnuCash?

Thanks for your help!

Eamann

eamann@eamann-laptop:~$ gnucash
gnc.bin-Message: main: binreloc relocation support was disabled at configure time.

An error occurred while creating the directory:
  /home/eamann/.gnucash/checks
Please correct the problem and restart GnuCash.
The reported error was 'Permission denied' (errno 13).
eamann@eamann-laptop:~$

---

### Post by macogw on 2007-10-31
ls -l ~/.gnucash/

---

### Post by hyper_ch on 2007-10-31
and also do:

```

ls -al /home/earmann

```

---

### Post by eamann on 2007-11-01
Thanks for the suggestions. This is the print out I get concerning GnuCash using the two commands:

eamann@eamann-laptop:~$ ls -l ~/.gnucash/
total 12
drwx------ 2 root root 4096 2006-09-30 20:46 books
-rw-r--r-- 1 root root 1531 2006-09-30 20:46 config-1.8.auto
-rw-r--r-- 1 root root  854 2006-09-30 20:43 qif-accounts-map

and 

drwxr-xr-x  3 root   root     4096 2006-09-30 20:46 .gnucash
drwxr-xr-x  2 root   root     4096 2007-11-01 14:34 GnuCash

I have tried to edit the permissions in this text in the Terminal, but that does not work.

Then I tried using "chmod" but that did not work either:

root@eamann-laptop:/home/eamann# chmod o+rwx gnucash
root@eamann-laptop:/home/eamann# ls -l 
Display all 111 possibilities? (y or n)
root@eamann-laptop:/home/eamann# chown eamann gnucash
root@eamann-laptop:/home/eamann#  ls -l ~/.gnucash/
total 36
-rw-r--r-- 1 root root 16951 2007-11-01 14:34 accelerator-map
drwx------ 2 root root  4096 2007-10-31 22:41 books
drwx------ 2 root root  4096 2007-10-31 12:25 checks
-rw-r--r-- 1 root root     0 2007-11-01 14:34 expressions-2.0
-rw-r--r-- 1 root root   766 2007-10-31 23:47 qif-accounts-map
-rw-r--r-- 1 root root   871 2007-11-01 14:34 stylesheets-2.0

I also tried "chown" but that was not successful either:

root@eamann-laptop:/home/eamann# chown eamann gnucash
root@eamann-laptop:/home/eamann#  ls -l ~/.gnucash/
total 36
-rw-r--r-- 1 root root 16951 2007-11-01 14:34 accelerator-map
drwx------ 2 root root  4096 2007-10-31 22:41 books
drwx------ 2 root root  4096 2007-10-31 12:25 checks
-rw-r--r-- 1 root root     0 2007-11-01 14:34 expressions-2.0
-rw-r--r-- 1 root root   766 2007-10-31 23:47 qif-accounts-map
-rw-r--r-- 1 root root   871 2007-11-01 14:34 stylesheets-2.0

Where do I go from here?

Thanks once more for your help!

Eamann

---

### Post by Whiffle on 2007-11-01
Its very odd that it got installed that way.  I am glad you're getting a grasp on the terminal as well :D 

I think  what you need to do is 
```

sudo chown -R eamann /home/eamann/.gnucash
sudo chgrp -R eamann /home/eamann/.gnucash

```

I'm not sure why it put all that stuff as owned by root though.  Hmmm.

Oh and if gnucash doesn't suit you, there is also kmymoney as well.

---

### Post by eamann on 2007-11-02
Thanks Whiffle!

That did it!

I don't know how all that stuff with root came to be there.

My intention is to install a new clean version of Ubuntu instead of merely upgrading so that I can make a fresh start.

I find GnuCash very complicated and not particularly adapted to my needs (keeping tabs on my mutual funds). It's a sledge hammer cracking a nut. I will certainly have a look at kmymoney, but will that work on Gnome?

Once again, thank you (and the others who reacted) very much!

Eamann

---

### Post by Whiffle on 2007-11-05
It will work, it may start a little slower though since it depends on kde libraries.  You could always drop by their website and peruse the screenshots and stuff too before you install it.  

[http://kmymoney2.sourceforge.net/index-home.html](http://kmymoney2.sourceforge.net/index-home.html)

---

