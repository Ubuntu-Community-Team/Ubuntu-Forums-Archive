---
title: "A little help with wine please"
date: 2007-07-09
forum: Absolute Beginner Talk
---

### Post by zabien1970 on 2007-07-09
I was following the instructions in this lin

[http://ubuntuforums.org/showthread.php?t=491153&highlight=wine](http://ubuntuforums.org/showthread.php?t=491153&highlight=wine)

when I got to :

 Then install it using Wine with the command below. Substitute the actual path that you downloaded the file to. If you installed it to your home directory, substitute your user name with "username." If the filename that you downloaded happens to be different, substitute the correct filename. It is important to put the "\" before spaces in a filename. That tells the CLI that the space isn't the end, it's part of the name.
Code:
   wine /home/username/downloads/Firefox\ Setup\ 2.0.0.4.exe

 I got stuck,
 Being new to linux I'm not sure how to find where it downloaded to and what 'username' to put in, I tried replacing 'username' with my name but that didn't work.

---

### Post by shrift on 2007-07-09
What he is saying to do is to use "wine" the program wine that you have installed to execute the firefox executable to install firefox.

So basically if I downloaded firefox.exe into the "downloads" folder in my home directory, the full directory name for that would be```
/home/bmartens/downloads/firefox.exe
```

to help things use "tab completion" to find what you want. IE: start typing the beginning of the directory you want in the command line, then press tab it will fill in the rest if it can. 

As far as the username part, this is the name that you use to login to ubuntu with. So for you to do what he's saying you'd type in a command line "wine /home/(your login name here)/the folder you downloaded firefox to(probably the desktop if you didn't choose manually)/Fire(then press tab to autocomplete)"

Then it should execute the firefox installer with wine.

---

### Post by zabien1970 on 2007-07-09
That's pretty much what I thought, but it's not working

brendon@brendon-laptop:~$ wine /home/brendon/downloads/Firefox\ Setup\ 2.0.0.4.exe
wine: cannot find '/home/brendon/downloads/Firefox Setup 2.0.0.4.exe'
brendon@brendon-laptop:~$ 

I see it in my download manager 'firefox' but it won't open, 
on my desktop,> right click>open it says no program available to open with

I know I'm close I just don't know what I'm missing

---

### Post by Papi-KB7VGW on 2007-07-09
What I do is open the wine file mgr >Applications>Accessories>wine file.  Then go find your desktop with that.  Double click on the .exe and it will install because it thinks it is in window.  Hope this helps   :)

---

### Post by zabien1970 on 2007-07-09
I don't have anything for wine in applications>accessories

---

### Post by Papi-KB7VGW on 2007-07-09
I would look at >Preferences>Main Menu to see if they are there.  If they are just check the boxes to get them to appear.  I don't remember if I had to do that when I installed wine.  Thats the trouble with getting old  CRS  :popcorn:

---

### Post by zabien1970 on 2007-07-09
Nothing there either :(
Any other suggestions, 
I really am a n00b so I may be missing something obvious,

---

### Post by Campingman on 2007-07-09
Hi,
You could try another way if you are having problems navigating to the folder with the terminal:
Right click on the file> select open with other application>click on the arrow next to use custom command and then on browse>navigate then to wine which is in filesystem/usr/bin select wine and it should then open the apllication with wine.

You could also install nautilus-open-terminal which makes navigating to different folders with the terminal a lot easier.  You can then use nautilus to navigate to the folder you want and right click, an option to open in terminal is now there.

---

### Post by Nekiruhs on 2007-07-09
Deleted by User.
Doh.. Stupid me...

---

### Post by shrift on 2007-07-09
> **zabien1970 said:**
> That's pretty much what I thought, but it's not working

brendon@brendon-laptop:~$ wine /home/brendon/downloads/Firefox\ Setup\ 2.0.0.4.exe
wine: cannot find '/home/brendon/downloads/Firefox Setup 2.0.0.4.exe'
brendon@brendon-laptop:~$ 

I see it in my download manager 'firefox' but it won't open, 
on my desktop,> right click>open it says no program available to open with

I know I'm close I just don't know what I'm missing

The problem is that your trying to execute a file in downloads that doesn't exist. It's on your desktop. So you need ```
wine /home/brendon/Desktop/Firefox\ Setup\ 2.0.0.4.exe

NOT

wine /home/brendon/downloads/Firefox\ Setup\ 2.0.0.4.exe
```

Also make sure that filename is correct. The Firefox Setup may be named something different for you than it was for the guy who wrote the HOWTO, ie: a newer version than what he used as an example.

---

### Post by shrift on 2007-07-09
One more thing to help you find the exact location of the file. If you look in the FF download manager in linux, you can right click the file you downloaded, the click properties. It has a box in there to show the full path name of the file. so where it says something like: ```
 file:///home/brendon/Desktop/Firefox Setup.exe
``` that should tell you exactly where you downloaded it, in case there was any confusion left. Just remember to tab complete it when entering it into the CLI, because you can't use spaces in the command line. Or you can simply rename the file so that it doesn't have any spaces before trying to execute it.

---

### Post by zabien1970 on 2007-07-09
Thanks Shrift, that did it, I figured it was something I was missing, 
That's one more thing I've learned, and thanks to everyone else for the help

---

