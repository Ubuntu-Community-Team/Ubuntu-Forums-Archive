---
title: "[SOLVED] dpkg --configure -a"
date: 2008-02-22
forum: Absolute Beginner Talk
---

### Post by MelissaEpiphany on 2008-02-22
Excuse my n

---

### Post by MelissaEpiphany on 2008-02-22
Oops, sorry pressed the wrong button, what I meant to say was, I've been struggling to get Java up and running on FireFox. I've been putting Wine and Shockwave on so my son can chat to his friends on Habbo. All's been going well but Java is being a pain in the proverbial. The other day I installed the jdk file (which went automatically to my desktop,) and now want to fix plugins in the terminal, but I keep getting this message every time I look in synaptic or add/remove or try to type commands in terminal:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

When I do put that command in terminal, it tells me to go download the grrr jdk file that I have already downloaded. What simpleton noob mistake have I made and how can I fix it?

Cheers, Mel

---

### Post by oedha on 2008-02-22
open terminal : go to applications - accesories - terminal
type : sudo dpkg --configure -a
wait until finish and then
sudo apt-get update

i suggest : => sudo apt-get install ubuntu-restricted-extras
for your java related

---

### Post by MelissaEpiphany on 2008-03-11
Hi, sorry for taking so long to respond. I've been so busy researching a solution to this problem without any luck. There was a great response in another post, to a user who had the exact same problem; 

[http://ubuntuforums.org/showthread.php?t=423615&highlight=uninstall+jdk](http://ubuntuforums.org/showthread.php?t=423615&highlight=uninstall+jdk)

For that user, doing what you suggest worked, but for me, I have tried over and over again to run 'sudo dpkg --configure -a' but my problem is that it just never completes itself. 

This comes up: 

"Setting up sun-java6-doc (6-00-2ubuntu2) ...
This package is an installer package, it does not actually contain the
""JDK documentation. You will need to go download one of the
archives:

jdk-6-doc.zip jdk-6-doc-ja.zip

(choose the non-update version if this is the first installation).
Please visit

[http://java.sun.com/javase/downloads/](http://java.sun.com/javase/downloads/)

now and download. The file should be owned by root.root and be copied
to /tmp.

[Press RETURN to try again, 'no' + RETURN to abort]"

...and stays up. I have left it like that for hours on end and still nothing, (no @desktop message that usually signifies the command has downloaded or configured itself) so I can never move on to the next steps. I can't download or install any software, nor install my updates, I just get this message over and over again: 

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem
E: _cache->open() failed, please report."

It's a never ending cycle and it is driving me NUTS! I'm about to uninstall 7.10 and reinstall it all over again, and I really don't want to have to do that. Is there anyone out there that can help me with this?

Cheers, Mel

---

### Post by glennric on 2008-03-11
Try typing
```
sudo apt-get remove --purge sun-java6\*
```
If that works then try
```
sudo apt-get install sun-java6-jre sun-java6-plugin
```

---

### Post by GreTTin on 2008-03-11
sounds like when i got stuck in a loop like that. look here

[http://ubuntuforums.org/showthread.php?t=703846&page=5](http://ubuntuforums.org/showthread.php?t=703846&page=5)

hope that helps. gl

---

### Post by MelissaEpiphany on 2008-03-13
That did help thank you. 


My problem was that initially I had not finished installing Java but did not realise it, I tried installing jdk on advice elsewhere, but that is what gave me the "dpkg --configure -a" problem.

After reading some posts I realized that after I had installed java, I had needed to press Tab and highlight "ok" then "yes" on the licensing agreement. Because I hadn't done this the first time, I had never properly installed.

I could not even use the command to purge java you gave me at first, it kept coming up with the same line "dpkg --configure -a," but I read your previous post, and tried "sudo dpkg --purge -a" That worked brilliantly, and after that I could get in to uninstall/purge java, get rid of the lot including that pesky jdk  then reinstall and this time properly fill in the licensing agreement. 

Thank you so much!

---

