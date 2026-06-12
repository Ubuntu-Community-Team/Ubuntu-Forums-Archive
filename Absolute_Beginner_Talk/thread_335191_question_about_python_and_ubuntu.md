---
title: "question about python and ubuntu"
date: 2007-01-09
forum: Absolute Beginner Talk
---

### Post by e^(i*pi) on 2007-01-09
Hello everyone.  I just switched from windows to ubuntu this week, and while I am loving it, there are some things I do not quite understand yet.  I tried to download Python 2.5, and it didn't really work out that well for me.  It was a compressed file and I can't exactly figure out what to do with it.  After the download it came up in the Archive Manager, which I also don't fully understand.  I didn't mind the problems so much, because I realized I that I have Python 2.4 already on my computer, but I am having an issue there as well.  Back when I was using it on windows, whenever I was working on a program I would just save it on my desktop as a .py file and at any time I could double click it and it would run.  I tried the same thing on here and when I double click it it just brings up my code in a text editor.  I'm sorry to ask so many foolishly simple questions, but I'm new to this and a little confused.  I'm sure once I get everything figured out it will be well worth the effort in learning.

---

### Post by Seine on 2007-01-10
While Windows will associate the .py file with Python because of the file extension, *nix is a little different (as you have discovered).

Firstly, ensure the script is executable using chmod. Try:```
chmod 755 *myscript*
```

Secondly, I believe you need to include a directive at the start of your script that tells Linux where to find the interpreter that will execute your script (i.e. Python). Find the location of your python executable ```
which python
``` and then make the first line of your script ```
#! *{location of the python executable}*
``` e.g. ```
#! /usr/bin/python
```

---

### Post by tweedledee on 2007-01-10
> **e^(i*pi) said:**
> Hello everyone.  I just switched from windows to ubuntu this week, and while I am loving it, there are some things I do not quite understand yet.  I tried to download Python 2.5, and it didn't really work out that well for me.  It was a compressed file and I can't exactly figure out what to do with it.  After the download it came up in the Archive Manager, which I also don't fully understand.  I didn't mind the problems so much, because I realized I that I have Python 2.4 already on my computer, but I am having an issue there as well.  Back when I was using it on windows, whenever I was working on a program I would just save it on my desktop as a .py file and at any time I could double click it and it would run.  I tried the same thing on here and when I double click it it just brings up my code in a text editor.  I'm sorry to ask so many foolishly simple questions, but I'm new to this and a little confused.  I'm sure once I get everything figured out it will be well worth the effort in learning.

Python 2.5 is in the repos, you can get it using synpatic.

If you write click on the python file, you should be able to select an alternative program to open it with - and one of them is probably python (although you may need to right click, select Properties -> Open With and add Python as an option, especially if you've added 2.5 on top of the existing 2.4).  Under Properties -> Open With, you can also change the default to Python, so double-clicking will run instead of edit (doing this for one python file will change it for all).

---

### Post by Iyatos on 2007-01-10
Download + install python2.5 with synaptic, then you will need to use chmod on any scripts you save

---

### Post by meng on 2007-01-10
I think it's still Python 2.4 in the repositories. There are some changes in 2.5 (of course, otherwise it would still be 2.4), so the question is how badly you need to have the latest version. Most Python books are still at 2.4 or earlier. One notable exception is Core Python, 2nd ed. (Wesley Chun)

---

### Post by e^(i*pi) on 2007-01-10
Thanks everybody for the help, however I am still having some problems.  I am no longer concerned with getting 2.5, since I already have 2.4 and the differences are most likely insignificant to me at this point.  As far as getting my applications to run, I'm still not there yet, here is what I have tried so far:

first: I tried the "which python" command and it is in /usr/bin/python, so I added the suggested line to the top of my code, saved it on the desktop, double-clicked it, and still just a text editor. Here is the exact code of the test program I tried:


#! /usr/bin/python

print "test"

raw_input("press enter to exit")

I saved it as test.py to my desktop.


I tried the reccomended "chmod" command, but as I am new to both linux and to command line in general, I am not sure what happend. I typed the command in exactly like this:

chmod 755 test,py

I do hope that I read the previous post correctly and that that was what I needed to type, and the message I got from the terminal was....

cannat acces 'test.py': no such file or directory

:confused: 

I thank all of you again for you efforts, and I would appreciate any more suggestions you have.

---

### Post by moshuptrail on 2007-01-10
sometimes, if the current directory is not in your PATH,
you need to type
$ python ./test.py

it tells python to look in the current directory.  a little different from Windoze

also, you can right-click on test.py in nautilus (like explorer) and choose Properties
then the "Open With" tab, and add /usr/bin/python to the list.

---

### Post by e^(i*pi) on 2007-01-10
thanks, now i'm getting somewhere.

when I do the first line you gave me, python ./test.py.... it runs in the terminal, no problem.

I added /usr/bin/python to the opes_with like you suggested, when I double click the icon or right click and tell it to open with python nothing happens.  It doesn't even think, just sits there

I'm very glad the first suggestion did work though, that has me farther along than I was before.

I still wonder why addint the #! usr/bin/python  as the first line of my code didn't do anything, I've seen that suggestion given to several people on several forums now, so it seems like a lot of people think it should work.

---

### Post by scxtt on 2007-01-10
adding **#!/usr/bin/python** allows you to do **./test.py** from the CLI (if you're in the directory where test.py resides or it's in your $PATH) and the shell will use the executable that's in that line ...

if you do **python test.py** from the CLI (if you're in the directory where test.py resides or it's in your $PATH) you're telling the shell to explicitly use python ...

doing **python ./test.py** seems kinda silly ...

---

### Post by noisc on 2007-01-10
> **e^(i*pi) said:**
> thanks, now i'm getting somewhere.

when I do the first line you gave me, python ./test.py.... it runs in the terminal, no problem.

I added /usr/bin/python to the opes_with like you suggested, when I double click the icon or right click and tell it to open with python nothing happens.  It doesn't even think, just sits there


I'm a complete newbie to linux and ubuntu, so take whatever I say with a very, very small grain of salt

Did you ever change your permissions correctly? Did the 'chmod 755 test.py' do what you needed it to do? If you still get error messages about not finding test.py:
If you saved test.py on your desktop, you need to do a 'cd Desktop' in a fresh terminal window to get the directory it's in. Then you might have to do '**sudo** chmod 755 test.py' if you're not logged in as root.

I need to have the following in order to run the script from Nautilus:
a.) my #! /usr/bin/python line at the beginning of my script
b.) my permissions set correctly

If either of these conditions aren't met, I get a similar problem that you have: I run the script from Nautilus, but basically nothing happens; a terminal window pops up and closes almost instantly. (Probably yelling at me about some error.)

---

### Post by rccharles on 2007-01-11
> **e^(i*pi) said:**
> 
first: I tried the "which python" command and it is in /usr/bin/python, so I added the suggested line to the top of my code, saved it on the desktop, double-clicked it, and still just a text editor. Here is the exact code of the test program I tried:


#! /usr/bin/python



I tried the reccomended "chmod" command, but as I am new to both linux and to command line in general, I am not sure what happend. I typed the command in exactly like this:

chmod 755 test,py

I do hope that I read the previous post correctly and that that was what I needed to type, and the message I got from the terminal was....

cannat acces 'test.py': no such file or directory

:confused: 


I suspect that you were not in the correct directory ( another name for folder ).  Find your way to the terminal. applications > accessories  > terminal 

to see the current directory type:
pwd

# this command will return cryptic results.
ls -l

You should notice the first letter d means directory.
Change to the desktop directory

cd Desktop

ls -l

See if you can find the file.

then do the chmod command & check the result via ls -l

Robert

---

### Post by e^(i*pi) on 2007-01-12
thanks everyone, you've been a great help.  I was indeed in the wrong directory, and after changing to the the right one, running the sudo chmod command and adding the lind of code I can finally run my program by double clicking it.  Well, almost....when I double click it I get a message box asking if I want to run it or display its contents, but I'm not complaining, I'm just happy it will run of the desktop period.  I have always heard that linux has a great community, and now I've seen for myself that it is true, it's much nicer over here.  Thanks again.

---

### Post by tweedledee on 2007-01-13
> **e^(i*pi) said:**
> thanks everyone, you've been a great help.  I was indeed in the wrong directory, and after changing to the the right one, running the sudo chmod command and adding the lind of code I can finally run my program by double clicking it.  Well, almost....when I double click it I get a message box asking if I want to run it or display its contents, but I'm not complaining, I'm just happy it will run of the desktop period.  I have always heard that linux has a great community, and now I've seen for myself that it is true, it's much nicer over here.  Thanks again.

Two additional tips:

You do not need to use the command line to change the permissions (provide you own the file, not root), you can do it by right-clicking, selecting Properties -> Permissions, and enabling the "execute" option.

Second, to deal with the "run vs open" issue, you can change that behavior in Nautilus.  In a Nautilus window, go to Edit -> Preferences -> Behavior, then the middle selection allows you to determine what happens when you select an executable & editable file.  Personally I go with "always view" and just choose open with "Python" or a custom run script I've set up to execute other types; you may want to do the opposite or just leave it alone.  Just keep in mind this setting will apply to all scripts, not just Python ones.

---

