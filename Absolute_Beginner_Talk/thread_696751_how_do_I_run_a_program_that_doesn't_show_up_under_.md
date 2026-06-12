---
title: "how do I run a program that doesn't show up under applications"
date: 2008-02-14
forum: Absolute Beginner Talk
---

### Post by xxnetcopxx on 2008-02-14
Ok I know how to get into the terminal but I've searched for specific commands to be run a program that doesn't show up under the applications menu in the GUI.  I've used both Automatix and add/remove programs to install programs but I have no idea on how to run them. Any help would be appreciated. Thanks in advance.

---

### Post by jaytek13 on 2008-02-14
```
./application_name
``` will run from a terminal. What are you trying to run?

---

### Post by xxnetcopxx on 2008-02-14
google desktop linux and wine

---

### Post by jaytek13 on 2008-02-14
There's nothing really to run with wine, stand alone. You should either be able to insert a CD with a windows installer on it and wine will recognize it and then start, or you can right click on files and select "run with wine," or just "run with" then type wine. 

As far as google desktop, I'm not sure of the name exactly. You can open a terminal and do ```
locate google*
``` and probably find the application name that way. Then whatever it is you would just type it as I typed it before, so it would be something like```
./google-desktop
```

---

### Post by Cypher on 2008-02-14
Wine can be executed simply as "wine <windows_application>.exe"..

For Google Desktop Linux, try something like
```

dpkg -l | grep google

```
This will hopefully find the package name (the first entry on the left), with that information you can do
```

dpkg -L <package_name> | less

```
List the contents of that package and in the output look for files that reside in the /usr/bin, /usr/local/bin directories. These are the executables that you can run. Hit space to scroll the output and hit 'q' to quit back to the prompt..

---

### Post by stevejesus on 2008-02-14
...or, from a terminal, type a couple of letters of the app, and then whack the TAB key.  The bash shell will attempt to autocomplete the command for you.

---

### Post by phr0ze on 2008-02-14
> **stevejesus said:**
> ...or, from a terminal, type a couple of letters of the app, and then whack the TAB key.  The bash shell will attempt to autocomplete the command for you.

This is what I always do. Type the first few letters of what you installed and push tab once or twice. It will fill in the name of the program or show you a whole list if there is more than one match.

---

### Post by ceagan on 2008-02-14
The easiest thing i can think of for you to try is search for the application using "apropos". Open a terminal window and type apropros followed by a search term. Here is an example search for instant messaging:

```
ceagan@GiantPSP:~$ apropos instant
Pidgin (3pm)         - Perl extension for the Pidgin instant messenger.
finch (1)            - A Pimpin' Penguin console frontend to libpurple. Instant Messaging client.
instant (1)          - manipulates ESIS from parsed SGML instance
nautilus-sendto (1)  - convenience application to send a file via email or instant messenger
pidgin (1)           - Instant Messaging client
Purple (3pm)         - Perl extension to the libpurple instant messenger library.
transpec (5)         - translation specification for instant
XRegisterIMInstantiateCallback (3) - open, close, and otain input method information
XUnregisterIMInstantiateCallback (3) - open, close, and otain input method information
```

Notice that pidgin appears in the list with the description, "Instant Messaging client". I can run pidgin by simply typing "pidin" in the same terminal window, or by using the ALT-F2 shortcut in GNOME, which brings up a run dialog. Good luck and I hope this helps!

---

### Post by Fixman on 2008-02-14
If you don't want to use the terminal, press alt+F2 and write the application name there.

---

### Post by seventhc on 2008-02-14
what app or apps are you trying to run?

---

### Post by littletinman on 2008-02-14
go to sytem>menu and choose what programs you want to be shown

---

