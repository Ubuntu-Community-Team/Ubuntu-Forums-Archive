---
title: "installing a program into WINE"
date: 2008-03-20
forum: Absolute Beginner Talk
---

### Post by Samurai Penguin on 2008-03-20
I have installed the latest release of WINE for Ubuntu
and need to learn how to add a program. I have
e-Sword.exe I need to add and I noticed iexplore.exe
as I was amking my way through the WINE folders so
can I use Internet Explorer with WINE in Ubuntu?

thanks

---

### Post by |{urse on 2008-03-20
quick:
[http://www.tatanka.com.br/ies4linux/page/Installation](http://www.tatanka.com.br/ies4linux/page/Installation)
concise:
you right click on an executable and run it with wine
to the point:
^^ <3

---

### Post by Nythain on 2008-03-20
quick concise and to the point:
install:
wine /path/to/whatever/you/want/to/install.exe
run it:
wine /path/to/where/program/is.exe

---

### Post by |{urse on 2008-03-20
lol actually i dont think he asked for quick now that i look again :)

---

### Post by Nythain on 2008-03-20
So a little more long winded explanation...
As for your question of IE via WINE... i think its possible, but only old crappy versions... dont be expecting 7 or possibly even 6... you should google "Wine Internet Explorer"... cant help you much more there :(

now, to the task at hand... most of my wine interaction is through the terminal... hopefully you know how to open that up...
and seriously, to run/install/do anything with a program its as easy as:
wine /path/to/what/you/want/to.exe

first note: run winecfg in terminal to initially set up Wine... it will create the "windows" directory structure, usually at
/home/username/.wine/drive_c/
but im assuming you know that too, since you stumbled upon IE...

now for an example... lets say in /home/rune/Desktop i have the install for WoW...
i would open a terminal and type:
wine /home/rune/Desktop/installer.exe
and it would do its thing...
then to run wow i would type something like this
wine /home/rune/.wine/drive_c/Program\ Files/World\ of\ Warcraft/Wow.exe

its really that simple... to make it even more simple, as mentioned above, you can even right click on windows files and there should be an option for "run with wine" or "run in wine" or whatever

hope that helps at least a little

---

### Post by Samurai Penguin on 2008-03-20
tomana@HAL:~$ cd Desktop
tomana@HAL:~/Desktop$ wine e-Sword.exe

worked great ... thanks

---

