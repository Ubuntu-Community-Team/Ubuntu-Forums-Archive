---
title: "[SOLVED] Unknown Error"
date: 2007-07-02
forum: Absolute Beginner Talk
---

### Post by acowboydave on 2007-07-02
Hello, when I run apt-get update or aptitude update, I am getting this error at the end.  
I installed ubuntustudio with Feisty already installed. Teh error reads error: http:// archive.ubuntustudio.org feisty Release: Unknown error executing gpgv. Any ideas

---

### Post by cogadh on 2007-07-02
Did you already download and install the GPG key for the Ubuntu Studio repository?

---

### Post by acowboydave on 2007-07-02
No I don't know how to do that.

---

### Post by cogadh on 2007-07-02
It looks like you also have the Ubuntu Studio repository added incorrectly. Run this in a terminal:
```
sudo su -c 'echo deb http://archive.ubuntustudio.org/ubuntustudio feisty main >> /etc/apt/sources.list'
wget -q http://archive.ubuntustudio.org/ubuntustudio.gpg -O- | sudo apt-key add - && sudo apt-get update
```
That will add the repository correctly and install the GPG key. You should then be able to install Ubuntu Studio packages without the error.

---

### Post by acowboydave on 2007-07-02
Hello, tried twice  the message at the end reads as follows..w: GPG error: [http://archive.ububtustudio.org](http://archive.ububtustudio.org) feisty release: unknown error executing gpgv.  then it follows you might want to run apt-get update to resolve these problems. I ran this command on the install and am running ubuntustudio now. Just unable to update  I should of said code, not command, i used that code to install

---

### Post by cogadh on 2007-07-02
I'm sorry, I didn't really understand that at all. Are you saying you were able to do what you needed to or are you still having a problem?

---

### Post by acowboydave on 2007-07-02
sorry about that, yes I am still having a problem. Did what you said to do and got back the same message, seems I am having problems with connecting to the site. tried update manager and got a error there also. It states" Could not download all repository indexes". So it just could be in communications,

---

### Post by cogadh on 2007-07-03
It appears that the repository may be offline, I'm not getting any response from it. The GPG key is definitely accessible though, which is a little weird, since it is hosted on the same site. I'm guessing the site itself is up, but the repository might not be. Try again later, maybe it will be back up.

---

### Post by acowboydave on 2007-07-03
Thanks for your help and time, that is why the Ubuntu community is so great, helping others. Uninstalled Ubuntustudio and reinstalled Ubuntu. So the problem is solved. Lol, gezz!  Thanks again!:D

---

