---
title: "installing programs that need ie"
date: 2006-08-08
forum: Absolute Beginner Talk
---

### Post by deadkarma on 2006-08-08
was wondering, what would it take to download ie so that i could get autocad installed?  can't seem to figure it out

---

### Post by akniss on 2006-08-08
> **deadkarma said:**
> was wondering, what would it take to download ie so that i could get autocad installed?  can't seem to figure it out

If IE is what you need, the program you need is most definitely a windows based app.  Your best bet then is to investigate wine, which will allow certain windows apps to run under linux.

---

### Post by deadkarma on 2006-08-08
> **akniss said:**
> If IE is what you need, the program you need is most definitely a windows based app.  Your best bet then is to investigate wine, which will allow certain windows apps to run under linux.

that's not so much the problem.  i can find ie, but it seems like you have to go to the ms website toget it, and i was wondering if there was a way to emulate it, or a website that has an older version i can get.  the ms site won't let you unless you have windows.

also is there a way to get linux to deal with RAR files?  i'm new to these things, so i'm most liklly am going to ask questions that seem kinda simple.

---

### Post by akniss on 2006-08-08
[http://www.rubyrailways.com/install-internet-explorer-on-ubuntu-dapper-in-3-easy-steps/](http://www.rubyrailways.com/install-internet-explorer-on-ubuntu-dapper-in-3-easy-steps/)

Well, i'm certainly no expert, as I took the easy way out and purchased codeweavers crossover office...  However, I seem to remember when I was playing with wine a few months ago, the winecfg would automatically install a version of IE.  Also, the above link may work for you.  Good luck!

---

### Post by deadkarma on 2006-08-08
> **akniss said:**
> [http://www.rubyrailways.com/install-internet-explorer-on-ubuntu-dapper-in-3-easy-steps/](http://www.rubyrailways.com/install-internet-explorer-on-ubuntu-dapper-in-3-easy-steps/)

Well, i'm certainly no expert, as I took the easy way out and purchased codeweavers crossover office...  However, I seem to remember when I was playing with wine a few months ago, the winecfg would automatically install a version of IE.  Also, the above link may work for you.  Good luck!

thanks this helped with getting ie, now i just need to get the program to realize it.  by the way, on the website to get ie they mentioned something about uncommenting some lines in the sources list.  what does that mean?

---

### Post by Jagot on 2006-08-08
This is by far and away the easiest way to get IE:

[http://www.tatanka.com.br/ies4linux/index-en.html](http://www.tatanka.com.br/ies4linux/index-en.html)

And in response to deadkarma, some of the repo's in the sources.list may have hash marks before them which means that they are then skipped over basically and ignored.  Removing the hashes means that those repositories will be activated enabling you to download from them

---

### Post by akniss on 2006-08-09
> **deadkarma said:**
> thanks this helped with getting ie, now i just need to get the program to realize it.  by the way, on the website to get ie they mentioned something about uncommenting some lines in the sources list.  what does that mean?

to 'uncomment' means to remove the ```
#
``` from the front of lines in a file.  so you would need to type at a terminal
```
sudo gedit /etc/apt/sources.list
```
then remove the # sign in front of lines that contain the needed repositories.

---

