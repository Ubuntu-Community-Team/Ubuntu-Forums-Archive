---
title: "Edit files over SSH"
date: 2006-03-02
forum: Absolute Beginner Talk
---

### Post by ClareJonsson on 2006-03-02
Hia,

How do I edit a file in the CLI via SSH? I tried emacs and it looks like I don't have that installed. gedit obviously won't work as I'm not logged into gnome on the actual machine.

TTFN,
Clare.

---

### Post by jpkotta on 2006-03-02
Emacs is easy to install.  ```
sudo apt-get install emacs21
```
Yes, you have to install it on the remote machine.  You can read the tutorial (it's on the startup screen) and realize why Emacs is so powerful.  Other text-mode editors are vim and nano, which are probably installed already.

On the other hand, read the SSH article in the wiki, and learn how to turn on X forwarding.  Then you can do ```
ssh -X -C user@host
``` to display X clients from the remote machine on the local machine.

---

### Post by ClareJonsson on 2006-03-02
Excelent, thanks for that, I just installed it via SSH.

I am liking linux more and more each day. You know what this reminds me of, my old Amiga :D .

---

### Post by phen on 2006-03-02
I am using Xemacs piped over SSH to my laptop just in this second :-)

its very user friendly...

---

### Post by darth_vector on 2006-03-02
tooooo many emacs ppl around here!!! vi (or vim) is the one true text editor ;-)

failing that, nano (a pico clone) is installed by default on ubuntu. both are text editors that run in a shell.

---

### Post by Sweet on 2006-03-02
[QUOTE=darth_vector]tooooo many emacs ppl around here!!! vi (or vim) is the one true text editor ;-)

failing that, nano (a pico clone) is installed by default on ubuntu. both are text editors that run in a shell.[/QUOTE]

Yeah, emacs is too complicated, so is VI in my opinion. pico & nano are simple and easy to use :)

---

### Post by wrtrdood on 2006-03-02
But fall flat when you want to do some sophisticated one-shot keyboard macros.  I'll take emacs any day.  Never liked modal editing.

Nano is good for quick things but just won't do a lot of the things I need.  Besides, for us "multiple platform" people, emacs is more universal...

---

### Post by LordBug on 2006-03-02
> pico & nano are simple and easy to use 
Which is exactly why I use them.  Quick, easy, done.  For basic text file work, I highly recommend them.

---

### Post by darth_vector on 2006-03-02
[QUOTE=wrtrdood]But fall flat when you want to do some sophisticated one-shot keyboard macros.  I'll take emacs any day.  Never liked modal editing.

Nano is good for quick things but just won't do a lot of the things I need.  Besides, for us "multiple platform" people, emacs is more universal...[/QUOTE]

universal!? i haven't seen a linux/unix distro that didn't have vi installed by default; ever!

the war will rage on; no sence in arguing about it i suppose :-)

---

### Post by Brunellus on 2006-03-02
you should just have nano installed.  if you don't want to use nano, apt-get your favorite text editor.

I recommend vim.

Others recommend emacs.

I find it a lot easier to learn vim, actually, with a cheat-sheet printed out and pinned near the computer.  Emacs?  not so much.

---

### Post by wrtrdood on 2006-03-02
[QUOTE=darth_vector]universal!? i haven't seen a linux/unix distro that didn't have vi installed by default; ever!

the war will rage on; no sence in arguing about it i suppose :-)[/QUOTE]


ummm.... I meant that it runs on VMS, Unix, Windows, DOS.  Yes, vi is on every *nix system but that's not what I meant.  Should have been more careful :rolleyes:

---

### Post by mlind on 2006-03-02
nano or pico :cool:

---

### Post by darth_vector on 2006-03-02
[QUOTE=wrtrdood]ummm.... I meant that it runs on VMS, Unix, Windows, DOS.  Yes, vi is on every *nix system but that's not what I meant.  Should have been more careful :rolleyes:[/QUOTE]

i hate to drag the argument on (well, i don't really :-)) but...

vim for windows and dos: [http://www.vim.org/download.php#pc](http://www.vim.org/download.php#pc)
vim for vms: [http://www.polarhome.com/vim/](http://www.polarhome.com/vim/)
vim for macintosh: [http://www.vim.org/download.php#mac](http://www.vim.org/download.php#mac)
vim for OS2: [http://www.vim.org/download.php#os2](http://www.vim.org/download.php#os2)
vim for amiga: [http://www.vim.org/download.php#amiga](http://www.vim.org/download.php#amiga)

and many more at [http://www.vim.org/](http://www.vim.org/)

---

