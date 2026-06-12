---
title: ".rar problem"
date: 2005-07-04
forum: Absolute Beginner Talk
---

### Post by SteExp on 2005-07-04
i have a lot of problem with .rar file.
I can't extract this files. i install rar and unrar... and don't working...
Someone, with Ubuntu 5.0.4, use rar format?

best regards,
Stefano

---

### Post by aragorn2909 on 2005-07-04
have you tried this?

```
sudo apt-get install unrar-nonfree
```

---

### Post by bored2k on 2005-07-04
[QUOTE=SteExp]i have a lot of problem with .rar file.
I can't extract this files. i install rar and unrar... and don't working...
Someone, with Ubuntu 5.0.4, use rar format?

best regards,
Stefano[/QUOTE]
 Install rar and unrar-nonfree.
If you have a passwd protected rar, in a terminal use rar e rarfile.rar to extract.

---

### Post by SteExp on 2005-07-04
[QUOTE=aragorn2909]have you tried this?

```
sudo apt-get install unrar-nonfree
```[/QUOTE]


yes aragorn, i've already tried this command line...

And this was the error:

E: Impossible to obtain the lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?



you know why give me this error?

---

### Post by bored2k on 2005-07-04
[QUOTE=SteExp]yes aragorn, i've already tried this command line...

And this was the error:

E: Impossible to obtain the lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?



you know why give me this error?[/QUOTE]
 Because you can't two programs use apt at the same time. Close synaptic and-or any other apt process other than the one you're using.

---

### Post by SteExp on 2005-07-04
[QUOTE=bored2k]Because you can't two programs use apt at the same time. Close synaptic and-or any other apt process other than the one you're using.[/QUOTE]

i've not other process in use with apt now...
How can i make me sure that i haven't some apt process activated?

Thanks a lot

---

### Post by bored2k on 2005-07-04
[QUOTE=SteExp]i've not other process in use with apt now...
How can i make me sure that i haven't some apt process activated?

Thanks a lot[/QUOTE]
 You have to be doing something.. try loggin in-out to make sure everything is closed.

---

### Post by SteExp on 2005-07-04
[QUOTE=bored2k]You have to be doing something.. try loggin in-out to make sure everything is closed.[/QUOTE]

I try to loggin in-out, i try to reboot, but i can't install unrar-nonfree...
Obviously you use Ubuntu, right?
You have some problem with .rar files?


Thanks a lot

---

### Post by poofyhairguy on 2005-07-04
[QUOTE=SteExp]I try to loggin in-out, i try to reboot, but i can't install unrar-nonfree...
Obviously you use Ubuntu, right?
You have some problem with .rar files?


Thanks a lot[/QUOTE]

Try installing unrar in synaptic.

---

### Post by bored2k on 2005-07-04
[QUOTE=SteExp]I try to loggin in-out, i try to reboot, but i can't install unrar-nonfree...
Obviously you use Ubuntu, right?
You have some problem with .rar files?


Thanks a lot[/QUOTE]
 I actually don't have any problems with rar files. If you still can't figure it out (ubuntuguide.org), install wine then install winrar through it.

---

### Post by aragorn2909 on 2005-07-05
I'm just curious SteExp, were you attempting to install through synaptic, or through the command line?

---

### Post by SteExp on 2005-07-06
I can't find unrar in Knaptik.

Aragorn, i use both methods.

---

### Post by SteExp on 2005-07-09
I resolved my problem.
i add this line: "deb [http://ftp.it.debian.org/debian/](http://ftp.it.debian.org/debian/) unstable main contrib non-free"
in /etc/apt/sources.list

sudo nano /etc/apt/sources. list

add line in the end of the souces.list

save and exit

apt-get update

apt-get install unrar

after installation remodify the sources.list file, put # before "deb [http://ftp.it.debian.org/debian/](http://ftp.it.debian.org/debian/) unstable main contrib non-free" (#deb [http://ftp.it.debian.org/debian/](http://ftp.it.debian.org/debian/) unstable main contrib non-free)

another time apt-get update

now try unrar


;)

---

### Post by Wordcrasher on 2007-01-12
Great, that worked, but does this mean ?  There is no unrar stable version available ?!?

---

