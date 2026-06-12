---
title: "New Ubuntuer wants to play Doom3 + expansion!"
date: 2008-03-12
forum: Absolute Beginner Talk
---

### Post by peterkeyani on 2008-03-12
Hello,

I am very new to Ubuntu and not that good with Windows XP either. Saying that, thanks to old posts on the forum I did manage to dual-install Gusty 7.1 and XP SE on my dual-core amd64 PC and get my favourite video player VLC player to install and work, so thanks for that!

I understand from these forums that one of my favourite games Doom 3 - and its expansion pack - can be easily installed and played on Gusty 7.1. However, I fall at the first step. I visited ID's site and found the download item which consists of 3 hyper links. But when I clicked on them, I just brought up a page of code?

Sorry for the stupid question but what am I supposed to do with it? Copy and paste it somewhere?

Thanks to all!

Pete
_____

---

### Post by Sef on 2008-03-12
Could you provide a link to that page?  Thank you.

---

### Post by mjwhitfield on 2008-03-12
theres a package in the repo's for it.

AFAIK you just download that, then it asks for the CDs and install itself.

---

### Post by peterkeyani on 2008-03-12
Thanks for replying

The link is [ftp://ftp.idsoftware.com/idstuff/doom3/linux/](ftp://ftp.idsoftware.com/idstuff/doom3/linux/)

I was directed to it by [https://help.ubuntu.com/community/Doom3](https://help.ubuntu.com/community/Doom3)

Pete

---

### Post by peterkeyani on 2008-03-12
> **mjwhitfield said:**
> theres a package in the repo's for it.

AFAIK you just download that, then it asks for the CDs and install itself.

I'm sorry what does this mean?  What are "the repos"?

Thanks
Pete

---

### Post by jken146 on 2008-03-12
You need doom3-linux-1.3.1.1304.x86.run -- right click on it and choose Save As.  Save it to your Desktop.

Then, open up a terminal (Applications -> Accessories -> Terminal) and copy & paste this command: ```
./Desktop/doom3-linux-1.3.1.1304.x86.run
```

---

### Post by patrickaupperle on 2008-03-12
I don't know if its in the repos or not, but the repos are what you access for software. You can access them by going to applications and add/remove ... or system, administration, synaptic package manager.

---

### Post by peterkeyani on 2008-03-12
> **jken146 said:**
> You need doom3-linux-1.3.1.1304.x86.run -- right click on it and choose Save As.  Save it to your Desktop.

Then, open up a terminal (Applications -> Accessories -> Terminal) and copy & paste this command: ```
./Desktop/doom3-linux-1.3.1.1304.x86.run
```


Downloaded it OK but when I copy and paste I get:

 ./Desktop/doom3-linux-1.3.1.1304.x86.run
:confused:
bash: ./Desktop/doom3-linux-1.3.1.1304.x86.run: Permission denied

---

### Post by xravexheavenx on 2008-03-12
sudo it.

---

### Post by Therion on 2008-03-12
Copy and Paste in a Terminal:

```
sudo ./Desktop/doom3-linux-1.3.1.1304.x86.run
```

---

### Post by peterkeyani on 2008-03-12
> **Therion said:**
> Copy and Paste in a Terminal:

```
sudo ./Desktop/doom3-linux-1.3.1.1304.x86.run
```

Thanks. I get 

sudo: ./Desktop/doom3-linux-1.3.1.1304.x86.run: command not found

---

### Post by peterkeyani on 2008-03-12
> **Therion said:**
> Copy and Paste in a Terminal:

```
sudo ./Desktop/doom3-linux-1.3.1.1304.x86.run
```

Thanks but I get

pete@ubuntu:~$ sudo ./Desktop/doom3-linux-1.3.1.1304.x86.run
sudo: ./Desktop/doom3-linux-1.3.1.1304.x86.run: command not found
pete@ubuntu:~$

---

### Post by jken146 on 2008-03-12
Are you sure you downloaded it to the desktop?

Also, check that the file is executable.  You can manke it executable with ```
chmod +x Desktop/doom3-linux-1.3.1.1304.x86.run
```

---

### Post by peterkeyani on 2008-03-12
> **Therion said:**
> Copy and Paste in a Terminal:

```
sudo ./Desktop/doom3-linux-1.3.1.1304.x86.run
```

I get sudo: ./Desktop/doom3-linux-1.3.1.1304.x86.run: command not found

Thanks:confused:

---

### Post by peterkeyani on 2008-03-12
> **jken146 said:**
> Are you sure you downloaded it to the desktop?

Also, check that the file is executable.  You can manke it executable with ```
chmod +x Desktop/doom3-linux-1.3.1.1304.x86.run
```

Thanks

I get

pete@ubuntu:~$ sudo ./Desktop/doom3-linux-1.3.1.1304.x86.run
sudo: ./Desktop/doom3-linux-1.3.1.1304.x86.run: command not found
pete@ubuntu:~$ chmod +x Desktop/doom3-linux-1.3.1.1304.x86.run
pete@ubuntu:~$ sudo: ./Desktop/doom3-linux-1.3.1.1304.x86.run
bash: sudo:: command not found
pete@ubuntu:~$ 

The file is sitting on the desktop. Might it not have downloaded coorectly?

Pete

---

### Post by PmDematagoda on 2008-03-12
Move to the Desktop with:-
```
cd ~/Desktop
```
and then post the output of:-
```
ls
```

---

### Post by mjwhitfield on 2008-03-12
sudo ./Desktop/doom3-linux-1.3.1.1304.x86.run

do not type : after sudo

---

### Post by peterkeyani on 2008-03-12
> **mjwhitfield said:**
> sudo ./Desktop/doom3-linux-1.3.1.1304.x86.run

do not type : after sudo

Thanks
still getting sudo: ./Desktop/doom3-linux-1.3.1.1304.x86: command not found:confused:

1) I downloaded the file from the id site using "Download as link":  was this right?

2) I have a amd64 dual-core PC; does that have any bearing?

Thanks again

---

### Post by PmDematagoda on 2008-03-12
1) I think you may have made a mistake there.

2) That will make no difference, it depends on your OS itself.

Please post the result of ls when you are in the Desktop directory, then we can make sure if you downloaded the file at all.

---

### Post by peterkeyani on 2008-03-12
> **PmDematagoda said:**
> 1) I think you may have made a mistake there.

2) That will make no difference, it depends on your OS itself.

Please post the result of ls when you are in the Desktop directory, then we can make sure if you downloaded the file at all.

Thanks

This is what I get

pete@ubuntu:~$ cd ~/Desktop
pete@ubuntu:~/Desktop$ ls
doom3-linux-1.3.1.1304.x86.run
pete@ubuntu:~/Desktop$

---

### Post by PmDematagoda on 2008-03-12
The file is indeed there, did you try executing the file now?

---

### Post by peterkeyani on 2008-03-12
> **PmDematagoda said:**
> The file is indeed there, did you try executing the file now?

I entered into terminal

 pete@ubuntu:~$ sudo ./Desktop/doom3-linux-1.3.1.1304.x86.run
[sudo] password for pete:
sudo: ./Desktop/doom3-linux-1.3.1.1304.x86.run: command not found
pete@ubuntu:~$ 

any ideas?:confused:

Pete

---

### Post by peterkeyani on 2008-03-12
> **PmDematagoda said:**
> The file is indeed there, did you try executing the file now?

also tried this with this result:


Quote:
Originally Posted by eragon100 View Post
Taht has nothing to do with sudo since it's in YOUR home folder and YOU are the file owner. You simply have to make it executable.

1. Right-click on it

2. select Properties

3. go to permissions tab

4. tick the box that says: allow executing file as program

5. click ok

Now you can run it either from terminal or bu double-clicking on it and selecting run in terminal
Thanks
That sort of worked
Got a "Installation Path" blue box which said " Please enter the installation path usr/local/games/doom3"
The options were "ok" or "cancel": OK was not accepted!

any ideas?
Pete
________:confused:

---

