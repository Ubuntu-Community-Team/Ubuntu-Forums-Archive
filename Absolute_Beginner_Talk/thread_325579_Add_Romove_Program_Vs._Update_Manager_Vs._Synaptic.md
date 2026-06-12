---
title: "Add Romove Program Vs. Update Manager Vs. Synaptic Package Manager"
date: 2006-12-26
forum: Absolute Beginner Talk
---

### Post by lucky_chouhan on 2006-12-26
Hi i want to know what is the difference between 

1. Add Romove Program 
2. Update Manager 
3. Synaptic Package Manager

:confused:

---

### Post by NeoLithium on 2006-12-26
The update manager, basically scans the repositories you have enabled, and checks for updates on your currently installed software; it will just automatically pop up a message when there are updates available.

Synaptic Package manager is the Graphical version of using aptitude; uses the repositories, of course.  You can install any of the programs available with the repositories that you have set up; and it will also install the dependencies, if any are lacking.

As for the add/remove program, *chuckles* I don't think I've ever even opened it...

---

### Post by thistransition on 2006-12-26
add remove programs installs programs that have been approved by the ubuntu community
this is where you will find new programs that you will want.

update manager ( i think ) updates your system with security updates that you should not decline

synaptic package manager is Add/Remove prgrms except it is much more specific.  each program has certain packages it uses.  for example, rhythmbox has different packages it uses and to listen to mp3s you need to install certain packages that it will use.

hope it was some help. i dont know all that much, but it seems that should give you a decent idea.

---

### Post by user1397 on 2006-12-26
> **NeoLithium said:**
> The update manager, basically scans the repositories you have enabled, and checks for updates on your currently installed software; it will just automatically pop up a message when there are updates available.

Synaptic Package manager is the Graphical version of using aptitude; uses the repositories, of course.  You can install any of the programs available with the repositories that you have set up; and it will also install the dependencies, if any are lacking.

As for the add/remove program, *chuckles* I don't think I've ever even opened it...synaptic really uses aptitude?  i always thought it used apt-get... (can someone test this? cause I'm on windows right now)

---

### Post by NeoLithium on 2006-12-26
> **erik1397 said:**
> synaptic really uses aptitude?  i always thought it used apt-get... (can someone test this? cause I'm on windows right now)

You're right, I'm wrong. Apt-get. Whoops :)

---

### Post by k1001001 on 2006-12-26
Nevermind. Ignore post.

---

### Post by hyperair on 2006-12-26
Actually, update-manager handles the updates of all packages. It just finds out the version of the packages installed and the versions of the packages available and then prompts you to install it.

Another thing, Synaptic package manager, aptitude, apt-get, and update-manager work on the same repositories.

Difference between aptitude and apt-get: aptitude downloads and installs recommended packages as well.

---

### Post by Sef on 2006-12-26
Aptitude handles dependencies better than apt-get.   If you install and then remove a program with aptitude it will take off all the dependencies unlike apt-get.

---

### Post by spockrock on 2006-12-26
in edgy apt-get also has an auto remove functionality.......

---

