---
title: "Installing programs"
date: 2005-09-28
forum: Absolute Beginner Talk
---

### Post by whiterabbit on 2005-09-28
:) Sorry... All sorted. Lost my head.

---

### Post by matthewv on 2005-09-28
Installing programs in linux can be easier than windows. It's easier in Breezy than Hoary. Breezy uses a special add applications dialogue to give access to hundreds of new applications. This program allows you to just choose programs to install according to category: click install and the program just downloads and installs automatically. Hoary includes the synaptic package management. Compiling a program shouldn't be necessary unless you wan't to try some obscure, new program. I have never had to compile a program, and I've been solely on Ubuntu for a few months.

---

### Post by whiterabbit on 2005-09-28
I've been trying to install specific programs from sites like Freshmeat etc.  

So the Add Applications updates on a regular basis or do I have to manualy add specific packages?

---

### Post by matthewv on 2005-09-28
If the program isn't in add applications or synaptic then I would search for a binary on the net. If you can't find a binary and only source is supplied then you probably have little choice but compiling. I'm no authority on that but I think its usually downloading and installing all dependancies and then going to the shell, extracting the source to a folder, navigating to the folder and then running:

```

./configure [set any options on compiling here]
make
sudo make install

```

---

### Post by Emerzen on 2005-09-28
Hello there,

1.) Look for whatever you need in Synaptic 1st...far...far easier.  Make sure you've added the universe, multiverse, and backports (if still Hoary) here's the perpetual link [http://www.ubuntuguide.org/](http://www.ubuntuguide.org/) for that.

2.) If that fails, I find it works better to do an install from source rather than use and (alien) .rpm package or a pure debian package.
     
     Go to Synaptic and install 'build-essential' & 'checkinstall' and any kernel
     headers for your linux-kernel.
     
     Download your (source) package (for the right architecture & for Debian   builds) to home directory desktop.

     Right-click package and choose "extract here."  You should get a folder 
     w/ the same name as original package minus any .tar.gz

     Browse inside folder for a readme file or install file...open it and see what 
     instructions it provides.  Pay particular for any dependencies mentioned, 
     and install any from Synaptic (if possible) or this procedure if from source.
     If there's an install.sh file in there, you often can simply just run this
     (more on that later).  Often the program's homepage on freshmeat will tell 
     about the dependencies.  If they are all installed, you're ready to start.

     prompt# cd Desktop/name_of_folder

     ./configure

(look for any error messages here or dependencies not met)  If all goes well go to next step.)

     prompt# make

     prompt# sudo checkinstall 

(this last step builds a debian package and installs it, follow the prompts on screen and recommended suggestions).  If all goes well you can now add/remove your program using Synaptic).  If checkinstall complains about anything, it's usually a dependency that's not met and you'll have to meet it.

(If there was an install.sh inside the package, open up the folder and double click it, then choose "run in a terminal."  If all goes well you will have your program installed BUT this will not make a deb package or give you access via synaptic.)

Have fun.

---

### Post by whiterabbit on 2005-09-28
Thank you both very much.  I was actually following these instructions(aren't too different from yours Emerzen).... [http://www.tuxfiles.org/linuxhelp/softinstall.html](http://www.tuxfiles.org/linuxhelp/softinstall.html)

Things actually started to work out after I put in...

```
sudo apt-get install build-essentials
```

Now that I've discovered Synaptic and "add applications", I think Ubuntu is too good to be true.  I'm learning something new everyday so it can't be all bad.  

Thanks guys.

---

### Post by psylvester on 2005-09-28
I tried to install soo many things, This is what I used to get always

root@ubuntu:/home/sylvu # sudo apt-get install sun-j2rel.5
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package sun-j2rel.5
root@ubuntu:/home/sylvu # sudo apt-get install flashplayer-mozilla
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package flashplayer-mozilla
root@ubuntu:/home/sylvu #

I dont know why Im getting this ? Can anyone help. Please try to explain step by step, so that I can understand. Im new to linux.

Regards,
ps

---

### Post by UbuWu on 2005-09-28
[QUOTE=psylvester]
root@ubuntu:/home/sylvu # sudo apt-get install sun-j2rel.5
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package sun-j2rel.5
[/QUOTE]

Because there is no package with that name in the Ubuntu repositories.

> 
root@ubuntu:/home/sylvu # sudo apt-get install flashplayer-mozilla
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package flashplayer-mozilla
root@ubuntu:/home/sylvu #


You have to enable the multiverse section of the repositories to install this one.

See [http://ubuntuguide.org/](http://ubuntuguide.org/) for some more info on both of these...

---

### Post by matthewv on 2005-09-28
I think you need to add extra repositories to your sources.list. Follow the instructions on ubuntuguide.org [here]("http://ubuntuguide.org/#extrarepositories")

---

### Post by whiterabbit on 2005-09-28
Is there an easy way to install video drivers?

EDIT: Nevermind.. I've done it!  Thanks to the Ubuntu help files. :)  I've gotta think before I post from now on.

---

