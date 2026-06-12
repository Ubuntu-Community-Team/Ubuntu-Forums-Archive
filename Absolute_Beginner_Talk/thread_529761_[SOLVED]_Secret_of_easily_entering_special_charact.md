---
title: "[SOLVED] Secret of easily entering special characters revealed -- sort of."
date: 2007-08-19
forum: Absolute Beginner Talk
---

### Post by Flyvapnet on 2007-08-19
Like many of you, I've become frustrated with the complexity of entering special characters.  It was a breeze with Windows, but not so much with Linux.

Well, I managed to find the following web page which goes a long way toward making special characters less of an ordeal:

[**_Special Characters made easier in Ubuntu -- Debian Admin_**](http://www.debianadmin.com/special-characters-made-easier-in-ubuntu.html)
[size=1]*Debian/Ubuntu Linux System Administration Tutorials,Howtos,Tips and Tricks*[/size]

Here's the too-short list which that page provides:

> To use it, hold the Compose key down and then type in the characters you want to mash together.For Example check the following ones
RightWin + C + = produces €
RightWin + = + C produces €
RightWin + C + O produces ©
RightWin + O + C produces ©
RightWin + a + ‘ produces á

Yes, it ends there.  My question is:  Where are the rest of them?

If you have a more complete list of these, shall we say, shortcuts could you please post it here?  Thank you for your assistance!

:confused:

=^..^=

---

### Post by Myglaren on 2007-08-19
You SHOULD be able to enter Unicode but I find that this option was disabled - or at least didn't work - in Dapper and now also in Feisty.
None of those options posted above work either.
¹²³€½¾@&#322;e¶&#359;&#8592;&#8595;&#8594;øþæßð&#273;&#331;&#295;j&#312;&#322;«»¢“”nµ·
Alt Gr produces the line above though.

---

### Post by Flyvapnet on 2007-08-19
How weird is that, **Myglaren**?  It would seem, at this point, a method for easily entering special characters remains a big mystery.

For example, the name "Björk" will have to be typed as either "Bjork" or "Bjoerk" -- the former being incorrect yet widespread and the latter being sort of correct yet unfamiliar to search engines and many humans.  The correct spelling was brought to you by our friends at the firm of Highlight, Copy & Paste.

:D

=^..^=

---

### Post by bapoumba on 2007-08-19
It really depends on your keyboard layout and your locales.
Look here: /usr/share/X11/locale/iso8859-1/Compose.

---

### Post by Flyvapnet on 2007-08-19
I tried that just now, **bapoumba**; and here's what I got:

> flyvapnet@Samantha:~$ /usr/share/X11/locale/iso8859-1/Compose
bash: /usr/share/X11/locale/iso8859-1/Compose: Permission denied
flyvapnet@Samantha:~$ sudo /usr/share/X11/locale/iso8859-1/Compose
Password:
sudo: /usr/share/X11/locale/iso8859-1/Compose: command not found
flyvapnet@Samantha:~$

See, thing of it is, I'm not big on this 1980s command-line stuff.  I'm a user and I want everything to be user-friendly!

At least I remembered the "sudo" thing, which gets you past the data operating system's first line of defense against users.  Thanks though, for trying to help.

:confused:

=^..^=

---

### Post by eapache on 2007-08-19
Under System>Preferences>Keyboard (not keyboard shortcuts), and the tab "Layout Options". Choose "compose key position" and select one (i prefer left-win). Then to use any special character, use compose key + base letter + special. So for me, é is leftwin + e + '.
e + ' = é
e + ` = è
c + , = ç

---

### Post by Flyvapnet on 2007-08-19
Thank you, **eapache**, for helping make this scenario clearer!  I've already got a compose key activated, so I'll mess around with the keyboard and see if I can figure out how to make those two dots appear over the "o" in "Björk."

:cool:

=^..^=

---

### Post by bapoumba on 2007-08-20
@ Flyvapnet: i'm very sorry, this is a text file to open. So open nautilus (or any other file manager) or open the "computer" or "file system" icon on your desktop (not sure of the name) and go to this location on your computer:
--> usr --> share --> X11 --> locale --> iso8859-1.
There should be a "Compose" file, which is a text file.

Double clic on it, to open it, and you should see a list of key combinations with the "compose" key and their actions. Some are redundant and for some very special characters, you may have to use the character map instead of the "compose" key.

Here are the first couple lines from mine:
```
# <Multi_key> Means <Compose>
# Special Character
<Multi_key> <plus> <plus>		: "#"	numbersign
<Multi_key> <apostrophe> <space>	: "'"	apostrophe
<Multi_key> <space> <apostrophe>	: "'"	apostrophe
<Multi_key> <A> <T>			: "@"	at
```

Do you have this file?

---

### Post by Fibonacci on 2007-08-20
I think it's Compose + " + o = ö.

---

### Post by Flyvapnet on 2007-08-20
Hooray, I've got it!  Thanks a whole bunch, **bapoumba**, for your help:  Indeed, that list is right where you said it would be and it definitely saves my day.

Thank you too, **Fibonacci**, for your input.  I'm on my way to Linux user-friendliness!

:)

=^..^=

---

### Post by bapoumba on 2007-08-20
You're welcome! Enjoy :)

---

