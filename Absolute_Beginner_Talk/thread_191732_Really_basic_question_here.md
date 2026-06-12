---
title: "Really basic question here"
date: 2006-06-07
forum: Absolute Beginner Talk
---

### Post by jaccav on 2006-06-07
I'm trying to mount my windows directory.  I found instructions that I've entered in terminal, but when I enter:

sudo gedit /etc/fstab

and hit enter, I just get a $ prompt.  Shouldn't I get a file coming up that I can append to?

It seems like this is happening with every command I give in terminal.

---

### Post by nalmeth on 2006-06-07
That is weird behavior

Try hitting ALT-F2
gksudo gedit /etc/fstab

---

### Post by jive_dude on 2006-06-07
When your in the /etc/ directory can you see the fstab file, for example:
cd /etc/
ls fs*

does the file even come up. Also another thing to try is hitting tab and using the autocomplete ability.

---

### Post by jaccav on 2006-06-07
the file comes up.  

If the system doesn't like the password, does it tell you?

And if for some reason I entered it incorrectly, can I change it?

---

### Post by uzi09 on 2006-06-07
well, the password is just your login passwd. if you want to change that, you should just be able to type:
passwd
and it'll let you change it.

i've heard some people complaining that gedit wasn't opening up for some reason. try running gedit by typing:
gedit
in the termina AND NOTHING ELSE to see if it'll show any errors. also, i'm not sure of your specs, but could possibly be taking a long time because of hardware, or some other software hogging the mem/cpu.

---

### Post by drtvasudevan on 2006-06-08
hope you are in ubuntu. not kubuntu or xubuntu!
gedit is in ubuntu only, right?

tv
[QUOTE=jaccav]I'm trying to mount my windows directory.  I found instructions that I've entered in terminal, but when I enter:

sudo gedit /etc/fstab

and hit enter, I just get a $ prompt.  Shouldn't I get a file coming up that I can append to?

It seems like this is happening with every command I give in terminal.[/QUOTE]

---

### Post by BoyOfDestiny on 2006-06-08
[QUOTE=jaccav]I'm trying to mount my windows directory.  I found instructions that I've entered in terminal, but when I enter:

sudo gedit /etc/fstab

and hit enter, I just get a $ prompt.  Shouldn't I get a file coming up that I can append to?

It seems like this is happening with every command I give in terminal.[/QUOTE]

Hmm never had that issue, but I've heard people say you should use gksudo when you want to launch a gui app as root.

gksudo gedit /etc/fstab

If that doesn't work

Try
Applications -> System Tools -> Run as different user (if the option isn't there, try the alacarte menu editor by right clicking Applications.)

---

