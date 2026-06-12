---
title: "School Software needed!"
date: 2006-02-27
forum: Absolute Beginner Talk
---

### Post by g_butler2000 on 2006-02-27
I'm in the midst of learning Ubuntu so we can setup this server at a non-profit school.  They are wanting a piece of software that would keep a gradebook, lesson plan, student database and homework section.  Is there something out there for Linux?  Any links are welcomed.

Thanks,

Gary

---

### Post by Kimm on 2006-02-27
OpenOffice.org Calc perhaps? :-k

---

### Post by shamrock_uk on 2006-02-27
[QUOTE=g_butler2000]I'm in the midst of learning Ubuntu so we can setup this server at a non-profit school.  They are wanting a piece of software that would keep a gradebook, lesson plan, student database and homework section.  Is there something out there for Linux?  Any links are welcomed.

Thanks,

Gary[/QUOTE]

You may want to be considering [Edubuntu](http://www.edubuntu.org) which is designed with this scenario in mind - in other words for non-techie teachers to setup and maintain servers.

According to the [tour](http://www.edubuntu.org/tour.html) it includes software called SchoolTool Calendar which be similar to what you're looking for.

Also the bundled KDE Edutainment package includes an exam creator [KEduca](http://edu.kde.org/keduca/index.php) which you may find useful.

---

### Post by aysiu on 2006-02-27
Edubuntu has a Schooltool Calendar and OpenOffice:
[http://www.edubuntu.org/tour.html](http://www.edubuntu.org/tour.html)

I don't know if there's any special database program, though. When I was a teacher, I simply used Excel to do all my grades and attendance. OpenOffice Calc would be a good substitute for that (nothing complicated that only Excel can do).

I knew a lot of teachers who did grades in physical (paper) gradebooks--nothing electronic at all.

---

### Post by stalefries on 2006-02-27
Schootool is exactly what you need. It is designed for that purpose. 

Also, you should seriously consider Edubuntu. It is tailored for schools.

Third, think about using thin clients. It will allow the school to save money on hardware.

---

### Post by dvarsam on 2006-02-27
What "stalefries" wanted to write was "schooltool".

If this is what you want, either launch "Synaptic" & perform a Search on this (to read more), or

visit: [www.schooltool.org/](www.schooltool.org/) to find more info about it.

---

### Post by souteneur3190 on 2006-02-27
is edubuntu for schools of all ages?  Iono, ive always thought it looked like something for primary school.

---

### Post by srt4play on 2007-05-15
FWIW, my sister teaches 1st grade and uses gradekeeper on Windows... which works perfectly from what I can tell under wine.

---

### Post by laidback on 2007-05-15
If it's of any interest the amgazine Linux Format did an article on Linux in schools (primary to adult).
This is the issue:-

[http://www.linuxformat.co.uk/modules.php?op=modload&name=NewArchives&issue=81](http://www.linuxformat.co.uk/modules.php?op=modload&name=NewArchives&issue=81)
July 2006

---

### Post by srt4play on 2007-05-16
Throwing this out there for anyone looking for a native gradebook app:

[http://gradel.sourceforge.net](http://gradel.sourceforge.net)

Is very similar to gradekeeper, which seems to be a popular Windows app.

---

### Post by dimeotane on 2007-09-21
Has anyone gotten gradeL to install and run on ubuntu?  
I installed gambas and build-essential and then did ./compile.sh but got an error:
 

```
dell-laptop:~/Desktop/gradel$ ./compile.sh

Checking for compiled components...

Compiling GradeL with gbc -p -a ...
gbc: ERROR: Cannot open file: /usr/share/gambas/info/gb.qt.kde.list
Creating executable archive "gradel" with gba ...
Done!

./compile.sh: 38: Syntax error: "(" unexpected
```

:confused:

---

### Post by msumurph on 2007-10-11
Actually, I write GradeL using Ubuntu (currently I'm the sole developer).  Anyway, it looks like I have a typo in the install script.  I'll double check it and release a fix if necessary.

It would probably help if I just created a deb package.  I'll put that on the list too ;)

By the way, which version of GradeL you are using?

Allen

---

### Post by msumurph on 2007-10-11
> **dimeotane said:**
> Has anyone gotten gradeL to install and run on ubuntu?  
I installed gambas and build-essential and then did ./compile.sh but got an error:
 

```
dell-laptop:~/Desktop/gradel$ ./compile.sh

Checking for compiled components...

Compiling GradeL with gbc -p -a ...
gbc: ERROR: Cannot open file: /usr/share/gambas/info/gb.qt.kde.list
Creating executable archive "gradel" with gba ...
Done!

./compile.sh: 38: Syntax error: "(" unexpected
```

:confused:

As it turns out, there is a small error in a message that the compile script displays.  It still compiles correctly, I just left out a quotation mark in an "echo" statement.

The install script (install.sh) also has a slight error (another typo) that will give an error, but does still install the gradel program.  You should be able to type "gradel" to run the program.  The next release will include the fix.  

Thanks for giving it a try.

---

### Post by sethtriggs on 2007-10-15
> **msumurph said:**
> As it turns out, there is a small error in a message that the compile script displays.  It still compiles correctly, I just left out a quotation mark in an "echo" statement.

The install script (install.sh) also has a slight error (another typo) that will give an error, but does still install the gradel program.  You should be able to type "gradel" to run the program.  The next release will include the fix.  

Thanks for giving it a try.

Didn't work for me:

```
seth@seth-laptop:~/installers/gradel$ sh ./compile.sh

Checking for compiled components...

Compiling GradeL with gbc -p -a ...
gbc: ERROR: Cannot open file: /usr/share/gambas/info/gb.qt.kde.list
Creating executable archive "gradel" with gba ...
Done!

./compile.sh: 38: Syntax error: "(" unexpected
seth@seth-laptop:~/installers/gradel$ 
seth@seth-laptop:~/installers/gradel$ 
seth@seth-laptop:~/installers/gradel$ sudo sh "./install.sh"

Installing GradeL ...
cp: cannot create regular file `/usr/doc/share/gradel': No such file or directory
Done!  To run type gradel.  Enjoy the program.

seth@seth-laptop:~/installers/gradel$ gradel
sizeof(CLASS) = 256 !
ERROR: #51: Bad archive: Invalid argument

```

I really want to be able to use GradeL too.

-Seth

---

### Post by msumurph on 2007-10-17
> **sethtriggs said:**
> Didn't work for me:

```
seth@seth-laptop:~/installers/gradel$ sh ./compile.sh

Checking for compiled components...

Compiling GradeL with gbc -p -a ...
gbc: ERROR: Cannot open file: /usr/share/gambas/info/gb.qt.kde.list

```

I really want to be able to use GradeL too.

-Seth

The syntax error with the "(" is not a critical thing. The "Cannot open file: /usr/share/gambas/info/gb.qt.kde.list" is a problem.  Looks like you don't have gambas-qt-kde package installed. Try:
```
sudo apt-get install gambas-qt-kde
```

In the next release, I have fixed the compile and install scripts, and I'll have a **deb package** for easy installation on Ubuntu.  I just have to fix a couple more things.  Should be out soon.

---

### Post by sethtriggs on 2007-10-17
> **msumurph said:**
> The syntax error with the "(" is not a critical thing. The "Cannot open file: /usr/share/gambas/info/gb.qt.kde.list" is a problem.  Looks like you don't have gambas-qt-kde package installed. Try:
```
sudo apt-get install gambas-qt-kde
```

In the next release, I have fixed the compile and install scripts, and I'll have a **deb package** for easy installation on Ubuntu.  I just have to fix a couple more things.  Should be out soon.

It can't find gambas-qt-kde, but it did find gambas-gb-qt-kde, which I already installed. Indeed, I installed all Gambas packages from Synaptic. Do I have to do another configuration or something?

-Seth

On edit: For some reason the kde error disappeared after I launched Gambas from the Applications menu. However, Gradel still fails to load.

```

seth@seth-laptop:~$ cd installers/gradel
seth@seth-laptop:~/installers/gradel$ sh ./compile.sh

Checking for compiled components...

Compiling GradeL with gbc -p -a ...
OK
Creating executable archive "gradel" with gba ...
Done!

./compile.sh: 38: Syntax error: "(" unexpected
seth@seth-laptop:~/installers/gradel$ sudo sh ./install.sh

Installing GradeL ...
cp: cannot create regular file `/usr/doc/share/gradel': No such file or directory
Done!  To run type gradel.  Enjoy the program.

seth@seth-laptop:~/installers/gradel$ gradel
sizeof(CLASS) = 256 !
ERROR: #51: Bad archive: Invalid argument
seth@seth-laptop:~/installers/gradel$ 

```

---

### Post by msumurph on 2007-10-17
> **sethtriggs said:**
> 

```

seth@seth-laptop:~$ cd installers/gradel
seth@seth-laptop:~/installers/gradel$ sh ./compile.sh

Checking for compiled components...

Compiling GradeL with gbc -p -a ...
OK
Creating executable archive "gradel" with gba ...
Done!

./compile.sh: 38: Syntax error: "(" unexpected
seth@seth-laptop:~/installers/gradel$ sudo sh ./install.sh

Installing GradeL ...
cp: cannot create regular file `/usr/doc/share/gradel': No such file or directory
Done!  To run type gradel.  Enjoy the program.

seth@seth-laptop:~/installers/gradel$ gradel
sizeof(CLASS) = 256 !
ERROR: #51: Bad archive: Invalid argument
seth@seth-laptop:~/installers/gradel$ 

```

Yes, I had a typo, the package is gambas-gb-qt-kde as you have stated.  Try this:

From the prompt, change to the [edit]gradel source directory, then type:

```
./gradel
```

This will try to run the local copy of the gradel executable archive.  If it starts gradel, then the install script is just bunk (which is weird because it worked here.)  If it doesn't work, the compile script is bunk - I can tell you the commands to type to get it running manually if this happens.

Like I said earlier, the next version will include a deb :).

---

### Post by rich.bradshaw on 2007-10-17
Moodle!

It's amazing!

It's a web app!

Go and get it now!

---

### Post by sethtriggs on 2007-10-17
> **msumurph said:**
> Yes, I had a typo, the package is gambas-gb-qt-kde as you have stated.  Try this:

From the prompt, change to the gambas source directory, then type:

```
./gradel
```

This will try to run the local copy of the gradel executable archive.  If it starts gradel, then the install script is just bunk (which is weird because it worked here.)  If it doesn't work, the compile script is bunk - I can tell you the commands to type to get it running manually if this happens.

Like I said earlier, the next version will include a deb :).

Thanks...

I don't know how to change to the Gambas source directory...cd doesn't work with sudo and I don't know which gambas directory is the right one.

I'm relatively new as a Linux user.

-Seth

---

### Post by msumurph on 2007-10-17
> **sethtriggs said:**
> Thanks...

I don't know how to change to the Gambas source directory...cd doesn't work with sudo and I don't know which gambas directory is the right one.

I'm relatively new as a Linux user.

-Seth

Man, I am 0 for 2 today on typos.  What I meant to say was change to the gradel directory and type:
```
./gradel
```

The gradel directory is the one you downloaded and extracted.  It is probably in your home directory somewhere.  No need for sudo, just type it as yourself.  Sorry for the confusion.  I guess the kids made me crazy today. :)

The other option is to just start Gambas (located under Programming from the Application Menu of Ubuntu), open the gradel project and execute it there by hitting the green arrow.

---

### Post by ubuntu27 on 2007-10-17
Like everyone said get [Edubuntu]("http://www.edubuntu.org"):

The [Edubuntu Tour Link]("http://www.edubuntu.org/screenshots")s is broken in the other post, here is the correct one:

[http://www.edubuntu.org/screenshots](http://www.edubuntu.org/screenshots)

and 

[http://www.edubuntu.org/UsingEdubuntu](http://www.edubuntu.org/UsingEdubuntu)


Edubuntu's [URL="http://www.edubuntu.org/FAQ"]Frequently Asked Questions[/URL


Tomorrow the new version of Ubuntu, Edubuntu, Kubuntu, and Xubuntu is coming. So just wait until it's released :)]

---

### Post by sethtriggs on 2007-10-17
> **msumurph said:**
> Man, I am 0 for 2 today on typos.  What I meant to say was change to the gradel directory and type:
```
./gradel
```

The gradel directory is the one you downloaded and extracted.  It is probably in your home directory somewhere.  No need for sudo, just type it as yourself.  Sorry for the confusion.  I guess the kids made me crazy today. :)

The other option is to just start Gambas (located under Programming from the Application Menu of Ubuntu), open the gradel project and execute it there by hitting the green arrow.

```

seth@seth-laptop:~/installers/gradel$ ./gradel
sizeof(CLASS) = 256 !
ERROR: #51: Bad archive: Invalid argument
seth@seth-laptop:~/installers/gradel$ J

```

You know, I wonder...is this because I'm running 64-bit Ubuntu or something?

-Seth

---

### Post by skompier on 2007-10-17
> **rich.bradshaw said:**
> Moodle!

It's amazing!

It's a web app!

Go and get it now!

That's what I was thinking also..[http://moodle.org/](http://moodle.org/)

---

### Post by crav on 2007-10-17
My highschool used to use a very expensive, very difficult to use software for grades, etc.over the pas couple years they've been working on a switch to moodle, and the teachers who aren't deeply in love with the old software seem to like moodle.

---

### Post by msumurph on 2007-10-18
> 
You know, I wonder...is this because I'm running 64-bit Ubuntu or something?

-Seth

Yes, unfortunately I think Gambas at this time only runs on 32-bit, not 64-bit.  So subsequently, any program written in Gambas won't run on 64-bit operating systems.  Not sure if or when this will be addressed by the Gambas developers.

---

### Post by sethtriggs on 2007-10-18
I would have installed 32-bit but I had totally wanted to take advantage of the 64-bit processor I have. Maybe once I get a bigger HD I can try to do this or something. Heh...40GB is not enough for me to do what I want to do with this really.

Now, doing this on my main desktop PC...that might do it nicely...

-Seth

---

### Post by Frak on 2007-10-18
Ever try Edubuntu?

---

### Post by sethtriggs on 2007-10-21
Edubuntu would be too much for me to use. All I want is a gradebook.

-Seth

---

