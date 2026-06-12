---
title: "Recent Emacs Update has messed some things up..."
date: 2007-08-18
forum: Absolute Beginner Talk
---

### Post by Rapidsnow on 2007-08-18
I am fairly new to programming with emacs and I know nothing about it really. I spent about 2 hours last week looking for commands to put into my .emacs file to get it working. So I finally got everything except for bold font faces working (still searching for that,) I then installed the emacs update today and now when I open emacs it doesn't read the .emacs file and it has all of the default settings. Can anyone help me out?

I'm not sure if there is an equivalent to .emacs in this new version, but if not, can someone help me link the old emacs to the emacs command in the terminal? 

My last part of this question is how to set the font to 10 Courier Bold from .emacs if I can get it working again.

---

### Post by jpkotta on 2007-08-19
To debug your ~/.emacs file, open it in Emacs.  Set "Enter Debugger on error" in Options and run "Evaluate Buffer" from the Elisp menu.  

I hope you are not adding all of your customizations by hand.  Sometimes you need to hand-edit, but for most things, I use the built-in configuration system, and the only hard thing about that is that there are so many options.  They are generally well documented.  

Also, I had been using GNU Emacs, but I just switched to XEmacs this weekend, I and have to say it is easier to use.  I only had some trouble with tabbar and CUA from emacs-goodies-el, but I decided that the XEmacs tabs were good enough and there is an XEmacs version of CUA mode.  The final straw with GNU Emacs was lack of horizontal scroll bars.

The Emacs wiki ([http://www.emacswiki.org/cgi-bin/wiki](http://www.emacswiki.org/cgi-bin/wiki)) is great.

---

### Post by jpkotta on 2007-08-19
Oh yeah, if you want to set the font, Options -> Customize Emacs -> Specific Face -> default<enter>.  All other faces (font+style) are inherited from this face.

---

### Post by Rapidsnow on 2007-08-19
Actually I already had my .emacs file working and yes I do all of the coding by hand, but if it messes up I just fix it. The problem is that the working .emacs file isn't being read by the new version of emacs.

---

### Post by jpkotta on 2007-08-20
[http://www.gnu.org/software/emacs/manual/html_node/emacs/Init-File.html](http://www.gnu.org/software/emacs/manual/html_node/emacs/Init-File.html)

---

