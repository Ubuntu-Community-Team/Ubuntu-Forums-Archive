---
title: "Installing crossover?"
date: 2007-05-07
forum: Absolute Beginner Talk
---

### Post by mech7 on 2007-05-07
I get this error when i am trying to install the trial of crossover does anybody know what to do :confused: 

[IMG]http://img64.imageshack.us/img64/5989/screenshotinstallcrossoob6.png[/IMG]

---

### Post by taurus on 2007-05-07
Are you not supposed to open it with gedit.  You suppose to run it to install it.

Open a terminal, Applications -> Accessories -> Teminal, and run

```
cd ~/Desktop
chmod 755 install-crossover-standard-demo-6.0.1.sh
sudo ./install-crossover-standard-demo-6.0.1.sh
```

---

### Post by mech7 on 2007-05-07
> **taurus said:**
> Are you not supposed to open it with gedit.  You suppose to run it to install it.

Open a terminal, Applications -> Accessories -> Teminal, and run

```
cd ~/Desktop
chmod 755 install-crossover-standard-demo-6.0.1.sh
sudo ./install-crossover-standard-demo-6.0.1.sh
```

Now i am getting a new error 0_o

> chris@chris-laptop:~$ cd Desktop
chris@chris-laptop:~/Desktop$ chmod 755 install-crossover-standard-demo-6.0.1.shchris@chris-laptop:~/Desktop$ sudo ./install-crossover-standard-demo-6.0.1.sh
Verifying archive integrity...OK
Uncompressing CrossOver Linux Standard
....................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................
The '/home/chris' directory does not belong to you.
Point $HOME to your home directory and try again.
chris@chris-laptop:~/Desktop$ 


---

### Post by taurus on 2007-05-07
Okay, run it without the sudo then.

```
./install-crossover-standard-demo-6.0.1.sh
```

---

