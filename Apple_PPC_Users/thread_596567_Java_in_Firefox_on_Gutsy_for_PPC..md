---
title: "Java in Firefox on Gutsy for PPC."
date: 2007-10-29
forum: Apple PPC Users
---

### Post by Macubus on 2007-10-29
Hey there, I've been struggling for some time with this, so hopefully someone can enlighten me on a better solution..

I am the owner of a G5 imac, and have been struggling to get firefox to work with the ibm 1.5 jre, that I built as described here: [https://help.ubuntu.com/community/Java]("https://help.ubuntu.com/community/Java")

All java things seem to work except firefox.  No matter what I do, the plugin doesn't seem to work with the firefox included in Ubuntu. I have made countless builds, properly linked to the plugin, but nothing seems to work...  I did manage to get it to work by hacking apart an iceweasel deb from etch, giving it the same dependencies as the firefox package, and rebuilding it, but if someone knows what the skinny is with this, it would be greatly appreciated.

Thanks, Macubus.

---

### Post by frog_pilot on 2007-10-30
thats what I mentioned with feisty [http://ubuntuforums.org/showthread.php?t=535196]("http://ubuntuforums.org/showthread.php?t=535196")

---

### Post by Macubus on 2007-10-30
Unfortunately, this happens even if you do make a proper symbolic link, so I'm not sure its the same issue..  Can someone else confirm a similar issue to this?

---

### Post by frog_pilot on 2007-10-31
You can verify this if you look into the firefox-plugin-folder as stated in the discussion. If the symlink for the javaplugin is pointing to the right location, this wont help you - tell your special problem. If not, execute the posted commands... What's the problem :confused:

To verify the recommendet symlink, simply look for the location of ```
libjavaplugin_oji.so
```

---

