---
title: "Thunderbird error's"
date: 2007-07-15
forum: Absolute Beginner Talk
---

### Post by Mr. Win on 2007-07-15
I have been trying to bring my Thunderbird over to feisty... However, I fubar'd something when I was editing the profile and now I can't get Thunderbird to work at all. 

I continue to receive an error stating that a Thunderbird process is running... I have looked through the processes and I don't see one. I have rebooted my machine and I have also uninstalled Thunderbird and reinstalled... I continue to have the same problem. 

I need my emails by Monday... or Monday is going to suck for me.

---

### Post by Pragmatist on 2007-07-15
Did you do a "complete" uninstall?  If you use Synaptic, that is one of the options; I'm not sure the command to use for apt.  The advantage of a "complete uninstall" is that it removes configuration files.

---

### Post by Moop on 2007-07-15
Uninstalling Thunderbird doesn't get rid of your profile and that's most likely what is messing things up. 

Your profile is stored in the home directory in a hidden folder named thunderbird. You can view it by enabling viewing of hidden files. 

You can use the profile manager to create a new profile and or delete the old profile.  Make sure Thunderbird is not running and in a terminal type ```
thunderbird -profilemanager
```

---

### Post by Mr. Win on 2007-07-15
> **Moop said:**
> Uninstalling Thunderbird doesn't get rid of your profile and that's most likely what is messing things up. 

Your profile is stored in the home directory in a hidden folder named thunderbird. You can view it by enabling viewing of hidden files. 

You can use the profile manager to create a new profile and or delete the old profile.  Make sure Thunderbird is not running and in a terminal type ```
thunderbird -profilemanager
```

This was the issue... however, I'm looking at this: [http://users.telenet.be/mydotcom/howto/linux/migration01.htm](http://users.telenet.be/mydotcom/howto/linux/migration01.htm)

It says i can just copy over my old profile information (which I backed up) and it should import everything including my mail. Am I overlooking something? 

:confused: <My face

---

### Post by michaelzap on 2007-07-15
I copied just my mail folders/files frmo XP over to Ubuntu, and as soon as I opened Thunderbird all my email was there as if nothing had changed. First I installed TB on Ubuntu and created a new profile (since it uses a random folder name for each profile), then I quit TB and copied my mail into that folder. If the mailboxes are in the right profile folder, they should show up, so doublecheck their location.

You might also just make sure that you haven't copied over some XP configuration file (that might include paths that aren't relevant on Ubuntu), and you could also delete the mailbox index files and just copy over the actual mail files (I compacted my mail folders on XP first and then recreated the index files on Ubuntu, but I don't think this is really necessary).

---

### Post by Moop on 2007-07-15
You can copy over all your settings etc by opening the old randomly named profile folder on XP and copying everything in it to your new randomly named profile folder in ubuntu. You don't want to copy the folder itself or the thunderbird folder in general.  It's best to have the same versions of thunderbird in both places.

---

### Post by Mr. Win on 2007-07-15
> **michaelzap said:**
> I copied just my mail folders/files frmo XP over to Ubuntu, and as soon as I opened Thunderbird all my email was there as if nothing had changed. First I installed TB on Ubuntu and created a new profile (since it uses a random folder name for each profile), then I quit TB and copied my mail into that folder. If the mailboxes are in the right profile folder, they should show up, so doublecheck their location.

You might also just make sure that you haven't copied over some XP configuration file (that might include paths that aren't relevant on Ubuntu), and you could also delete the mailbox index files and just copy over the actual mail files (I compacted my mail folders on XP first and then recreated the index files on Ubuntu, but I don't think this is really necessary).

> **Moop said:**
> You can copy over all your settings etc by opening the old randomly named profile folder on XP and copying everything in it to your new randomly named profile folder in ubuntu. You don't want to copy the folder itself or the thunderbird folder in general.  It's best to have the same versions of thunderbird in both places.

Thanks guys! The key here was copying the whole "mail" folder. So simple but I had to step away for a while to realize it. 

Thanks again.

---

