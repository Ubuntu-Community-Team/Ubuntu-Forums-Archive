---
title: "Installing texlive"
date: 2006-11-09
forum: Absolute Beginner Talk
---

### Post by col_b on 2006-11-09
Hello,

This really is a noob question....

I've just installed texlive using Synaptic.  I've typed tex -version to get version info to see if it's working, and it is.

My question is, where does Synaptic install texlive to?

Cheers,
Col

---

### Post by localuser on 2006-11-09
There are a couple of things you can do...

whereis command at the command prompt:
```
$ whereis xxx
```

In Synaptic Package Manager:
Find the package, right-click, Properties, Installed Files tab

---

### Post by col_b on 2006-11-09
Thanks localuser! :) :) :)

---

### Post by col_b on 2006-11-09
OK. I need a bit of help on this one...

 I installed ubuntu the other day.  Everything is sweet.

I use latex and texnic center in windows, so I'm trying to install latex in ubuntu.  I found a few tutorials and used Synaptic to install texlive and Kile.  texlive is installed and seems to be working, i.e. it displays version info when i type tex -version.

Now, I'm trying to use kile to compile a .tex document, which I know is coded correctly.  But, I get loads of undefined control sequences when i run tex, and the .dvi output is messed up.  Does kile need configured or something?

I appreciate your help.
Cheers,
Col

---

### Post by aikishugyo on 2006-12-22
if it's undefined control sequences, this means macros are undefined. Ergo, you are using some macros in your latex document which your installation does not know about. The best thing to do is simplify your document to basics that must be in every tex installation, wrt classes, packages and options. Then try again, and if asking for help, try to include the critical output. HTH

---

