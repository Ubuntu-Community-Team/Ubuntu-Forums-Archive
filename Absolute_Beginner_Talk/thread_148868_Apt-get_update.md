---
title: "Apt-get update"
date: 2006-03-22
forum: Absolute Beginner Talk
---

### Post by juliodj on 2006-03-22
Is there a way to save the information downloaded when I use the update command? Each time I shutdown and restart my computer, then *apt-get update*, it start from the beginning each time. Why the system don't save that information?

---

### Post by Sutekh on 2006-03-22
[QUOTE=juliodj]Is there a way to save the information downloaded when I use the update command? Each time I shutdown and restart my computer, then *apt-get update*, it start from the beginning each time. Why the system don't save that information?[/QUOTE]
[QUOTE=apt-get man page]

update
    **update is used to resynchronize the package index files from their sources**. The indexes of available packages are fetched from the location(s) specified in /etc/apt/sources.list. For example, when using a Debian archive, **this command retrieves and scans the Packages.gz files, so that information about new and updated packages is available**. An update should always be performed before an upgrade or dist-upgrade. Please be aware that the overall progress meter will be incorrect as the size of the package files cannot be known in advance.[/QUOTE]

The whole point of apt-get update is to resyncronise/refresh the packages available from the sources in your /etc/apt/sources.list.  

So everytime you use apt-get update it will download the information again.  Its supposed to.

---

### Post by dragomirov on 2006-03-22
Because if you tell the system to be updated, the system look for updates. 

If you don't "apt-get update" the system keeps information from your last update and doesn't search for more by itself :)

---

### Post by juliodj on 2006-03-22
[QUOTE=Sutekh]The whole point of apt-get update is to resyncronise/refresh the packages available from the sources in your /etc/apt/sources.list.  

So everytime you use apt-get update it will download the information again.  Its supposed to.[/QUOTE]
The issue is that when I update the system and have all the indexed downloaded, reboot and try to install a package that is suppose to be in the index, the system said that it is not available and force me to run update again. It dont keep the information from last update.

Is the system deleting the index at shutdown? If yes, is there a way to prevent it?

---

### Post by Sutekh on 2006-03-22
Ok I think I understand now.  No, the newer information/package list from an apt-get update shouldn't be deleted.  If you apt-get update and then try to install the package and its available, then rebooting should not require you to apt-get update again.

I can't think of why you are having this problem.  What and where is the package you are trying to get?

---

### Post by dragomirov on 2006-03-22
I know it's not an answer. but I experienced the same with Breezy, not between boot and reboot, but across days. It's a kind of date probably. 

Now I'm running Dapper and this doesn't happen any more.

---

### Post by vayu on 2006-03-23
[QUOTE=juliodj]The issue is that when I update the system and have all the indexed downloaded, reboot and try to install a package that is suppose to be in the index, the system said that it is not available and force me to run update again. It dont keep the information from last update.

Is the system deleting the index at shutdown? If yes, is there a way to prevent it?[/QUOTE]


No, the packages on the servers are constantly changing (offering you more and better stuff).  So you may have updated two days ago, but yesterday some package got updated or moved around and your index is now out of sync, so you have to update again.

---

