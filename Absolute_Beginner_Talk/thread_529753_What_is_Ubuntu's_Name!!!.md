---
title: "What is Ubuntu's Name!!!"
date: 2007-08-19
forum: Absolute Beginner Talk
---

### Post by Decatur on 2007-08-19
here which one do I download becuase it does not say Ubuntu is there an official name? 
[http://www.opera.com/download/index.dml?custom=yes](http://www.opera.com/download/index.dml?custom=yes)

---

### Post by Tyke91 on 2007-08-19
depends on what kind of comp you have...

im assuming you want i386

---

### Post by Decatur on 2007-08-19
umm i just made a comp.

---

### Post by Tyke91 on 2007-08-19
altho, i dont know why you're doing it the hard way

just type 

```
sudo apt-get opera
```

---

### Post by moredhel on 2007-08-19
Hint: Always try the repos before the official website ;)

---

### Post by Tyke91 on 2007-08-19
lol, moredhel is right... ubuntu has a gigantic online repository of common programs that it can connect to and download from. 

check the synaptic package manager and the add remove programs list to view what's in the repos first.


(opera is in the repos, sudo apt-get install opera is just the command line way of downloading from the repos)

---

### Post by Decatur on 2007-08-19
what r repos

---

### Post by misfitpierce on 2007-08-19
[http://www.opera.com/download/](http://www.opera.com/download/) just go there and it should detect Ubuntu or you can drop down to Ubuntu and just download

---

### Post by Jimmyfj on 2007-08-19
Repositories are the place where the packet for each release is stored on some mighty big servers

---

### Post by por100pre1 on 2007-08-19
Look at this [page]("http://www.opera.com/download/?platform=linux"). Select Ubuntu and the version number. I think it easier to copy/paste and ENTER this in a terminal:

```
sudo apt-get install opera
```

---

### Post by jgrabham on 2007-08-19
> **Decatur said:**
> what r repos

first - that word is "are"

and second repository's are place where thousands of applications are saved on the internet - you just have to install them straight from there

---

### Post by jgrabham on 2007-08-19
Click on applications in the top left corner, then go accesorys > terminal

a black box with a bit of text will come up - its called a terminal - you can use it to tell the computer to do things copy and paste      > sudo apt-get install opera     into it then press enter then type in your password and press enter again.

---

### Post by eentonig on 2007-08-19
Thank you Wikipedia!!

> Software repository
From Wikipedia, the free encyclopedia
Jump to: navigation, search

A software repository is a storage location from which software packages may be retrieved and installed on a computer. Many software publishers and other organisations maintain servers on the Internet for this purpose, either free of charge or for a subscription fee. Repositories may be solely for particular programs, such as CPAN for the Perl programming language, or for an entire operating system. Operators of such repositories typically provide a package management system, tools intended to search for, install and otherwise manipulate software packages from the repositories. For example, some Linux distributions use Advanced Packaging Tool or yum.

For more info, follow the links in my signature.

---

### Post by Myglaren on 2007-08-19
Uh-Oh!

innamoramento@innamoramento-desktop:~$ sudo apt-get install opera
Password:
Reading package lists... Done
Building dependency tree
Reading state information... Done
Package opera is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package opera has no installation candidate


innamoramento@innamoramento-desktop:~$ sudo apt-get install Opera
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package Opera
innamoramento@innamoramento-desktop:~$

And it all looked so easy - I had forgotten I didn't have Opera on this machine.  Still haven't.  Oh well.

---

### Post by Decatur on 2007-08-19
kk got it its i386

---

### Post by Lord Illidan on 2007-08-19
Do it from Add/Remove in Applications, it is easier that way, as it will automatically enable the commercial repository.

---

### Post by &#1050;&#1085;&#1077;&#1083;&#1077; on 2007-08-19
> **por100pre1 said:**
> I think it easier to copy/paste and ENTER this in a terminal:

```
sudo apt-get install opera
```
I think that he/she has to edit the source list first if he/she wants to install Opera that way. 
So, in order to install Opera, Skype, Real Player, Google Earth, SUN Java Runtime Environment, Acrobat Reader (etc.) that way, do the following:
```
sudo gedit /etc/apt/sources.list
```
Then add this three lines at the end of the file and choose save.
```
## MEDIBUNTU REPOSITORY
deb http://packages.medibuntu.org/ feisty non-free
deb-src http://packages.medibuntu.org/ feisty free non-free
```
Add some keys with:
```
cd /tmp
```
```
wget http://packages.medibuntu.org/medibuntu-key.gpg
```
```
sudo apt-key add medibuntu-key.gpg
```

Now you should be able to install Opera with the command:
```
sudo apt-get install opera
```

---

### Post by Myglaren on 2007-08-19
It's rather odd - doesn't appear to be in the repositories either?

---

### Post by Tyke91 on 2007-08-19
you need the universal repositories to be open... refer to the above post :)

---

