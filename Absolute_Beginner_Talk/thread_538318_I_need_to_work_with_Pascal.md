---
title: "I need to work with Pascal"
date: 2007-08-29
forum: Absolute Beginner Talk
---

### Post by vandroiy.cl on 2007-08-29
Hi
i need to use pascal to study for a class, but I still can't get Free Pascal to work. I used Kpackager, and it shows that it is installed but i don't know how to run the program because it doesn't appear on the K Menu. Should I run it from terminal or install something else?
thanxs

---

### Post by Skrynesaver on 2007-08-31
I don't know the free pascal package, however most pascal linkers/compliers run from the terminal.  edit your source code, then if it installed a man page apropos pascal should point you at the command, failing that sudo updatedb and locate pascal should throw up an answer then calling the binary with a --help should give you an idea of how to use it.

Best of look with the class and I hope you'll be a contributor to Open Source soon ;)

---

### Post by Fingolfin on 2007-09-22
I would advise that you deinstall the existing version of Free Pascal and download the latest from the web site. It may come in the tar archive named fpc-i386-2.2-linux.tar or something like that.
Unpack it and in the command prompt run the installation script with:
% ./install.sh
That will install the compiler and additional tools.
To compile any  program.pas then just type
%fpc program.pas

For a full list of the compiler options:
% fpc -?

Free Pascal also has IDE similar to that produced by Borland many years ago for Turbo Pascal series.
To get into it, just type
% fp
from the command prompt.

Abundant documentation about Free Pascal is also available in PDf format from [www.freepascal.org](www.freepascal.org)

---

