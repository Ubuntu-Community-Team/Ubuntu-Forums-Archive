---
title: "Need help updating to newest Java"
date: 2007-01-15
forum: Absolute Beginner Talk
---

### Post by canfield on 2007-01-15
Hello

I am very new to Ubuntu so be kind to me.  I am new to terminal also.

I am running Ubuntu 6.10 on a new machine and can't run Frostwire because on not having newest Java update.  Every time I try to install it it won't go.  After SU It lets me change directory but won't go any further. It stops with no file found.  If someone could take the time to walk me through the steps to load Java please do.


Paul

---

### Post by taurus on 2007-01-15
[https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)

---

### Post by canfield on 2007-01-15
How is this done??

---

### Post by rabid9797 on 2007-01-15
in terminal do:
```

sudo apt-get install java-common
sudo apt-get install java-package

```

---

### Post by taurus on 2007-01-15
Did you even look over the link that I included?  It walks you from adding the extra repos to installing and configuring java...

---

### Post by canfield on 2007-01-15
To install proprietary Java, you must have the Multiverse repository enabled.

So sorry how is this done?

Paul

---

### Post by taurus on 2007-01-15
> **canfield said:**
> To install proprietary Java, you must have the Multiverse repository enabled.

So sorry how is this done?

Paul

Do you see a link to "**Managing Repositories.**" under that?

---

### Post by canfield on 2007-01-15
9797

It did a lt of stuff so I will try installing Frostwire again.

Paul

---

### Post by canfield on 2007-01-15
Did my reading but found this in loading multiverse paper

Navigate to "System" > "Administration" > "Software Properties"

My admin. section does not have Software Properties.

Paul

---

### Post by mikewhatever on 2007-01-15
Software Sources, not Software Properties.

---

