---
title: "Update Manager Will NOT Work"
date: 2010-04-19
forum: Apple Hardware Users
---

### Post by xxander on 2010-04-19
I have used Update Manager once, but now when I go to it, it displays this message after failing: W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 3F2A5EE4B796B6FE   .  (period not included)  How do I fix this and get my updates?  

Additional Info: MacBook running Desktop version of Ubuntu with a Netbook version add-on.  Thanks guys!:)

---

### Post by linuxopjemac on 2010-04-20
In the console, try this:

```
sudo gpg --keyserver keyserver.ubuntu.com --recv 3F2A5EE4B796B6FE
sudo gpg --export --armor 3F2A5EE4B796B6FE | sudo apt-key add -
```

[https://help.ubuntu.com/community/Repositories/Ubuntu#Authentication%20Tab](https://help.ubuntu.com/community/Repositories/Ubuntu#Authentication%20Tab)

---

### Post by xxander on 2010-04-21
I will try this tonight!  Thanks for your quick response.

---

### Post by xxander on 2010-04-21
> **linuxopjemac said:**
> In the console, try this:

```
sudo gpg --keyserver keyserver.ubuntu.com --recv 3F2A5EE4B796B6FE
sudo gpg --export --armor 3F2A5EE4B796B6FE | sudo apt-key add -
```[https://help.ubuntu.com/community/Repositories/Ubuntu#Authentication%20Tab]("https://help.ubuntu.com/community/Repositories/Ubuntu#Authentication%20Tab")


I tried this, and when I entered the first 'sudo', I was given an error..

---

### Post by linuxopjemac on 2010-04-22
are are in the sudoers list ?

---

### Post by xxander on 2010-04-23
> **linuxopjemac said:**
> are are in the sudoers list ?


What is that?  And also, it changed from giving me an error to just downloading them without any confirmation that they were installed correctly.  When I go to download it again, it always downloads the same 48 files...

---

### Post by linuxopjemac on 2010-04-23
then it's working correctly.

---

### Post by xxander on 2010-04-23
Are you sure?  Because my friend has his do something different.  Why would it have to download it a million times?

---

### Post by mmalone21 on 2010-04-23
It is not downloading the same files it is the just checking the repositories for updates.

---

### Post by xxander on 2010-04-24
Okay.  This just seems very odd because the first time I downloaded updates, it did not do this.  But now the second time around, it's acting weird.

---

### Post by avtolle on 2010-04-24
Need to ask: what happens when you do ```
sudo apt-get update
sudo apt-get upgrade
```from the terminal?

---

### Post by xxander on 2010-04-25
I've tried this, but I guess I'll just wait 4 days until 10.04 is released.  Thanks for all of your help everybody!

---

### Post by linuxopjemac on 2010-04-26
> **avtolle said:**
> Need to ask: what happens when you do ```
sudo apt-get update
sudo apt-get upgrade
```from the terminal?

You update the repository and then you install all newer packages.

---

