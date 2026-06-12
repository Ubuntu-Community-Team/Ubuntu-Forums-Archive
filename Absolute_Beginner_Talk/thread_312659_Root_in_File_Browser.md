---
title: "Root in File Browser?"
date: 2006-12-04
forum: Absolute Beginner Talk
---

### Post by i8bugs on 2006-12-04
Because I am weak on terminal commands, I need some way to be root in the File Browser.  I'm an ex-Xandros user and it was easy to do in Xandros.  I tried to copy files from my CD into a quake3 file and I kept getting "file does not exist" when I know it does.  

Using UBUNTU Edgy (Actually it's the linuxmint version).
VR,
bugs

---

### Post by 23meg on 2006-12-04
```
gksudo nautilus
```will launch Nautilus as root.

---

### Post by drphilngood on 2006-12-04
You might want to try Gnome Commander as well.  It allows you root in two windows, side by side, so you can easily transfer files between the two.

Just see here:

[Gnome Commander]("http://www.nongnu.org/gcmd/")

---

### Post by i8bugs on 2006-12-04
> **drphilngood said:**
> You might want to try Gnome Commander as well.  It allows you root in two windows, side by side, so you can easily transfer files between the two.

Just see here:

[Gnome Commander]("http://www.nongnu.org/gcmd/")

OK I got Gnome Commander installed, but it still won't allow me to drag and drop files without a login, and I cannot find the root permission login for commander.  I even tried the command line an the bottom of the page...no joy.
**Recommendations??**
VR,
the bugs

---

### Post by i8bugs on 2006-12-04
OK I took 23megs advice and that appears to be where I want to go.  Still mystified about commander.
Thanks

---

### Post by i8bugs on 2006-12-04
> **23meg said:**
> ```
gksudo nautilus
```will launch Nautilus as root.

Is there a way to program that into an menu Icon so it will launch/login/execute program?
bugs//

---

### Post by ciscosurfer on 2006-12-04
Go to System > Preferences > Menu Layout and place a new entry wherever you like.  You can also create a launcher on the desktop or place one on your panel.

---

### Post by Cardmaster91 on 2006-12-05
> **i8bugs said:**
> Is there a way to program that into an menu Icon so it will launch/login/execute program?
bugs//

you could also open up the file manager, tthen just right click>scripts>nautilus

---

### Post by ciscosurfer on 2006-12-05
> **Cardmaster91 said:**
> you could also open up the file manager, tthen just right click>scripts>nautilusYou must create or install these scripts.

---

### Post by drphilngood on 2006-12-06
> **i8bugs said:**
> OK I got Gnome Commander installed, but it still won't allow me to drag and drop files without a login, and I cannot find the root permission login for commander.  I even tried the command line an the bottom of the page...no joy...

I´m not sure I understand you.  Did you launch it in terminal like so:

```
gksudo gnome-commander
```

---

### Post by i8bugs on 2006-12-09
Thank-you this worked and was very helpful.. You are all great!

---

### Post by i8bugs on 2006-12-10
> **drphilngood said:**
> I´m not sure I understand you.  Did you launch it in terminal like so:

```
gksudo gnome-commander
```

That worked well.  Got that added to my menu...thanks!

---

