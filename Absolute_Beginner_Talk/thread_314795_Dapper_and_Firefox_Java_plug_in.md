---
title: "Dapper and Firefox Java plug in"
date: 2006-12-08
forum: Absolute Beginner Talk
---

### Post by Sef on 2006-12-08
I am helping my friend in Oz with installing Ubuntu.  Got the repositories set up and she was able to download java.  However, there was not a plug in for Firefox. How can she get a java plug in for firefox?

---

### Post by seijuro on 2006-12-08
I had a simmilar issue I found a plugin in /etc/alternatives with the name firefox-javaplugin.so and just created a sym link to it in the firefox plugin directory ran fine after that.

Also I almost never see it mentioned but the Sun's installer for linux runs fine in dapper so you can use their package right off the main site as well.

---

### Post by Sef on 2006-12-08
> I had a simmilar issue I found a plugin in /etc/alternatives with the name firefox-javaplugin.so and just created a sym link to it in the firefox plugin directory ran fine after that.


How do you create the sim link?

---

### Post by seijuro on 2006-12-08
```
ln -s /path/to/file
```

---

### Post by Sef on 2006-12-08
How do I find the path to the file? (I m helping her over the computer, so I need to be very explicit when explaining this.)

---

### Post by seijuro on 2006-12-08
well if she has the file it should be in /etc/alternatives so I would cd to that directory do a ls and see if firefox-javaplugin.so is listed if not you'll have to get the plugin from a repo or sun's site. if it is there cd to /usr/lib/firefox/plugins/ then type sudo ln -s /etc/alternatives/firefox-javaplugin.so remember to close firefox and reopen it for plugins to load.

---

### Post by Sef on 2006-12-08
Thank you for your help.

Update: To get the firefox java plugin, this is what I had her do in her terminal:

```
sudo aptitude update
```

```
sudo aptitude install sun-java5-plugin
```

---

### Post by seijuro on 2006-12-08
no problem let me know how it turns out.

---

### Post by Sef on 2006-12-08
Thank you so much for your help.  After a few false starts, she has the java plug in installed in firefox.

---

### Post by seijuro on 2006-12-08
Awesome!

---

### Post by k1001001 on 2006-12-11
This worked for me as well. Finally. I was getting very frustrated with the other suggestions, none of which mentioned creating a link to /etc/alternatives, and none of which worked. To get Java working though, I had to actually *uncheck* the "Enable Java" option in Firefox 2.0. Whatever. It works. Thanks!

---

### Post by tophatandy on 2006-12-11
worked for me.

thanks so much.

:D

---

