---
title: "Applications in Ubuntu"
date: 2007-09-21
forum: Absolute Beginner Talk
---

### Post by Stall on 2007-09-21
Good day. I am giving some thought to switching over form Ubuntu from Vista. After trying it for a little bit, it has motivated me to dig out an old HDD and give it a try on it. It has a certain feel I can't quiet place that is better than Windows. I really am enjoying my time using it so far.

However, I have a question regarding the locaiton of applications in Ubuntu. Where is the file that is similar or the equivalant of program files in Ubuntu? I would be much obliged if someone could tell me where to find this location I spoke of.

Also, I have two other questions. What is a program that is similar to Irfan View on Linux? And might there be a sort of 'master list' of shell commands that I could print/save for future use?

I thank you for your time, 
Stall

---

### Post by dcstar on 2007-09-22
> **Stall said:**
> Good day. I am giving some thought to switching over form Ubuntu from Vista. After trying it for a little bit, it has motivated me to dig out an old HDD and give it a try on it. It has a certain feel I can't quiet place that is better than Windows. I really am enjoying my time using it so far.

However, I have a question regarding the locaiton of applications in Ubuntu. Where is the file that is similar or the equivalant of program files in Ubuntu? I would be much obliged if someone could tell me where to find this location I spoke of.

Also, I have two other questions. What is a program that is similar to Irfan View on Linux? And might there be a sort of 'master list' of shell commands that I could print/save for future use?

I thank you for your time, 
Stall

[http://wiki.linuxquestions.org/wiki/Linux_software_equivalent_to_Windows_software](http://wiki.linuxquestions.org/wiki/Linux_software_equivalent_to_Windows_software)
[http://www.ibiblio.org/pub/Linux/docs/HOWTO/other-formats/html_single/Bash-Prompt-HOWTO.html](http://www.ibiblio.org/pub/Linux/docs/HOWTO/other-formats/html_single/Bash-Prompt-HOWTO.html)

---

### Post by NoThanksM$ on 2007-09-22
Correct me if I'm wrong, Stall, but I don't think either of the links are the information you're looking for, correct?  I've wondered the same thing you asked myself, though, and would love to know the answer.

---

### Post by anemptygun on 2007-09-22
> **Stall said:**
> 

However, I have a question regarding the locaiton of applications in Ubuntu. Where is the file that is similar or the equivalant of program files in Ubuntu?

/local is the "equivalent" of C:\Program Files. This is where the binaries and data are store by the sys admin.*****

> **Stall said:**
> What is a program that is similar to Irfan View on Linux?

Is there a particular task you use Irfan for?

> **Stall said:**
>  And might there be a sort of 'master list' of shell commands that I could print/save for future use?

[http://www.ss64.com/bash/](http://www.ss64.com/bash/)



***corrected by edd07

---

### Post by edd07 on 2007-09-22
As far as I know, the binaries (which are the executables) are in the /bin folder. However, there is a /usr/share/applications folder, where some files Ubuntu tells me are "desktop configuration files" live. All of my applications are there. I have no idea what those "desktop configuration files" are.

---

### Post by AndyCooll on 2007-09-22
There isn't a "Program Files" type of folder as such, files in general are placed according to type. These two links will hopefully explain things a bit better:
[File System Tree]("http://www.vias.org/linux-knowhow/lnag_05_02_03.html")
[Linux's directory structure]("http://www.tuxfiles.org/linuxhelp/linuxdir.html")

:cool:

---

### Post by rich.bradshaw on 2007-09-22
Literal programs are in /bin, system binaries are in /sbin, program settings are in /etc, specific user settings are in their /username/home/ and start with a .

Basically, it's all split up instead of in the same place as it is in Windows - you don't need to know this to use the system though, it only really matters if you are making packages.

---

### Post by sailor2001 on 2007-09-22
in synaptics, search for anything you want. It does a good job of finding most every type of program you're looking for. Also go to community cafe and read some of the posts about "favorite programs" and check each one out in synaptics. You'll find some great programs you never thought bout before

---

### Post by mcduck on 2007-09-22
Pretty much all user programs (as compared to parts of the system itself) are inside /usr. You'll find the executable files of most of your programs in /usr/bin, all the documentation in /usr/share/doc, images in /usr/share/pixmaps and so on. So instead of placing files to directories based on what program they belong to they are located based on what the purpose of the file is.

While this may sound confusing in the first place it actually makes things easier for you. For example you never need to search for the executable file of a program, as they are all in the same place.

---

