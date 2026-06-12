---
title: "help with installation, please."
date: 2007-09-04
forum: Absolute Beginner Talk
---

### Post by Parasitesss on 2007-09-04
Okay, I want to download HJSplit for Linux.
But in order to do that it says that I must firts download the kylix library.
So I do. I Open up the folder that I just downloaded (the kylix lib.) and I open the README.
This is what it instructs me to do: 

"Just run install.sh as root in order to install these Kylix 3
libraries.

Step by step:
1. > su
2. enter root password
3. # ./install.sh
4. # exit"

okay.
So I type "su" in the Terminal.
it asks for my psswd, so I type it in.
Then as the instruction says, I typed in "./install.sh"
and this is the reply I get, help me please.
"bash: ./install.sh: No such file or directory"

---

### Post by banewman on 2007-09-04
This should get you there - sudo /path/to/install.sh -
e.g - sudo /home/prarasitesss/downloads/install.sh.

---

### Post by Parasitesss on 2007-09-04
thank you soo much for youre reply, I'll try that.

---

### Post by Parasitesss on 2007-09-04
please help
> john@john-desktop:~$ sudo /home/john/downloads/install.sh
Password:
Sorry, try again.
Password:
sudo: /home/john/downloads/install.sh: command not found
john@john-desktop:~$

---

### Post by Parasitesss on 2007-09-04
I tried this to no avail.

> john@john-desktop:~$ sudo /home/john/install.sh
sudo: /home/john/install.sh: command not found
john@john-desktop:~$ sudo /home/john/Desktop/kylixlibs3-borqt/install.sh
install: cannot stat `libborqt-6.9.0-qt2.3.so': No such file or directory
cp: cannot stat `libborqt-6.9.0-qt2.3.so': No such file or directory
grep: /etc/ld.so.conf: No such file or directory
john@john-desktop:~$

---

### Post by ramjet_1953 on 2007-09-04
Did you [COLOR="Blue"]unpack[/COLOR] the tar.gz file first?

You can do this by right clicking on it and choose the [COLOR="Blue"]Extract Here option[/COLOR].

Also it is important that the command entered is[COLOR="Blue"] ./install.sh[/COLOR]

Yes the . is critical.

Regards,
Roger :cool:

---

