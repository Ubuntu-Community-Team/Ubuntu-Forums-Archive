---
title: "problem launching synaptics package manager"
date: 2007-09-05
forum: Absolute Beginner Talk
---

### Post by antisocialist on 2007-09-05
i went to open synaptics package manager and got this error

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

how do i fix this?

---

### Post by diatribe on 2007-09-05
sudo dpkg --configure -a

---

### Post by Seisen on 2007-09-05
> **diatribe said:**
> sudo dpkg --configure -a

You need to run it in the terminal.

---

### Post by ehamman on 2008-01-12
Hi,
I'm a noob as well, and am very keen to get away from Windows.  However, I am still getting to know the ropes and do therefor not know whether I've somehow managed to mess up in a mjajor way.

I'm experiencing the same problem when I try to launch Synaptics package manager, and have tried to run the command suggested:
  sudo dpkg --configure -a
Prior to executing, it  asks me for a sudo password. I did not set one up and have no idea what this is.  So, when I press enter it seems to continue, but after logging on it does not solve the problem.

A quick history:
I installed Ubuntu last night (Toshiba J100 Laptop), downloaded a couple patches and also a NVidea "Restricted Driver" activated to optimise the graphics.  This worked fine.
Then I tried to get my second (Acer) monitor to work.  I somehow managed to get my Toshiba stuck on  640x480 resolution and could not get the "Screen and Graphics" app to run to fix it.  All the other stuff seemed to work.
So I saw I had to run
  sudo dpkg -reconfigure -phigh xserver-xorg 
I got the same request for a password. But this did not seem to work either.  By know I was very "fond" of the start up screen and process, so I went to untick the NVidia option in the Restricted Driver Manager.
 
Whether it was a combo of this untick, another sudo run or just my swearing, but hey presto - the computer started up with graphics that did not require cokebottle bottom to read the text. 
I fixed the screen resolution for my Laptop and then tried to run my Restricted Driver Manager, which did not work and then tried to run the Synaptics package manager, which also did not work.

So, here we are.  Big please and thank you for your help.

---

### Post by bapoumba on 2008-01-12
When using sudo, your user gains administrative privileges. When entering the password, nothing appears on screen for security reasons. Type your user login password and hit <enter>.

What is the exact error you are getting? Could you please post the output to:
```
sudo apt-get update
```

---

### Post by pisewip on 2008-01-12
if you installed ubuntu you need to give a password when you insert your personal data, like user name, client name.
That is the sudo password.

---

### Post by ehamman on 2008-01-12
Thanks for the feedback.
The error I got was exactly the same as for the original post.

  E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
  E: _cache->open() failed, please report.

I will try to post it with the:
  sudo apt-get update

Thanks a again.

PS I like strawberries too!

---

### Post by zipperback on 2008-01-12
Are you running this from the LiveCD or from an installation of Ubuntu on your hard drive?

- zipperback
:popcorn:

---

### Post by bapoumba on 2008-01-13
@ ehamman: have you tried:
```
sudo dpkg --configure -a
```

---

