---
title: "command syntax"
date: 2006-07-12
forum: Absolute Beginner Talk
---

### Post by fjm03 on 2006-07-12
What is the command syntax to recover the kernel version number in U 6.06?

Using the GUI menu path Places >> Computer >> File System returns  "2.6.15-25" for the linux-header paths in /usr/src but I'm not sure that, in fact, is the kernel version.

I have been advised by another 6.06 user they just receieved a notice, through the upgrade icon, that kernel 2.6.15-26 is available as an upgrade. I have not received any upgrade notification and an upgrade check along the menu path System >> Upgrade Manager,  returns "Your system is up-to-date". 

The question arises because of the linux-header path changes necessary to run VMW Server 1.0 if the kernel is upgraded.

Thanks in advance.

---

### Post by ProjectGod on 2006-07-12
uname -a

or

lsb_release -a****

---

### Post by bruenig on 2006-07-12
```
uname -r
``` for just the kernel

---

### Post by fjm03 on 2006-07-13
Thank you both. Did the trick.

---

### Post by fjm03 on 2006-07-16
Resolution of this circumstance was interesting.

As a newbie I thought that the SPM allowed the user to select an application, then automatically selected appropriate dependencies, download the package and applied the download. I also assumed that updates followed the same course allowing the user to select the updates. Apparently not, as Ubuntu approaches updates, anyway.

In this case, the kernel update to 2.6.15-26 was on a "need to know" basis. Apparently, Ubuntu's updater is sophisticalted enough to know the user's repository substricptions or at least the libraries that result from each subscription. Only after I expanded my repository subscriptions did I almost immediately receive notification of the -26 kernel update.

Just as counterintuitive, was SPM's handling of the linux-header files associated with VMWare server installations. When intially installing VMWare server 1.0 on the Dapper host, the SPM automatically brought along linux-headers 2.6.15-25-386 when I selected linux-header 2.6.15-25. This time, however, when preparing to use VMWare's config file on the updated kernel, I requested only linux-header 2.6.15-26, fully expecting SPM to also drag along linux-header 2.6.15-26-386. SPM did not.  Both files had to be installed seperately.

I found this behavior particularly odd since VMWare "dependency" files are probably not statistically insignicant requests.

Interesting.

---

### Post by fjm03 on 2006-07-18
[I]Just as counterintuitive, was SPM's handling of the linux-header files associated with VMWare server installations. When intially installing VMWare server 1.0 on the Dapper host, the SPM automatically brought along linux-headers 2.6.15-25-386 when I selected linux-header 2.6.15-25. This time, however, when preparing to use VMWare's config file on the updated kernel, I requested only linux-header 2.6.15-26, fully expecting SPM to also drag along linux-header 2.6.15-26-386. SPM did not. Both files had to be installed seperately.

I found this behavior particularly odd since VMWare "dependency" files are probably not statistically insignicant requests.[/I]

Posted this 2 days ago. Yesterday, I received an update notification.

You guessed it! Linux-headers 2.6.15-26 and linux-headers 2.6.15-26-386.
I'm left to assume that these files had been modified since I manually uploaded them through SPM last weekend.

Thanks for listening Ubuntu.

---

