---
title: "Install new package"
date: 2006-09-11
forum: Absolute Beginner Talk
---

### Post by MiXor on 2006-09-11
Hi there!

I do not know how to install a new package (such as libxml-perl)... Could anyone help me with that? Do I have to extract the packages in a particular directory or can I do that anywhere? If so how can I change the PATH?
Thanxx :KS 

Aline

---

### Post by Najand on 2006-09-11
> **MiXor said:**
> Hi there!

I do not know how to install a new package (such as libxml-perl)... Could anyone help me with that? Do I have to extract the packages in a particular directory or can I do that anywhere? If so how can I change the PATH?
Thanxx :KS 

Aline

Use the command:
```
$ sudo apt-get install <PackageName>
```
from terminal. It can be run from anywhere in your filesystem.

There is a similar command, too:
```
$ sudo aptitude install <PackageName>
```
with a little difference in installing files. (The way they deal with dependencies)

If you are looking for a package you don't know its name aptitude can help too:
```
$ sudo aptitude search <KeyWord>
```

If you are using gnome, another package manager called synaptic can be found at:
> system -> Administration -> synaptic package manager

Synaptic is also a complete package manager with all search, proxy settings, ... facilities.

---

### Post by MiXor on 2006-09-11
I downloaded all the packages I needed, and I get the following error : 
E: Could not get lock /var/lib/dpkg/lock - ope, (ll Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg), is another process using it?
What does that mean??

---

### Post by Najand on 2006-09-11
you are trying to use any of packages while at least one other package manager is active. It is neccessory to use just one package manager at a time... for example you cannot use synaptic while using apt-get. Try closing unneccessory package managers and try again.

---

### Post by MiXor on 2006-09-11
ok, that solved the error message problem. Now comes another problem : 
E: Couldn't find package <name of package>
Although I have already downloaded and extracted the package
Help!

---

### Post by Najand on 2006-09-11
Wow, is it a downloaded application... What is its type?

---

### Post by MiXor on 2006-09-11
Well, I dont know what a type of package is... (blushing) I got the packages zipped from ubuntu.packages and unzipped them. How do you install packages?

---

### Post by Najand on 2006-09-11
Was is a *.deb file? If so there is no need to extract it... Just use the command:
```
 sudo dpkg -iv <filename>.deb
```

---

### Post by MiXor on 2006-09-11
well, it is not a single file... When I extracted the stuff from the .tar.gz I downloaded, a whole directory full of files and more directories appeared. It is the only thing I can find on ubuntu.packages... To get an example you can have a look at libid3tag_0.15.lb.orig.tar.tar (which is one of the packages I would like to install)

BTW, thank you for helping me :-D The Ubuntu community is a very friendly bunch of people that welcome newbies like myself very well! =)

---

### Post by Najand on 2006-09-11
Oh! You are just looking for "ID3 tag reading library from the MAD project"? If it is the only thing you are looking for, just download ***libid3tag0_0.15.1b-8_i386.deb*** (libid3tag0 with i386 architecture.) from [Ubuntu packages]("http://packages.ubuntulinux.org/dapper/libs/libid3tag0") And then use the dpkg command I wrote above.
```
$ sudo dpkg -iv libid3tag0_0.15.1b-8_i386.deb
```

---

### Post by MiXor on 2006-09-11
Ultimate noobie question : what is the "architecture" they talk about? How can I know the package I can use?

---

### Post by Najand on 2006-09-11
Unlink Microsoft Windows or Mac OS X or even Unix that can be installed on a particular type of computers, Linux can be installed on a variety of different computers with intel 8086 /intel pentium /Machintosh Power PC/ AMD Athlon&#8482; 64 processor/ et cetra.... For example I have Linux installed on a computer with Pentium 4 processor (which is a i386 architecture) and I have it installed on my Apple Macintosh iBook G4 (which is a ppc architecture), too... They are both ubuntu, but with differect architecture and I need to find packages that match the architecture of the computer I am using... So, if you are using a compute with intel pentium on it use i386.

---

### Post by MiXor on 2006-09-11
my Ubuntu doesn't seem to know the option 'v'
What is it? Is it necessary? (I know a little bit of shell, and I'm willing to learn, so feel free to explain! :D )

---

### Post by Perfect Storm on 2006-09-11
My advise is you set up your sourcelist first:
```
sudo nano /etc/apt/sources.list
```

Now uncomment the lines that starts with one # (by removing the the #).
Also add:
```

# Ubuntu community supported packages (packages, GPG key: 437D05B5)
deb http://archive.ubuntu.com/ubuntu dapper universe multiverse
deb http://archive.ubuntu.com/ubuntu dapper-updates universe multiverse
deb http://security.ubuntu.com/ubuntu dapper-security universe multiverse


## Ubuntu community supported packages (sources, GPG key: 437D05B5)
deb-src http://archive.ubuntu.com/ubuntu dapper universe multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper-updates universe multiverse
deb-src http://security.ubuntu.com/ubuntu dapper-security universe multiverse

## Cipherfunk multimedia packages (packages, GPG key: 33BAC1B3)
deb ftp://cipherfunk.org/pub/packages/ubuntu/ dapper main

## Cipherfunk multimedia packages (sources, GPG key: 33BAC1B3)
deb-src ftp://cipherfunk.org/pub/packages/ubuntu dapper main

## Penguin Liberation Front (packages)
deb ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/ dapper free non-free

## Penguin Liberation Front (sources)
deb-src ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/ dapper free non-free

```

Save and exit <ctrl> +<o> | <ctrl> + <x>

Open the terminal and write:
```
sudo apt-get update
sudo apt-get install libid3tag0
```

Furthermore you can now via Synaptic package manager find every package with ease and quickly install them.(System tab ---> Adminstration ---> Synaptic)

---

### Post by MiXor on 2006-09-11
ok, I guess that will be smashing when I connect my ubuntu to the internet -installed ubuntu yesterday and enquiring from a friend's computer!- but in the meantime, is there another solution?
I also tried the command, just for kicks, and I got the following error message : 
The method driver usr/lib/apt/methods/frp could not be found
this is gibberish to me.. what does that mean?

---

### Post by Najand on 2006-09-11
Just do it without v option, i.e.
```
$ sudo dpkg -i libid3tag0_0.15.1b-8_i386.deb
```

---

