---
title: "problem installing vive"
date: 2007-06-08
forum: Absolute Beginner Talk
---

### Post by natakim on 2007-06-08
i am a complete noob with terminal. currently i'm trying to install vive. following the instructions here

[http://ubuntuforums.org/showthread.php?t=114946]("http://ubuntuforums.org/showthread.php?t=114946")

the first two terminal entries seem to have worked, but when i get to the third

> ./configure --prefix=/usr
make
sudo make install 

i get this error

> natakim@natakim-desktop:~$ ./configure --prefix=/usr
bash: ./configure: No such file or directory
natakim@natakim-desktop:~$ make
make: *** No targets specified and no makefile found.  Stop.
natakim@natakim-desktop:~$ sudo make install
Password:
make: *** No rule to make target `install'.  Stop.
natakim@natakim-desktop:~$ 



as is indicated before this terminal entry, i downloaded vive and extracted the contents. it was placed in my home folder. i'm sure i am missing something very basic here, but i really have no idea. any suggestions greatly appreciated.

thanks

---

### Post by Kobalt on 2007-06-08
Within the Terminal, you need to navigate to the vive folder. You downloaded the sources as an archive, extract it in your Home folder. Now you must have a vive folder in you Home. From the Terminal enter : ```
cd /vive
```(adapt the folder name to what you had extracting the archive. No you can enter the compilation commands you have (./configure, make & make install) from there.

---

### Post by natakim on 2007-06-08
> **Kobalt said:**
> Within the Terminal, you need to navigate to the vive folder. You downloaded the sources as an archive, extract it in your Home folder. Now you must have a vive folder in you Home. From the Terminal enter : ```
cd /vive
```(adapt the folder name to what you had extracting the archive. No you can enter the compilation commands you have (./configure, make & make install) from there.


sounds good so far. would it be then..

cd /home/natakim/vive

the folder in my   /home/natakim    is vive-1.0.2

sorry to be so ignorant, there is a conceptual leap involved here and i just can't quite make it.

---

### Post by natakim on 2007-06-08
ok so something else is missing now

> natakim@natakim-desktop:~$ cd /home/natakim/vive-1.0.2
natakim@natakim-desktop:~/vive-1.0.2$ ./configure
Checking your system in order to install Vive...
Checking for ffmpeg...Found
Checking for vobcopy...Found
Checking for cpdvd...Not found
Please install cpdvd from [http://www.lallafa.de/bp/cpdvd.html](http://www.lallafa.de/bp/cpdvd.html) or your repositories
natakim@natakim-desktop:~/vive-1.0.2$ 


i went to the page and clicked on download but it just gives a page of text?

i'm drowning here:o

---

### Post by natakim on 2007-06-08
ok i downloaded cpdvd through synaptic package managers (kudos to me, or not). blundered through the rest and on the third try it works. so now i type vive in terminal and wippee, it launches. thanks for the assistance. i love linux, but god it is confusing when you know nothing..

cheers:p

---

### Post by Kobalt on 2007-06-08
It's a whole new learning process, but you seem to be learning quick :) 

Glad I could help you.
Welcome to Ubuntu ! ;)

---

### Post by 3rdalbum on 2007-06-08
Congratulations - you're learning very quickly. Compiling from source isn't difficult once you know how, but it's alien to most people so difficult to work out for yourself.

---

### Post by natakim on 2007-06-10
> **3rdalbum said:**
> Congratulations - you're learning very quickly. Compiling from source isn't difficult once you know how, but it's alien to most people so difficult to work out for yourself.


agreed. i think the most daunting aspect is just thinking about it. linux is very different to my m$ and mac experience, and the terminal scares me to death. but it really does seem to be largely a conceptual shift, one needs to go through things step by step, and the learning is fun, plus i think one really does get an insight into how things actually work, rather than just staring at pretty gui's. (though i do love pretty gui's)

what i love the most is that when i come across a problem, there are truly helpful people such as yourself who offer quick and useful advice. also, every time i have a new need, ie video encoding or whatever, it is merely a matter of searching these forums and finding the name of some software then a quick trip to applications/add-remove, and bingo- install app and problem solved. though i still use my windows partition sometimes, it is getting rarer an event. 

cheers

---

