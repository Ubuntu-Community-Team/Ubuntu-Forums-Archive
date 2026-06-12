---
title: "error code during install"
date: 2007-07-17
forum: Absolute Beginner Talk
---

### Post by jakelaptop on 2007-07-17
I get this error code every time I try to install something, and it is preventing Synaptic from making any installs or removals also. 
This line comes at the end of any succesful package download (i.e. i just ran sudo apt-get install supertux, and right when it was done downloading, this came up)

dpkg: parse error, in file `/var/lib/dpkg/available' near line 1:
 field name `' must be followed by colon
E: Sub-process /usr/bin/dpkg returned an error code (2)


How Do I fix this?

---

### Post by jimrz on 2007-07-17
> **jakelaptop said:**
> I get this error code every time I try to install something, and it is preventing Synaptic from making any installs or removals also. 
This line comes at the end of any succesful package download (i.e. i just ran sudo apt-get install supertux, and right when it was done downloading, this came up)

dpkg: parse error, in file `/var/lib/dpkg/available' near line 1:
 field name `' must be followed by colon
E: Sub-process /usr/bin/dpkg returned an error code (2)


How Do I fix this?

try ```
sudo dpkg --configure -a
```

---

### Post by Al3xK3aton on 2007-07-17
It sounds like you're using the wrong installation procedure.

---

### Post by jakelaptop on 2007-07-17
When i tried the --a configure it returned this error message:

dpkg: parse error, in file `/var/lib/dpkg/available' near line 1:
 field name `' must be followed by colon


And as for using the wrong install procedure... that could be the case, but I still dont understand why Synaptic isn't working, and I'm assuming that the problems are related.

---

### Post by Al3xK3aton on 2007-07-17
> **jakelaptop said:**
> I'm assuming that the problems are related.

Well, you know what they say about assuming.

---

### Post by jakelaptop on 2007-07-17
well either way, I need to figure out why synaptic isn't able to install packages it has downloaded, and I need to know why terminal can't install packages it has downloaded. Let's pick one and try to figure out how to fix it, Please.

---

### Post by meierfra on 2007-07-17
Somehow the file  /var/lib/dpkg/available  got screwed up.  You might look at the file and see whether you can fix it. (Back it up first)  If you google "/var/lib/dpkg/available' you will find that other people had the same problem.  For example: 

[https://bugs.launchpad.net/ubuntu/+source/dpkg/+bug/64012]("https://bugs.launchpad.net/ubuntu/+source/dpkg/+bug/64012")

---

### Post by jakelaptop on 2007-07-17
that sounds right to me. Any chance you're willing to help me with a more step-by-step guide to how to get that done, everythinf from backing up to changing the files? I'm new here, can't you tell...

---

### Post by meierfra on 2007-07-17
I'll try.
Open a terminal and move to the folder /var/lib/dpkg/:

```
 cd  /var/lib/dpkg/ 
```

Backup the file "available"

```
sudo cp  available  available.backup
```

try to open the file "available":

```
gksudo gedit available 
```

and post the first few lines

---

### Post by meierfra on 2007-07-17
I found a possible solution at 

[http://www.linuxquestions.org/questions/showthread.php?t=225508]("http://www.linuxquestions.org/questions/showthread.php?t=225508")

In the terminal type: 

```
sudo dpkg --clear-avail
```

and

```
sudo apt-get update
```

That should fix your problem.

---

### Post by jakelaptop on 2007-07-17
> **meierfra said:**
> I'll try.
Open a terminal and move to the folder /var/lib/dpkg/:

```
 cd  /var/lib/dpkg/ 
```

Backup the file "available"

```
sudo cp  available  available.backup
```

try to open the file "available":

```
gksudo gedit available 
```

and post the first few lines

jwertz@jwertz-laptop:/var/lib/dpkg$ gksudo gedit available
/home/jwertz/.themes/Alphacube GTK 0.5/gtk-2.0/gtkrc:63: Clearlooks configuration option "menuitemstyle" is not supported and will be ignored.
/home/jwertz/.themes/Alphacube GTK 0.5/gtk-2.0/gtkrc:64: Clearlooks configuration option "listviewitemstyle" is not supported and will be ignored.
/home/jwertz/.themes/Alphacube GTK 0.5/gtk-2.0/gtkrc:65: Clearlooks configuration option "progressbarstyle" is not supported and will be ignored.

---

### Post by jakelaptop on 2007-07-17
> **meierfra said:**
> I found a possible solution at 

[http://www.linuxquestions.org/questions/showthread.php?t=225508]("http://www.linuxquestions.org/questions/showthread.php?t=225508")

In the terminal type: 

```
sudo dpkg --clear-avail
```

and

```
sudo apt-get update
```

That should fix your problem.


first command gave me nothing, second command gave me this:
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release.gpg [191B]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Translation-en_US
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty Release.gpg [191B]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/multiverse Translation-en_US
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates Release.gpg [191B]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/restricted Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Packages        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/restricted Sources
Fetched 3B in 2s (1B/s)  
Reading package lists... Done

---

