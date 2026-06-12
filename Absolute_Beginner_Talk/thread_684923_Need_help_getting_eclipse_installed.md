---
title: "Need help getting eclipse installed"
date: 2008-02-01
forum: Absolute Beginner Talk
---

### Post by Azureglows on 2008-02-01
I am brand new to linux, and command line usage in general.  I tried installing the eclipse version that comes with Ubuntu.  After I got the installation running I get this error
```
This package is an installer package, it does not actually contain the
JDK documentation.  You will need to go download one of the
archives:

    jdk-6-doc.zip jdk-6-doc-ja.zip

(choose the non-update version if this is the first installation).
Please visit

    http://java.sun.com/javase/downloads/

now and download.  The file should be owned by root.root and be copied
to /tmp.
```
I need help figuring out what to do.  I have downloaded the jdk-6-doc.zip file, and use the java jar program to extract it.  So right now I have the docs folder as a subdirectory of my /home/username.  Thanks in advance :)

---

### Post by emarkd on 2008-02-01
I'd install it from Synaptic if I were you.  Enable all the repositories under Settings > Repositories and then search for sun-java6

---

### Post by jan quark on 2008-02-01
can you please navigate in the terminal to the downloaded and extracted eclipse package

you can use the command cd to change directory for instance if you have dowloaded the file to the desktop  type 

```
cd /Desktop/name of file
```

when you are in the folder please run the command 

```
ls 
```

this will show all files that are stored in this particular folder
it will help us to say how to install that package

---

### Post by jan quark on 2008-02-01
emerkd you are right

just open the synaptic package manager 

search for eclipse

mark the box for installation and apply 

all the dependencies will be installed automatically

and we don't have to play with compiling such a big file

---

### Post by Azureglows on 2008-02-01
I tried running the installing of the sun-java6-doc from Synaptic and I received the same message.  I have all the repositories under Ubuntu Software tab checked.

---

### Post by Azureglows on 2008-02-01
I have also just tried reinstalling eclipse through Synaptic and get the same error.

---

### Post by emarkd on 2008-02-01
Are you sure you're installing the jdk and not just the jre.  They're in different packages.  You'll need sun-java6-jdk to run Eclipse.  After you get that installed, go to your command line and run 

```
javac -version
```

to see what you've got as the default.

---

### Post by Azureglows on 2008-02-01
From the synaptic list it says I have everything installed.  When typing in the version command it says javac 1.6.0_03.
Edit -- Typo, hit 4 where that 3 is.

---

### Post by emarkd on 2008-02-01
So you've definitely got Java 6 JDK.  Those docs it's complaining about are probably in sun-java6-doc, but I guess you have that already installed too.  I use Eclipse myself and didn't have to download anything from Sun to get it to work.  Hmm...

---

### Post by Azureglows on 2008-02-01
Alright, so since I couldn't get anything else working.  I went and downloaded he jdk-6-doc.zip file and unzipped it via
```
sudo jar xvf jdk-6-doc.zip
```

And used the following commands to try and get it into /tmp and owner be root.root as the error was complaining about
```
sudo chown root.root docs
sudo cp docs /tmp
```

I can confirm I see the docs file in the tmp via the graphical explorer and that the owner is root.root, but it still won't do install.  Did i miss something, or is this really not the issue? :confused:

---

### Post by sowelie on 2008-02-01
I would honestly install eclipse from the eclipse site.  [http://www.eclipse.org]("http://www.eclipse.org") is where you can find it.  The version in the repos is old and most of the plugins out there require the latest version.  It's easy to install, just extract the archive you download to a folder of your choice and run eclipse from that directory.

---

### Post by Azureglows on 2008-02-01
Thanks.  I was actually having problems getting that one to work at first, which prompted me to try the eclipse in the package.  But it seems to be working now (after I learned how to actually install java :) )

The original error still occurs with the other, but I've given up since i go the other eclipse to work.

---

### Post by sowelie on 2008-02-06
As far as eclipse goes, I'd always stick with the latest stable version on their site.  Like I said, all of the best plugins out there generally require the latest version anyway.

---

