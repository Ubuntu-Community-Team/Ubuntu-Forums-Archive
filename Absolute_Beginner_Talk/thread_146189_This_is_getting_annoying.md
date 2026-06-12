---
title: "This is getting annoying"
date: 2006-03-17
forum: Absolute Beginner Talk
---

### Post by Linux-gamer on 2006-03-17
I dont even know if I have wine, but I guess I do since I found it in usr doc shared. But How do I start it? When I click on it there is nothing there that looks like it could. Im just trying to install steam to get a game going and Ill be happy. Is their like a automatix that can do it for me :p

And when ppl say run wine blah blah does that mean  go to the terminal and start it from there? Like when I downloaded tohoma font I cant go in the file system. isnt that like the c drive in windows? I am too used to windows to figure out how to install something after it appears on my desktop hehe. And i cant even install the new update for wine it keeps giving me an error. I just need detailed steps on what to do and where to extract the files. I already tried several websites but its not getting in me. I guess linux isnt for me lol

---

### Post by mustang on 2006-03-17
Well, lets first check for sure if you have wine:

Type the following in the terminal

```
wine --version
```

Does it return a version number? If so, proceed. If not, [http://www.winehq.com/site/download-deb](http://www.winehq.com/site/download-deb) or Automatix---I reccommend the former option since Synaptic's updater will nicely tell you whenever there is a new version of wine out.

When you want to run a program (.exe) using wine, you can either

1)Open the terminal and use

```
wine <file>.exe
```

2)You can use nautilus, right click on the file and select run with wine. 

So you in your case (assuming this is possible, I actually don't know if you can install and run steam via wine), just do 

```
wine SteamInstall.exe
```

after you downloaded it from the steam website. Let us know how it goes and if you have more questions.

---

### Post by Linux-gamer on 2006-03-17
I do have a version of wine. When I typed wine steaminstall.exe I got the following:

wine: could not load L"c:\\windows\\system32\\steaminstall.exe": Module not found

---

### Post by YokoZar on 2006-03-17
[QUOTE=Linux-gamer]I do have a version of wine. When I typed wine steaminstall.exe I got the following:

wine: could not load L"c:\\windows\\system32\\steaminstall.exe": Module not found[/QUOTE]
Navigate to the folder where the steaminstall.exe file is and try again.

Alternatively, you can find it in nautilus and right click -> open with Wine

---

### Post by Linux-gamer on 2006-03-17
when i open steaminstall.exe and once its done copying steam.exe to the c drive 
it says the following: 

Steam.exe(main exception): Win32 StructuredException at 7D43b127 : Attempt to read from virtual address 0 without appropriate access rights.

Also When I tried to put the Tahoma.ttf file in x11 folder it said I do not have permission to write to this folder. But I am the only person on who uses this computer how can I not be admin?

---

### Post by hscottyh on 2006-03-17
Things do get a little frustrating when you having to learn bunch at once....

I think I've seen this before. First copy the file to your wine directory and run it from there. It's a hidden the directory and is .wine in your home directory, you may want to create a link to this directory.

If that doesn't work for you, I would suggest installing winetools. It makes it much easier to get wine configured.... You can get it from the address below:
[http://www.von-thadden.de/Joachim/WineTools/](http://www.von-thadden.de/Joachim/WineTools/)

Some of the wine developers don't like winetools... see the articles at winehq to find out why, but it can make getting it configured and working much easier.

---

### Post by Linux-gamer on 2006-03-17
I tried to click and drag the steaminstall.exe to the wine folder but it again said I do not have permission.

Also after I download winetools where do I extract it?

---

### Post by Madpilot on 2006-03-17
[QUOTE=Linux-gamer]Also When I tried to put the Tahoma.ttf file in x11 folder it said I do not have permission to write to this folder. But I am the only person on who uses this computer how can I not be admin?[/QUOTE]

I've never used Wine, so I'll leave that to other people, but installing new fonts in Ubuntu is very easy...

Open Nautilus (the file manager), create a new directory in your home directory called ".fonts" - note the period on the front of that name, it's important.

Press Ctrl+H to show hidden files (anything with a dot/period in front of it is hidden by default) and drop any TTF or other font files you want to use into .fonts. They should be autodetected by every application in your system.

Ctrl+H will turn display of your hidden settings files off again.

---

### Post by Jason_25 on 2006-03-17
First, sticky the terminal somewhere where you can easily launch it.  Then launch it, and type
```

sudo -s

```
then
```

nautilus

```
Then you will have nautilus opened as root so that you may change files as needed.

---

### Post by hscottyh on 2006-03-17
I extracted it in my home folder then goto to that folder and do:

sudo install
after it installs then:
winetools

do a base install and your good to go. You can install fonts with it too.

as far as the permission thing.... Anyone?

---

### Post by Linux-gamer on 2006-03-17
umm wow this is newbie but Nautilus is in my filesystem right? When I open in it I am just looking at its contents, my question is how do I make nautilus start?

---

### Post by Linux-gamer on 2006-03-17
[QUOTE=Jason_25]First, sticky the terminal somewhere where you can easily launch it.  Then launch it, and type
```

sudo -s

```
then
```

nautilus

```
Then you will have nautilus opened as root so that you may change files as needed.[/QUOTE]
I did that It did open the root - file browser but I did get this in terminal dont know if its bad or not:

talmadge@ubuntu:~$ sudo -s
root@ubuntu:~# nautilus

(nautilus:12403): Eel-CRITICAL **: wrap_table_get_num_fitting: assert ion `max_child_size > 0' failed

(nautilus:12403): Eel-CRITICAL **: wrap_table_get_num_fitting: assert ion `max_child_size > 0' failed

---

### Post by Linux-gamer on 2006-03-17
Well I do thanks for everyone help, mabey Its made not to be hehe

thanks for the suggestions I guess Ill keep on trying sorry if I wasted yalls time trying to help me

oh and I got this also man I just suck at linux haha. And to think I am trying to get my A+. Mabey I should of tryed to get a C++ :p

---

### Post by Jason_25 on 2006-03-17
Those errors are nothing to worry about.

---

### Post by katarot on 2006-03-18
hey would wine work on the driver.exe

---

