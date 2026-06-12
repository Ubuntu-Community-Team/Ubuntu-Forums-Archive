---
title: "Enigmail .95.5 not asking for password in Thunderbird"
date: 2007-11-21
forum: Absolute Beginner Talk
---

### Post by optimusmedia on 2007-11-21
Using: 
Thunderbird 2.0.0.6
Enigmail 0.95.5
Ubuntu 7.10

When trying to open an encrypted message, I get the following error (email removed) without being asked for my passphrase: 

```
Error - decryption failed

gpg command line and output:
/usr/bin/gpg --charset utf8  --batch --no-tty --status-fd 2 -d --use-agent 
gpg: problem with the agent - disabling agent use
gpg: can't query passphrase in batch mode
gpg: Invalid passphrase; please try again ...
gpg: can't query passphrase in batch mode
gpg: Invalid passphrase; please try again ...
gpg: can't query passphrase in batch mode
gpg: encrypted with 2048-bit ELG-E key, ID 90CD6040, created 2007-08-30
      "Name removed <email@removed.for.security>"
gpg: public key decryption failed: bad passphrase
gpg: decryption failed: secret key not available
```

Thanks!

PS: I have reviewed [this post]("http://ubuntuforums.org/showthread.php?t=325813"), and found none of the suggestions there to work.

---

### Post by optimusmedia on 2007-11-22
Should this be moved to security?  I don't want to double post, but do need to get this solved.

---

### Post by tribaal on 2007-11-22
How did you install enigmail?

The only way for me to get it to work properly was to install the repos version: "sudo apt-get install enigmail".

Hope the repos version will work for you as it does for me...

- trib'

---

### Post by optimusmedia on 2007-11-22
I've tried both ways.. or three.

1. I started with the repos.
2. Imported from a TB profile (shared with vista (yuk))
3. uninstalled repos - installed mozdev add-on.
4. currently back to repos version.

I think i'll try with a fresh profile and see if i can import my key to that.. because when all else fails - blame microsoft ;)

In the meantime if anyone else has suggestions I'm open to all that don't start with "RM..." ;)

---

### Post by optimusmedia on 2007-11-22
Update: 
I tried to create a new profile but it keep locking up on me (had to reboot -- not sure why).
Thankfully rebooting is not a 10 min wait, like w/ Vista.

Long story short: I created a new profile (and it works).  I log back into the old profile and it's still broken (even when checking the same message).  So it must be something vista changed when sharing my profile.

So.. now I just have to find the enigmail setting in the new profile and copy them to the old profile.  

If anyone knows the specifics of that - you can save me a lot of guess work.  And you'd give me one more thing to be thankful for today. ;)

Happy thanksgiving!

---

### Post by optimusmedia on 2007-11-27
Quick update (and bump).  I can not find the settings I need to move from the working profile to the profile I need it to work in.

---

### Post by optimusmedia on 2007-11-28
Problem solved thanks to [contacting the Enigmail developer]("http://mozilla-enigmail.org/forum/viewtopic.php?p=1312#1312") 

> If Enigmail works in one profile, but on in another one, then I'm pretty sure that this will help: make sure that the option "use gpg-agent for passphrases" is DISabled in OpenPGP > Advaned.

It did.  Thanks Patrick!  Great program.

---

### Post by prazgod on 2008-03-15
I had this problem today - and my option ("use gpg-agent for passphrases" is DISabled in OpenPGP > Advaned.) was already TICKED 

But Unticking it forced a popup asking for my passphrase, strange - its now using the agent I guess???

---

### Post by mattack on 2008-05-07
this fixed it for me on  clean install of 8.04
[https://bugs.launchpad.net/ubuntu/+source/seahorse/+bug/183514/comments/5]("https://bugs.launchpad.net/ubuntu/+source/seahorse/+bug/183514/comments/5")
Basically delete the file /etc/X11/Xsession.d/90gpg-agent and restart X (CTRL+ALT+Backspace).

---

