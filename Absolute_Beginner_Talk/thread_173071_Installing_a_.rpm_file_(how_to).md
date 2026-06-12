---
title: "Installing a .rpm file (how to)"
date: 2006-05-09
forum: Absolute Beginner Talk
---

### Post by LipSkidr on 2006-05-09
I would like to install this program, but it seems that you cannot just double click the file.  I have tried looking for the answer but I am having trouble.

I was going to try the command that I used for updating firefox but thought that could be bad?

So if one were to want to install a .rpm or any file for that matter is there a place one could get the commands?

TIA
LS.

---

### Post by ComplexNumber on 2006-05-09
i'm not surprised you're having trouble :D. ubuntu doesn't use rpm. it uses deb. you can convert it from rpm to deb using a package called alien.

---

### Post by rado_london on 2006-05-09
There is a program called alien. It basically converts rpm to deb file. Do it in terminal:
```
sudo alien package.rpm
```
then you have deb package

---

### Post by Harold P on 2006-05-09
Make sure you install alien, like ComplexNumber said.

```
sudo apt-get install alien
```

---

### Post by xXx 0wn3d xXx on 2006-05-09
[QUOTE=rado_london]There is a program called alien. It basically converts rpm to deb file. Do it in terminal:
```
sudo alien package.rpm
```
then you have deb package[/QUOTE]
But you need to install alien since it is not in Ubuntu by default. Open terminal (Applications > Accessories > Terminal) and copy and paste:

> sudo apt-get install alien

---

### Post by user1397 on 2006-05-09
...and to install the package just do 
```
sudo dpkg -i <deb_file>.deb
```

---

### Post by LipSkidr on 2006-05-09
I would like to thank every one for the advice and help.  It all worked out fine except :confused: Where would I find my progam I installed?  I found it in something called Synaptic and it says installed.

erik1397 I noticed in your how to sig to find an installed file and tried to do the second option but just get the error :  

(note: I also did the first part sudo apt-get update as explained first)


richard@home-96u1az6cer:~/Desktop$ sudo apt-get install xfce4-appfinder
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package xfce4-appfinder
richard@home-96u1az6cer:~/Desktop$

LS

---

### Post by ComplexNumber on 2006-05-09
> I found it in something called Synaptic and it says installed. just go onto the command line and use it there. if you type in 'which alien', it should say its installed in (probably) /usr/local/bin or /usr/bin. but there's an environmental variable called PATH, and this variable holds the paths to where linux looks when its looking for where to execute programs. if you type in 'echo $PATH', this will give the lists of paths (echo just means 'print out' and the $ means 'the value of'). one of them will be /usr/bin, so when you type in the name of the program(in this case, alien), it will look through all those paths and see if it can find the program there. in this case, it will find it at /usr/bin/alien.


firstly, to see how to use the program, type in 'alien --help'. that should give the syntax of the program and the options that you can use. i haven't got alien installed at the moment and i've only used it a few times, so i can't tell you how to use it, unfortunately. maybe someone else can.

---

### Post by LipSkidr on 2006-05-09
Very usefull info ComplexNumber.  I found to files that are for my program but there text files?  I must have done something wrong.  My eyes are burning from all the reading.  I will figure this out eventually :).

ok I was able to resolve the issue.  With lots of help of course :)

---

### Post by ComplexNumber on 2006-05-09
[this]("http://www.linuxnewbieguide.org/") may be able to help. i found it at digg and i think its quite a wonderful resource for the newbie.



> I found to files that are for my program but there text files?
what are those text files called?

---

### Post by LipSkidr on 2006-05-09
one of the files had "XX" and the other had "XXX" ?

---

### Post by ComplexNumber on 2006-05-09
noticed that you've edited your post to let us all know that you've resolved the issue. thats good :). 
as a newbie,  you didn't really need to know about the PATHs and stuff that i explained about before. but i think it helps to know how things work under the hood when they're explained well and explained in simple-ish terms

---

### Post by LipSkidr on 2006-05-09
ComplexNumber: Wow I love this site you posted, I did not realise Linux has been around for so long or had the force it has of users.  This will def be a very good and helpful read.

---

### Post by ComplexNumber on 2006-05-09
[quote=LipSkidr]ComplexNumber: Wow I love this site you posted, I did not realise Linux has been around for so long or had the force it has of users.  This will def be a very good and helpful read.[/quote]
well, if it can help you, me, and many others about linux more,  its a worthwhile read :).

---

