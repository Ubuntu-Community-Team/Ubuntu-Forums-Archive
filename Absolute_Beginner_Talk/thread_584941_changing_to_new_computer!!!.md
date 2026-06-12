---
title: "changing to new computer!!!"
date: 2007-10-21
forum: Absolute Beginner Talk
---

### Post by rafkin on 2007-10-21
Got another computer today!! If I install a fresh Gutsy on it and  my /home backup will it have all my settings and contacts and email there?

---

### Post by laharrin on 2007-10-21
Settings, yes.  But for contacts and emails it depends on what you're using for email.

---

### Post by rafkin on 2007-10-21
thanks for the quick reply. I am using evolution, I will make a backup of it anyway just in case. thanks again!

---

### Post by Dr Small on 2007-10-21
> **rafkin said:**
> thanks for the quick reply. I am using evolution, I will make a backup of it anyway just in case. thanks again!
That would be wise. But most of your settings for applications are stored in your home folder in hidden folders. As long as Gutsy doesn't overwrite you /home partition, which it should not, everything should be fine.

Dr Small

---

### Post by LanDan on 2007-10-21
have a look at the files in your home that start with a dot .evolution-mail for example, thats where all your e-mail settings are

---

### Post by RTrev on 2007-10-21
> **LanDan said:**
> have a look at the files in your home that start with a dot .evolution-mail for example, thats where all your e-mail settings are

Just a suggestion about something I have found works well for me....

Once I got everything tuned the way I wanted, way back in some previous version of Ubuntu, I took all of the .config files, like .vlc, .mozilla, .gftp, etc., and *moved* them to another drive.. a data drive.

I put them in a directory I just called "symlinks" to remind me of what they were there for.

I then created symbolic links for each of them.

Now, whenever I install any new distro or version of Ubuntu, I simply put a copy of the symbolic link for each application in my new home directory, and rename them.

So, for example, in my /home/bob directory I have a symbolic link called .mozilla.  It points to the *real* .mozilla out on the data drive.  

The advantage, of course, is that I can install anything I want, then just mount the data drive and copy over those links, and all of my distros are using the same config files.. meaning email, newsgroups, etc., are always in synch.

I'd rather not have a single /home directory, because who knows what else might change in there between versions, distros, etc.?  I'd rather just have the application config data the same, and let the new distro do whatever it wants to other files in /home.

Hope this idea helps someone.  It's been working flawlessly for me since at least Edgy.

Bob

---

