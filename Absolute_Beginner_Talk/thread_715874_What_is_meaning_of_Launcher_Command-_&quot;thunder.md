---
title: "What is meaning of Launcher Command- &quot;thunderbird %u&quot;"
date: 2008-03-05
forum: Absolute Beginner Talk
---

### Post by AlP36 on 2008-03-05
The command to launch Firefox and Thunderbird has a "%u" after the app name. Could some one explain what it means? I can't find any references to it in man or help. I think it was in the instructions for setting up Firefox and it worked but I don't understand it.

---

### Post by Awperator on 2008-03-05
> **AlP36 said:**
> The command to launch Firefox and Thunderbird has a "%u" after the app name. Could some one explain what it means? I can't find any references to it in man or help. I think it was in the instructions for setting up Firefox and it worked but I don't understand it.

I would assume that it means 'per this user'... meaning that it should load thunderbird with your user information and settings. Just a guess though.

---

### Post by glennric on 2008-03-05
The %u will substitute a url or file name.  For instance if you add that launcher to your panel or put it on your desktop and click and drag a file onto the launcher, the file will open in thunderbird.  I am not exactly sure what this will do with thunderbird (it may add the file as an attachement to an email), it is more effective with firefox.

---

### Post by Cogito² on 2008-04-28
I was wondering about this as well. If you remove the "%u", it loads up and goes straight to your inbox. If you leave the "%u" in, it seems to keep you from going to your inbox and doesn't check messages right away. I like the function better sans "%u" so I just removed it, but if someone happens to read this and know specifically what it does, I'd be curious to know.

The only thing I can think of is that using "%u" to keep the inbox from checking messages right away keeps thunderbird from checking emails "too quickly"...since if thunderbird is able to load before your internet connection resolves (might take a moment with wireless), it will tell you that it has no connection which can be annoying...but I'm sure there's another reason as well.

---

