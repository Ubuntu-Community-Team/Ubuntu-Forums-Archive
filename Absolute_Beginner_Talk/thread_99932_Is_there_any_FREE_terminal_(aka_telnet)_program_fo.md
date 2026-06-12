---
title: "Is there any FREE terminal (aka telnet) program for ubuntu..."
date: 2005-12-06
forum: Absolute Beginner Talk
---

### Post by OrAtE! on 2005-12-06
that emulates SCOANSI? i dont know where to look and the only thing i need FOR sure, when changing OS from windows is that:

1º You can read XLS files (you can with openoffice)
2º Got a terminal emulation with SCO ANSI enabled. Telneting on console does not work :(.

Thanks in advance.

---

### Post by jwd45244 on 2005-12-06
what? what about telnet?  When you login to the box you can set your TERM to whatever you need.

---

### Post by OrAtE! on 2005-12-06
sorry, i dont know what you mean... this is my first time installing ubuntu never used any linux stuff before....  can you tell me how to do that?

---

### Post by moberry on 2005-12-06
I did a quick google, and did not get much information on it. Next time you are in front of the box you need to telent into type this:
```
echo $TERM
```

see what it says, and on your box before you telnet type
```
export TERM="what ever"
```

i hope this helps... shot in the dark.

---

### Post by veehell on 2005-12-06
... on each linux you can have more command shells (bash,sh, posix, ksh,zsh....and some others) which interpret commands  and scripts and use some basic tools. for telnet you can use similar tools, in command line "telnet" "ftp" "ssh" "scp" "sftp" "tftp" and so on as on winbox cmd prompt. 
If you need SCO ANSI enviroment, you have to choose terminal / "terminals" "terminal-emulators" "x-terminal" and so on (Aterm,Xterm, RxVt, gTerm, ...and so on.) /some of them have gui to set their own variables or have config files, focus on it.

... and finally if you are win user, there is also **PuTTy** package. which provide various of "putty" tools :). Which never fails to connect to various shell accounts.
cheers

---

### Post by OrAtE! on 2005-12-06
[QUOTE=veehell]... on each linux you can have more command shells (bash,sh, posix, ksh,zsh....and some others) which interpret commands  and scripts and use some basic tools. for telnet you can use similar tools, in command line "telnet" "ftp" "ssh" "scp" "sftp" "tftp" and so on as on winbox cmd prompt. 
If you need SCO ANSI enviroment, you have to choose terminal / "terminals" "terminal-emulators" "x-terminal" and so on (Aterm,Xterm, RxVt, gTerm, ...and so on.) /some of them have gui to set their own variables or have config files, focus on it.

... and finally if you are win user, there is also **PuTTy** package. which provide various of "putty" tools :). Which never fails to connect to various shell accounts.
cheers[/QUOTE]

so? i need an external program to connect to the box? can you remeber of one free wich i can use on ubuntu 5.04?

---

### Post by jwd45244 on 2005-12-06
telnet <box>

Once you are in do what you need to do.  if the display is not as you expect contact the system adminstrator of the box and ask him/her what your "TERM" environment variable should be set to.

for most of the boxes i go to i use TERM=xterm and life is good, but not all some I have to use TERM=vt52 or TERM=vt100  

You might try TERM=ansi

---

### Post by veehell on 2005-12-06
all those apps/terms come free or under GPL/GNU/FOSS licences....you just set one favorite or two or all of them. (mean terminal). And as **jwd45244** wrote above, you need to set how your term will behave (localy on client which connect or after connection as variable in the system which you connect to).

aD_putty: i check it, putty have option especially to "SCO" enviroment (keybindings) with this also come visual change.


group.google.com have some threads check them by own self.

Some infor point to : set variable to SCOANSI on linuxbox, be sure you have ANSI on scobox. Because ANSI=means BBs ansi type (old times;), and SCOANSI is used to tell term which ansi it is. However SCO box recognize only "ANSI" (it does not care that there is/was bbs-ansi.

---

### Post by OrAtE! on 2005-12-07
Dude can please speak plain english? sorry if im a little slow...  but im really n00b on linux, have no idea where to download appz, have no idea how to install...    or how to do it...   can you post someone step by step?  im really going nowhere ATM with this... :(

---

### Post by The Mekon on 2005-12-07
I did a Google search which lead me, via the Suse forums, to a program called minicom.  I checked with Synaptic and found that it is there.

This is the description;

friendly menu driven serial communication program
Minicom is a clone of the MS-DOS "Telix" communication program. It emulates
ANSI and VT102 terminals, has a dialing directory and auto zmodem download.
backports for the stable Debian release are provided at Minicom's upstream
homepage, which can be found at [http://alioth.debian.org/projects/minicom/](http://alioth.debian.org/projects/minicom/).

There is an associated program modemu on Synaptic which is described as:

Telnet services for communication programs
modemu is a program that lets you telnet to remote sites using
any standard communications program such as Minicom or Seyon.
It emulates a modem, including options for 8-bit clean mode so
one can use Zmodem or Kermit over a telnet connection.

It can also be used for other tasks, such as UUCP over telnet.


I hope that this is clear enough.

---

### Post by cwaldbieser on 2005-12-07
[QUOTE=OrAtE!]Dude can please speak plain english? sorry if im a little slow...  but im really n00b on linux, have no idea where to download appz, have no idea how to install...    or how to do it...   can you post someone step by step?  im really going nowhere ATM with this... :([/QUOTE]
For what you want to do, you don't really need to download anything.  You can open the terminal (Applications -> Accessories -> Terminal).  The $ is a prompt like C:\> in Windows.  You just type these commands:
```

$ export TERM=vt100
$ telnet computer-name-or-address

```
In this example, I set the terminal type to vt100.  If you don't know what the exact terminal type is called, you just need to ask the sysadmin who runs the telnet server.  He or she should understand.
The "computer-name-or-address" part just gets replaced with the name of the computer or the address.  For example, 192.168.0.2.

---

