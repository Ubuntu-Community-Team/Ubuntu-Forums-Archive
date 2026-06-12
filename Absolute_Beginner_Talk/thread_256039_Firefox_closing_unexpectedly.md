---
title: "Firefox closing unexpectedly"
date: 2006-09-12
forum: Absolute Beginner Talk
---

### Post by jmtjet on 2006-09-12
This started happening yesterday. I'll open Firefox and browse a few pages. Then Firefox will close without warning. Nothing, it just closes as if I hit the close X. Anyone experience this problem? Any ideas on how to correct it? TIA.

---

### Post by junglepeanut on 2006-09-12
Do you recall what pages they are. I have issues with pages that have mad crazy java on them. Firefox 2.0b2 fixed alot of issues but not all.

---

### Post by tomj on 2006-09-23
I have been having the same problem. I havn't seen any pattern to it so far. Its rather frustrating when you have a lot of tabs open.

---

### Post by powder on 2006-09-23
Have you tried crating a new profile?

```
mv .mozilla .mozilla_backup
```

Now run Firefox, it will create a new profile automatically.

---

### Post by Dinerty on 2006-09-23
> **jmtjet said:**
> This started happening yesterday. I'll open Firefox and browse a few pages. Then Firefox will close without warning. Nothing, it just closes as if I hit the close X. Anyone experience this problem? Any ideas on how to correct it? TIA.

I also found Firefox highly unstable on Dapper with version 1.5 and beta 2 (Obviously beta 2 is bound to have some bugs)

I notice it crashes after watching flash videos

---

### Post by tomj on 2006-09-30
After creating a new profile the problem has stopped thanks powder. make sure you back up your bookmarks before you do it :( . I installed the most up to date version of flash and removed the old version from the plugins folder and flash videos are now working fine and so far i haven't had firefox crash after a playing a video.

---

### Post by CatKiller on 2006-09-30
You should be able to retrieve your old bookmarks. They'll be stored as a HTML file in your ~/.mozilla_backup folder.

---

### Post by andiii on 2006-09-30
> **tomj said:**
> I have been having the same problem. I havn't seen any pattern to it so far. Its rather frustrating when you have a lot of tabs open.

Use the extension "Sessionmanager"

---

### Post by tomj on 2006-10-01
Thanks i managed to find the bookmarks. I dont think i will install session manager as the reviews i have read says it tends to slow down firefox. My computer isn't particularly snappy. If there is something that i need to get back i can always look in the history thanks for the suggestion though.

---

### Post by altonbr on 2006-10-01
I had the same problem here: [http://www.ubuntuforums.org/showthread.php?t=248949]("http://www.ubuntuforums.org/showthread.php?t=248949")

But I wasn't able to find any solutions.

This looks promising though:

> 
Have you tried crating a new profile?

Code:

mv .mozilla .mozilla_backup

Now run Firefox, it will create a new profile automatically.


---

