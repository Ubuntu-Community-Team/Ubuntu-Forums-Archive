---
title: "I'm trying to install programs with the terminal (WINE)"
date: 2007-05-08
forum: Absolute Beginner Talk
---

### Post by MS-DOS4 on 2007-05-08
So one of my friends told me about a program called WINE that emulates windows. This could be neat for playing halo and steam games on. So I went to the Wine website and went to the download section, and it told me to put this into the terminal:

```
wget -q http://wine.budgetdedicated.com/apt/387EE263.gpg -O- | sudo apt-key add -
```

and I hit enter once I do that. It asks for a password (so before I do that, I go to applications>System>Users and groups and change the password to one I want and then retry the whole terminal thing. once it asks for the password I click enter to get the _ so I can type and type in my password and it ends up looking like this:

[img]http://img442.imageshack.us/img442/9289/helpvg5.png[/img]

I'm a bit at a loss here. Here's what I'm trying to do: [http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)

Can you perhaps help me? Please? :confused:

---

### Post by bobplano on 2007-05-08
it's supposed to do that because you are only getting the key to the wine repositories(the place with the programs). that means that you are deciding to trust it. then you need to run```
sudo apt-get update
sudo apt-get install wine
```
*then* you will have wine unless something goes horribly wrong. the password doesn't show for security reasons so just keep typing

---

### Post by MS-DOS4 on 2007-05-08
I'm afraid I don't understand anything in that message. Thanks for replying though.

---

### Post by bobplano on 2007-05-08
you really just need to copy and paste the commands. ubuntu doesn't automatically trust places to get software because it could be malicious so it assigns them a "key". the command you typed in got the key

---

### Post by MS-DOS4 on 2007-05-08
So the password I typed in is my key? :confused:

---

### Post by bobplano on 2007-05-08
no, i'm sorry for the confusion. the key was gotten by your command and that's it. don't worry about the key, ubuntu handles that stuff. the password you type in is the password that you chose. now after running that command and typing in your password you need to run```
sudo apt-get update
sudo apt-get install wine
```
to actually get wine

---

### Post by MS-DOS4 on 2007-05-08
Ehh forget it. Thanks for the help though.

---

### Post by ubnewbie2 on 2007-05-08
open 'Add/remove programs', select 'all available applications' from the choices at the top right, search for the word, wine, check the box next to "Wine Windows Emulator" and click the 'Apply' button

---

### Post by zvacet on 2007-05-09
Another option is to open synaptic and in search box type wine.When you find it click on withe box on the left and mark for installation.That is all you have to do to get wine.When wine is installed type in terminal

```
winecfg
```

---

