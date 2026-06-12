---
title: "how do i delete extraneous (leftover) files after removing a program"
date: 2007-07-20
forum: Absolute Beginner Talk
---

### Post by GMachine_24 on 2007-07-20
Hi:

I just removed (as in apt-get remove) the slimserver program from a computer that is running kubuntu 7.04. i knew there would be 'leftover' files after the removal - and now i'm wondering how to get rid of them. some are in the /var/cache/slimserver  folder; in fact, almost all of them are. a few are log files; the remainder (about 20) are listed under /etc/<something>/slimserver or /etc/<something>/S20slimserver, etc.

I checked the slimdevices site with no luck. I can't imagine removing these files will cause any problems; fortunately I back up my complete system every day so even if something blows getting back to where I am now is not a big to do.

Any ideas??

Thanks in advance.

gm

---

### Post by mikewhatever on 2007-07-20
Are you looking for > sudo apt-get autoremove

---

### Post by Rocket2DMn on 2007-07-20
For future reference, when you uninstall programs, use 
```
sudo apt-get --purge autoremove packagename 
```
This will clear out dependencies and get rid of config files as well.

---

### Post by az on 2007-07-20
> **GMachine_24 said:**
> 

Any ideas??


I seriously doubt that removing those files and folders would cause any problems.  

The package manager is responsable for installing each package's files and running install or removal scripts.  It is not responsable for files that are written and saved by the application itself.  For example, the package manager will not remove any configuration files written to /etc or to your home foolder - that's not its job.

Are such leftover files a problem?  Is cleaning them a problem?  I think the latter is more often the case.  For example, if you have a database running and you want to upgrade the server to a new version or to a new type of database server, you don't want your package manager to be forced to erase the existing database as part of the removal of the old version and installation of the new version.

So, I guess the answer depends on each individual package.  And each upstream project will have its own opinion about how this is handled.

---

### Post by GMachine_24 on 2007-07-20
Thanks to everyone for the prompt and helpful replies.

I suppose I should have mentioned the reason I wanted to remove all files related to slimserver is that I was having lots of problems and thought about installing a different Linux version - when i first used slimserver it was on an fc4 box and it ran more or less flawlessly. since the sad demise of that computer, i decided to upgrade to ubuntu on all my linux computers - i guess i should mention i attempted to use ubuntu to run slimserver but it froze all the time and was just a mess to work with, which is why i went with fc4 (this is a couple years ago).

now there are only two linux slimserver options - .rpm and .deb. i am still having issues with the ubuntu version install - it works... but usually freezes after a few songs and takes quite awhile to load the list of songs from the server; this used to take less than 15 seconds and now can take minutes.

anyway, i tried the .rpm package via alien and it did not work at all. so now i am back to the .deb package and hopefully i will be able to figure out what's wrong.

thanks again for your help.

gm

---

