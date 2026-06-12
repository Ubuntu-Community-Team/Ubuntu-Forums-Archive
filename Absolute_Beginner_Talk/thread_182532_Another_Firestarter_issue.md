---
title: "Another Firestarter issue"
date: 2006-05-26
forum: Absolute Beginner Talk
---

### Post by nwgray on 2006-05-26
Good morning everyone,
   Please forgive me if this has been covered before. I updated to Dapper Drake yesterday and my Firestarter GUI no longer comes up. Firestarter is installed, but when I try to manually start the GUI from a terminal window, I get this error:

(firestarter:6331): Gtk-WARNING **: cannot open display:

Here's the terminal info from my remove and reinstall:

 sudo apt-get remove firestarter
Reading package lists... Done
Building dependency tree... Done
The following packages will be REMOVED:
  firestarter
0 upgraded, 0 newly installed, 1 to remove and 3 not upgraded.
Need to get 0B of archives.
After unpacking 1946kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 117198 files and directories currently installed.)
Removing firestarter ...
graynw@ubuntu7:~$ sudo apt-get install firestarter
Reading package lists... Done
Building dependency tree... Done
The following NEW packages will be installed:
  firestarter
0 upgraded, 1 newly installed, 0 to remove and 3 not upgraded.
Need to get 0B/391kB of archives.
After unpacking 1946kB of additional disk space will be used.
Selecting previously deselected package firestarter.
(Reading database ... 117141 files and directories currently installed.)
Unpacking firestarter (from .../firestarter_1.0.3-1.1ubuntu4_i386.deb) ...
Setting up firestarter (1.0.3-1.1ubuntu4) ...

graynw@ubuntu7:~$ sudo firestarter
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified


(firestarter:6331): Gtk-WARNING **: cannot open display:


I have no idea what this error means other than the GUi can't open.

Thx a lot!

---

### Post by clint1010 on 2006-05-26
I'm no expert, but drake isn't officially released till june. You have installed a daily build testing version. Maybe firestarter and its intergration with drake is yet to be finalised?

---

### Post by Sutekh on 2006-05-26
Firestarter and Dapper should work fine.

Try removing your firestarter configuration files and then installing
```
sudo apt-get --purge remove firestarter
sudo apt-get install firestarter
```

Else try
```
export DISPLAY=:0 && sudo firestarter

```

---

### Post by nwgray on 2006-05-28
[QUOTE=Sutekh]Firestarter and Dapper should work fine.

Try removing your firestarter configuration files and then installing
```
sudo apt-get --purge remove firestarter
sudo apt-get install firestarter
```

Else try
```
export DISPLAY=:0 && sudo firestarter

```[/QUOTE]
Tried the first option and got this:

 sudo apt-get --purge remove firestarter
Password:
Reading package lists... Done
Building dependency tree... Done
The following packages will be REMOVED:
  firestarter*
0 upgraded, 0 newly installed, 1 to remove and 15 not upgraded.
Need to get 0B of archives.
After unpacking 1946kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 119337 files and directories currently installed.)
Removing firestarter ...
Purging configuration files for firestarter ...
dpkg: error processing firestarter (--purge):
 subprocess post-removal script returned error exit status 1
Errors were encountered while processing:
 firestarter
E: Sub-process /usr/bin/dpkg returned an error code (1)

Reinstalled firestarter and I'm not sure if it's running or not. I opened System Monitor, selected All Processes under VIEW, and it wasn't listed. Here's the install text:

 sudo apt-get install firestarter
Reading package lists... Done
Building dependency tree... Done
The following NEW packages will be installed:
  firestarter
0 upgraded, 1 newly installed, 0 to remove and 15 not upgraded.
Need to get 0B/391kB of archives.
After unpacking 1946kB of additional disk space will be used.
Selecting previously deselected package firestarter.
(Reading database ... 119280 files and directories currently installed.)
Unpacking firestarter (from .../firestarter_1.0.3-1.1ubuntu4_i386.deb) ...
Setting up firestarter (1.0.3-1.1ubuntu4) ...


When running the export, I got this:

export DISPLAY=:0 && sudo firestarter
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified


(firestarter:6753): Gtk-WARNING **: cannot open display:

I am totally lost on this one. I want to get rid of XP but not until I feel comfortable with Ubuntu.

Thx

---

### Post by ym4546 on 2006-08-15
try running: gksudo firestarter....or kdesu firestarter if you're on kde...

just a wild guess, b/c AFAIK, sudo is not meant for gui applications.

---

