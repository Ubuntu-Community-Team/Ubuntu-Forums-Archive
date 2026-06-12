---
title: "Help please - Perl and Paths"
date: 2006-04-06
forum: Absolute Beginner Talk
---

### Post by cliff0108 on 2006-04-06
I am a new Linux user and wanted to familiaroze myself with Perl at the same time I learn about Linux.

My Perl tutorial (lesson 1 !! ) suggests writing a small file saved as 'hello'

#! /usr/bin/perl
print "Hello, World!\n;

In saving the file - I just used my Home directory and tried  to execute  it by typing  'perl hello'****

When I do this I get an error message :
"Can't open perl script "hello": No such file or directory"

I assume the problem is that the perl interpreter is way down in /usr/bin and there is no "path' to it in /home/hello .

I imagine there may be serveral ways to get up and running in perl - but I wonder if someone could help me do it the correct way. 

Cliff

---

### Post by oldmanstan on 2006-04-06
[QUOTE=cliff0108]I am a new Linux user and wanted to familiaroze myself with Perl at the same time I learn about Linux.

My Perl tutorial (lesson 1 !! ) suggests writing a small file saved as 'hello'

#! /usr/bin/perl
print "Hello, World!\n;

In saving the file - I just used my Home directory and tried  to execute  it by typing  'perl hello'****

When I do this I get an error message :
"Can't open perl script "hello": No such file or directory"

I assume the problem is that the perl interpreter is way down in /usr/bin and there is no "path' to it in /home/hello .

I imagine there may be serveral ways to get up and running in perl - but I wonder if someone could help me do it the correct way. 

Cliff[/QUOTE]

As long as perl is in the $path you should be able to execute it no matter what your working directory is. That first line "#! /usr/bin/perl" is called the shebang line and it tells the OS where to find the interpreter to run the script, since you've got that (assuming perl is installed in that location) you should be able to just do ```
./hello
```and have it run just fine.

anyway, the fact that you got the error in the first place indicates perl is on your system and in your $path so the problem is with the script itself

the error you got is most likely caused by the filename being wrong or you being in the wrong directory when you tried to run it, make sure the file is saved with the name you think it should be (i.e. there isn't an extension like .pl on it or something) then check that when you run it you are in the right directory (type *ls* just before running it, you should see your file in the list)

also, you need to close the quotes in your print command :)

---

### Post by cliff0108 on 2006-04-06
Thanks so much !
I made a newbie error of naming the file Hello and executing it hello ... <sigh !! >

However when I execute it perl hello it works - but ./hello does not
What is happening?

cliff@ubuntu:~$ perl hello
Hello, World !
cliff@ubuntu:~$ ./hello
bash: ./hello: Permission denied

I'd like to run may commands without typing perl every time.

---

### Post by siminone on 2006-04-06
type in 

chmod +x hello

---

### Post by cliff0108 on 2006-04-06
Do I have to do this with every file I now create in Perl to change the
 file permissions ?

---

### Post by cliff0108 on 2006-04-06
Or I could put all my perl applications in to one subdirectory in Home and use chmod to set file permissions on all of them ?
ie chmod + x perlapps   or something ??
Sorry if I am being a bit 'thick' this morning :o)

---

### Post by htinn on 2006-04-06
The easy way: create a template.

Take your hello.pl file and move it to ~/Templates (create "Templates" if you don't already have it). Then, any time you need a new perl file, go to the File/Create New Document/hello for a new perl file (with the +x conveniently added at creation time).

---

### Post by cliff0108 on 2006-04-06
Thanks everyone - I think this will get me started ! :)

---

