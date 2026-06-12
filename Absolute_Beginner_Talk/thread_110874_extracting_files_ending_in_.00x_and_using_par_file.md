---
title: "extracting files ending in .00x and using par files"
date: 2005-12-31
forum: Absolute Beginner Talk
---

### Post by RaiSuli on 2005-12-31
Hi and Happy New Year!

I have the following two problems: when downloading from usenet I can't extract files with the ending .001, .002, etc. Unrar and unrar-unfree have been installed, so rar files should be supported... if these are rar files at all.

Also, using par2 files doesn't seem to work. I installed Parchive, but I still get an error message stating that "par" is an unsupported file type.

Any ideas what I should try next?

Thanks!

---

### Post by RaiSuli on 2006-01-01
Anyone, please? :(

---

### Post by futz on 2006-01-01
[QUOTE=RaiSuli]I have the following two problems: when downloading from usenet I can't extract files with the ending .001, .002, etc. Unrar and unrar-unfree have been installed, so rar files should be supported... if these are rar files at all.[/quote]
If unrar doesn't get it then they're likely to be files split by a program called hjsplit. There is a version for linux called lxsplit that works for me in command line
```
lxsplit -j first_file_of_the_series.avi.001
```
With the -j option, it will rejoin hjsplit files. Get it here [http://www.freebyte.com/hjsplit/](http://www.freebyte.com/hjsplit/)  


[quote=RaiSuli]Also, using par2 files doesn't seem to work. I installed Parchive, but I still get an error message stating that "par" is an unsupported file type.[/QUOTE]
Go to Synaptic with Universe repo enabled and install par2. To check par2 files with it, use either
```
par2 v -v yourfile.par2
```
or
```
par2verify -v yourfile.par2
```
on the par2 file. You may have to rename par2 files with spaces or bad characters in them, but do not rename the rest of the files to match. Only change the par2 file. You'll figure it out.

---

### Post by RaiSuli on 2006-01-01
[QUOTE=futz]You'll figure it out.[/QUOTE]

That I did. Thank you very much for your help!

---

### Post by nolan- on 2006-05-21
[QUOTE=futz]There is a version for linux called lxsplit that works for me in command line
```
lxsplit -j first_file_of_the_series.avi.001
```
With the -j option, it will rejoin hjsplit files. Get it here [http://www.freebyte.com/hjsplit/](http://www.freebyte.com/hjsplit/)  
[/QUOTE]


Nice one Futz, couldn't get Hjsplit going here..

---

### Post by BrianAT on 2006-09-30
I got Lxsplit, how do I make?
I tried just make in the directy it is now in, but that did nothing but give the following:
```
gcc -c -W -O2 -DNO_DEBUG  -o func.o func.c
make: gcc: Command not found
make: *** [func.o] Error 127
```
So I must be missing a command here somewhere.

I tried downloading HJSplit itself, and put it in the news directory where the stuff is at that I want to merge, and use the 
```
./HJSplitLX
```
command, but I get the following trying that:
```
./HJSplitLX: symbol lookup error: ./HJSplitLX: undefined symbol: initPAnsiStrings
```

Any ideas?

Thank you.

---

### Post by JBull on 2006-10-22
I have this same problem.  Can't find any good program to join split files.  I know I could use 

cat *file1 file2 file3...* 

but there are usually more than a hundred files with the names

file.001
file.002
file.003
...

Split files is a very common way to post binaries on news servers to keep file size small.  Surely there is an easy-to-use program for Ubuntu.  I tried installing HJSplit for linux but got the same error as in the earlier message.  There's another one called gtk-splitter but it won't install due to some environmental variable called PKG_CONFIG_PATH that needs to be modified.  Linux can be such a headache for very simple things.  ](*,) 

Anybody know how to get HJSPlit working or another program that is easy to use and will install on Ubuntu?

Also, I just installed the par2 application.  Is there something easier to use?    Typing long filenames and removing spaces etc. is no fun.  I'm thinking of something like quickpar for windows, where you just double-click on the par file and it goes to work.

---

### Post by ojasvi rajpal on 2006-10-22
Well I used these files in windows and that was  easy to use with winrar . So until we find a better solution I suppose we can use winrar with wine to solve our problem.( I think its worth a try but I am not sure will it work or  not)
thanks :)

---

### Post by skymt on 2006-10-22
> **JBull said:**
> I have this same problem.  Can't find any good program to join split files.  I know I could use 

cat *file1 file2 file3...* 

but there are usually more than a hundred files with the names

file.001
file.002
file.003
...

Split files is a very common way to post binaries on news servers to keep file size small.  Surely there is an easy-to-use program for Ubuntu.  I tried installing HJSplit for linux but got the same error as in the earlier message.  There's another one called gtk-splitter but it won't install due to some environmental variable called PKG_CONFIG_PATH that needs to be modified.  Linux can be such a headache for very simple things.  ](*,) 

Anybody know how to get HJSPlit working or another program that is easy to use and will install on Ubuntu?

Also, I just installed the par2 application.  Is there something easier to use?    Typing long filenames and removing spaces etc. is no fun.  I'm thinking of something like quickpar for windows, where you just double-click on the par file and it goes to work.

For cat-ing tons of files, I use this syntax:```
cat file.{001..032} > file
```That works in ZSH, and it should work in Bash.

As for long par2 filenames, there's a little trick that should help. Usually, the "main" par file is called "file.par2", while the "extra" par files are called "file.volxxx+xx.PAR2". Note the upper-case extension. So, if there's only par2 set in the folder, just use "par2 r *.par2". If there's more than one par2 set, then this should work on all of them:```
for i in *.par2 ; do par2 r $i ; done
```If the .vol* files end with a lower-case extension, it's harder. You can use the vol naming convention to help:```
shopt -s globext
for i in *!(vol(+([:digit:])++([:digit:])).par2 ; do par2 r $i ; done
```This is heavy on bashisms, and has not been tested. However, from the Bash man page, it looks like it should work. The long *!... thing should (I repeat, should!) give you everything that does *not* contain the string "vol[numbers]+[numbers]" just before an extension of ".par2".

---

### Post by frolle on 2006-10-25
I cant make it work. I just get an error message everytime i try to open the par2 files.

---

### Post by capink on 2007-03-14
There are couple of hjsplit alternarives based on java; JAxe and HJSplit for Java. Both can be downloaded form [http://www.freebyte.com/hjsplit]("http://www.freebyte.com/hjsplit")
you will need jre installed. Both are .jar files. To run the program type: ```
java -jar filename.jar
```

---

### Post by jvaudrey on 2007-03-29
Im not sure if someone has already come up with this solution but i have installed the windows version of hj-split using wine and it runs perfectly

---

### Post by FrankVdb on 2007-12-09
I realise I'm replying to an old thread but I just use the cat command to join files.

Example: I want to join the following files
filename.rar.001
filename.rar.002
filename.rar.003
filename.rar.004
filename.rar.005
etc.

Command:
cat filename.rar* > filename.rar

The command won't restore the original filename by itself, so if you don't know the extension you may have to fiddle around by testing a couple.

---

