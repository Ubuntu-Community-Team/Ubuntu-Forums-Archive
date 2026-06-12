---
title: "Firefox Profiles"
date: 2007-02-19
forum: Absolute Beginner Talk
---

### Post by zuesko on 2007-02-19
I have just upgraded  Firefox/2.0.0.1 and want to setup personal profile.
Please advise how and were to run firefox ProfileManager. I have tried and and continually get error message "no such file or directory.
Any help would be greatly appreciated:confused:

---

### Post by Detonate on 2007-02-19
When you open Firefox as a user the first time, a profile is automatically created under that user's home directory.  If another user opens Firefox, a new profile is created in that user's home directory.  And so forth. No need to run a profile manager.

---

### Post by petersjm on 2007-02-19
But if you wanted to create an additional profile for testing etc, I believe you simply type the following in Terminal/Konsole:

```
./firefox -profilemanager
```

And remember you MUST have all occurances of Firefox closed before running this, or the profile manager will not load. Oh, and you need the dash (-) before the "P", as well.

---

### Post by flanagan on 2007-02-19
And here is an article that will tell your about your Firefox profile, where it is, and what is in it: [http://kb.mozillazine.org/Profile](http://kb.mozillazine.org/Profile)

Here is another article specifically about running the profile manager: [http://kb.mozillazine.org/Profile_Manager](http://kb.mozillazine.org/Profile_Manager)

---

