---
title: "azureus closes on startup"
date: 2007-02-06
forum: Absolute Beginner Talk
---

### Post by sailingboarder on 2007-02-06
i installed azureus this morning, and it worked fine
i left it on while i went 2 class, and when i got back it was no longer open
i tried to load it, and it loaded, but as soon as the main window opened, it closed
i just uninstalled and reinstalled azureus, but have the same problem
(i am installing from the repo's)
i checked the website, but could find nothing in the wiki page

```
~$ java -version
java version "1.5.0_08"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_08-b03)
Java HotSpot(TM) Client VM (build 1.5.0_08-b03, mixed mode, sharing)
```

i don't think java is the problem, either

any ideas?

---

### Post by taurus on 2007-02-06
Run it from a terminal to see what's the problem is.

```
azureus
```

---

### Post by hardyn on 2007-02-06
there have been posts about this problem... (do a quick search)

unless the repository version had been replaced reciently, its broken (its well documented on the azurius site)

you will have to replace the JAR file.

good luck.

---

### Post by Dritzen on 2007-02-06
There's a problem with the default azureus install.  Do sudo apt-get remove azureus

Then go here: [Azureus Homepage]("http://azureus.sourceforge.net/")

Download the newest version and install it.  It's very simple to get working and it works great.

---

### Post by sailingboarder on 2007-02-06
```
changeLocale: *Default Language* != English (United States). Searching without country..
changeLocale: Searching for language English in *any* country..
changeLocale: no message properties for Locale 'English (United States)' (en_US), using 'English (default)'
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  146
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  146
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Warning: Cannot convert string "-b&h-luxi sans-medium-r-normal--*-140-*-*-p-*-iso8859-1" to type FontStruct
Warning: Cannot convert string "-misc-ar pl shanheisun uni-medium-r-normal--*-*-*-*-p-*-iso10646-1" to type FontStruct
#
# An unexpected error has been detected by HotSpot Virtual Machine:
#
#  SIGSEGV (0xb) at pc=0xb0b52004, pid=5434, tid=3085407920
#
# Java VM: Java HotSpot(TM) Client VM (1.5.0_08-b03 mixed mode, sharing)
# Problematic frame:
# C  [libgtk-x11-2.0.so.0+0x4]  pango_parse_markup+0x4
#
# An error report file with more information is saved as hs_err_pid5434.log
#
# If you would like to submit a bug report, please visit:
#   http://java.sun.com/webapps/bugreport/crash.jsp
#
Aborted

```

i'm going to try the install from the website now, hopefully that will work

---

### Post by sailingboarder on 2007-02-06
downloaded and installed it

works fine 4 now, hopefully it will later

---

### Post by bebop_tango on 2007-02-08
> **Dritzen said:**
> There's a problem with the default azureus install.  Do sudo apt-get remove azureus

Then go here: [Azureus Homepage]("http://azureus.sourceforge.net/")

Download the newest version and install it.  It's very simple to get working and it works great.

It suddenly stops after a while... I was kept removing the ~/.azureus directory every time this happened... and then the program would start again. But this is no solution... it eventually will stop again.

:mad: 

Anyway, thankfully it has been corrected on the newest version.

---

### Post by feanil on 2007-02-09
This worked for me when I was having problems in Dapper and has also worked in edgy.

```
http://ubuntuforums.org/showthread.php?t=219369&page=3
```

---

### Post by raven on 2007-02-10
your solution [here]("http://ubuntuforums.org/showthread.php?t=219369&page=3") worked perfectly
Thanks

---

### Post by sailingboarder on 2007-02-11
updating from the website works great
i've been running it for a few days, with no problem

---

### Post by Forceflow on 2007-03-03
how exactly do I update with the version from the website ?

---

