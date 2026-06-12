---
title: "Beryl dependencies broken ... Macbook Pro"
date: 2007-04-22
forum: Apple Intel Users
---

### Post by rscow on 2007-04-22
Hi, I just managed to install Feisty on my Macbook Pro.  I am triple booting with OS X.4.9 and Vista Ultimate.  I had some problems getting Feisty installed.  Eventually had to install Edgy and then upgrade via apt-get.  

Now, I'm trying to install Beryl and when I either use apt or symantic, I get a message that the dependencies are broken and I can't install.  I may possibly not have all the right sources in /etc/apt/sources.list  but I have these that directly relate to beryl.  GPG keys are installed.

deb [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) edgy main
deb [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) edgy beryl-svn
deb-src [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) edgy beryl-svn

ANyone have any better luck?  I have looked at several howto's, etc. but haven't had any luck yet.

---

### Post by russell.h on 2007-04-22
All those lines that say edgy, change them to say feisty (assuming you are running fesity, which is what I understood).

---

### Post by rscow on 2007-04-23
Oh, my.  How could I have missed that.  that was stupid.  I'll change them, and try again.  Thanks.
I feel like an Ubuntidiot.

Roger

---

### Post by rscow on 2007-04-23
That let me install Beryl, Emerald, etc., but still no Beryl when I start up the session.  I am not sure what I have done wrong.  Or if there is anything wrong.

I will post a new message, so that I can get more feedback on the success of users with Beryl.

Roger

---

### Post by ronocdh on 2007-04-23
> **rscow said:**
> That let me install Beryl, Emerald, etc., but still no Beryl when I start up the session.  I am not sure what I have done wrong.  Or if there is anything wrong.

I will post a new message, so that I can get more feedback on the success of users with Beryl.

Roger
[This]("http://ubuntuforums.org/showthread.php?t=399643&highlight=x200m") is what I used to get Beryl running on my MBP. It shows how to create the necessary scripts to have effects at login.

---

