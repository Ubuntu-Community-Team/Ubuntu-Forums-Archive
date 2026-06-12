---
title: "So much for thunderbird, it's gone?? :("
date: 2007-09-03
forum: Absolute Beginner Talk
---

### Post by gimpguy2000 on 2007-09-03
Well, I had TB 1.5 on my Ubuntu feisty and I tried to manually update to the latest version since it seems Ubuntu hasn't yet put it in the repo. 

I followed instructions to a T and what I get now is a Thunderbird that won't even work. It says 

**Failed to execute child process "mozilla-thunderbird" (No such file or directory)**

I have tried everything and can't even delete the folders manually... I can't login as root, rmdir doesn't work in root mode seeing the folder is not empty, I added ROOT to user group for login access normally but even that won't work. 

I have since uninstalled TB, tried to reinstall through add\remove. Still, I get the same. 

I have since June, been fighting with Ubuntu more than enjoying it as it seems nothing goes how it should and getting to the point of simply not using it any more. So many things have gone wrong and it's simply tiring. I am trying to hang in there but Windows is so close to being my OS of choice yet again. 

TX

---

### Post by Paul133 on 2007-09-03
Why not just 'sudo rm -rf /the/directory'; that forces removal of directories recursively. If tou want a root file browser, try 'gksudo nautilus'.

---

### Post by philinux on 2007-09-03
To correct feisty go to synaptic and mark thunderbird for reinstallation. This is the important bit.

Now once you've sorted that out got to.

[http://ubuntuzilla.wiki.sourceforge.net](http://ubuntuzilla.wiki.sourceforge.net) and follow the instructions.

The end result is that synaptic is happy and you get thunderbird 2 and the latest firefox if you want it.

---

### Post by nanotube on 2007-09-03
> **gimpguy2000 said:**
> Well, I had TB 1.5 on my Ubuntu feisty and I tried to manually update to the latest version since it seems Ubuntu hasn't yet put it in the repo. 

I followed instructions to a T and what I get now is a Thunderbird that won't even work. It says 

**Failed to execute child process "mozilla-thunderbird" (No such file or directory)**

I have tried everything and can't even delete the folders manually... I can't login as root, rmdir doesn't work in root mode seeing the folder is not empty, I added ROOT to user group for login access normally but even that won't work. 

I have since uninstalled TB, tried to reinstall through add\remove. Still, I get the same. 

I have since June, been fighting with Ubuntu more than enjoying it as it seems nothing goes how it should and getting to the point of simply not using it any more. So many things have gone wrong and it's simply tiring. I am trying to hang in there but Windows is so close to being my OS of choice yet again. 

TX

besides the specific problem with thunderbird, you seem to have problems with root access... i suggest you read about the 'sudo' model in ubuntu before you go adding root to things:
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by gimpguy2000 on 2007-09-03
Thanks for the help all, but so far, nada.  Anything I install I still get the same error as above. It won't open TB no matter what I try, even by command line.  I did delete the folder and reinstalled followed the instructions as posted, still nothing.  I would even take the old thunderbird back right now if I could, I can't use it at all though. 

TX

---

### Post by nowshining on 2007-09-03
by default root is disabled no one can login as root from the logon prompt you'll have to give root a password & in the login windows box you'll have to allow administrators to login from the login prompt... doing everything in sudo if you can or try this command

gksudo nautilus

enter password

don't worry if it shows an authentication error - it's a known bug, it should start up the file browser in root/sudo mode..:) now you can add/delete anything wherever..if you want try clicking on the thunderbird folder / right click - properties and under permissions making sure you as a user have any permissions..

---

### Post by st33med on 2007-09-03
Remember, Gutsy is unstable.

Beside the point, try installing thunderbird 2.0
```
sudo apt-get install thunderbird 2.0
```

---

### Post by MetalMusicAddict on 2007-09-03
> **st33med said:**
> Remember, Gutsy is unstable.

Beside the point, try installing thunderbird 2.0
```
sudo apt-get install thunderbird 2.0
```

Its simply **sudo apt-get install thunderbird**. Your command will have it look for a package called **2.0**.

---

### Post by gimpguy2000 on 2007-09-03
Thanks again.  Unfortunately all I get is this...
[I]
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package thunderbird is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package thunderbird has no installation candidate
gimpguy@gimpguy-desktop:~$ sudo apt-get install thunderbird
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package thunderbird is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package thunderbird has no installation candidate
gimpguy@gimpguy-desktop:~$ 

I tried with tb 2.0 and without the 2.0. [/I]

As well, just for the root access part, I just went to System>Admin>login window>security and allowed me to login as root from login screen. However, it only worked after a few restarts, go figure. :confused:  Anyway, it accomplished nothing anyway, lol.  


So this leaves me yet with this problem...

**Failed to execute child process "mozilla-thunderbird" (No such file or directory)**

Any other ideas? I have honestly looked and tried many installations and fixes and yet nothing has dented this problem. The directory is in fact there but it seems the startup isn't maybe pointing in the correct place? Could this be part of the problem?

TX

Paul

---

### Post by nanotube on 2007-09-03
which version of ubuntu? what architecture (64bit or 32bit?)

---

### Post by gimpguy2000 on 2007-09-03
32 only.  Also, the command for Thunderbird from icon states this...  in launcher tab...

**mozilla-thunderbird**

I checked again to make sure the directory was created and it is in the usr/lib/        so the path is in fact /usr/lib/mozilla-thunderbird.  It's just not launching then it seems or can't find it's way to the launcher.

TX

Paul

---

### Post by nanotube on 2007-09-03
which instructions did you use (the ones you followed to a t) to install tbird 2.0.0.6?

also, you haven't said which version of ubuntu you are using. to see your version, try:
```
cat /etc/issue
```

---

### Post by gimpguy2000 on 2007-09-03
I did post it in my my first post, i'm using Fiesty, but if you needed the version as in this....then np, ....  Ubuntu 7.04 \n \l
Also, I tried all the install methods that were listed in this thread. 

TX

Paul

---

### Post by nanotube on 2007-09-03
> **gimpguy2000 said:**
> I did post it in my my first post, i'm using Fiesty, but if you needed the version as in this....then np, ....  Ubuntu 7.04 \n \l
Also, I tried all the install methods that were listed in this thread. 

TX

Paul
oh yea, i kinda missed that in your first post :) heh.
ok, so if you have tried ubuntuzilla... then, what's your output of
```
ls -al /usr/bin/thunderbird
```
and can you launch thunderbird with command
```
thunderbird
```
?

---

### Post by gimpguy2000 on 2007-09-04
All I get is this...  [B] lrwxrwxrwx 1 root root 28 2007-09-03 15:28 /usr/bin/thunderbird -> /opt/thunderbird/thunderbird
[/B]

Then if I try to launch using thunderbird I get this...

** command not found**

And the plot thickens....:confused:

TX again,

Paul

---

### Post by gimpguy2000 on 2007-09-04
Ok, got it fixed :)  What I did... but take no credit for ...is this...

Ok, I couldn't delete the folder **mozilla-thunderbird** using sudo, su, etc.... So I re-went into root login screen and still couldn't delete it. I moved it to desktop and still couldn't delete it so I opened it, deleted the files then deleted the folder but it only worked while moved to desktop.  

Then going back into user login, I reinstalled through Synaptic, still didn't work however and still got an error, but this time, I re-went over the instructions at the link per  Philinux instructions and re-tried the install. This time it didn't get some minor errors as before, this time it went through and it works. :):) 

I think the folder was somehow messing it up and which is why I wanted to get rid of it but just root access command line wouldn't work. 

Either way, it even kept settings, etc... and I thank  **everyone** for the help. If not for all suggestions, I would still be wondering what to do...:KS 

I probably shouldn't spout off about going into Windows again but have been having a lot of trouble with simple matters in Ubuntu lately, things I don't even change, etc.. so it's been frustrating so I apologize for that, just letting off some steam. :mad::mad::mad:   ;)

Thanks again,

Paul

---

