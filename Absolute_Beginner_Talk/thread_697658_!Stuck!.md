---
title: "!Stuck!"
date: 2008-02-15
forum: Absolute Beginner Talk
---

### Post by majikhotline on 2008-02-15
i used synaptic to install jasper and dont know what folder its install in..... also when i try to use the webcam in kopete it say "Webcam for is not available".  how can i this to work......Please help!

---

### Post by eggdeng on 2008-02-15
For the first issue, try
```
which jasper
```
If you get no joy, run
```
updatedb
```
then
```
locate jasper
```

---

### Post by majikhotline on 2008-02-15
which jasper:
/usr/bin/jasper

i dont think i used the updatedb right:
updatedb: fatal error: You are not authorized to create a default slocate database!

locate jasper:
/usr/share/doc/libjasper1
/usr/share/doc/libjasper1/copyright
/usr/share/doc/libjasper1/changelog.Debian.gz
/usr/share/doc/libjasper1/README.Debian
/usr/lib/libjasper.so.1
/usr/lib/libjasper.so.1.0.0
/var/lib/dpkg/info/libjasper1.postinst
/var/lib/dpkg/info/libjasper1.md5sums
/var/lib/dpkg/info/libjasper1.list
/var/lib/dpkg/info/libjasper1.postrm
/var/lib/dpkg/info/libjasper1.shlibs

I hope this helps

---

### Post by oldos2er on 2008-02-15
You need to run "sudo updatedb."

 You can also use Synaptic to show where each file in the package is installed. Click Status, Installed, then right-click on a package and choose Properties, Installed Files.

---

### Post by majikhotline on 2008-02-15
i found the .exe in /usr/bin/jasper but cant open it, i also sudo updatedb and really didnt see to much happening, what do i do next

---

### Post by oldos2er on 2008-02-15
You'll need to explain what "can't open it" means. Are you trying to run it in the terminal, or through Nautilus? What, if any, error msgs do you see?

 After running 'sudo updatedb,' re-run "locate jasper." But apparently you already know where it is.

---

### Post by eggdeng on 2008-02-15
The output from the which command
```
/usr/bin/jasper
```
tells you that jasper is installed to the /usr/bin directory, which is in the system path. So you should be able to run it by typing 
```
jasper
```
in a terminal.

---

