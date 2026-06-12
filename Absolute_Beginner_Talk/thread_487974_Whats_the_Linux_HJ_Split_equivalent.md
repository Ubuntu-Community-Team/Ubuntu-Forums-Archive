---
title: "Whats the Linux HJ Split equivalent?"
date: 2007-06-29
forum: Absolute Beginner Talk
---

### Post by iamiso on 2007-06-29
Trying to joIn up a couple of files and in XP I'd use HJ Split. Does anyone know the equivalent in Linux? 

As ever many thanks!

---

### Post by paulg on 2007-06-29
I believe the command is:

```
cat file.001 file.002 file.003 file.mpg
```

Where file.mpg is the name of the output file. In this case, 'cat' is short for catenate.

Sorry, don't know of a GUI. Hope this works for you.

---

### Post by iamiso on 2007-06-29
Nice one! I'll give it a go...

---

### Post by kpkeerthi on 2007-06-29
Shouldn't it be ...
```
cat file.001 file.002 file.003 > file.mpg
```

---

### Post by paulg on 2007-06-29
That's the one. Thanks, was away from my computer ;)

---

### Post by BCtom on 2007-07-28
I'm replying to this thread fairly late, (better late than never...), but I use a file splitting apps, with its own GUI, that is very similar to the Windoze HJ-Splitter: called GTK-SPITTER. It is not part of Ubunut's Synaptic's library, or list of programs yet, but it is easy to install and run regardless. You need to download the RPM version of it first, then convert it into a DEB installation file so Synaptic can install it. 

[step 1] Download the gtk-splitter.rpm here: [http://rpm.pbone.net/index.php3/stat/4/idpl/1116749/com/gtk-splitter-2.0-1.i386.rpm.html]("http://rpm.pbone.net/index.php3/stat/4/idpl/1116749/com/gtk-splitter-2.0-1.i386.rpm.html")
I choose version 2.0-0 because I know it is stable.

[step 2]Next, fire up your terminal and CD to the directory where the gtk-splitter.rpm is, and copy & paste this command line, that will convert the RPM into a DEB installation file. 
[HTML]cd 'home/user_name/Desktop'
sudo alien gtk-splitter-2.0-1.i386.rpm[/HTML]

[step 3] Install the gtk-splitter.deb by clicking on it with your mouse (simplest way???).

[step 4] Use your terminal to start the app "gtk-splitter," or create a Launcher. 

I use gtk-splitter all the time for joining and splitting huge archived files. It is very user friendly and fairly easy to use if you are a former Windoze user.

---

### Post by Palmyra on 2007-07-30
BCTom, I thank you a lot!  GKT-Splitter works just fine, with all sorts of formats.  It's just great.  It doesn't have the greatest GUI, but it is simple, small, and it works.  Can't really ask for more.  

The round-about way is slightly annoying, but it doesn't matter.  I should contact the developer and ask for a .deb (one for the public).

---

### Post by vasiliymeshko on 2007-07-30
> **iamiso said:**
> Trying to joIn up a couple of files and in XP I'd use HJ Split. Does anyone know the equivalent in Linux? 

As ever many thanks!

There *is* a Linux version of HJ Split.

[http://www.freebyte.com/hjsplit/#linux](http://www.freebyte.com/hjsplit/#linux)

Hope this helps

---

### Post by BCtom on 2007-07-31
Hey Palmyra, I'm glad the process worked well for you.
I know, it is a pain!



One point I left out about GTK-SPLITTER, that is, it leaves a link in the main menu: Applications --> Utilities --> FileSplitter. There was no need for a command-line start up, just re-start X and it's there.

 

vasiliymeshko: Yes, I know about the LINUX version of HJ Split. I gave up on installing it because of the required  Library  that is needed to run it. Ever since the last Kernel up-grade, it became broken. I was fed up with it too, I could of spent time finding a fix to get it working, but I switched back to what I was using during my Fedora-Core days.

---

### Post by capink on 2007-08-28
> **BCtom said:**
> 
vasiliymeshko: Yes, I know about the LINUX version of HJ Split. I gave up on installing it because of the required  Library  that is needed to run it. Ever since the last Kernel up-grade, it became broken. I was fed up with it too, I could of spent time finding a fix to get it working, but I switched back to what I was using during my Fedora-Core days.

Me too. But I found a good alternative [here]("http://www.freebyte.com/hjsplit/#java")
Note that this will require java installed. To run the application just type:

java -jar /path/to/hjsplit_g/jar

---

### Post by estelgrace on 2008-06-01
> **capink said:**
> Me too. But I found a good alternative [here]("http://www.freebyte.com/hjsplit/#java")
Note that this will require java installed. To run the application just type:

java -jar /path/to/hjsplit_g/jar

How do I install this?

---

### Post by capink on 2008-06-01
> **estelgrace said:**
> How do I install this?

I made a Debian package for this program. It is attached with this post. But before installing this package you need to install java first:

```
sudo apt-get install sun-java6-jre sun-java6-bin
```


NOTE: To install sun java in the previous step you need to enable the multiverse repositories. Here is guides to enable multiverse ([Ubuntu GUI]("https://help.ubuntu.com/community/Repositories/Ubuntu#head-5bbef89639d9a7d93fe38f6356dc17847d373096") [,Kubuntu GUI]("http://linux.about.com/od/kubuntu_doc/a/kubudg22t04.htm") [,CLI]("https://help.ubuntu.com/community/Repositories/CommandLine#head-e1a24b1b2037f68b5a95f54388582b58ea4c9bd0")).

Then, install the package attached with this message by double clicking it. After the pakcage is installed, you should find an entry called hjsplit in your main menu.

---

### Post by spirit2 on 2008-06-11
How do I select the files to be combined using gtk-splitter? I tried drag selecting, ctrl- clicking, shift-clicking, ctr+entering to no avail. 

Using the cat command did not work either nor did the Java version of HJSplit (the program launches and main menu appears, but the proceeding windows are blank). In the end, using Wine + the Windows version of HjSplit was successful for me in joining the desired files together.

---

### Post by Grizli on 2008-06-18
Thanks @capink! This works greate!:lolflag:

---

### Post by snapemiken on 2008-07-08
Hey thanks a million _capink_ I got mine working !!!

---

### Post by damis648 on 2008-07-08
There is a linux version you know: [http://www.freebyte.com/hjsplit/#linux](http://www.freebyte.com/hjsplit/#linux)

---

### Post by floe on 2008-07-08
Thanks capink :)
Works fine

---

