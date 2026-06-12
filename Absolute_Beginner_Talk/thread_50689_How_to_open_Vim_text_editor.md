---
title: "How to open Vim text editor?"
date: 2005-07-21
forum: Absolute Beginner Talk
---

### Post by stig on 2005-07-21
Hi,
I want to open the Vim text editor but cannot find it in any menus.

If I type vim in the Run window it doesn't do anything.

If I type vim in the terminal it just gives me details of Vim version etc but it does not look anything like the appearance of Vim in screenshots on the Vim web page. It seems still to be the terminal.

In Windows I would simply go to Program Manager and look for the Vim folder then the .exe file and then click on it to open the package - and then make a link to it.

What do I do in Linux?

---

### Post by poofyhairguy on 2005-07-21
seems like there is a gnoem version, not just a terminal version.

[http://packages.ubuntu.com/hoary/editors/vim-gnome](http://packages.ubuntu.com/hoary/editors/vim-gnome)

> sudo apt-get install vim-gnome

---

### Post by stig on 2005-07-21
[QUOTE=poofyhairguy]seems like there is a gnoem version, not just a terminal version.

[http://packages.ubuntu.com/hoary/editors/vim-gnome](http://packages.ubuntu.com/hoary/editors/vim-gnome)[/QUOTE]

I also tried downloading and installing this using Synaptic but get the same results as already described (equally whether I type vim or vim-gnome).

---

### Post by agger on 2005-07-21
[QUOTE=stig]I also tried downloading and installing this using Synaptic but get the same results as already described (equally whether I type vim or vim-gnome).[/QUOTE]
 The Vim GUI application to run under Gnome is called gvim - try typing "gvim" in the
terminal.

If you type "vi" in the terminal you also get vim, but the terminal/console version,
not the Gui version (apparently there is no "real" vi in Ubuntu, but it's also not
necessary since it functionality is a subset of vim's anyway).

---

### Post by stig on 2005-07-21
[QUOTE=agger]The Vim GUI application to run under Gnome is called gvim - try typing "gvim" in the terminal.
[/QUOTE]

Thanks, that's great!! gvim opens it OK - but how do I make an icon or an entry in the Gnome panel so that I don't need to open terminal each time I want to start it?

---

### Post by Wolki on 2005-07-21
[QUOTE=stig]Thanks, that's great!! gvim opens it OK - but how do I make an icon or an entry in the Gnome panel so that I don't need to open terminal each time I want to start it?[/QUOTE]

right-click on panel -> add to panel -> Custom Application -> you get a dialog. Change Name to whatever you like, and enter "gvim" (without quotes) into the command field. choose an Icon you like, and click ok.

That said, vi is not exactly the the most friendly text editor, but if it works for you... :)

---

### Post by stig on 2005-07-21
[QUOTE=Wolki]That said, vi is not exactly the the most friendly text editor, but if it works for you... :)[/QUOTE]

What I'm trying to find is one that will do things like letting me search & replace across lots of files opened in tabs at the same time (open 10 files, replace in all 10 at once) and to define my own tags for inserting in text. Gedit, for example, doesn't seem to have this type of replace function and although it has tags, I don't see any way of making my own.

In Windows I use EditPadPro ([http://www.editpadpro.com/index.html](http://www.editpadpro.com/index.html)) and find it very good. There is a Linux version but I'd hoped to get something similar that was in an ubuntu rep and easy to install  :)

---

### Post by agger on 2005-07-21
[QUOTE=stig]What I'm trying to find is one that will do things like letting me search & replace across lots of files opened in tabs at the same time (open 10 files, replace in all 10 at once) and to define my own tags for inserting in text. Gedit, for example, doesn't seem to have this type of replace function and although it has tags, I don't see any way of making my own.

In Windows I use EditPadPro ([http://www.editpadpro.com/index.html](http://www.editpadpro.com/index.html)) and find it very good. There is a Linux version but I'd hoped to get something similar that was in an ubuntu rep and easy to install  :)[/QUOTE]
 Vi(m) has a high learning curve, but once you've learned it, it's a very powerful and still very lightweight editor.

It doesn't have tabbed editing, though - but you can repeat the same commands in multiple buffers ...

---

