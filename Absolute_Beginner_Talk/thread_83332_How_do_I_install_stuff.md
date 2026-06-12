---
title: "How do I install stuff?"
date: 2005-10-28
forum: Absolute Beginner Talk
---

### Post by ramdisc on 2005-10-28
I went to Konsole, and typed in:
```
apt-get install firefox
```
I got returned with a bash error.  Please help.

---

### Post by heimo on 2005-10-28
Try using:
```
sudo apt-get install firefox
```

Or: System->Administration->Synaptic Package Manager

---

### Post by commodore on 2005-10-28
Ok, I have installed stuff with apt-get and synaptic only, but when I need to install something from a package I downloaded through a browser what do I have to do?

---

### Post by Kyral on 2005-10-28
Assuming its a .deb package (it will have the extension .deb and most icon themes will make it look different in Nautilus) you just have to open a terminal, navigate to where you downloaded the package, and do this


```
sudo dpkg -i <nameoffile>
```

---

### Post by JurB on 2005-10-28
there's also [Debinstaller]("http://www.gnomefiles.org/app.php?soft_id=601")
Once installed you can just double click deb's , and they automatically install.

---

### Post by Kyral on 2005-10-28
I suddenly have an idea....to make an Apt-Get For Beginners Guide....hmmm

---

### Post by commodore on 2005-10-28
Deb is the usual package for ubuntu? Are there any other packages I can install from?

---

