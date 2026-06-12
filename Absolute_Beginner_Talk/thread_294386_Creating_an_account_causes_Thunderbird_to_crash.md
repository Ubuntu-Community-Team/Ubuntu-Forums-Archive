---
title: "Creating an account causes Thunderbird to crash"
date: 2006-11-06
forum: Absolute Beginner Talk
---

### Post by Noutro on 2006-11-06
Hello everybody!

I've got a problem with my newly installed Thunderbird 1.5.0.7 (20060918 ) from the Ubuntu 6.10 package. After I've created a new email account, thunderbird kills itself 2-3 seconds after I pressed the button which finishes the new account. If I, then, try to start up thunderbird again, it kills itself immediately.

I found out that I can retrieve control if I delete the profile folder "~/.mozilla-thunderbird". Once again I tried to create a new email account then, with the same result as before (thunderbird crashes). :( 

What is wrong here? Can anybody help me?

I already read a lot about thunderbird, but I didn't find an answer.

I should mention that this problem doesn't occur if I manually download and install Thunderbird 1.5.0.7 (20060909) from mozilla webpage; but I'd prefer to use the official Ubuntu Thunderbird package instead.

I would be happy if you could help me. :) 

Thx,
Noutro

Ubuntu 6.10, Thunderbird 1.5.0.7 (20060918 ) from Ubuntu package

---

### Post by Average Joe on 2006-11-06
Weird. I wish I could help you, but I have no clue what could be wrong.

I am also running Ubuntu 6.10, and installed the exact same Thunderbird version as you did. I created several e-mail accounts, and it works perfect.

Maybe you could try to create another profile first with:
> thunderbird -profilemanager
and then create new accounts.

---

### Post by Noutro on 2006-11-06
Meanwhile I found out that I the Ubuntu release of Thunderbird works if I can start it _successfully_ as superuser:

> sudo mozilla-thunderbird

Then everything works the ways one would expect it!!

But if I start it using my default Ubuntu account, thunderbird returns the following error message:

> 
mozilla-thunderbird
DOUBLE-CLICK: 400 --> -1 THRESHOLD: 8 --> -1 Segmentation fault (core dumped)


I don't have the solution but now it doesn't seem too bad anymore. I guess that there's something wrong with the ....
Ohhh, I think I understand want went wrong! I installed thunderbird using Synaptic as superuser!!
Then everything is clear (I hope)!

I will try it...

---

### Post by Average Joe on 2006-11-06
> Ohhh, I think I understand want went wrong! I installed thunderbird using Synaptic as superuser!!
Synaptic will always ask for your sudo password, so I doubt if this is the problem. Good luck with it anyway.

---

### Post by Noutro on 2006-11-06
That's what I found in my profile folder:
> noutro@computer:~/.mozilla-thunderbird/077hke7a.default$ ls -al
insgesamt 2263
drwx------ 5 noutro noutro    1024 2006-11-06 21:26 .
drwx------ 3 noutro noutro    1024 2006-11-06 21:05 ..
-rw-r--r-- 1 root   root      1866 2006-11-06 21:26 abook.mab
-rw------- 1 noutro noutro   65536 2006-11-06 21:26 cert8.db
-rw------- 1 noutro noutro     136 2006-11-06 21:05 compatibility.ini
-rw-r--r-- 1 noutro noutro  138007 2006-11-06 21:05 compreg.dat
drwxr-xr-x 2 noutro noutro    1024 2006-11-06 21:05 extensions
-rw-r--r-- 1 noutro noutro     312 2006-11-06 21:05 extensions.cache
-rw-r--r-- 1 noutro noutro     300 2006-11-06 21:05 extensions.ini
-rw-r--r-- 1 noutro noutro    2875 2006-11-06 21:05 extensions.rdf
-rw-r--r-- 1 root   root      1415 2006-11-06 21:25 history.mab
-rw------- 1 noutro noutro   16384 2006-11-06 21:26 key3.db
-rw-r--r-- 1 noutro noutro    5399 2006-11-06 21:26 localstore.rdf
drwxr-xr-x 4 noutro noutro    1024 2006-11-06 21:06 Mail
-rw-r--r-- 1 noutro noutro     477 2006-11-06 21:05 mailViews.dat
-rw-r--r-- 1 noutro noutro    2623 2006-11-06 21:05 mimeTypes.rdf
-rw-r--r-- 1 noutro noutro    2729 2006-11-06 21:26 panacea.dat
-rw-r--r-- 1 noutro noutro       0 2006-11-06 21:24 .parentlock
-rw-r--r-- 1 root   root      3821 2006-11-06 21:26 prefs.js
-rw------- 1 noutro noutro   16384 2006-11-06 21:05 secmod.db
-rw------- 1 root   root       178 2006-11-06 21:26 signons.txt
drwxr-xr-x 2 noutro noutro    1024 2006-11-06 21:05 US
-rw-r--r-- 1 root   root        10 2006-11-06 21:26 virtualFolders.dat
-rw-r--r-- 1 noutro noutro   98964 2006-11-06 21:05 xpti.dat
-rw-r--r-- 1 noutro noutro 1973545 2006-11-06 21:25 XUL.mfasl

Obviously, there are some files which are owned by 'root'. I guess that's the reason that thunderbird didn't work.

Has anyone an idea how to set the rights correctly? I mean: the rw-flags!
I will change the owner from 'root' to 'noutro' and see want happens.

---

### Post by Noutro on 2006-11-06
Thank you for your help! I guess I narrowed the failure now.
Nice evening to you! :)

---

### Post by Average Joe on 2006-11-06
Yes, that could be the problem. You can make noutro owner of everything by going to your profile directory and typing:
> sudo chown -R noutro noutro *
This will recursively also make you the owner of all the files in underlying directories.

P.S. You can change the file permissions for a file by typing:
> chmod 644 <filename>
That will make the file readable and writable for you, and only readable for others. But it probably won't be necessary anymore once you are the owner of the file.

---

### Post by Noutro on 2006-11-06
Meanwhile, I did the following:

1. I deinstalled Thunderbird
2. I _explicitly_ removed "~/.mozilla-thunderbird/" directory using "rm -r ~/.mozilla-thunderbird"
3. I installed Thunderbird again, but now _not_ as superuser but with my default account
4. As expected, I own all files in the profile folder now

As not expected, Thunderbird, still, shows that strange behaviour!!! :( 
Are there additional files of which I have to be the owner?
I have no clue??

Has anybody suggestions what to try next?

---

### Post by Average Joe on 2006-11-08
You could try:
```
sudo apt-get purge thunderbird
```
to make sure that you also remove all the Thunderbird configuration files. If you then remove your .mozilla-thunderbird directory, and then reinstall Thunderbird again (as normal user) it should work fine.

Other then this I have no suggestions (apart from installing Ubuntu from scratch).

---

### Post by Noutro on 2006-11-13
You surely meant:
```
sudo apt-get --purge remove mozilla-thunderbird
```

I tried this but it didn't help.

Obviously other users have the same problem, e.g. dgorchak, who posted the thread "Thunderbird crash" in this forum.

Does -- meanwhile -- anyone have a satisfying solution? I, still, couldn't get Thunderbird run.

---

### Post by BlackwaterPark on 2006-11-19
I am having what I imagine is the same problem, except I do not have that permissions issue. Instead, as soon as I install Thunderbird and run it for the first time, I create an account (tried all kinds of accts - Mail, Blogs, etc) and attempt to browse to that folder when Thunderbird crashes/disappears. Afterwards, anytime I try to click on a folder within Thunderbird, it does the same disappear/crashing act. While running it as root, it runs just fine.

---

### Post by pastorti on 2006-11-25
I am having the same problem.  For now I have changed my start-up link to sudo mozilla-thunderbird with the run in terminal box checked and it works... but I'd love to know how to fix the problem.  Please advise.

---

### Post by jerrykenny on 2006-11-25
"sudo mozilla-thunderbird" is a bad idea, its running a mail programme as superuser and leaving you open to damage . . . 

If others are having the same problem , then its maybe a ubuntu or mozilla bug . . . 

Wait for them to fix it, file a bug report . . in the meantime use evolution mail, but NOT "sudo mozilla-thunderbird"

---

