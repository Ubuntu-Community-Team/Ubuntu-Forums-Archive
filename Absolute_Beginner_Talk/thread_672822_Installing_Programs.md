---
title: "Installing Programs"
date: 2008-01-20
forum: Absolute Beginner Talk
---

### Post by tarrant on 2008-01-20
I also just down loaded flash player in .tar.gz format and i extracted it using archive manager which made it a .so file. Then when I went to install it, it said "No application is known for this kind of file". What do i do?

---

### Post by SunnyRabbiera on 2008-01-20
flash is in the repositories, again i will link you to this page:
[http://monkeyblog.org/ubuntu/installing/]("http://monkeyblog.org/ubuntu/installing/")

also keep in mind this is not a chatroom, please keep your replies in one topic.
I know you want to get things working but you wont do it by being hasty.

your original topic moved down a bit but its still there

---

### Post by Rabindranath on 2008-01-20
Open the tar.gz file. Drag and drop the folder to the desktop. Open the folder and note down the path of the folder. Open the terminal and type "cd <path>". Then type "./flashplayer-installer". :)

---

### Post by jleaker01z on 2008-01-20
> **tarrant said:**
> I also just down loaded flash player in .tar.gz format and i extracted it using archive manager which made it a .so file. Then when I went to install it, it said "No application is known for this kind of file". What do i do?

Click Applications>Add/Remove Applications.  In the upper right where it says "Supported Ubuntu Applications" click that and select "All available applications".  Then search for what you are looking for.  When you find it, check the box beside what you want to install then click Apply or OK.  Pretty much anything you might need can be found and installed in this manner.

---

### Post by aysiu on 2008-01-20
If you are not using 64-bit, installing Flash should be as easy as visiting a page that requires Flash and then following the prompts.

More details here:
[http://www.psychocats.net/ubuntu/flash](http://www.psychocats.net/ubuntu/flash)

---

### Post by SunnyRabbiera on 2008-01-20
> **jleaker01z said:**
> Click Applications>Add/Remove Applications.  In the upper right where it says "Supported Ubuntu Applications" click that and select "All available applications".  Then search for what you are looking for.  When you find it, check the box beside what you want to install then click Apply or OK.  Pretty much anything you might need can be found and installed in this manner.

yes there is this method too, in fact for beginners it is the method to use...

---

### Post by erfahren on 2008-01-20
it actually intends you to use the terminal and change directory into the untarred folder and run the installer (like "./flashplayer-installer")

but... there is a easier way to do this - open Nautilus (the file browser) as root and just paste that file into /usr/lib/firefox/plugins

to do that press Alt+F2 and type in:
```

gksu nautilus

```
you'll get a window that has root premissions (so don't do anything crazy! - lol)

browse to /usr/lib/firefox/plugins and paste the libflashplayer.so file inside there and restart firefox

that's it.

---

### Post by erfahren on 2008-01-20
> **Rabindranath said:**
> Open the tar.gz file. Drag and drop the folder to the desktop. Open the folder and note down the path of the folder. Open the terminal and type "cd <path>". Then type "./flashplayer-installer". :)
there's a little app that I really like for stuff like that - its called "nautilus-open-terminal" (available in Synaptic or "sudo apt-get install nautilus-open-terminal")

anyway - it adds an option to the right-click context menu to open a folder in the terminal  - comes in handy! (Xubuntu's Xfwm has something like that by default).

---

