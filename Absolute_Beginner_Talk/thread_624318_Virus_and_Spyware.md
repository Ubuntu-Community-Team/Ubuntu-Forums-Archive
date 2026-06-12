---
title: "Virus and Spyware"
date: 2007-11-26
forum: Absolute Beginner Talk
---

### Post by JasonBourneLinux on 2007-11-26
hey,

Ive read other threads but are there good apps (lol graphical- for me, a noob) fo anti-virus and spyware? I know Linux is pretty darn secure but I get nightmares after reading the thread bout the malicious commands (and I share this one partition with a windows installation)

thanks for the help!!

Ubuntu w/ desktop effects > Windows XP

^_^

---

### Post by patchido on 2007-11-26
maliciuos commands will not harm u unles.... u make does commands.. u dont really need more protection..

---

### Post by mikewhatever on 2007-11-26
No antivirus or antispyware would protect you from deleting your root directory, which was exactly the thing the command did. Read these to calm down -->
[http://psychocats.net/ubuntu/security](http://psychocats.net/ubuntu/security)
[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

It may also be a good idea to reread the thread about malicious commands. Things are well explained there and there is no mention of an antivirus.

---

### Post by Sef on 2007-11-26
> maliciuos commands will not harm u unles.... u make does commands.. u dont really need more protection..

Ubuntu is very secure itself.   Don't install anything that you don't know where it came from.  Third party apps are the weakest point, so make sure that you update any security patches or the latest version of them.

---

### Post by santiagoward2000 on 2007-11-26
> **patchido said:**
> maliciuos commands will not harm u unles.... u make does commands.. u dont really need more protection..

That's right! You have to open a terminal and type this commands yourself for them to be "malicious". It's like, in DOS typing:
```
format c:\
```
It can't erase anything unless you type it.
About the AV, unless you share your drive with a Windows computer, you shouldn't worry.
Cheers!

---

### Post by Slakker on 2007-11-26
Even if you do share your drive with a windows partition, there's little cause for alarm.  The Linux filesystem is constructed in such a way that viruses have a hard time breaking in.

---

### Post by glotz on 2007-11-26
If you have windoze on your disk and it get's rootkitted it can subvert Ubuntu on the same box.

---

### Post by Jadephyre on 2007-11-26
well, i guess Linux is pretty safe right now, thanks to it not being an Operating System the Majority of Computer Users have installed on their Box.
Not saying that Linux is bad though... not anymore at least ;)

---

### Post by Slakker on 2007-11-26
Linux never was bad, people were just too stupid to use it.

---

### Post by HermanAB on 2007-11-26
Popularity has nothing to do with security (or lack thereof).  If it was true, then Linux would have had worse security than Windows, since there are a lot more Linux systems in the world than Windows systems!  

There are only about 600 million Windows systems.  However, there are at least 2 billion Linux systems, a tiny minority of which are desktop systems.  Most Linux systems are embedded - cell phones, routers, phone switches, control systems,  servers and also super computers.

The difference between Linux and Windows is that Linux is secure by design, while Windows (all versions) is insecure by design.

---

### Post by barney385 on 2007-11-26
cryptography is a better way to determine " security "

---

### Post by lespaul_rentals on 2007-11-26
Viruses and spyware are not a large problem in Linux, and even firewalls are somewhat optional considering the only ports that are open are ones that you have services running on, I.E. BitTorrent clients or system monitoring daemons.  It's all up to you, and as long as you don't go running around Jack's Porn Shack and downloading 200 KB files from the gNutella network you should be fine.

You did ask, however, so I will be more than happy to help you out if you are still interested.  ClamAV seems to be one of the more popular applications.  I believe it's available by typing:

```
sudo apt-get install clamav
```

That should give you the GUI interface for whichever desktop enviroment you use.  If it somehow doesn't, just let us know, we'll help you get it.

As for the malicious code that you are afraid of, don't worry about that!  Just don't type "sudo rm rf" or anything that looks like it.  If you are uncertain about a certain code, ask one of us.  You can even PM me if you want, I can tell you if something's legit or not.  Those codes can be executed by the local super-user only.  That means **you**.  So don't worry about that stuff.

Just update your system, be smart about what you download, don't run malicious codes, and you will be 100% a-okay.  :)

Let me know if you need any help.

---

### Post by Paulmd on 2007-11-27
> **Slakker said:**
> Linux never was bad, people were just too stupid to use it.

Being harder to figure out than the competition is bad. People haven't gotten smarter, Linux has gotten easier to use.

---

### Post by Paulmd on 2007-11-27
> **JasonBourneLinux said:**
> hey,

Ive read other threads but are there good apps (lol graphical- for me, a noob) fo anti-virus and spyware? I know Linux is pretty darn secure but I get nightmares after reading the thread bout the malicious commands (and I share this one partition with a windows installation)

thanks for the help!!

Ubuntu w/ desktop effects > Windows XP

^_^

If you routinely send cute attachments in email to other people, an antivirus is a courtesy to the public. It's not nice to be the digital equivalent of Typhoid Mary.

An antivirus can also be handy in a linux dual boot situation, as you can use it to clean your Windows partition. (Some of them you can, anyway)

---

