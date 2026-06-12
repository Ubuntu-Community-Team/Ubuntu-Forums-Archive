---
title: "Help with packaging souce into programs??"
date: 2007-01-20
forum: Absolute Beginner Talk
---

### Post by ndworecki on 2007-01-20
so i downloaded the source of many programs but i need to package them to install them i googled this but didnt understand. Can anyone help please?



thanx

---

### Post by po0f on 2007-01-20
ndworecki,

Do you mean you need to *un*pack them?  You should be able to just double-click on them and extract them from the GUI.  Or, if you want to unpack them from the command-line:
```
[FONT="Courier New"]$ tar xvzf /path/to/tarball.tar.gz   # for *.gz (gzip) format
$ tar xvjf /path/to/tarball.tar.bz2  # for *.bz2 (bzip2) format[/FONT]
```
[list]
[*]**x**: extract
[*]**v**: verbose
[*]**z**: file is in gzip format
[*]**j**: file is in bzip2 format
[*]**f**: the file to extract
[/list]

Note: the dollar sign represents your terminal prompt (**user@host:~$**) and is *not* part of the command.  Also, an argument has to immediately follow the **f** option.

[EDIT]

You most likely downloaded the file to your Desktop, so replace "/path/to/tarball.tar.{gz,bz2}" with "~/Desktop/tarball.tar.{gz,bz2}".

---

### Post by ndworecki on 2007-01-20
im sorry but i dont understand this

i have downloaded the source codes for ubuntu for programs and i think i need to build them



thanx

---

### Post by po0f on 2007-01-21
ndworecki,

What are you trying to compile?  It might be that the program in question is already in the repos, and is just a click away in Synaptic.

---

### Post by ndworecki on 2007-01-21
ive searched there and automatix any yes i made sure it included the third party software as well

i want to build multiple programs, as well as i believe ill need to in the future.


Sorry im pretty new to ubuntu.

---

### Post by po0f on 2007-01-21
ndworecki,

I'd still like to know what you are compiling, I could help you resolve the dependencies for it.

(If you haven't already, install [build-essential](http://packages.ubuntu.com/edgy/devel/build-essential) either through Synaptic or the command-line.)

To start off with, create a "src" directory in your home directory (all of the commands I post should be executed from a terminal, and the actual commands are in bold):
```
[FONT="Courier New"]~$ **cd ~**
~$ **mkdir src**
~$ **cd src**
~/src$[/FONT]
```

Now, we need to unpack the tarball.  Pick one:
```
[FONT="Courier New"]~/src$ **tar xvzf ~/Desktop/coolprogram-0.1.tar.gz**
~/src$ **cd coolprogram-0.1**
~/src/coolprogram-0.1$[/FONT]
```

Now, just let me know what the program is, and we can go from there.

---

