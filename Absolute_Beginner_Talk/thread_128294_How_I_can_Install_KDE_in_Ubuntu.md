---
title: "How I can Install KDE in Ubuntu?"
date: 2006-02-11
forum: Absolute Beginner Talk
---

### Post by wint on 2006-02-11
Hello! Have a nice time of day.:cool: 
I had install Ubuntu on my Laptop from DVD.
But i can't install KDE - desktop on it.

i type:
#sudo apt-get install kubuntu-desktop

But then i'll see on screen:
....
E: Couldn't find pakage kubuntu-desktop

What is wrong?:confused: 
P.S. I can't go to Internet from Leptop, so i can't install this package by Network
P.P.S. Sorry for my English;)

---

### Post by drfalkor on 2006-02-11
Add this at the bottom of your /etc/apt/source.list file:

sudo gedit /etc/apt/source.list 

(then copy and paste this: )

##kde 3.5
deb [http://kubuntu.org/packages/kde35](http://kubuntu.org/packages/kde35) breezy main

(save and exit)

sudo apt-get update

sudo apt-get install kubuntu-desktop, or you could try to:
sudo apt-get install kde

---

### Post by Lord Illidan on 2006-02-11
You have absolutely no internet access??

Having it would greatly facilitate installing KDE..

---

### Post by rudiz on 2006-02-11
sudo apt-get install kde-desktop

---

### Post by bartbes on 2006-02-11
It is ```
sudo apt-get kubuntu-desktop
``` but if you have no internet, first put in your install cd and put in ```
sudo apt-get cdrom add
``` and it will try to install as many as possible from the cd

---

### Post by Lord Illidan on 2006-02-11
But if he has the Ubuntu install cd, he won't be able to install KDE from it..

---

### Post by wint on 2006-02-11
I type:

#sudo apt-get cdrom add

but next i'll see

E: Invalid operation cdrom


P.S. I can go to Web by my "table" PC ... download files and copu them in my Laptop... What and where i must download to install KDE on my Ubuntu? Or i can do it from my Ubuntu-DVD?

---

### Post by wint on 2006-02-11
Oh! I forget! I download Kubuntu CD... but i don't wont to REINSTALL Linux, i want install KDE only... May be i can do it from KubuntuCD?

---

### Post by Lord Illidan on 2006-02-11
Good. 

Insert your Kubuntu CDROM, and type ```
sudo apt-cdrom add
```

---

### Post by gezzabob on 2006-02-11
[QUOTE=drfalkor]Add this at the bottom of your /etc/apt/source.list file:

sudo gedit /etc/apt/source.list

(then copy and paste this: )

##kde 3.5
deb [http://kubuntu.org/packages/kde35](http://kubuntu.org/packages/kde35) breezy main

(save and exit)

sudo apt-get update

sudo apt-get install kubuntu-desktop, or you could try to:
sudo apt-get install kde[/QUOTE]

sorry this may be the problem ...

sudo gedit /etc/apt/source.list is missing an s on the end of source shouldnt it be sudo gedit /etc/apt/sources.list
:-k

---

### Post by gezzabob on 2006-02-11
well just tried to gedit the source.list and it was blank, changed it to sources.list and got the file.

Sorry to point this out but it maybe causing some of the above problems....  Dont mean to be rude but just noticed it as I was browsing and well if it helped then all well and good please no hard feelings

---

### Post by wint on 2006-02-11
GREAT thanks to all!
I have do IT
So if you want to install KDE on Ubuntu and you have Kubuntu-CD/DVD this is solution for you:

#sudo apt-cdrom add

#sudo apt-get install kubuntu-desktop

_______________
KDE - Rulezzz;)

---

### Post by Lord Illidan on 2006-02-11
Though it is not going to be the most recent version of KDE. If you need KDE 3.5, its best if you have net access. Indeed, Ubuntu needs net access...

---

### Post by bartbes on 2006-02-11
Sorry that I typed apt-get cdrom it had to be apt-cdrom.. Just wanted to make clear that I was telling the same

---

