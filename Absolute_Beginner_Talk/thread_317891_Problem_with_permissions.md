---
title: "Problem with permissions"
date: 2006-12-13
forum: Absolute Beginner Talk
---

### Post by Muppeteer on 2006-12-13
I started using Ubuntu Edgy last week and it´s been great, but i´m getting annoyed now...

I was trying to install ati drivers last week and created a temporary directory on my desktop. So i extracted all the folders and files into it, and now i can´t delete them. I´ve changed the permissions of the fglrx-install directory but the folders inside it are still read only. 

I can go through the terminal and chmod every folder and file but it´s gonna take forever. Is there a quicker way to change permissions of a directory and it´s contents, be it folders or files?

---

### Post by thornomad on 2006-12-13
Did you try using option "-R" ?

```
ubuntu:~$ chmod --help
Usage: chmod [OPTION]... MODE[,MODE]... FILE...
  or:  chmod [OPTION]... OCTAL-MODE FILE...
  or:  chmod [OPTION]... --reference=RFILE FILE...
Change the mode of each FILE to MODE.

  -c, --changes           like verbose but report only when a change is made
      --no-preserve-root  do not treat `/' specially (the default)
      --preserve-root     fail to operate recursively on `/'
  -f, --silent, --quiet   suppress most error messages
  -v, --verbose           output a diagnostic for every file processed
      --reference=RFILE   use RFILE's mode instead of MODE values
  -R, --recursive         change files and directories recursively
      --help     display this help and exit
      --version  output version information and exit

Each MODE is of the form `[ugoa]*([-+=]([rwxXst]*|[ugo]))+'.

Report bugs to <bug-coreutils@gnu.org>.

```

What error do you get, specifically, when you try and rm the directory and what command are you using ?

---

### Post by Muppeteer on 2006-12-13
Thanks dude, i just added the recursive and it´s solved my problem :D

---

### Post by hotbrainz on 2006-12-13
Another way to do this, 

well you can do this:

> gksudo nautilus

This will open up a file window in which you have root privileges to everything. You can do as you like. But close this window after use as you might unwittingly delete somehitng useful.

Careful...you can delete anything.

Cheers
Hope this helps

---

### Post by Muppeteer on 2006-12-13
Thanks for the tip :)

---

