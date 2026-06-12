---
title: "need a command for search &amp; copy in terminal"
date: 2008-02-11
forum: Absolute Beginner Talk
---

### Post by willfriedwald on 2008-02-11
okay, am in terminal, in a directory

I want to find all folders (in the current directory) that contain the words : "tony]"  (not case sensitive)

and at the same time, copy them to an external SATA drive which is currently showing up in gP as "/dev/sdo" - terminal recognizes it (I think) as "/media/TVISTO2"

is there a command for that in terminal? to find the folders and copy them to the drive?

thanks!

w

---

### Post by stchman on 2008-02-11
> **willfriedwald said:**
> okay, am in terminal, in a directory

I want to find all folders (in the current directory) that contain the words : "tony]"  (not case sensitive)

and at the same time, copy them to an external SATA drive which is currently showing up in gP as "/dev/sdo" - terminal recognizes it (I think) as "/media/TVISTO2"

is there a command for that in terminal? to find the folders and copy them to the drive?

thanks!

w

```
find . -name "tony*" -exec cp '{}' /media/TVISTO2 \;
```

Only problem is that the find command is case sensitive so use "Tony*" next.  The find command is recursive so it will search subdirectories.  If you are not concerned with a recursive search then do teh following:

```
cp ./tony* /media/TVISTO2
```

---

### Post by jfinkels on 2008-02-11
```
find /media/TVISTO2 -maxdepth 1 -type d -iwholename "*tony\]*" -print
```
This command will find all directories ("-type d") only in the level under the directory /media/TVISTO2 ("-maxdepth 1"), searching for the case-insensitive pattern "tony]" ("iwholename '*tony\]*'"), and making sure that each successfully found entry is printed! ("-print")

Test if this works, then you can use this command to filter the output of the find command to "cp":```
find . -maxdepth 1 -type d -iwholename "*tony\]*" -print | xargs cp -r -t /path/to/target/
```
("-r" means copy entire directories recursively, including all children of the directory, "-t" means use the target directory "/path/to/target/")

To read more about these or any other command, type:```
man find
man cp
```

EDIT:

stchman's solution is cooler, because the cp is built-in to the find command :)

---

### Post by willfriedwald on 2008-02-11
all the folders I want END in "ToNY]" (the stuff before that is all different, but they all that way.

the command I tried was 

find . -name "tony]*" -exec cp '{}' /media/TVISTO2 \;

am not sure if terminal liked it or not!  it seems to be doing something, although I can't tell if it's actually copying something or not...

w

---

### Post by jfinkels on 2008-02-11
Read more about the options to find by typing ```
man find
```

Try my first suggested command and see the output (without copying it). Then try it with "-wholename" instead of the case-insensitive version "-iwholename".

---

### Post by ghostdog74 on 2008-02-11
> **willfriedwald said:**
> all the folders I want END in "ToNY]" (the stuff before that is all different, but they all that way.

the command I tried was 

find . -name "tony]*" -exec cp '{}' /media/TVISTO2 \;

am not sure if terminal liked it or not!  it seems to be doing something, although I can't tell if it's actually copying something or not...

w

the -r option of the cp command will copy the whole folder and everything under it to your destination. also, use -type d for finding directories

```


find . -type d -iname "tony]*" -exec cp -r '{}' /media/TVISTO2 \;

```

---

### Post by willfriedwald on 2008-02-15
am trying :
will@will-linux:/mnt/the_matrix$ find . -type d -iname "*tony]" -exec cp -r '{}' /media/OneTouch4 \;

all right, am  trying it with a USB drive entitled "OneTouch4" -

the directories (folders) that I want all END in "ToNY"
(some may be "tony" actually - i hate case-sensitivity!!!!)

they currently reside on
/mnt/the_matrix

and am trying to copy them to
/media/OneTouch4

so if I am currently in the right directory (will@will-linux:/mnt/the_matrix$)
and I run the above command, will that work for me?  am trying it now...

can't tell if it's doing anything yet... there are nearly 2000 of these folders I need to copy.... containing 130 GB or so worth of music files... 

update: wait!  It does indeed seem to be working!  all right - this totally rocks!

---

### Post by jfinkels on 2008-02-15
> **willfriedwald said:**
> am trying :
will@will-linux:/mnt/the_matrix$ find . -type d -iname "*tony]" -exec cp -r '{}' /media/OneTouch4 \;

all right, am  trying it with a USB drive entitled "OneTouch4" -

the directories (folders) that I want all END in "ToNY"
(some may be "tony" actually - i hate case-sensitivity!!!!)

they currently reside on
/mnt/the_matrix

and am trying to copy them to
/media/OneTouch4

so if I am currently in the right directory (will@will-linux:/mnt/the_matrix$)
and I run the above command, will that work for me?  am trying it now...

can't tell if it's doing anything yet... there are nearly 2000 of these folders I need to copy.... containing 130 GB or so worth of music files... 

update: wait!  It does indeed seem to be working!  all right - this totally rocks!

Excellent.

You can always run the find command without the "-exec" option (and all arguments that follow it) to find it out if "find" actually outputs the names of the files you are looking for.

As for case sensitivity, it's no problem for us! We have the power of regular expressions! The case-insensitive flag ( the 'i' before 'name' in '-name') tells the program to ignore case when checking the names.

---

### Post by willfriedwald on 2008-02-15
thanks for the input ....

two very curious things happened...

1 - it doesn't seem to have copied ALL the "ToNY]" folders; I remember I had roughly 1750, and it seems to have stopped after 700 or so.  can't figure out why!

2 - even though I said "tony" in the command, all the folders it found were named "ToNY" - I thought it was case-sensitive, so much the better if it isn't.

any clues or hints?  Am going to try it with another batch and see what happens - these will be my [+obc] folders (my collection of original broadway cast albums...]

------

another question: is it possible to STOP a terminal command,once it's already started - if I just close the terminal window, what happens?

---

### Post by jfinkels on 2008-02-15
> **willfriedwald said:**
> 
another question: is it possible to STOP a terminal command,once it's already started - if I just close the terminal window, what happens?

If you press "Ctrl+C" in the terminal window, you will send an Interrupt signal to the running program, which will, in most cases, cause it to stop execution.

Closing the window also will stop any program running in the terminal in that window, however, I recommend using the former method, because the program may have some built-in way of handling the Interrupt signal that will allow for a clean end of execution, as opposed to just cutting it off in the middle of execution.

EDIT: If you find yourself in some situation where the program is not responding to Ctrl+C, the Keyboard Interrupt signal, you might try Ctrl+D, the Terminate signal, or "EOF" (End of File) signal. This might be considered to be more "powerful" a signal.

---

### Post by willfriedwald on 2008-02-15
thanks

I tried it with another name inserted - "[+OBC]" - and it just went nuts, seems to have listed everything (notice this is just find, not find & copy)

will@will-linux:~$ find /mnt/the_matrix . -type d -iname "*[+OBC]"
/mnt/the_matrix/0000 [RS]/RS classical/{Bach}/Bach - Toccata & Fugue, Famous Organ Music
/mnt/the_matrix/0000 [RS]/RS classical/{Brahms}/Brahms - Sonatas for Clarinet and Piano
/mnt/the_matrix/0000 [RS]/RS classical/{Dvorak}/Dvorak (Kubalek Zenaty) - Complete Music for Violin and Piano
/mnt/the_matrix/0000 [RS]/RS classical/{Luciano Pavarotti}/Luciano Pavarotti - O Sole Mio
/mnt/the_matrix/0000 [RS]/[#]/10,000 Maniacs/Blind Man's Zoo
/mnt/the_matrix/0000 [RS]/[#]/10cc
/mnt/the_matrix/0000 [RS]/[#]/2Pac
/mnt/the_matrix/0000 [RS]/[#]/311/Music
/mnt/the_matrix/0000 [RS]/[#]/{10,000 Maniacs}/10,000 Maniacs - Blind Man's Zoo
/mnt/the_matrix/0000 [RS]/[#]/{311}/311 - Music
/mnt/the_matrix/0000 [RS]/[A]/!{VA}!/African Disco
/mnt/the_matrix/0000 [RS]/[A]/!{VA}!/Alpha ************* A Tribute To Turbonegro
/mnt/the_matrix/0000 [RS]/[A]/ABC
/mnt/the_matrix/0000 [RS]/[A]/ABC/Absolutely ABC_ The Best Of ABC
/mnt/the_matrix/0000 [RS]/[A]/ABC/Beauty Stab
/mnt/the_matrix/0000 [RS]/[A]/AC_DC
/mnt/the_matrix/0000 [RS]/[A]/AC_DC/Blow Up Your Video
/mnt/the_matrix/0000 [RS]/[A]/AC_DC/Who Made Who
/mnt/the_matrix/0000 [RS]/[A]/ADZ/Alpha *************_ A Tribute To Turbonegro
/mnt/the_matrix/0000 [RS]/[A]/Abbott & Costello
/mnt/the_matrix/0000 [RS]/[A]/Abbott & Costello/Abbott & Costello
/mnt/the_matrix/0000 [RS]/[A]/Aerosmith/Honkin' On Bobo
/mnt/the_matrix/0000 [RS]/[A]/Aerosmith/Toys in the Attic
/mnt/the_matrix/0000 [RS]/[A]/Afro Celt Sound System/Volume 1 Sound Magic

then it abruptly stopped - have no idea why!

W

---

### Post by jfinkels on 2008-02-15
EDITED: see below

You want to use a regular expression perhaps, by using the -regex option with the string "\[\+OBC\]", like this:```
-regex "\[\+OBC\]"
``` in place of the "-name" option

---

### Post by ghostdog74 on 2008-02-16
> **willfriedwald said:**
> thanks

I tried it with another name inserted - "[+OBC]" - and it just went nuts, seems to have listed everything (notice this is just find, not find & copy)


-name and -iname match shell patterns, not regular expression , like [+OBC].
read the man page of find and check the -regex , -iregex  options.

---

