---
title: "Xterm:Possible to list the programs available in sources.list with star: ls gnome*  ?"
date: 2006-01-08
forum: Absolute Beginner Talk
---

### Post by patrick295767 on 2006-01-08
I would like to know all the programs that I can downlaod from apt-get -f install from my sources.list (breezy).
  
Imagine for isntance:
apt-get list gnome* 
  would for instance give all the programs that are available starting by gnome*
(* = for whatever may follow)
  
Is it possible ?
  
Thank you !
  
Pat'

---

### Post by deNoobius on 2006-01-08
If I'm understanding you correctly, the command would be:

sudo apt-cache pkgnames gnome 

No asterisk.  The list will be filtered using the word after "pkgnames".  See man apt-cache for more details.

---

### Post by patrick295767 on 2006-01-08
[QUOTE=deNoobius]If I'm understanding you correctly, the command would be:

sudo apt-cache pkgnames gnome 

No asterisk.  The list will be filtered using the word after "pkgnames".  See man apt-cache for more details.[/QUOTE]
 
  
  Cool !!  Thank you very much !!
  
That's very useful function !
  
Greetings DeNoobius, 

Patrick

---

### Post by deNoobius on 2006-01-08
You're welcome!  Apt-cache has some nice options--it's worth checking out the man page. One other thing you can also do is find out all the dependencies of a package, for example.

---

