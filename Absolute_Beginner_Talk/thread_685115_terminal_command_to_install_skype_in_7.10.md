---
title: "terminal command to install skype in 7.10"
date: 2008-02-01
forum: Absolute Beginner Talk
---

### Post by 2manydrugsago on 2008-02-01
I am sure this info is posted elsewhere but my  brain is not letting me find it. could some one tell me how to get skype installed on 7.10?

---

### Post by taurus on 2008-02-01
Perhaps

```
sudo apt-get update
sudo apt-get install skype
```

---

### Post by 2manydrugsago on 2008-02-01
It will work .. i forgot I am updating with synaptic so  ill wait  but thanks

---

### Post by TJCIB on 2008-02-01
i would use the medibuntu repository then install it through synaptic.  

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

after you have the repository installed you can use the code if you want to do it from terminal.  

The other option is download the .deb file from skype.com, which I wouldn't recommend cause of the dependency issues.

another how to...a little outdated [https://help.ubuntu.com/community/Skype?action=show&redirect=SkypeHowto](https://help.ubuntu.com/community/Skype?action=show&redirect=SkypeHowto)

---

### Post by 2manydrugsago on 2008-02-01
this is what I get:


harlan@harlan-desktop:~$ sudo apt-get install skype
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package skype
harlan@harlan-desktop:~$ 


any ideas?

---

### Post by TJCIB on 2008-02-01
Did you add the repository?
After adding the repository, did you update it?

```
sudo apt-get update
```

[http://ubuntuguide.org/wiki/Ubuntu:Gutsy#How_to_add_extra_repositories](http://ubuntuguide.org/wiki/Ubuntu:Gutsy#How_to_add_extra_repositories)

---

### Post by 2manydrugsago on 2008-02-01
I did the update first should I do it again?

---

### Post by 2manydrugsago on 2008-02-01
how do i add the reposotories?

---

### Post by taurus on 2008-02-01
[http://medibuntu.org/packages.php](http://medibuntu.org/packages.php)
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by 2manydrugsago on 2008-02-01
i mean whats the repos for skype?
[www.skype.com/download/skype/linux/](www.skype.com/download/skype/linux/) ???

---

### Post by TJCIB on 2008-02-01
follow this link
[http://ubuntuguide.org/wiki/Ubuntu:G...a_repositories](http://ubuntuguide.org/wiki/Ubuntu:G...a_repositories)

it gives you step-by-step instructions for specifically adding the medibuntu repository (although it is an example of how to add most/all repositories).  There are a couple different ways shown, choose the one that you are most comfortable with.  They are all pretty self-explanatory.

be sure to update it once you've added medibuntu to your sources list

---

### Post by 2manydrugsago on 2008-02-01
thanks for the links  it worked now im workin!!

---

