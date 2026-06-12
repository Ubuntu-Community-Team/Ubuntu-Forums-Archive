---
title: "dpkg --configure -a"
date: 2007-06-10
forum: Absolute Beginner Talk
---

### Post by ajmannen on 2007-06-10
Hi, when i started the computer today i got this messegde [http://bildr.no/view/73901]("http://bildr.no/view/73901") so i wrote sudo dpkg --configure -a but now my add/remove programs won't work! 

Help plz (and please tell how you figured out the terminal comand, i'm trying to learn terminal;))

---

### Post by gerscht on 2007-06-10
can you still add/remove programs via apt?
try an
```

sudo apt-get update
sudo apt-get upgrade
```
and post any error messages

---

### Post by ajmannen on 2007-06-10
[[img]http://bildr.no/thumb/74418.jpeg[/img]](http://bildr.no/view/74418) 
when i try to run the comand i get "E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem."
 :(

---

### Post by gerscht on 2007-06-10
ehm, your screenshot shows 'udo ...' instead of 'sudo ...'?!
what happens when you run 'dpkg --configure -a', as suggested, any error messages there?

---

### Post by ajmannen on 2007-06-10
i get 
E: Kunne ikke åpne låsefila /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
(yes i typed sudo in front) and the first one means E: unable to open lock file bla bla bla

---

### Post by taurus on 2007-06-10
You need to shut down synaptic first if you have it open before you run that command from a terminal.  

```
sudo dpkg --configure -a
sudo apt-get update
```

---

### Post by gerscht on 2007-06-10
Have a look in your system monitor whether the update manager is running at the moment (it might be downloading updates).
if it's not running (and you're sure!!), you can move the lock file (It might not have been cleared after the last run)
```

sudo mv /var/lib/dpkg/lock /var/lib/dpkg/lock_old

```
and try again (it will create a new lock file).
Let me know how it goes.

---

### Post by ajmannen on 2007-06-10
Now it works, thanks (-:

---

