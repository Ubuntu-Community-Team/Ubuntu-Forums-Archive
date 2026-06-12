---
title: "Compile Songibird From Source...And Compiling From Source In General"
date: 2007-01-16
forum: Absolute Beginner Talk
---

### Post by Fingerz91 on 2007-01-16
Hey All,

I've been using Ubuntu for a week and a half at my buisness, and now I installed it on PC at home....

I want to try a GNU music management software called Songbird, and I have been given its tar gz, which I unzipped to a folder called Songbird on my desktop, as pictured below...

[IMG]http://i133.photobucket.com/albums/q59/Fingerz91/desktopsongbird.png[/IMG]

I then open a terminal, cd to that directory and type ./configure, but am given:

tommy@tommy-desktop:~$ cd desktop
bash: cd: desktop: No such file or directory
tommy@tommy-desktop:~$ cd Desktop
tommy@tommy-desktop:~/Desktop$ cd Songbird/
tommy@tommy-desktop:~/Desktop/Songbird$ ./configure
bash: ./configure: No such file or directory
tommy@tommy-desktop:~/Desktop/Songbird$ configure
bash: configure: command not found


I know I input ./configure correctly, and I know build-essential is installed...

[IMG]http://i133.photobucket.com/albums/q59/Fingerz91/buildessential.png[/IMG]

I also know the three basics of compiling.... ./configure, make, make install (i've done it in Linspire...)

I am not sure why, but I cannot compile....

---

### Post by bodhi.zazen on 2007-01-16
Songbird is distributed as a binary, no need to compile :p

[http://doc.gwos.org/index.php/SongBird](http://doc.gwos.org/index.php/SongBird)

And for source installs, check out checkinstall

---

### Post by 23meg on 2007-01-16
Are you sure you got the source archive for Songbird, and do you have a specific reason to build from source? Most likely not; not every archive file with a .tar.gz extension contains sources. You probably got the binary archive; just double click on the executable file "Songbird" in the directory and it will run.

---

### Post by s04bf1c2 on 2007-01-16
When you cd into the directory, list (ls) its contents. If it is the same version i downloaded, there is not need to run configure,make.... You just run "./Songbird". Hope this helps

---

### Post by Fingerz91 on 2007-01-16
I got the binary :)

I also didnt know Songbird was available via automatix.....

Still, why wouldnt ./configure yield a result, since I have the build-essential package installed, shouldnt it give me something?

---

### Post by zytsef on 2007-01-16
> **Fingerz91 said:**
> I got the binary :)

I also didnt know Songbird was available via automatix.....

Still, why wouldnt ./configure yield a result, since I have the build-essential package installed, shouldnt it give me something?

As a matter of fact, configure is just a script that is often used with source code to read some parameters from your operating environment and fill in the appropriate flags in a makefile. 

In short, no, a binary shouldn't give you anything when you try to ./configure.

---

### Post by bodhi.zazen on 2007-01-16
But it did, an error message :p

./configure is to compile source code and in this case you do not have the source code.

---

### Post by Fingerz91 on 2007-01-16
ahh i see...

thanks for the help

do you happen to know if songbird 1 is coming anytime soon and if it'll be in the repos?

---

