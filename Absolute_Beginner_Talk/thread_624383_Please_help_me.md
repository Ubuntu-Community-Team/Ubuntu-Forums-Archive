---
title: "Please help me"
date: 2007-11-26
forum: Absolute Beginner Talk
---

### Post by alejandro.mc on 2007-11-26
Hey I really need help. I was making a slideshow with Kdenlive, so I finish the slideshow, export to DVD (all files in my desktop) suddenly, all folders and files dissapear in a second. Can't find them anywhere. Beagle can't find, I don't.. are they deleted forever? what's wrong how could that happen? i have very important files. Had a backup but its also gone.

Please any help will be appreciated.

---

### Post by zabien1970 on 2007-11-26
Did you have the files previously saved? If so you may be able to use the whereis command in the terminal  ie. 'whereis pictures' using the name you saved them under

---

### Post by alejandro.mc on 2007-11-26
I just yped whereis a.jpg (that was one picture) and this came up:

alejandro@alejandro:~$ whereis a.jpg
a:
alejandro@alejandro:~$ 
alejandro@alejandro:~$ 


HEY THX FOR HELPING ME IM FREAKING OUT I REALLY NEED THOSE FILES

what does it mean?

thx

---

### Post by brennydoogles on 2007-11-26
> **alejandro.mc said:**
> Hey I really need help. I was making a slideshow with Kdenlive, so I finish the slideshow, export to DVD (all files in my desktop) suddenly, all folders and files dissapear in a second. Can't find them anywhere. Beagle can't find, I don't.. are they deleted forever? what's wrong how could that happen? i have very important files. Had a backup but its also gone.

Please any help will be appreciated.

Does Kdenlive close unexpectedly, or do the files just suddenly disappear? If kdenlive is still open, chances are the files were moved to /tmp for a while. Otherwise we may need to try and recover the files with testdisk.

---

### Post by alejandro.mc on 2007-11-26
Kdenlive closed, and all my files in my desktop dissapeared inmediately. went to places, recent documents, and open the ones there, and it says they are not there anymore.

checked the tmp, they are not there

what is this test thing?

THANKX A LOT FOR YOUR HELP

---

### Post by brennydoogles on 2007-11-26
> **alejandro.mc said:**
> Kdenlive closed, and all my files in my desktop dissapeared inmediately. went to places, recent documents, and open the ones there, and it says they are not there anymore.

checked the tmp, they are not there

what is this test thing?

THANKX A LOT FOR YOUR HELP

Testdisk includes a file recovery option, but we want to avoid using it if possible, because it will be an extraordinary pain in the rear. Did KDEN leave an error log anywhere in your home directory for you?? When you look, make sure that you hit ctrl+h to show hidden files, because it might be called .kdenlive.log

---

### Post by Dr Small on 2007-11-26
If he would have been running the application with the terminal, it would have spilled any errors into it..

---

### Post by alejandro.mc on 2007-11-26
No no logs, did the hidden files things, no logs for errors or kdenlive logs.

**** i'm so scared, i have a powerpoint file already prepared there in the desktop to resent in 7 hours, im dead. it took me hours to build it. damned kdenlive..

THANKS FOR BEING THERE MAN

---

### Post by brennydoogles on 2007-11-26
> **Dr Small said:**
> If he would have been running the application with the terminal, it would have spilled any errors into it..

yes, but I don't think many people run their apps from terminal. Where is the system log located?? Maybe we could gt some answers there??

---

### Post by brennydoogles on 2007-11-26
> **alejandro.mc said:**
> No no logs, did the hidden files things, no logs for errors or kdenlive logs.

**** i'm so scared, i have a powerpoint file already prepared there in the desktop to resent in 7 hours, im dead. it took me hours to build it. damned kdenlive..

THANKS FOR BEING THERE MAN

Do not write any data to your hard drive until you get these files back. If you do there is a small chance you will overwrite them completely.

---

### Post by alejandro.mc on 2007-11-26
Ok

---

### Post by alejandro.mc on 2007-11-26
Anyone else? Well i guess this things happen. But i wonder where the hell did my files go.. its very rare.

if anyone else knows anything i could do please let me know, bye

---

### Post by brennydoogles on 2007-11-26
ok, I want you to type the following into a terminal...

```
gksudo nautilus /var/log
```
This will open a file browser [COLOR="Red"](AS ROOT.... DON'T DELETE ANYTHING)[/COLOR] open up your syslog, and search for kden (you can do that by pushing ctrl+f). Post anything that is related to kden. Hopefully we can find something there!!

---

