---
title: "Xfire on gaim"
date: 2005-12-31
forum: Absolute Beginner Talk
---

### Post by appdx on 2005-12-31
I did a forum search and found that I can install this plugin from source, so i downloaded the source

when I went
~/Desktop/gaim-xfire-0.5.8.tar.gz ./configure it says  /home/appdx/Desktop/gaim-xfire-0.5.8.tar.gz: command not found

so then i tried configure ~/Desktop/gaim-xfire-0.5.8.tar.gz and it says command not found again, I'm guessing that configure isn't a command in the terminal so if anyone can help me build this gaim plugin from source that would be a great help. Also, I already got the gaim-dev package from synaptic so it should be ready to go.

Thanks,
[app.dx]

---

### Post by mztriz on 2005-12-31
I don't know if this is your problem or not but try
```
sudo apt-get install build-essential
```
and then try to compile it

---

### Post by appdx on 2005-12-31
Yes, that was my problem, also I didn't to tar -xvf gaim-xfire-0.5.8.tar.gz first to extract it. Thanks.

---

### Post by appdx on 2005-12-31
ok, so after that i did ./configure, make, make install then restarted gaim and I don't see xfire in the drop down box when i go to add a new account

---

### Post by mztriz on 2005-12-31
try going to tools>plugins first and see if you can check it there, then try to add the account.

---

### Post by appdx on 2005-12-31
So, I got xfire to appear in the drop down menu for accounts, but when i try to log in it says version is too old...I tried changing it to 45 from 41 in the options but that didn't work either...anyone help?

---

### Post by Griff on 2005-12-31
Try version 49.  It's working for me right now.  I don't remember what the default version is, but I just kept climbing up until it worked.

---

### Post by appdx on 2005-12-31
I changed it to 49 and it works! Thanks!!!

---

### Post by Algorab on 2006-02-08
I'm having the same problem..but I can't really follow what happened here :).
I have stored the tar.gz file on the desktop. What are the next steps?

---

### Post by nik on 2006-02-08
In terminal:
```

cd Desktop
tar -xvf gaim-xfire-0.5.8.tar.gz
cd gaim(whatever)
./configure
make
sudo make install

```

---

### Post by Algorab on 2006-02-08
Thanks man! Xfire up and running!!! :D

---

### Post by centy on 2006-02-08
Hello, I typed these commands

```
cd Desktop
tar -xvf gaim-xfire-0.5.8.tar.gz
cd gaim(whatever)
./configure
make
sudo make install
```

but I am presented with the following error

configure: error: cannot find install-sh or install.sh in . ./.. ./../..

any ideas? Im new : )

---

### Post by centy on 2006-02-15
bump, it's been a week.
I'm sure one of the more experienced of you will be able to spot immediately what i'm doing wrong :(

---

### Post by appdx on 2006-02-18
Ok, I'm going to tell you step by step how i did this.
first, what you need:
-Xfire plugin, I got it from [http://www.fryx.ch/xfire/](http://www.fryx.ch/xfire/)
-gaim-dev package

_**Step 1:**_
Download the Xfire tar.gz from the link above to your _DESKTOP_ (I assume that's where the .tar.gz file is)
type "cd ~/Desktop" in terminal (without quotes)
extract it by typing "tar -xvf gaim-xfire-0.5.8.tar.gz" in terminal (again without quotes)
type "sudo apt-get install gaim-dev" in terminal
type "./configure --with-gaim=/path/to/gaim --prefix=/usr" (for me path to gaim was /usr/bin/gaim)
*note* If this step didn't work, you may need to do "sudo apt-get install build-essential" in terminal
type "make then sudo make install" in terminal
_**Step: 2**_
Restart gaim
you should now see Xfire in the drop down box to create a new account
make sure the version is correct in the "show more options" thing in gaim (I used 52)
Put in your account infor and login!

FINISHED!!!
This is what worked for me, I hope you find it useful.

---

