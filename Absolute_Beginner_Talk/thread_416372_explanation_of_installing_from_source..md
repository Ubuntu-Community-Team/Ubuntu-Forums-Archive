---
title: "explanation of installing from source."
date: 2007-04-21
forum: Absolute Beginner Talk
---

### Post by pjones0404 on 2007-04-21
i am fairly new to linux and have a question about installing from source. I dont understand exactly how to do it. There are a few different apps that i see it is required to install this way and not w/ apt-get or through synaptic. Is there some overview of what this process entails. 

Any explanation would be appreciated as i just want to understand how to do this so i can apply it to the various applications out thee. I understand what installing from source is jut not how to do it. Anyone have a link to a site that explains how to do it. 

another question is where does it put the source when i run a command like, "sudo apt-get install source anyprogram"

thanks in advance.

---

### Post by dunedust on 2007-04-21
Heres a guide for software installation

*[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)*

programs will get downloaded to your home folder 
most of them are hidden
so you can see the program folders by using ctrl+h inyour home folder

---

### Post by ffxr on 2007-04-21
hmmm ... im no expert ... but ll offer my 2 pennies...

firstly i dont download the source via apt-get.. so i dont know where the source goes, but ll hazard a guess and say /usr/src 

i usually get the the source from the applications' website (or wherever) in an archived format.. generally a tar archive..

then i extract the archive either via the gui by right clicking 'extract here' or via the command line, eg:

```

tar -xvf sourcecode.tar.bz

```

i then inspect the extracted files for a README or an INSTALL file and i find build/compile instruction in there... also, the applications' website might contain build instructions..

usually it involves.. running
```

./configure 

```
which creates a make file which tailors the application to your system and/or your requirements.
```

make

```
which compiles the source for your system
```

make install

```
which installs the compiled code into your user directories..

*also some applications provide an install script , which means you dont have to run the configure, make & make install steps manually.. keep an eye out for these..

*compiling source can fail because your system has not got dependent libraries installed, also worth bearing in mind.. (can be compilers, development libraries etc, often pointed out in the README)

Compiling from source is  a little daunting to begin with, but, it does become a lot easier, the more you do it = the more confident you become with it, so dont be afraid of compiling source code (like i was)

I am sure there is some gaps in my knowledge of the subject, but im pretty confident im thinking along the right lines , so i hope this helps some.

happy experimenting.

---

### Post by GSF1200S on 2007-04-21
> **ffxr said:**
> hmmm ... im no expert ... but ll offer my 2 pennies...

firstly i dont download the source via apt-get.. so i dont know where the source goes, but ll hazard a guess and say /usr/src 

i usually get the the source from the applications' website (or wherever) in an archived format.. generally a tar archive..

then i extract the archive either via the gui by right clicking 'extract here' or via the command line, eg:

```

tar -xvf sourcecode.tar.bz

```

i then inspect the extracted files for a README or an INSTALL file and i find build/compile instruction in there... also, the applications' website might contain build instructions..

usually it involves.. running
```

./configure 

```
which creates a make file which tailors the application to your system and/or your requirements.
```

make

```
which compiles the source for your system
```

make install

```
which installs the compiled code into your user directories..

*also some applications provide an install script , which means you dont have to run the configure, make & make install steps manually.. keep an eye out for these..

*compiling source can fail because your system has not got dependent libraries installed, also worth bearing in mind.. (can be compilers, development libraries etc, often pointed out in the README)

Compiling from source is  a little daunting to begin with, but, it does become a lot easier, the more you do it = the more confident you become with it, so dont be afraid of compiling source code (like i was)

I am sure there is some gaps in my knowledge of the subject, but im pretty confident im thinking along the right lines , so i hope this helps some.

happy experimenting.

Right on.. I dont know if this is necessary, but I usually use:

sudo make clean

Before you do this, I might remind you to change directories. After you download the .tar.gz package, and extract its contents, you need to change directories to the extracted folder. For example, if you extract a folder named ChuckNorris to your /home folder and want to install it, you would type:

cd ChuckNorris

sudo make

sudo make install

sudo make clean

Hope this helps...

**Edit** In order to compile .tar.gz packages, you need to have build-essential, which you can find in the synaptic package manager..

---

### Post by pjones0404 on 2007-04-21
i appreciate all the explanations. i was alwas curious about the correct process when doing this. i am going to bookmark this thread when i find another application that i want to install.

anyone else that wants to add there information would be welcomed as well.

thanks again.

---

