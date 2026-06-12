---
title: "vim?how to save"
date: 2007-04-26
forum: Absolute Beginner Talk
---

### Post by STREETURCHINE on 2007-04-26
i have edited a file with  vim, but i just cant workout how to save what i have done,
i have read the man pages but they dont mention saving.

---

### Post by igknighted on 2007-04-26
hit escape to make sure you are not in insert mode, then
```
:wx
```
enter.

EDIT: I have been dying to know, is your username in reference to the book Ender's Shadow?

---

### Post by kevinlyfellow on 2007-04-26
If you want to save it as a different name, hit esc and then

:save filename

---

### Post by eeverson on 2007-04-26
I am not sure :wx works..

i always use

:wq

If you are on insert mode you will need to hit escape to exit that before you can type :

w = write
q = quit

Cheers
Euge

---

### Post by igknighted on 2007-04-26
> **eeverson said:**
> I am not sure :wx works..

i always use

:wq

If you are on insert mode you will need to hit escape to exit that before you can type :

w = write
q = quit

Cheers
Euge

You're probably right... im not normally a vim user, i know just enough to get by on the times nano/pico isn't there :).  Thanks for the correction.

---

### Post by kevinlyfellow on 2007-04-26
edit: I'll make use of my mistake...

:wx doesn't work, but :w and :x works

edit: :x should read ": x" without the space

---

### Post by STREETURCHINE on 2007-04-26
> **igknighted said:**
> hit escape to make sure you are not in insert mode, then
```
:wx
```
enter.

EDIT: I have been dying to know, is your username in reference to the book Ender's Shadow?

no reference what so ever:) 

>  Originally Posted by eeverson  View Post
I am not sure :wx works..

i always use

:wq

If you are on insert mode you will need to hit escape to exit that before you can type :

w = write
q = quit

Cheers
Euge

tried that but it would not let me save it .
any way the problem has esculated a tad ,i tried to edit it using gksudo nautilus ,i draged the sudoers file out to edit it that way ,then it would not let me put it back,then my power went out now i have no sudoers file

---

### Post by eeverson on 2007-04-26
If you have wiped the contents or an error in the sudoers file then use this thread to help recover and edit it...

[http://ubuntuforums.org/showthread.php?t=411646](http://ubuntuforums.org/showthread.php?t=411646)

Cheers
Euge

---

