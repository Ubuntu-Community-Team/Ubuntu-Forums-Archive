---
title: "workgroup settings"
date: 2006-04-10
forum: Absolute Beginner Talk
---

### Post by rameez on 2006-04-10
How can I remove totem player, it sucks doesnot play anything.
When I try to remove it using add application, it says :
There are other applications depending on this one. If you really want to remove it, please use the "Advanced" mode from the menu.
Where is the Advanced mode and how do I remove totem player.

Thanks.

---

### Post by johnnymac on 2006-04-10
try this at a terminal:

sudo apt-get remove totem

GL

---

### Post by WoodyMahan on 2006-04-10
I use Totem on my machine and it works very well.  All my DVD's, .wmv, .mp3, etc. run with it.  Maybe you can load the Non Free Codecs and get better performance from it.  What kind of files are you trying to run?  Maybe we can help improve it's performance for you.

---

### Post by rameez on 2006-04-10
I installed the codecs and VLC plays DVD and mp3 but totem doesnot, any idea on how to fix it?
Or should I just uninstall it.

---

### Post by dvarsam on 2006-04-10
[QUOTE=rameez]I installed the codecs and VLC plays DVD and mp3 but totem doesnot, any idea on how to fix it?
Or should I just uninstall it.[/QUOTE]

Dear, rameez,
Do NOT worry, you are NOT the only one out there with this problem!!!
My "Totem" could NOT play anything also!!!
And I used the Ubuntu v5.10 Breezy Gnome Desktop install!
It just Crashes!!!
So I installed a different player, instead...

Good Luck!

---

### Post by WoodyMahan on 2006-04-10
On the wiki - under restricted formats, I found these 2 command lines:
  sudo apt-get install libdvdread3
  sudo /usr/share/doc/libdvdread3/examples/install-css.sh

I ran them and my Totem started playing my DVD's perfectly.

Not saying you didn't try this already of course.  But it worked for me so maybe it will work for you.

---

### Post by enyaw on 2006-04-10
[QUOTE=WoodyMahan]On the wiki - under restricted formats, I found these 2 command lines:
  sudo apt-get install libdvdread3
  sudo /usr/share/doc/libdvdread3/examples/install-css.sh

I ran them and my Totem started playing my DVD's perfectly.

Not saying you didn't try this already of course.  But it worked for me so maybe it will work for you.[/QUOTE]

I needed this...thx

---

### Post by WoodyMahan on 2006-04-11
I actually helped someone.  WOOHOO
My pleasure, of course.

---

