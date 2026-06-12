---
title: "Need advice from adimistrator Ubuntu could be ruining peoples hardware."
date: 2006-06-09
forum: Apple PPC Users
---

### Post by n00bWillingToLearn on 2006-06-09
I don't know if it is just an isolated problem but my fans on my g4 powerbook are not being turned on in Ubuntu and as a result the proccessor has overheated on many occasions to the point that the temp sensors shut down the computer abruptly. I had not realized that the reason for these shutdowns was the CPU soverheating untill today.

I would like advice on the best way to make sure no one elses harware is permenently damaged due to this bug. Please respond with any advice.

---

### Post by colinhayes on 2006-06-09
[QUOTE=n00bWillingToLearn]I don't know if it is just an isolated problem but my fans on my g4 powerbook are not being turned on in Ubuntu and as a result the proccessor has overheated on many occasions to the point that the temp sensors shut down the computer abruptly. I had not realized that the reason for these shutdowns was the CPU soverheating untill today.

I would like advice on the best way to make sure no one elses harware is permenently damaged due to this bug. Please respond with any advice.[/QUOTE]

yes, you can do what I do and continually try to compile a new kernel and just have the computer shutdown every single time you try.  it's really a lot of fun.


but uh, the fans on my G5 work, but my comp does shutdown

---

### Post by goofyheadedpunk on 2006-06-10
[QUOTE=n00bWillingToLearn]I would like advice on the best way to make sure no one elses harware is permenently damaged due to this bug. Please respond with any advice.[/QUOTE]

The module that controls the fan in an ibook is "therm_adt746x". Could you issue lsmod and tell me if the fan control module shows up?

---

### Post by jwk on 2006-06-10
[QUOTE=colinhayes]the fans on my G5 work, but my comp does shutdown[/QUOTE]

Didn't they (the Linux kernel developers) change a module or something in the kernel so that the G5s didn't shut down as much? I thought I saw it in a change log 8) , but I can't find it. :-k If i rememebr correctly, they changed it so that the kernel waits a couple seconds before finally shuting down, it's seems the cpu would over heat, but the fans werent given enough time to spin up. So it could be that Ubuntu includes the kernel before they changed it.

---

### Post by colinhayes on 2006-06-10
[QUOTE=jwk]Didn't they (the Linux kernel developers) change a module or something in the kernel so that the G5s didn't shut down as much? I thought I saw it in a change log 8) , but I can't find it. :-k If i rememebr correctly, they changed it so that the kernel waits a couple seconds before finally shuting down, it's seems the cpu would over heat, but the fans werent given enough time to spin up. So it could be that Ubuntu includes the kernel before they changed it.[/QUOTE]

this would be wonderful, but the damn bug is preventing me from compiling a 2.6.16.19 kernel.  I think this might get to me sending someone my .config and have them make a kernel package for me.

---

### Post by n00bWillingToLearn on 2006-06-10
[quote=colinhayes]this would be wonderful, but the damn bug is preventing me from compiling a 2.6.16.19 kernel.  I think this might get to me sending someone my .config and have them make a kernel package for me.[/quote]

I have been keeping my powerbook from overheating by setting it on an ice pack. I have three ice packs so when one has warmed up I put it back in the freezer and grab another. I realize that a g5 is a beast to cool so there may not be such an easy way of cooling it, but you only need to cool it until the new kernel is compiled.  It may be a little crude but it could work if you have portable air conditioner? Most of all, though, this needs to be fixed and if it really does just require a recompile than the devs should focus on this and I believe more should be done to alert them to this problem than just a buggzilla report. If nothing else, when someone does find a solution the instructions should be stickied as I doubt that it is good to let your proccessor get hot enough that the temp sensors get triggered and it gets stopped forcefully. That is why I started this thread, to get advice on how others should be at least warned about this problem. I don't know if this is good forum edicate, as these are the first forums I have ever used, but I posted another thread to actually find how to fix this bug here [http://ubuntuforums.org/showthread.php?p=1122899#post1122899](http://ubuntuforums.org/showthread.php?p=1122899#post1122899) and then posted this to try to alert an admin about this critical problem. Sorry for the double post.

---

### Post by colinhayes on 2006-06-10
[QUOTE=n00bWillingToLearn]I have been keeping my powerbook from overheating by setting it on an ice pack. I have three ice packs so when one has warmed up I put it back in the freezer and grab another. I realize that a g5 is a beast to cool so there may not be such an easy way of cooling it, but you only need to cool it until the new kernel is compiled.  It may be a little crude but it could work if you have portable air conditioner? Most of all, though, this needs to be fixed and if it really does just require a recompile than the devs should focus on this and I believe more should be done to alert them to this problem than just a buggzilla report. If nothing else, when someone does find a solution the instructions should be stickied as I doubt that it is good to let your proccessor get hot enough that the temp sensors get triggered and it gets stopped forcefully. That is why I started this thread, to get advice on how others should be at least warned about this problem. I don't know if this is good forum edicate, as these are the first forums I have ever used, but I posted another thread to actually find how to fix this bug here [http://ubuntuforums.org/showthread.php?p=1122899#post1122899](http://ubuntuforums.org/showthread.php?p=1122899#post1122899) and then posted this to try to alert an admin about this critical problem. Sorry for the double post.[/QUOTE]

no, I don't have a portable AC.

I guess I could try turning to comp off for a few hours and then going straight to compiling the kernel.

---

### Post by onehotcutey on 2006-06-10
I have a Powerbook G4 1 ghz with 1 gig of ram and am running the latest version of Dapper.

I haven't experienced any of these problems and I've been doing some processor heavy work lately.

I knew the G5 was having issues, but I'm not having any of these issues with mine.

---

