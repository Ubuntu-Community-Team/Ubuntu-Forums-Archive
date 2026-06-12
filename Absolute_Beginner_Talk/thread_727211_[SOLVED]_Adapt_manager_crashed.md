---
title: "[SOLVED] Adapt manager crashed"
date: 2008-03-17
forum: Absolute Beginner Talk
---

### Post by bioShark on 2008-03-17
Hi

In kubuntu 7.10: Went to Adapt Manager and tried to install JDK package. In the middle of the process, it crashed saying something that not all the packages were able to download. A window with KDE crash appeared. The Adapt Manager didn't wanna start again, only the KDE crash window appeared. After running the command:

> sudo apt-get update  

The Adapt Manager started again, but now whatever JDK package I try to install it says: 

> There was an error commiting changes. Possibly there was a problem downloading some packages or the commit would break packages 

???!!! What is that?

---

### Post by taurus on 2008-03-17
What happens if you run (make sure you close down the update manager window first)?

```
sudo apt-get update
sudo apt-get upgrade
```

Otherwise, post your /etc/apt/sources.list.

```
cat /etc/apt/sources.list
```

---

### Post by bioShark on 2008-03-17
Hi,

thank, it's solved. Here is how:

> sudo apt-get update

..did some update, but it didn't fix the probelem, I already tried it before you posted your reply.

> sudo apt-get upgrade

...it started to do some upgrade but it stopped in the middle of it, with an error, saying I should run:

> sudo apt-get -f install

...which I did, and it actually continued the installation of the JDK where it was left when it first crashed. Now the adept manager works fine.

Maybee you know a solution to my other problem I posted in the thread:

[http://ubuntuforums.org/showthread.php?t=727096]("http://ubuntuforums.org/showthread.php?t=727096")

Thanks a million, anyway. I need to remember that command.

---

