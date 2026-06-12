---
title: "Changing fonts in Emacs"
date: 2007-05-13
forum: Absolute Beginner Talk
---

### Post by O-pos on 2007-05-13
Hello,

I'm using Emacs21 for statistical calculations. When I installed emacs, both GUI window and fonts was looking very ugly. I downloaded emacs-snapshot-gtk and now the window is ok, but that ugly font remained. So now I want to change the font. I'd like very much to use the same font my emacs that is default one for GNOME-Terminal. Any ideas how can I do that?

Thanks in advance,

O-pos

---

### Post by laptoplinux on 2007-05-18
Here's a few quick tips.  Hope these help:

First, this site offers a way to get antialiased fonts in Emacs :

[http://peadrop.com/blog/2007/01/06/pretty-emacs/](http://peadrop.com/blog/2007/01/06/pretty-emacs/)

(the instructions were written with an Ubuntu distro in mind)

Secondly, you can change the font for that specific session by holding shift and clicking on the left mouse button in the emacs window.  Use the menu that appears to change to a better font.  But that only holds for that session.

To change the fonts permanently, edit your .emacs file (notice the dot in front of emacs).

Every user has a .emacs file in their home directory that configures the behavior of their emacs sessions.  You can change the font in the .emacs file to any of the choices in the font menu I mentioned.  

Now, there are all kinds of ways to customize a .emacs file, so it's probably best if I point you to a helpful example:

[http://www.geocities.com/kensanata/dot-emacs.html](http://www.geocities.com/kensanata/dot-emacs.html)

And here is an example of two possible lines to change the font in a .emacs file:
```
(set-default-font "9x15")
```
 
```
(set-default-font "Bitstream Vera Sans Mono-10") 
```

---

### Post by mopi on 2007-06-26
```
(set-default-font "Bitstream Vera Sans Mono-10") 
```

I used that code but it gives me this error:

```

An error has occurred while loading `/home/mopi/.emacs.d/init.el':

error: Font `Bitstream Vera Sans Mono-10' is not defined

```

I can select Bitstream Vera Sans Mono in System -> Preferences -> Font so I guess it's there.

I have built emacs 22.1 from sources with the following options:
./configure --with-gtk --with-jpeg --with-png --with-xpm --with-gif --enable-font-backend --with-xft

What am I missing?

---

### Post by Kelsin on 2007-06-28
> **mopi said:**
> I have built emacs 22.1 from sources with the following options:
./configure --with-gtk --with-jpeg --with-png --with-xpm --with-gif --enable-font-backend --with-xft

What am I missing?

Unless you edited the source first you might need to run emacs with the --enable-font-backend flag like:

```
emacs --enable-font-backend
```

---

### Post by mopi on 2007-06-29
Still doesn't work. When running emacs with this option
```
 emacs --enable-font-backend
```

I get this message in  *Messages* buffer

```

("emacs" "--enable-font-backend")


An error has occurred while loading `/home/mopi/.emacs.d/init.el':

error: Font `Bitstream Vera Sans Mono-10' is not defined

To ensure normal operation, you should investigate and remove the
cause of the error in your initialization file.  Start Emacs with
the `--debug-init' option to view a complete error backtrace.

command-line-1: Unknown option `--enable-font-backend'
```

---

### Post by mopi on 2007-07-08
After some investigation I have come to the conclusion that emacs 22 doesn't support setting the font in that way. An alternative is to use the alpha version of emacs 23 that does indeed support it. 

On 32 bit systems there are very easy descriptions how to install it here:
[http://peadrop.com/blog/2007/01/06/pretty-emacs/]("http://peadrop.com/blog/2007/01/06/pretty-emacs/")

On other systems you have to compile it yourself and it is described here:
[http://peadrop.com/blog/2007/04/13/pretty-emacs-compile-guide-for-unsupported-platforms/]("http://peadrop.com/blog/2007/04/13/pretty-emacs-compile-guide-for-unsupported-platforms/")

---

### Post by sfjohnsen on 2008-02-23
For me laptoplinux' hint works fine with the standard emacs 22 comming with Gutsy. In my case, the reason the setting was not read before was a line prior to that containing the font specification in which it was attempted to load a Lisp library that was not installed.
After having removed that line the "(set-default-font "9x15")" instruction was properly executed.

But I have to add that the error message which I received was a different from that of mopi.

---

