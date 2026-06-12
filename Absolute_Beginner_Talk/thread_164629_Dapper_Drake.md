---
title: "Dapper Drake"
date: 2006-04-23
forum: Absolute Beginner Talk
---

### Post by Metta on 2006-04-23
Hi

I received an email this morning, explaining about Dapper Drake,

[http://www.ubuntu.com/testing/dapperbet]("http://www.ubuntu.com/testing/dapperbet")

I followed the upgrading instructions and edited the terminal with: gksudo "update-manager -d"

All went well and the download manger kicked in, then told me that the install had completed, I then rebooted, but 5.10 was what I got, and not the newer version, any ideas.

Gnome version as follows:

2.12.1

build date 03 10 05

Plus:

I would like to migrate my firefox and thunderbird profiles from my laptop, which duel boots both Ubuntu (Version unclear as yet, see above message) and XP (FAT32). I know how to get the profiles via windows, but I am completely lost when it comes to transferring and installing them on to ubuntu?

Just for interest can I use Thunderbird for email on both XP and Ubuntu, and keep the email folders on the XP partition and just edit the preferences file on the Ubuntu partition to read/write to the same file? If yes, how? In plain simple language please, because this terminal work is all new to me! 

Thanks :)

---

### Post by htinn on 2006-04-23
I don't know what went wrong with update-manager, but you probably need to update update-manager itself first before you can perform that Dapper upgrade.

As for sharing profiles between different systems, it may be possible but I doubt you are interested in the technical problems with it. There are probably web-based alternatives to what you are looking for.

---

### Post by Metta on 2006-04-23
How do you update the update manager?

Thanks

---

### Post by htinn on 2006-04-23
If you go to the Synaptic Package Manager (which is either in the System/Admin menu or the Applications/System Tools menu), you can upgrade it from there.

Just make sure you click "Reload" first.

---

### Post by wylfing on 2006-04-23
I would counsel you against installing bleeding-edge software unless you think yourself a moderately advanced user. By its very nature such software is going to expose you to technical problems that do not have easy solutions. It's probably much wiser to wait until the official release is out.

If, however, you are still bound and determined to use Dapper beta, you may not be well served by using update-manager. That fact may change as Dapper gets on to release. For now, I'd suggest doing things the old-fashioned way. 

1. Edit your sources.list and change all instances of "breezy" to "dapper":
```
sudo gedit /etc/apt/sources.list
```

2. Update your package lists:
```
sudo apt-get update
```

3. Do a massive upgrade:
```
sudo apt-get dist-upgrade
```

Regarding the sharing of Firefox and Thunderbird profiles between operating systems, **htinn** is right that this involves a lot of headaches. The problem mostly has to do with the static nature of profiles -- they don't easily "roam" and are frustratingly resistant to being shared or moved or tampered with or looked at cross-eyed.

---

### Post by Metta on 2006-04-23
Thanks for the info, I think I'll will wait for the offical release, just in case!

Thanks

---

### Post by Metta on 2006-04-23
Does the profile migrating work earier with firefox? 

Thanks

---

### Post by wylfing on 2006-04-23
No, neither Firefox nor Thunderbird like it when you share profiles. The best you can get is to use the bookmark-synchronizing extension for Firefox. That should allow you to (relatively) easily maintain the same bookmark list between operating systems.

---

### Post by pez on 2006-04-23
[QUOTE=Metta]Thanks for the info, I think I'll will wait for the offical release, just in case!

Thanks[/QUOTE]

That's what I have done aswell. I tried it and recieved constant problems. I'm not yet a strong Linux user. The documentation for 5.10 is comprehensive to the point that it has covered all hardware issues that I had when installing Ubuntu 5.10.

---

### Post by Metta on 2006-04-24
Ho about if I transfer my forefox profiles via usb stick from Xp on my PC to Ubuntu on the laptop? Would that be easier?

---

### Post by Caligula on 2006-04-24
I tried dapper for a few days, it was great at the begining, but then the problems started...

Menues started going weird, weird crashes, all that kind of stuff...
Now I'm back with the safe breezy... anyway, it's not long to wait...

---

### Post by steve.horsley on 2006-04-24
I shared a Thunderbird profile between Windows and Linux for a year or more. The problem was in getting the profile manager of the second install to use the profile that the first one made. I remember starting thunderbird by hand with an option like -profile or something like that. Of course, you can't share a profile on an NTFS partition because you can't write to it from Linux.

---

