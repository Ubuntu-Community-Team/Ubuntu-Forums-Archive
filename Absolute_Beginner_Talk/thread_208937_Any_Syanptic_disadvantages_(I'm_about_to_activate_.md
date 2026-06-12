---
title: "Any Syanptic disadvantages? (I'm about to activate it)"
date: 2006-07-04
forum: Absolute Beginner Talk
---

### Post by Average_Joe on 2006-07-04
I'm running Ubuntu 6.06 on a dual boot box with Windows XP.  

I really enjoy Ubuntu so far.

I'm just about ready to activate Synaptic using the instructions at the link below, but before I do so, wanted to ask the other users/experts if they feel there is any disadvantage to doing so.  I'm not afraid to use CLI for these things in particular if CLI offers more flexibility.

Thanks in advance!

---

### Post by bitoiu on 2006-07-04
Hi ,

I'm not an expert, but I use linux for a few years specialy ubuntu. I'm pretty sure the synaptic us not much more than a simple interface to the apt-get command. I use apt-get when I know the name of the package, like perl packages, that are all named pretty much the same. Synaptic is great when you want something but you just don't know what. Like if you want a dictionary, you search by description of the language for example, it's good for searching packages.

And I say without absolute certain, that synaptic is harmless and recommended ;)

---

### Post by steve.horsley on 2006-07-04
No problems. Synapic is very well behaved. Personally I find synaptic easier than command line because of the easy package search and I rarely know exactly what package name I'm looking for.

Remember to enable multiverse and universe repositories for extra software packages.

---

### Post by aysiu on 2006-07-04
Well, the disadvantage is that Synaptic won't remove packages that get installed along *with* another package.

[http://www.psychocats.net/ubuntu/aptitude](http://www.psychocats.net/ubuntu/aptitude)

---

### Post by crystal on 2006-07-04
> Well, the disadvantage is that Synaptic won't remove packages that get installed along with another package.
What is the solution to that?

---

### Post by Jagot on 2006-07-04
[QUOTE=crystal]What is the solution to that?[/QUOTE]

Use aptitude from the commandline instead.

---

### Post by cjm5229 on 2006-07-04
[quote=crystal]What is the solution to that?[/quote]

Try this [http://www.ubuntuforums.org/showthread.php?t=140920&highlight=clean]("http://www.ubuntuforums.org/showthread.php?t=140920&highlight=clean")

---

### Post by aysiu on 2006-07-04
[QUOTE=cjm5229]Try this [http://www.ubuntuforums.org/showthread.php?t=140920&highlight=clean]("http://www.ubuntuforums.org/showthread.php?t=140920&highlight=clean")[/QUOTE]
By why do all that when you can just use *aptitude* and avoid all the junk in the first place?

---

### Post by Bloch on 2006-07-04
> Well, the disadvantage is that Synaptic won't remove packages that get installed along with another package.


This is generally not a big problem. The average user should be happy with synaptic. Eventually you may reach a program that says it can't be installed because of conflicts, but it will show you what will be removed.

---

### Post by aysiu on 2006-07-04
[QUOTE=Bloch]This is generally not a big problem. The average user should be happy with synaptic. Eventually you may reach a program that says it can't be installed because of conflicts, but it will show you what will be removed.[/QUOTE]
I was just about to say that a lot of users on these forums are not average users, and a common complaint is actually that those dependencies do not get removed along with the original package...

... then I saw the username of the OP.

---

