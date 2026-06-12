---
title: "First-time compiling"
date: 2006-07-18
forum: Absolute Beginner Talk
---

### Post by aeto on 2006-07-18
eversince i started using linux & ubuntu i didnt find a need to compile anything since i got everything i wanted..but like they say, sometimes u wont find what u need. And what's linux w/o learning how to compile?

I tried going thru the tutorials but this particular source file doesnt have a configure file. I read something inside which tells me to download other required packages, and then "do make". So i skipped the configure step & ran make..but there seems to be errors all over. I would highly appreciate it if some1 could download the source file & let me know how u went through installing it :mrgreen: Here is the link to the download: [http://www.ninjam.com/downloads/src/cclient_src_v0.01a.tar.gz](http://www.ninjam.com/downloads/src/cclient_src_v0.01a.tar.gz)
Thanks alot!

---

### Post by Sef on 2006-07-18
The problem could be that it is version 0.01a.   Versions that low are basically alpha versions, i.e. experimental.   One should expect lots of crashes and problems installing.

Now what problems have you had when installing?

Also what are your computer specs?

---

### Post by OU812 on 2006-07-18
Try installing the dependencies first. Then reinstall the app. When finished, run it from the terminal so that if there's an error it will be echoed to the terminal. If there's no errors, then you can launch it from the menu.

john

P.S. After make, I think you have to do

sudo make install

(make can be done as user, but make install as root)

---

### Post by swamytk on 2006-07-18
Are you sure you installed the libraries mentioned in Compiling file? I think you have to install development library, i.e -dev files.
> On linux, install libogg, libvorbis, libasound, then do

make


It is good practice to post the error message for better support :-)

---

### Post by diepruis on 2006-07-18
[QUOTE=aeto]I read something inside which tells me to download other required packages...[/QUOTE]

These are dependencies, you must install them first before compiling the program.

---

### Post by aeto on 2006-07-18
hey thanks for the input guys..my cpu specs are as follows:

Intel Pentium 3 866@910
320MB RAM
Onboard AC'97 sound
4MB/S Cable (Ethernet Connection)

I dont think specs are the problem coz my friend has an old k7 533MHz & he's able to get the software running..though not in Linux.

Thanks. I downloaded the -dev files for the dependencies. But same thing happens:

[[IMG]http://img92.imageshack.us/img92/2052/lsyy3.th.jpg[/IMG]](http://img92.imageshack.us/my.php?image=lsyy3.jpg)

everything goes fine until:

[[IMG]http://img93.imageshack.us/img93/7108/error1tf4.th.jpg[/IMG]](http://img93.imageshack.us/my.php?image=error1tf4.jpg)

[[IMG]http://img95.imageshack.us/img95/4300/error2cq9.th.jpg[/IMG]](http://img95.imageshack.us/my.php?image=error2cq9.jpg)

[[IMG]http://img224.imageshack.us/img224/3940/error3gu9.th.jpg[/IMG]](http://img224.imageshack.us/my.php?image=error3gu9.jpg)

Thats the whole big list of errors divided into 3 windows.

Is there something wrong with how my Ubuntu is configured? Any other required packages? I'v gotten all the needed files for compiling a software in Ubuntu Linux. And this app has surely been tested in Linux since there is "popular demand" :-k I have no problem with harbouring unstable software..but its not even installing :lol:

---

### Post by mlind on 2006-07-18
Looks like you're missing at least some ncurses dev package, probably
libncurses5-dev ?

Maybe you should read a tutorial about compiling programs on linux platform, otherwise it could get pretty rocky for starters..

---

### Post by aeto on 2006-07-18
yep i went thru a few tutorials before i got started. did everything i was told to do..i will now try to compile another software to ensure my method is correct.

---

### Post by aeto on 2006-07-18
yep..it seems others are working. i tried with a software which doesnt have a configure file. so i went straight to make & it successfully installed. anyway how do i run the app now? i cant find it in the applications or deb menu..normally which type of file is the run file? If there is then i'd just make a shortcut.

---

### Post by OU812 on 2006-07-18
Open a terminal and enter the name of the program. If it doesn't run, you will probably be given some explanation as to why. If for example the problem is command not found, you'll have to search your files for the location of your app (the "executable" is usually in /path/bin). Then type /path/name_of_program. Any other errors, please post.

john

P.S. @experienced users: Can you do "program_name &> out_file" to get a text file of the output at the terminal (redirecting it, basically)? If this is not correct, how?

---

### Post by aeto on 2006-07-19
thanks..well its command not found. i used checkinstall..so i used the name i chose during installation..doesnt work. i searched for the executable, tried clicking, tried using the name through terminal..nothing happens. the only way is navigating to the root directory of the installation & clicking an sh file/shell script. Btw i have trouble understanding the following:

> *nix versions of cube clients and standalone servers.

The clients **function identical to the win32 client**, see config.html.
Run them from the **root cube dir (chmod em as exe first)**.
Clients will need the following dynamic link libraries present:
opengl, glu, sdl, sdl_image, sdl_mixer, png, jpeg, zlib (1.2.1 for
all SDL libs, do a ldd for details).

The servers need NO libs, no external files, no sound or video,
just run it :) Server port is fixed at 28765, currently.

Make sure to **chmod +x these binaries and the cube_unix script**
before running them.


What do the phrases in bold mean?

And one more thing.."cd to the directory containing the package's source code" -- does it mean the root installation directory? Or the "src" folder?

Thanks again..y'all have been very helpful \\:D/

---

### Post by mlind on 2006-07-19
> **aeto said:**
> thanks..well its command not found. i used checkinstall..so i used the name i chose during installation..doesnt work.


checkinstall should make you a installable .deb of your program.

"root cube dir" probably means the directory you've installed this cube thingy. "chmod as exe" means use chmod command to give executable bit for all executable scripts/binaries.
```

chmod +x *file*

```

---

### Post by argie on 2006-07-19
[quote=OU812]P.S. @experienced users: Can you do "program_name &> out_file" to get a text file of the output at the terminal (redirecting it, basically)? If this is not correct, how?
[/quote]
```
program > file
```
works.

---

### Post by mlind on 2006-07-19
> **argie said:**
> ```
program > file
```
works.

execpt it will only redirect stdout, not stderr. To get both, try
```

program > file 2>&1
program &> file

```

---

### Post by aeto on 2006-07-19
thanks again. i figured out those source packages that do not have a configure file normally get installed from "make" onwards. if they dont, then there is something wrong with the package.

---

### Post by mlind on 2006-07-19
> **aeto said:**
> thanks again. i figured out those source packages that do not have a configure file normally get installed from "make" onwards. if they dont, then there is something wrong with the package.

Also, if you're grabbing sources from cvs/svn, there's often file called autogen.sh which will generate configure and Makefile(s) for you.
You'll need bunch of dependencies to successfully execyte autogen.sh script, like automake1.9, autoconf, autotools-dev, pkg-config .. etc.

---

### Post by OU812 on 2006-07-20
Thanks argie and mlind.

john

---

