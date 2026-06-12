---
title: "New to Ubuntu"
date: 2008-03-26
forum: Absolute Beginner Talk
---

### Post by mattman059 on 2008-03-26
Okay so far my experience with Ubuntu has been a good one, except for the fact that I am having trouble installing things. For example I downloaded the Java JRE to install but I dont know how? This is pretty much the same for all things in Ubuntu, I go into the Synaptic Package Manager and look up "Java" for example and get nothing. Any help into how to install things on Ubuntu would be appreciated. Thanks

---

### Post by Luinar on 2008-03-26
I would recommend reading through the ubuntu guide - [http://ubuntuguide.org/wiki/Ubuntu:Gutsy](http://ubuntuguide.org/wiki/Ubuntu:Gutsy). That should give you a basic introduction to using Ubuntu, and will talk you through installing commonly used apps (inc. Java IIRC).

---

### Post by oedha on 2008-03-26
> **mattman059 said:**
> Okay so far my experience with Ubuntu has been a good one, except for the fact that I am having trouble installing things. For example I downloaded the Java JRE to install but I dont know how? This is pretty much the same for all things in Ubuntu, I go into the Synaptic Package Manager and look up "Java" for example and get nothing. Any help into how to install things on Ubuntu would be appreciated. Thanks

make sure that you have enabled the repository servers....
go to system - administration - software sources 
mark all boxes
then click close button and after that reload button
now......go back to synaptic again....can you find java now ?

---

### Post by mali2297 on 2008-03-26
See here: [http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

Check that the *multiverse* repository is enabled.

---

### Post by clanky on 2008-03-26
If you got system > administration > software sources

Under the Ubuntu software tab, click all the boxes (no need to click the source code box, but it won't do any harm if you do).  What you are doing is allowing your system to access extra repositories.

When you close the window it will prompt you to reload, do that and it will download package information, after that there should be more packages in the synaptic package manager.

For even more do a forum search for medibuntu.

---

### Post by pedro_orange on 2008-03-26
Synaptic is the method of choice for installing anything really.

But if you want to install from the command line, you can be cheeky&clever!

So you want to install the Java runtime environment? If memory serves me correct that package is called sun-java6-jre.

Using apt-get:

```
sudo apt-get install sun-java6-jre
```

Then it does everything for you. Downloads the file & installs it. Magic.

You can however install things in any number of ways. If you have the tarball downloaded from the website. (.tar.gz)
Unzip that file, and extract it to wherever you want.

Then open a terminal cd to that directory (as you would in Windows - case sensitive remember!) and run the install script. (I've not personally installed Java JRE this way but I would imagine they have an install script - something like install.sh) Then to run this .sh you simply to a:

```
sudo ./install.sh
```

In the directory it's located ofc.

You may find this a better method though; as it's a great time saver and you spend less time faffing about. You can install Mp3 / DVD / Flash / Java all in 1 command. (Thats right! 1 comand!)

```
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by clanky on 2008-03-26
> **oedha said:**
> make sure that you have enabled the repository servers....
go to system - administration - software sources 
mark all boxes
then click close button and after that reload button
now......go back to synaptic again....can you find java now ?

beat me to it!

---

### Post by hyper_ch on 2008-03-26
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

