---
title: "Upgrading Software (Repositories?)"
date: 2008-04-05
forum: Absolute Beginner Talk
---

### Post by Ravorion on 2008-04-05
After my brief experience with Ubuntu 8.04 I decided to be on the safe side and install Ubuntu 7.10 for now. But like my previous Linux attempts I am confused with how Linux stores files and installs/upgrades software. Been checking out several websites and forums, skimming trough them to find a good guide or something, but no succes so far. I was wondering how exactly you are suppose to get your installed pograms (say Firefox, Openoffice, Pidgin) up to date without resorting to downloading the .deb from websites. I know it has something to do with repositories, but I don't really know which custom ones i should add to upgrade these software packages to their latest versions.

For example.. Ubuntu 7.10 comes with Pidgin 2.2.1 and Ubuntu 8.04 with 2.4.0, but the Pidgin already has a 2.4.1 version. Ubuntu 7.10 has a Firefox 2.0 while Ubuntu 8.04 is using the newer Firefox 3 already. I tried checking the Synaptic Package Manager and found a Firefox 3 in there, but I think it was an alpha version instead of the beta ones you can find on the Firefox website. I removed Firefox 2 and installed the Firefox from the SPM to test, but I had no clue how to exactly start up the new Firefox (which is my problem with how Linux stores files ;))

So are there some well known third party repositories that let me update software like Firefox, Pidgin and such automaticly or should I get used to working with older versions until Ubuntu makes new releases every 6 months ?

---

### Post by djnm on 2008-04-05
If you run...
```
sudo apt-get upgrade
```
it should upgrade :) the packages you have on your computer to the newest versions in the Ubuntu repos for 7.10.

Hope this helps

EDIT: Or, correct me if I'm wrong, you could add the 8.04 repos and get the packages from there?

---

### Post by Inxsible on 2008-04-05
Repos are something that are maintained by ubuntu and it contains all the software installations available for Debian based distros.

They lag behind the actual developers' software simply for the fact that they update repos every so often and therefore cannot include "each and every" update made by the software developers.

Having said that, the repos also sometimes do have the latest and the greatest versions of quite a few softwares.

There are also quite a few forum users who maintain their own repos and you can add those if you want to get some software that is not available in the standard Ubuntu repos.

---

### Post by Amarsingh0793 on 2008-04-05
I don't know any 3rd Party Repositories, but you must know that some 3rd Party repositories can be dangerous. Only get 3rd party repositories from trusted sources.

Good Luck and be cautious :)

---

### Post by Ravorion on 2008-04-05
Thanks for the quick replies !!

#djnm: I've done the "sudo apt-get upgrade" before, but it did not upgrade Firefox, Pidgin etc at all :S. That command line is basically the same as using the Update Manager or Synaptic Package Manager is it not ? Using the 8.04 repo sounds like a very good idea to me, but how would I add that repo to the System - Software Resource menu? Or does it have to be done trough Terminal?

#Inxsible: Ah k. Already thought that the repo system might have a slight delay in it which would explain why 8.04 is using 2.4.0 Pidin and not 2.4.1 :)

#Amarsingh0793: Yea I've noticed many people and guides mention to be careful with 3rd party repo's. So I'll refrain from using those till I have a better understanding of Linux. Thanks for the warning. :D

---

### Post by Inxsible on 2008-04-05
What's the rush?

Hardy(8.04) releases on the 24th of april. Just wait on it and you will not only upgrade your repos, but your OS as well.

---

### Post by Ravorion on 2008-04-05
Well I'd thought I'd start using Linux already, figure out how things work in Linux instead of waiting. :) Knowing how to use new repos and upgrading software seems handy to know no matter what Ubuntu release is out ?

---

### Post by Martje_001 on 2008-04-05
The reprosities only get updated, when there is a security problem in the software, or if it's very critical. That's the reason you don't get 'bleeding edge' software.

---

### Post by zvacet on 2008-04-05
You can download latest Pidgin from [here.](http://www.getdeb.net/search.php?keywords=pidgin)

---

### Post by Ravorion on 2008-04-05
I've attempted to install the 2.4.1 Pidgin from that site, but I couldn't manage to get it working. I downloaded the 3 pidgin files and used the standard GDeb on pidgin-data to install Pidgin (after removing the older Pidgin) and had no idea how to actually start the Pidgin 2.4.1 I just installed. :oops:

EDIT: After removing the older Pidgin the normal start place: Applications -> Internet -> Pidgin was gone so no clue how to start it up otherwise

---

### Post by conscious on 2008-04-05
You will find a good answer here: [https://help.ubuntu.com/community/UbuntuBackports]("https://help.ubuntu.com/community/UbuntuBackports").

In short, upgraded version of packages are available through the backports repository. Not all software gets backported though.

---

### Post by Ravorion on 2008-04-05
Read trough the page. A very good link, thank you!

If I understand it correctly it's a smart thing to enable the "proposed" and "backport" options in System -> Administration -> Software Sources -> Updates so you get more up to date packages for certain software ?

Will Update Manager automatically update the software that I have installed from that backport repo or do I have to do something in the Synaptic Packet Manager and/or in Terminal?

Sorry for all these questions, but this is basically the only problem I have with switching to Linux. Installing, upgrading and running programs is quite confusing for me in Linux because I've become very used to Windows (unfortunately :().

Thanks for all the replies so far though.

---

### Post by conscious on 2008-04-05
> **Ravorion said:**
> If I understand it correctly it's a smart thing to enable the "proposed" and "backport" options in System -> Administration -> Software Sources -> Updates so you get more up to date packages for certain software ?
This will certainly get you closer to the bleeding edge, and this seems to be what you want.

> **Ravorion said:**
> Will Update Manager automatically update the software that I have installed from that backport repo or do I have to do something in the Synaptic Packet Manager and/or in Terminal?
In the same dialog, you can choose the frequency of updates and automatic actions. As I understand it, only security updates can be installed automatically, but you will get a notification when others are available.

---

### Post by zvacet on 2008-04-05
You need to download and install all packages from site.

---

### Post by Ravorion on 2008-04-05
How you mean "from site" ? Which site exactly ? Or do you mean I shouldn't forget to download and install all the packages the Update Manager shows me ? :)

Btw I managed to install Pidgin 2.4.1 from  [http://www.getdeb.net/search.php?keywords=pidgin]("http://www.getdeb.net/search.php?keywords=pidgin")! Forgot to properly install the other 2 packages from the site so it didn't work at first.

Slowly but steadily starting to get the hang of this. :D

---

### Post by zvacet on 2008-04-06
> Forgot to properly install the other 2 packages from the site so it didn't work at first.

That is what I´m try to tell you.

---

### Post by Ravorion on 2008-04-06
Ah k sorry! :oops:

Yea the first time I downloaded all of them, but I thought by installing the pidgin-data it would use the other 2 packages and install the program, but that was just my Windows lazy thinking. So the second time I used all of the 3 packages and it worked. :)

---

### Post by Sef on 2008-04-06
There are two types of distro releases:

A) Time release, like Ubuntu, which software only gets updated when the new operating system version comes out.  (With exceptiions as noted in previous posts.)

B) Rolling release, like Arch, which updates when a new product version comes out.

---

