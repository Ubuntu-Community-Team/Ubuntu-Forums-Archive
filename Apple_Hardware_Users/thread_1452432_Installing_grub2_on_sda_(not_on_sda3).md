---
title: "Installing grub2 on sda (not on sda3)"
date: 2010-04-11
forum: Apple Hardware Users
---

### Post by Nikos.Alexandris on 2010-04-11
Thought this might be interesting:

I recently decided that it was time to resize my linux partitions and (try to) (re-)install (K)ubuntu [*read more in the Kubuntu forum ******]. Specifically, I've tested Kubuntu Lucid Lynx (Beta1 and) Beta2 which did eventually run but with numerous bugs making the system practically unusable.


Anyhow, I want to share that:

- twice when I selected the root partition (in my case **sda3**) to install GRUB (the boot loader) my system failed to boot. rEFIt would recognise that there was some Linux somewhere but GRUB would never show up.

- twice it worked (one using Lucid Lynx Beta2 and another one Kamic 9.10, both Kubuntu 64bit live CD's) when I let **sda** to be the target in which GRUB would be installed.

I am not sure what I did back in November 2008 when I first performed the installation and since then had no boot problems. And even more unsure I am now if **sda3** is the correct choice (as the wiki instructs **[/]**) since it failed for me.

Regards, Nikos

---

**[*]** [http://kubuntuforums.net/forums/index.php?topic=3110960.msg224899#msg224899]("http://kubuntuforums.net/forums/index.php?topic=3110960.msg224899#msg224899")

**[/]** [https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation#Dual-Boot:%20Mac%20OSX%20and%20Ubuntu]("https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation#Dual-Boot:%20Mac%20OSX%20and%20Ubuntu")

---

### Post by buntuLo on 2010-04-12
here both installations of intrepid and karmic went fine choosing the root partition as a target for grub and grub2, respectively. i guess you did syncronise MBR and GPT partition tables with rEFIt after that..

---

### Post by Nikos.Alexandris on 2010-04-12
> **buntuLo said:**
> here both installations of intrepid and karmic went fine choosing the root partition as a target for grub and grub2, respectively. i guess you did syncronise MBR and GPT partition tables with rEFIt after that..

Right, I did. rEFIt was _always_ replying that the tables were synced. No idea... (shrug)?

---

### Post by _mario_ on 2010-04-13
> **Nikos.Alexandris said:**
> 
Anyhow, I want to share that:
- twice when I selected the root partition (in my case **sda3**) to install GRUB (the boot loader) my system failed to boot. rEFIt would recognise that there was some Linux somewhere but GRUB would never show up.

ack. updated karmic to lucid yesterday. lucid failed to boot afterwards due to grub (grub-pc) inside the boot partition (/dev/sda3) not working anymore. and i definitely didn't run rEFIt's partitioning tool. could fix it by reinstalling grub using the live cd.

btw: afaik, i was never able to install grub from my running system (each grub upgrade caused the same problem). i always had to use the live cd.

ciao,
Mario

---

### Post by Nikos.Alexandris on 2010-04-13
> **_mario_ said:**
> ack. updated karmic to lucid yesterday. lucid failed to boot afterwards due to grub (grub-pc) inside the boot partition (/dev/sda3) not working anymore. and i definitely didn't run rEFIt's partitioning tool. could fix it by reinstalling grub using the live cd.

btw: afaik, i was never able to install grub from my running system (each grub upgrade caused the same problem). i always had to use the live cd.

ciao,
Mario

Among my numerous attempts the last days, I've (too) installed grub from the live-cd (the usual live-cd way as well as using chroot) and failed to fix it. I guess I should have posted in the forum and maybe I would not loose too much time...

Anyhow, I have now a *superbe* stable and fast Kubuntu Karmic, re-organised and ready to fly... (read upgrade) to Lucid :-)

---

