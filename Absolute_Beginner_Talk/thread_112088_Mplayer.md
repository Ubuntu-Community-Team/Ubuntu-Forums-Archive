---
title: "Mplayer"
date: 2006-01-03
forum: Absolute Beginner Talk
---

### Post by Drew32 on 2006-01-03
Im trying to install Mplayer which actually gives you the option to make .deb files but the problem is it says my GCC is to new and it doesnt support it and i should go back to an older version of GCC, problem is how do i do that? or is there a better video viewing software i should use?

---

### Post by Swab on 2006-01-03
You could try "sudo apt-get install gcc-3.4"

---

### Post by Swab on 2006-01-03
Also you can install mplayer from one of the repositories... multiverse I think.

---

### Post by Drew32 on 2006-01-03
[QUOTE=Swab]Also you can install mplayer from one of the repositories... multiverse I think.[/QUOTE]

ok yea the first step gave me more errors but did fix the GCC problem. so what is this multiverse and how do i use it?

---

### Post by Swab on 2006-01-03
Here is a howto:  [https://wiki.ubuntu.com/AddingRepositoriesHowto](https://wiki.ubuntu.com/AddingRepositoriesHowto)
Once that is done you can use synaptic to search for and install mplayer!

---

### Post by [Rui] on 2006-01-03
For mplayer, multiverse and marillat suck BIG TIME.

It's better to install dependencies from those repositories, compile mplayer and do checkinstall to create and install a .deb

---

### Post by Swab on 2006-01-03
[QUOTE='[Rui]']For mplayer, multiverse and marillat suck BIG TIME.

It's better to install dependencies from those repositories, compile mplayer and do checkinstall to create and install a .deb[/QUOTE]

I didn't realise that was the case.  My mplayer install from multiverse works fine.   What exactly is the problem with the packages in those repositories?

---

### Post by Drew32 on 2006-01-03
[QUOTE=Swab]I didn't realise that was the case.  My mplayer install from multiverse works fine.   What exactly is the problem with the packages in those repositories?[/QUOTE]

mine worked fine, and somehow it installed XMMS too but im happy because i was planning on getting that next. Thanks for all your help!

---

