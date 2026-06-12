---
title: "Shell and sound cards problems."
date: 2006-11-13
forum: Absolute Beginner Talk
---

### Post by Otsuko on 2006-11-13
Hello all, Im new to Ubuntu and excited to use something other than M$. This is the first time I have used any GNU/Linux type OS and im still getting used to all of the unique new words and programs.

On to my problem. It orriginally seemed to be a simple problem, yet its caused much frustration and confution.

First: What exactly is shell? As far as I know, shell is linux's command prompt. I do not know how to get to it from the desktop and I have reset the system to go to GRUB. I have seen this multiple times for a way to have your OS recognize your sound card. I tried typing "aplay -l" in GRUB, and got a "unreccognized command" type of responce (I dont recall the actual line -_-;)

next, I right click my volume control and go to "open volume control" only to get "No volume control GStreamer plugins and/or devices found." I then went to the package manager to install them. all were installed, yet the sound card was not recognized. I am using a Riptide HSF 56k PCI Modem that has a sound integrated.

Many thanks, Otsu

---

### Post by bodhi.zazen on 2006-11-13
> **Otsuko said:**
> Hello all, Im new to Ubuntu and excited to use something other than M$. This is the first time I have used any GNU/Linix type OS and im still getting used to all of the unique new words and programs.

Welcome in from the cold... :p

> On to my problem. It orriginally seemed to be a simple problem, yet its caused much frustration and confution.

First: What exactly is shell? As far as I know, shell is linix's command prompt.

Almost. The shell is the program that interprets the commands you enter at the prompt. Linux uses bash, but there are others (csh, zsh, korn ...).

> I do not know how to get to it from the desktop and I have reset the system to go to GRUB.

You can go to the CLI via[list=number][*]Ctrl-Alt F1, Ctrl-
Alt-F2, .... Ctrl-Alt-F6.

[*]**Ctrl-Alt-F7** will return you to X, your GUI, gnome.
[*]From gnome select terminal in your menu to start a terminal.[*]I always add a launcher to the gnome menu for a terminal.[/list]
> I have seen this multiple times for a way to have your OS recognize your sound card. I tried typing "aplay -l" in GRUB, and got a "unreccognized command" type of responce (I dont recall the actual line -_-;)

next, I right click my volume control and go to "open volume control" only to get "No volume control GStreamer plugins and/or devices found." I then went to the package manager to install them. all were installed, yet the sound card was not recognized. I am using a Riptide HSF 56k PCI Modem that has a sound integrated.

Many thanks, Otsu

Not sure about your sound.  Unmute sound ? ?Re-boot

---

### Post by Otsuko on 2006-11-14
Thank you for letting me in...now wheres the hot chocolate?

anywho, I found the terminal under the apps and added it to my desktop.
My sound is not muted, and the sound works on the Win XP I have on the other drive. I might have to get a new sound card, but if not, then the better. Any help is appreciated.

---

### Post by Bachstelze on 2006-11-14
It would help if you told us what kind of soundcard you have, please paste the output of the command *lspci*.

---

### Post by ReaderRat on 2006-11-14
The CLI is the Command Line Interface (the Terminal)-FYI.I would suggest, if you get a new sound card, be sure it is supported and fairly easy to install. You may check at Hardware Compatibility List below in my signature.

---

### Post by Otsuko on 2006-11-14
> **HymnToLife said:**
> It would help if you told us what kind of soundcard you have, please paste the output of the command *lspci*.

0000:01:09.0 Multimedia audio controller: Rockwell International: Unknown device  4310
        Subsystem: Risq Modular Systems, Inc.: Unknown device 4310
        Flags: bus master, fast Back2Back, medium devsel, latency 64, IRQ 5
        I/O ports at 2400 [size=64]
        Capabilities: <available only to root>

It's a Rockwell International. It's a 56k modem with integrated sound on it.

---

