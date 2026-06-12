---
title: "Applications-&gt;Add remove Programs, Will not work"
date: 2008-04-14
forum: Absolute Beginner Talk
---

### Post by LordOOTFD on 2008-04-14
Alrighty I have Ubuntu 7.10
I boot Applications-> Add remove programs and search for anything, for example aMSN.
double clicking or clicking on the box to the left of the entry that shows up generates the following message:

The list of applications is not availabe

Click on 'Reload' to load it. To reload the list you need a working internet connection.

I hit refresh, It asks for admin password, I enter it, then it says something about downloading package lists or something, finishes and then the add/remove programs window refreshes, and goes back to normal. nothing has installed, and this repeats every time I click on it.

Now next I did this

Open terminal, and enter "sudo apt-get install aMSN" (I cut the command base from a sample in the restricted formats tutorial, it also fails when I sue if for sound converter) which asks for the admin password, however the terminal stops responding to any keyboard activity and sinply sits with a black blinking entry redicule doing nothing.

I then looked arround fo this and I found th suggestion, to go to System->Administrator->synaptic package manager and hit reload, and then retry Add-remove programs, after this the original results repeat.

my system is a dualboot Vista-Ubuntu machine, with a fairly small Ubuntu partition, and a clean Ubuntu install. I can't find anything about this problem and It's quite infuriating.
I have an active internet connection.

---

### Post by PmDematagoda on 2008-04-14
Go to Software Sources in System>Administration>Software Sources and select all the choices except for the installation CD-ROM and then reload the sources list again. Then check Add/Remove again.

---

### Post by LordOOTFD on 2008-04-14
It works now, Thanks a bunch

---

### Post by stchman on 2008-04-14
> **LordOOTFD said:**
> Alrighty I have Ubuntu 7.10
I boot Applications-> Add remove programs and search for anything, for example aMSN.
double clicking or clicking on the box to the left of the entry that shows up generates the following message:

The list of applications is not availabe

Click on 'Reload' to load it. To reload the list you need a working internet connection.

I hit refresh, It asks for admin password, I enter it, then it says something about downloading package lists or something, finishes and then the add/remove programs window refreshes, and goes back to normal. nothing has installed, and this repeats every time I click on it.

Now next I did this

Open terminal, and enter "sudo apt-get install aMSN" (I cut the command base from a sample in the restricted formats tutorial, it also fails when I sue if for sound converter) which asks for the admin password, however the terminal stops responding to any keyboard activity and sinply sits with a black blinking entry redicule doing nothing.

I then looked arround fo this and I found th suggestion, to go to System->Administrator->synaptic package manager and hit reload, and then retry Add-remove programs, after this the original results repeat.

my system is a dualboot Vista-Ubuntu machine, with a fairly small Ubuntu partition, and a clean Ubuntu install. I can't find anything about this problem and It's quite infuriating.
I have an active internet connection.

What kind of internet access do you have?  Cable, DSL, dialup?  Make sure you are connected to the internet.  I know, but start with the simple stuff first.

Make sure you have all your repositories enabled after you confirm you have internet access.

Also give Ubuntu at least 10GB, my install is 25GB for the OS.

---

