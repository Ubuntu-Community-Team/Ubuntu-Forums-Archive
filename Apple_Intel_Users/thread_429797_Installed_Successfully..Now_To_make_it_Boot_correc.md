---
title: "Installed Successfully..Now To make it Boot correctly"
date: 2007-05-01
forum: Apple Intel Users
---

### Post by Steve1496 on 2007-05-01
Hi guys, I've already installed 7.04 from the Live CD onto my triple boot 20" iMac Core 2 Duo.  When booting the computer with rEFIt, I do get the option to boot into Ubuntu.  However, when I do, all i get is a black screen with a blinking white _ .  I'm not sure where to go from here.  I've also got Windows XP installed and OS X 10.4.9.

Thanks.

---

### Post by ronocdh on 2007-05-01
> **Steve1496 said:**
> Hi guys, I've already installed 7.04 from the Live CD onto my triple boot 20" iMac Core 2 Duo.  When booting the computer with rEFIt, I do get the option to boot into Ubuntu.  However, when I do, all i get is a black screen with a blinking white _ .  I'm not sure where to go from here.  I've also got Windows XP installed and OS X 10.4.9.

Thanks.
How was the installation? Did you have to install any restricted drivers in order to get the GUI to display? And this black screen appears before (that is, instead of) the GRUB screen, correct? If that is the case, it sounds like a GRUB issue. Have you synchronized your partition tables? (This is done by selecting the partitioning tool on the rEFIt boot screen; it will ask for permission to synchronize if it is necessary.)

---

### Post by Steve1496 on 2007-05-01
> **ronocdh said:**
> How was the installation? Did you have to install any restricted drivers in order to get the GUI to display? And this black screen appears before (that is, instead of) the GRUB screen, correct? If that is the case, it sounds like a GRUB issue. Have you synchronized your partition tables? (This is done by selecting the partitioning tool on the rEFIt boot screen; it will ask for permission to synchronize if it is necessary.)


There may be a bigger issue.  There's a lot of text on the partition screen, so I took a shot with my camera that may be more helpful.  It says theres no GPT found, so a sync isnt necessary.

---

### Post by Gen2ly on 2007-05-01
reinstall.  uh wait.  hmm how did you partion the drive may I ask?

---

### Post by ronocdh on 2007-05-02
> **Dirk.R.Gently said:**
> reinstall.  uh wait.  hmm how did you partion the drive may I ask?
Dirk's right, but reinstall with a different disc, for which you've verified the checksum. And grab the alternate iso and burn that, too. I personally always install from the alternate discs.

---

### Post by michaels on 2007-05-02
Oh, my god! Your hidden EFI partition is missing!!! You must have erased it during your partition!

To tell the truth, there's totally no hope to fix it! The only thing you can do is reinstall the whole system from OS X! This time you should pay more attention on it ! This is my [howto]("http://www.cs.helsinki.fi/u/jzshen/install_feisty.html"). I hope it could help you.

Good Luck!

---

### Post by Chrisj303 on 2007-05-02
Did you delete any of the small partitions that QT/GParted shows on the partition table? Something has gone seriously wrong there, and like the other guys have said, just re-install. 

Maks sure you read through as many guides as you can - cross referencing them when needed, and don't do anything your not 150% comfortable with.

Someone correct me if i am wrong - but the message rEFIt is showing seems to imply that there is no GUID partition table. If this is the case will a simple re-install of ubuntu fix that?



cheers,
chrisj303

---

### Post by Steve1496 on 2007-05-02
Yeah, I didn't even notice the missing EFI partition.  As soon as I get enough free time, I'll reinstall the whole system and do a checksum on the linux disc first.

Your guide seems helpful, **michaels**, thanks for the link!  The funny thing is, though, I didn't have any issue installing...it all went perfectly, with no errors.  


Thanks for your help!

---

### Post by ronocdh on 2007-05-02
> **Steve1496 said:**
> Yeah, I didn't even notice the missing EFI partition.  As soon as I get enough free time, I'll reinstall the whole system and do a checksum on the linux disc first.

Your guide seems helpful, **michaels**, thanks for the link!  The funny thing is, though, I didn't have any issue installing...it all went perfectly, with no errors.  


Thanks for your help!
It probably went without a hitch because it had found partitions for everything it needed; problem is, the partitions it was using were **not** ones we want to lose! As michaels said, without the GPT rEFIt spot in place, ugh, it's all gone.

(And Chrisj303 is right, too; reinstalling just Ubuntu won't restore your OS X functionality.)

Please post back and let us know how it goes!

---

### Post by Steve1496 on 2007-05-05
Working on the reinstall.  I got the error: Executing 'grub-install (hd0)' failed.This is a fatal error. "  Here's my partition table:
162GB OS X 
30G Linux
40G Windows

Following the guide, I did not have to start gdm using commands--the live CD loaded perfectly.  Installing, I'm using ext3 with no swap.  GRUB is set to install, as the guide says, at (hd0, 2).  

Any ideas?

---

### Post by ronocdh on 2007-05-05
> **Steve1496 said:**
> Working on the reinstall.  I got the error: Executing 'grub-install (hd0)' failed.This is a fatal error. "  Here's my partition table:
162GB OS X 
30G Linux
40G Windows

Following the guide, I did not have to start gdm using commands--the live CD loaded perfectly.  Installing, I'm using ext3 with no swap.  GRUB is set to install, as the guide says, at (hd0, 2).  

Any ideas?
OK. You're sure you're installing 7.04? This reminds me of the GRUB error Edgy and Dapper used to throw during installation. There was a sweet work around in [this famous guide]("https://help.ubuntu.com/community/MacBook"). Maybe that would work for you?

Also, I thought you were reinstalling OS X, not Ubuntu. I guess that went OK, and now with OS X and Win XP, you're trying to add Ubuntu?

---

### Post by Steve1496 on 2007-05-05
Thanks to everyone's help, I've got Ubuntu working correctly.  

However, when I try to enable Desktop Effects, I get the error: The Composite Extension is not available.  I'm new to Ubuntu...what exactly does this mean?  I'm using the Unsupported ATI drivers..


Thanks to everyone who has helped!

---

### Post by ronocdh on 2007-05-05
> **Steve1496 said:**
> Thanks to everyone's help, I've got Ubuntu working correctly.  

However, when I try to enable Desktop Effects, I get the error: The Composite Extension is not available.  I'm new to Ubuntu...what exactly does this mean?  I'm using the Unsupported ATI drivers..


Thanks to everyone who has helped!
By "unsupported ATI drivers" do you mean fglrx? The issue with Compiz and Beryl on our hardware is that they don't support AIGLX, which is what our sessions are by default. It is possible to arrange to have an XGL session, but your results with it are nothing certain. Please do let us know how it goes, though.

For a slightly outdated look at how to do this, try [this guide.]("http://ubuntuforums.org/showthread.php?t=399643&highlight=x200m") You can look at the official Beryl how-to [here]("http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu").

---

### Post by Steve1496 on 2007-05-05
> **ronocdh said:**
> By "unsupported ATI drivers" do you mean fglrx? The issue with Compiz and Beryl on our hardware is that they don't support AIGLX, which is what our sessions are by default. It is possible to arrange to have an XGL session, but your results with it are nothing certain. Please do let us know how it goes, though.

For a slightly outdated look at how to do this, try [this guide.]("http://ubuntuforums.org/showthread.php?t=399643&highlight=x200m") You can look at the official Beryl how-to [here]("http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu").


Thanks for the links...yes I meant the AIGLX drivers.  I looked through the links and followed information from both.  My results--
*Gnome with XGL works, although it is buggy.
*The startxgl.sh bug where you dont get the shutdown/restart/etc bug from the top right menu affected me.  Adding the extra code as suggested makes XGL not function at all.
*So far, I've only got Wobbly Windows and standard "desktop effects" bundled with ubuntu.

---

### Post by ronocdh on 2007-05-05
> **Steve1496 said:**
> Thanks for the links...yes I meant the AIGLX drivers.  I looked through the links and followed information from both.  My results--
*Gnome with XGL works, although it is buggy.
*The startxgl.sh bug where you dont get the shutdown/restart/etc bug from the top right menu affected me.  Adding the extra code as suggested makes XGL not function at all.
*So far, I've only got Wobbly Windows and standard "desktop effects" bundled with ubuntu.
The wobbly windows is decent progress; that usually works OK once you create an XGL session. As for Beryl and flippycube effects, that's a real chore on the ATI cards. Best of luck to you if you pursue that route.

---

