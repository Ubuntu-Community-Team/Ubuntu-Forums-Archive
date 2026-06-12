---
title: "[SOLVED] Very new to this"
date: 2007-08-31
forum: Absolute Beginner Talk
---

### Post by ninja99 on 2007-08-31
Sorry if this has been posted before but I have been in a hurry with school just starting and haven't had much time to search the forums.  I have a couple of problems:

I can't get in as root. (sorta don't know how to do it)

When I try to download programs such as audacity, it says this program conflicts with existing ones.  When I go to synaptic package manager to remove them, it says they are a vital part of the system and removing them may result in system failure.  Is it still ok to remove them?

when I go to software resources to add a reposity that was in the error message, I type it in and the add source button still does not light up to allow me to add it.

when I try to download new programs like azureus, amarok, and others, it says I am having some trouble with repositories, I'm not sure how to get the ones I need or where to get them from.  (example)  when I try to download amarok, it comes up with a box that says cannot download all repository indexes. This is when I go to applications, add remove.  

Again I am very sorry if this has been an issue with someone else and has been posted.

Thanks

---

### Post by diatribe on 2007-08-31
to run a program with root access use sudo, if you need a root prompt use sudo -i

---

### Post by dca on 2007-08-31
What happens when you go into Synaptic under -> system ->administration -> synaptic and press the 'reload' button???  
 
The only time I ever had trouble w/ the 'add/remove' was when I lost my connection to the internet...  Wait a minute, did you use Automatix at all?

---

### Post by ninja99 on 2007-08-31
No, I have not used automatix, it wont load it.Hitting the reload button does nothing.  I have repository problems.  It wont let me add the ones I think I need and I don't know where to get the ones I need from. 

When I hit reload it says I cannot download all repository indexes.  it says the ones I am missing are as follows:

http://us.archive.ubuntu.com/ubuntu/dists/feisty/main/binary-i386/Packages.gz<z>   The z at the end is to show it as normal, that's not part of the actual link
http://us.archive.ubuntu.com/ubuntu/dists/feisty/main/source/Sources.gz<z>
http://us.archive.ubuntu.com/ubuntu/dists/feisty/mainbinary-i386/Packages.gz<z>

after each of those it says Sub-process gzip returned an error code (1)

What does this mean?

---

### Post by diatribe on 2007-08-31
what is the exact error

---

### Post by ninja99 on 2007-08-31
I couldn't get a screenshot of it right now but it goes as follows:

Could not download all repository indexes

The repository might be no longer available or could not be contacted because of network problems.  If available an older version of the failed index will be used.  Otherwise the repository will be ignored.  Check your network connection and the correct writing of the repository address in the preferences.

Then in a box the websites I just typed are in there with the error code I mentioned behind them.

---

### Post by diatribe on 2007-08-31
are they reposotories you added or the defaults?  post a copy of your /etc/apt/sources.list

---

### Post by ninja99 on 2007-08-31
They are the defualts and when I type /etc/apt/sources.list it says permission denied.  I then typed sudo -i /etc/apt/sources.list and it showed up 

/etc/apt/sources.list:  line 4:  deb: command not found
/etc/apt/sources.list:  line 5:  deb-src:  command not ofund
/etc/apt/sources.list:  line 9:  deb: command not found
/etc/apt/sources.list:  line 10:  deb-src:  command not ofund
/etc/apt/sources.list:  line 17:  deb: command not found
/etc/apt/sources.list:  line 18:  deb-src:  command not ofund
/etc/apt/sources.list:  line 25:  deb: command not found
/etc/apt/sources.list:  line 26:  deb-src:  command not ofund
/etc/apt/sources.list:  line 38:  deb: command not found
/etc/apt/sources.list:  line 39:  deb-src:  command not ofund
/etc/apt/sources.list:  line 40:  deb: command not found
/etc/apt/sources.list:  line 41:  deb-src:  command not ofund
/etc/apt/sources.list:  line 42:  deb: command not found
/etc/apt/sources.list:  line 43:  deb-src:  command not ofund
 /etc/apt/sources.list:  line 44:  deb: command not found

---

### Post by diatribe on 2007-08-31
man type cat /etc/apt/sources.list and post the result

---

### Post by PaulFr on 2007-08-31
Please post output of ```
grep '^deb' /etc/apt/sources.list
```

---

### Post by zyth on 2007-08-31
Type this;

> 
less /etc/apt/sources.list


and paste the output here.

---

### Post by ninja99 on 2007-08-31
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty main restricted
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-updates main restricted
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) feisty main

---

### Post by diatribe on 2007-08-31
I assume you are connected to the internet, are you behind a proxy or firewall?

---

### Post by ninja99 on 2007-08-31
I am but have no problem connecting to things.  I am running two pc's, one with xp and the other with ubuntu.  they both connect to the internet through a network I built in my basement.  they are both on the same network.

---

### Post by alienexplorers on 2007-08-31
Did you try sudo aptitude update and the sudo aptitude upgrade.  If errors pop up can you post them here.

---

### Post by diatribe on 2007-08-31
you have to edit your proxy settings in synaptic I believe

---

### Post by ninja99 on 2007-08-31
The same error that I posted about the add/remove apps showed up.  the same sites, it said sub-process gzip returned an error code.  

err [http://us/archive.ubuntu.com](http://us/archive.ubuntu.com) feisty/main Sources Sub-Process gzip returned an error code (1)
err [http://us/archive.ubuntu.com](http://us/archive.ubuntu.com) feisty/main Packages Sub-Process gzip returned an error code (1)

---

### Post by diatribe on 2007-08-31
it should be [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) ;p

---

### Post by ninja99 on 2007-08-31
there is a dot between the two, I typed that and did it wrong.  I copied the first one so it showed up again.

---

### Post by PaulFr on 2007-09-01
Please run the following command ?```
sudo rm /var/cache/apt/archives/partial/*
```Then see if the errors recur. Is your net connection stable ?

---

### Post by diatribe on 2007-09-01
solved! :D

---

### Post by Paul133 on 2007-09-01
Go to Thread Tools -> Mark Thread as Solved, please.

---

### Post by ninja99 on 2007-09-01
Thanks so much guys.  Everything is working good.  someone said something about automatix, when I looked to do the perfect desktop as listed in the forums it said to use automatix.  Is there something wrong with using it?

---

