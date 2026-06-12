---
title: "clearing an update manager error - how to?"
date: 2007-08-27
forum: Absolute Beginner Talk
---

### Post by HarmonicaGoldfish on 2007-08-27
For the past week or more I have been receiving an error in update manager that makes it so it can not complete the update process for one update (screenlets). 

Evidently this update is not going to happen, however it constantly reminds me of this update.

How can I clear the update manager of this broken update? Or can I?

Also, How can I remove the screenlets program that is causing this?

I tried using add/remove and there is nothing under screenlet or flower screenlet in the list.

The message I get is:

E: /var/cache/apt/archives/screenlets_0.0.10-3_i386.deb: trying to overwrite `/usr/share/applications/FlowerScreenlet.desktop', which is also in package screenlets-core

THANKS!

---

### Post by ellgor on 2007-08-27
Hi,
 
Try this, open up synaptic manager and enable all repo's, click on Mark all Upgrades and then click on Apply, it will cycle through its regular process and you end up with a little window telling you how bad things are, close the little window and if you look at the repositries list the offending package(s) will be highlighted in yellow, right click on the highlighted package and click on remove completely, from the drop down list and click on apply,hopefully this will purge the offending package and reload it for you.

Regards, Ellgor.

---

### Post by Harpoon on 2007-08-27
I pulled up the synaptics package manager and searched for anything with "screenlet" in the name or description.  It returned nothing.

This probably means that you installed it in some other way- - either with dpkg (the package installer for "deb" files), or perhaps from a tarball (.tar).  If this is true, synaptics cannot help you remove it.  If you used dpkg, then try "dpkg -r program_name" (without the quotes).  Of course, change program_name to the correct name of this application (try screenlets, for that name, first).

if it is from a tarball, I am not sure what to tell you except find the original file you instlled from, open it in an archive manager, and hope is says something about uninstalling the package.

I hope this helps and goes smoothly for you.

---

### Post by ShdwNova on 2007-08-28
I am having the exact same problem. I used the Falcon repositories to install screenlets: [HTML]http://hendrik.kaju.pri.ee/[/HTML]
Here are the relevant entries in sources.list:
```
deb http://hendrik.kaju.pri.ee/ubuntu feisty screenlets
deb-src http://hendrik.kaju.pri.ee/ubuntu feisty screenlets
```
At first, I just couldn't update or remove screenlets. After ignoring the problem for a few days, it somehow got worse. Now I can no longer update any program using apt-get. 
I get this error message when I try:
```
E: Could not get lock /var/cache/apt/archives/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the download directory

```
After reading a post about a similar problem in Red Hat, which you can find here:
[HTML]http://www.linuxforums.org/forum/yoper-linux-help/18223-apt-get-problem.html[/HTML]
I deleted /var/cache/apt/archives/lock (backing it up first, of course) and that fixed my problem with updating all programs, except for Screenlets which threw this error when I ran apt-get update:
```
Errors were encountered while processing:
 /var/cache/apt/archives/screenlets_0.0.10-3_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```
I couldn't update it, but luckily I could remove screenlets using:
```
apt-get remove screenlets
```
I'm still not quite sure how this problem began but hopefully some of this can help those with similar problems. Good luck.

---

### Post by HarmonicaGoldfish on 2007-08-28
Thanks for all of the great tips!

I used 

sudo apt-get remove screenlets 

(seemed the simplest :) )

and then was prompted to do 

sudo apt-get autoremove

It all seems to have worked since the orange update notification icon disappeared. Though I did get this comment:

dpkg - warning: while removing screenlets-utils, directory `/usr/local/share/applications' not empty so not removed.

The only thing there is a file called mimeinfo.cache, which appears empty and seems to be locked - there is a little orange lock above it. 

What is that?

---

### Post by satkata on 2007-08-30
With screenlets 0.0.10 everything you need is in all-in-one package.

There's is no screenlets-core, etc. anymore.

That means, that you have to uninstall every screenlets package first, before you upgrade, else you will get the above described errors.

And you shouldn't delete packages under /var/cache/apt from the command-line. This could mislead synaptic as it keeps track of them. Just go in Synaptic--> Preferences-->Files Tab and select "delete cached files"

To avoid future errors, where you have deleted the old packages, but you still can't install the new ones, you should select "Delete Downloaded packages after installation", because in some cases the old packages are still kept in the cache. This option also means, that synaptic will download every package again, even if you've downloaded it 2min before.

Back to screenlets, ones you've uninstalled all packages with the "--purge" option from the command-line or from synaptic "Mark for complete remove", you will see only one screenlets packages, which as i said contains everything you need.

Just install and be happy.
After that under System->Preferences->Screenlets you can start them

You also no longer have to add a start option under your Session menu to start them.
In the screenlets-manager window you have the "automatically start at login" option. Select it and it adds the necessary entries under ~/.config/autostart

I hope, this will help you solve your problems.

---

### Post by HarmonicaGoldfish on 2007-09-01
Thanks for the help. I've started to use gdesklets instead. I was looking to remove screenlets from my computer, and the advice I received from ShdwNova to use:

> apt-get remove screenlets

worked just fine!

If I ever want to reinstall them I will follow your advice.

---

