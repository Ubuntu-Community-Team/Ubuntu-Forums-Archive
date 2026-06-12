---
title: "Hi, Pleaseeeeeeeee Help Me!"
date: 2007-08-19
forum: Absolute Beginner Talk
---

### Post by Khurrum on 2007-08-19
Hi, whenever I try to install a debian package using terminal lets say the package is ub.deb. Its on the desktop. I go to the terminal and type:
sudo dpkg -i /home/(myusername)desktop/ub.deb
I keep getting and error like:
dpkg: error processing /home/(myusername)/desktop/ub.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 /home/(myusername)/desktop/ub.deb

Is there something I am doing wrong or is my terminal spoiled pleaseeeeeeee help!

I AM NEVER ABLE TO INSTALL ANYTHING VIA TERMINAL!

I want to know why can't I install with terminal, is this a bug or something??????????????

---

### Post by Jimmyfj on 2007-08-19
Just browse to the file using nautilus. Then right-click on the file and select Install with Debian packet installer.

---

### Post by MenZa on 2007-08-19
The default location for the desktop is /home/yourusername/Desktop, not /home/yourusername/desktop. ext3 filenames are case-sensitive.

---

### Post by linque on 2007-08-19
You put "desktop", but it should have an initial capitalization -- "Desktop". Try using this:

```
home/(myusername)/Desktop/ub.deb
```

---

### Post by tdrusk on 2007-08-19
but if you want to know what you are doing wrong...

Desktop is capitalized. The terminal is case sensitive. That's why the terminal couldn't find it.

---

### Post by RomeReactor on 2007-08-19
Hi. The command line is case sensitive, so you must enter:
```
sudo dpkg -i /home/(myusername)**Desktop**/ub.deb
```
That said, you really shouldn't install debian packages in Ubuntu; try looking in [GetDeb]("http://www.getdeb.net/") or the [Ubuntu packages site]("http://packages.ubuntu.com/") for an Ubuntu version of the program you want to install.

What program is it?

Oh, and as Jimmyfj said, you can just double-click the .deb file to install it.

---

### Post by Khurrum on 2007-08-19
Thanks alot guys, it finally worked, didn't know about the case sensitive thing!

---

### Post by intel on 2007-08-19
check the permissions on the *.deb file it should be the same as chown <ur name>:<ur name> *.deb

i believe that should solve ur problem

---

### Post by por100pre1 on 2007-08-19
[SIZE="3"]A cheap trick (a good one) is type the command with the space after it and then DRAG and DROP the file to be used into the terminal window, then press enter as usual. Enjoy! :)[/SIZE]

---

### Post by RomeReactor on 2007-08-19
> **por100pre1 said:**
> [SIZE="3"]A cheap trick (a good one) is type the command with the space after it and then DRAG and DROP the file to be used into the terminal window, then press enter as usual. Enjoy! :)[/SIZE]

Nice one! I tried:
```
java -jar 
```
and then dropped a java program, and it worked. This could help people who use wine a lot.

---

### Post by por100pre1 on 2007-08-19
> **RomeReactor said:**
> Nice one! I tried:
```
java -jar 
```
and then dropped a java program, and it worked. This could help people who use wine a lot.

Yep, it works with folders too (if you use the correct command for folders, of course). This works because the so called "terminal windows" are actually **terminal emulators**. That trick only works inside X, obviously.
:popcorn:

---

### Post by TheWizzard on 2007-08-19
> **por100pre1 said:**
> [SIZE="3"]A cheap trick (a good one) is type the command with the space after it and then DRAG and DROP the file to be used into the terminal window, then press enter as usual. Enjoy! :)[/SIZE]

brilliant. thanks!

---

### Post by mysticmatrix on 2007-08-19
> **por100pre1 said:**
> [SIZE="3"]A cheap trick (a good one) is type the command with the space after it and then DRAG and DROP the file to be used into the terminal window, then press enter as usual. Enjoy! :)[/SIZE]

Good tip!!!! Thanks for this one

---

