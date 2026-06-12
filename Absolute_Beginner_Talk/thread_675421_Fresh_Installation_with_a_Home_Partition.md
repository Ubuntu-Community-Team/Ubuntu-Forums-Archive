---
title: "Fresh Installation with a Home Partition"
date: 2008-01-22
forum: Absolute Beginner Talk
---

### Post by intense.ego on 2008-01-22
After much effort I have managed to creat a seperate /home partition. I want to install Gutsy on my computer (I currently have Feisty), but want to keep the /home folder, all the user data,the themes and splash screen, the settings, and the applications, etc. How exactly do I do this? Please be somewhat detailed because I am prone to be indecisive otherwise.

---

### Post by bodhi.zazen on 2008-01-22
just go ahead and install

At the partitioning step, add the partition as /home 

DO NOT FORMAT IT

---

### Post by intense.ego on 2008-01-23
Will all my applications (including ms office which i installed with crossover) still be there and work well?

---

### Post by bumanie on 2008-01-23
Do not make a new /swap or /home. Only make a new /root for gutsy to install to and you should be fine. Obviously, you'll have to choose manual partitioning or else gutsy will install itself to an area you don't want it to go.

---

### Post by intense.ego on 2008-01-23
So should I make the new /root over the old feisty /root, or will that delete some application data/customized settings?

---

### Post by mivo on 2008-01-23
> **intense.ego said:**
> Will all my applications (including ms office which i installed with crossover) still be there and work well?

I don't know about Crossover Office since I never used it, but Linux applications are not kept in your home directory. Data is kept there, as well as configuration files. You'll probably have to reinstall your applications, but you won't (usually) have to re-configure them. (Which, personally, I feel is often  the bulk of the work, whereas installing the software is painless and fast.)

Now, it may be different for the Windows programs you use/emulate. If you use Wine, the Windows software _is_ kept on the home partition and it would work still after reinstalling the OS (provided there are no other issues). Crossover may work similarly, but like I said, I have never used it, so can't say much about it.

---

### Post by intense.ego on 2008-01-23
I do believe it is the same with crossover as it is based on wine. Installing all the applications again shouldn't be a problem, except for one important one. This is "Remotedesktop Client." I forgot how I installed it, but i will have a look through my posts on the forum and see whether or not I found out from the forums.

---

### Post by mivo on 2008-01-23
> **intense.ego said:**
> So should I make the new /root over the old feisty /root, or will that delete some application data/customized settings?

Ideally, for most people, there should be three partitions:  10 GB for /, rest for /home, and 1-2 GB for swap. Now, if you do not already have a layout like this, there may be issues. At the very least, you need a separate /home partition, which you said you have. In that case you need to specify the "mount point" for this partition (and name it /home), and DO NOT check the "format" box. The "system" itself should be placed where the respective Feisty partitions were at (these need to be formatted during installation, overwriting without formatting will cause trouble). This will overwrite the system files and such, but not the data and most of your customized settings that are stored in /home (there are settings in /etc too, but you'll have to redo that -- trying to backup much here will lead to chaos and possibly to an unstable system).

How is your drive currently partitioned?

---

### Post by maybeway36 on 2008-01-23
Put the new root over the old root, but format it. This will get rid of the Feisty root, though, so be careful.

---

### Post by intense.ego on 2008-01-23
My hardrive is currently partionioned 38gb for home, 10gb for all the rest, and 1.1gb for swap. I also have a windows partition, but that shouldn't be relevant.

---

### Post by mivo on 2008-01-23
I should add this: I know it's a bit of "broken record" type of advice, but if you have the option, do backup your data before you upgrade your system. At least the important stuff, like text documents, pictures, etc ... just the things that would be hard or impossible to get back. The easiest way is to compress them into a file and burn them on a CD or DVD. An external drive is better. If you don't format /home, there most likely won't be problems, but it's better to invest a bit of extra time than to bite into the table in frustration later on if something does go wrong.

There also may be some Gnome related configuration issues,  so I usually delete the Gnome settings when upgrading a box, but this may or may not happen and can be manually fixed. Just mentioning it for completitions sake. Upgrading from Feisty to Gutsy can be a little touchy and it's not the most perfectioned and stable process. Better would be to backup /home, format the disk and install Gutsy from scratch, though I realise this means some extra work.

---

### Post by mivo on 2008-01-23
> **intense.ego said:**
> My hardrive is currently partionioned 38gb for home, 10gb for all the rest, and 1.1gb for swap. I also have a windows partition, but that shouldn't be relevant.

That looks good, almost perfect even! :)  So, yes, you start the installer from the live CD, select manual partitioning (not guided or any such), then use the mount points "/home" for the 38 GB partition, "/" for the 10 GB partition, and "swap" for the 1.1 GB one (minus quotation marks). Sometimes you can choose the mount points from a drop-down menu, sometimes you have to type them in manually. Check the "format" box for / and swap, and leave it blank for /home. This should work flawlessly, save for possible issues with Gnome config files (like, misplaced icons, or too large icons -- that's fixable and may not even happen).

I think you're good to go! Do make backups, though. ;)

---

### Post by intense.ego on 2008-01-23
I read in a previous thread that i should back up some things like xorg.conf and perhaps the sources.list so that that can remain the same after installation.

---

### Post by mivo on 2008-01-23
Backuping up xorg.conf is a good idea if you modified it heavily. If not, the Ubuntu installer is pretty good at creating a new one. If your sources.list is long, backup it up as well. 

You can also create a list of currently installed software by using this command:

```
dpkg --get-selections > installed-software
```

And if you want to automatically re-install all the same programs after installing the new version of Ubuntu, you can use these two commands (provided you kept the "installed-software" file and the sources.list is the same):

 ```
dpkg --set-selections < installed-software
dselect
```

---

### Post by intense.ego on 2008-01-23
Thanks! that would prove very useful. However, this only applies to applications installed via apt or from the repos, right?

---

### Post by mivo on 2008-01-23
Yes, both, via apt or Synaptic/Aptitude/etc, and also via the manual .deb-files installer, and dependencies that were auto-installed. But it doesn't cover any Windows programs installed via Wine/Crossover/etc. Still, it should take care most of your applications and get you back up running with only minimal manual work.

You might want to run this here before creating a list:

```
sudo apt-get autoremove
```

It'll remove unused and obsolete dependencies from your system. Unless you install/uninstall software per Aptitude, obsolete dependencies are usually not removed and just linger around (it's not necessarily a problem unless you are low on space). As always, though, anything that removes files automatically is potentially troublesome and backups are recommended. Unless you installed and then uninstalled a lot of programs in the past, I'd skip the cleanup/autoremove. But I wanted to include it as a possible option to trim down the list to what you actually use in case there is a lot of baggage.

---

