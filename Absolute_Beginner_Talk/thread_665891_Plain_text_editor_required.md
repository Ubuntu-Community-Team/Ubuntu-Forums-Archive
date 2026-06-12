---
title: "Plain text editor required"
date: 2008-01-12
forum: Absolute Beginner Talk
---

### Post by a.v.l on 2008-01-12
I'm looking for a text editor that will allow me to save documents as plain text. Can you suggest one please. 

Emacs only seems to work via the terminal and the text editor in 7.10 i.e. applications> accesories> text editor doesn't seem to allow me to save a document as plain text either, what else is available please.

---

### Post by maybeway36 on 2008-01-12
The text editor program can only save in plain text, I think.

---

### Post by taurus on 2008-01-12
Have you tried the basic text editor like nano or vim?

```
nano *filename*
```

---

### Post by Tenken on 2008-01-12
The text editor (gedit) should save the file as plain text, you just need to give it the .txt extension because it doesn't to it for you.

---

### Post by Rocket2DMn on 2008-01-12
> **taurus said:**
> Have you tried the basic text editor like nano or vim?

```
nano *filename*
```

He's looking for a non terminal text editor.

Per your last post, emacs can be run from the GUI.  I noted there it should be under Applications->Programming , but you may have to enable the submenu by right clicking Applications and selecting Edit Menus.  You should also be able to right click a text document and Open With-> Emacs

---

### Post by maybeway36 on 2008-01-12
You can also try mousepad.

---

### Post by krendar on 2008-01-12
gEdit (Applications | Accessories | Text Editor) should save as plain text by default. What made you conclude it did not save as text? Perhaps you accidentally pressed some keycombination that inserted a non-ascii character.

---

### Post by c0met on 2008-01-12
If you don't like GEdit, then if you install WINE, you'll find that Notepad is also automatically installed. It will be located under the WINE menu.

---

### Post by naugiedoggie on 2008-01-12
> **a.v.l said:**
> I'm looking for a text editor that will allow me to save documents as plain text. Can you suggest one please. 

Emacs only seems to work via the terminal and the text editor in 7.10 i.e. applications> accesories> text editor doesn't seem to allow me to save a document as plain text either, what else is available please.

If you open a terminal window in the UI and type 'emacs' and get the terminal version, then you don't have the GUI version installed.  Something like 'sudo apt-get install gtk-emacs' will  fix that.  That said, emacs may not be the best solution if you are looking for just basic small text file editing.

Vi is the standard in the linux/unix world.  Ubuntu departs from the standard by making nano the system default editor.  Nano is a descendant of the Pine mail client, it is the editor in that software detached from the mailer.  I personally will not use it.  Vi is easier to use (and that is saying something). 

I'm a longtime emacs user, myself, but you probably need to be more clear about your editing goals to get the best answer to the question.  For complex editing tasks like programming, writing TeX documents and similar tasks, I don't think you can beat emacs.  But for plain editing of plain (small) text files, I generally use vi unless I happen to be already in emacs.

Thanks.

mp

---

### Post by a.v.l on 2008-01-12
> **naugiedoggie said:**
> If you open a terminal window in the UI and type 'emacs' and get the terminal version, then you don't have the GUI version installed.  Something like 'sudo apt-get install gtk-emacs' will  fix that.  That said, emacs may not be the best solution if you are looking for just basic small text file editing.

Vi is the standard in the linux/unix world.  Ubuntu departs from the standard by making nano the system default editor.  Nano is a descendant of the Pine mail client, it is the editor in that software detached from the mailer.  I personally will not use it.  Vi is easier to use (and that is saying something). 

I'm a longtime emacs user, myself, but you probably need to be more clear about your editing goals to get the best answer to the question.  For complex editing tasks like programming, writing TeX documents and similar tasks, I don't think you can beat emacs.  But for plain editing of plain (small) text files, I generally use vi unless I happen to be already in emacs.

Thanks.

mp


Thanks everyone. my aims are to learn and rewrite my website using CSS formatting and the book I've bought recommends I use a plain text editor to practice with.This will not save any formatting from my website when I copy and past the text. The recommendations in the book were to use vi, vim or emacs. I could not find vi or vim in synaptics, hence my request..

---

### Post by jrusso2 on 2008-01-12
gvim is a gui version of vim

---

### Post by Dr Small on 2008-01-12
If you use gEdit, it has CSS syntax highlighting, which is helpful.
I program in Php and gEdit is quite useful with syntax hightlighting ;)

Dr Small

---

### Post by krendar on 2008-01-12
> **a.v.l said:**
> Thanks everyone. my aims are to learn and rewrite my website using CSS formatting and the book I've bought recommends I use a plain text editor to practice with.This will not save any formatting from my website when I copy and past the text. The recommendations in the book were to use vi, vim or emacs. I could find vi or vim in synaptics, hence my request..

What the author probably means is not to use a "WYSIWYGW" html-editor so that you won't learn the html/css syntax. I recommend you try to install Bluefish via Synaptic. Bluefish is a nice HTML editor which will allow you to edit the code directly just as the author wants you to.

---

### Post by oldos2er on 2008-01-12
> **a.v.l said:**
> Thanks everyone. my aims are to learn and rewrite my website using CSS formatting and the book I've bought recommends I use a plain text editor to practice with.This will not save any formatting from my website when I copy and past the text. The recommendations in the book were to use vi, vim or emacs. I could not find vi or vim in synaptics, hence my request..

 vim should be installed by default. Type "vi" in a terminal.

---

### Post by naugiedoggie on 2008-01-12
> **a.v.l said:**
> Thanks everyone. my aims are to learn and rewrite my website using CSS formatting and the book I've bought recommends I use a plain text editor to practice with.This will not save any formatting from my website when I copy and past the text. The recommendations in the book were to use vi, vim or emacs. I could not find vi or vim in synaptics, hence my request..

I haven't used the recommended software Bluefish.  It may be good.  Here's a good quick reference to [**CSS editors**]("http://tips.webdesign10.com/good-css-editor-for-linux-ubuntu").  One of the items suggested there is [**jEdit**]("http://www.jedit.org").  That is a tool I can recommend.  You can get plugins for almost everything, including CSS and HTML editing.

I think the advice to use a text editor, as opposed to an IDE that allows you to build pages in a "design mode," is good advice.  Once you have learned the basics of CSS and HTML (and it's not rocket science), the design tools provide useful shortcuts.  One advantage of a site editor (IDE) is that it allows you to create/review the total structure of the site, while you are working on it.  

Thanks.

mp

---

### Post by szymon_g on 2008-01-12
vim (ang gVim - vim-full package ;p) rulez ;p

---

### Post by blueridgedog on 2008-01-12
In actuality (IMHO) in Ubuntu/Linux it would be hard to find something that saved a file in a non text format.  I think the previous posters listed the majority of what is available, but I second the bluefish and also recommend AptanaStudio.

(as an aside, I had to install AptanaStudio and run it the first time as root, as it wants to install updates on the fly.  Once installed I could run the application as a normal user, but the "hold your mouth right" trick would have thrown someone without Linux experience a curve)

---

