---
title: "[SOLVED] X11 Installation"
date: 2008-02-23
forum: Absolute Beginner Talk
---

### Post by PostScript on 2008-02-23
Hi!

My name is Phillip, and I just installed Ubuntu on my computer. I was suggested to use Conky, a program for rendering system variables on my desktop, so I downloaded the program's tar file and unzipped it, then ran './configure'.

./configure returns an error which says that X11 is not installed. I have googled X11 and I get an FTP download site, but there are hundreds of files on the site, all in the X11 folder. Do I have to download all of the files to get X11, or is there only one specific file I need?

Thanks alot!

---

### Post by SOULRiDER on 2008-02-23
Oh man, youre doing it the hard way! Youc an install applications in a very very very simple way here. Check this out
[https://help.ubuntu.com/community/SoftwareManagement](https://help.ubuntu.com/community/SoftwareManagement)

And once you get conky installed juts go here to get some scripts:
[http://ubuntuforums.org/showthread.php?t=205865](http://ubuntuforums.org/showthread.php?t=205865)

If you have any questions dont be afraid to ask!

---

### Post by PmDematagoda on 2008-02-23
You can install Conky using the repositories using:-
```
sudo apt-get install conky
```
Inatalling conky using this way means that the dependencies are automatically taken care of and is installed faster.

---

### Post by PostScript on 2008-02-23
[COLOR=Black]Thank you for your replies! That was quick.[/COLOR]

> **SOULRiDER said:**
> Oh man, youre doing it the hard way! Youc an install applications in a very very very simple way here. Check this out
[https://help.ubuntu.com/community/SoftwareManagement](https://help.ubuntu.com/community/SoftwareManagement)

And once you get conky installed juts go here to get some scripts:
[http://ubuntuforums.org/showthread.php?t=205865](http://ubuntuforums.org/showthread.php?t=205865)

If you have any questions dont be afraid to ask!
[COLOR=Black]Wow, thanks! So... I tried using the add/remove program, but when I ran a search for the word 'conky' in the database, it returned no results.[/COLOR]


> **PmDematagoda said:**
> You can install Conky using the repositories using:-
```
sudo apt-get install conky
```Inatalling conky using this way means that the dependencies are automatically taken care of and is installed faster.
[COLOR=Black]I tried that, and for any query I use with apt-get, it returns "Couldn't find package <search query>". Am I doing something wrong?


** Thanks again!**

[/COLOR]

---

### Post by SOULRiDER on 2008-02-23
Launch Synaptic from the System menu and try looking for conky with it. I dont see why that command couldnt install conky, try with this one
```
sudo aptitude install conky
```

---

### Post by PostScript on 2008-02-23
[COLOR=Black]Nope. Couldn't find anything in the Synaptic either. Here, let me see if returning what I got from my Terminal helps:
```
phillip@PhilMwu:~$ sudo aptitude install conky
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
Couldn't find any package whose name or description matched "conky"
The following packages have been automatically kept back:
  linux-restricted-modules-common 
The following packages have been kept back:
  <long list of packages>
0 packages upgraded, 0 newly installed, 0 to remove and 186 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      

```
[/COLOR]

---

### Post by PostScript on 2008-02-23
[COLOR=Black]Hm. I ran 'sudo apt-get install conky' and it worked. I really appreciate you guys taking the time to help me, thanks alot![/COLOR]

---

### Post by SOULRiDER on 2008-02-23
Im glad we could help :)

---

