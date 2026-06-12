---
title: "what does this error message means"
date: 2007-09-07
forum: Absolute Beginner Talk
---

### Post by rahul_bhise on 2007-09-07
yesterday there was a notification icon telling me to update some packages. they were all marked security up dates (i have a screen shot attached) but while updating there was an error message which i did not understand. can anyone help me on this

---

### Post by thelocust on 2007-09-07
Any time this kind of stuff happens I do a 

```
sudo dpkg --configure -a
```
That usually takes care of things.

---

### Post by rahul_bhise on 2007-09-08
no this didn't solve the problem. same error is shown while updating this 3 updates

---

### Post by diatribe on 2007-09-08
try sudo apt-get install -f

---

### Post by rahul_bhise on 2007-09-09
this did not solve the problem the output of the terminal is

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libofx3 libosp5
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
```

---

### Post by rahul_bhise on 2007-09-12
can i cancel this update so it does not keep showing up on every login

---

### Post by stmiller on 2007-09-12
Just do
```

sudo apt-get autoremove

``````

sudo apt-get autoclean

```

---

### Post by rahul_bhise on 2007-09-14
no this did not solve the problem
i think this is something to do with the postfix package should i uninstal it through syneptic manager i think it is used to send mail (i think i can do without it)

---

### Post by SOULRiDER on 2007-09-14
Try:
```
sudo aptitude update
sudo aptitude dist-upgrade
```

See what happens.

---

### Post by rahul_bhise on 2007-09-14
this was the output of the second comand
```
brahul@uhome:~$ sudo aptitude dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done      
The following packages will be upgraded:
  libkadm55 libkrb5-dev libkrb53 
3 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/1261kB of archives. After unpacking 0B will be used.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
dpkg: syntax error: unknown user `postfix' in statoverride file 
E: Sub-process /usr/bin/dpkg returned an error code (2)
A package failed to install.  Trying to recover:
```

---

### Post by SOULRiDER on 2007-09-14
I googled and found this:
[http://calizdemana.blogspot.com/2007/07/error-al-instalar-con-apt-get.html](http://calizdemana.blogspot.com/2007/07/error-al-instalar-con-apt-get.html) Its in spanish but theys ay the solution is:
```
sudo groupadd postdrop
sudo useradd postfix
```
Also, check this link out before doing anything:
[http://ubuntuforums.org/showthread.php?t=329560](http://ubuntuforums.org/showthread.php?t=329560)

---

### Post by rahul_bhise on 2007-09-15
the thread [http://ubuntuforums.org/showthread.php?t=329560](http://ubuntuforums.org/showthread.php?t=329560) did help
though i did not understand what i did but it did solved the problem

---

### Post by Tecguy2 on 2007-09-15
Congrats for fixing it:)

---

