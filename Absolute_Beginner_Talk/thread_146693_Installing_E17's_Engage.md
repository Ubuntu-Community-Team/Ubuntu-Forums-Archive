---
title: "Installing E17's Engage"
date: 2006-03-18
forum: Absolute Beginner Talk
---

### Post by gnu2ubuntu on 2006-03-18
I am attempting to install Engage using instructions with the excerpt below, but I don't know how to create the **/etc/apt/preferences** file indicated. 

> Let’s do it then by adding the following to sources.list:

deb [http://gefechtsdienst.de/uman/files/](http://gefechtsdienst.de/uman/files/) unstable main

Next we need to edit or create /etc/apt/preferences with:

Package: enlightenment
Pin: version 0.16.999*
Pin-Priority: 999

Package: enlightenment-data
Pin: version 0.16.999*
Pin-Priority: 999 

Can anyone walk a newbie thru the procedure for creating this file. In general I open up my Home folder and click on "file", "create folder". I tried this within **/etc/apt** but it doesn't allow me to create a folder. I am thinking this is something I have to do in a terminal, however I am not really adept at using the command line [having recently migrated from the "point and click" windows mindset].
Any and all help will be greatly appreciated.

---

### Post by FizDev on 2006-03-18
Just type in the terminal :
```
sudo mkdir /etc/apt/preferences
```

Edit: You could also type in the terminal :
```
gksudo nautilus
```
It will open nautilus but now you'll have root privileges so you should be able to create the folder without any problems.

---

### Post by gnu2ubuntu on 2006-03-18
that eazy? :) Thanks FizDev!

---

### Post by gnu2ubuntu on 2006-03-18
next hurdle... I've created /etc/apt/preferences. how do I edit it with

Package: enlightenment
Pin: version 0.16.999*
Pin-Priority: 999

Package: enlightenment-data
Pin: version 0.16.999*
Pin-Priority: 999

?

---

### Post by FizDev on 2006-03-18
Oh, it wasn't a folder they wanted... then in that case.

```
cd /etc/apt
```
```
sudo gedit
```
Put the text you want in it, save and exit.

Or you could also do :
```
cd /etc/apt
```
```
sudo nano
```
put the text, press Ctrl+X, Y, then put "preferences" as name.

Could you please put the address of the site where you follow directions?

---

### Post by gnu2ubuntu on 2006-03-18
ok... now I'm a little confused becuz they say to create or edit /etc/apt/preferences. here is the url.

[http://www.macewan.org/category/ubuntu-linux/]("http://www.macewan.org/category/ubuntu-linux/")

---

### Post by FizDev on 2006-03-18
Hmm... first of all, do you have Breezy or Dapper?
These directions are for Dapper so..

---

### Post by gnu2ubuntu on 2006-03-18
I have Dapper

---

### Post by FizDev on 2006-03-18
Ok, in that case, you'll have to do what I told you before :
```
sudo gedit
```
Paste this text into the new file
> 
Package: enlightenment
Pin: version 0.16.999*
Pin-Priority: 999

Package: enlightenment-data
Pin: version 0.16.999*
Pin-Priority: 999
then save it in /etc/apt as "preferences"

---

