---
title: "I edited, now how do I save the edits"
date: 2007-01-27
forum: Absolute Beginner Talk
---

### Post by paydaydaddy on 2007-01-27
I made some changes to a .conf file but when I restarted the changes were not saved. (see my post about screen relosution problems). How do I make the changes stick?

---

### Post by smartbei on 2007-01-27
were you running the text editor as root (with sudo) so that you can save?
```
$ sudo gedit /etc/X11/xorg.conf
```

---

### Post by jvc26 on 2007-01-27
How did you open the .conf file? You could try:
```

gksudo gedit /path/to/conf/file/.conf

```
Then make your changes and click save.

It is could well be because you just opened it without the gksudo/sudo command and thus you don't have root permissions to write to the file.
Il

---

### Post by Titus A Duxass on 2007-01-27
Depends on the editor you used.

---

### Post by jvc26 on 2007-01-27
> **smartbei said:**
> were you running the text editor as root (with sudo) so that you can save?
```
$ sudo gedit /etc/X11/xorg.conf
```
Do use gksudo in the instructions you give:
```

gksudo gedit /etc/X11/xorg.conf

```
 although for the most part using sudo for graphical applications will cause no problems, it can actually do a lot of damage: 
"There are other times, though, when side effects can be as mild as Firefox extensions not sticking or as extreme as as not being able to log in any more because the permissions on your .ICEauthority changed" (from: [http://psychocats.net/ubuntu/graphicalsudo](http://psychocats.net/ubuntu/graphicalsudo))

Use gksudo for graphical apps, for terminal apps use sudo.
Il

---

### Post by paydaydaddy on 2007-01-27
I did open it with sudo and gedit, but not gksudo.

---

### Post by jvc26 on 2007-01-27
You can open it with sudo its highly unlikely to cause problems, but as a piece of advice I would use gksudo rather than sudo for graphical apps (as mentioned above) (My comment was to the poster of the instructions :))

Now back to your issue: Had you used the 'sudo/gksudo' command and not been able to save using gedit? (apologies not sure whether I misunderstood your last post)
With gedit all you do is click the 'save' button on the panel.
Il

---

### Post by paydaydaddy on 2007-01-27
It worked and I got my desired resolution back. Thanks to all. It only took about 4 hrs. to get it figured out. I think I'm really starting to get the hang of this Linux stuff!{;^)

---

### Post by jvc26 on 2007-01-27
Excellent :)
Il

---

### Post by PurplePenguin on 2007-01-27
> **paydaydaddy said:**
> It worked and I got my desired resolution back. Thanks to all. It only took about 4 hrs. to get it figured out. I think I'm really starting to get the hang of this Linux stuff!{;^)

It'll take a while, but once you have figured it out, it'll all be worth it. :KS

---

