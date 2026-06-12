---
title: "Trouble installing scripts (Please help!)"
date: 2007-03-28
forum: Absolute Beginner Talk
---

### Post by JimmyHopkins on 2007-03-28
I can't seem to figure out how to install scripts. Specifically, I need an open-terminal-here script, to help install packages from source. However, this script I found here ([http://g-scripts.sourceforge.net/nautilus-scripts/Execute/Open%20terminal/Open%20Terminal%20Here]("http://g-scripts.sourceforge.net/nautilus-scripts/Execute/Open%20terminal/Open%20Terminal%20Here"). It's just plain text. In detail (I'm only 2 months off of windows!), could someone help me?


Thanks in advance!

---

### Post by h0ax on 2007-03-28
you will want to install this:
[B]nautilus-open-terminal

[/B]do ```
sudo apt-get install nautilus-open-terminal
```Now when you're browsing in nautilus you will have the option.
See screenshot:

---

### Post by nanotube on 2007-03-29
in general, to install nautilus scripts, just take the script, and place it into ~/.gnome2/nautilus-scripts directory (where ~ stands for your home dir).
don't forget to make the script executable (right click, go to permissions, check the box)

then, the script will show up in your right-click menu, under "Scripts"

the previously suggested solution works too, for the particular case of the terminal, but if you want to install scripts, generally, this is the way to go.

---

### Post by h0ax on 2007-03-29
> **nanotube said:**
> 
don't forget to make the script executable (right click, go to permissions, check the box)


or alternatively if you move the file to that directory via the terminal you can change the permission to executable by typing 
```
sudo chmod +x scriptname.whatever
```

---

### Post by JimmyHopkins on 2007-03-29
I appriciate it, but I have another question. please go to my specific link. It's just text. When I right click and download it, it saves as html. How do I save a bunch of random text to a script? Gedit? If so, what kind of fime format (.txt,.sh, whatever). this is just for future purposes.

Thanks again!

---

### Post by zvacet on 2007-03-29
[http://doc.gwos.org/index.php/Nautilus_Scripts]("http://doc.gwos.org/index.php/Nautilus_Scripts")

---

### Post by nanotube on 2007-03-29
> **JimmyHopkins said:**
> I appriciate it, but I have another question. please go to my specific link. It's just text. When I right click and download it, it saves as html. How do I save a bunch of random text to a script? Gedit? If so, what kind of fime format (.txt,.sh, whatever). this is just for future purposes.

Thanks again!

just copy the text of the script, and save it to a plain text file with gedit. file extension doesn't matter to the computer, that is purely for human preferences :) so you might as well save it as a .sh to indicate that it's a script, but if you wanted to, you could do whatever. as long as it actually /is/ a plain text file.

---

