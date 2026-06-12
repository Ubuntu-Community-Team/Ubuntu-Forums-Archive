---
title: "I want to learn how to install non-synaptic programs..."
date: 2008-02-28
forum: Absolute Beginner Talk
---

### Post by OZFive on 2008-02-28
Hello you Ubuntu folks...

I am learning more and more every day but I am kind of stumped when it comes to installing somethin that is not offered in Synapitc (oh that program is so damn cool).  For example I wanted to play Assault Cube and found out i is not in the repositories, so I went to the website and downloaded the files.  The folder is extracted to my desktop now and I have looked around and tried to use the ~/configure (not sure that is the real command, it is early and this was late last night).  But every time I ran it in the terminal I got "No such file or directory exists".  **So what I would like to know, can someone give me a step by step instructions so that I might install things not in Synaptic**?  Thanks!

---

### Post by uberlube on 2008-02-28
Here you go, hope this covers everything you need:

[http://monkeyblog.org/ubuntu/installing.html](http://monkeyblog.org/ubuntu/installing.html)

---

### Post by spydon on 2008-02-28
try this:


```
./configure
make
sudo make install
```

if there is a file called "bootstrap" in the directory you can start with ```
sh bootstrap
```

Sometimes you can download ubuntu** .deb** packages and you just have to double click to install them.

---

### Post by spamzilla on 2008-02-28
Get familiar with the terminal. When having to compile programs, useful commands are:

> cd /path/to/file         
For example: cd /home/user/Desktop/filename

This will change the terminal directory to /home/user/Desktop/filename. From here you can then compile the program by running these commands:

> ./configure
make
sudo make install

If all goes well, the program should be compiled and installed.

---

### Post by hyper_ch on 2008-02-28
and before you try to configure and compile from source, you'll have to get compiler and stuff:

```

sudo apt-get instal build-essential

```

---

### Post by OZFive on 2008-02-28
okay so far this is what I got... it seems not to be working though....

---

### Post by bazzawill on 2008-02-28
According to [http://gaming.gwos.org/doku.php/guides:32bit:assultcube]("http://gaming.gwos.org/doku.php/guides:32bit:assultcube")
assult cube does not need to be configured, UGA is a good place to hit to find guides to install games for installing from source generally there will be a file included called INSTALL which should give you the commands needed for the particular code also it should tell you what packages are needed, because unlike synaptic packages dependancies are not handled by source code

---

### Post by Scut_Farkus on 2008-02-28
> **OZFive said:**
> okay so far this is what I got... it seems not to be working though....

Hi OZFive.  I'm new, too.  I looked at your screen shot and it looks like you simply spelled "install" incorrectly.  I only see one "L" at the end of the command.  

Could it be that simple?  :)

I hope this helps.

Your question was GREAT and I am book marking this page because I've wanted to do this, too. (Install outside of synaptic).

---

### Post by markbusu on 2008-02-28
Hi

Ok, starting off, 'install' is with a double 'l' so that might be the reason why apt-get was failing to install your package.

Secondly, can you ensure that there is a configure file in the folder you are trying to run the ./configure Command?

Finally, dont leave a space when you try to run configure, therefore like this 

'./configure'

and not like this

' ./configure'

I just started on this too... but you get used to it m8!

Good Luck!

---

### Post by hyper_ch on 2008-02-28
well, it's 

```

install

```

---

### Post by djbsteart1 on 2008-02-28
if the file ends in .bin, (this can be done with some other packages aswell, some one correct me if you need an installer) go to properties and select permissions, then make executable. then just double click....... google earth is like this.

---

### Post by OZFive on 2008-02-28
> **hyper_ch said:**
> and before you try to configure and compile from source, you'll have to get compiler and stuff:

```

sudo apt-get instal build-essential

```

Got that!

Still cannot configure, probably becasue there is not a configure file :(

he is what was included in the DL...

---

### Post by oldos2er on 2008-02-28
Have you read the README.xml and startup.xml files in the docs directory? I'd probably start there. Also post the output of ls when you're in ~/Desktop/AssaultCube

---

### Post by octopuskevin on 2008-02-29
> **OZFive said:**
> Got that!

Still cannot configure, probably becasue there is not a configure file :(

he is what was included in the DL...


Hey buddy, here are the deb files for assault cube, hosting thanks to the glorious getdeb.net :D

[http://getdeb.net/app/AssaultCube](http://getdeb.net/app/AssaultCube)

just select your distro version [feisty or gusty 32 or 64], download the assaultcube and assaultcube-data files and just install like any normal deb [double click and install] you may need to install the -data before the assaultcube deb or vise-versa... dependencies will also be downloaded for ya.

anyways hope that helps

p.s. when you install a .deb file and later want to remove it, you can do it either do it via synaptic [it's automatically added] or if your feeling comfortable with the command line, a simple ```
sudo aptitude remove assaultcube
``` will do the trick. 

:D

- Kevin

p.s.s. in the readme it states to run in linux execute the assaultcube.sh file... so for that, just run the command: ```
sh assaultcube.sh
```
... you can also right click on the assaultcube.sh file, go to properties, and under permissions check the execute box. then you can just double click and run...

---

