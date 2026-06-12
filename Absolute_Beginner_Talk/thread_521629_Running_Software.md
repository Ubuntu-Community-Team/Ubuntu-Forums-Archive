---
title: "Running Software?"
date: 2007-08-09
forum: Absolute Beginner Talk
---

### Post by SeriousName on 2007-08-09
This is making me feel incredibly newbish, but here goes.

There was a program I wanted to get, TrueCrypt, which was relatively useful to me when I was running Windows. So I went and grabbed the .tar.gz file (one specifically for Ubuntu 7.04), opened it up, and opened the .deb file. Installation went fine.

Now however, my problem is that I have absolutely no idea how to access the program. It's there on my hard drive, the Synaptic Package Manager can find it, but... how am I supposed to run it?:confused:

---

### Post by rubikfreak on 2007-08-09
Is it anywhere in the applications menu?

---

### Post by SeriousName on 2007-08-09
[QUOTE=rubikfreak]Is it anywhere in the applications menu?[/QUOTE]
No, it's not.

---

### Post by raja on 2007-08-09
Type ```
truecrypt
``` in a terminal to know if it is installed and to start the application. It may not appear in the menu until the gnome-panel is restarted.

---

### Post by forestpixie on 2007-08-09
have you tried opening a terminal and running truecrypt from there

 Edit - it's that slow keyboard :)

---

### Post by oilchangeguy on 2007-08-09
go to applications, accessories, alacarte menu editor. and see if you can add it from there.

---

### Post by rubikfreak on 2007-08-09
You can make an icon on the Desktop for it by right-clicking and choosing "Create Launcher...".
From there you can fill in TrueCrypt for application name, truecrypt for command, and provide an image for the icon and write a comment if you like.

---

### Post by SeriousName on 2007-08-09
Okay, it seems to run from the terminal, at least it gives me a list of commands. However, launchers for TrueCrypt don't seem to do anything.

Does this mean I'll have to use TrueCrypt from the terminal from now on? I'd like a GUI, but I'm sure I can adjust.

---

### Post by oilchangeguy on 2007-08-09
> **SeriousName said:**
> Okay, it seems to run from the terminal, at least it gives me a list of commands. However, launchers for TrueCrypt don't seem to do anything.

Does this mean I'll have to use TrueCrypt from the terminal from now on? I'd like a GUI, but I'm sure I can adjust.

have you tried what was suggested in post #6?

---

### Post by asmoore82 on 2007-08-09
Honestly, this type of software is rediculous IMO.
Using unsupported, probably partially broken Apps like this is what leads many ppl
to destroy a perfectly good Linux system and for What?

What info is so important that you need the illusion of security?

---

### Post by oilchangeguy on 2007-08-09
> **asmoore82 said:**
> Honestly, this type of software is rediculous IMO.
Using unsupported, probably partially broken Apps like this is what leads many ppl
to destroy a perfectly good Linux system and for What?

What info is so important that you need the illusion of security?

are you sure you're in the right thread? haven't seen anything in any of the user's post's about a security issue.

---

### Post by asmoore82 on 2007-08-09
encrypting a file or set of files is the equivalent of trying to enforce
**physical** security through a **logical** means.

I.E. such a thing is theoretically flawed and practically impossible.

the first rule of securtiy is physical presence ... anyone with a live Linux CD can access
all of your files with root permission so don't worry about security at that level.
their physical presence at your box trumps your logical security.
Encryping files in an extension of the same paradigm; anyone with physical access
to your drive can walk away with it and ***eventually*** get any data they want from it.

you data is much more likely to be stolen at the network level and guess what ...
Before **you** send your data from encrypted files over the network,
**you** are decrypting the data for the intruders.

---

### Post by SeriousName on 2007-08-09
> **oilchangeguy said:**
> have you tried what was suggested in post #6?
I don't seem to have the program you suggested (I'm running 7.04). However, I did figure out how to add it into my Applications menu. Unfortunately, it seems to behave the same way as creating a desktop launcher.

---

### Post by oilchangeguy on 2007-08-09
> **asmoore82 said:**
> encrypting a file or set of files is the equivalent of trying to enforce
**physical** security through a **logical** means.

I.E. such a thing is theoretically flawed and practically impossible.

sounds like you've had way too much coffee.

---

### Post by SeriousName on 2007-08-09
@asmoore82: I may be a Linux newbie but I'm fairly experienced with computers otherwise. I understand how the program works, and it works well enough for my purposes. However, this thread was created to get help on a specific problem, not to discuss the validity of encryption programs.

EDIT: And just to clarify, my last question is if anyone happens to know if TrueCrypt can be run in a GUI in Ubuntu 7.04.

---

### Post by asmoore82 on 2007-08-09
> **SeriousName said:**
> @asmoore82: I may be a Linux newbie but I'm fairly experienced with computers otherwise. I understand how the program works, and it works well enough for my purposes. However, this thread was created to get help on a specific problem, not to discuss the validity of encryption programs.

**previous post updated**

I was just curious as to what your "purposes" were while trying to save you time and trouble
AND a performance degredation of your Linux system.

---

### Post by SeriousName on 2007-08-09
> **asmoore82 said:**
> **previous post updated**

I was just curious as to what your "purposes" were while trying to save you time and trouble
AND a performance degredation of your Linux system.

I don't wish to go into what my purposes for this program entail. My use of this program is not what this thread is about, and I'd rather you quit derailing the thread in that direction.

However, I would like to know specifically what you mean by "performance degradation." If you mean the time it takes to encrypt/decrypt files, then I already know and accept that. However, if you mean something else by that, I would be interested to know.

---

### Post by ocean223 on 2007-08-10
Ok The program that I wan,t to make a shortcut for has to be run from root. I right click on desktop
select "create launcher" what do I use for "command" I tried - sudo program name but that did'nt work. I can run from terminal with "sudo program name" however.:)

---

### Post by Erdos_3 on 2007-09-16
There is a GUI for Truecrypt in Linux - it's called Forcefield (there might be others but this one I know about) and you have to install it separately.

Unless you get Forcefield or something similar there would be no point creating a launcher for truecrypt, because it doesn't have a built-in GUI.

If you care to hear my opinion though, a GUI is not worth it. I've switched to command-line about a year ago, and am entirely satisfied. I think it's faster; not the encryption process of course, but just the process of using it.

---

