---
title: "Installing Software"
date: 2007-10-24
forum: Absolute Beginner Talk
---

### Post by mdpalow on 2007-10-24
Hello Everyone,

I have an application I downloaded from the web that I want to install. What I want to know is...

Should the application be installed by me as a user or as an administrator (ie. sudo)?

I'm the only one on the computer, so my account is the FIRST account.

It's a .tar file that I need to extract.

Common sense is telling me I have to do it as an administrator because in order to use synaptic you have to put in a password to install an app.

So, if that's true - can I just put 'sudo' in front of the "tar xvzf /path/to/file.tar.gz" and type it like:

sudo tar xvzf /path/to/file.tar.gz

Complete NOOB, so pls don't assume anything if and when replying. :)

Thanks

---

### Post by Maestro23 on 2007-10-24
Installing Software in Ubuntu:
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

Once you extract that tarball, it should have a Readme/Install doc inside the extracted folder.

What are you trying to install by the way?

---

### Post by taurus on 2007-10-24
```
cd ~/Desktop
tar xvzf filename.tar.gz
cd filename
sudo aptitude update
sudo aptitude install build-essential checkinstall
./configure
make
sudo make checkinstall
```

[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

---

### Post by aysiu on 2007-10-24
Are you absolutely sure it needs to be downloaded separately? Most popular software can be installed via the package manager. See the above links (monkeyblog and psychocats) for more details on the *easy* ways to install software.

---

