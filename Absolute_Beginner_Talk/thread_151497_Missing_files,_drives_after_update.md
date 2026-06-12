---
title: "Missing files, drives after update"
date: 2006-03-28
forum: Absolute Beginner Talk
---

### Post by jlhughes on 2006-03-28
After installing ubuntu, the automatic updates service reported a long list of items needed to be updated. I OK'd the update.  When everything was done, I was alerted that a kernel update required rebooting the machine.

I rebooted the machine.

Before the update, I was able to see a built-in CompactFlash drive that has a card in it. I was also able to see the default local home page in Firefox.

After the update and after the reboot, Firefox reports it can't find /usr/share/ubuntu-artwork/home/index.html.

I have been able to figure out how to use System --> Administration --> Disks to assign the CompactFlash to a directory I created using sudo mkdir /media/compactflash 

I'm still unable to figure why Firefox can't find its original default page.

---

### Post by taurus on 2006-03-28
The obsvious question is does /usr/share/ubuntu-artwork/home/index.html still there?

---

### Post by mrbiscuit on 2006-03-28
Ah, it is just missing the default homepage. I believe that you may have uninstalled the ubuntu-artwork package in Synaptic. Just go to a Terminal and run "sudo apt-get install ubuntu-artwork" (without the quotes of course) and that should work. If not, just assign another homepage.

---

### Post by jlhughes on 2006-03-28
[QUOTE=mrbiscuit]Ah, it is just missing the default homepage. I believe that you may have uninstalled the ubuntu-artwork package in Synaptic. Just go to a Terminal and run "sudo apt-get install ubuntu-artwork" (without the quotes of course) and that should work. If not, just assign another homepage.[/QUOTE]

**Keeping in mind that this is the *REALLY* newbie forum . . . **

When I run the command sudo apt-get install ubuntu-artwork I get this response:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.

I have crashed this system several times after the initial install (but I'm doing better now). Before I learned about Crtl-Alt-Backspace I was forced to power down to get out. I am more than willing to believe I may have corrupted some files that were open when the system crashed.

And, in response to the earlier question about about whether the /usr/share/ubuntu-artwork directory exists, the answer is yes. It contains the ubuntu.css file but nothing else that I can see.

---

### Post by Mustard on 2006-03-28
[QUOTE=jlhughes]**Keeping in mind that this is the *REALLY* newbie forum . . . **

When I run the command sudo apt-get install ubuntu-artwork I get this response:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.

I have crashed this system several times after the initial install (but I'm doing better now). Before I learned about Crtl-Alt-Backspace I was forced to power down to get out. I am more than willing to believe I may have corrupted some files that were open when the system crashed.

And, in response to the earlier question about about whether the /usr/share/ubuntu-artwork directory exists, the answer is yes. It contains the ubuntu.css file but nothing else that I can see.[/QUOTE]


I would suggest you run the command suggested by apt-get as it seems there is still some configuration that needs to be done...

```
sudo dpkg --configure -a
```

---

### Post by jlhughes on 2006-03-28
I am unable to install applications with the Add Applications tool. 

This is the error message I get when I launch the tool:

Unable to get exclusive lock

This usually means that another package management application (like apt-get or aptitude) already running. Please close that application first

I rebooted the machine, but I continue to get this message.

---

### Post by jlhughes on 2006-03-28
[QUOTE=Mustard]

```
sudo dpkg --configure -a
```[/QUOTE]

This fixed the problem with the Add Application problem I reported.

---

### Post by mrbiscuit on 2006-03-30
When you tried to run dpkg, was Synaptic or anything that would use dpkg open? I hope this is somewhat helping.

---

### Post by mrbiscuit on 2006-03-30
Try running Synaptic, it should tell you what is wrong, and tell you how to fix it with a nice GUI, considering your ubuntu-artwork package is missing, some package must be broken.

---

