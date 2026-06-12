---
title: "Switch from U.S. to U.K."
date: 2006-09-30
forum: Absolute Beginner Talk
---

### Post by OptimusPrime on 2006-09-30
Could anybody tell me how to change where I download everything from (I want to download using uk. instead of us.?  I live in the U.S. but I don't want to use U.S., It doesn't work, so I like using U.K..

---

### Post by kewldude606 on 2006-09-30
Have you already installed ubuntu and want the updates downloaded from the UK?  Or are you just downloading the ubuntu install CD now?

---

### Post by OptimusPrime on 2006-09-30
I have Linux, and I want to download using UK.

---

### Post by CatKiller on 2006-09-30
You could change your /etc/apt/sources.list file so that all the entries were [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) I suppose.

---

### Post by OptimusPrime on 2006-09-30
Ok, I'm a little dumb tonight, but I tried doing that in the Konsol, and by going to the files.  It doesn't really let me do that.

---

### Post by CatKiller on 2006-09-30
Are you doing it as root or a normal user?

---

### Post by OptimusPrime on 2006-09-30
Ok, I am really a newbie.  I can tell you that i'm the admin. does that help?

---

### Post by nthdegree on 2006-09-30
Open up a terminal, then type the following:

sudo nano /etc/apt/sources.list

Then press enter and insert your password.  You will now be able to edit the /etc/apt/sources.list.  Change all the archive.ubuntu.com entries to gb.archive.ubuntu.com.

Then press ctrl+X and you can then proceed to save the file.

After you have left nano, type the following:

sudo apt-get update

You will now be downloading from the U.K after the process has completed.

---

### Post by wieman01 on 2006-09-30
Here is a source-list generator in case anybody is interested. The repositories work fine... never had a problem with it:

[http://www.ubuntulinux.nl/source-o-matic]("http://www.ubuntulinux.nl/source-o-matic")

---

### Post by CatKiller on 2006-09-30
What nthdegree said ;)

---

### Post by got_nix on 2006-09-30
I always just take the prefix for the country off so dns deals with that and figure which to get from. so instad of [http://us.reponame](http://us.reponame) i just have [http://reponame](http://reponame)

---

