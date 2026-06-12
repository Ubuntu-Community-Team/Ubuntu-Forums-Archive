---
title: "[SOLVED] Trouble installing program from .tar/.gz (Missing something?)"
date: 2008-01-24
forum: Absolute Beginner Talk
---

### Post by Motorhead Kaze on 2008-01-24
I read these very helpful points about installing .tar.gz files from the web and the other forum posts under the title "Installing tar gz" but I wonder what I'm missing.

I am trying to install a translation tool called "Omega T".  I made sure to get  *build-essential *from synaptic, but when changing directories to where I put the tar gz file I tried "./configure" I tried "Make" and "sudo make install" and was denied. 

kaze@kaze:~/omega$ ./configure
bash: ./configure: No such file or directory
kaze@kaze:~/omega$ 

kaze@kaze:~/omega$ make
make: *** No targets specified and no makefile found.  Stop.
kaze@kaze:~/omega$ sudo make install
make: *** No rule to make target `install'.  Stop.
kaze@kaze:~/omega$ 

kaze@kaze:~/omega$ tar jxvf filename.tar.bz2
tar: filename.tar.bz2: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
kaze@kaze:~/omega$ sudo apt-get install build-essential.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package build-essential.
kaze@kaze:~/omega$ 

I'm just getting bashed and stopped.  (grin)
So, what am I doing wrong?  I thought perhaps I wasn't "In deep enough" so I 

kaze@kaze:~/omega$ cd omegat.tar.gz
bash: cd: omegat.tar.gz: Not a directory

I'm sorry, I'm limited to this.  So please let me know what I need to do that I'm missing.
If it helps, I did extract the bits from the .tar.gz file itself but there is no install file, just a jar file, some text files and 4 folders named "jre" (java run envir.)  "lib" "Images" and "docs"  so ... help?

Thanks!

---

### Post by rhc on 2008-01-24
Isn't there an installation file called Installation or something in those folders?
Many programs have some documentaries.

---

### Post by LaRoza on 2008-01-24
No period at the end of "build-essential"

Read the documentation for this, it could be anything...

---

### Post by p_quarles on 2008-01-24
[SIZE=2]> **Motorhead Kaze said:**
> 
kaze@kaze:~/omega$ ./configure
bash: ./configure: No such file or directory
kaze@kaze:~/omega$ 
Based on that, I'm guessing you haven't yet extracted the tar.gz files:
```
tar -xzvf *name-of-download*.tar.gz
```Then, cd into the new directory that's creating by unpacking those files. Repeat the steps you tried earlier. [/SIZE]

---

### Post by PeterJS on 2008-01-24
Looks like it's a java program, it should run in place with no need to build or install. Try:
```

java -jar *something*.jar

```

Is there a shell script in there as well? It might need to have it's environment set up before invoking java.

---

### Post by Rocket2DMn on 2008-01-24
Should be something like this:
```
sudo apt-get install build-essential
tar -xzvf omegat.tar.gz
cd omegat
./configure
make
make install
```
You will need to check the directory though.  What are you trying to install anyway?

---

### Post by Sef on 2008-01-24
Read [How to Install Anything in Ubuntu]("http://monkeyblog.org/ubuntu/installing/").

---

### Post by Motorhead Kaze on 2008-01-24
Thanks for all the help.  God Ubuntu people rule.

Responding here, backwards:

Sef - That was the exact tutorial I read, in fact it's still open. Sorry I wasn't more clear about WHICH tutorial I read.   This is where I read about the need for build-essential, under  "Source Package (.tar, .tar.gz, .tgz, .tar.bz, ...)" .  As I said above, I followed these instructions the best I could, then read some other people's troubles on the forums before coming here.  Something was missing that wasn't written in the tutorial.  I'm guessing  "java -jar OmegaT.jar"

Rocket2dmn - When I got to: "tar -xzvf omegat.tar.gz"  the terminal just went to town.  But at"cd omegat" and "./configure"  I got the same errors as before.  So...

Peter JS - Thanks to you too. " java -jar OmegaT.jar" UNJARRED another part of my problem.  The program has opened successfully, although I got this in the terminal:
18648: ===================================================================
18648: OmegaT-1.6.1_4 (Thu Jan 24 18:50:45 JST 2008)  Locale en_US
18648: 
Fontconfig error: "~/.fonts.conf", line 2: no element found
Fontconfig error: "~/.fonts.conf", line 2: no element found
Fontconfig error: "~/.fonts.conf", line 2: no element found

It seems to me that the combination of above both worked.  Am I correct in assuming that I didn't have the correct JRE installed and Peter's code installed it?  Anyway, it is working.  So thanks!

P_quarles - Domo.  I got "tar jxvf filename.tar.bz2"  from one of the other forum posts, I'm guessing that in "-xzvf" vs. "jxvf" the "J" is wrong?

LaRozza - Thanks. That was sloppy cut and pasting on my part.  I overlooked the fact that I pasted the words with the period.  After that I grabbed build-essential from Synaptic and installed it.

Thank you guys, very much.  I don't mean to be all gushy, but this kind of help is exactly why people want to come to Ubuntu.

BTW, care to share with me how to post code in the boxes so I don't have to use quotations?

(annoying little sunglass guy on my "2008" there.  Glad that doesn't show up in my terminal!)

---

### Post by p_quarles on 2008-01-24
Yes, the difference is important. the "j" option is used for unpacking files that were compressed with bzip2 (i.e., .tar.bz2 files), while the "z" option is used for unpacking files compressed with gzip (= .tar.gz files). In this case, you have a tar.gz file, so the command I gave you is the right one.

---

### Post by Motorhead Kaze on 2008-01-24
Dang.  My mistake was in blurring over the fact that the post I was reading was for bzip2 files.  But now I'm all clear and learned some more about the terminal.  Until today I pretty much stayed away from anything tar gz, but I'm glad I tried this.

---

