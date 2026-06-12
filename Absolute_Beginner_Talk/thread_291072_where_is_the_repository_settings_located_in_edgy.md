---
title: "where is the repository settings located in edgy?"
date: 2006-11-02
forum: Absolute Beginner Talk
---

### Post by noktekniq on 2006-11-02
where do i get the repository option in edgy? 
i'm trying to follow this thread [http://ubuntuforums.org/showthread.php?t=263851](http://ubuntuforums.org/showthread.php?t=263851)

but i'm having prob with the beginning where it says., repos. i'm a new linux/ubuntu user.please help thanks

---

### Post by seshomaru samma on 2006-11-02
In Ubuntu the repositories are in /etc ,in the /apt directory
To edit them try:
```
sudo gedit /etc/apt/sources.list
```
and add the new sources at the end of the page

---

### Post by NeoLithium on 2006-11-02
Well, if you're using GNOME, you can go to System -> Administration and click on Synaptic Package Manager.  Go to settings and repositories.

To use the command line, you can type ```
sudo gedit /etc/apt/sources.list
```

---

### Post by bmathis on 2006-11-02
I was typing and next thing you know there is 2 people who beat me... ohh well!!!



you can either go to System > Administration > Software Properties and enable all the repositories there or you can open a terminal and enter the following command:
> sudo nano /etc/apt/sources.list
and uncomment [remove all #] all repositories and save the file. Then run 
> sudo apt-get update

---

### Post by noktekniq on 2006-11-02
geez so confusing.

---

### Post by NeoLithium on 2006-11-02
It just takes practice to get used to it. You'll find that not too long from now, quite a few things become second nature.

---

