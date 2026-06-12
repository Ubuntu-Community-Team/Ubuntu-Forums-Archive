---
title: "Right i've downloaded the software i want...further help is required pls."
date: 2006-06-04
forum: Absolute Beginner Talk
---

### Post by gsingh on 2006-06-04
I've downloaded gnormalize-0.49, extracted.  When i went to synaptic PM, i cant find the folder i want to install- am i doing something wrong?

---

### Post by kane77 on 2006-06-04
is it a .deb file or a source code??

---

### Post by christhemonkey on 2006-06-04
If you downloaded a .deb file, do not extract it.

type into a terminal:
```
sudo dpkg -i /wherever/your/file/is/file.deb 
```

If any errors, note them and report them here.

If your using Dapper, you can just double click on the .deb file and it should open in Gdebi for you to install.

---

### Post by gsingh on 2006-06-04
.deb file is a bit beyond me - sorry for sounded stupid!!   the file i downloaded is gnormalize-0.49.tar.gz - i doubt this is .deb?  Is that short for debian?

---

### Post by christhemonkey on 2006-06-04
You may want to [read]("http://www.beginningubuntu.com/software_17.html") this guide.

Basically, extract, ./configure and sudo make install.

---

### Post by gsingh on 2006-06-04
Thanks for the quick replies, i've read the basics, but it seems like im missing something.  i've done the following:
gs63897@gs63897-desktop:~$ sudo apt-get install gnormalize
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package gnormalize
gs63897@gs63897-desktop:~$

i've extracted the package to the desktop - but its not finding the package.


Cheers.

---

### Post by kane77 on 2006-06-04
so basicly first you need to install build-essential so "sudo apt-get install build-essential" 
then you need to follow the readme that's found in your program as you untar it (" tar zxvf file.tar.gz") as every program is different, but basicaly christhemonkey is right "./configure" "sudo make install"
and yes deb most likely stand for debian...

---

### Post by gsingh on 2006-06-04
i've done the build-essential.  this is what is says in the readme file:

Execute the bash script commands:
                           tar zxvf gnormalize-0.49.tar.gz
			   cd gnormalize-0.49/                           
			   ./install
as root.

So i've pasted the below in terminal:
 tar zxvf gnormalize-0.49.tar.gz
			   cd gnormalize-0.49/                           
			   ./install
as root.

But now stuck - not sure what to do from here.  what is ./configure?

---

### Post by kane77 on 2006-06-04
if it's stated to do something as root you need to log in as a root or use "sudo" before the command so in your case it'd look something like this...
"sudo ./install" (in the directory where you extracted the tar  ( gnormalize-0.49/ )

this should install the program... however this does not create a shortcut in the menu and the only way to run the program is to type its executable... (I'd guess  "gnormalize" in your case...) but using Applications menu editor you can add a new entry into any category that's fit... Choose any name you'd like and as a command use the executable ("gnormalize")

---

### Post by uzi09 on 2006-06-04
i'd just download the rpm, convert it to deb using 'alien' and run it -- using .deb files is a LOT cleaner than compiling from source and much easier to uninstall too. here are the steps:

download file:
[http://prdownloads.sourceforge.net/gnormalize/gnormalize-0.49-1.noarch.rpm?download](http://prdownloads.sourceforge.net/gnormalize/gnormalize-0.49-1.noarch.rpm?download)

install alien using synaptic (or thru terminal, type this)
```

sudo aptitude install alien

```

then convert rpm to deb file:
```

alien gnormalize*.rpm

```

then install using dpkg (must be root)
```

sudo dpkg -i gnormalize*.deb

```

run it!
```

gnormalize

```
(ps, i'm not sure if that's the name, try pressing tab after gnormalize to have auto-complete complete it properly and then hit enter :D)

---

