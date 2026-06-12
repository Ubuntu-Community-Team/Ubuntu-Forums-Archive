---
title: "OK, &quot;Alien&quot; is alien to me"
date: 2007-01-13
forum: Absolute Beginner Talk
---

### Post by kliljedahl on 2007-01-13
I finally found the Linux driver for my Lexmark Z705 printer. It's a .RPM file which I downloaded to my desktop. I couldn't find a deb file. Lexmark support for Debian seems slim, but at least they've got something. Any and all help (as always) is greatly appreciated. You people are wonderful.

---

### Post by Frak on 2007-01-13
No offence, but did you try to convert the .rpm to a .deb, with this command

```
alien -d **/home/user/Desktop/driver.rpm**
```

Where the bold is the location to the rpm driver.

---

### Post by Denn1s on 2007-01-13
try:
```
sudo apt-get install alien
``` 
```
alien name_of_file
```

---

### Post by ComplexNumber on 2007-01-13
fire up the terminal, and go to where the rpm is. then type on the command line 'sudo alien -d <rpm package name>'. this will create the deb. to install the deb, type in 'sudo dpkg -i <name of the newly created deb package>'.

---

### Post by petersjm on 2007-01-13
> **ComplexNumber said:**
> to install the deb, type in 'sudo dpkg -i <name of the newly created deb package>'.

Or the old "Windows way" -- double-click it.

---

### Post by BarfBag on 2007-01-13
Alien is a useful tool, but I've always had trouble with converted packages.  Not sure why.

If they have a .tar.gz, you should use that.

---

### Post by ComplexNumber on 2007-01-13
> **petersjm said:**
> Or the old "Windows way" -- double-click it.
well, considering that he's already got the terminal out and in the right location, its probably less effort to just type in another command at the terminal. it will also give him some practice with new commands.

---

### Post by Frak on 2007-01-13
> **BarfBag said:**
> Alien is a useful tool, but I've always had trouble with converted packages.  Not sure why.

If they have a .tar.gz, you should use that.
Good idea, tar.gz's are more reliable.

---

### Post by kliljedahl on 2007-01-13
> **Frak said:**
> No offence, but did you try to convert the .rpm to a .deb, with this command

```
alien -d **/home/user/Desktop/driver.rpm**
```

Where the bold is the location to the rpm driver.

Tried that and got "Must run as root to convert to deb format (or you may use fakeroot).
" I apologize for my ignorance, but I'm less than 2 weeks at this, From what I've "learned" so far, that requires a "sudo" command.

---

### Post by ComplexNumber on 2007-01-13
> **kliljedahl said:**
> Tried that and got "Must run as root to convert to deb format (or you may use fakeroot).
" I apologize for my ignorance, but I'm less than 2 weeks at this, From what I've "learned" so far, that requires a "sudo" command.
use my instructions. you have to run alien as root (ie use sudo before the command)

---

### Post by Pollywoggy on 2007-01-13
> **Frak said:**
> Good idea, tar.gz's are more reliable.

That is where checkinstall comes in handy.  I would rather use a tar.gz and convert a rpm to a deb only as a last resort.  The checkinstall command (in the checkinstall package) can often be used to make a deb from a tar.gz and install in one step.  It won't work if there is no Makefile in the tarball.

---

### Post by kliljedahl on 2007-01-14
> **ComplexNumber said:**
> fire up the terminal, and go to where the rpm is. then type on the command line 'sudo alien -d <rpm package name>'. this will create the deb. to install the deb, type in 'sudo dpkg -i <name of the newly created deb package>'.

and I keep getting this: dpkg: error processing /home/kliljedahl/Desktop/lexmark-z700-cups-driver-1.1.1-1.i586.rpm (--install):
 subprocess dpkg-deb --control returned error exit status 2
Errors were encountered while processing:

---

### Post by Frak on 2007-01-14
run

```
alien --help
```

and look for the option that says "to tar.gz" which should be this

```
sudo alien -t <location of file>
```

**OR**

you can just** install** the **RPM** as it is with

```
sudo alien -i <location of file>
```

Try this last one **First**.

---

### Post by ComplexNumber on 2007-01-14
> **kliljedahl said:**
> and I keep getting this: dpkg: error processing /home/kliljedahl/Desktop/lexmark-z700-cups-driver-1.1.1-1.i586.rpm (--install):
 subprocess dpkg-deb --control returned error exit status 2
Errors were encountered while processing:
that may well be because lexmark-z700-cups-driver-1.1.1-1.i586.rpm has a dependency which isn't installed.

---

### Post by kliljedahl on 2007-01-14
Thank you guys, it finally converted and theoretically installed. Once again I thank you for your assistance and patience.

---

