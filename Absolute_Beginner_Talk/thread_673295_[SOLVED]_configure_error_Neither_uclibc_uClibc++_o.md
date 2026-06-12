---
title: "[SOLVED] configure: error: Neither uclibc uClibc++ or standard gcc stdc++ libraries f"
date: 2008-01-20
forum: Absolute Beginner Talk
---

### Post by Mark_in_Hollywood on 2008-01-20
configure: error: Neither uclibc uClibc++ or standard gcc stdc++ libraries found.

that's the last message from trying to figure kismet:

mark@Lexington-19:/tmp/kismet-2007-10-R1$ ./configure

I tried using Synaptic to install many, many files & libs from searching for uclibc uClibc++ and gcc stdc++ as well. 

40 meg of files later, kismet still says it can't find what it needs.

What gives here? I had installed kismet from Synaptic. doing: sudo kismet returned:

mark@Lexington-19:~$ sudo kismet
[sudo] password for mark:
Server options:  none
Client options:  none
Starting server...
Waiting for server to start before starting UI...
Suid priv-dropping disabled.  This may not be secure.
No specific sources given to be enabled, all will be enabled.
Enabling channel hopping.
Enabling channel splitting.
NOTICE: Disabling channel hopping, no enabled sources are able to change channel.
Source 0 (addme): Opening none source interface none...
FATAL: Please configure at least one packet source.  Kismet will not function if no packet sources are defined in kismet.conf or on the command line.  Please read the README for more information about configuring Kismet.
Kismet exiting.
[1] + Done(1)                    ${BIN}/kismet_server --silent ${server}
mark@Lexington-19:~$ locate kismet

/usr/share/pixmaps/gtali/kismet6.svg
/usr/share/pixmaps/gtali/kismet-none.svg
/usr/share/pixmaps/gtali/kismet1.svg
/usr/share/pixmaps/gtali/kismet5.svg
/usr/share/pixmaps/gtali/kismet3.svg
/usr/share/pixmaps/gtali/kismet2.svg
/usr/share/pixmaps/gtali/kismet4.svg

so I uninstalled kismet via Synaptic and downloaded it from the kismet webpage. 

1) is there a best way to install kismet

2) do I now need to uninstall the kismet webpage d/l and reinstall via Synaptic or what?

---

### Post by Paul820 on 2008-01-20
Do you have **build-essentia**l installed? It can't find the standard C++ libraries:
> configure: error: Neither uclibc uClibc++ or standard gcc stdc++ libraries found.

---

### Post by Mark_in_Hollywood on 2008-01-20
OK, I used synaptic to install build-essential. I then used syn. to re-install kismet. Please see below:

mark@Lexington-19:~$ locate kismet

/usr/share/pixmaps/gtali/kismet6.svg
/usr/share/pixmaps/gtali/kismet-none.svg
/usr/share/pixmaps/gtali/kismet1.svg
/usr/share/pixmaps/gtali/kismet5.svg
/usr/share/pixmaps/gtali/kismet3.svg
/usr/share/pixmaps/gtali/kismet2.svg
/usr/share/pixmaps/gtali/kismet4.svg

pixmaps doesn't seem like a likely place for kismet. anybody get some ideas?

---

### Post by Paul820 on 2008-01-20
Instead of **locate**, type
> whereis kismet
You should find it in** /usr/bin/kismet /etc/kismet /usr/share/kismet**

---

### Post by Paul820 on 2008-01-20
> FATAL: Please configure at least one packet source.  Kismet will not function if no packet sources are defined in kismet.conf or on the command line.  Please read the README for more information about configuring Kismet.
You will find the kismet.conf file in **etc/kismet**

---

### Post by Mark_in_Hollywood on 2008-01-20
Like Emily Litella said: 'never mind'

mark@Lexington-19:~$ whereis kismet
kismet: /usr/bin/kismet /etc/kismet /usr/share/kismet /usr/share/man/man1/kismet.1.gz

cd/usr/bin/

and 

./configure

fails; as does gksudo /etc/kismet.conf

and I read the Kismet readme and only got confused. None of the instructions can be followed as given.

---

### Post by Paul820 on 2008-01-20
It's **gksudo gedit /etc/kismet/kismet.conf**

---

### Post by Mark_in_Hollywood on 2008-01-20
Thank you. I've got the kismet.conf as a sample on the desktop and will start learning how to do the config.

Now we return to the New England Patriots against the San Diego Chargers . . .

---

