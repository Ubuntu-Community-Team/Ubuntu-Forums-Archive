---
title: "Messed up repositories"
date: 2006-12-18
forum: Absolute Beginner Talk
---

### Post by PillowFightin on 2006-12-18
Okay, so I've been trying to upgrade to the new Firefox in Dapper and in the process I've messed up my repositories list. I added two that it apparently doesn't think are valid, and so now I get errors every time I try to use the package manager. I simply need to remove TWO lines in sources.list, but it won't let me do it because I don't have the right permissions, and I have failed to do it via command line (which I am really not very good at).

I need to remove:
[http://www.apt-get.org/main/](http://www.apt-get.org/main/)
[http://www.apt-get.org](http://www.apt-get.org)

Can someone please help me do this?

Also, if anybody has any suggestions for a painless firefox 2 update I'd love to hear it. I've tried three differnt ways and each has utterly failed (terminal way, shell script way, etc.).

---

### Post by ciscosurfer on 2006-12-18
> **PillowFightin said:**
> Okay, so I've been trying to upgrade to the new Firefox in Dapper and in the process I've messed up my repositories list. I added two that it apparently doesn't think are valid, and so now I get errors every time I try to use the package manager. I simply need to remove TWO lines in sources.list, but it won't let me do it because I don't have the right permissions, and I have failed to do it via command line (which I am really not very good at).

I need to remove:
[http://www.apt-get.org/main/](http://www.apt-get.org/main/)
[http://www.apt-get.org](http://www.apt-get.org)

Can someone please help me do this?

Also, if anybody has any suggestions for a painless firefox 2 update I'd love to hear it. I've tried three differnt ways and each has utterly failed (terminal way, shell script way, etc.).So, issuing the following doesn't work for you?```
gksu gedit /etc/apt/sources.list
```Once you get inside, comment out ( put a pound sign, a #, in front of the lines) or completely remove those lines you added.  Then save the file and close it.  Next, issue an update to apt to get the lastest package list from the repositories```
sudo aptitude update
```As for way to upgrade to Firefox 2, this page will help you out immensely: [http://psychocats.net/ubuntu/firefox](http://psychocats.net/ubuntu/firefox)

---

### Post by PillowFightin on 2006-12-18
Thanks very much--no, I hadn't tried that one. I am still trying to get the hang of command lines. If you don't mind, what is the difference between sudo and gksu? Is there somewhere I look at a comprehensive list of Ubuntu commands (with examples, perhaps)?

Anyway, that worked perfectly, thank you. And the psychocats URL was very helpful also. I've been there before but somehow missed his Firefox section. Thanks!

---

### Post by ciscosurfer on 2006-12-18
> **PillowFightin said:**
> Thanks very much--no, I hadn't tried that one. I am still trying to get the hang of command lines. If you don't mind, what is the difference between sudo and gksu? Is there somewhere I look at a comprehensive list of Ubuntu commands (with examples, perhaps)?

Anyway, that worked perfectly, thank you. And the psychocats URL was very helpful also. I've been there before but somehow missed his Firefox section. Thanks!For differences between sudo, gksudo, gksu, kdesu (and many other issues), please check here: 
[http://psychocats.net/ubuntu/](http://psychocats.net/ubuntu/)
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

For commands, you can start by looking here: [http://www.ubuntuforums.org/showthread.php?p=812448](http://www.ubuntuforums.org/showthread.php?p=812448) (also located in my signature: Help Yourself)

---

### Post by PillowFightin on 2006-12-18
Hmmmm. I know this is getting off the original topic, but...

Those scripts really seem to be the way to go for upgrading Firefox. I've tried a couple of them and I always get the same result, though, and I can't figure out why.

Here's what I get:
```
root@Ubuntu:~/Desktop# chmod +x installnewfirefox.sh
chmod: cannot access `installnewfirefox.sh': No such file or directory

```

No matter what I do it always tell me the file isn't there. And the thing is, the file IS there, I can see it right in front of my face. What am I doing wrong?

---

### Post by ciscosurfer on 2006-12-19
> **PillowFightin said:**
> Hmmmm. I know this is getting off the original topic, but...

Those scripts really seem to be the way to go for upgrading Firefox. I've tried a couple of them and I always get the same result, though, and I can't figure out why.

Here's what I get:
```
root@Ubuntu:~/Desktop# chmod +x installnewfirefox.sh
chmod: cannot access `installnewfirefox.sh': No such file or directory

```No matter what I do it always tell me the file isn't there. And the thing is, the file IS there, I can see it right in front of my face. What am I doing wrong?Check Firefox to see where you are downloading items to.  You may have it set to download to your home directory instead of your Desktop.  Type **cd** then issue the command again.

EDIT: just noticed that your are actually root...you don't want to be.  If you've logged in as root, log out and log back in as your normal user.  If you've just su'ed to root (or by some other means within your terminal), then type in **exit** and then issue the command again (the file is probably on your Desktop -- it's just it's on your user's desktop, not your root's desktop.  Hope that helps.

---

### Post by PillowFightin on 2006-12-19
Ah. I knew it had to be something simple like that. Well the script ran and did great all the way up to the last little bit, and then failed, because it said that it didn't have permission to execute the firefox-2.0.tar.gz file (which seems to be set as 644 root-owned). Not sure how to get around this, since I'm sure you can't be logged in two different ways at once.

Thanks so much for all your help, I really appreciate it!

---

### Post by ciscosurfer on 2006-12-19
> **PillowFightin said:**
> Ah. I knew it had to be something simple like that. Well the script ran and did great all the way up to the last little bit, and then failed, because it said that it didn't have permission to execute the firefox-2.0.tar.gz file (which seems to be set as 644 root-owned). Not sure how to get around this, since I'm sure you can't be logged in two different ways at once.

Thanks so much for all your help, I really appreciate it!Remember, you need to be using your regular user and not root.  When you login to your computer, you are logging in as your regular user, not root, correct?  If you are logging in as root, don't.  For various reasons, it's not a good idea to do that.  Log in as a regular user and then cd to the directory where the firefox-2.0.tar.gz is located and then issue the **chmod +x firefox-2.0.tar.gz** this will give exectue permissions to the file and allow it to be run as your regular user.

---

### Post by PillowFightin on 2006-12-20
To be perfectly honest I am not sure which way I am logging in. (Sad, I know). But yes, I am probably going root without even thinking. I am so confused as to which functions need root and why, and which ones don't. I am truly new at this and am used to the Windows way of doing things. Honestly I am a little annoyed at the way Ubuntu asks for passwords all the time for everything...though I know it is for a good reason.

I will research the issue...thank you for your tips!

---

### Post by macogw on 2006-12-20
You're only logging in as root if you type "root" at the "username" part, otherwise you're a normal user.  The password is to keep outside evil people from breaking your computer.  The fact that outside evil people could get in because of lack of passwords would be why you probably had viruses and spyware and adware in Windows.

Administrative stuff like installing and editting system files require "sudo" at the beginning and your password.  That's a temporary root.  The rest of the time, you should be yourself.

---

### Post by randiroo76073 on 2006-12-20
As another win convert to linux I just look at the password as replacing all the security prgms I had to run to keep windoz safe + the constant nagging need to keep them all updated, all the while failing miserably.  Linux is so much safer :)

---

### Post by ciscosurfer on 2006-12-20
> **macogw said:**
> You're only logging in as root if you type "root" at the "username" part, otherwise you're a normal user.  The password is to keep outside evil people from breaking your computer.  The fact that outside evil people could get in because of lack of passwords would be why you probably had viruses and spyware and adware in Windows.

Administrative stuff like installing and editting system files require "sudo" at the beginning and your password.  That's a temporary root.  The rest of the time, you should be yourself.I know what you're saying here, but it might be fair to mention that another reason it's not customary to log in as root is because you can do waayyyyyy more damamge as root (to your system) than if you are logged in as your normal user.  The sudo command is there for a reason and the warning it gives for a password is significant and basically is saying, "Hey!  You're about to make a system-wide change...If that's okay with you, continue to enter in your password and I'll proceed."  Without this password prompt, users themselves can do a lot of damage to their system--most of the time, completely inadvertently.

---

### Post by PillowFightin on 2006-12-25
Arrrrgh. I figured out what I had been doing wrong. I had forgotten I had made a root terminal shortcut and was just automatically using that for everything. I finally realized the problem and used the regular terminal. Duh! The firefox upgrade worked fine after that. 

Thanks for all your help!

---

