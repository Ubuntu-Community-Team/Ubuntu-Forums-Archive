---
title: "super-mode konsole"
date: 2006-06-19
forum: Absolute Beginner Talk
---

### Post by Blinkiz on 2006-06-19
Hi all

I have got tired of typing sudo everytime. Is their a way around this?
For example, is it possible to open a super-mode konsole that requires password when I start it?

---

### Post by Winblowz on 2006-06-19
Type "sudo -s". It will ask you for your sudo password, but after that you no longer have to type "sudo" before every command.:cool:

---

### Post by mjm115 on 2006-06-19
or, you could hit Alt+F2 and type in 'kdesu konsole'.  This will load konsole as super user and you don't have to keep typing in sudo.

---

### Post by Lord Illidan on 2006-06-19
[quote=mjm115]or, you could hit Alt+F2 and type in 'kdesu konsole'.  This will load konsole as super user and you don't have to keep typing in sudo.[/quote]

Just close the thing after you are ready. Don't use it to launch applications like firefox, for example.

---

### Post by Blinkiz on 2006-06-20
[QUOTE=Winblowz]Type "sudo -s". It will ask you for your sudo password, but after that you no longer have to type "sudo" before every command.:cool:[/QUOTE]
Thank you. Works great!

[QUOTE=mjm115]or, you could hit Alt+F2 and type in 'kdesu konsole'. This will load konsole as super user and you don't have to keep typing in sudo.[/QUOTE]
Dosn't work... Maybe it's KDE only command.

---

### Post by ashrack on 2006-06-20
[QUOTE=Blinkiz]Thank you. Works great!


Dosn't work... Maybe it's KDE only command.[/QUOTE]
Yes it is.

U should type:
gksu gnome-terminal

---

### Post by FredB on 2006-06-20
Using alt+F2 dialog box ;)

Or creating a launcher on the desktop to be quicker ?

---

### Post by mjm115 on 2006-06-20
It depends on how fast you type. :-D  I thought it was KDE cause you said 'konsole'.  You know us KDE users.  If it starts with a 'K' . . .

---

### Post by FredB on 2006-06-20
[QUOTE=mjm115]It depends on how fast you type. :-D  I thought it was KDE cause you said 'konsole'.  You know us KDE users.  If it starts with a 'K' . . .[/QUOTE]

How fast ? 40 to 50 words per minute or so.

KDE ? I saw it in its 0.12 version... And never use it for more than a week since.

I used console, not konsole, or may I need some holidays ? :-\"

---

### Post by mjm115 on 2006-06-20
I think the Alt-F2 method is faster, but that's just me.

---

### Post by mixim on 2006-06-20
type "sudo bash"

---

### Post by FredB on 2006-06-20
[QUOTE=mjm115]I think the Alt-F2 method is faster, but that's just me.[/QUOTE]

indeed. But if you create a launcher, you'll have to double click, and no other keystrokes.

---

