---
title: "Using and Creating SFV files in Ubuntu 7.10"
date: 2008-02-06
forum: Absolute Beginner Talk
---

### Post by papuccino1 on 2008-02-06
I recently downloaded this little program called: cksfv

Saw it in a forum somewhere and I think it's what I need. Found it in Synaptic and installed it. 

Here's my questions: 

1. How do I use it because when I right click a RAR file I don't get the option: "Create SFV file" in the shell. I know the program is not malfunctioning, it's just my newbie-ness to doing this in Linux.

2. Is this the program right here in my System File\Usr\Bin????? Not really sure on this.

[IMG]http://i32.tinypic.com/20ac950.png[/IMG]


3. How do I split a file into smaller rar files. Like .rar1 .rar2. rar3 etc.

Can someone point me in the right direction please?:)

---

### Post by papuccino1 on 2008-02-07
Bump.

---

### Post by Ptero-4 on 2008-02-16
I think you may need to use it through the console (Applications>Accesories>Terminal).

---

### Post by mm2004 on 2008-03-01
Hi i have created a program that will after rar-ing your files it will create .sfv files for the rar's also it has a gui dialog to make it easy for newbies to use also hope this helps :)

take a look here [http://ubuntuforums.org/showthread.php?t=708398&highlight=rar]("http://ubuntuforums.org/showthread.php?t=708398&highlight=rar")

---

### Post by victor.zamanian on 2008-06-06
In case you're still interested, here is some help:

1.
You must use the program in a terminal shell. Open the Applications menu, go to Accessories, then Terminal (or press Alt+F2 and type in "gnome-terminal"). Then use the command "cd" and the path to where the SFV file is which you want to use to verify your files. Then use cksfv as such:
```
$ cksfv -f FILE_TO_OPEN.sfv
```
or
```
$ cksfv -r
```
to check all subdirectories for SFV files and open them with the program.

You can create SFV files with cksfv as well, by not providing any switches to the program (switches are what is telling the program what to do, and usually start with one or two dashes, like -f and -r for instance). To create an SFV file of all the MP3 files in a directory, for example, use the following command:

```
$ cksfv *mp3
```
This will output the results to the Terminal shell window. If you want to save it to a file, you could add an output redirection command, like so:

```
$ cksfv *mp3 > a_file.sfv
```

2.
That should be the program in that directory, yeah. If you want to know this because you want to make the program the default program for SFV files in Nautilus, you should be warned. I never got that to work.

3.
Splitting a RAR file is something I'm not sure how to do. I do however know how to create RAR files that are in split volumes. What I mean is, I don't know of a way to split already-created RAR files, but I know how to package a file into split RAR volumes. It goes like this:

First you must install the rar program:
$ sudo apitude install rar

Then you navigate ("cd") to the directory where you have your files using the Terminal shell (always with the terminal shell... :). Now you use rar in the following way:

rar <command> <switches> <name_of_rar_file(s)> <files_to_archive>
where <command> can be e, a, u etc for extract, add and update, respectively. We will be using a for add. Switches will be -v<size> where <size> will be the size of your choice. In this example, I will use 5000, which will mean 5000*1024 bytes = 5120000 B. So now we put all of it together, and the command becomes:
```
$ rar a -v5000 archived.rar /path/to/my/stuff/*mp3
```

This will put all MP3 files in /path/to/my/stuff into the file "archived.rar" in the current folder. Be careful not to put a space between -v and 5000. It really needs to be "-v5000".

Sidenote: This command will produce volume names using the "new scheme" which means they will look like "archived.part1.rar, archived.part2.rar" etc. If you want the "old naming scheme", just add one switch to the command, namely "-vn":
```
$rar a -v5000 -vn archived.rar /path/to/my/stuff/*mp3
```

This will produce files with the names "archived.rar, archived.r00, archived.r01" etc.

Hope this helps. :-)

---

