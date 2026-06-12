---
title: "An app that you can save web pages AND links."
date: 2007-08-16
forum: Absolute Beginner Talk
---

### Post by tk338 on 2007-08-16
Is there an app. that you can save a webpage and all the content... AND the content of the links?

---

### Post by sad_iq on 2007-08-16
I think you can do that with the command **wget**. Haven't used it the way you want but I think it's what you need. > Wget can follow links in HTML and XHTML pages and create local versions
       of remote web sites, fully recreating the directory structure of the
       original site.  This is sometimes referred to as &#8216;&#8216;recursive download&#8208;
       ing.&#8217;&#8217;  While doing that, Wget respects the Robot Exclusion Standard
       (/robots.txt).  Wget can be instructed to convert the links in down&#8208;
       loaded HTML files to the local files for offline viewing.
Type ```
man wget
``` and read about it!!!

---

### Post by vexorian on 2007-08-16
> **tk338 said:**
> Is there an app. that you can save a webpage and all the content... AND the content of the links?
I just used it.

create a folder where you want to save the web page to, use the terminal to get to that folder and type:

```

wget -r http://site.com/pageaddress.html

```

it will begin downloading everything it finds.

Also, if you want to save links with extensions other than .html you can do:


```

wget -r  --accept *.html,*.htm,*.pdf,*.png http://site.com/pageaddress.html

```

---

### Post by tk338 on 2007-08-16
sorry, not familiar with the file structre of linux, say i put the folder on my desktop, how would I use terminal to get to that folder?

---

### Post by Arthur Archnix on 2007-08-16
This is your home folder:
```
~/
```
This is your Desktop:
```
~/Desktop
```
cd means change directory, mkdir means create a folder, ls means list files and folders in my current directory. Those are all the commands you should need to get started in the terminal.

---

### Post by vexorian on 2007-08-16
> **tk338 said:**
> sorry, not familiar with the file structre of linux, say i put the folder on my desktop, how would I use terminal to get to that folder?
if you don't mind, I recommend the nautilus-open-terminal package


use  ```
sudo apt-get install nautilus-open-terminal
```

from a terminal or try looking for the nautilus-open-terminal package in synaptic package manager.

Once it is installed you'll have an option in nautilus' file menu to open a terminal in your current location, it is very useful

---

### Post by tk338 on 2007-08-16
Ah thankyou everyone, a great help.

EDIT: 
Ok, so I do all that and then it comes up with bash: /home/tk338/Desktop/folder: is a directory

---

