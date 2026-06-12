---
title: "Stupid question"
date: 2007-04-29
forum: Absolute Beginner Talk
---

### Post by PricklySponge on 2007-04-29
How do I save a xorg.conf file after I have edited it?

---

### Post by Pobega on 2007-04-29
Depends on the editor you are using. Also, you must have root permissions (Through the use of sudo in Ubuntu) to be able to write to the file.

---

### Post by floke on 2007-04-29
Depends how you are editing it.
If you're using sudo nano ... then ctrl-x and choose 'yes'

If sudo gedit - then click save.

* VERY IMPORTANT - BACKUP BEFORE CHANGING IT! sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup - then reverse the paths to restore if needed

---

### Post by PricklySponge on 2007-04-29
I'm using the terminal. So what exactly do I do?

---

### Post by floke on 2007-04-29
Make your backup
Then type sudo [name of editor] [path of file to edit]
So eg

sudo nano /etc/X11/xorg.conf

Will open up the editor in the terminal - make the changes and hit ctrl-x to exit - select yes to save before exiting.

Or...

sudo gedit /etc/X11/xorg.conf

Assuming you use Gnome - will open up a text editor in another window. 
Make chanegs and select save before exiting.

Hoipe this helps

---

### Post by PricklySponge on 2007-04-29
worked like a charm 

Thanks:)

---

### Post by topsites on 2007-04-29
> **Steve.K said:**
> Make your backup
Then type sudo [name of editor] [path of file to edit]
So eg

sudo nano /etc/X11/xorg.conf

Will open up the editor in the terminal - make the changes and hit ctrl-x to exit - select yes to save before exiting.

Or...

sudo gedit /etc/X11/xorg.conf


Interesting...

I always type 
pico /etc/X11/xorg.conf

from the command line.
Not much into sudo'ing, I guess...

---

### Post by floke on 2007-04-29
You live and learn.
Nice one :)

---

