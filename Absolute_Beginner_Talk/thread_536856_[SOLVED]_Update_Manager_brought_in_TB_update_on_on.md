---
title: "[SOLVED] Update Manager brought in TB update on one computer, isn't giving on other"
date: 2007-08-28
forum: Absolute Beginner Talk
---

### Post by swarup on 2007-08-28
Yesterday a set of updates came into my other computer (also Ubuntu Feisty) for upgrading Thunderbird from 1.5.0.13 to 2.0.0.6. I very much want that upgrade on this computer too, but Update Manager has not put its icon on the top bar of this computer's screen to offer it. So I purposely opened Update Manager and asked it to check for updates, and it checked-- but says everything is up to date.  But everything is NOT "up-to-date". My TB on this computer is version 1.5.0.13 and should be updated to 2.0.0.6. I've been very much waiting for this update (because their is a certain add-on which can only be appended to version 2.0.0.6). Doing the update on one's own without Update Manager's help is not necessarily easy. So now that the official Ubuntu repository TB 2.0.0.6 update is available through Update Manager on my other computer, then why is it not being offered for this computer as well???

---

### Post by ThrobbingBrain66 on 2007-08-28
There are a couple of possibilities here, but the Ubuntu Devs did not upload the new 2.0.0.6 package.  Once an Ubuntu version is released only bug and security fixes are accepted.  And as you can see [here]("http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=thunderbird&searchon=names&subword=1&version=feisty&release=all"), the correct Thunderbird package version in Feisty is 1.5.0.13

1) You installed/updated the Thunderbird package yourself with a script or from the Mozilla site.

OR

2) You have an extra, 3rd party repo on one computer (and not the other) that updated the package.

---

### Post by swarup on 2007-08-28
I see. That is interesting indeed. --I was thinking that the Update Manager would only come up if the Ubuntu Developers had added something. But if it is as you say, i.e. that a 3rd party repo can also prompt the Update Manager to open, and that the Ubuntu Devs did not bring in this 2.0.0.6 update, then I can guess at what may have happened. 

My TB 1.5.0.13 on the other computer was from the Ubuntu repo. But I had very much wanted to upgrade it to 2.0.0.6 so as to get a particular add-on for it only available to the new TB version. So for the past two days I'd been struggling hard to get 2.0.0.6 loaded and running on the computer. I tried using various methods, and succeeded in installing it but could not get it to open. But the failed attempts to load it, had apparently resulted in the addition of  a few things that WERE successful. For example, in one attempt I had installed it using a special method using Ubuntuzilla. It was a load through the terminal window. The install had gone fine, and at the end of the install it asked, "Would you also like to have an automatic updater added, which will prompt you for updates when available?" I chose "yes". After it was all done, I could not get that version of 2.0.0.6 to open on the computer so I removed the "Ubuntuzilla 2.0.0.6" upgrade and just the 2.5.0.0.13 version remained. Actually I had tried that Ubuntuzilla install twice and upon its not working, had uninstalled it both times. BUT some time during all these hours of struggle, the orange Update Manager icon had appeared on the top bar. As I was busy, I had ignored it. But now I clicked on it, and lo and behold, it was the 2.0.0.6 upgrade!!! So I thought to myself, "What a coincidence. After all this struggle of mine, it has all turned out to be unnecessary as the Ubuntu Devs have themselves now offered the upgrade." I thought this to be great, and surely since it was coming from the Ubuntu side, it would work with my system. And indeed it did! But now I see that perhaps that was not at all from the Ubuntu side, but instead was the Ubuntuzilla automatic update. And somehow coming from the angle of the Update Manager, it worked. Could this be what happened? If so, then I'll just have to do the Ubuntuzilla install on this computer as well. Even if the install doesn't work, perhaps the automatic updater will!

---

### Post by nanotube on 2007-08-28
> **swarup said:**
> I see. That is interesting indeed. --I was thinking that the Update Manager would only come up if the Ubuntu Developers had added something. But if it is as you say, i.e. that a 3rd party repo can also prompt the Update Manager to open, and that the Ubuntu Devs did not bring in this 2.0.0.6 update, then I can guess at what may have happened. 

My TB 1.5.0.13 on the other computer was from the Ubuntu repo. But I had very much wanted to upgrade it to 2.0.0.6 so as to get a particular add-on for it only available to the new TB version. So for the past two days I'd been struggling hard to get 2.0.0.6 loaded and running on the computer. I tried using various methods, and succeeded in installing it but could not get it to open. But the failed attempts to load it, had apparently resulted in the addition of  a few things that WERE successful. For example, in one attempt I had installed it using a special method using Ubuntuzilla. It was a load through the terminal window. The install had gone fine, and at the end of the install it asked, "Would you also like to have an automatic updater added, which will prompt you for updates when available?" I chose "yes". After it was all done, I could not get that version of 2.0.0.6 to open on the computer so I removed the "Ubuntuzilla 2.0.0.6" upgrade and just the 2.5.0.0.13 version remained. Actually I had tried that Ubuntuzilla install twice and upon its not working, had uninstalled it both times. BUT some time during all these hours of struggle, the orange Update Manager icon had appeared on the top bar. As I was busy, I had ignored it. But now I clicked on it, and lo and behold, it was the 2.0.0.6 upgrade!!! So I thought to myself, "What a coincidence. After all this struggle of mine, it has all turned out to be unnecessary as the Ubuntu Devs have themselves now offered the upgrade." I thought this to be great, and surely since it was coming from the Ubuntu side, it would work with my system. And indeed it did! But now I see that perhaps that was not at all from the Ubuntu side, but instead was the Ubuntuzilla automatic update. And somehow coming from the angle of the Update Manager, it worked. Could this be what happened? If so, then I'll just have to do the Ubuntuzilla install on this computer as well. Even if the install doesn't work, perhaps the automatic updater will!

well.. ubuntuzilla does not work with the repositories system at all, so there is no way it would have pushed out an update through the update manager. it must have come after you were messing around with other methods (probably the iuculano's feisty backport repository).

don't know why the ubuntuzilla method didn't work for you... what exactly happened when you installed with ubuntuzilla, and then tried to open tb2? any error messages, etc.?

---

### Post by swarup on 2007-08-28
> **nanotube said:**
> well.. ubuntuzilla does not work with the repositories system at all, so there is no way it would have pushed out an update through the update manager. it must have come after you were messing around with other methods (probably the iuculano's feisty backport repository).

Yes, yes I did try that one as well. That must be the iuculano's feisty backport repository then, which resulted in the update. Thanks very much for that piece of insight. Otherwise I was going to try the whole thing with Ubuntuzilla in the other computer. But now I'll just do it with  the iuculano's feisty backport repository.

> **nanotube said:**
> don't know why the ubuntuzilla method didn't work for you... what exactly happened when you installed with ubuntuzilla, and then tried to open tb2? any error messages, etc.?

The whole tale of my efforts along with the suggestions of those helping me, is recorded in this thread:

[http://ubuntuforums.org/showthread.php?t=535652](http://ubuntuforums.org/showthread.php?t=535652)

It starts with the last post on page 1 (posting #10), and goes on from there. You'll find all the details. 

In short, TB 2.0.0.6 would install but wouldn't open. At the end of all my struggle, one person wrote in to say he'd had the same problem, and found out there is a known incompatibility between TB 2.0.0.6 (at least the Ubuntuzilla version) and SCIM. He said there is a workaround for it given in the FAQ of the Ubuntuzilla site. I have SCIM on my computer, and I need it. So I tried the SCIM workaround but it didn't help. I don't know if that was the problem or not. But ultimately when the iuculano's feisty backport repository update appeared in Update Manager, that worked on my computer (despite my having SCIM on it). So the bottom line is, I do not know why Ubuntuzilla did not work on my computer-- but the iuculano's feisty backport repository's Update Manager update certainly did. By the say, my own efforts to get the iuculano's feisty backport repository to work directly, also yielded no fruit. I couldn't get it to make TB 2.0.0.6 open either. That tale is also detailed on the thread I cite above.  But in the end as I say, its Update Manager upgrade did the trick.

So in view of all this, what method would you recommend I use to get TB 2.0.0.6 on my other computer? (It does not have SCIM on it.) --Ubuntuzilla? iuculano's feisty backport repository? or perhaps best would be just use iuculano's feisty backport repository and wait for its upgrade to come in through Update Manager?

---

### Post by nanotube on 2007-08-28
> **swarup said:**
> Yes, yes I did try that one as well. That must be the iuculano's feisty backport repository then, which resulted in the update. Thanks very much for that piece of insight. Otherwise I was going to try the whole thing with Ubuntuzilla in the other computer. But now I'll just do it with  the iuculano's feisty backport repository.



The whole tale of my efforts along with the suggestions of those helping me, is recorded in this thread:

[http://ubuntuforums.org/showthread.php?t=535652](http://ubuntuforums.org/showthread.php?t=535652)

It starts with the last post on page 1 (posting #10), and goes on from there. You'll find all the details. 

In short, TB 2.0.0.6 would install but wouldn't open. At the end of all my struggle, one person wrote in to say he'd had the same problem, and found out there is a known incompatibility between TB 2.0.0.6 (at least the Ubuntuzilla version) and SCIM. He said there is a workaround for it given in the FAQ of the Ubuntuzilla site. I have SCIM on my computer, and I need it. So I tried the SCIM workaround but it didn't help. I don't know if that was the problem or not. But ultimately when the iuculano's feisty backport repository update appeared in Update Manager, that worked on my computer (despite my having SCIM on it). So the bottom line is, I do not know why Ubuntuzilla did not work on my computer-- but the iuculano's feisty backport repository's Update Manager update certainly did. By the say, my own efforts to get the iuculano's feisty backport repository to work directly, also yielded no fruit. I couldn't get it to make TB 2.0.0.6 open either. That tale is also detailed on the thread I cite above.  But in the end as I say, its Update Manager upgrade did the trick.

So in view of all this, what method would you recommend I use to get TB 2.0.0.6 on my other computer? (It does not have SCIM on it.) --Ubuntuzilla? iuculano's feisty backport repository? or perhaps best would be just use iuculano's feisty backport repository and wait for its upgrade to come in through Update Manager?

even though i'm partial to ubuntuzilla, since i wrote it, :) i'd say, if iuculano repository works for you, then you might as well use it and be consistent across your systems.

---

### Post by swarup on 2007-08-28
> **nanotube said:**
> even though i'm partial to ubuntuzilla, since i wrote it, :) i'd say, if iuculano repository works for you, then you might as well use it and be consistent across your systems.

I am impressed-- I must say I thought the whole thing was very smooth. I really enjoyed loading 2.0.0.6 using your setup. The only question in my mind was and still is, why 2.0.0.6 wouldn't open on my computer using your ubuntuzilla? It tried to open, but couldn't. I don't know whether it was the SCIM, but I tried the workaround and it didn't do it. Strange...

On the other computer, whether I use the iuculano or the ubuntuzilla, could you tell me: should I delete the current version of 1.5.0.13 first, or leave it there and do the install? In other words, do either or both these tools have an upgrade feature in them for detecting and upgrading an existing 1.5.0.13, or are they fresh installs which would then best be done by first deleting the existing 1.5.0.13?

---

### Post by nanotube on 2007-08-28
> **swarup said:**
> I am impressed-- I must say I thought the whole thing was very smooth. I really enjoyed loading 2.0.0.6 using your setup. The only question in my mind was and still is, why 2.0.0.6 wouldn't open on my computer using your ubuntuzilla? It tried to open, but couldn't. I don't know whether it was the SCIM, but I tried the workaround and it didn't do it. Strange...

On the other computer, whether I use the iuculano or the ubuntuzilla, could you tell me: should I delete the current version of 1.5.0.13 first, or leave it there and do the install? In other words, do either or both these tools have an upgrade feature in them for detecting and upgrading an existing 1.5.0.13, or are they fresh installs which would then best be done by first deleting the existing 1.5.0.13?

well, my first thought would have been the SCIM, but... it seems that with SCIM tbird actually prints a 'segmentation fault' message, but it didn't do that in your case... so I'm just not sure what it could be. without any error messages, it would take some serious tinkering and troubleshooting to even start having a clue as to what it could be. it's just not worth the trouble, what with the third-party repository methods being available. it clearly is something specific to your setup, because no other reports of the same problem have materialized over the thousands of people who have used ubuntuzilla...

about using the third-party repositories... i don't think it is necessary to uninstall tb 1.5 before installing 2.0 - but it wouldn't hurt to do that, either. so if you wanna "play it safe" you could uninstall tb1.5.

edit: oh, and thanks for your positive comment about ubuntuzilla. :)

---

### Post by swarup on 2007-08-28
> **nanotube said:**
> well, my first thought would have been the SCIM, but... it seems that with SCIM tbird actually prints a 'segmentation fault' message, but it didn't do that in your case... so I'm just not sure what it could be. without any error messages, it would take some serious tinkering and troubleshooting to even start having a clue as to what it could be. it's just not worth the trouble, what with the third-party repository methods being available. it clearly is something specific to your setup, because no other reports of the same problem have materialized over the thousands of people who have used ubuntuzilla...

I see. Yes, you're right that at this point it isn't worth such an investigation, especially since we've already gotten success with the load on this computer. I was just curious, trying to learn something for the future.

> **nanotube said:**
> about using the third-party repositories... i don't think it is necessary to uninstall tb 1.5 before installing 2.0 - but it wouldn't hurt to do that, either. so if you wanna "play it safe" you could uninstall tb1.5. 

I see. And what about with ubuntuzilla. Is it needed to first delete 1.5.0.13...or is there an upgrade feature in it?

One last question: one of the moderators on the TB support forum suggested that I open my 1.5.0.13 TB, go to Help -> check for updates. She suggested I could upgrade to TB 2.0.0.6 by doing this. She is a Windows user though, and herself told me she is not very familiar with Linux. In Linux can one upgrade TB by the route she suggested?

---

### Post by nanotube on 2007-08-28
> **swarup said:**
> I see. Yes, you're right that at this point it isn't worth such an investigation, especially since we've already gotten success with the load on this computer. I was just curious, trying to learn something for the future.



I see. And what about with ubuntuzilla. Is it needed to first delete 1.5.0.13...or is there an upgrade feature in it?


ubuntuzilla basically "ignores" what's installed from the repositories, so there's no need to uninstall what you have before using ubuntuzilla. it will install the official mozilla build side by side with the repos install.
> 
One last question: one of the moderators on the TB support forum suggested that I open my 1.5.0.13 TB, go to Help -> check for updates. She suggested I could upgrade to TB 2.0.0.6 by doing this. She is a Windows user though, and herself told me she is not very familiar with Linux. In Linux can one upgrade TB by the route she suggested?

that won't work with a repositories install - that upgrade feature is intentionally disabled in the ubuntu repos version of thunderbird, because you are supposed to use the update manager to update, not the built-in mozilla updater. so... yea, it won't work, unless you use the official mozilla build (as installed by ubuntuzilla, e.g., or if you install it manually).

hope that clarifies things some more. :)

---

### Post by swarup on 2007-08-28
Yes, it certainly does. Thank you very much. I think you've given me the answer to every question I even dreamed of wanting to know the answer to. :)

---

### Post by nanotube on 2007-08-29
> **swarup said:**
> Yes, it certainly does. Thank you very much. I think you've given me the answer to every question I even dreamed of wanting to know the answer to. :)

glad i could be of help. ;)

---

