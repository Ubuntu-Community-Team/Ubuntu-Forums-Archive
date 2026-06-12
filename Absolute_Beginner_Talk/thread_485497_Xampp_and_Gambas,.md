---
title: "Xampp and Gambas,"
date: 2007-06-26
forum: Absolute Beginner Talk
---

### Post by phizikal on 2007-06-26
Ok, how do I uninstall these programs with the shell. Because I don't need them and they are getting on my nerves being on my HD.

Please and thank yous.

---

### Post by charles.g.moore on 2007-06-26
> **phizikal said:**
> Ok, how do I uninstall these programs with the shell. Because I don't need them and they are getting on my nerves being on my HD.

Please and thank yous.

First off how were they installed?

if you installed them from source there should be an uninstallation script in the folder you unzipped when you first installed the application.

if you installed from the command line through the repo's you could just do 

sudo aptitude remove *name of application*

---

### Post by phizikal on 2007-06-26
Thank you very munch. :)

---

### Post by KIAaze on 2007-06-26
It depends how you installed them...

1)If you installed through apt-get:
```
apt-get remove Xampp Gambas
```

2)If you installed from source:
Go into the directory containing the Makefile (where you typed ./configure;make;make install) and execute the command:
```
make uninstall
```

3)If you installed using add/remove programs or Synaptic:
Well, simply use them to remove the program.
There is probably a command-line with apt-get or aptitude doing the same thing, but I'm not sure, so...

edit: too late...

---

### Post by phizikal on 2007-06-27
Is there a shell command that can make a folder read and writeable because i can do it with the file properties?

---

### Post by charles.g.moore on 2007-06-27
> **phizikal said:**
> Is there a shell command that can make a folder read and writeable because i can do it with the file properties?

if you want to make a folder r/w

sudo chmod +rw *name of folder*

---

### Post by phizikal on 2007-06-27
It still doesn't have the right permissions.

---

### Post by charles.g.moore on 2007-06-27
> **phizikal said:**
> It still doesn't have the right permissions.

post your ls -l

does it give you an error???

---

### Post by phizikal on 2007-06-27
When I try to drag and drop into the /var/www folder I get an error that the folder isn't writeable

```

drwxr-xr-x  3 root root  4096 2007-06-26 16:10 www

```

---

### Post by phizikal on 2007-06-27
accidental  bump.

---

