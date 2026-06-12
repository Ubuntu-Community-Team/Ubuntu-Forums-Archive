---
title: "Search for filetype"
date: 2006-12-28
forum: Absolute Beginner Talk
---

### Post by andrewlondonuk on 2006-12-28
I'm trying to search through my music collection which is at /home/andrew/Music so that i can remove all the .m4a and .wma files. I've tried the search that comes with gnome and can't get it to find anything and i've tried kerry beagle with ext:m4a

The thing is nothing is coming up..... i need to remove these files because amarok isn't building a collection because of these files, they're causing banshee to crash as well....

Please help... ](*,)

---

### Post by pseudonym on 2006-12-28
You should be able to play them by installing the package 'w32codecs' . You'll need to add a repository to your software sources to be able to download the package.

For all the instructions, read the [Restricted Formats]("https://help.ubuntu.com/community/RestrictedFormats") wiki.

---

### Post by andrewlondonuk on 2006-12-28
I have that installed already and am playing the files fine. It's just that when i try and build a collection in amarok or a library in banshee it just stops when it gets to either of these filetypes...
I thought the best way around this would be to find them, and convert them to mp3....

---

### Post by OffHand on 2006-12-28
> **andrewlondonuk said:**
> I'm trying to search through my music collection which is at /home/andrew/Music so that i can remove all the .m4a and .wma files. I've tried the search that comes with gnome and can't get it to find anything and i've tried kerry beagle with ext:m4a

The thing is nothing is coming up..... i need to remove these files because amarok isn't building a collection because of these files, they're causing banshee to crash as well....

Please help... ](*,)

remove .m4a files from your music folder: 
```
find /home/andrew/Music -name "*.m4a" -exec rm '{}' \;
```

remove .wma files from your music folder: 
```
find /home/andrew/Music -name "*.wma" -exec rm '{}' \;
```

---

### Post by andrewlondonuk on 2006-12-28
I posted a reply before seeing that, i'm just wondering, is there a way to move all the files to another folder rather than remove them altogether?

---

### Post by OffHand on 2006-12-28
> **andrewlondonuk said:**
> I posted a reply before seeing that, i'm just wondering, is there a way to move all the files to another folder rather than remove them altogether?

I'm not the king of bash or something but my guess is it would be something like
```
cp /home/andrew/Music/*.wma /home/andrew/Music/wma_files
```

where wma_files is a folder in Music.

Again, I might be a bit wrong with that command but it's close hehe

---

### Post by univremonster on 2007-09-05
I too am far from king of bash, in fact I'm pretty much the apprentice for the guy who scoops out the royal stables, but I have a similar problem, and while I'm only moving 7 files which would be easy enough in the GUI this seems like a good learning experience... here's what I get when I try to move 'em:

remonster@remonster-desktop:~/Music/artists w 4 or fewer tracks$** ls**
*//long list of songs I have removed//*
Gogol bordello - future kings.ogg
Gogol Bordello - Gypsy Part of Town.ogg
Gogol Bordello - let's get radical.ogg
Gogol Bordello - Madagascar.ogg
Gogol Bordello - Punk Rock Paranada.ogg
Gogol Bordello - Sacred Darling.ogg
Gogol Bordello - Under the World Strike.ogg
*//long list of more songs I have removed//*

remonster@remonster-desktop:~/Music/artists w 4 or fewer tracks$ **cp /home/remonster/Music/*Gogol* /home/remonster/Music/Gogol\ Bordello/**
cp: omitting directory `/home/remonster/Music/Gogol Bordello'

Why did it decide not to 'omit' this directory?  I have also tried using the command 'mv' but I am not sure how to get it to work without typing in each file individually.

EDIT:  I tried going further down the directories, thinking that maybe since I was trying to move some files to where they already are (Those Gogol Bordello files which are already in the correct directory) it would cause an issue.  Here's the results:

remonster@remonster-desktop:~/Music/artists w 4 or fewer tracks$ cp /home/remonster/artists\ w\ 4\ or\ fewer\ tracks/*Gogol* /home/remonster/Music/Gogol\ Bordello/

which did NOT produce the omitted directory error, however it also didn't move the files...

---

### Post by univremonster on 2007-09-06
bump

---

### Post by univremonster on 2007-09-07
bump

---

### Post by univremonster on 2007-09-07
bumpity bump bump... this seems like a really easy question for somebody to answer given the amount of command line die-hards out there... where are you guys?

---

### Post by vanadium on 2007-09-07
Offhand provided *the* solution to the original poster: the power of the find command. You just need to underdstand what it does:

find /home/andrew/Music -name "*.m4a" -exec rm '{}' \;

* Find must start its search in /home/andrew/Music
* -name: it must find files with a name that suits the patters "*.m4a", this means all files with .m4a at the end.
* -exec: it will execute the command rm on every file it finds. Find will replace {} with the filename. The ; (protected from the shell using \) is needed to terminate the command.

Want to move the files to a dedicated directory? replace the -exec part by

-exec mv {} <dir_of_your_choice> \;

---

### Post by univremonster on 2007-09-09
> **vanadium said:**
> Offhand provided *the* solution to the original poster: the power of the find command. You just need to underdstand what it does:

find /home/andrew/Music -name "*.m4a" -exec rm '{}' \;

* Find must start its search in /home/andrew/Music
* -name: it must find files with a name that suits the patters "*.m4a", this means all files with .m4a at the end.
* -exec: it will execute the command rm on every file it finds. Find will replace {} with the filename. The ; (protected from the shell using \) is needed to terminate the command.

Want to move the files to a dedicated directory? replace the -exec part by

-exec mv {} <dir_of_your_choice> \;

Thanks!

---

