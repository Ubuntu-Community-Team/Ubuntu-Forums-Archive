---
title: "Move directory to another directory as root?"
date: 2008-01-29
forum: Absolute Beginner Talk
---

### Post by a-converted-sparky on 2008-01-29
Hi everyone

I have trailed the forums but cant see the answer im looking for

I have extracted a tar.bz2 file onto my desktop, although ideally i need to dump it into
/usr/share/cairo-clock/themes

When i extract the files i get an error reporting i am not root.

What is the best way to do this? how can i run the extractor as root?

I have tried thru the terminal but my knowledge and understanding is not that great, i tried:

su - to log in as root
root@ihatems:/home/sparky/Desktop/move# mv "*.*" -t "/usr/share/cairo-clock/themes"

I was hoping to select all the files/folders in the new folder (extracted from the tar.bz2) and mv them to /usr/share/cairo-clock/themes

Please anyone?

Many Thanks

Mark

---

### Post by luisromangz on 2008-01-29
su was the way to do this kind of thing before, but in Ubuntu we use the sudo command, which grants you root priveleges only for the command especified with sudo.

For example: sudo mv "*.*" -t "/usr/share/cairo-clock/themes"

If you want to perform several tasks as root, you can use:

sudo su

---

### Post by aysiu on 2008-01-29
Why don't you extract it to your desktop?

Then Alt-F2 ```
gksudo nautilus
``` which will open your file browser as root, navigate to /usr/share/cairo-clock/themes and paste the extracted folder there.

---

### Post by a-converted-sparky on 2008-01-29
Why?.... becuase i didnt know about this alt F2 business,

GREAT STUFF! easy when you know how

Many thanks!

Mark

---

### Post by aysiu on 2008-01-29
> **a-converted-sparky said:**
> Why?.... becuase i didnt know about this alt F2 business,

GREAT STUFF! easy when you know how

Many thanks!

Mark
Sure. Read more about it here:
[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)

---

