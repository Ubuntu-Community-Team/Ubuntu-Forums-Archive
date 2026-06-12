---
title: "Error logging in to Gutsy AMD64"
date: 2008-04-14
forum: Absolute Beginner Talk
---

### Post by PoopyTheJ on 2008-04-14
When I log into Gutsy, I get this error, 
User's $HOME/.dmrc file is being ignored. This prevents the default session and language from being saved. File should be owned by user and have 644 permissions. User's $HOME directory must be owned by user and not writable by other users.

I got this error after using Nautilus as sudo and making me, not root owner and allowing everything to my home directory. I was trying to install steam, and it seemed like a good idea at the time, based on info from a friend. Long story short steam still failed to install and now I get this error. Also UT2004 now fails to start, although that could be due to the patch 3369. Anyway how do I fix this error?

---

### Post by estaticd on 2008-04-14
sudo chmod 644 .dmrc
sudo chown user_name .dmrc
sudo chmod 755 /home/your_user_name
sudo chown -R user_name /home/your_user_name

---

### Post by PoopyTheJ on 2008-04-14
Thanks, I don't get that error anymore but now I have no internet connection. As soon as I went through all the commands I lost my internet connection. I logged out and back in but still nothing, I'll try fully rebooting, but anything I might have done to cause this, or anything I should try to fix it? And can you explain what all those commands did?

---

### Post by PoopyTheJ on 2008-04-14
Never you mind, a reboot fixed the issue, thanks for the help, although I would like to know what those commands mean, I am a bench tech at a local computer shop and know my way around windows very well, I'd like to get to the same level with Linux. Any help, good starting points etc?

---

### Post by Moop on 2008-04-14
> **PoopyTheJ said:**
> Never you mind, a reboot fixed the issue, thanks for the help, although I would like to know what those commands mean, I am a bench tech at a local computer shop and know my way around windows very well, I'd like to get to the same level with Linux. Any help, good starting points etc?

Linux file permissions. [http://www.zzee.com/solutions/linux-permissions.shtml](http://www.zzee.com/solutions/linux-permissions.shtml)

---

