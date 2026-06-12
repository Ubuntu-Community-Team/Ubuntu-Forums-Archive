---
title: "how to copy using vim"
date: 2007-04-02
forum: Absolute Beginner Talk
---

### Post by gil michael on 2007-04-02
Hi,
how can i copy a block of code using vim? (in other windows-based editors i would mark the piece of code, right-click - copy & pase)

thanks

---

### Post by tunggul on 2007-04-02
- press ESCAPE to change into command mode
- put cursor on the beginning of textblock you want to copy
- press v (vim will enter VISUAL mode)
- move cursor to the end of textblock
- press 'y' to copy (or 'x' for cut operation)
- move cursor to the place you want to paste the text, then press 'p'

If you work in X, you can also block text using mouse, enter vim's EDIT mode (press INSERT, or 'a'), then press the middle-button to paste the text

---

### Post by RedSquirrel on 2007-04-02
Also, if you can count (at a glance) how many lines you want to copy, put the cursor anywhere on the first line you want to copy and then do (in command mode): nyy, where n is the number of lines you want to copy (e.g., 5yy). Then move the cursor to where you want to paste the lines and press p (in command mode, of course).

---

### Post by Syntaxius on 2008-01-06
> **tunggul said:**
> - press ESCAPE to change into command mode
- put cursor on the beginning of textblock you want to copy
- press v (vim will enter VISUAL mode)
- move cursor to the end of textblock
- press 'y' to copy (or 'x' for cut operation)
- move cursor to the place you want to paste the text, then press 'p'

If you work in X, you can also block text using mouse, enter vim's EDIT mode (press INSERT, or 'a'), then press the middle-button to paste the text


This was really an good and straight on answer. Big thx!

---

### Post by geirha on 2008-01-06
Use v to select only parts of a line,
use Shift+v to select full lines
and use Ctrl+v to select a rectangular block

(with the same procedure as tunggul posted)

---

### Post by Gen2ly on 2008-03-13
A more... ambitious question...  What if I need to put text into the X server clipboard so I can right-click in Open Office and copy text there?

---

### Post by scorp123 on 2008-03-13
> **Dirk.R.Gently said:**
>  What if I need to put text into the X server clipboard so I can right-click in Open Office and copy text there? You could use vi's graphical cousin: **gvim** ... If you have to edit files as root you could use "sudo", e.g.  **sudo gvim /path/to/file**

Ubuntu ships with a very limited version of "vi" (and it's sad they do this!) so in order to get "gvim" (and many other goodies such as improved syntax highlighting) I'd recommend to install the "vim-full" package on a desktop system: ```
sudo apt-get update
sudo apt-get install vim-full
```

So with this you'd have your "vi" (= **gvim** in this case) on your GUI too (e.g. together with OpenOffice) and you can copy & paste stuff easily, e.g. **gvim** has menus too and it works as any other GUI program with menus and options where you'd expect them, you're not really forced to use those cryptic commands (but you can use them too if you want to).

As for copy & paste on X11 in general: You can highlight stuff with your left mouse button (e.g. text from a terminal window) and then press the middle mouse button in most other applications: this will instantly copy & paste the highlighted text.

---

### Post by reenen on 2008-07-03
To copy text across different versions of vim, you can use the + register:

Eg, to select a line of text in a vim session, and copy to a different instance of vim:

In the first instance, highlight, select + register, and yank (save) to it:
Shift-v
"+y

In the second vim, select + register, and paste from it:
"+p

To copy and paste from and to the select buffer, use the * register, eg:
"*p
To paste from a mouse highlighted selection.

See [http://www.vim.org/tips/tip.php?tip_id=984](http://www.vim.org/tips/tip.php?tip_id=984) (have a look at the comments)

---

