---
title: "Sixpack No Gui Mode"
date: 2007-11-14
forum: Absolute Beginner Talk
---

### Post by maracaibo on 2007-11-14
I recently installed Sixpack version 0.99.001222-6(dapper) on Mepis 6.5. It seems to run in terminal when I type:
"bib". However, I get  an error message when I try to use "bib -gui". Here's what happens:

Tadeusz@3[~]$ bib -gui
Checking /usr/share/sixpack/Bib
 Loading /usr/share/sixpack/Bib
bad option "side": must be -after, -anchor, -before, -expand, -fill, -in, -ipadx, -ipady, -padx, -pady, or -side at /usr/lib/perl5/Tk/Widget.pm line 1144.
 at /usr/bin/bib line 5445
Tadeusz@3[~]$

Also, I don't get a return path when in terminal and I type: "which sixpack". I'm wondering if I'm missing some dependencies. I have python-tk and perl-tk installed. Or,maybe, this version of the program doesn't really have a gui mode? Synaptic doesn't show any dependencies for this version. This can't be right? Well, guys, I'm stumped. Time for a happy meal!

Sincerely,
maracaibo

---

