---
title: "how do i add windows after i have installed linux"
date: 2006-08-21
forum: Absolute Beginner Talk
---

### Post by chester on 2006-08-21
I finally bit the bullet, after having trouble installing with every other option given me on the live cd, and reformatted the whole drive and installed ubuntu. What are my dual boot options now?

---

### Post by exjinn on 2006-08-21
You will need to create a partition for windows

however...

Windows needs to be the first partition on the hard drive in order for it to boot properly. 

This could have been set up under Ubuntu's initial installation, but now that you are up and running you may have a problem.

---

### Post by gn2 on 2006-08-21
Beware, adding Windows after installing Ubuntu will corrupt the MBR and Ubuntu won't boot.

Have you looked at VM Ware?

I have had endless problems dual-booting, now I have one PC running XP home (for the wife who steadfastly refuses to change) and one PC running Ubuntu.

Keeps things separate and much easier to manage.

---

### Post by r4ik on 2006-08-21
Found this link,

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

It is for 5.10 so i do not know if it will work on Dapper.
Enybody give it green ?
Thanks.

---

### Post by Major_Stitch on 2006-08-21
It isn't a real problem!

Just install Windows normally. At first you won't be able to boot into Ubuntuk, but just print (or have it handy) [Recovering Ubuntu]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows"), and your Ubuntu Live CD (or Desktop if it's 6.06).
Hope it helps (it's how I do it when I need it)

---

### Post by r4ik on 2006-08-21
Since that is the same link i suppose it should work.

---

### Post by Major_Stitch on 2006-08-21
> **r4ik said:**
> Since that is the same link i suppose it should work.

Ooops! Sorry, didn't see your link. Yeah it has a green light! Just follow the instructions and don't be frightened you might lose something, because you won't!

---

### Post by greybirds on 2006-08-21
I'm backing Major_Stitch on this one; I've always done it that way as well. 

However, vmware has quite a few advantages over dual booting (running both operating systems at once, pasting information from windows to linux apps and back, things like that). You might want to look at this:

[http://ubuntuforums.org/showthread.php?t=183209&highlight=vmware]("http://ubuntuforums.org/showthread.php?t=183209&highlight=vmware")

---

### Post by r4ik on 2006-08-21
Nevermind Major_Stich just as long Chester is helped out :)

---

### Post by Major_Stitch on 2006-08-21
> **greybirds said:**
> 
However, vmware has quite a few advantages over dual booting (running both operating systems at once, pasting information from windows to linux apps and back, things like that).


I have no experience with Virtualisations but I think it's better to have an OS rather than its virtualisation, correct me if I'm wrong!

---

