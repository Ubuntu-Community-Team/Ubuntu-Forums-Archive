---
title: "Help what to do after downloading a program?"
date: 2007-01-10
forum: Absolute Beginner Talk
---

### Post by calypsogal on 2007-01-10
I am sorry to be so NEW at this, but i have finally found a program that i want to use called manslide. i went to their website, downloaded it to my desktop, then  extracted it to my tpm directory. Now what?

the file i downloaded is called manslide.tar.gz

how do i get it in the system? i'm a windows person who rarely add programs there so ...i can't remember what to do at all.

thx

---

### Post by punx45 on 2007-01-10
good first step is usually to go to the directory that the tar file extracted to and look for a readme or installation instruction file.   you probably downloaded a source code file and will have to compile it which follows a general process, but may include some idosyncracies for the particular software.

check out the "installing from source" section of [this guide]("http://www.psychocats.net/ubuntu/installingsoftware").

also, in the future, to avoid compiling sources, check the synaptic package manager for the program, and then check the program's website for a .deb (prefrence) or .rpm (may require more work than .deb but usually better than compiling source)

---

### Post by gentlemanmasher on 2007-01-10
extract the tar 
cd to the file cd filename
./configure
make
sudo make install

---

### Post by r4ik on 2007-01-10
Here is another guide,

[http://monkeyblog.org/ubuntu/installing.html](http://monkeyblog.org/ubuntu/installing.html)

Good luck !

---

### Post by calypsogal on 2007-01-10
> **gentlemanmasher said:**
> extract the tar 
cd to the file cd filename
./configure
make
sudo make install

I'm sorry but what does this mean? do i type this somewhere? I have this file and i want to install it. Do i iuse the terminal? is cd mean copy disk?

Im still at a loss. Can't connect with the 3rd reply's site, will try later.

gawd this reqires a lot of persistance and patience!
](*,)

---

### Post by ComplexNumber on 2007-01-10
> **calypsogal said:**
> I'm sorry but what does this mean? do i type this somewhere? I have this file and i want to install it. Do i iuse the terminal? is cd mean copy disk?

Im still at a loss. Can't connect with the 3rd reply's site, will try later.

gawd this reqires a lot of persistance and patience!
](*,)
you'll find the terminal in main menu -> accessories -> terminal. after you have unpacked the tarball(ie manslide.tar.gz) by right clicking on it and selecting 'extract here'. now fire up the terminal and go INTO where the tarball has unpacked (eg /home/<your-username>/manslide). use the "cd" command to go to that directory.
then type in "./configure"(without the quotes). 
then, once its finished,  type in "make". 
again, when until its finished begfore you type in " sudo make install".

if possible, can you give us a screenshot of the contents of the unpacked manslide? for example, something like the screenshot below. then we can see exactly what needs to be done for you to compile manslide.

---

### Post by calypsogal on 2007-01-10
> **ComplexNumber said:**
> you'll find the terminal in main menu -> accessories -> terminal. after you have unpacked the tarball(ie manslide.tar.gz) by right clicking on it and selecting 'extract here'. now fire up the terminal and go INTO where the tarball has unpacked (eg /home/<your-username>/manslide). use the "cd" command to go to that directory.
then type in "./configure"(without the quotes). 
then, once its finished,  type in "make". 
again, when until its finished begfore you type in " sudo make install".

if possible, can you give us a screenshot of the contents of the unpacked manslide? for example, something like the screenshot below. then we can see exactly what needs to be done for you to compile manslide.

thanks for the help, but two small problems still. lol just two for now!

1. how do i make and attach a screenshot?
i bet this will be an intsllation thing on it's own...is it in kpackage?

2. how do i go INTO the place where the extracted files are? I can see the folder titled manslide...but i guess the screen shot would be easiest.

---

### Post by calypsogal on 2007-01-10
further this is what i get in the terminal.

miriam@miriam-desktop:~$ ./configure
bash: ./configure: No such file or directory
miriam@miriam-desktop:~$

it's kinda greek to me....

---

### Post by Sef on 2007-01-10
Read [Psychocat's installing software]("http://www.psychocats.net/ubuntu/installingsoftware").

After extracting you need to go to that directory.  In the terminal, type cd ~/File name of extracted package

Note: after 3 or 4 letters press tab and that should bring up the rest of the file name.

---

### Post by Frank Golden on 2007-01-10
Hi, calypsogal
   I downloaded the program you are interested in but since I am using Gnome and this is a KDE
program I didn't dare install it. However I did extract the files and took a screenshot for you. It is attached below.
In gnome there is a menu item (button) to make a screenshot. I don't know about KDE.
I am assuming that you ae using Kubuntu, hence KDE program.



[ATTACH]22720[/ATTACH]

---

### Post by ComplexNumber on 2007-01-10
it looks like manslide is  ready made binary. therefore, it just needs the user to double click the file called '<Manslide' (ie the file directly underneath the directory/folder called Effects).

---

### Post by Frank Golden on 2007-01-10
> **ComplexNumber said:**
> it looks like manslide is  ready made binary. therefore, it just needs the user to double click the file called '<Manslide' (ie the file directly underneath the directory/folder called Effects).
Or if that doesn't work make sure the extracted manslide folder is on the Desktop
and type in the terminal ```
cd ~/Desktop
``` This changes directory (cd) to your Desktop. Then type ```
sudo /manslide/manslide 
```enter and
provide your password at prompt and enter again. This will run the manslide command
as root if that is needed. Try just double clicking it first though.

BTW, the command cd part of the above command means Change Directory.
The ~/ part of the command is an Ubuntu shortcut which means /home/<your user name>
and of course the Desktop is the desktop which is really a sub directory in the /home/<your user name> directory. Note the captial D in Desktop. The command is case sensitive as is almost everything in Linux.

---

### Post by calypsogal on 2007-01-12
Thanks Frank Gloden and all the other ubuntu gang who have given me help on this thread! I've litterally never been on a foum before, and certainly not one to help me how to use my computer...lol I always thought you needed a live 'computer guy' to call.

again much thanks so far.:D 

So it seems i have gnome so i guess this program manslides is not good to open? right frank? 

I'm off to make another thread to look for a program.

Thanks for the tip on the screenshot button. i found it and it is exactly as yours showed. How would i open this if it was safe to do it? 

btw why is it not 'safe' to open a KDE based program? will it crash my system? won't it just refuse to install?

so many questions...so much help!
thx

---

### Post by calypsogal on 2007-01-12
ok that last post was very poorly composed.

i missed the posts about the cd stuff and ~/ stuff and all these lovely codes you are all teaching me when i first responded. So i think i know how to install a program like this one again. Thanks!

in grade 8 I did learn DOS for a simple elective and we wrote a pick a number between 1-10 program...too bad that was in 1980! 

What does a ready made binary mean?

I will wait for advice before tring to install anything.

---

### Post by obsidion on 2007-01-12
> Thanks Frank Gloden and all the other ubuntu gang who have given me help on this thread! I've litterally 
> never been on a foum before, and certainly not one to help me how to use my computer...lol I always >thought you needed a live 'computer guy' to call.

>again much thanks so far.:D 

>So it seems i have gnome so i guess this program manslides is not good to open? right frank? 

  It will cause your system no harm and is hardly unsafe because it is a kde program. It may not run however due to needing some kde libraries that your system probably doesn't have on it. If you do go for it and it won't work, run it from a terminal and the output should let you know what you need. By Frank's unsafe idea, my system must not work because I have kubuntu and run several gnome programs like Gramps, gftp and pan.


>I'm off to make another thread to look for a program.

  Try [www.google.com/linux](www.google.com/linux) first, the linux addition makes all the difference in the world when looking for software. The other hint I can give along those line is don't try linux equivalent of this windows program, instead, decide what you want from a program and use that instead. Eg if you want an mp3 player don't search for winamp on linux or something similar look for mp3 player ubuntu instead for instance.

Thanks for the tip on the screenshot button. i found it and it is exactly as yours showed. How would i open this if it was safe to do it? 
btw why is it not 'safe' to open a KDE based program? will it crash my system? won't it just refuse to install?

  It isn't gnome and kde programs happily live and work together on each others desktops.

---

### Post by Frank Golden on 2007-01-12
> **obsidion said:**
> > Thanks Frank Gloden and all the other ubuntu gang who have given me help on this thread! I've litterally 
> never been on a foum before, and certainly not one to help me how to use my computer...lol I always >thought you needed a live 'computer guy' to call.

>again much thanks so far.:D 

>So it seems i have gnome so i guess this program manslides is not good to open? right frank? 

  It will cause your system no harm and is hardly unsafe because it is a kde program. It may not run however due to needing some kde libraries that your system probably doesn't have on it. If you do go for it and it won't work, run it from a terminal and the output should let you know what you need. By Frank's unsafe idea, my system must not work because I have kubuntu and run several gnome programs like Gramps, gftp and pan.


>I'm off to make another thread to look for a program.


  Try [www.google.com/linux](www.google.com/linux) first, the linux addition makes all the difference in the world when looking for software. The other hint I can give along those line is don't try linux equivalent of this windows program, instead, decide what you want from a program and use that instead. Eg if you want an mp3 player don't search for winamp on linux or something similar look for mp3 player ubuntu instead for instance.

Thanks for the tip on the screenshot button. i found it and it is exactly as yours showed. How would i open this if it was safe to do it? 
btw why is it not 'safe' to open a KDE based program? will it crash my system? won't it just refuse to install?

  It isn't gnome and kde programs happily live and work together on each others desktops.

I guess I really didn't mean unsafe so much as may not run.
I had a problem a while back with instaling the KDE desktop on my machine.
(I am using Ubuntu). So I am gun shy about loading KDE progs on my machine.
Sorry if I misled you. I have no need for this program so I won't be installing it anyway.
Perhaps that is what I should have said any way.:p

---

