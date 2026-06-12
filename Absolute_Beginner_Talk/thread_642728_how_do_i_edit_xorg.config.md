---
title: "how do i edit xorg.config"
date: 2007-12-16
forum: Absolute Beginner Talk
---

### Post by aas452 on 2007-12-16
does any one know the command to edit when X isn't running

---

### Post by Rocket2DMn on 2007-12-16
If you ever touch xorg.conf, always make a backup first
Then you can edit the file from the command line using nano, a simple terminal based text editor.  Be careful!
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
sudo nano /etc/X11/xorg.conf
```

If you need to regenerate xorg.conf, you will need to run this and get asked questions about your hardware:
```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by PmDematagoda on 2007-12-16
```
sudo dpkg-reconfigure xserver-xorg
```

A backup is automatically made.

---

### Post by scizzo on 2007-12-16
you can do various things to edit the xorg.conf file.

First of all you can edit it with a normal editor ex: vi or so

# vi /etc/X11/xorg.conf

Or you can reconfigure it completely with:

# sudo dpkg-reconfigure xserver-xorg

I am sure there are a few other ways to configure it but those are the once I use mostly.

---

### Post by nowshining on 2007-12-16
u can edit it in applications - terminal

sudo gedit /etc/X11/xorg.conf

u can press the Tab key in the terminal / console to complete names:

example: type /et and hit the tab key u get /etc/
then type X then hit the tab key u get /etc/X11/
then type xo then hit the tab ke u get /etc/X11/xorg.conf

when u input ur password ur password will NOT show up while u type as this is for security, just type it as usual, and hit the enter key.

---

### Post by anewguy on 2007-12-17
If you don't have X running, you can't run the normal graphical editors.  As mentioned a couple of posts up, you can us vi  or you can use   vim.  Vim is just another version of vi.  These editors are not quite as easy as the aren't just plain WYSIWYG editors - so be sure to read the man pages or help online (if you can get there on another PC).  DO make a backup first -

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.good

then

sudo vim /etc/X11/xorg.conf

After editing, just logout and log back in.

What type of problem are you having that you need to do the edit - maybe we can help you with it?  Most all of us have had a need to edit that file more than once, so you'll probably find an answer here.

For now, do one step at a time - edit the file, save it, log off  logon (or just reboot).  If still no luck, then try the xserver-xorg reconfigure.  Sometimes people have a tendency to do "all at once" and in the mean time mess things up.  Keep in mind that 
sudo dpkg-reconfigure xserver.xorg

will overwrite the xorg.conf file, so if you make changes and then run the configure, you will probably just wipe out the changes you made.

---

### Post by Rocket2DMn on 2007-12-17
running the configure makes a backup automatically in the form of xorg.conf.YearMonthDayTime
I suggest using nano instead of vi/vim - it is very straightforward to use whereas vi is like beating yourself with a bat.  Don't get me wrong, vi can be great for some uses, like programming, but it's not needed for something this simple, esp. if you've never used it.
Also note that when you're in X, if you sudo for a graphical editor (or any other graphical program), use "gksudo" instead of "sudo".

---

### Post by nowshining on 2007-12-17
oh lolz, i forgot yes, yes

i suggest nano tho it's easier

ctrl + x to exit and when asked to save press Y on ur keyboard then enter key then re-start the x server/gui.

---

### Post by PmDematagoda on 2007-12-17
Hey, 7 posts in a time period of about 3 minutes, now that is responsiveness:D, looks like we may have set a new Ubuntu Forums record here:lolflag:.

---

### Post by nowshining on 2007-12-17
lolz PmDematagoda

---

### Post by anewguy on 2007-12-17
> **Rocket2DMn said:**
> running the configure makes a backup automatically in the form of xorg.conf.YearMonthDayTime
I suggest using nano instead of vi/vim - it is very straightforward to use whereas vi is like beating yourself with a bat.  Don't get me wrong, vi can be great for some uses, like programming, but it's not needed for something this simple, esp. if you've never used it.
Also note that when you're in X, if you sudo for a graphical editor (or any other graphical program), use "gksudo" instead of "sudo".

LOL - the vi/vim comments - perfect!!  I've always hated them since the first time I used vi about 14 years ago!!

---

### Post by Rocket2DMn on 2007-12-17
Just trying to save the guy some hassle.  Personally, I use emacs, but we won't go there tonight, hehe.

---

### Post by nowshining on 2007-12-17
i could never figure out VI out myself :/ so i just gave up and finally found nano to be installed - easy to figure out and use, and that's what i stuck with and continue to stick with. :)

---

