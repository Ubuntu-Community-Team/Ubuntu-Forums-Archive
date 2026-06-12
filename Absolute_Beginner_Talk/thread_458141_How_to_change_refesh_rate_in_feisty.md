---
title: "How to change refesh rate in feisty?"
date: 2007-05-29
forum: Absolute Beginner Talk
---

### Post by pablo66 on 2007-05-29
I am trying to change my refresh rate running feisty from 50hz to 60hz(the native refresh rate) and when I open: /etc/X11/xorg.conf the file is empty, nothing in it, nada.

---

### Post by Pragmatist on 2007-05-29
Please post output:
```
ls -l /etc/X11
```

---

### Post by Smu on 2007-05-29
Try this:

1. Ctrl + Alt + F1
This will open upp a non-graphical session. To get back to the gnome-desktop and your current session -> Ctrl + Alt + F7

2. Login
3. sudo dpkg-reconfigure xserver-xorg
4. fill in the information of your monitor
5. Ctrl + Alt + F7
6. Ctrl + Alt + Backspace (restart x)


Worked for me when I had problems with my monitor...

---

### Post by pablo66 on 2007-05-31
my output from ls -l /etc/X11:

paul@paul-laptop:~$ ls -l /etc/X11
total 76
drwxr-xr-x 2 root root  4096 2007-05-18 00:27 app-defaults
drwxr-xr-x 2 root root  4096 2007-05-18 00:22 cursors
-rw-r--r-- 1 root root    14 2006-10-25 08:39 default-display-manager
drwxr-xr-x 7 root root  4096 2007-05-18 00:16 fonts
lrwxrwxrwx 1 root root     6 2007-05-17 15:43 gdm -> ../gdm
-rw-r--r-- 1 root root 17371 2006-06-11 22:40 rgb.txt
lrwxrwxrwx 1 root root    13 2007-05-17 15:43 X -> /usr/bin/Xorg
drwxr-xr-x 3 root root  4096 2006-10-25 08:31 xinit
drwxr-xr-x 2 root root  4096 2007-05-18 00:11 xkb
-rw-r--r-- 1 root root  3810 2007-05-18 07:46 xorg.conf
drwxr-xr-x 2 root root  4096 2007-05-18 00:05 Xresources
drwxr-xr-x 2 root root  4096 2007-05-18 00:22 xserver
-rwxr-xr-x 1 root root  4157 2006-10-12 10:33 Xsession
drwxr-xr-x 2 root root  4096 2007-05-18 00:27 Xsession.d
-rw-r--r-- 1 root root   265 2006-06-11 22:40 Xsession.options
-rw------- 1 root root   614 2006-10-25 08:26 Xwrapper.config
paul@paul-laptop:~$

---

### Post by Pragmatist on 2007-05-31
>  -rw-r--r-- 1 root root  **3810** 2007-05-18 07:46** xorg.conf**

Well, this file doesn't appear to be empty.  In fact it is larger than mine.  My xorg.conf is 2082 bytes.  Your permissions are fine and everyone should be able to read the file.

Please give the output of this command:
```
file /etc/X11/xorg.conf
```

---

### Post by pablo66 on 2007-06-02
paul@paul-laptop:~$ file /etc/X11/xorg.conf
/etc/X11/xorg.conf: ASCII English text
paul@paul-laptop:~$

---

### Post by kernel tom on 2007-06-02
reconfigure ur xorg file

sudo dpkg-reconfigure xserver-xorg, then when it asks you to put in the refresh rates, change em to what you know ur monitor can handle

---

### Post by olddoser on 2007-06-02
pablo I think prag intended to say cat not file at the beginning of the code.  Try that and post results.

---

### Post by Pragmatist on 2007-06-02
> **olddoser said:**
> pablo I think prag intended to say cat not file at the beginning of the code.  Try that and post results.

No, actually I meant "file".  The OP stated that his /etc/X11/xorg.conf file was empty.  If that were true, then the "file" command would return that the file was empty.  Here is an example:

> 
desktop:~$ touch example
desktop:~$ file example
example: empty
desktop:~$ echo "blah blah" >> example
desktop:~$ file example
example: ASCII text
desktop:~$ 
I created a file called "example", and then used the file command to check its contents.  The reply is that the file is empty.  Then I add the phrase "blah blah" to the file and then, after I run the file command again, I get a response "ASCII text".

I'm just confirming that the file is not empty.

Now, we need to see the file, so please attach it in your next post.

---

