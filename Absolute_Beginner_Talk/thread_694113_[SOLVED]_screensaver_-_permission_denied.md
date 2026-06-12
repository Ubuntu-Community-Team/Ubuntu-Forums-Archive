---
title: "[SOLVED] screensaver - permission denied"
date: 2008-02-11
forum: Absolute Beginner Talk
---

### Post by skymera on 2008-02-11
[http://micrux.net/?p=66](http://micrux.net/?p=66)

im trying to do this for a screensaver.

ive done all it said, however when i go system>prefs>screensaver

i get permission error how do i solve this?

o and where do i enter cat `find /usr/src/linux-source/ -name '*.c' | argshuf` ??

theres no option button

---

### Post by taurus on 2008-02-11
You run that command from a terminal, Applications -> Accessories -> Terminal.

---

### Post by skymera on 2008-02-11
yes.

but i need to enter that command on the screensaver settings, which i cannot find

---

### Post by spiderbatdad on 2008-02-11
have you tried running it as root```
sudo su
cat `find /usr/src/linux-source/ -name '*.c' | argshuf`
```

---

### Post by skymera on 2008-02-11
not sure you quite understand.

[http://micrux.net/?p=66](http://micrux.net/?p=66)

that is what i am following.
but it wont work.

---

### Post by spiderbatdad on 2008-02-11
it looks like you were supposed to download his tar afghfs (whatever) and install it as root.```
Installation:
	Unzip the archive:
		# tar -vxzf argshuf.tar.gz
	
	Move into the source directory
		# cd argshuf

	Compile the source code:
		# make

	Install the binary:
		# sudo make install

```

haven't figured out the permissions problem with Preferences>>Screensaver, though. Are you logged into an account that doesn't have administrative privileges? Administration>>Users and Groups>>Properties>>user privileges.

---

### Post by skymera on 2008-02-11
thats all done.

the screensaver works fine in xscreensaver

but when i use gnome-screensaver i get a permissin error

---

### Post by skymera on 2008-02-11
how do i chnage the screensaver settings?

theres no option in the Gnome menu;s

---

### Post by jan quark on 2008-02-11
system > preferences > screensaver 
don't you have this?

---

### Post by skymera on 2008-02-11
yes i do.

i want to change the settings of a screensaver, how it looks etc

---

### Post by skymera on 2008-02-11
dont qorry, i sorted it.

thanks =D

i changed a screensaver to show linux source, attached a screenie.

now looks like im super geek, o yeah :guitar:

---

