---
title: "Has anyone installed ubuntu on a mac?"
date: 2009-04-17
forum: Apple Hardware Users
---

### Post by Sashin on 2009-04-17
On a new iMac, I've tried to resize the default OSX partition and install Ubuntu 9.04 (32 bit, ext4) after it. However, when I start the computer it boots OSX and I'm unsure of how to access Ubuntu.

Has anyone done this before?

---

### Post by bapoumba on 2009-04-17
Moved to Apple Users. You'll probably get answers here :)

---

### Post by lisati on 2009-04-17
> **Sashin said:**
> On a new iMac, I've tried to resize the default OSX partition and install Ubuntu 9.04 (32 bit, ext4) after it. However, when I start the computer it boots OSX and I'm unsure of how to access Ubuntu.

Has anyone done this before?
Not me, but it has been done. There's even a section of the forums dedicated to such users. See here: [http://ubuntuforums.org/forumdisplay.php?f=328](http://ubuntuforums.org/forumdisplay.php?f=328)

---

### Post by perpetualcacophany on 2009-04-17
> **Sashin said:**
> On a new iMac, I've tried to resize the default OSX partition and install Ubuntu 9.04 (32 bit, ext4) after it. However, when I start the computer it boots OSX and I'm unsure of how to access Ubuntu.

Has anyone done this before?

You'll need to install rEFIt on your OS X partition. There are tutorials all over the place for it.

---

### Post by Sashin on 2009-04-17
okay, I've deleted Mac OSX and I only want to boot from ubuntu. But when I turn it on I only get a white screen.

I can boot from the Ubuntu partition only by using the CD and choosing "Boot from first hard disk".

Does anyone know what could be causing this problem?

---

### Post by Peasantoid on 2009-04-17
Do not delete OS X, you *will* need it later. If you're really sure, you can remove it, but this is most likely a bad idea.

And yes, I am running Ubuntu on my Mac (MacBook3,1). Fairly simple process, although much tweaking is required.

---

### Post by tactus on 2009-04-17
Good place to start.

[https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation](https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation)

A few Apple specific tweaks might or might not be needed, so being a little conservative saves some headache. Ubuntu 9.04 is still release candidate. :P

---

### Post by Sashin on 2009-04-17
Wait, so you're saying it's impossible to have it as an only ubuntu machine.

The iMac I'm using is new and has the intel architecture not powerPC so I assumed it would be normal...

Is there anyway, I can get rid of mac completely and just use it as a normal ubuntu machine without OSX?

---

### Post by lisati on 2009-04-17
> **Sashin said:**
> Is there anyway, I can get rid of mac completely and just use it as a normal ubuntu machine without OSX?
Before you do, you'll need to check if it will affect your warranty.

---

### Post by Sashin on 2009-04-17
Okay I've got it working but I have to press the opeion button when I boot.

Does anyone know if it's possible to replace EFI with BIOS because I can't get it to load ubuntu normally.

(I don't care about the warranty.)

---

### Post by tactus on 2009-04-17
Sashin: I assume you didn´t check the link I provided? Cheers, anyhow. :)

---

### Post by cyberdork33 on 2009-04-17
> **tactus said:**
> Good place to start.

[https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation](https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation)

A few Apple specific tweaks might or might not be needed, so being a little conservative saves some headache. Ubuntu 9.04 is still release candidate. :P+1

> **lisati said:**
> Before you do, you'll need to check if it will affect your warranty.
It won't affect your warranty...

> **tactus said:**
> Sashin: I assume you didn´t check the link I provided? Cheers, anyhow. :)
Yes, you really should read the Installation wiki...

You need to sync the partition tables and probably bless the ubuntu partition still. Good Luck!

---

### Post by Peasantoid on 2009-04-17
The Ubuntu partition doesn't need blessing as far as I know, just a GPT/MBR sync. Then it'll boot properly.

If it seems to hang at the Tux logo, do a force-shutdown (hold the power button down) and try again.

---

### Post by Sashin on 2009-04-17
I saw the guide, but for that I'll have to reinstall. Is there a way to have it work with EFI without that.

At the moment I have to hold alt when I turn it on which is not that bad.

Is there a way I can configure it just to boot Ubuntu normally without reinstalling it?

---

### Post by Peasantoid on 2009-04-18
You can set the system to automatically boot from the Ubuntu partition.

[http://ubuntuforums.org/showpost.php?p=5166788](http://ubuntuforums.org/showpost.php?p=5166788)

---

### Post by cyberdork33 on 2009-04-19
> **Sashin said:**
> I saw the guide, but for that I'll have to reinstall. Is there a way to have it work with EFI without that.

At the moment I have to hold alt when I turn it on which is not that bad.

Is there a way I can configure it just to boot Ubuntu normally without reinstalling it?
bless...

---

