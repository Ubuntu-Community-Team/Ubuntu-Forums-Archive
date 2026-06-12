---
title: "Startupmanager problems"
date: 2007-06-22
forum: Absolute Beginner Talk
---

### Post by phil66 on 2007-06-22
(startupmanager:9553): Gtk-WARNING **: Locale not supported by C library.
        Using the fallback 'C' locale.
Traceback (most recent call last):
  File "/usr/bin/startupmanager", line 45, in ?
    locale.setlocale(locale.LC_ALL, '')
  File "/usr/lib/python2.4/locale.py", line 381, in setlocale
    return _setlocale(category, locale)
locale.Error: unsupported locale setting

Downloaded Startupmanager and installed on Ubuntu Dapper

Used debi to install. Program listed in systems>administration as startup manager
When clicked nothing happens program will not load

Attempted to start from terminal and got the error listed at the beginning of the thread
This locale not supported by c library error also shows up on other terminal commands

Is there a workaround to this bug not yet fixed by Ubuntu

Thanks for the help

Ray

---

### Post by DBStevens on 2007-06-22
Please post the result of:

set | grep LC

---

### Post by phil66 on 2007-06-22
ray@ray-desktop:~$ sudo set grep LC
sudo: set: command not found
ray@ray-desktop:~$

---

### Post by phil66 on 2007-06-22
ray@ray-desktop:~$ set | grep lc
                                lcase notrunc ucase swab noerror sync'         -- $cur ));
        oocalc)
            COMPREPLY=($( compgen -W 'chomp chop chr crypt hex index lc \
            lcfirst length oct ord pack q qq reverse rindex sprintf \
ray@ray-desktop:~$

---

### Post by DBStevens on 2007-06-22
Ray,

Would you please retry that with LC instead of lc Linux is case sensitve.

Thanks

---

### Post by phil66 on 2007-06-22
ray@ray-desktop:~$ set | grep LC
MAILCHECK=60
ray@ray-desktop:~$

---

### Post by DBStevens on 2007-06-22
You might want to check the version of start up manager you installed:

[http://web.telia.com/~u88005282/sum/index.html](http://web.telia.com/~u88005282/sum/index.html)

Tell the story of a few issues along with instructions.

The locale error message is a warning and not the reason for your primary problem.

Be certain to get the correct version for the flavor of Ubuntu you are running.

I don't have it installed on my system at all.

---

### Post by DBStevens on 2007-06-22
The locale warning is frequently caused by an incorrect value being set for one of the locale variables.  These are normally set at install time.

man locale provides a list of them that is why I asked you to run a grep on the output of set.

---

### Post by phil66 on 2007-06-22
I have version 1.0.2-2 which is for Dapper and earlier

Thanks for the help

Ray

---

### Post by DBStevens on 2007-06-22
Do you also have usplash installed?

---

### Post by phil66 on 2007-06-22
Yes version 0.2-4

It was installed when Dapper was installed

Ray

---

### Post by DBStevens on 2007-06-23
Ray,

What follows is the result of running locale on my system. 

~$ locale
LANG=en_US.UTF-8
LC_CTYPE="en_US.UTF-8"
LC_NUMERIC="en_US.UTF-8"
LC_TIME="en_US.UTF-8"
LC_COLLATE="en_US.UTF-8"
LC_MONETARY="en_US.UTF-8"
LC_MESSAGES="en_US.UTF-8"
LC_PAPER="en_US.UTF-8"
LC_NAME="en_US.UTF-8"
LC_ADDRESS="en_US.UTF-8"
LC_TELEPHONE="en_US.UTF-8"
LC_MEASUREMENT="en_US.UTF-8"
LC_IDENTIFICATION="en_US.UTF-8"
LC_ALL=
~$ 

The above information may help in fixing the error mesage:

 locale.Error: unsupported locale setting

---

### Post by phil66 on 2007-06-23
ray@ray-desktop:~$ locale
locale: Cannot set LC_ALL to default locale: No such file or directory
LANG=en_US.UTF-8
LANGUAGE=en                 ********
LC_CTYPE="en_US.UTF-8"
LC_NUMERIC="en_US.UTF-8"
LC_TIME="en_US.UTF-8"
LC_COLLATE="en_US.UTF-8"
LC_MONETARY="en_US.UTF-8"
LC_MESSAGES="en_US.UTF-8"
LC_PAPER="en_US.UTF-8"
LC_NAME="en_US.UTF-8"
LC_ADDRESS="en_US.UTF-8"
LC_TELEPHONE="en_US.UTF-8"
LC_MEASUREMENT="en_US.UTF-8"
LC_IDENTIFICATION="en_US.UTF-8"
LC_ALL=
ray@ray-desktop:~$

***** I have one entry more than you "language=en"
Also the locale:cannot set LC_All to default locale: no such file or directory

Ray

---

### Post by DBStevens on 2007-06-23
Ray,

Try running

unset LANGUAGE 

Then doing the locale comand again.

---

### Post by phil66 on 2007-06-23
Ran unset LANGUAGE 

No response terminal went back to home position

Tried unset LANGUAGE=en 

response was invalid identifier

Locale did not change still showing LANGUAGE=en

Ray

---

### Post by phil66 on 2007-06-23
ray@ray-desktop:~$ unset LANGUAGE
ray@ray-desktop:~$
ray@ray-desktop:~$ sudo unset LANGUAGE
Password:
sudo: unset: command not found
ray@ray-desktop:~$
ray@ray-desktop:~$ unset LANGUAGE=en
bash: unset: `LANGUAGE=en': not a valid identifier
ray@ray-desktop:~$
ray@ray-desktop:~$ unset language
ray@ray-desktop:~$
ray@ray-desktop:~$ locale
locale: Cannot set LC_ALL to default locale: No such file or directory
LANG=en_US.UTF-8
LC_CTYPE="en_US.UTF-8"
LC_NUMERIC="en_US.UTF-8"
LC_TIME="en_US.UTF-8"
LC_COLLATE="en_US.UTF-8"
LC_MONETARY="en_US.UTF-8"
LC_MESSAGES="en_US.UTF-8"
LC_PAPER="en_US.UTF-8"
LC_NAME="en_US.UTF-8"
LC_ADDRESS="en_US.UTF-8"
LC_TELEPHONE="en_US.UTF-8"
LC_MEASUREMENT="en_US.UTF-8"
LC_IDENTIFICATION="en_US.UTF-8"
LC_ALL=
ray@ray-desktop:~$

---

### Post by DBStevens on 2007-06-23
Ok now let us try the following

unset LC_ALL    

followed by a 

locale

---

### Post by phil66 on 2007-06-23
ray@ray-desktop:~$ unset LC_ALL
ray@ray-desktop:~$ locale
locale: Cannot set LC_ALL to default locale: No such file or directory
LANG=en_US.UTF-8
LANGUAGE=en
LC_CTYPE="en_US.UTF-8"
LC_NUMERIC="en_US.UTF-8"
LC_TIME="en_US.UTF-8"
LC_COLLATE="en_US.UTF-8"
LC_MONETARY="en_US.UTF-8"
LC_MESSAGES="en_US.UTF-8"
LC_PAPER="en_US.UTF-8"
LC_NAME="en_US.UTF-8"
LC_ADDRESS="en_US.UTF-8"
LC_TELEPHONE="en_US.UTF-8"
LC_MEASUREMENT="en_US.UTF-8"
LC_IDENTIFICATION="en_US.UTF-8"
LC_ALL=
ray@ray-desktop:~$

---

### Post by DBStevens on 2007-06-23
Ray,

You have a PM.  I'll be gone for a couple of hours but will be back by 8:00 PM Eastern.

---

