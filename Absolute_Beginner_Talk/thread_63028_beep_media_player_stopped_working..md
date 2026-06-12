---
title: "beep media player stopped working."
date: 2005-09-06
forum: Absolute Beginner Talk
---

### Post by wilywampa on 2005-09-06
*sigh*. nothing in linux works without editing a bunch of obscure files, downloading 100 packages, configuring some more stuff, troubleshooting a lot. i finally got beep media player and plugins to work without any problems.. until now. i install kubuntu-desktop and played with that. beep-media-player still works in that, but i went back into gnome, ran beep-media-player, and it exited right after it loaded. i ran it from a terminal and got:

wilywampa@wilywampa:~$ beep-media-player
The program 'beep-media-player' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadAccess (attempt to access private resource denied)'.
  (Details: serial 7 error_code 10 request_code 33 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

i can run it if i do "sudo beep-media-player" but why should i have to do that? i wish this friggin thing would at least tell me WHAT private resource it can't access. oh, i tried installing beep media player again from the source, but that didn't fix anything. maybe it would if stuff could actually be uninstalled properly.

thanks for any help. i'm about ready to go back to windows, because what's the point if everything is this much trouble?

---

### Post by kingbilly on 2005-09-06
[QUOTE=wilywampa]
maybe it would if stuff could actually be uninstalled properly.
[/QUOTE]

i don't know if this will help, but did you try:

     apt-get remove beep-media-player

and then do a re-install?

---

### Post by wilywampa on 2005-09-06
that would only work if i had installed it through apt. originally i did, but the version through apt and actually even the newest source has a bug that causes a plugin i need to crash the player. it's also weird that now it works in KDE but not in gnome

---

### Post by wilywampa on 2005-09-06
fixed by deleting config file. simple enough.

---

