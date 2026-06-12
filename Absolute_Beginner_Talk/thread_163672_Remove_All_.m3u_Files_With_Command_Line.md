---
title: "Remove All .m3u Files With Command Line?"
date: 2006-04-21
forum: Absolute Beginner Talk
---

### Post by OffHand on 2006-04-21
Hi
I would like to remove all the .m3u files in /home/admin/Music and the subfolders of Music. Is there a way to do this with the command line?
Thnx in advance,
Subsonic

---

### Post by skinnygmg on 2006-04-21
sudo rm -r /home/admin/Music/*.m3u

i think

---

### Post by earobinson on 2006-04-21
should work NOTE:rm will remove the files they will not be in the trash can they will be gone

---

### Post by OffHand on 2006-04-21
rm: cannot remove `/home/admin/Music/*.m3u': No such file or directory
I get this error. Appreciate your help guys  :)

---

### Post by mostwanted on 2006-04-21
I don't think it's possible to recursively remove files without removing everything (including directories), using the rm command that is! There might be some other syntax for that purpose.

---

### Post by gr0kzer0 on 2006-04-21
AFAIK rm -r should work. i just did something similar. but the problem may be the path. is /home/admin/Music the right path?

---

### Post by gr0kzer0 on 2006-04-21
You need to search the subdirectories. How about 'rm -r /home/admin/Music/*/*.m3u'?

---

### Post by OffHand on 2006-04-21
[QUOTE=gr0kzer0]You need to search the subdirectories. How about 'rm -r /home/admin/Music/*/*.m3u'?[/QUOTE]
Can anyone confirm this? It's a lot of music and I don't want to lose it.

---

### Post by Kimm on 2006-04-21
if you cd to the directory where the files are and run:

```

rm -f *.m3u

```

It should remove all m3u files, leave directories and all other files.
I use this to remove all mp3 files after converting my music library to Ogg using mp32ogg

Edit:
Aaah, with subdirectories.. hm... bit more tricky

Edit 2:
You can do it with two commands:

```

cd /home/admin/Music
rm -f */*.m3u
rm -f *.m3u

```

If you make it go through sub directories it will skip the current directory, thus you need two commands.

PS.
I made some empty textfiles to test this and it worked, so no worries.

---

### Post by gr0kzer0 on 2006-04-21
Heh. I tested my suggestion by backing up my own music then selectively deleting the backup. 'rm -r' works, 1 command, if u have files to delete in the subdirectories but none in just Music (you get what i mean?) But run it with sudo or it'll ask about every write-protected file. Backup with 'cp -r' 1st if you want to test it.

---

### Post by xenmax on 2006-04-21
You can always use ls instead of "rm" to check if wildcards work.

You can also try somthing like
```
find . -name "*.m3u" -exec ls '{}' \;
```
where you can replace "." with base directory you want or cd to that dir and then try the command.
If it works, you can use rm instead of ls :)

---

### Post by OffHand on 2006-04-21
[QUOTE=Kimm]if you cd to the directory where the files are and run:

```

rm -f *.m3u

```

It should remove all m3u files, leave directories and all other files.
I use this to remove all mp3 files after converting my music library to Ogg using mp32ogg

Edit:
Aaah, with subdirectories.. hm... bit more tricky

Edit 2:
You can do it with two commands:

```

cd /home/admin/Music
rm -f */*.m3u
rm -f *.m3u

```

If you make it go through sub directories it will skip the current directory, thus you need two commands.

PS.
I made some empty textfiles to test this and it worked, so no worries.[/QUOTE]Did what you said but it didn't work:

admin@linux:~/Music$ ls
albums  artist  ep  labels  mixes  new  temp  tracks
admin@linux:~/Music$ rm -f */*.m3u
admin@linux:~/Music$ rm -f *.m3u

Didn't remove the .m3u files.

---

### Post by OffHand on 2006-04-21
[QUOTE=gr0kzer0]You need to search the subdirectories. How about 'rm -r /home/admin/Music/*/*.m3u'?[/QUOTE]

admin@linux:~/Music$ rm -r /home/admin/Music/*/*.m3u
rm: cannot remove `/home/admin/Music/*/*.m3u': No such file or directory

---

### Post by Kimm on 2006-04-21
> 
Did what you said but it didn't work:

admin@linux:~/Music$ ls
albums artist ep labels mixes new temp tracks
admin@linux:~/Music$ rm -f */*.m3u
admin@linux:~/Music$ rm -f *.m3u

Didn't remove the .m3u files.


Then you have to have some privelage problems, I just tried it again without any problems on .txt files:

> 
kim@ubuntu:~/test$ find */*
test2/test.apg
test2/test.bzz
test2/test.img
**test2/test.txt**
test3/test.apg
test3/test.bzz
test3/test.img
**test3/test.txt**
test4/test.apg
test4/test.bzz
test4/test.img
**test4/test.txt**
test5/test.apg
test5/test.bzz
test5/test.img
**test5/test.txt**
test6/test.apg
test6/test.bzz
test6/test.img
**test6/test.txt**
kim@ubuntu:~/test$ rm -f */*.txt
kim@ubuntu:~/test$ rm -f *.txt
kim@ubuntu:~/test$ find */*
test2/test.apg
test2/test.bzz
test2/test.img
test3/test.apg
test3/test.bzz
test3/test.img
test4/test.apg
test4/test.bzz
test4/test.img
test5/test.apg
test5/test.bzz
test5/test.img
test6/test.apg
test6/test.bzz
test6/test.img
kim@ubuntu:~/test$


---

### Post by OffHand on 2006-04-22
Thanks for the help so far. I still would like to know how I can delete the files with the command line though. Any ideas? The folder Music only contains subfolders btw, no .m3u files.

---

### Post by xenmax on 2006-04-22
Did you try the "find command with exec option" i suggested?
If so, what is wrong with it? If you post results, i can try and see whats wrong - [that way i learn at your expense] ;):)

---

### Post by OffHand on 2006-04-22
[QUOTE=xenmax]Did you try the "find command with exec option" i suggested?
If so, what is wrong with it? If you post results, i can try and see whats wrong - [that way i learn at your expense] ;):)[/QUOTE]```
admin@linux:~$ find ~/Music -name "*.m3u" -exec rm '{}' \;

``` Did do the trick. Thanks a bunch  :D This is why I love Linux... POWER

---

