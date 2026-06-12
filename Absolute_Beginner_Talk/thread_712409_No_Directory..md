---
title: "No Directory."
date: 2008-03-01
forum: Absolute Beginner Talk
---

### Post by AbsentHarvest on 2008-03-01
[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)
> Download the latest version of alsa from [WWW] Alsa project (driver, lib, and utils) to a directory (eg. ~/downloads). In the following we assume that the latest version is 1.0.14. Please change this in accordance with the one you downloaded from the Alsa project site.

The problem is, one, i cannot download to that location. Because i do not have permission to do so. Another, i tried to substitute it, to the Desktop and then Documents. No go. I get that the message..
> cp: missing destination file operand after `/home/zack/documents/alsa'
Try `cp --help' for more information.


Point being, i cannot complete this following step.
> sudo mkdir -p /usr/src/alsa
cd /usr/src/alsa
sudo cp ~/downloads/alsa* .
sudo tar xjf alsa-driver*.bz2
sudo tar xjf alsa-lib*.tar.bz2
sudo tar xjf alsa-utils*.tar.bz2

need help, thanks.

---

### Post by spiderbatdad on 2008-03-01
One suggestion is to check the names of the folders you are trying to use for case. For example...documents, actually being Documents. In Linux case matters.

---

### Post by AbsentHarvest on 2008-03-01
beside the point, i've tried several locations and get the same error.
how can this be resolved?

---

### Post by pommattski on 2008-03-01
> **AbsentHarvest said:**
> 
The problem is, one, i cannot download to that location.

I may have the wrong end of the stick, but...

How are you attempting to download the files?.. 
Since, by definition, ~/downloads/ (or ~/Desktop) is in **your** home folder, unless something major is wrong, you should have write permissions for it.

Exactly what are you typing to get the response:
> cp: missing destination file operand after `/home/zack/documents/alsa'
Try `cp --help' for more information.

---

### Post by AbsentHarvest on 2008-03-02
Well, i downloaded it by going to the actual page, clicking on the link which would download to Firefox's default download location.

I've tried several things.
> sudo cp ~/downloads/alsa
> cp ~/downloads/alsa
And then replace the ~/downloads/ with ~/home/desktop etc..
Same error.
So, I'm guessing that I have to download it some other way?

---

### Post by zerhacke on 2008-03-02
> **AbsentHarvest said:**
> 
And then replace the ~/downloads/ with ~/home/desktop etc..

You're forgetting to put your username in there.  Also, ~ means /home/username.  Try the following.

cd ~/Desktop

---

### Post by pommattski on 2008-03-02
> **AbsentHarvest said:**
> Well, i downloaded it by going to the actual page, clicking on the link which would download to Firefox's default download location.
I've tried several things.

So,you are successfully downloading the files.
It looks as though you are using the cp (copy) command incorrectly though.  You need to give it the source and destination. See```
man cp
```for lots more detail.
Just entering "sudo cp ~/downloads/alsa" will give you the error "cp: missing destination file operand after `/home/zack/documents/alsa'" because you are telling it to copy a file, but you're not telling it where to copy it to.

OK... I've just had another look at the instructions you're following: I think you may have missed the dot **.**  The line:```
sudo cp ~/downloads/alsa* .
```has a <space><dot> at the end. This is very important. The dot indicates your current working directory, which at that point in your procedure should be /usr/src/alsa because you just typed "cd /usr/src/alsa" to "change directory" to there.


So, you should first confirm the location of your downloaded files - I will assume that they are on your desktop. Then change to your newly created directory using "cd /usr/src/alsa". Now type:```
sudo cp ~/Desktop/alsa* .
```This has the effect of copying all files in the directory /home/zack/Desktop/ whose filenames start with the charaters alsa, to your current working directory.

I hope this is of some help. 
Matt.

---

### Post by AbsentHarvest on 2008-03-02
Ok.
When I typed that in, i get this.
> zack@Testament:~$ cd /usr/src/alsa
zack@Testament:/usr/src/alsa$ sudo cp ~/Desktop/alsa* .
cp: omitting directory `/home/zack/Desktop/alsa'
zack@Testament:/usr/src/alsa$ 

After this point, I've tried what the tutorial instructs.
> zack@Testament:/usr/src/alsa$ sudo tar xjf alsa-driver*.bz2
tar: alsa-driver*.bz2: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
zack@Testament:/usr/src/alsa$ 

So, I thought, maybe, if i subbed in the version numbers, id get a different result.

> zack@Testament:~$ cd /usr/src/alsa
zack@Testament:/usr/src/alsa$ sudo cp ~/Desktop/alsa* .
cp: omitting directory `/home/zack/Desktop/alsa'
zack@Testament:/usr/src/alsa$ sudo tar xjf alsa-driver-1.0.16.tar.bz2tar: alsa-driver-1.0.16.tar.bz2: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
zack@Testament:/usr/src/alsa$ sudo tar xjf alsa-driver-1.0.16*.tar.bz2
tar: alsa-driver-1.0.16*.tar.bz2: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors


Nope.
Then I thought well, maybe xjf was to blame, and tried it without that.
Nope.
Then I noticed that the code I was instructed to use. 
> sudo tar xjf alsa-driver*.bz2
Did not include the .tar so I tried it with that.
Nope.

In all attempts I got this message.
> Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors


---

### Post by pommattski on 2008-03-02
It looks to me as though the files still may not be being copied to /usr/scr/alsa successfully.
At every stage, it is worthwhile checking the contents of the directories you are working with.  
Use "ls" to view a list of the files in your current directory, and, for example, "ls ~/Desktop/" to list the files on your desktop. You should see, amongst others, the 3 files: 
alsa-driver-1.0.16.tar.bz2 
alsa-lib-1.0.16.tar.bz2 and 
alsa-utils-1.0.16.tar.bz2

Another tip I would offer would be to use auto-complete - the <tab> key.
Eg. When typing the command "sudo tar xjf alsa-driver*.bz2", stop after you've typed "sudo tar xjf alsa-dr" and press <tab>. If the file we're looking for is in our current directory, the file-name will be automatically completed for us.  This ensures that we enter the name correctly, that it is present, and can end up saving a lot of time.

---

### Post by AbsentHarvest on 2008-03-06
Unfortunately.
I've toyed around with your advise.
Nothing seems to work. :/
> zack@Testament:~$ ls
Desktop    downloads  Music     Public     Videos
Documents  Examples   Pictures  Templates
zack@Testament:~$ cd /usr/src/alsa
zack@Testament:/usr/src/alsa$ ls
zack@Testament:/usr/src/alsa$ sudo cp ~/Desktop/alsa* .
[sudo] password for zack:
cp: omitting directory `/home/zack/Desktop/alsa'
zack@Testament:/usr/src/alsa$ ls
zack@Testament:/usr/src/alsa$ ls ~/Desktop/
alsa
zack@Testament:/usr/src/alsa$ ls ~/Desktop/alsa
alsa-driver-1.0.16.tar.bz2  alsa-lib-1.0.16.tar.bz2  alsa-utils-1.0.16.tar.bz2
zack@Testament:/usr/src/alsa$ sudo tar xjf alsa-driver-1.0.16.tar.bz2
tar: alsa-driver-1.0.16.tar.bz2: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
zack@Testament:/usr/src/alsa$ 
Display all 1955 possibilities? (y or n)
zack@Testament:/usr/src/alsa$ sudo tar xjf alsa-d


As you see near the end, i've tried the tab shortcut, however nothing is coming up.

---

### Post by pommattski on 2008-03-06
When you typed "~/Desktop/alsa", you were shown the 3 files you are trying to copy. This means that the 3 files are in a directory called alsa in the Desktop directory in your home directory. 
So, in order to copy the files, try: ```
cd /usr/src/alsa
sudo cp ~/Desktop/alsa/alsa* .
```Note that the "*" is a "wild card" - it can represent anything. So the above command "says copy any file whose name starts with alsa in the directory /home/zack/Desktop/alsa/, to my current location"
Give that a go.

---

### Post by AbsentHarvest on 2008-03-06
I followed that command.
The files were copied into that directory, from there i compiled and installed them according to the tutorial's instructions.  The TAB shortcut command proved useful.  I rebooted, and now.
I have sound!
:guitar:

all thanks to you. i appreciate the help you've provided. i'm glad you had the patience.
cheers.

---

### Post by pommattski on 2008-03-07
Great to hear :)
I'm pleased I could help.

---

