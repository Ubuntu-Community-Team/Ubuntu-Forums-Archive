---
title: "[SOLVED] Quick Queries"
date: 2007-10-09
forum: Absolute Beginner Talk
---

### Post by cooper892 on 2007-10-09
After many greuling hours, I have finally worked out many of the major issues I was originally having with Ubuntu, much thanks to the contributers of the forums! I just have a couple more "Absolute Begginer" questions that I've been wondering about.

- The only way I can run Audacity correctly is to go into the terminal and type "aoss audacity". Is there any other way to do this without having the terminal open?

-Is shell scripting the equivlent of making batch files in Windows?

-When is it estimated that the final and bug-free (for the most part) Beryl will be released?

-What is the difference between Beryl and Compiz

-Will it be possible to make a Live CD of Gusty Gibbon when it is released?

-Is it possible to completely change the log in process. I know that you can go into "System-Administration-Login Window", but is there a way that I can mabye put a video and sound before and after I enter my username and password?

I am very grateful to the Ubuntu community who have already assisted me in adapting to the Linux enviorment. Any answers to the above questions is greatly appreciated. Thank you!

---

### Post by jgrabham on 2007-10-09
> **cooper892 said:**
> After many greuling hours, I have finally worked out many of the major issues I was originally having with Ubuntu, much thanks to the contributers of the forums! I just have a couple more "Absolute Begginer" questions that I've been wondering about.

- The only way I can run Audacity correctly is to go into the terminal and type "aoss audacity". Is there any other way to do this without having the terminal open?


go to /usr/bin, and in there there should be a file calles aoss-audacity, or just audacity, double click that, or create a shortcut.  Also, try restarting, and it may appear in your applications menu somewhere.

---

### Post by jonobr on 2007-10-09
Hello


For starting your app, you can create a text file in vi and enter the patch and make it executable.
For example to run my oracle caleandar client
I have a file on my desktop containing 

~/Oracalcalendar/bin/ocal &
This runs my app as a background task.
When you machine boots you can double click and run it.


As for shell scripting compared to batch files, doing a quick google it says your right, but me being Linux inclined, I will say that you can do so much more then windows, even though that may be a biased view....
Cant help on your other questions:-(

---

### Post by jonobr on 2007-10-09
Last post was a bit sloppy,

IN the terminal create a file using vi,

enter the path to execute your application, and end in & to make it run as a background task

(I was born with fat fingers.... Thanks Mama!!)

---

### Post by cooper892 on 2007-10-09
Not sure what vi is...I tried going to usr/bin and making a shortcut of Audacity, but I was having the same problems as I did before typing "aoss Audacity"

---

### Post by Paqman on 2007-10-09
> **cooper892 said:**
> 
- The only way I can run Audacity correctly is to go into the terminal and type "aoss audacity". Is there any other way to do this without having the terminal open?


You can change the command assigned to a launcher in the menus. Right click on the Ubuntu icon in the top left to get into the menu editor. You can change the icons and the commands that they use to launch things

> 
-When is it estimated that the final and bug-free (for the most part) Beryl will be released?

-What is the difference between Beryl and Compiz


Beryl and Compiz have merged. They are now called Compiz Fusion, and it's installed by default (and largely bug-free!) in Gutsy

> 
-Will it be possible to make a Live CD of Gusty Gibbon when it is released?


Absoloodle

> 
-Is it possible to completely change the log in process. I know that you can go into "System-Administration-Login Window", but is there a way that I can mabye put a video and sound before and after I enter my username and password?


You can pick different login screens  from "Login Screen" in Adminstration. People like to make their own ones (called GDM screens) There's lots at [GNOME-look](http://www.gnome-look.org/index.php?xcontentmode=150). I've got no idea about adding multimedia, sorry!

---

### Post by cooper892 on 2007-10-09
Thank you Paqman, I finally got it to work! Thanks to everyone for all the quick responses. And with my newfound knowledge I CAN'T WAIT for Gusty Gibbon to come out. I'm going to try distributing free Ubuntu CDs around my school (99% Windows users, other 1% Mac OS X) and see if I can get a computer revolution to commence. Thanks again to everyone who contributed. Problem Solved!

---

### Post by Paqman on 2007-10-09
> **cooper892 said:**
> Thank you Paqman, I finally got it to work!

No problem, glad to help! :)

---

