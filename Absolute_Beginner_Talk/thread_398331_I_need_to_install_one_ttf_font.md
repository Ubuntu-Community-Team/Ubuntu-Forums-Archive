---
title: "I need to install one ttf font"
date: 2007-03-31
forum: Absolute Beginner Talk
---

### Post by ausbun on 2007-03-31
I have downloaded a ttf file of a font called Curlz MT. It doesn't come with Unbunt and it was my wife's favorite for her kindergarten letters back when I was a slave of Bill Gates'.

Can I simply move the file from my desktop into a font folder? I have searched my computer for a fonts folder and can't find it!

I have searched the forums and have seen instructions for downloading lots of fonts at once, but nothing about a single font.

Thanks in advance for any advice.

---

### Post by true_friend on 2007-03-31
open up terminal and give this command
> gksudo Nautilus
U will be asked passwod give ur password. Then it will open up Nautilus the file manager for gnome(Ubuntu)
here find the place where u have that font file copy it and then give this command in address bar >>>>>fonts:
u will have fonts folder opened there are two possibilites personal and system wide i always choose system wide open it up and copy the font file there. This file should be available in newly started applications otherwise a simple restrat will help.
Regards
True_Friend

---

### Post by david_kt on 2007-03-31
Make a directory in your home folder. Open your home folderl:
[INDENT]Places>Home Folder[/INDENT]

Make a .font directory:

    File> Create Folder and name it .fonts

Make the folder visible:

    View>Show Hidden Files

Copy/extract whatever fonts you want to install in this folder.

Open terminal:

    Applications>Accesories>Terminal

copy and paste below command and enter:

    fc-cache -f -v

Check this thread if you have difficulties:
[http://ubuntuforums.org/showthread.php?p=2349636#post2349636](http://ubuntuforums.org/showthread.php?p=2349636#post2349636)

DK

---

### Post by ausbun on 2007-03-31
When I do the gksudo command, it tells me:

sudo: Nautilus: command not found

What next?

---

### Post by qamelian on 2007-03-31
> **ausbun said:**
> When I do the gksudo command, it tells me:

sudo: Nautilus: command not found

What next?

It should be nautilus...all in lower case.

---

### Post by ausbun on 2007-03-31
DavidKT,:KS  your instructions worked!

Thanks.:)

---

### Post by true_friend on 2007-04-08
it was because linux is case sensitive.

---

