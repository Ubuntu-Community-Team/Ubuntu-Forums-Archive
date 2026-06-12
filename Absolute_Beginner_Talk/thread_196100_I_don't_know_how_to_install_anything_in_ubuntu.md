---
title: "I don't know how to install anything in ubuntu"
date: 2006-06-13
forum: Absolute Beginner Talk
---

### Post by Drifter on 2006-06-13
can someone help me learn how to install, I know nothing about how to do this.

---

### Post by johnc4510 on 2006-06-13
Here is a good guide if you are using Dapper:
[http://krazypenguin.net/Ubuntu_Dapper_Drake_6.06_Guide](http://krazypenguin.net/Ubuntu_Dapper_Drake_6.06_Guide)
If you are using Breezy post back here and I'll give you that guide.

---

### Post by taurus on 2006-06-13
you can use either apt-get (text base) or synaptic (GUI) to install stuff...

Open a terminal by clicking Applications -> Accessories -> Terminal and type
```

sudo apt-get install <program_name>
(When it asks you for a password, use the same one that you use to log in...)

```

Or click System -> Adminstrator -> Synaptic Package Manager.  And in the Search field, type in the name of a program you are looking for, highlight it, and click it with a mouse to put a check mark (for installing)...

---

### Post by aysiu on 2006-06-13
[http://www.monkeyblog.org/ubuntu/installing](http://www.monkeyblog.org/ubuntu/installing)

---

### Post by measure on 2006-06-13
I'm in the same boat, I have seen some demonstrations but I have completely forgotten. Forgive me for being such a pain but I must ask someone to help me upgrade from Hoary Hedgehog to the newest version which I believe is Dapper Drake.

So far I have seen this page [http://ubuntuguide.org/wiki/Dapper#Unofficial_Ubuntu_6.06_.28Dapper_Drake.29_Starter_Guide](http://ubuntuguide.org/wiki/Dapper#Unofficial_Ubuntu_6.06_.28Dapper_Drake.29_Starter_Guide)

Although it doesn't help me very much since my version is so very old. Perhaps I should download the new version and re-install? Or not?!

---

### Post by cjm5229 on 2006-06-13
You can also go to Applications>Add/Remove. One of the nicest things about Ubuntu isthat you don't have to hunt all over the Internet for software, then pay for it, then download it, then agree to give your soul to the vendor, then remove all the adware and spyware. 
Check out Automatix here in the forums under 3rd Part projects. and check out repository support also. You will find that there is an app for nearly anything you could ever want to do and they are free! 
Also browse the Howto's in the forums, lots of good stuff there.

Edit; 
Measure, 
Backup your home file and reinstall,  It might work to upgrade but going from Hoary to Dapper is a bit much. either way backup your Home files.

---

### Post by johnc4510 on 2006-06-13
You can not upgrade by skipping a version ie: Hoary to Dapper, skipping Breezy
You can upgrade to Breezy then to Dapper
Or you can download an iso and reinstall to the newer version

---

### Post by measure on 2006-06-13
Thanks. I will try to find a page to upgrate to breezy, although if you know of one or know where you can find one please point me in the right direction. Thanks

---

### Post by Bloch on 2006-06-13
> help me upgrade from Hoary Hedgehog to the newest version which I believe is Dapper Drake.
>  I will try to find a page to upgrate to breezy,
Measure, if it is at all possible, reinstall Dapper. The two-step upgrading process is making things difficult for yourself. 
In the end it might take longer than a fresh install.

I think it's fair to say that a fresh install gives less problems (usually none at all) than an upgrade

---

### Post by Drifter on 2006-06-13
Sorry, I have been away from my computer for awhile.  I know about autmatix and I use it, also know about snaptic, what I don't know is how to install things myself.  For exsample, kmymoney is what I need now, it is not in snaptic or automatix.  Also the repositories are a big problem for me.  I don't even know how to untar a download.  I will read some of the info that some of you gave me.  I have been searching how to's for a long time but can't seem to get anything concerning how to get and install kmymoney.  There are 0thers that I would like to do but I first need a working understanding of how to untar and then install and then get all the dependencies and repo's etc.

---

### Post by IYY on 2006-06-13
To untar a file, just double click on it and extract it like you would with any zip file in Windows. You can also do it through the command line:

tar -xvvzf foo.tar.gz
tar -xvvf foo.tar

(based on the extension)

Then, to install, read the readme file inside the archive. Usually you'll need to do something like

./configure
make
make install

but it's not always set up the same way, especially the first part.

---

### Post by cjm5229 on 2006-06-13
KMyMoney is in the repositories, Go to the repository support section and follow Ubuntu_Demons guide. After you have enabled the neccessar repositories you will find KMyMoney in Synaptic. By the way, that is one great App. I use it all the time.

---

### Post by measure on 2006-06-13
So far I'm downloading the upgrades and, well I can't say that they are going to install themselves but I got some help from here.

[http://ubuntuforums.org/archive/index.php/t-75823.html](http://ubuntuforums.org/archive/index.php/t-75823.html)

---

### Post by Drifter on 2006-06-13
OK now I have kmymoney how do I import a quicken file into it.  What is OFX

---

