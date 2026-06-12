---
title: "Moving Home from laptop to desktop"
date: 2006-10-17
forum: Absolute Beginner Talk
---

### Post by jls on 2006-10-17
I am currently running Breezy on my laptop with everything on the one partition, I have just reloaded Dapper on my desktop which I have setup to have home on its own partition. Is there a way to just copy everything from the laptop home to the desktop, if so will this keep all my settings,etc intact and/or will it cause problems if a package is not installed at the time/added later etc etc? TIA

---

### Post by bsussman on 2006-10-17
In principle, you can replicate from the laptop to your desktop with no issues,  assuming the releases are identical and you copy everything in sys1:/home/whatever to sys2:/home/whatever

I recommend that you backup your destination home directory (DO NOT FORGET THE .files) as you will probably find behavior differences and want to get back the original files for something.

nautilus can do this -using an ssh method - in the text bar, ssh://user@remotesys will get you to the remote system, provided you have ssh installed

---

### Post by aysiu on 2006-10-17
I would recommend not messing with something that works.

If you must, make an image back-up first:
[http://www.psychocats.net/ubuntu/partimage](http://www.psychocats.net/ubuntu/partimage)

Honestly, though, you don't need to copy *all* of home, probably. I, for example, would copy over ~/.mozilla, ~/.thunderbird, ~/.icewm, and ~/.gnome2/rhythmbox. The rest I would configure again by hand.

---

### Post by fadder on 2006-10-18
I would use rsync rather than any copy - check this out. One advantage is that it can be safely interrupted, and will just restart from where it left off.

Actually, I use unison (a two-way) rsync, to keep my portable and desktop PCs  identical. Excellent in general. I use unison between each one and an external hard-drive (Maxtor). Life has been much easier, faster, and a lot safer since  discovered both rsync and unison.

---

### Post by Mimsy on 2006-10-18
Aplogies for hijacking the thread a little bit, but would you mind sharing a link or two to where I can learn a bit more about rsync and unison?

Thanks,
Mimsy

---

### Post by aysiu on 2006-10-18
[Here's a link](http://www.ubuntuforums.org/showthread.php?t=209724&highlight=hype+rsync) for *rsync*.

---

### Post by jd65pl on 2006-10-18
[Here is]("http://www.linuxjournal.com/article/7712") some info on unison

---

### Post by Mimsy on 2006-10-18
Thanks! I'll check out all that info as soon as I get home tonight. 

/Mimsy

---

### Post by Mimsy on 2006-10-18
Now that I've looked at both of them, I tink rsync is closer to what I need than unison. I just want to make backups of what is on thelaptop, and rsync can do that. I installed the graphic frontend in Synaptic, and it's working out magnificently so far.

So thanks again! I had no idea how badly I needed a quick and easy way to make backups. :)

/Mimsy

---

