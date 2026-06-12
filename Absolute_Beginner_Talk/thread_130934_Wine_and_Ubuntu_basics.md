---
title: "Wine and Ubuntu basics"
date: 2006-02-15
forum: Absolute Beginner Talk
---

### Post by BiggoCharley on 2006-02-15
Does anyone know where I can go on the web to find out about wine basics (getting started) I have tried winehq website and "Franks corner" (i think that's the right name)and many others, but all the info I can find assumes I know something about wine to start with. I know just enough to be dangerous. If I could start in the middle I'd be OK but I need to start at the beginning.  for example "how to install programs into wine? or where do I put the windows programs that I want to run with wine? do I need to create special directories or are they already there after install wine?  etc etc.
Help  will be appreciated.  
Charley:confused:

---

### Post by Mr.X on 2006-02-15
[QUOTE=BiggoCharley]Does anyone know where I can go on the web to find out about wine basics (getting started) I have tried winehq website and "Franks corner" (i think that's the right name)and many others, but all the info I can find assumes I know something about wine to start with. I know just enough to be dangerous. If I could start in the middle I'd be OK but I need to start at the beginning.  for example "how to install programs into wine? or where do I put the windows programs that I want to run with wine? do I need to create special directories or are they already there after install wine?  etc etc.
Help  will be appreciated.  
Charley:confused:[/QUOTE]
Finally! Something i can help out on ;)
I installed WINE no problems at all, and all the info i needed was on the wine site!
[http://winehq.com/site/download-deb](http://winehq.com/site/download-deb) < download instructions
Then load up terminal, and type wine [location of program]

Good luck,
X

---

### Post by BiggoCharley on 2006-02-15
> **Mr.X]Finally! Something i can help out on  said:**
> http://winehq.com/site/download-deb[/url] < download instructions
Then load up terminal, and type wine [location of program]

Good luck,
X

Thanks but i managed to get that far --I was able to download and install --seemingly ok.  But Where I'm stuck is what's next?  Where do (and how do I install the windows programs I want to run?

---

### Post by Zeroangel on 2006-02-15
Thanks for the link. I managed to get WINE up and running by clicking on the .EXE files that I want to open up but I found the following caveats:

WINE AS USER
- I cannot initialize/edit the configuration data using the 'winecfg' command. The changes (including setup of drives) do not show up when I reopen winecfg leading me to believe they are not applied!

WINE AS ROOT (terminal -> gksudo wine path/to/appname.exe)
```
dave@dlinux:~$ sudo wine cleo.exe
Warning: the specified Windows directory L"c:\\windows" is not accessible.
Warning: the specified System directory L"c:\\windows\\system32" is not accessible.
Warning: could not find DOS drive for current working directory '/home/dave', starting in the Windows directory.
wine: cannot open (null)
```

---

### Post by BiggoCharley on 2006-02-16
[QUOTE=Zeroangel]Thanks for the link. I managed to get WINE up and running by clicking on the .EXE files that I want to open .........

Two questions --(I'm still stuck at the beginning)--
where and how did you install the windows programs?

did you have to create a separate dos drive partition?

---

### Post by piedamaro on 2006-02-16
you have a fake windows drive under wine and the good news is that it's just a directory: it should be under /home/yourname/.wine
so you run a windows installer like this:
wine setup.exe
then you install it as a normal windows app. The files will be copied under ~/.wine

You can even associate your exe files with wine and launch them with a double click, but it isn't a great idea.
You can run windws viruii too, but they don't work well under linux :D

---

### Post by BiggoCharley on 2006-02-17
[QUOTE=piedamaro]you have a fake windows drive under wine and the good news is that it's just a directory: it should be under /home/yourname/.wine
so you run a windows installer like this:
wine setup.exe
then you install it as a normal windows app. The files will be copied under ~/.wine

You can even associate your exe files with wine and launch them with a double click, but it isn't a great idea.
You can run windws viruii too, but they don't work well under linux :D[/QUOTE]

Thanks very much for your help -- went like a charm!!
That's just what i needed to get me off dead center.  
Charley

---

### Post by BiggoCharley on 2006-02-17
[QUOTE=BiggoCharley]Thanks very much for your help -- went like a charm!!
That's just what i needed to get me off dead center.  
Charley[/QUOTE]

I installed Paint Shop Pro (the install seemed to go ok but when i tried to find the program .exe file I wasn't able to open the directory "Program Files".

Here's what happened:
charley@ubuntu:~$ cd /home/charley/.wine/drive_c
[email]charley@ubuntu:~/.wine[/email]/drive_c$ cd Program Files
bash: cd: Program: No such file or directory

so I did this:
[email]charley@ubuntu:~/.wine[/email]/drive_c$ ls
My Documents  Program Files  windows

Am I doing something wrong syntax wise? I tried as shown above plus I tried all lower case etc all with the same results.

I also tried the following:
charley@ubuntu:~$ cd /home/charley/.wine/drive_c/Program Files
bash: cd: /home/charley/.wine/drive_c/Program: No such file or directory
charley@ubuntu:~$

I'm stuck aagain!!:confused:

---

### Post by %hMa@?b&lt;C on 2006-02-17
when there is a drive with a space, youneed to have the whole thing in quotes.
like 
'home/user/.wine/fake_c/Program Files'

or if it is easier for you just look for the file in nautalis, go to places>home.
then press CONTROL+H to view hidden.  At the very bottom should be .wine from there i assume that you can find the directory. then when you find the exe to run PaintShop Pro, right click on it and you go to properties go to opens with then click add then add a custom command.  in the bar simply type wine. Now you can open it by double clicking

---

