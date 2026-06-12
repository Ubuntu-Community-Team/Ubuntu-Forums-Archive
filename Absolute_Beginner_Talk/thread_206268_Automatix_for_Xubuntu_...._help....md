---
title: "Automatix for Xubuntu .... help..."
date: 2006-06-29
forum: Absolute Beginner Talk
---

### Post by mourad on 2006-06-29
I am trying to install automatix for my Xubuntu, I tried to follow the instructions of installing at thier website but I encountered 2 problems;

1) When I tried to edit my sources.list with gedit, it told me that I can not save changes to the file, as it is a read only, however I am the administrator ?!?!?!!!!!

2) At the website the said, "Xubuntu users need to uncomment all the additional sources as well as add the automatix repository. " ...
 *** What are the additional scources, and how to UNCOMMENT them ???
*** How to add the automatix respository ????

Also, they said that automatix can be installed by synaptic as well, I think it is easier way, but I searched for automatix , but it gave me no results .... Should I use another word for search ??? or does it lay under what section that I can manually search for it ????

One final question, Is there anyway to select from the many capabilities that automatix offer, as there are many programming tools that I don't need !!!!

Thanks .... ;)

---

### Post by vseehua on 2006-06-29
1. by default you are running xubuntu/ubuntu as a normal user, the admin is the root account...

try typingthis into the terminal instead *```
sudo gedit /etc/apt/sources.list
``` *afterwards you can edit like normal

2. just remove the *#* character in front of each line which have *deb* behind it...

3. add this line[I][I]

```
deb [http://www.beerorkid.com/automatix/apt]("http://www.beerorkid.com/automatix/apt") dapper main
```[/I] 

[/I]in a new line into your sources.list. afterwards, start synaptic, reload and search for automatix...

---

### Post by confused57 on 2006-06-29
This is the way I installed Automatix:

[http://www.ubuntuforums.org/showthread.php?t=190025](http://www.ubuntuforums.org/showthread.php?t=190025)

You'll still want to enable all your repositories, as mentioned above.

---

