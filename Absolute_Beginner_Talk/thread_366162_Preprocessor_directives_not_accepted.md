---
title: "Preprocessor directives not accepted"
date: 2007-02-20
forum: Absolute Beginner Talk
---

### Post by Mariane on 2007-02-20
Hi, 

The only post I could find which sounded like a similar problem was 
[http://ubuntuforums.org/showthread.php?t=172475&highlight=preprocessor+directives](http://ubuntuforums.org/showthread.php?t=172475&highlight=preprocessor+directives)
but this discussion is tagged closed. 

I am looking for my preprocessor directives and I can't find them. 
They worked fine with Debian, then I plugged in a computer with ubuntu. 
I can get into a failsafe session but in a normal session it says:

/usr/X11R6/bin/sessreg -a -w (etc)

# emacs.-fonts: <etc> Unknown # directive # emacs
# emacs.-fonts: <etc'> Unknown # directive # emacs
# emacs.-fonts: <etc''> Unknown # directive # emacs
# fonts are in <etc>  Unknown # directive # fonts
# type xlsfonts fo a list Unknown # directive # type
# see xrdb Unknown # directive # see

6 error in preprocessor


It looks as if  # has been used as a comment symbol in the preprocessor directives file. 
But I can't find the file. 

Please tell me where preprocessor directives are stored
Please tell me the correct syntax for comments in preprocessor directives files

Thank you

Mariane

---

### Post by NewOldTimer on 2007-02-20
Way out of my league.. this any help?
[http://www.cplusplus.com/doc/tutorial/preprocessor.html](http://www.cplusplus.com/doc/tutorial/preprocessor.html)
[http://en.wikibooks.org/wiki/C++_Programming/Examples/Hello_world](http://en.wikibooks.org/wiki/C++_Programming/Examples/Hello_world)

---

### Post by Mariane on 2007-02-20
No, but thanks anyway. 

These are for specific programs you write
(eg "#include <file>" means "use this file in the program"). 

I am looking for preprocessor directives I didn't write myself, and which 
deal with a user session. 
(eg something which means "For emacs text editor use courrier font by 
default"). 

Mariane

---

### Post by Mariane on 2007-02-20
This was about another subject, really, so I put it in a new post. 

I wanted to delete this part but I didn't find how to delete, only edit. Sorry. 

Mariane

---

### Post by Mariane on 2007-02-22
Anyone has a suggestion, please? 

Mariane

---

### Post by po0f on 2007-02-22
Mariane,

Are you talking about configuration files for programs?  You mentioned trying to set a font in emacs.  Usually, a user's configuration files are stored under your home directory (/home/<username>, or ~ for short).  An example would be Vim's file .vimrc.  The full path is /home/<username>/.vimrc, or ~/.vimrc.  Maybe you're looking for ~/.emacsrc?  (I don't know what emacs' config file is called, I don't use the stuff  ;))

Default configuration files are stored in /etc.  You should be able to copy a generic config to your home dir and modify it, ie `cp /etc/vim/vimrc ~/.vimrc`.  Substitute with emacs config file and you should be good to go.

HTH

---

