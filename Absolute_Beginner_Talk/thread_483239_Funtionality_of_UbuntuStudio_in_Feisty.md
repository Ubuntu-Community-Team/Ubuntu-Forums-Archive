---
title: "Funtionality of UbuntuStudio in Feisty?"
date: 2007-06-24
forum: Absolute Beginner Talk
---

### Post by ts51 on 2007-06-24
Is there a way to simply type something in the terminal and get all the programs that UbuntuStudio has without actually install UbuntuStudio? I just discovered the flavor of Ubuntu, but I don't feel like installing it over my current Feisty, as it is all set up the way I want. Also, if there is a place where I can get the theme and wallpaper, please let me know. 

I am assuming that UbuntuStudio is Open Source...


thanks,
ts51

---

### Post by qamelian on 2007-06-24
> **ts51 said:**
> Is there a way to simply type something in the terminal and get all the programs that UbuntuStudio has without actually install UbuntuStudio? I just discovered the flavor of Ubuntu, but I don't feel like installing it over my current Feisty, as it is all set up the way I want. Also, if there is a place where I can get the theme and wallpaper, please let me know. 

I am assuming that UbuntuStudio is Open Source...


thanks,
ts51

Just add the Ubuntu Studio repos to your sources.list file and do ```
sudo aptitude update
```. Then you'll be able to install all the Ubuntu Studio apps without doing a full reinstall.

---

### Post by overdrank on 2007-06-24
> **ts51 said:**
> Is there a way to simply type something in the terminal and get all the programs that UbuntuStudio has without actually install UbuntuStudio? I just discovered the flavor of Ubuntu, but I don't feel like installing it over my current Feisty, as it is all set up the way I want. Also, if there is a place where I can get the theme and wallpaper, please let me know. 

I am assuming that UbuntuStudio is Open Source...


thanks,
ts51

Hi I believe this is what you need
[http://www.ubuntustudio.org/downloads](http://www.ubuntustudio.org/downloads)
good luck!:popcorn:

---

### Post by Sidzone on 2008-07-12
I have the update to Studio but I get error messages during Synaptic update telling me that the repository can't be accessed.  Has the support link for Studio been changed recently?  I just installed Studio from Feisty about a week ago. This is the error I keep getting:

Could not download all repository indexes

The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.

Failed to fetch [http://archive.ubuntustudio.org/ubuntustudio/dists/feisty/main/binary-amd64/Packages.gz](http://archive.ubuntustudio.org/ubuntustudio/dists/feisty/main/binary-amd64/Packages.gz)  404 Not Found [IP: 64.158.56.56 80]
Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by Sidzone on 2008-07-12
How do we add ubuntustudio repositories.  If I (a newbie) can be baby stepped through what I need to type into the Terminal to make the change, I've got the balls to do it; I just don't get it based upon some of the blogs that assume we all have years of experience hacking (just 'cause we're brave enough to work with Linux vice Microsoft); give us a break please.

Sidzone

---

