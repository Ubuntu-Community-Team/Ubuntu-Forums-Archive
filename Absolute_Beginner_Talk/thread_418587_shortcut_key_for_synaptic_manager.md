---
title: "shortcut key for synaptic manager?"
date: 2007-04-22
forum: Absolute Beginner Talk
---

### Post by thelegionnaire on 2007-04-22
so i beleive what i did horribly wrong is deleted my desktop packages in SPM and i need to get there, but alas no desktop, how do i get there with just shortcuts? right now i'm in windows, i cant do anything in ubuntu (except take a screenshot :) )

---

### Post by SOULRiDER on 2007-04-22
If you know what you deleted you can install them via the command line. Once youre into GNOME, press ctrl+alt+F1 and youll be in a console. To install a package simply type:

```
 sudo aptitude install <package1> <package2> ...... <packagen>
```

I suggest you install the ubuntu-desktop package, it might fix your problem:

```
sudo aptitude install ubuntu-desktop
```

---

### Post by aysiu on 2007-04-22
You can take a screenshot without a desktop?

Do this: ```
sudo apt-get update
sudo apt-get install ubuntu-desktop
sudo /etc/init.d/gdm restart
```

---

### Post by thelegionnaire on 2007-04-22
ok so when u go to take a screenshot you can access the helpfile, the helpfile had a link to a url, so i am now on firefox in ubuntu.

i cannot run anything

no alt-f3 

cant enter a terminal

i am totally lost

---

### Post by aysiu on 2007-04-22
No Alt-F2 either?

---

### Post by thelegionnaire on 2007-04-22
nope, i am so lost

---

### Post by aysiu on 2007-04-22
What about Control-Alt-F1? Does that take you to a full-screen terminal?

---

### Post by thelegionnaire on 2007-04-22
i could however open a file using firefox, is there a way to enter the terminal through the file manager?

---

### Post by aysiu on 2007-04-22
Yes.

Press Control-L

Go to /usr/bin

Then double-click on *gnome-terminal*

---

### Post by thelegionnaire on 2007-04-22
i dont have it...

---

### Post by thelegionnaire on 2007-04-22
oh and btw ctrl alt f1 worked, but next time how do i get out of it without resetting?

---

### Post by aysiu on 2007-04-22
Control-Alt-F7 will take you back

---

### Post by thelegionnaire on 2007-04-22
can i copy/paste in there?

---

### Post by thelegionnaire on 2007-04-22
nothing happened when typed 
sudo aptitude install ubuntu-desktop

---

### Post by aysiu on 2007-04-22
Nothing?

In other words, this is what you see? ```
thelegionnaire@ubuntu:~$ sudo aptitude install ubuntu-desktop
thelegionnaire@ubuntu:~$ 
``` No errors, not asking for a password--*nothing*?

---

### Post by thelegionnaire on 2007-04-22
oh yes, im sorry it did say some things but when i came back to the gui everything looked the same

also did the get updates and same thing

get updated went through some downloading

---

### Post by aysiu on 2007-04-22
> **thelegionnaire said:**
> oh yes, im sorry it did say some things but when i came back to the gui everything looked the same

also did the get updates and same thing

get updated went through some downloading
Well, it sounds as if there's something wrong with your user profile.

Press Control-Alt-F1, log in, and type ```
sudo adduser testuser
sudo adduser testuser admin
``` The press Control-Alt-F7 to get back to the GUI, Control-Alt-Backspace to reset the X server, and log in as *testuser*

If your test user experiences the same problems, it's a system-wide issue. If not, then there's something wrong with your regular user's /home directory.

---

### Post by thelegionnaire on 2007-04-22
i would be fine with reinstalling ubuntu, as i havent done anything on it as of yet, is there an easy way to reinstall over the same partition?

---

### Post by thelegionnaire on 2007-04-22
made the test user, same problem

---

