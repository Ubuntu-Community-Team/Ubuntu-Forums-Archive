---
title: "Can't run a binary file"
date: 2007-05-16
forum: Absolute Beginner Talk
---

### Post by paintwiz on 2007-05-16
Hello, I am completely new to linux, I just tried to manually install a program (Songbird) using the

sudo tar xzvf <file>

code and it seemed  to be working until I tried to execute the newly un-tarred files, I got a error saying

bash: ./Songbird: cannot execute binary file

I haven't got a clue, please help.

---

### Post by chamberlain2006 on 2007-05-16
It's been a while since I've installled songbird, but you'll probably need to make the file executable.

```
sudo chmod +x Songbird
```
will do so.

---

### Post by paintwiz on 2007-05-17
Nope, I just tried it, the same error comes back, cannot execute binary file.
:mad:

---

### Post by taurus on 2007-05-17
Can you post the output of this command, in the directory that you intend to execute Songbird?

```
ls -la
```

---

### Post by Stian24 on 2007-05-17
follow the instructions here:
[http://www.psychocats.net/ubuntu/songbird](http://www.psychocats.net/ubuntu/songbird)

---

### Post by paintwiz on 2007-05-17
There we go, that last one did the trick, thanks alot Stian

---

### Post by paintwiz on 2007-05-17
*sigh* scratch that, Songbird installs and appears to launch, but it never runs. Great. This is just a guess but I think the installer provided at psychocats.com gave me the install made for the wrong architecture. Yeah, it probably would have been smart to mention I'm running this off a PS3.
And heres the listing for the output, or at least I think it is:

total 136
drwxrwxr-x  8  502   11  4096 2007-03-01 21:49 .
drwxr-xr-x  3 root root  4096 2007-05-16 21:41 ..
-rw-rw-r--  1  502   11   213 2007-03-01 21:49 application.ini
drwxrwxr-x  3  502   11  4096 2007-03-01 21:49 chrome
drwxrwxr-x  2  502   11  4096 2007-03-01 21:49 components
drwxrwxr-x  3  502   11  4096 2007-03-01 21:49 defaults
-rw-rw-r--  1  502   11 17996 2007-03-01 21:49 gpl.txt
-rw-rw-r--  1  502   11 18649 2007-03-01 21:49 LICENSE.txt
drwxrwxr-x  2  502   11  4096 2007-03-01 21:49 plugins
drwxrwxr-x  2  502   11  4096 2007-03-01 21:49 scripts
-rwxrwxr-x  1  502   11 49796 2007-03-01 21:49 Songbird
-rw-rw-r--  1  502   11   241 2007-03-01 21:49 TRADEMARK.txt
drwxrwxr-x 10  502   11  4096 2007-03-01 21:49 xulrunner

I hope you know what that means, cause I don't.

I went to some tutorials, tried everything I found, searching for packages,   make,   ./configure,  but nothing works! There isn't a configure file,  when I run make it says no specified targets and no makefiles found and there aren't any songbird packages on synaptic!.... Help... anyone?

---

