---
title: "setting a password for a folder"
date: 2007-12-14
forum: Absolute Beginner Talk
---

### Post by LostMagix on 2007-12-14
I dont want to just set it so only i can look at it, i am on and off my computer a log and its a hassle to log on and off every time

so i would like to set up a group of files so you need a password to access

---

### Post by LostMagix on 2007-12-14
*bump*

---

### Post by LostMagix on 2007-12-14
so i guess there is no way to do this??

---

### Post by llamakc on 2007-12-14
Don't bump threads that quickly. Have you tried googling or searching the forums yourself yet? This has been asked before.

---

### Post by LostMagix on 2007-12-14
i tried both google and the forums search, all i could come up with is how to encrypt a file or how to set access

i have been working on this all day, i cant find anything that can help

---

### Post by JillSwift on 2007-12-14
Google is you bestest buddy! =^_^=

[https://answers.launchpad.net/ubuntu/+question/9592](https://answers.launchpad.net/ubuntu/+question/9592)

There really isn't a direct way to do what you're looking to do. The Linux/Unix security rests on permissions and location in the file system tree. If you've files you need to keep away from others, you really need to have everyone on their own, non-administrative, login.

---

### Post by llamakc on 2007-12-14
[http://ubuntuforums.org/showthread.php?t=594814&highlight=protect+folder](http://ubuntuforums.org/showthread.php?t=594814&highlight=protect+folder)

You could have found this by searching. 

You'll need to install encfs, fuse, and any dependencies to start.

And then follow the ENTIRE thread above by reading it once first, then visiting 

[http://www.tomatarium.pwp.blueyonder.co.uk/cryptkeeper.html](http://www.tomatarium.pwp.blueyonder.co.uk/cryptkeeper.html)

and grabbing the deb for Feisty.

---

### Post by PinkFloyd102489 on 2007-12-14
You could always remove read permissions from the folder all together and then gksudo nautilus to the folder. That's what I do. That way the person who wants to access your files has to know your password.

---

### Post by airtonix on 2007-12-19
Pinkfloyd: which wont work for the OP becuase they share username and password access with many people.

reason? so they dont have to remember it, they most probably have their desktop to auto login on bootup....

at which point....securing a folder from other users sharing the same desktop account wont  be a viable way since they are all using same account....

OP : you want encfs. coupled with some bash scripts that use Zenity to request the nessecary info from you (in gui form).

i also highly recomend encrypting folders that are on your removable storage device. that way you dont leave them around for others to practice brute-forcing their way into your encrypted folder.

---

