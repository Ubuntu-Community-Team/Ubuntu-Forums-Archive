---
title: "Could i be Infected ?"
date: 2012-10-08
forum: Any Other OS
---

### Post by CCgirl6690 on 2012-10-08
Hello everyone ,  not sure if its a right forum for this , but since people in here is so helpful and friendly so imma ask here , thanks someone wanted to make a link for me on 5gbfree.com and he said he couldnt do it on his own computer and that he needed to do it on mine so i let him use teamviewer and he sent me 3 files from his computer and then uploaded them on that website through my computer , 2 of those files were .jpg and .png and the other one was.php  . he asked me to delete those files from my computer after he uploaded them thou i didnt , anyways then my teamviewer crashed  so i rebooted my laptop and after i got back online he said he got all my passwords  im so worried , i want to know if thats possible? or am i keylogged ?i changed most of my passwords btw but still worried , i still have the files he sent me and uploaded them , although he asked me to get rid of them ,if someone would please check that php file for me and figure it out maybe? Btw i'm on backtrack 5  i Need your help please and thanks...........

---

### Post by twipley on 2012-10-08
The only thing I can say: if you are worried about being keylogged, install a clean Ubuntu version from fresh (for example, the 12.10 beta 2), *and only then*, change every one of your current passwords.

---

### Post by oldos2er on 2012-10-08
Moved to Other OS/Distro Talk.

---

### Post by critin on 2012-10-08
If you had any type of financial passwords, bookmarks, go to those sites and change them at once.  Alert the companies of the issue.  Install a new os and go from there.  New passwords again, even another set of bank, pay pal, etc passwords because if you changed it an hour ago, the new one may have been passed on.  If you don't have to store financial passwords--don't.

---

### Post by sidzen on 2012-10-08
It sounds like someone was being a smartass because your were using Backtrack5, took advantage of you, may have installed malware and/or obtained your passwords via at least one of the files you mentioned, and may now have you and your machine being tracked.  This is a worst-case scenario, so don't get too alarmed until speaking with your ISP to explain your concern.  If on-campus at a university or college, contact the IT Admin and blow the whistle <snip>
 
If not a hoax yourself and want more advice, answer and tell us if a concern still exists on your part.

---

### Post by critin on 2012-10-08
umm, I didn't know what Backtrack was, but I guess this will give you a great opportunity to test it.   Maybe this one will work as promised and there was no harm done.

---

### Post by CCgirl6690 on 2012-10-08
thank everyone i have backtrack 5 dual booted with win7 , it happend when i was on backtrack. do i need to get rid of my windows 7 too?????? im going to install ubuntu 12.4.1 and get rid of backtrack , iv been told that its not made for installing but i didnt listen , i guess ubuntu is more safe than backtrack thanks

---

### Post by sidzen on 2012-10-08
Rules say I cannot tell you the way i would do it using the dd command, but find a way to wipe the **partitions** on which Backtrack was installed with *zeros*, then use same partitions (take note of them) to install your chosen distro onto.

---

### Post by varunendra on 2012-10-09
[COLOR=DarkRed]DISCLAIMER : I am NOT a Security Expert, nor a PHP Expert ![/COLOR]

> **sidzen said:**
> find a way to wipe the **partitions** on which Backtrack was installed with *zeros*,
Sorry, but that would be absolutely unnecessary plus extremely time-taking (for no worthy reason). :)

Zero-filling is done only for :

[LIST=1]
[*]Attempting a repair on a dying HDD to make it re-usable for a few more days,
[*]To make sure no one can resurrect the data that existed on the drive, using data-recovery tools and advance techniques - both of which require full and physical access to the drive.
[/LIST]
Assuming that the attacker really did what he claimed (although I don't believe that), all that needs to be done is doing a fresh install of 'Any' OS (be it Ubuntu, Windows, BackTrack itself, or whatever trusted one), **THEN** change all the local and remote passwords from the fresh installation. Nothing more is required. Even if a malicious code is written on the disk (and even if it is on MBR) and has become active in an existing OS, it is absolutely neutralized once the suspected partition is 'Simply' formatted and a fresh OS is installed and allowed to overwrite the MBR.


In worst case scenario, an attacker may also inject some malicious code in the other existing operating systems (windows in this case) and/or partitions using some really smart code, which may become active (and may spread itself again like a virus) once that OS is booted or the infected partition is accessed.[COLOR=DarkRed] In that case, you need to reformat both the operating systems (in fact all the partitions if you suspect they may have been 'infected'), and do a fresh installation of them.[/COLOR]

That said, I don't think one can get access to someone's passwords just by uploading some files via teamviewer. But of-course if the php file was specially designed for that purpose, AND was RUN on the target computer before (pretending to) uploading, then it is quite possible. But that is something any normal php coder can figure out by analyzing that file. If that file is clean, then I don't think someone can break into a strong OS like backtrack using a simple service like teamviewer (assuming the OP has told us EVERY ACTIVITY that apparently happened on her computer in that duration).




But, *CCgirl6690*, if you really want to implement 'paranoid' level security, just transfer all your 'trusted' data to an external drive, wipe out the partitions (simply delete them using gparted), recreate them and do a fresh installation of the OSes of your choice. Of course this is too much, but still much-much quicker than a zero-filling. Then always remember - "NEVER give access to your computer to someone you can't trust !!".

---

### Post by CCgirl6690 on 2012-10-09
Thank you so much , i dont know anythign about zero formating ,so i think i will do what varunendra said , and wipe the partitions , is it possible that when i want to back up my date the virus gets transferred along with them then when i want to copy them back to my new Installed OS the virus gets back too?  thank you

---

### Post by varunendra on 2012-10-09
The 'move-data > reinstall everything' routine was a common  exercise for windows installations. For any Linux distro, only a fresh  installation is enough (assuming the existing one has really been  infected, and we are unable to clean it). This is because even if a file is infected (or a virus itself), linux doesn't execute it automatically (unlike windows) just by accessing it. It can get executed only after seeking explicit permission from you. However, presuming the threat was real, the existing installation may have it included in some auto-start routine, that's why a fresh installation is suggested.

Although there are  really good tools in linux for virus and rootkit detection, (of which  'clamav' is in default ubuntu repo, rkhunter is already included in  Backtrack live DVD), since we are suspicious of a custom script in your  case, which these tools may fail to detect with normal options, a fresh  installation is the best way to go.

Now if the attacker is not a  professional hacker or security expert, the chances of him being able to  infect your whole system is next to zero. Assuming that true, just a  re-installation of the Linux part (after formatting the partition) is enough.  Then change your passwords from the fresh installation. No need to  change any passwords if you have already done that from a DIFFERENT  computer.

But yes, **IFF** the data files are also infected (A BIG funny Question Mark here :)), they may get carried. That's why I said "your trusted data" in my previous post. However, as I stated in the first paragraph above, they can only pose threat in windows environment.

That also brings up an interesting thing to consider - a code, which can infect files, thus allowing unauthorized access to the system, can either be designed to take advantage of linux, or can be designed for windows. Since the attack (??) was made in linux, it means the code should be harmless for windows unless it is some platform-independent script lying around as a file, waiting to be executed manually (like the php script you were handed).


**So the summary is :**
Just delete and quarantine any suspicious files (from your description so far, I can suspect none excet that php script), reinstall the linux part, allow it to overwrite MBR (it will, by default), change passwords as required, and you should be all good.

As for OS recommendation, while Backtrack is a really  strong and one of the most secure OSes, it is not meant for normal  day-to-day work (although you can do so by just installing additional  software). So I'd suggest Ubuntu 12.04 64bit or 32 bit if your system  does not support 64bit. If the system has less than 1GB RAM, install Lubuntu or Xubuntu instead.

And as for me checking your system (as per your pm), I simply can't for two reasons -

[LIST=1]
[*]I'm not an expert as you have mistaken me for,
[*]I'm on a crappy gprs connection which typically takes 20-30 seconds to just open a page, so using any remote service to offer help like that is beyond my dreams at the moment.
[/LIST]
Oh and there's a third reason as well - You've just suffered one threat, don't risk more ! ;)


Good luck !

---

### Post by cobooboc on 2012-10-09
After formatting your data is gone?

---

### Post by CCgirl6690 on 2012-10-09
thank you varunendra , it was very complete and useful , lovely............. so i wont format my windows drive , and i will just install ubuntu  .thanks again  @ cobooboc  , what?

---

### Post by Elfy on 2012-10-09
You are going to be better of using the backtrack forums - closed.

---

