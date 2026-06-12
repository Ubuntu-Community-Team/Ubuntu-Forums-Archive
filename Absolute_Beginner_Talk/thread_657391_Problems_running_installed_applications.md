---
title: "Problems running installed applications"
date: 2008-01-03
forum: Absolute Beginner Talk
---

### Post by anvivapre on 2008-01-03
I have installed a number of applications via synaptic and GDebi. They are installed. They're there. I can see that they're there. I can even run their names in the terminal so I know for sure that they have been installed. The terminal displays information about each of the apps but does not launch them which I find I find strange because all other installed programs are launched when you do this.

Am I missing something here or is xubuntu so vastly different from ubuntu that I need to do something special.

It's quite strange that some programs appear in the applications menu when installed and other do not.

Any help would be greatly appreciated.

---

### Post by jan quark on 2008-01-03
which applications do not run properly?

---

### Post by anvivapre on 2008-01-03
Thanks for replying.

The applications in question are in fact interactive fiction interpreters; Gargoyle and Frotz.

I also managed to install version 6 of Inform via synaptic and even this does not run from the terminal. 

Very strange. Any ideas?

---

### Post by twiceasworn on 2008-01-03
Are you getting any sort of errors?  It should at least spit something out at you when you try to run it?

---

### Post by Seisen on 2008-01-03
Also some applications you have to enter it a certain way in the terminal. For example for weechat you have to enter ```
weechat-curses
``` in the terminal to get it to run. I would check the documentation for the program you are trying to use sometimes it will have what command you have to run in the terminal.

---

### Post by anvivapre on 2008-01-03
When trying to run Inform 6. I simply type in inform into the terminal.

This is what I get:

[I]Inform 6.30 for Linux (27th Feb 2004)

This program is a compiler of Infocom format (also called "Z-machine")
story files: copyright (c) Graham Nelson 1993 - 2004.

Usage: "inform [commands...] <file1> [<file2>]"

<file1> is the Inform source file of the game to be compiled. <file2>,
if given, overrides the filename Inform would normally use for the
compiled output.  Try "inform -h1" for file-naming conventions.

One or more words can be supplied as "commands". These may be:

  -switches     a list of compiler switches, 1 or 2 letter
                (see "inform -h2" for the full range)

  +dir          set Include_Path to this directory
  +PATH=dir     change the PATH to this directory

  $...          one of the following memory commands:
     $list            list current memory allocation settings
     $huge            make standard "huge game" settings (default)
     $large           make standard "large game" settings
     $small           make standard "small game" settings
     $?SETTING        explain briefly what SETTING is for
     $SETTING=number  change SETTING to given number

  (filename)    read in a list of commands (in the format above)
                from this "setup file"

For example: "inform -dexs $huge curses".

For fuller information, see the Inform Designer's Manual.[/I]

[No compilation requested]

I would be lying if I said that I understood any of this!!

---

