---
title: "How to update Pidgin?"
date: 2007-10-27
forum: Absolute Beginner Talk
---

### Post by h2z on 2007-10-27
I'm using the Pidgin version that came with Gutsy (2.2.1). The Pidgin developers have released a new version (2.2.2) a few days ago, what do I have to do in order to update to that newest version (without loosing my settings and logs obviously)?
Do I have to completely remove (using add/remove) the older version of Pidgin and compile the new one? Do I just compile the new one which will overwrite the older one?

---

### Post by Martje_001 on 2007-10-27
> **h2z said:**
> I'm using the Pidgin version that came with Gutsy (2.2.1). The Pidgin developers have released a new version (2.2.2) a few days ago, what do I have to do in order to update to that newest version (without loosing my settings and logs obviously)?
Do I have to completely remove (using add/remove) the older version of Pidgin and compile the new one? Do I just compile the new one which will overwrite the older one?
Remove the current one, and compile. It will not erase your setting, as it's in you home-folder.

---

### Post by llamakc on 2007-10-27
Neither.

When you download and compile the source for the most recent release, the binary will be placed in /usr/local/bin instead of /usr/bin, so in essence you will have two concurrent pidgins, the Ubuntu version at /usr/bin/pidgin (2.2.1 until updated in the repos) and /usr/local/bin/pidgin (2.2.2). 

Any launcher you create would need to call the new version by its full path.

Yes, it will use your current logs and account info in ~/.purple.

Unless there is some to-die-for feature I'd wait for the repositories to be updated.

PS: Don't forget to install `build-essential`. Also, if the source code complains about missing dependencies, this means you would need to install the *-dev package. For example, when you run `./configure` in the source code directory it may fail and spit out that it needs "foo2". You would then install FROM THE REPOSITORIES the "foo2-dev" package.

HTH

---

### Post by h2z on 2007-10-27
Thanks, I guess I'll wait for repros to update to the newest versoin as I'm not really affected by that crash/fix.

---

### Post by bentelk on 2007-11-02
I will also wait.  not everyone wants to get their hands dirty compiling programs :P

---

