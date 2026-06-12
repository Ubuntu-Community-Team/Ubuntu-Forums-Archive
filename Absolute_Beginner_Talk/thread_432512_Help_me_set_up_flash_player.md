---
title: "Help me set up flash player"
date: 2007-05-04
forum: Absolute Beginner Talk
---

### Post by destructo on 2007-05-04
Hi i have been copying this sticky article about how to install flash player on an amd64 machine and I can't seem to copy the files into the mozilla plugins folder. 

[http://ubuntuforums.org/showthread.php?t=341727&highlight=flash+64bit](http://ubuntuforums.org/showthread.php?t=341727&highlight=flash+64bit)


It says i don't have permission, so being a total noob with linux i know not what to do. Any ideas.

Thanks.

---

### Post by aysiu on 2007-05-04
Try this:
[http://www.psychocats.net/ubuntu/permissions#gui](http://www.psychocats.net/ubuntu/permissions#gui)

---

### Post by aysiu on 2007-05-04
Try this:
[http://www.psychocats.net/ubuntu/permissions#gui](http://www.psychocats.net/ubuntu/permissions#gui)

---

### Post by destructo on 2007-05-04
man/woman you are the best, thanks for the tip. I save the page as well to save me asking again. 

Ta.

---

### Post by destructo on 2007-05-04
no its not resolved, once again my noobness shines through. 

I did not add the link for alternative 1 to the repositories, how do i do this?

---

### Post by aysiu on 2007-05-04
I've changed the subject title back.

I don't know Italian, but it seems you paste these two commands in the terminal: ```
gpg --keyserver hkp://keyserver.ubuntu.com:11371/ --recv-keys 2C4C84CC && gpg --export --armor 2C4C84CC | sudo apt-key add -
wget http://janvitus.interfree.it/ubuntu/2C4C84CC.gpg -O- | sudo apt-key add -
``` And then edit your /etc/apt/sources.list: ```
sudo nano -B /etc/apt/sources.list
``` and paste these lines at the end: ```
deb http://janvitus.interfree.it/ubuntu/ feisty-janvitus main-amd64
deb-src http://janvitus.interfree.it/ubuntu/ feisty-janvitus main-amd64
``` and save (Control-X, Y, Enter) and finally ```
sudo apt-get update
```

---

### Post by destructo on 2007-05-04
i think i totally messed this one up aysiu, i have never done this before so thanks for helping me. 

this is what i get 

99% [Connecting to janvitus.interfree.it (213.158.72.68)]                      
99% [Connecting to janvitus.interfree.it (213.158.72.68)]
Err [http://janvitus.interfree.it](http://janvitus.interfree.it) feisty-janvitus Release.gpg
  Could not connect to janvitus.interfree.it:80 (213.158.72.68). - connect (113 No route to host)
Err [http://janvitus.interfree.it](http://janvitus.interfree.it) feisty-janvitus/main-amd64 Translation-en_US
  Could not connect to janvitus.interfree.it:80 (213.158.72.68), connection timed out
Err [http://janvitus.interfree.it](http://janvitus.interfree.it) feisty-janvitus/main-amd64 Translation-en_US
  Could not connect to janvitus.interfree.it:80 (213.158.72.68). - connect (113 No route to host)
99% [Connecting to janvitus.interfree.it (213.158.72.68)]



it just sits there, i think i may have stuffed it up.

---

### Post by destructo on 2007-05-04
is there a way you could run through it step by step for me. I seem to get confused as to what I'm supposed to do and when to do it. I will need specific instructions as i'm a windows nub.

---

