---
title: "Compile Software"
date: 2007-07-05
forum: Absolute Beginner Talk
---

### Post by justin1278 on 2007-07-05
Hello,

I've been using linux for a while and am trying to learn how to compile software in Ubuntu, so far the various ways have only confused me. I really like Ubuntu and would really appreciate it if somebody could help me in learning how to compile software. 

Thanks,
Justin

---

### Post by limbourg31 on 2007-07-05
here it is in the short and sweet form:

download package
extract trhrough archive manager or tar  -zvxf "package directory"
cd to the newly created folder
./configure
make
sudo make install

and that's it (make sure you have done sudo apt-get install build-essential first if you have not already installed it)

---

### Post by Majorix on 2007-07-05
Why do you need to compile software? For us normal people the repos are enough of an inventory :p

---

### Post by limbourg31 on 2007-07-05
some software isn't always available in the repos, and and if you're browsing and find a neat tool, you just want to download it and make it run, instead of adding the deb-src to your source list :)

---

### Post by justin1278 on 2007-07-05
> **Majorix said:**
> Why do you need to compile software? For us normal people the repos are enough of an inventory :p

I want to install the latest version of thunderbird

---

### Post by dwanders on 2007-07-05
This looks very promising for you r needs:

[http://ubuntuforums.org/showthread.php?t=323939](http://ubuntuforums.org/showthread.php?t=323939)

---

### Post by justin1278 on 2007-07-05
> **limbourg31 said:**
> some software isn't always available in the repos, and and if you're browsing and find a neat tool, you just want to download it and make it run, instead of adding the deb-src to your source list :)

Thanks for the reply, I will try that now and see how it works.

---

### Post by justin1278 on 2007-07-05
I get this error, what am I doing wrong?

---

### Post by justin1278 on 2007-07-05
Anyone have any ideas what I'm doing wrong, I really would like to learn how to compile software from source.

---

### Post by dwanders on 2007-07-05
The link to the how-to lays it out pretty much. Did you get a chance to look it over and see if you have everything installed that you need to be able to compile source?

---

### Post by Cypher on 2007-07-05
> **justin1278 said:**
> I get this error, what am I doing wrong?

Please don't follow instructions blindly. The person who suggesded the "./configure; make; make install" routine suggested that USUALLY happens, but that doesn't mean it's the way for all applications.

After going into the directory of the software you want to compile, look around and first see what files you have. Next read any README or INSTALL files and you should have an idea of what to do next..

---

### Post by justin1278 on 2007-07-05
I looked at the readme and it just gave me a link which doesn't give any installation instructions, it's ok I will just use Thunderbird 1.5 from the respositories.

---

### Post by misfitpierce on 2007-07-05
They make pre-compiled sources of thunderbird for ubuntu... compiling it is not necessary... Also to build you need to make sure you have build-essential installed. I would just try automatix or get-deb.net for a thunderbiird if you wish for easier way to get it.

---

### Post by justin1278 on 2007-07-05
Yes but the pre-compiled one is an older version (1.5), thanks for the links, I will check them out.

---

### Post by andrew.46 on 2007-07-08
Hi,

 Saw your post:

> **justin1278 said:**
> I get this error, what am I doing wrong?

 Have you installed the compiling tools? These are not part of the 'default' install and need to be downloaded seperately. Could I suggest before jumping in boots first read this excellent tutorial:

[https://help.ubuntu.com/community/CompilingSoftware](https://help.ubuntu.com/community/CompilingSoftware)

                 Andrew.

---

