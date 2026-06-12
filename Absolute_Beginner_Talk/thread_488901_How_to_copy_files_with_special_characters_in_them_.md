---
title: "How to copy files with special characters in them? (To an iPod / through usb)"
date: 2007-06-30
forum: Absolute Beginner Talk
---

### Post by Laplace's Daemon on 2007-06-30
So I'm pretty new to Ubuntu, and i've been ripping all my cds to .ogg format, which I now want to copy to my iPod (which is using Rockbox).  I ripped all of the cds using Sound Juicer and didn't change any of the names.  But when I try copying it all to the iPod, I keep getting errors like these:
```
cp: cannot create regular file `/media/DAVID\'SIPOD/music/Clifford Brown & Max Roach/Study in Brown/09. Clifford Brown & Max Roach - Take the "A" Train.ogg': Invalid argument
cp: cannot create regular file `/media/DAVID\'SIPOD/music/Clifford Brown & Max Roach/Clifford Brown and Max Roach/07. Clifford Brown & Max Roach - What Am I Here For?.ogg': Invalid argument
```
I used the command```
cp -r ~/music/ .
```while in the main iPod directory (/media/DAVID\'SIPOD/).  As far as I can tell, all of the file or directory names contain characters like ?, " or :.  Trying it from my home directory causes the same error, as does trying to do it graphically with the Places folder and through GNOME Commander.

I get the same error trying to copy to copy to a flash drive, but not when trying to copy to the hard drive itself.  I also tried scp and rsync, but they seem to be having the same errors.

Does anyone have a solution?

---

### Post by KIAaze on 2007-07-01
I once had such a problem with files starting with "-".
I solved it by renaming the files through the GUI and then transferring them.

However, if you say that you can't even transfer the files through the GUI, I doubt that this will work for you.
But you should try at least to see if the problem really comes from special characters or not.

I did a little test with your filenames and the creation and listing by command-line work perfectly well:
> >ls media/DAVID\'SIPOD/music/Clifford\ Brown\ \&\ Max\ Roach/Study\ in\ Brown/09.\ Clifford\ Brown\ \&\ Max\ Roach\ -\ Take\ the\ \"A\"\ Train.ogg
media/DAVID'SIPOD/music/Clifford Brown & Max Roach/Study in Brown/09. Clifford Brown & Max Roach - Take the "A" Train.ogg
> >ls media/DAVID\'SIPOD/music/Clifford\ Brown\ \&\ Max\ Roach/Clifford\ Brown\ and\ Max\ Roach/07.\ Clifford\ Brown\ \&\ Max\ Roach\ -\ What\ Am\ I\ Here\ For\?.ogg
media/DAVID'SIPOD/music/Clifford Brown & Max Roach/Clifford Brown and Max Roach/07. Clifford Brown & Max Roach - What Am I Here For?.ogg

When using an expression containing special characters, you can either use single-quotes ('), double quotes (") or a backslash in front of every special character (don't forget spaces) to remove their special meaning.

Here's a little bit more info about special characters and quoting in UNIX:
[http://www.grymoire.com/Unix/Quote.html]("http://www.grymoire.com/Unix/Quote.html")

Basically, if you use ('), all special characters should loose their meaning, while if you use ("), characters like the $ sign keep their meaning.

edit:
Try the following to see if it works:
```
cp ~/music/Clifford\ Brown\ \&\ Max\ Roach/Study\ in\ Brown/09.\ Clifford\ Brown\ \&\ Max\ Roach\ -\ Take\ the\ \"A\"\ Train.ogg /media/DAVID\'SIPOD/music/Clifford\ Brown\ \&\ Max\ Roach/Study\ in\ Brown/
cp ~/music/Clifford\ Brown\ \&\ Max\ Roach/Clifford\ Brown\ and\ Max\ Roach/07.\ Clifford\ Brown\ \&\ Max\ Roach\ -\ What\ Am\ I\ Here\ For\?.ogg /media/DAVID\'SIPOD/music/Clifford\ Brown\ \&\ Max\ Roach/Clifford\ Brown\ and\ Max\ Roach/

```

re-edit:
_SOLUTION TO "--*" or "-*" FILES:_
[QUOTE=wjevans_7d1@yahoo.co]After the last switch (if any), use "--" by itself, and anything after that will be interpreted as a filename.

Example:

```

wally:~/saturday$ ls
wally:~/saturday$ touch -- -abcd
wally:~/saturday$ touch -- --abcd
wally:~/saturday$ ls
--abcd  -abcd
wally:~/saturday$ # following will fail because it seems like "ls --abcd -abcd"
wally:~/saturday$ ls *abcd
ls: unrecognized option `--abcd'
Try `ls --help' for more information.
wally:~/saturday$ # but this will work:
wally:~/saturday$ ls -- *abcd
--abcd  -abcd
wally:~/saturday$ 

```

Hope this helps.[/QUOTE]
[http://www.linuxquestions.org/questions/showthread.php?p=2814844#post2814844]("http://www.linuxquestions.org/questions/showthread.php?p=2814844#post2814844")

---

### Post by Laplace's Daemon on 2007-07-02
Thanks for the link and the reply and the link.  I was doing some research on this problem, and it looks like it's not a problem with Linux, but with the fact that FAT32 won't accept those characters in it's files, so I can't create files with those names.  So I ended up going through and renaming all the files myself.

---

