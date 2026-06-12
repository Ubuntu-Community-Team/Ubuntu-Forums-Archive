---
title: "Celestia controls?"
date: 2006-08-19
forum: Absolute Beginner Talk
---

### Post by georgetoon on 2006-08-19
I installed Celestia and it runs, but here are the controls? i can't find any controls.  i tried adding he gnome front end and the KDE front end thinking this would solve the problem, but to no avail.  Is there a keyboard command which will bring up the controls?

---

### Post by taurus on 2006-08-19
Do you mean by moving around when celestia is running?  Look at the bottom left corner...

---

### Post by georgetoon on 2006-08-19
> **taurus said:**
> Do you mean by moving around when celestia is running?  Look at the bottom left corner...

I looked. Nothing there except speed readout.

how do I cotrol this program? In Linspire, there'sa browser that comes right up and I can go to any planet/star inthe system.

I've tried right clicking, left clicing, two button clicking, etc. nothing happens.

---

### Post by taurus on 2006-08-19
See the help command...

```
celestia --help
```

---

### Post by georgetoon on 2006-08-19
> **taurus said:**
> See the help command...

```
celestia --help
```

Thanks.  I typed this in terminal. Not much help.  It just gave me options for other help menus for KDE, etc.

And there's no place to find help in Celestia.

---

### Post by taurus on 2006-08-19
I am at home right now and my Ubuntu is in the office so I can't play around with it to tell you how to do it but if you can send me the output of that command again, celestia --help, maybe I can give you a hint!!!

---

### Post by georgetoon on 2006-08-19
Whoa!  I typed "Celestia" in terminal and up came the most current version of Celestia, controls and all! Woo-hoo!:)

Obviously, I have the wrong version of Celestia  installed (along with the correct version). I'm gonna have to sort this out.

Is there any way I can link the proper Celestia in the menu?

---

### Post by taurus on 2006-08-19
How did you get two versions of celestia on your system???

---

### Post by georgetoon on 2006-08-19
I went into Alacarte Menu Editor and changed the command from "celestia-glut" to "celestia" and Celestia for KDE (with controls) comes up and runs nicely.:)

Thank you for your help and input.:)


The only thing I may (or may not) do is uninstall the other versions.

---

### Post by taurus on 2006-08-19
You can find where are those two versions of celestia on your machine.  Then run each one (with complete path) to see which version is the latest...

```

sudo find -/ name celestia -print

```

---

### Post by georgetoon on 2006-08-19
Thanks. the command does not work.  I copied and psted and re-typed exactly. It's giving me:

find: invalid predicate `-/'

---

### Post by andlinux21 on 2006-08-19
The software looks pretty sweet do you use it for teaching?

---

### Post by taurus on 2006-08-19
Sorry.  Got the - in the wrong spot...  ](*,) 

```

sudo find / -name celestia -print

```
There is also a stellarium in case you want to check it out...

---

### Post by andlinux21 on 2006-08-20
I installed it today that is some sweet software I hope to set up some Ubuntu or Edbunutu PCs in a daycare/after school facility no more than 10 PCs this would be a great add.

---

### Post by nalmeth on 2006-08-20
man celestia 
has all the details

---

