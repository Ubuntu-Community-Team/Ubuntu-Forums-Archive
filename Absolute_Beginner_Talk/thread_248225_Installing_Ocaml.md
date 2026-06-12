---
title: "Installing Ocaml"
date: 2006-08-31
forum: Absolute Beginner Talk
---

### Post by Hydrargyri on 2006-08-31
Hello! Ubuntu is definitely growing on me, but there is one thing I still can't figure out. How to install one of my favorite languages: Ocaml!

I went to the official website, and ended up here:
[http://packages.debian.org/stable/devel/ocaml](http://packages.debian.org/stable/devel/ocaml)

Now, I know that the ubuntu CD I used was i386, so I chose that ocaml installation option. However...

As I clicked one of the download options, and opened it in the package installer, I got this message:

Status: Error: Dependency is not satisfiable: ocaml-base

Now, I still don't even know how installing files on ubuntu even works, let alone how to solve this problem. If one of you could help me, I'd be very thankful.

Illustrated thusly: Thanks!
:D

---

### Post by atomkarinca on 2006-09-02
i don't know if it's a native package or is it because i added some to the sources.list but i made a search:

> sudo apt-cache search ocaml

and this package is present. so you can just

> sudo apt-get install ocaml

or

sudo aptitude install ocaml (i prefer this one :))

---

### Post by Hydrargyri on 2006-09-03
Thanks, that worked!

However, I do have a few other questions. I'm now trying to install another language, (which required ocaml installed to run), and the commands given to compile the thingy are for a different sort of shell, not bash. Specifically, the make command. What is the bash equivelant? I did a google search, but the results ended up being about wireless internet and such.

Also, I know this sounds like a stupid question, but how do I actually run ocaml? That is to say, where's the application? I tried opening a .ml file in emacs, but I'm inept at emacs so nothing really happened.
(On that note, if someone knows a good tutorial on how to get started programming using emacs, and how to use the shell in emacs [I've seen it done], that'd be truly awesome.)

Thanks!

---

### Post by jworr on 2006-10-23
I don't know how to use emacs so I can't help you there

as for using ocaml

if you type "ocaml" into bash then you will get the interactive ocaml interepter

if you type "ocaml <file name>" it will run that file through the ocaml interpreter and run the program contained in the file

if you type "ocamlc <file name>" then it will run the file through the ocaml compiler and create an executable called "a.out" you can then run the program by typing "./a.out"

---

