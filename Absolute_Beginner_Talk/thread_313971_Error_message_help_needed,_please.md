---
title: "Error message help needed, please"
date: 2006-12-06
forum: Absolute Beginner Talk
---

### Post by L Campbell on 2006-12-06
I received the following message from the 'update icon' at the top of the screen.

>>>>>
An error occurred, please run Package Manager from the right click menu or apt-get on a terminal to see what is wrong.
The error message was: 'Error: Opening the cache  '(E: Malformed line 8 in source list /etc/apt/sources.list (dist).  E: The list of sources could not be read.)'
<<<<<

Although I have tried both apt-get and Package Manager, I can't see what the error is, or how to fix it.

If someone would favor me with a suggestion, I'd really appreciate it.

---

### Post by sabelsen on 2006-12-06
Let's have a look at you /etc/apt/sources.list file. The error message states that something is wrong with line 8 in that file. Can you paste its content for us?

---

### Post by L Campbell on 2006-12-07
> **sabelsen said:**
> Let's have a look at you /etc/apt/sources.list file. The error message states that something is wrong with line 8 in that file. Can you paste its content for us?

Hi, thanks for your interest.

This is all I could get:-

sudo: /etc/apt/sources.list: command not found

Kind regards.

---

### Post by Scorpuk on 2006-12-07
You need to edit the file so you can see whats in it. Its not a command.

Type


```
sudo gedit /etc/apt/sources.list
```

and then post whats in the file. :)

---

### Post by Bachstelze on 2006-12-07
/etc/apt/sourceS.list is not a command but a file, you neet to open it in a text editor, e.g. :

gksudo gedit /etc/apt/sources.list

---

### Post by L Campbell on 2006-12-07
> **Scorpuk said:**
> You need to edit the file so you can see whats in it. Its not a command.

Type


```
sudo gedit /etc/apt/sources.list
```

and then post whats in the file. :)

Oops!!!!    :-)

Thanks for pointing this out.

This is exatly how it came to me:-

## Uncomment the following two lines to fetch updated software from the network
deb http:archive.ubuntu.com/ubuntu dapper main restricted
deb-src http:archive.ubuntu.com/ubuntu dapper main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb http:archive.ubuntu.com/ubuntu dapper-updates main restricted
deb-src http:


















archive.ubuntu.com/ubuntu dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main

deb [http://packages.freecontrib.org/plf/](http://packages.freecontrib.org/plf/) dapper free non-free
deb-src [http://packages.freecontrib.org/plf/](http://packages.freecontrib.org/plf/) dapper free non-free
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe

deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) dapper main

---

### Post by kakalaky on 2006-12-07
Remove the huge chunk of whitespace between line 8:

```
deb-src http:
```

and the next line:

```
archive.ubuntu.com/ubuntu dapper-updates main restricted
```

so that the line looks like this:

```
deb-src http:archive.ubuntu.com/ubuntu dapper-updates main restricted
```

---

### Post by L Campbell on 2006-12-07
> **kakalaky said:**
> Remove the huge chunk of whitespace between line 8:

```
deb-src http:
```

and the next line:

```
archive.ubuntu.com/ubuntu dapper-updates main restricted
```

so that the line looks like this:

```
deb-src http:archive.ubuntu.com/ubuntu dapper-updates main restricted
```

OK, thanks, I appreciate it.

I did as you suggested, re-booted and the error warning has gone away.

---

