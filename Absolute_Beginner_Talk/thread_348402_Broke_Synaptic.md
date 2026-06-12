---
title: "Broke Synaptic?"
date: 2007-01-28
forum: Absolute Beginner Talk
---

### Post by Daemion_AF on 2007-01-28
Ok so i was trying to load the deb [http://www.albertomilone.com/drivers/dapper/latest/32bit](http://www.albertomilone.com/drivers/dapper/latest/32bit) binary/ repository. After clicking add > custom and copy and pasting this link i can no longer access my add/remove link under applications. when i type the command line this is what i get. What did I break now?
daemion@daemion-laptop:~$ sudo apt-get update
E: Malformed line 33 in source list /etc/apt/sources.list (dist parse)

---

### Post by taurus on 2007-01-28
Let's have a look at your /etc/apt/sources.list.  Open a terminal and paste the output here.

```
cat /etc/apt/sources.list
```

---

### Post by Daemion_AF on 2007-01-28
deb-src [http://mx.archive.ubuntu.com/ubuntu/](http://mx.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://mx.archive.ubuntu.com/ubuntu/](http://mx.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://mx.archive.ubuntu.com/ubuntu/](http://mx.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb-src [http://mx.archive.ubuntu.com/ubuntu/](http://mx.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://mx.archive.ubuntu.com/ubuntu/](http://mx.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
# deb-src [http://mx.archive.ubuntu.com/ubuntu/](http://mx.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper multiverse universe main restricteddeb [http://www.albertomilone.com/drivers/dapper/latest/32bit](http://www.albertomilone.com/drivers/dapper/latest/32bit) binary

---

### Post by taurus on 2007-01-28
You need to break the last long line into two separate lines.

```

deb http://archive.ubuntu.com/ubuntu/ dapper multiverse universe main restricted
deb http://www.albertomilone.com/drivers...r/latest/32bit binary

```

---

### Post by Daemion_AF on 2007-01-28
> **taurus said:**
> You need to break the last long line into two separate lines.

```

deb http://archive.ubuntu.com/ubuntu/ dapper multiverse universe main restricted
deb http://www.albertomilone.com/drivers...r/latest/32bit binary

```

I think that is just a pasting error on my part no? It is two seperate lines in the terminal.

---

### Post by taurus on 2007-01-28
What does the last line look like anyway because that's what it's complaining about?

---

### Post by Daemion_AF on 2007-01-28
deb [http://www.albertomilone.com/drivers/dapper/latest/32bit](http://www.albertomilone.com/drivers/dapper/latest/32bit) binary

---

### Post by taurus on 2007-01-28
Should be like this.

```

deb http://www.albertomilone.com/drivers/dapper/latest/32bit binary/

```

---

### Post by MkfIbK7a on 2007-01-28
erm daemon can you deit that post press go advanced and uncheck 

automatically parse links in text 

by the bottom of the message?

that way we can see the entire thing

---

### Post by taurus on 2007-01-28
> **wert613 said:**
> erm daemon can you deit that post press go advanced and uncheck 

automatically parse links
 in text by the bottom of the message?

that way we can see the entire thing

Just put the cursor over it and you can see the whole thing.

---

### Post by MkfIbK7a on 2007-01-28
ah thx taurus

apparently hes missing the slash at the end...

---

### Post by Daemion_AF on 2007-01-28
Any idea how to fix it at the terminal?

---

### Post by taurus on 2007-01-28
```
gksudo gedit /etc/apt/sources.list
```
or
```
sudo nano -w /etc/apt/sources.list
```

---

### Post by Daemion_AF on 2007-01-28
sweet that got it...hmmmm i copied it from the site i guess i just missed the /. Ok now i will try to get that ATI driver again. Thanks alot!

---

### Post by MkfIbK7a on 2007-01-28
no problem

---

### Post by Hedghg88 on 2007-03-01
Thanks, this just fixed my problem also, lol, week 2 of Ubuntu drapper drake.

---

