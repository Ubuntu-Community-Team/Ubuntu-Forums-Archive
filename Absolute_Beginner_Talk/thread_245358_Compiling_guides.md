---
title: "Compiling guides?"
date: 2006-08-27
forum: Absolute Beginner Talk
---

### Post by podunk on 2006-08-27
Hi! I am new to Ubuntu and Linux. Thanks to you folks I have
mounted my windows drives
Learned how to use pico and nano
Learned my way around the system
Found several tutorials and read them and even remember little bits and pieces.

so thank you!

I think Ubuntu looks cool :-D

I have a game I wish to compile. Is there a general guide somewhere on compiling? I know so little about this that I don't what questions to ask yet. :-)

Thanks!

---

### Post by Jagot on 2006-08-27
[http://monkeyblog.org/ubuntu/installing/#source](http://monkeyblog.org/ubuntu/installing/#source)

This method may not work all the time - there should be a readme or install file in the directory with the program that may give you instructions specific to the program you want to install.

---

### Post by charbo on 2006-08-27
Hi,

Usually, following are the steps required.
1. Download the software file.
2. Uncompress the file. Usually the file is compressed using *gzip* command, and made into a single file by *tar* command. If so, then the file you downloaded would have the extention, .tar.gz. Then, in order to uncompress, you would also use the same command set. Usuallty the command you type is *tar xvzf filename*. Here, the x option means to extract, and z means to uncompress using gzip.
3. Go into the directory created.
4. Read the *readme* file.
5. Run a script to configure, usually by typing *./configure* since the script usually has the name configure.
6. Run *make* comand.
7. Run *make install* command.

It depends on the software, so you definitely want to read the instructions in the readme file. Sometimes, (though it's gotten a lot better than before) you will get dependency errors. Then you would have to install different software or library required by the software you are trying to install, prior to installing it.

I found an example with decent amount of explanations. Go to the section **Source Code**. 
[http://www-128.ibm.com/developerworks/linux/library/l-roadmap9/](http://www-128.ibm.com/developerworks/linux/library/l-roadmap9/)

I hope this helps.
Good luck and have fun.

---

### Post by charbo on 2006-08-27
The link is very nice.

I recommend you follow Jagot's response first.

---

### Post by podunk on 2006-08-27
Thank you!

I did it - I think! :-) There is a whole bunch of stuff scrolling down the terminal screen anyway.

---

