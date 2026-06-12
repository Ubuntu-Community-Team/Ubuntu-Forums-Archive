---
title: "unpacking software"
date: 2007-10-06
forum: Absolute Beginner Talk
---

### Post by mszl_1 on 2007-10-06
once i downloaded software to my desktop how do i unpack/ install from there. i have no idea of how to run gzip etc? ark linux has a great app called **rpm installer** that works by right clicking and selecting install with ... rpm installer. it runs thrpough a wizard and whala installed. it also gives additional packages that may need to be installed if not installed already in the repos. any help will be appreciated. thanks

:)

---

### Post by Pumalite on 2007-10-06
You can double click the file, Ark will come up and you can extract after selecting 'all'. Then go to folder and ./configure, or run. (it's good to read the README file first)

---

### Post by Lord Illidan on 2007-10-06
That's for Kubuntu. Ubuntu has file-roller.

It would help if you tell us what you are trying to install. We can give you step by step instructions.

---

### Post by Pumalite on 2007-10-06
Thanks.

---

### Post by mszl_1 on 2007-10-08
i was thinking of games or software or even themes from kde.org. it is not something specific, id rather know how to do things in principle so i cab figure it out from there or ask questions if im unsure. im very unsure as far as a lot of things go in linux but im learning!!
thanks for the help so far.  :):KS

---

### Post by Circus-Killer on 2007-10-08
okay, excuse the obviousness of what i'm about to post. the reason for the post is because

a) the OP said he was new (and thus might not know)
b) he refers to rpm's in arch, but refers to .tar.gz for ubuntu, just checking to make sure he is aware of how the different package management systems work.

okay, so now for the actual post. whilst virtually all linux-based applications are available in source code, you dont *usually* have to install from source.

in ubuntu, *most* application are available through the repositories. as someone mentioned, it would help if we knew what you were trying to install, as various things require different installation methods. but for the most part, for the software in the repositories, all you have to do is run the following command:

```
sudo apt-get install <package-name>
```

so for example if you wanted to install XChat:

```
sudo apt-get install xchat
```

by downloading and installing through the package manager, not only will it handle dependencies, but will also keep those extra packages up-to-date when updating your system.

there are two otherwise to get software. if you download an application in .deb format, then you need to run:

```
sudo dpkg -i filename.deb
```

however, the odds are is that it will tell you that you are missing dependencies, which you will have to install (usually by the first method).

the last of the options is that of installing from source. this involves download a .tar.gz or a .tar.bz2 file. to extract the .tar.gz file:

```

gzip -d filename.tar.gz
tar xvf filename.tar

```

for .tar.bz2 its pretty much the same, except change the word gzip to the word bzip2. (i think). once extracted, usually you would go into the directory of the unpackaged stuff and run:

```

./confugre
make
sudo make install

```

however, t his can vary from program to program. i dont know how helpful i've been, but as said before, i recommend using the repositories for downloading new software. its the easiest and safest, with least possibility of things going horribly wrong.

---

### Post by mszl_1 on 2007-10-08
im sorry if my previous post did not make sense, i have used Ark for a litle while before coming to Ubuntu, hence the mention of the RPM installer. i know ubuntu works differently and im aware of the install via the repos. i have done so a few times so my confidence is ok. however when i want to install a theme form kde.org say, i get it to a file on the desktop and from, here i fail since im newish to linux. i have ben looking at various distro's for about a year now. im just unsure how to run tar.gz etc! i have found the previous post helpful and will have a go with the info provided. thanks. ill keep trying and asking till i get it worked out.

:) haak Vrystaat

---

