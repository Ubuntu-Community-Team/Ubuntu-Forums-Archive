---
title: "Sync Profiles Between Two Machines"
date: 2007-12-26
forum: Absolute Beginner Talk
---

### Post by jas0 on 2007-12-26
I have tried searching for this, but it seems that all threads pertaining to this issue have zero replies.

I know in theory how to make this work using rsync, but I want to know whether it's possible and will work.

What I want to do is share the profile of my desktop machine with my laptop machine. Both machines have the same software installed and the same user account names. If i rsync my desktop profile to laptop profile and overwrite all files, will end up with the same settings on both or a botched laptop user profile?

---

### Post by p_quarles on 2007-12-26
I'm not sure what you mean by "profile." If you just mean your user's home directory, then yeah, that could easily work.

That said, I wouldn't rsync the entire directory: you could end up messing up things like .dmrc. I would recommend synching specific configuration and data directories, rather than the whole thing. Profiles for apps like Firefox and Tomboy are very portable, and this should work nicely. But there's no point in synching any thing that you don't need to.

---

### Post by Hospadar on 2007-12-26
all of your user data is stored in the home directory for each user, so if you have the *exact* same hardware and software installed ideally everything would go off without a hitch.  Probably however, some configurations for certain things might need to be a little different, so I'd back up the target machine, and try moving everything you think you'll need, and then monkey around a bit until you get it set the way you want.

Probably any application-specific configuration folder would transfer over fine, as well as the gnome and gnome2 and bashrc files/folders, some of the more picky startup scripts might complain, but if you have a backup it should be easy to work out.

---

### Post by jas0 on 2007-12-26
Thank you for the responses. I am going to test moving specific directories from one home folder to the other and report back with my results.

---

