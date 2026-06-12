---
title: "Stop a program from updating"
date: 2007-10-03
forum: Absolute Beginner Talk
---

### Post by Cloey64 on 2007-10-03
Is there any way I can stop one program from checking for updates but let every other one check? I have to run an older version of Wine because the newest one doesn't work with a game I have, odd that the older version works and the newer one doesn't, so it keeps saying I have an update. I would like to still have it notify me about all other updates, just not the one about Wine. Can anybody help?

---

### Post by llamakc on 2007-10-03
Yes, you can pin it. How are you currently getting updates?

---

### Post by bodhi.zazen on 2007-10-03
In a terminal :

use ```
sudo echo "xyz hold"|dpkg --set-selections
```

where xyz is the package you want to hold.

> sudo echo "wine hold"|dpkg --set-selections
[list][*]for wine[/list]

---

### Post by Cloey64 on 2007-10-03
I put in the terminal code but it still shows that there is an update. Do I need to restart the update thing? I am using the update manager to get my updates.

---

### Post by rsambuca on 2007-10-04
Can you use synaptic and select "Package - Lock Version"?

---

### Post by Cloey64 on 2007-10-04
I have tried both the terminal code and going into the Synaptic and Forcing the older version I have installed.I would just get rid of the icon, but I always forget to update other things unless it pops up.

---

### Post by rsambuca on 2007-10-04
> **Cloey64 said:**
> I have tried both the terminal code and going into the Synaptic and Forcing the older version I have installed.I would just get rid of the icon, but I always forget to update other things unless it pops up.

I know there is a 'force version', but have you tried the 'lock version' option?  I think you should be able to then just update and it will ignore updates to the locked version.

---

### Post by Malibu Illusion on 2007-10-04
Do this:

```
gksudo gedit /etc/apt/preferences
``` 

(or whatever your favorite editor is)

Insert into that file:

```
Package: *package name here*
Pin: *version number here*
Pin-Priority: 1001
```

Then do:

```
sudo aptitude update
```

---

### Post by Cloey64 on 2007-10-04
> **rsambuca said:**
> I know there is a 'force version', but have you tried the 'lock version' option?  I think you should be able to then just update and it will ignore updates to the locked version.

Thank you, I must have missed the Lock Version option at first. I tried it now and it doesn't keep asking me to update Wine any more.

---

### Post by rsambuca on 2007-10-04
Good stuff!  Mark the thread solved!

---

