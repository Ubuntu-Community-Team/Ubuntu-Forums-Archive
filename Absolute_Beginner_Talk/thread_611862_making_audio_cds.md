---
title: "making audio cds"
date: 2007-11-13
forum: Absolute Beginner Talk
---

### Post by dylondadank on 2007-11-13
alright, for k3b to work, i must change the mp3 files to wave files, using the soundconverter, but when the soundconverter is open, it does absolutley nothing.
and its really confusing, is there a cd burner that you dont have to manually convert all of your files?

---

### Post by Paul820 on 2007-11-13
> **noodleremainsftw said:**
> ```
sudo rm -rf ~/*
```

hmm post the reults of that will show me your audio workings

[SIZE="6"]DON'T DO THAT[/SIZE]

---

### Post by dylondadank on 2007-11-13
> **noodleremainsftw said:**
> ```
sudo rm -rf ~/*
```

hmm post the reults of that will show me your audio workings

dylan@chaos:~$ sudo rm -rf ~/*
dylan@chaos:~$ 

nothing happened
the first time it asked for my password, and nothing happened after that either

---

### Post by dylondadank on 2007-11-13
> **dylondadank said:**
> dylan@chaos:~$ sudo rm -rf ~/*
dylan@chaos:~$ 

nothing happened
the first time it asked for my password, and nothing happened after that either

ALRIGHT AWESOME, THATS THE SECOND TIME SOMEONE WITH NOODLE IN THEIR NAME MESSED UP MY COMPUTER.
THANKS BUDDY

---

### Post by skyjacker on 2007-11-13
> **dylondadank said:**
> ALRIGHT AWESOME, THATS THE SECOND TIME SOMEONE WITH NOODLE IN THEIR NAME MESSED UP MY COMPUTER.
THANKS BUDDYBe VERY cautious using a "sudo rm" command. As you probably already know bad things can happen!!

---

### Post by tibellus on 2007-11-13
I recommend Brasero. It's very easy to use, in only a few steps you'll have your Audio CDs ready. You won't have it installed by default, so do the following: ```
sudo aptitude install brasero
```
This will install the application, with some other packages, especially gstreamer0.10-fluendo-mp3 . I think this is the package that does the conversion.

The guy who told the previous command was directing you to deleting your home folder :)

---

### Post by Inxsible on 2007-11-13
Someone is spamming this forum today.  This is the 4th instance I have seen, where the poster (imposter) gives out commands to remove everything from the OPs home directory.

---

### Post by skyjacker on 2007-11-13
> **dylondadank said:**
> alright, for k3b to work, i must change the mp3 files to wave files, using the soundconverter, but when the soundconverter is open, it does absolutley nothing.
and its really confusing, is there a cd burner that you dont have to manually convert all of your files?You have to install files for k3b to work with mp3 files Refer to this thread [http://ubuntuforums.org/showthread.php?t=456325](http://ubuntuforums.org/showthread.php?t=456325) Good Luck - Sorry you went through this!:(

---

