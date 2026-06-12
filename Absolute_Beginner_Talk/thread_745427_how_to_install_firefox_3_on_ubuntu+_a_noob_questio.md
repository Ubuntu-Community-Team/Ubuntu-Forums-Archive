---
title: "how to install firefox 3 on ubuntu+ a noob question."
date: 2008-04-04
forum: Absolute Beginner Talk
---

### Post by Nedux on 2008-04-04
Hi frends, I just downloaded firefox3 from <a href="http://www.mozilla.com/en-US/firefox/all-beta.html">here</a> and I don`t know how to install it . Please help; 
 and the second thing I would like to ask  about my computer, <a href="http://h18000.www1.hp.com/products/quickspecs/11506_na/11506_na.HTML">hpXW8000</a>
there`s a sticker on it with the windows in with says "designed for microsoft windows xp"
Is there a probeblem if I installed ubuntu on it . I mean .. hmm It will work well with ubuntu ? or I need to install windows to get the best of it.

---

### Post by bumanie on 2008-04-04
I assume you have downloaded the file 3.0b5.tar.bz2 Is this correct? Also, firefox 3 is included in the upcoming hardy release - not long to wait.

---

### Post by Michael.Godawski on 2008-04-04
I cannot open the site with the hp computer. Perhaps I am dumb or something. But I do not see a problem in installing linux on a machine with such a sticker. I do not think there really is a computer "designed for an operating system". 

Concerning firefox 3 
[http://de.youtube.com/watch?v=pIpne4cc3Hk](http://de.youtube.com/watch?v=pIpne4cc3Hk)

---

### Post by chris82543 on 2008-04-04
try downloading firefox from add and remove programs, they should have it under networking, check the box then click apply, It should install it for you.

---

### Post by northern lights on 2008-04-04
> **chris82543 said:**
> try downloading firefox from add and remove programs, they should have it under networking, check the box then click apply, it should adimaticly install it.It will, but not 3beta5...

---

### Post by Nedux on 2008-04-04
yes firefox 3.0b5.tar.bz2 correct :)
 this one is my computer. [http://www.midisoft.de/studio2005/xw8000.htm](http://www.midisoft.de/studio2005/xw8000.htm)

---

### Post by marine63 on 2008-04-04
extract the tar .gz and take the "firefox" folder that been extracted and rename it firefox 3.0 beta 5 then place the folder in usr/lib/. 
manually put launcher in taskbar and in the menu you need to make the launcher for the file name "firefox"
im sure most pc parts are made for windows drivers wise but ubuntu is doing a good job of making more hardware to work for ubuntu

---

### Post by Nedux on 2008-04-04
I get a error: you do not have permissions to write to this folder., what can I do now?

---

### Post by northern lights on 2008-04-04
open your file browser with root rights. If your using gnome: ```
gksu nautilus
```should do the job. If you're copying from the commandline, run "cp" with "sudo"...

---

### Post by Nedux on 2008-04-04
it`s not working I get this error now ,"couldn`t find /gksu nautilus" sorry . I`m new to linux. 
Maybe you should guide me to some basic things first.

---

### Post by Nedux on 2008-04-04
oh it worked :D I typed that command in a terminal and It worked, I copied firefox folder into /usr/lib now how do I create a launcher  ?

---

### Post by Nedux on 2008-04-04
it`s working :D firefox 3 it`s working but how do I create a shortcut .? 
thanks guys :D

---

### Post by mikewhatever on 2008-04-04
Right click on the desktop, select 'Create Launcher', in the command line type the path to the executable (should be /usr/lib/firefox/firefox).

---

