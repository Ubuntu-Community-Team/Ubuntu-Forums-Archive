---
title: "GNU/Linux Commander (GLC)"
date: 2006-04-26
forum: Absolute Beginner Talk
---

### Post by rameez on 2006-04-26
I am trying to install this sofware GLC that is a file explorer like Total Commander(windows) I have followed these instrutions after downloading and extracting 
```

$./configure --prefix=usr/local
$su
$make install
$logout
$tar -C $Home -xvzf ./homefiles.tar.gz

```
it works uptil here fine without any error then then instructions say to enter
$startx
Under X, in a terminal window run:
$glc

the problem is when I enter startx I get the error:
```
xauth: creating new authority file /home/xxx/.serverauth.12648
X: user not authorized to run the X server, aborting
xinit: Server error
```
I have also tried running this command with sudo but still doenot work.
any help in this matter will be greately appreciated

Thanks.

---

### Post by Nikusan on 2006-04-26
[QUOTE=rameez]I am trying to install this sofware GLC that is a file explorer like Total Commander(windows) I have followed these instrutions after downloading and extracting 
```

$./configure --prefix=usr/local
$su
$make install
$logout
$tar -C $Home -xvzf ./homefiles.tar.gz

```
it works uptil here fine without any error then then instructions say to enter
$startx
Under X, in a terminal window run:
$glc

the problem is when I enter startx I get the error:
```
xauth: creating new authority file /home/xxx/.serverauth.12648
X: user not authorized to run the X server, aborting
xinit: Server error
```
I have also tried running this command with sudo but still doenot work.
any help in this matter will be greately appreciated

Thanks.[/QUOTE]

startx is the command to start the x server, your graphical environment. Try following the instructions but skipping that step.

Is GLC anything like [Gnome Commander]("http://www.nongnu.org/gcmd/")? Gnome Commander is in the repositories so if you can get away with using it instead it will be much easier to install. To install simply:
```
sudo apt-get install gnome-commander
```

---

### Post by htinn on 2006-04-26
I personally prefer Worker and Krusader, but here's a nice chart you can refer to:

[http://en.wikipedia.org/wiki/Comparison_of_file_managers](http://en.wikipedia.org/wiki/Comparison_of_file_managers)

---

### Post by rameez on 2006-04-26
thanks I have installed gnome commander, 
just one more thing how do I uninstall the non working glc now?

I searched for krusader and on synaptic and it says that this utility is for KDE how can I install it on gnome?

---

### Post by htinn on 2006-04-26
KDE and GNOME are just different frameworks for doing UI code. You don't have to go the full desktop environment route to use one or the other.

I use GNOME, and I regularly use K3b, for example. It looks a little different, and there are slightly different rules for how the interface works, but otherwise there is no real difference.

---

