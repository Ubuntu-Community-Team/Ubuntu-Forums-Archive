---
title: "i don't know how to do..."
date: 2007-07-22
forum: Absolute Beginner Talk
---

### Post by jonnyyoa on 2007-07-22
the following:

1)install anything after i downloaded something from the internet

2) when i use the package w/e thingy i get this message

[COLOR="Red"]A unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Type '-e\n' is not known on line 44 in source list /etc/apt/sources.list, E:The list of sources could not be read.'[/COLOR]

3) i can't update either because of the above error

4) i tried to use terminal to install wine and i got error also

:confused::confused:

---

### Post by starcraft.man on 2007-07-22
> **jonnyyoa said:**
> the following:

1)install anything after i downloaded something from the internet

2) when i use the package w/e thingy i get this message

[COLOR="Red"]A unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Type '-e\n' is not known on line 44 in source list /etc/apt/sources.list, E:The list of sources could not be read.'[/COLOR]

3) i can't update either because of the above error

4) i tried to use terminal to install wine and i got error also

:confused::confused:

Hmmm, ok. Well first to understand how installing things in Ubuntu works, please read the entirety of the blue link in my sig. I know it's long but trust me you will understand when done reading. That will take care of problem 1 4 I believe. 2 and 3 are tied to sources list it appears. While reading my blue link please pay careful attention to the sections on the sources list. Use the graphical   method of viewing the sources.list file, then copy/paste the outputs here with CODE tags (number sign) around the output in a reply to the thread. Then we will get it fixed I hope, so post back once ya done reading :).

---

### Post by alienexplorers on 2007-07-22
Are the programs you are trying to load not in synaptic.  If they are you would not have any problems loading them.  Remember if you are loading from another site that the programs will probably need to be compiled.  You will need to load build-essentials from synaptic first.

---

### Post by starcraft.man on 2007-07-22
> **alienexplorers said:**
> Are the programs you are trying to load not in synaptic.  If they are you would not have any problems loading them.  Remember if you are loading from another site that the programs will probably need to be compiled.  You will need to load build-essentials from synaptic first.

I recommend against compiling. It's really not needed unless your program is extremely specialist, most programs are in the repos or else a third party one. To be sure you can post which programs you were trying to install. WINE certainly is in the repositories.

I'm still pretty sure at least part of the problem is the sources list... please paste it here for review.

---

