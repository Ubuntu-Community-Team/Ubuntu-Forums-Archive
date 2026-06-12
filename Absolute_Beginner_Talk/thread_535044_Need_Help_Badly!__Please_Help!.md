---
title: "Need Help Badly!  Please Help!"
date: 2007-08-26
forum: Absolute Beginner Talk
---

### Post by Fonon on 2007-08-26
have a problem, as I stated. I tried to install Virtual Box, but I stopped after I installed all the stuff, because the installation was getting no where. However, the .deb window wouldn't close, so I ignored. Eventually, I had to turn off my computer so I could fix my wireless card. Now, I get this error when trying to install updates, and when starting Synaptic Package Manager:

Could not initialize the package information

A unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:The package virtualbox needs to be reinstalled, but I can't find an archive for it.'

Also, whenever I am in Add/Remove, when I try to check something, I get the loading signal, and it never stops, thus I am not able to install something from there. Could someone please help me with this problem?

I posted this in another thread, but no one was recognizing it...so I thought perhaps a better title would help it.

---

### Post by Fonon on 2007-08-26
Bump for help

---

### Post by wormser on 2007-08-26
Here is something to try.  Applications> Accessories> Terminal.

```
sudo apt-get clean
```
```
sudo apt-get update
```
```
sudo apt-get upgrade
```

---

### Post by Fonon on 2007-08-26
The first command freezes my terminal...but it doesn't matter anymore, I figure now i'll just upgrade to kubuntu.

---

### Post by some_random_noob on 2007-08-26
> **Fonon said:**
> The first command freezes my terminal...but it doesn't matter anymore, I figure now i'll just upgrade to kubuntu.
True, but you should learn to fix the problem. Try and kill virtualbox to avoid getting that error - try to uninstall it via apt. Then do a search for it and try deleting some stuff. You should easily be able to fix this problem without reinstalling your OS. My shutdown button disappeared once, so I uninstalled some software which I figured was dodgy, and then I got my shutdown button back. My computer also seemed to terminate processes more efficiently when shutting down :D 

(Lots of fun!)

---

### Post by Warren Watts on 2007-08-26
Note : After I read everything I wrote below, I realized it may be a bit off-topic, but here's my two cents anyway... :-)> **some_random_noob said:**
> True, but you should learn to fix the problem.
I'll drink to that!  Too many people experience some sort of problem, have difficulty resolving the issue, and their solution is to reinstall, upgrade, or just plain abandon the OS.

It's MUCH more productive to work your way through the problem, so if it occurs again, you are prepared and know what caused it and what needs to be done to remedy it.  Reinstalling the OS is a workable solution if you haven't had the OS up and running long, but when three months have gone by and you have tweaked and tuned your system just the way you want it and have large amounts of  irreplaceable data, reinstalling the OS is not really something you want to have to do.

In a case like that, knowing how to fix it is a Godsend. 

I think that the urge to reinstall has it's roots in closed source OS's; when something goes wrong, reinstalling the OS is your only choice.  The only people who know a closed source OS inside and out are the vendors themselves, and good luck getting a resolution from them!

Open Source is different in that respect; the knowledge base is immense.  There are thousands of people worldwide you can call upon to help you.  You may not get a to-the-letter solution to the issue you face, but I guarantee you will get plenty of worthwhile suggestions that may point you to an exact solution.

So don't give up yet!  There is probably someone out there who can help!

---

### Post by some_random_noob on 2007-08-26
> **Warren Watts said:**
> Note : After I read everything I wrote below, I realized it may be a bit off-topic, but here's my two cents anyway... :-)
I'll drink to that!  Too many people experience some sort of problem, have difficulty resolving the issue, and their solution is to reinstall, upgrade, or just plain abandon the OS.

It's MUCH more productive to work your way through the problem, so if it occurs again, you are prepared and know what caused it and what needs to be done to remedy it.  Reinstalling the OS is a workable solution if you haven't had the OS up and running long, but when three months have gone by and you have tweaked and tuned your system just the way you want it and have large amounts of  irreplaceable data, reinstalling the OS is not really something you want to have to do.

In a case like that, knowing how to fix it is a Godsend. 

I think that the urge to reinstall has it's roots in closed source OS's; when something goes wrong, reinstalling the OS is your only choice.  The only people who know a closed source OS inside and out are the vendors themselves, and good luck getting a resolution from them!

Open Source is different in that respect; the knowledge base is immense.  There are thousands of people worldwide you can call upon to help you.  You may not get a to-the-letter solution to the issue you face, but I guarantee you will get plenty of worthwhile suggestions that may point you to an exact solution.

So don't give up yet!  There is probably someone out there who can help!
I'll drink to that response :D

I have reinstalled MANY times myself. I claim to be really talented with Linux and computers, yet I sometimes edit configuration files without making backups. Or I just mess around for ages trying to fix something, then forget what I did. The second one is probably because I get really desperate to fix stuff. I've been careful more recently.

I hate reinstalling, it should only happen once a year or so. But I mainly use my computer for experimental purposes anyway, so I always screw stuff up. I've figured that I've learnt enough now, and I'm trying to keep my installations for longer. I also try troubleshooting more often, and it pays off heaps! :)

I had heaps of ports open recently from services that I installed. Did I reformat? Hell no! I used nmap, netstat -lntp, ps -e and "kill". The result? No ports open. So easy that a 16 yearold can do it :lolflag: I'm very pleased with myself.

---

