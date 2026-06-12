---
title: "Pogo?"
date: 2005-12-15
forum: Art &amp; Design
---

### Post by Sp@z on 2005-12-15
Hi all I am trying to install this program [http://www.ibiblio.org/propaganda/pogo/](http://www.ibiblio.org/propaganda/pogo/)
but am having a hard time with extracting the file that is also needed. (imLIb) Any help? I hate being a noob asking silly stuff, but I guess this is the best way to learn.



Thanx in advance..............

---

### Post by endersshadow on 2005-12-15
```
sudo apt-get install imlib1 imlib-base imlib1-dev
sudo -k
cd
wget http://www.ibiblio.org/propaganda/pogo/pogo-3.0RC43.tar.gz
tar xzf pogo-3.0RC43.tar.gz
cd pogo-3.0
./pogo-installer
~/.pogo/pogo
```

Just do those commands into the terminal, and you'll be all set.

---

### Post by Sp@z on 2005-12-15
thank you for your help! It says it is installed and tells me to type a command and well I do and it does nothing > blinks at me.

I am so frustrated with Linux right now and I can't even tell if I have maybe a bad install. ughhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhh

I think imma go back to M$ winders (windows for rednecks)

---

### Post by endersshadow on 2005-12-15
I've attached a patch.  Download it and save it to your Home folder.  Then run these commands:

```
cd
tar xzf pogofix.tar.gz
mv -f pogo.c ~/pogo-3.0/src
cd pogo-3.0
./pogo-installer
~/.pogo/pogo
```

Should work now.

---

### Post by Sp@z on 2005-12-15
OMG man I am totally missing something, it still doesn't work. [sarcasm]Are all programs as  well document as this one [/sarcasm]

Imma buy you a beer or a coke, even though it didn't work, thank you for the time you have spent trying to help me.

---

### Post by XQC on 2005-12-16
Is there anywhere a screenshot, so everybody can see how it's supposed to look like?

---

### Post by Sp@z on 2005-12-16
I will hunt one up and post it. :P I am still trying to get this but I reinstalled linux breezy last night, so I will work on this later. :)

---

### Post by Sp@z on 2005-12-16
Here is a link, it is the tool bar at the bottom. I will settle for something close to that, I am not having luck installing this program...:(

[http://www.gnome-look.org/content/preview.php?preview=2&id=31128&file1=31128-1.jpg&file2=31128-2.jpg&file3=31128-3.jpg&name=Gentle+Gnome&PHPSESSID=94037f1a14bb3b3949d734ab734372a2](http://www.gnome-look.org/content/preview.php?preview=2&id=31128&file1=31128-1.jpg&file2=31128-2.jpg&file3=31128-3.jpg&name=Gentle+Gnome&PHPSESSID=94037f1a14bb3b3949d734ab734372a2)

---

### Post by Sp@z on 2005-12-16
Ok well, I got it installed, but here is the issue now. It popped up on my screen for about 3 seconds (Long enough to get wood) then dissapeared.......I opened up the system processes to see what was running and I see POGO and it is SLEEPING. I have not been able to get it to actually come up on the screen again. Any ideas from there?

Thanks Endersshadow, you have been a big help and very patient. We are close LOL.

---

### Post by Sp@z on 2005-12-17
got it working thanks all for your patients. Seems to only run with a terminal window open???????Odd but I am looking for configs to fix that now!

---

### Post by endersshadow on 2005-12-17
[QUOTE=Sp@z]got it working thanks all for your patients. Seems to only run with a terminal window open???????Odd but I am looking for configs to fix that now![/QUOTE]

Create a launcher, and use the command you use to open it in the terminal.

---

### Post by Sp@z on 2005-12-17
thanx man worked like a charm!!!!!!w00t!!!!!!!!!!

---

### Post by endersshadow on 2005-12-17
Glad to hear it...I'm here for you :-D

---

### Post by Sp@z on 2005-12-17
I still owe you a beer or a coke man!

---

### Post by endersshadow on 2005-12-17
Beer's preferable, but only the Coke's legal...

---

