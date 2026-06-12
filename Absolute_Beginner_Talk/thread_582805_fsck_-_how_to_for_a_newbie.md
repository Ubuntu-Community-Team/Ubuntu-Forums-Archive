---
title: "fsck - how to for a newbie?"
date: 2007-10-20
forum: Absolute Beginner Talk
---

### Post by qprfact on 2007-10-20
Due to a problem outlined in this thread - [http://ubuntuforums.org/showthread.php?t=579942](http://ubuntuforums.org/showthread.php?t=579942) - I no longer have Update Manager running and can't get to shiny new Gutsy.

It's been suggested that fsck can possibly solve my problems. I've Googled it, but it looks a little daunting - can any kind soul treat me like a simpleton and give me really straightforward instructions for it please?!!

Thanks!

---

### Post by mikeyphi on 2007-10-20
1. It is possible to update using the 'Alternate'CD
2. If you want to run 'fsck' you should do so with your disk unmounted.... try through the LiveCD 
3 Perhaps a 'clean' install?

---

### Post by qprfact on 2007-10-20
I must be really dim, as I've downloaded the alternate CD, burnt the ISO and booted up with it and - although it has different options from the desktop CD - I can't see anything that says upgrade.

Which option do I take? Everything seems to point towards a fresh install!

Failing that, what do I need to do to run fsck with disk unmounted? Does that mean I boot up with the desktop CD, then when the Ubuntu desktop has appeared, fire up terminal and type fsck? Is that all I need to do?

Clean install is an option - just trying to avoid that at present as that means re-installing all programs, settings, etc (though not data, that's on my Windows partition)

Thanks in advance!

---

### Post by qprfact on 2007-10-20
D'oh! I don't boot from it, do I? Trying it again now....

---

### Post by qprfact on 2007-10-20
Nothing! I have the disk in. I press ALT F2 and get the box, I type:

```
gksu "sh /cdrom/cdromupgrade"
```

Nothing happens.

I try changing it to gksu "sh /cdrom0/cdromupgrade" and gksu "sh /cdrom1/cdromupgrade" to see if that makes any difference. Nothing either!

What am I doing wrong?! I even signed in as root and tried - no dice there either!

---

### Post by mikeyphi on 2007-10-20
You didn't do anything wrong!!!
Should've realised that with a broken update manager there would be problems!!

"Failing that, what do I need to do to run fsck with disk unmounted? Does that mean I boot up with the desktop CD, then when the Ubuntu desktop has appeared, fire up terminal and type fsck? Is that all I need to do?"

Confirm that the disk is actually unmounted - should be able to see it under Places/Computer...right click the icon and select unmount - if necessary.

---

### Post by qprfact on 2007-10-20
Ah! Not going mad then!

OK, here I am in Live CD mode. My hard drive isn't mounted, so into terminal I go, type fsck and...
```

ubuntu@ubuntu:~$ fsck
fsck 1.40.2 (12-Jul-2007)
```

Is that it???!!

---

