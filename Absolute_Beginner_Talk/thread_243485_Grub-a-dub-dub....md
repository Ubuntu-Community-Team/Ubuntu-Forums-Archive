---
title: "Grub-a-dub-dub..."
date: 2006-08-25
forum: Absolute Beginner Talk
---

### Post by qwazert on 2006-08-25
Forgive me if this topic has been dealt with before, or if I'm in the wrong section - the mods may delete this if they desire.

I have successfully editted the grub menu.lst by copying it into my home directory. Problem is, I can't seem to be able to acquire ROOT powers to copy it back to where it belongs!

I remember there was some command that allowed you to open NAUTILUS as a ROOT (or something to that effect) but I cannot, for the life of me, recall HOW it is done.

[SIZE="1"]Help[/SIZE]?

---

### Post by Druidor on 2006-08-25
```

gksudo nautilus 

```

in command line to bring up the GUI nautilus where you can drag & drop files as root.

---

### Post by Titus A Duxass on 2006-08-25
As an alternative do it through the terminal:

sudo cp /home/Name/menu.1st /boot/xxx/menu.lst

---

### Post by FuriousLettuce on 2006-08-25
To open nautilus as root, simply do 

```
gksudo nautilus &
```

That will open nautilus as root and let you run it in the background, allowing you to keep using the terminal.

Alternatively, you can do

```
sudo cp ~/menu.lst /boot/grub/menu.lst
```

You can use mv instead of cp if you want to.

NB: I'm not at my ubuntu box, so can't remember the exact directory that menu.lst should be in, so make sure that you check the directory first.

In addition, if you want to edit it where it is next time, simply do

```
gksudo gedit menu.lst &
```

(when you are in the grub directory.)

---

### Post by harisund on 2006-08-25
FuriousLettuce, a small suggestion, or a word of advice if you will. 

sudo is intended to run command line applications as a root user. Gedit and Nautilus doesn't fall under that category, as they are X11 applications. The correct way to launch them is to use 'gksudo' instead of 'sudo'. This is what gksudo is meant for. 

Yes, in most cases just appending sudo instead of gksudo for gtk applications might work, but is not suggested.

---

### Post by FuriousLettuce on 2006-08-25
Thanks, I did wonder what gksudo was, thanks for the advice :-)

---

### Post by qwazert on 2006-08-25
Thank you all, that worked!

**Gksudo Nautilus** did the trick!

---

### Post by harisund on 2006-08-25
Great!

A small side note, watch out what you do with nautilus invoked through gksudo. You could potentially mess up with anything since you are running it as root. 

FuriousLettuce, gk is for gtk apps. I believe there is something similar for QT applications, but I am not really sure.

---

### Post by FuriousLettuce on 2006-08-25
I believe it's kdesu, but I don't use KDE/any QT apps so I could be wrong...

---

### Post by harisund on 2006-08-25
kdesu.. you are right (kde)+(su). 

Thanks :)

---

