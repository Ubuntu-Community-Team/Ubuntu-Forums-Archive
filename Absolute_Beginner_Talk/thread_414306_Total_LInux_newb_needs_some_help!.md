---
title: "Total LInux newb needs some help!"
date: 2007-04-19
forum: Absolute Beginner Talk
---

### Post by Shane_linuxnewb on 2007-04-19
Hi, I have had dapper drake for about 6 months and am just getting the time to finally develop it to maybe make a partial transition from windows. I am having problems with three main things. 

1) This is the most important thing! I really want to install Java but i cannot. The Desktop Guide says that i can find an Ubuntu friendly version (.deb) at the repositories or archives, however i have yet to find any archives that have user friendly programs in it.
            * I would like to know where this repository is
            * I would like help on installing programs

2) I am having problems in figuring out how to log into my administrative account in the terminal. It prompts me for my user name, once i enter this it prompts my password but i cannot enter one untill i hit the return key. Any ideas?

3)Music. i love music but cannot find and install programs that can enable me to convert MP3s. Any ideas?

Thanks,
Shane:guitar:

---

### Post by raja on 2007-04-19
1. Read [this]("https://help.ubuntu.com/community/Java").
2. What do you want the admin status for? Most things can be done with  temporary admin status you can get by adding the prefix 'sudo' to the command. This is safer since you dont have to remember to log back into normal mode.

---

### Post by Shane_linuxnewb on 2007-04-19
Thank you about the username, i thought it was critical, now i know better:). The page u linked me is confusing though. I see what to install "sun-java5-bin" if im not mistaken, however the page doesn't tell me where to find this or how to install. Sorry i am a complete beginner and most of this is confusing. Any help is GREATLY appreciated.

Thanks,
Shane

p.s. Is there such a thing as this "archive" of downloadable apps for ubuntu?

---

### Post by dugas on 2007-04-19
to install java (and plugin):
```
sudo apt-get install sun-java5-jre sun-java5-plugin
```

---

### Post by eyelessfade on 2007-04-19
1. Can't remember for dapper, but that is old. in edgy and feisty sun-java is in the repo. if jou deside to upgrade to edgy (mush new stuff) you can just apt-get install sun-java5(6)-jre. dapper may also have it in repos. just do a "apt-cache search sun"

2. as the last guy said

3. do you want to rip cd's to mp3?
many programs do that. I use kde so I use kaudiocreator. can't remember any gnome programs though.

---

### Post by eyelessfade on 2007-04-19
> **Shane_linuxnewb said:**
> p.s. Is there such a thing as this "archive" of downloadable apps for ubuntu?

Synaptic

everything use apt. so a apt-cache search will also do the trick

---

### Post by Shane_linuxnewb on 2007-04-19
Thanks guys. I am gonna try dugas method first cuz its in chronalogical order lol. dugas, that code appears to work cept i dont have the java file. do u know where i can get it. 
Thanks

---

### Post by Scunizi on 2007-04-19
for MP3 conversion try ripperx in synaptic.  You might have to enable universe and/or multiverse.  You may also need lame..... an mp3 encoder.

---

### Post by raja on 2007-04-19
> **Shane_linuxnewb said:**
> Thanks guys. I am gonna try dugas method first cuz its in chronalogical order lol. dugas, that code appears to work cept i dont have the java file. do u know where i can get it. 
Thanks

You just have to type (or copy and paste) that code in the terminal. Ubuntu has a repository of all applications and the package you asked for will be downloaded from there. 'apt-get' is a package manager which will manage this for you. Synaptic is a similar program with a graphical front end. So you should look it up (System->Administration->Synaptic) and look at all the software that is available for installation with just a click. 

PS. If you have already typed that command in the terminal, you can check to see if the program was installed by typing ```
java -version
```in the terminal - this will show you the version of java you currently have.

---

### Post by Panzor on 2007-04-19
> **Shane_linuxnewb said:**
> It prompts me for my user name, once i enter this it prompts my password but i cannot enter one untill i hit the return key. Any ideas?


The reason why it does not show the password is to protect the number of characters should someone be looking over your shoulder. You should just type your password normally without worrying about characters showing up. There is actually a later java plugin that you can get here: [http://www.java.com/en/download/linux_manual.jsp?locale=en&host=www.java.com](http://www.java.com/en/download/linux_manual.jsp?locale=en&host=www.java.com)

There are already tutorials for installing this, so I won't bore you.

---

### Post by scanez on 2007-04-19
I suggest you consider upgrading to Feisty, which was just released. Then, note that Sound Juicer (which is installed by default in Feisty) can rip CDs to mp3s.

---

