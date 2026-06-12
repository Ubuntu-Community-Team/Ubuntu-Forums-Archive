---
title: "Help with ./configure"
date: 2007-05-23
forum: Absolute Beginner Talk
---

### Post by gogogo111 on 2007-05-23
Ok, so I am trying to install Cube 2/Sauerbraten, a game for linux. Google it if you want.


I'm reading how to install .tar.bz2, so I did this.

tar xvjf sauerbraten_2007_04_15_spring_edition_linux.tar.bz2


Ok, it did some stuff, and I cd'd to the "sauerbraten" folder it made.

So I try to do ./configure, and I get this.

```
matthew@matthew-desktop:~/Desktop/sauerbraten$ ./configure
bash: ./configure: No such file or directory

```

Any help with this? It does this to any .tar file too. I would love to figure this out.

---

### Post by chamberlain2006 on 2007-05-23
Are you sure that you need to run ./configure?  Some programs already have the Makefile included.  What is the output of "ls". (what files are in the directory)

---

### Post by WW on 2007-05-23
Look for a file in the directory with a name like "README" or "INSTALL", and read it.

---

### Post by chamberlain2006 on 2007-05-23
Just as I thought.  From the site:
"For Linux: gunzip, chmod +x sauerbraten_unix and then ./sauerbraten_unix. Needs a decent and compliant OpenGL implementation."
So do the following:
```
chmod +x sauerbraten_unix
./sauerbraten_unix
```

---

### Post by gogogo111 on 2007-05-23
Ok, here is the output of ls


```
matthew@matthew-desktop:~/Desktop/sauerbraten$ ls
bin_unix  config.cfg  data  docs  packages  README.html  sauerbraten_unix  src

```

I did see a makefile in /sauerbraten/src though. How would I go about executing it?

---

### Post by chamberlain2006 on 2007-05-23
Read my last post!

---

### Post by gogogo111 on 2007-05-23
Yup, I did. Thank you for that part, but now I get this.

```
matthew@matthew-desktop:~/Desktop/sauerbraten$ ./sauerbraten_unix
./bin_unix/linux_client: error while loading shared libraries: libSDL_mixer-1.2.so.0: cannot open shared object file: No such file or directory

```


Ok, so I did this.

```
sudo aptitude install libsdl-image1.2
```

Ok, so then I try ./sauerbraten_unix again.

```
matthew@matthew-desktop:~/Desktop/sauerbraten$ ./sauerbraten_unix
./bin_unix/linux_client: error while loading shared libraries: libSDL_mixer-1.2.so.0: cannot open shared object file: No such file or directory

```

I wish this would work. :(

---

### Post by chamberlain2006 on 2007-05-23
You'll need the -dev package, libsdl-image1.2-dev

---

### Post by WW on 2007-05-23
I downloaded the file, and tried it out. It worked on my system, but I already have a lot of libraries installed.

To start, run this command to install some SDL libraries:
```

sudo apt-get install libsdl1.2debian-oss libsdl-image1.2 libsdl-mixer1.2

```
and try the saurerbraten_unix command again. (You may need to install more libraries, but it's worth a shot.)

---

### Post by WW on 2007-05-23
Actually, you won't need the -dev packages.  This is a precompiled executable; you just need to install the appropriate shared libraries.

---

### Post by gogogo111 on 2007-05-25
YES! THANK YOU! I got it! It was the libs that were missing, so I did the command WW told me, and it worked!! Thank you to all of you who helped me during this process. I have this game on Windows too, and I noticed a couple of differences.

1) Windows version had more shadows? Like enviroment shadows. The linux version does not, no option for it either. Maybe its something with the nvidia driver. 

2) Performance is worse, but I'm thinking this is driver related too. Its more then playable (70+ FPS), but on Windows, its about 150 up.

Screenshots:

[IMG]http://img399.imageshack.us/img399/1746/sauerbratenyesiw0.png[/IMG]

[IMG]http://img260.imageshack.us/img260/3012/sauerbraten2lp3.png[/IMG]

---

