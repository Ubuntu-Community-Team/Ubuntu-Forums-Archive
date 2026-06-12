---
title: "extracting with 7za (p7zip)?"
date: 2008-01-29
forum: Absolute Beginner Talk
---

### Post by iansane on 2008-01-29
Hi, I am trying out p7zip. I found the command to launch it and to make an archive of several files at once but I am having trouble extracting to a certain directory. Here is what I have tried.

```
 ian@lotus-control:~/Desktop$ 7za e test2.7z -o testdirectory


Error:
Incorrect command line
ian@lotus-control:~/Desktop$ 
```

and 

```
 ian@lotus-control:~/Desktop$ 7za e test2.7z testdirectory

7-Zip (A) 4.51 beta  Copyright (c) 1999-2007 Igor Pavlov  2007-07-25
p7zip Version 4.51 (locale=en_US.UTF-8,Utf16=on,HugeFiles=on,2 CPUs)

Processing archive: test2.7z


No files to process
ian@lotus-control:~/Desktop$ 
```

as you can see, I am trying to tell 7za to extract the files into the directory, "testdirectory"
The man page says -o <directory> for output directory. I don't understand the error for the second one because if I right click and extract here, the files are in there. Can someone tell me the exact commands to do this? Thanks

---

### Post by PinkFloyd102489 on 2008-01-29
Try doing:

```

7za -eo test2.7z testdirectory

```

---

### Post by iansane on 2008-01-29
No that doesn't work.

```
 ian@lotus-control:~$ 7za -eo test2.7z testdirectory


Error:
Incorrect command line 
```

I've tried some other variations to (with and without the - and moving the o around.)

Seems like it would follow a standard. Compileing with gcc  It would be 

```
 gcc  -O file -o outputfile 
```

seems like the -o would be used the same way if there is some kind of standard.

---

### Post by iansane on 2008-01-29
anyone? suggestions, comments, or rude remarks? :-)

---

### Post by iansane on 2008-01-30
wow does anyone know how to use p7zip?

---

### Post by bumanie on 2008-01-30
This may help you, I have used 7zip, but only once and that was a while ago.

Ubuntu is able to deal with .7z archives. Do the following in a terminal.

Code:
> sudo apt-get -y install rar unrar p7zip p7zip-fullThis will install the 7zip and rar packages.

Now you will be able to double click on a .7z archive and file roller will be able to unpack these archives.

Very simple. Make sure you have the universe repositories enabled.

---

### Post by iansane on 2008-02-01
Thanks for the info. I'm trying to learn how to do everything through terminal though. A lot of people say that is best and I now agree even though I was fighting it, because what do you do if you don't have a GUI? And using terminal actually helps me to understand the indepth workings of a computer and OS. The problem is, when I do what the man tells me to and it doesn't work, sometimes I come across something that no one on the forums can tell me the answer to. How do I learn about a particular command that way? Anyway, thanks for the other info. :-)

---

### Post by crazybilly on 2008-06-10
I did some looking around the other day...it looks like the -o switch actually runs right into the path.  Like this:

7z x stuff.7z -o/home/name/destination

What I can't figure out is how to get 7z to do more than one file at a time.

Anybody got any cluse about that?

---

### Post by totals2002 on 2008-06-17
I also need to know the same thing ... seems strange for such an obvious feature to be absent.

---

