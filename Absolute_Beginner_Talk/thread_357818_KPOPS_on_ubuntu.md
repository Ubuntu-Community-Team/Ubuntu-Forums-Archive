---
title: "KPOPS on ubuntu?"
date: 2007-02-10
forum: Absolute Beginner Talk
---

### Post by avatar3 on 2007-02-10
Hey. 

The topic pretty much says it all, im wondering how to get this program working on ubuntu (gnome) as i wouldnt like to install whole KDE. I cant figure this on out.. If someone could do a little "tutorial" :) 

And this is the program we are talking about: 

[http://linux.softpedia.com/get/Utilities/KPOPS-Converter-22322.shtml](http://linux.softpedia.com/get/Utilities/KPOPS-Converter-22322.shtml)

---

### Post by ingo on 2007-02-11
I've got kubuntu running yet have some gnome programmes. Similarly you should be able to have single kde programmes running under gnome. Your next problem though appears to be to make a .deb package out of the tar.gz so that all dependencies will be met automatically. Can't help you there, though...

just came across this to make .deb

./configure
make
sudo checkinstall -D make install

hth

---

### Post by avatar3 on 2007-02-11
Hmm. i didnt really get what you were meaning by that post. Somebody please help me ](*,) ](*,)

---

### Post by ingo on 2007-02-12
You didn't? Let's try again...

You download tar.gz file to a folder of your choice. Then you untar it
> tar zxvf name_of_file
Now you change to the new folder, usually it has the same name as the original tar file, i.e.
> cd name_of_file(without the .tar.gz at the end)
followed by 
> ./configure
and
> make
and 
>  sudo checkinstall -D make install

If everything went according to plan you now have a name_of_your_programme.deb file. If so, you can now 
> sudo dpkg -i name_of_your_programme.deb
and it will try to install - and fail because of unmet dependencies. This is easily dealt with though by
> sudo apt-get install -f

hth

---

### Post by avatar3 on 2007-02-12
have you downloaded the file and tested it yourself to see if that method of yours actually works? :confused: :confused: 

```
simo@simo-desktop:~/Desktop/51672-KPOPS_Converter1.5.tar.gz_FILES$ ./configure
bash: ./configure: No such file or directory
simo@simo-desktop:~/Desktop/51672-KPOPS_Converter1.5.tar.gz_FILES$ 

```

---

### Post by ingo on 2007-02-12
No, I don't want it on my system, but from what you posted it appears you did not untar the file - is that right?

---

### Post by avatar3 on 2007-02-12
yes i did untar it. there is no "configure" file i think. this sounds stupid, but you would happen to have irc / msn so you could direct me into the right direction :guitar:

---

### Post by ingo on 2007-02-12
That is a good idea, but unfortunately I do not have msn... Sorry about that. So you untarred, changed into the directory and you're saying there is no ./configure file? Highly irregular and unusual :)

In that case I cannot help you any further, I'm afraid apart from looking for ready made .deb files on the net.

Good luck!

---

### Post by avatar3 on 2007-02-12
here are the contents of that folder. 

```
simo@simo-desktop:~/Desktop/51672-KPOPS_Converter1.5.tar.gz_FILES$ ls
bin  Installer.kmdr  inst.sh  psptools  README  share

```

---

### Post by 3rdalbum on 2007-02-12
> **ingo said:**
> That is a good idea, but unfortunately I do not have msn... Sorry about that. So you untarred, changed into the directory and you're saying there is no ./configure file? Highly irregular and unusual :)


It's not really so unusual - there are a lot of programs these days with no ./configure. [/QUOTE]

Also, Checkinstall doesn't list dependencies - you still have to get them yourself before you can compile.

---

### Post by ingo on 2007-02-12
Thanks for posting the contents of that folder. First I'd read the README! It should tell you what to do next. If you have to make anything executable (which I believe you will) so that it can work like an *.exe file you do
> chmod +x name_of_file
Come back in case of other questions, but you appear to be persistent enough :)

---

### Post by avatar3 on 2007-02-12
hello. in the readme it says install using the "installer.kmdr" as i have thought for a while. it is used by "Kommander", as you probably know cause you are running kubuntu. 

and it needs the following files too:

Kommander-executor
kdialog (KDE)
ImageMagick (convert)
PdfToolKit (pdftoppm)
cdrdao

as far as i have understood i need to be running kde or do some "tuning" of my programs? as my laptop finishes installing kde on it i will try running it on that computer. i will post for any progress

EDIT: 

i found kde rather "bad". atleast i think so. still couldnt get the program work in kde. "failed to install copstation" or something.. pretty annoying. but someone with superior wisdom will soon come save me :)

---

