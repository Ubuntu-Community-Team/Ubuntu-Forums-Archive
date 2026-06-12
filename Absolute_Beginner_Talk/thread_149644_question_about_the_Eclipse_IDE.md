---
title: "question about the Eclipse IDE"
date: 2006-03-24
forum: Absolute Beginner Talk
---

### Post by Amarantin on 2006-03-24
ok so i'm new to Linux (made the transfer yesterday and am content)

and i want to program something in Java 

problem is i need to get that eclipse-jdt plugin wich i can't seem to get through the use of sudo apt-get (if i am on a good way to getting it through this line please do tell)

the line i entered was:

sudo apt-get install eclipse-jdt
wich seemed to give an error 

thx in advance

---

### Post by kassetra on 2006-03-24
[quote=Amarantin]ok so i'm new to Linux (made the transfer yesterday and am content)

and i want to program something in Java 

problem is i need to get that eclipse-jdt plugin wich i can't seem to get through the use of sudo apt-get (if i am on a good way to getting it through this line please do tell)

the line i entered was:

sudo apt-get install eclipse-jdt
wich seemed to give an error 

thx in advance[/quote] 
You need to give apt more software repositories to look through.  eclipse-jdt is in Universe.

apt looks at a file called sources.list to see where it should look for software. In order to add the officially unsupported universe, you will need to edit sources.list from the terminal window like this:
```
sudo gedit /etc/apt/sources.list
``` 
Then look for the following lines:
```
## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team

deb http://archive.ubuntu.com/ubuntu breezy universe multiverse
deb-src http://archive.ubuntu.com/ubuntu breezy universe multiverse

``` 
Notice how my two lines that start with "deb" do not have ## or # in front of them? You need to make the same changes to your file, then save it, close it, and then type:
```
sudo apt-get update
``` 
Then you should be able to install eclipse and eclipse-jdt through apt-get install.

---

### Post by Amarantin on 2006-03-24
allright that worked 

thank you very much 

i'm sure i'll have more questions in the future but i'll leave it at this last one for now :p 

how do you know/can you find out wich app is from wich repository because it seems changes will need to be made frequently to get stuff to work here (just my opinion :) )

---

### Post by Jagot on 2006-03-24
I personally leave the multiverse and universe repositories open all the the time.  I have noticed that some peope think this may destabalise the system to an extent, as when the system update runs it will be getting packages from these repositories which are not officially supported.

I haven't had any stability issues myself.

If you leave the repositories active all the time then you will be able to find the software you need from whichever one it's on, and if you are concerned with the stability issues then you can always close the repositories when you do a system update/upgrade.

---

### Post by Amarantin on 2006-03-24
uhm about the "sudo gedit" comand line that you posted above for me to be able to get that eclipse-jdt to work if i edit it in a similar way and use this url "http://amsn.sourceforge.net" by adding it to the file would i be able to easily update my Amsn or would this basically compromise my system stability in a greater extent ? and otherwise i would like to ask how do i get that .deb file for Amsn that i just dl'ed to work ??

---

