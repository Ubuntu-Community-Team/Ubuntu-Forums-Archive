---
title: "some questions about cedega......"
date: 2007-06-24
forum: Absolute Beginner Talk
---

### Post by techno-mole on 2007-06-24
hello.
so i decided to go linux all the way, so now i dont have a windows install, but i thought id try cedega to play some games with, at least until ive completed them.
so ive installed cedega (latest version) and ive picked need for speed underground 2 as the first game to install, as far as i can tell the install went ok, no errors, but when i try to start the game i get a nfsu window pop up and then nothing, if i take the game disc out of the drive it asks for it, so the install must be ok ?
anyway if i start cedega from terminal i get this out put - 

/usr/lib/transgaming_cedega/gddb.py:24: RuntimeWarning: Python C API version mismatch for module gddb_parser: This Python has API version 1013, module gddb_parser has version 1012.
  import gddb_parser
F1 2007-06-24 09:38:17,985 WARNING The Cedega version (6.0.2) you are defaulting to is missing the following file : /home/user/.cedega/.winex_ver/winex-6.0.2/.transgaming/config
so this says to me that something is missing, so the question is that as it mentions wine, does that mean you need wine or at least some wine components in order to run cedega properly ?
the other thing is how do i fix this problem ?
im guessing that the install of cedega did not go as well as i thought.
cheers in advanced for anyhelp.
cheers

---

### Post by Sokraates on 2007-06-26
Cedega does not need a separate installation of WINE, since it basically is an expanded and modified version of WINE itself.

From the looks of things, the problem lies with the engine you use (version 6.0.2) missing a config file. You could try a slightly older engine (6.0 or 6.0.1) or simply delete and reinstall 6.0.2. You can manage engines from within Cedega. Older engines can be found on the official website. You only need to login first.

If nothing helps, purge Cedega (i.e. also remove all your preferences and configuration files; best use Synaptic) and then reinstall.

---

### Post by techno-mole on 2007-06-26
cheers, i have managed to get it to work with an earlier engine, cheers again.

---

