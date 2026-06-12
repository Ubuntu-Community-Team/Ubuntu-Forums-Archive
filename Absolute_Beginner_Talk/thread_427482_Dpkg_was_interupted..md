---
title: "Dpkg was interupted."
date: 2007-04-29
forum: Absolute Beginner Talk
---

### Post by naughtywill on 2007-04-29
This is what I get when I try to use synaptic or terminal. I cant do anything with it. I tried google and the other forums and I still can't seem to fix it.  Any assistance fixing this issue would be greatly appreciated.[IMG]http://img102.mytextgraphics.com/photolava/2007/04/29/screenshot-46b1ys0j4.png[/IMG]

---

### Post by taurus on 2007-04-29
What's the error message when you run these two commands form a terminal?

```
sudo aptitude update
sudo aptitude upgrade
```

---

### Post by naughtywill on 2007-04-29
> **taurus said:**
> What's the error message when you run these two commands form a terminal?

```
sudo aptitude update
sudo aptitude upgrade
```
[IMG]http://img106.mytextgraphics.com/photolava/2007/04/29/screenshot-46b26230a.png[/IMG]

---

### Post by taurus on 2007-04-29
Try

```
sudo dpkg --configure -a
sudo aptitude update
sudo aptitude upgrade
```

---

### Post by naughtywill on 2007-04-29
> **taurus said:**
> Try

```
sudo dpkg --configure -a
sudo aptitude update
sudo aptitude upgrade
```
[IMG]http://img106.mytextgraphics.com/photolava/2007/04/29/screenshot-46b289c66.png[/IMG]

---

### Post by Sef on 2007-05-02
Try this from[ debianhelp]("http://www.debianhelp.co.uk/pkgadm.htm") in the UK:

```

sudo aptitude -f install
sudo dpkg --configure -a
sudo aptitude update
sudo aptitude upgrade
```

---

