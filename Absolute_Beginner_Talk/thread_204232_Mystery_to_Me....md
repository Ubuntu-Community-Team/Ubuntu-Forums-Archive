---
title: "Mystery to Me..."
date: 2006-06-26
forum: Absolute Beginner Talk
---

### Post by ACQ on 2006-06-26
I've Googled and forum searched the living daylights out of this and because of the nature of the question, I have no luck finding the answer. Please excuse me if this has already been discussed.

Bear with me as I state something most of us already know…

In DOS/Windows you have EXE files and such (CMD, BAT, etc.). In order to execute an EXE file in DOS you must be specific about the location of the executable. For instance just typing "iexplore.exe" at the C:\ prompt will get you nothing, unless iexplore.exe is actually sitting in the root of C:\.

In Linux this is completely unreliable for me. I'm the kind of person that likes to know "why and where" more than just "do [this] and it works". An example here would be typing "nvidia-settings" in a Terminal. Wow! Magically here appears my nVidia configuration editor. How the heck did Linux know where to find the "executable" for nvidia-settings? This goes for typing "gedit" or "lxdoom" or anything that is executable in Linux. Is there a database that has all these commands stored and are those commands recognized from within any directory in the file system? Could someone please elaborate for me and help me break the confines of a Windows mentality?! Thanks everyone!

---

### Post by scxtt on 2006-06-26
PATH ... it has a set of variables that it uses (do a printenv for bash) and you can see most of them ... everything in PATH is checked to see if the command resides there ...

do an "echo $PATH" to see what yours currently is (and you can change it) ...

---

### Post by Kilz on 2006-06-26
[QUOTE=ACQ]I've Googled and forum searched the living daylights out of this and because of the nature of the question, I have no luck finding the answer. Please excuse me if this has already been discussed.

Bear with me as I state something most of us already know…

In DOS/Windows you have EXE files and such (CMD, BAT, etc.). In order to execute an EXE file in DOS you must be specific about the location of the executable. For instance just typing "iexplore.exe" at the C:\ prompt will get you nothing, unless iexplore.exe is actually sitting in the root of C:\.

In Linux this is completely unreliable for me. I'm the kind of person that likes to know "why and where" more than just "do [this] and it works". An example here would be typing "nvidia-settings" in a Terminal. Wow! Magically here appears my nVidia configuration editor. How the heck did Linux know where to find the "executable" for nvidia-settings? This goes for typing "gedit" or "lxdoom" or anything that is executable in Linux. Is there a database that has all these commands stored and are those commands recognized from within any directory in the file system? Could someone please elaborate for me and help me break the confines of a Windows mentality?! Thanks everyone![/QUOTE]

From what I understand the executables are all in /bin, /user/bin or /usr/local/bin are in the ["path" ]("https://wiki.ubuntu.com/OneTruePath?highlight=%28path%29") when you type the command, its actualy the name of the file in one of the /bin folders. Linux looks in the /bin folders for that file name and launches it.

---

### Post by Brunellus on 2006-06-26
those executables that you're being asked to type in are installed in directories that appear in your PATH environment variable.

MS-DOS had a similar (but not identical) provision;  by default, in MS-DOS, your PATH looked like this

path=C:\DOS\COMMAND\

(reference: [http://www.computerhope.com/pathhlp.htm](http://www.computerhope.com/pathhlp.htm))

which is where all of DOS's command executables were stored:  dir, cd, md, del, edlin, and so forth.

---

### Post by FenrisAbraxas on 2006-06-26
type $whereis programname
or $locate programname
or $whatis programname

hope that helps

---

### Post by ACQ on 2006-06-26
Ah, okay that makes sense! I sincerely appreciate the help (especially the varied replies). Thanks a ton :)

---

