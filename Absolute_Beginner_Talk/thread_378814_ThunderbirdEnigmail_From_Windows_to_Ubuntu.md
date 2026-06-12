---
title: "Thunderbird/Enigmail From Windows to Ubuntu"
date: 2007-03-07
forum: Absolute Beginner Talk
---

### Post by RKCole on 2007-03-07
Hello, everyone.

This may be a dumb question, but I admit my ignorance on this topic.

I have just begun to use Thunderbird with the Enigmail/OpenPGP program in Windows.  I would like to transfer my profile and OpenPGP-related information to Ubuntu.  I know that the profile transfer si probably as easy as copying the related files from Windows to the Thunderbird-related directory in Ubuntu, but I am not so sure about how I would go about transferring my key pairs and other needed OpenPGP-related data.  Does anyone know how to do this?

I"m not worried about sharing mail with Windows as I soon intend to solely use Linux.

Thanks for any input or suggestions.

Take care.

---

### Post by gaten on 2007-03-07
It all about your profiles. I personally just changed the profile path in my ~/.mozilla-thunderbird/profiles.ini to something like this:

```
[General]
StartWithLastProfile=0

[Profile0]
Name=default
IsRelative=0
Path=/media/hdd1/Profiles/1nels8vh.default/
```


The important part above is the "IsRelative=0" value, it has to be 0 or the path u put in will mess things up. As you can see, my profile in windows (located on /media/hdd1/) is located in the "1nels8vh.default" directory. It should be noted that hdd1 is a fat32 drive, NOT ntfs (so no problems with writing). If you want to, you could just copy your entire Profile folder over to linux and point your profile to there. The only thing is you will need to change your Engimail config to point to /usr/bin/gpg (as it's still point to the windows .exe at this point.) 

Hope this helps, let me know if you have any problems.

---

### Post by RKCole on 2007-03-12
Sorry for the long-delayed reply...I have not had the chance to look into things much until now.

What I want to do is to simply import my Thunderbird profile (not really wanting to share directories with Windows as XP is on a NTFS partition).  I know it's somewhat lazy, but I just want to copy over my profile and address book so I do not have to completely re-do everything.  I also set up Enigmail and my OpenPGP information in Windows (my key pair, passphrase, and keys of others).  As far as that is concerned, I want to find out how to copy over everything, including the OpenPGP information so that I do not need to set up a whole new key and passphrase.  Is this possible?

Thanks for the help and the quick response, gaten.

Take care.

---

### Post by gaten on 2007-03-12
I don't see why not. Just copy your thunderbird profiles folder over from windows (something like "My Documents\Application Data\Mozilla" etc) to your thunderbird folder in linux (usually ~/.mozilla-thunderbird/). 

The folder with the funky name is your profile folder. You will need to change profiles.ini to point to that folder. As for your key, you can Import keys under OpenPGP w/ the "Key Management" option. You'll have to find your key on the windows install first (don't remember if it's stored in your profiles directory or not), then copy it over and import it.

---

### Post by Crakie on 2007-03-12
Note that Gaten's solution has an additional advantage: mail you retrieve in Windows also shows up in your Linux-copy of Thunderbird and vice versa. As he stressed, it's important to put your mail on a FAT partition or drive, so both Linux and Windows can write on it. 

I use the same construction. When I was still using XP frequently, it was a relief. I didn't have to reboot anymore when looking for that particular message I seemed to have retrieved when I was using 'the other' operating system. And as Murphy states, that is usually the case ;)

---

### Post by RKCole on 2007-03-13
I'll give that a shot as I do have a FAT32 partition I made when I installed Ubuntu on my secondary HDD.  So I would just have to redirect Thunderbird to that directory in both Ubuntu and Windows, right?  I am going to wait for Feisty to come out (at least in beta form) and then do the switch.

Thanks for the input on this matter.

I'll post back after it's all done and post the method of how I did it all in case anyone else comes up with this same situation.

Thanks again and take care.

---

### Post by RKCole on 2007-04-05
Sorry for bringing back an old thread, however I think I have solved this issue.

I kind of solved this by accident as I was placing a version of Thunderbird Portable (with Enigmail/GPG) onto my flash drive as I'm leaving for awhile come this afternoon, and I wanted to take Thunderbird and all my settings with me. (Isn't open source great? :) )  I'm pretty sure that the files that Thunderbird uses for profiles and mail are the same platform-to-platform, so what I did (and what should work in a transition to Ubuntu) was:

1)  Copied my profile information from C:\Documents and Settings\<username>\Application Data\Thunderbird\Profiles\xfizkc4c.default to the new profiles directory.
2)  Opened the new Thunderbird installation and checked my e-mail (and sent an encrypted message). :)

So, apparently, all that would need to be done (for a Ubuntu-only system without dual booting) is to:

[LIST=1]
[*]Install Thunderbird
[*]Get and install the Enigmail plugin (I do not think that you have to install OpenPGP/GPG as I believe it comes with Ubuntu...Am I right?)
[*]Copy the profile information (not the folder, but just its contents) from <Windows Drive>:\Documents and Settings\<username>\Application Data\Thunderbird\Profiles\xfizkc4c.default (I think the folder name may vary) into the new Thunderbird installation's Profiles directory (probably in ~/.thunderbird/).
[*]Use Thunderbird!
[/LIST]

Enigmail/GPG seemed to work perfectly right out of the box.

Anyway...I figured I'd just come back and mark this as solved and explain what I did in case anyone else can benefit from this information.

Take care, everyone.

---

