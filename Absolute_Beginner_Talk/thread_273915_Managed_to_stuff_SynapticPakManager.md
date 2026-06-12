---
title: "Managed to stuff SynapticPakManager"
date: 2006-10-09
forum: Absolute Beginner Talk
---

### Post by carloslosgrande on 2006-10-09
I tried to add id3lib from sourceforge.net to my repository list but stuffed it up and now SynPacMan won't work!:confused: [passion fingers strikes again].

I get an error every time I try to do anything in it. it says the error type is; [COLOR=Red]> [https://sourceforge.net/projects/id3lib](https://sourceforge.net/projects/id3lib) is not known on line 73 in source list /etc/apt/sources.list
Unable to lock the list directory.

[/COLOR]How do I get rid of the entry I made?:(
HELP.

---

### Post by dmizer on 2006-10-09
at the command line do this:
```
gksudo gedit /etc/apt/sources.list
```
remove the line pertaining to your id3lib.
save.
then at the command line do:
```
sudo aptitude update
```

should be all better then :)

---

### Post by carloslosgrande on 2006-10-09
Thank you Dmizer. Yes its all better now. Its happy:D, I'm happy:D, and once more learned where NOT to stick my fingers and some small part of 'how to do/fix stuff'.
I've never had this sort of support before. [windoze etc]
An excellently simple and effective fix, much appreciated Dmizer.

Relieved newby.

---

### Post by dmizer on 2006-10-09
great to hear i could help.

for the future, don't worry about "sticking your fingers in" ... just leave yourself an out.

in this case, you could have made a backup copy of your sources list before you modified it:
```
sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup
```
then if something goes wrong, all you have to do is replace the suffed apt sources list with the known good backup:
```
sudo mv /etc/apt/sources.list_backup /etc/apt/sources.list
```

by the way, you can apply this technique to any critical config file.  ex: fstab, xorg.conf etc.

---

### Post by carloslosgrande on 2006-10-10
I've just copied that to my fixes file, thanks again Dmizer

---

