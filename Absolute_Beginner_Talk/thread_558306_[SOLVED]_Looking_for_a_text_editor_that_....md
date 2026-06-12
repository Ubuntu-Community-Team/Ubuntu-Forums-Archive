---
title: "[SOLVED] Looking for a text editor that ..."
date: 2007-09-23
forum: Absolute Beginner Talk
---

### Post by Bruce M. on 2007-09-23
I'm looking for a text editor that will do 2 things:
  1.  BLOCK cut and paste, and
  2.  Spell check

Like TextPad does in M$ Windozzz-cra$h-dummy.

I have GVim ... flying the space shuttle would be easier I think
It's for programmers, not simple text files.  Although they say it does BLOCK cut and paste.  I've been trying to figure it out for a week now.

I have Gedit ... it doesn't do BLOCK cut and paste, but spell checks.

Bruce Milmine

---

### Post by IYY on 2007-09-23
I'd suggest to stick with GVim, or maybe use the Cream editor, which is a friendlier version of GVim (no command mode, can do more through the GUI menus).

vi/Vim/GVim takes a few weeks to learn but it *is* the best text editor out there, is certainly not just for programmers, and you will wonder how you've ever managed to live without it once you fully understand it.

---

### Post by ButteBlues on 2007-09-23
> **IYY said:**
> vi/Vim/GVim takes a few weeks to learn but it *is* the best text editor out there, is certainly not just for programmers, and you will wonder how you've ever managed to live without it once you fully understand it.

This thread would never be complete unless I mentioned [my editor of choice](http://dev.compiz-fusion.org/~wfarr/posts?tag=emacs). ;)

---

### Post by Bruce M. on 2007-09-23
> **IYY said:**
> I'd suggest to stick with GVim, or maybe use the Cream editor, which is a friendlier version of GVim (no command mode, can do more through the GUI menus).

vi/Vim/GVim takes a few weeks to learn but it *is* the best text editor out there, is certainly not just for programmers, and you will wonder how you've ever managed to live without it once you fully understand it.

If I install Cream, can I still use GVim by itself?

---

### Post by thisllub on 2007-09-23
> **Bruce M. said:**
> I'm looking for a text editor that will do 2 things:
  1.  BLOCK cut and paste, and
  2.  Spell check

Like TextPad does in M$ Windozzz-cra$h-dummy.

I have GVim ... flying the space shuttle would be easier I think
It's for programmers, not simple text files.  Although they say it does BLOCK cut and paste.  I've been trying to figure it out for a week now.

I have Gedit ... it doesn't do BLOCK cut and paste, but spell checks.

Bruce Milmine

move cursor to one corner of block
Ctrl-V 
move cursor to opposite corner of block
y
move cursor to new location
p

---

### Post by Bruce M. on 2007-09-25
> **thisllub said:**
> move cursor to one corner of block
Ctrl-V 
move cursor to opposite corner of block
y
move cursor to new location
p

In GVim ... gotta try that.  :)

Thanks

---

### Post by Bruce M. on 2007-09-25
That did "copy and paste" ok ... but:

It didn't "cut and paste"

Here's an example of what I want to do:

1. Go Home ..................[gh]
2. Go to the Kitchen.......[gk]

and make it look like this:

1. [gh] Go Home
2. [gk] Go to the Kitchen

Any ideas?
or ...
Can you point me to a really good Documentation file on GVim?
I have "vimbook-OPL.pdf" and I'm reading it but being a PDF doc, I can't search for something.  Still I am learning "slowly".

---

### Post by MountainX on 2008-02-04
> **IYY said:**
>  use the Cream editor, which is a friendlier version of GVim (no command mode, can do more through the GUI menus).


How do I install Cream? Thanks
UPDATE: I installed it by downloading the archive, extracting and installing without SPM. I couldn't get it through a repository for some reason. Anyway, I have it installed now.

---

### Post by MountainX on 2008-04-04
> **Bruce M. said:**
> I'm looking for a text editor that will do 2 things:
  1.  BLOCK cut and paste, and
  2.  Spell check

Like TextPad does in M$ Windozzz-cra$h-dummy.

I have GVim ... flying the space shuttle would be easier I think
It's for programmers, not simple text files.  Although they say it does BLOCK cut and paste.  I've been trying to figure it out for a week now.

I have Gedit ... it doesn't do BLOCK cut and paste, but spell checks.

Bruce Milmine

Scite does block cut and paste. They call it Rectangular regions. I tested and it does do cut and paste for the block. It works extremely well and is very easy. From the help:
"Rectangular regions of text can be selected in SciTE by holding down the Alt key on Windows or the Ctrl key on GTK+ while dragging the mouse over the text."

As far as spell checking, I am not sure if the more recent versions of SciTE directly support this or not. Below is one option from a 2005 posting - I would think there is a better way. 

Another option is "word substitution." From [http://lua-users.org/wiki/SciteWordSubstitution:](http://lua-users.org/wiki/SciteWordSubstitution:)

"This is code for a simple replace-on-the-fly facility for SciTE; it's similar to Word's ability to automatically substitute 'the' for 'teh'."

Spell Checking for SciTE 
------------------------------
1. [http://groups.google.com/group/scite-interest/](http://groups.google.com/group/scite-interest/) - post a question here

2. [http://ask.metafilter.com/25494/SciTE-aspell-on-linux-how](http://ask.metafilter.com/25494/SciTE-aspell-on-linux-how)

Here's one way:

Put this in .SciTEUser.properties:

command.name.1.*=aspell
command.1.*=/usr/X11R6/bin/rxvt -e /usr/bin/aspell check ($FileDir)/($FileNameExt)
command.subsystem.1.*=0

Mind the bit in bold; if you don't have rxvt, change that to xterm or eterm or whatever. What this'll do is open up a terminal running aspell against the document you're working on. You won't be able to use aspell to correct the spelling, since SciTE doesn't reload the document after the command executes. But it will tell you when you **** up!

---

### Post by stchman on 2008-04-04
> **IYY said:**
> I'd suggest to stick with GVim, or maybe use the Cream editor, which is a friendlier version of GVim (no command mode, can do more through the GUI menus).

vi/Vim/GVim takes a few weeks to learn but it *is* the best text editor out there, is certainly not just for programmers, and you will wonder how you've ever managed to live without it once you fully understand it.

A few weeks!!!!  Awesome.  Gedit is on of the best easiest text editor I have ever used.  I wish that Notepad++ was native to Linux.

---

### Post by Bruce M. on 2008-04-17
> **Bruce M. said:**
> Here's an example of what I want to do:

1. Go Home ..................[gh]
2. Go to the Kitchen.......[gk]

and make it look like this:

1. [gh] Go Home
2. [gk] Go to the Kitchen


Best one I found (for non programmers) is Kate, it's a KDE app, heavy, but for what I want it for as seen above it does the trick.
And since I very very seldom use a "word processor" the weight is bearable.

Bruce

---

### Post by Delkster on 2008-04-17
> **Bruce M. said:**
> Best one I found (for non programmers) is Kate, it's a KDE app, heavy, but for what I want it for as seen above it does the trick.

Seconded. If you want something with more features than Gedit but still just a plain text editor that is (relatively) easy to use and looks familiar, Kate is probably one of the better bets.

It's got some of its own issues, e.g. I still can't get over some of its configuration, but it's probably worth trying. It's a KDE application and requires some KDE libraries but works decently on Gnome.

---

### Post by Bruce M. on 2008-04-17
> **Delkster said:**
> Seconded. If you want something with more features than Gedit but still just a plain text editor that is (relatively) easy to use and looks familiar, Kate is probably one of the better bets.

It's got some of its own issues, e.g. I still can't get over some of its configuration, but it's probably worth trying. It's a KDE application and requires some KDE libraries but works decently on Gnome.

Works well in Xfce too.  :)

---

