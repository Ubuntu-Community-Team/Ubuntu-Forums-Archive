---
title: "Software update issue"
date: 2007-04-18
forum: Absolute Beginner Talk
---

### Post by ector on 2007-04-18
Whenever I try to run updates I get:

> An error occured
The following details are provided:

E: /var/cache/apt/archives/mysql-server-5.0_5.0.24a-9ubuntu2_i386.deb: subprocess new pre-removal script returned error exit status 1 

I had a look around but I couldn't find this specific problem.  Any help would be greatly appreciated.

Thanks.

---

### Post by freebird54 on 2007-04-18
It would appear that an attempt was made to remove that file, and it was unsuccessful.  If you remove it yourself, thanks should be back to normal.  Thus:

```
cd /var/cache/apt/archives
sudo rm mysql-server-5.0_5.0.24a-9ubuntu2_i386.deb
```

should get rid of it.  Exit terminal and try again.  Presumably this got left behind in a previous go around.  If you like, before removing it, try

```
ls -l mysq* 
```

to see if we can see what might be wrong with it.

Hope this gets you going!

---

### Post by ector on 2007-04-18
Thanks for the speedy reply :) 

I removed the file only to have it recreated on the next attempt, followed by the same error ... If I delete the file it downloads the file again and gives me the same error (as opposed to giving me the error immediately if I don't delete it). 

ls -l gives me:

> -rw-r--r-- 1 root root  6955638 2007-04-04 20:04 mysql-client-5.0_5.0.24a-9ubuntu2_i386.deb
-rw-r--r-- 1 root root    42274 2007-04-04 20:04 mysql-common_5.0.24a-9ubuntu2_all.deb
*-rw-r--r-- 1 root root 24937074 2007-04-04 20:04 mysql-server-5.0_5.0.24a-9ubuntu2_i386.deb*

---

### Post by ector on 2007-04-18
Strange thing... When I select *"Check"* in the *Software Updates* form I get:

> W: GPG error: [http://www.getautomatix.com](http://www.getautomatix.com) edgy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY CC919A31E23C5FC3

No idea if the two issues are related at all.. just thought I'd post it anyway..

---

### Post by freebird54 on 2007-04-18
It sounds almost as if it was trying to double download the flle.  The probable cause of that is beyond my knowledge of the system though!  Does the install manage to complete - has it been put on your system?

Another possibility - which I give no guarantees on the result! - is to to try another method for getting the files installed.  Is this from 'update' or from Add/Remove or from Synaptic?  If it is not from Synaptic, you might try getting the files from there directly..

---

### Post by freebird54 on 2007-04-18
Unless mysql is being installed by Automatix, I don't think there is a related problem there,  What that is telling you is that Automatix - and all its updates - will not appear as VALIDATED when they occur, because the verification key is not available.  Don't know why it isn't - should check with their site I guess?  Not relevant to the current difficulty though, that I can see.

Waiting to hear about method of acquisition etc. before suggesting anything furher.  DOn't want to break more than is already :)

---

### Post by ector on 2007-04-18
Originally I was trying to go update using Update manager. I tried updating through Synaptic but no joy :( , I get the same error. In the update summary (before the update attempt) I can see:

> 
mysql-server-5.0 (version 5.0.24a-9) will be upgraded to version 5.0.24a-9ubuntu2

I tried checking the Mysql version through PhpMyAdmin to see if had actually been updated somehow and it looks like its still version 5.0.24a-9 (Sorry I don't know a better way to check the version number of an program.. although I'm sure there'd be a command for it through the terminal).

---

### Post by Seisen on 2007-04-18
You need the GPG key for the Automatix repos. This will help you fix that.

[http://www.getautomatix.com/forum/index.php?showtopic=880]("http://www.getautomatix.com/forum/index.php?showtopic=880")

Try this in the terminal and see if it fixes your problem. Sometimes it works sometimes it doesnt

```
sudo dpkg --configure -a 
```

---

### Post by ector on 2007-04-18
> **Seisen said:**
> You need the GPG key for the Automatix repos. This will help you fix that.

[http://www.getautomatix.com/forum/index.php?showtopic=880]("http://www.getautomatix.com/forum/index.php?showtopic=880")

Thanks worked fine :)

> **Seisen said:**
> Try this in the terminal and see if it fixes your problem. Sometimes it works sometimes it doesnt

```
sudo dpkg --configure -a 
```

No luck with this one :(

---

### Post by Seisen on 2007-04-18
try going into /etc/rc0.d-rc6.d and remove any instances of mysql and then try reinstalling it and see if that works.

---

### Post by ector on 2007-04-18
> **Seisen said:**
> try going into /etc/rc0.d-rc6.d and remove any instances of mysql and then try reinstalling it and see if that works.

I removed all files containing "sql" in directories rc0.d to rc6.d. Tried reinstalling but still get the same error:

> An error occured
The following details are provided:

E: /var/cache/apt/archives/mysql-server-5.0_5.0.24a-9ubuntu2_i386.deb: subprocess new pre-removal script returned error exit status 1

---

### Post by ector on 2007-04-19
I have no idea what happened, but when I turned the computer on today the update mysteriously went through! :D

Thanks for the help!

---

