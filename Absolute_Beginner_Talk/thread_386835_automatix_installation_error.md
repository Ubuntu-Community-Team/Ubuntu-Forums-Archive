---
title: "automatix installation error"
date: 2007-03-17
forum: Absolute Beginner Talk
---

### Post by ajeffreys on 2007-03-17
When I type this into the terminal,

ajeffreys@ajeffreys-laptop:~$ echo "deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) edgy main"
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) edgy main
ajeffreys@ajeffreys-laptop:~$ sudo tee -a /etc/apt/sources.list
wget [http://www.getautomatix.com/apt/key.gpg.asc](http://www.getautomatix.com/apt/key.gpg.asc)
wget [http://www.getautomatix.com/apt/key.gpg.asc](http://www.getautomatix.com/apt/key.gpg.asc)
gpg --import key.gpg.asc
gpg --import key.gpg.asc

It just keeps repeating what I type, and so i am getting no where. Could somebody please tell me what i did wrong.

Ajeffreys

---

### Post by taurus on 2007-03-17
> **ajeffreys said:**
> When I type this into the terminal,

ajeffreys@ajeffreys-laptop:~$ echo "deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) edgy main"
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) edgy main
ajeffreys@ajeffreys-laptop:~$ sudo tee -a /etc/apt/sources.list
wget [http://www.getautomatix.com/apt/key.gpg.asc](http://www.getautomatix.com/apt/key.gpg.asc)
wget [http://www.getautomatix.com/apt/key.gpg.asc](http://www.getautomatix.com/apt/key.gpg.asc)
gpg --import key.gpg.asc
gpg --import key.gpg.asc

It just keeps repeating what I type, and so i am getting no where. Could somebody please tell me what i did wrong.

Ajeffreys

Actually, you want to add this line, deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) edgy main, to your /etc/apt/sources.list.  So, open a terminal, Applications -> Accessories -> Terminal, and type

```
gksudo gedit /etc/apt/sources.list
```
Then, scroll to the end of the file and add this line to it.

```
deb http://www.getautomatix.com/apt edgy main
```
Save the change.  And at the prompt, run

```

wget http://www.getautomatix.com/apt/key.gpg.asc
gpg --import key.gpg.asc
gpg --export --armor 521A9C7C | sudo apt-key add -
sudo aptitude update
sudo aptitude install automatix2
```

It should now be in Applications -> System Tools.

---

### Post by r4ik on 2007-03-17
-

---

### Post by ajeffreys on 2007-03-17
Thanks for the help, it now works flawlessly :)

---

