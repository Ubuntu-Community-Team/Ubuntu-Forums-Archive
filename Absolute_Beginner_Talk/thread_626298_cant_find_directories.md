---
title: "cant find directories"
date: 2007-11-28
forum: Absolute Beginner Talk
---

### Post by W33ZY_GHz on 2007-11-28
installed ubuntu and have benn working with it tring to find dir and such.Well i am only geting 1 dir and it is desktop. any input? (/boot /bin etc...)

---

### Post by jordanmthomas on 2007-11-28
?  I'm not sure what you're asking here..
What do you get if you type this in a terminal? (applications --> accessories --> terminal)
```
ls -a ~
```
This will list all the directories in your home folder.

---

### Post by W33ZY_GHz on 2007-11-28
ok thank you it brought up more dir's.  (Thats not what the manual said to do).

---

### Post by jordanmthomas on 2007-11-28
If you leave off the -a from the ls command, you will not see the hidden folders.
Just curious, what did the manual say to do?

---

### Post by ryanVickers on 2007-11-29
still, what are you trying to do?
cd will change directories
mkdir will make one
rm wil remove stuff
mv to move/rename
cp to copy & rename
ls to list
etc... :p
Do you seriously have a manual for something...? just wondering..., could you explain? ;)

---

### Post by W33ZY_GHz on 2007-11-29
ok i am tring to install S.A.T.A.N. and i cant figure it out any ideas. I was reffering to the online forums guide when i said manual.

---

### Post by jordanmthomas on 2007-11-29
Just so you know, s.a.t.a.n is an *ancient* program.
There's GOT to be something newer that will do what you want.  All the pages I've found about it are from 1997 or so and most (if not all) of the download links are broken.

What features from s.a.t.a.n were you looking for?  Perhaps we can guide you to something else.

**edit**
As best as I can tell, there's a program called Nagios that picked up where s.a.t.a.n left off.

---

### Post by W33ZY_GHz on 2007-11-29
ok i got that but how do i get it to install?

---

### Post by jordanmthomas on 2007-11-29
get what to install?

---

### Post by W33ZY_GHz on 2007-11-29
the program nagios  i extracted it to my desktop and now i want to install

---

### Post by jordanmthomas on 2007-11-29
Ah, my friend.  You have much to learn about installing software in Ubuntu.  This isn't like Windows; you don't have to go to some website and find the right download.
First, read [this]("http://www.psychocats.net/ubuntu/sources") link and enable the universe repository.

Then, you can either go to Synaptic Package Manager (System --> Administration --> Package Manager) and search for nagios (I believe nagios2 is its name) or just install it from the command line with
```
sudo apt-get install nagios2
```

If you are really wanting to install from source, though, read this:
[http://monkeyblog.org/ubuntu/installing/#source](http://monkeyblog.org/ubuntu/installing/#source)
and have fun.

---

### Post by W33ZY_GHz on 2007-11-29
well now i feel like a big idiot. i got it installed but now cant find it to run. is there a command to make programs run from the terminal?

---

### Post by jordanmthomas on 2007-11-29
You can follow the instructions here:
[http://ubuntuforums.org/showthread.php?t=223498](http://ubuntuforums.org/showthread.php?t=223498)
You've already done up to step 6, and the packages they install by hand in step 7 are in the repositories as well (meaning they're in synaptic)

You still need to install apache (step 2), just follow their instructions there.
For the record, I have never used satan / nagios so I can't be of too much help probably, beyond helping with obvious error messages.  I'm not entirely sure what exactly these programs are even used for (and yes, I'm too lazy to look it up at the moment :) )

---

