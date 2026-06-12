---
title: "How Do I Know If It Worked?"
date: 2007-01-02
forum: Absolute Beginner Talk
---

### Post by CheshireMac on 2007-01-02
Hey folks . . .I just restarted my machine after upgrading to Edgy . . . it's working, and I'm online with no problems . . .but everything looks identical, and there's no welcome-mat to the new version . . .the only thing I noticed change in was the boot screen . . .am I crazy?

---

### Post by NeoLithium on 2007-01-02
No, you're not crazy; edgy's not a massive difference from dapper in any blatant sense, it's more cutting edge programs that are the latest releases, really.

---

### Post by CheshireMac on 2007-01-02
> **NeoLithium said:**
> No, you're not crazy; edgy's not a massive difference from dapper in any blatant sense, it's more cutting edge programs that are the latest releases, really.

Okay, so unless my machine blows up right now, all is good? I've got no errors, and everything seems to be working as it should . . I've run a couple tests to check.

---

### Post by Iarwain ben-adar on 2007-01-02
> **CheshireMac said:**
> Hey folks . . .I just restarted my machine after upgrading to Edgy . . . it's working, and I'm online with no problems . . .but everything looks identical, and there's no welcome-mat to the new version . . .the only thing I noticed change in was the boot screen . . .am I crazy?

You could try with 
```
lsb_release -a
```

That will show you what version you are running :wink:


Iarwain

---

### Post by maxamillion on 2007-01-02
Open up a terminal and type ```
uname -r
```

if your kernel version (which is what that command will output) now looks like ```
2.6.17-10-generic
```

your upgrade went fine and you are now running edgy

if it still says ```
2.6.15-28-<processor_architecture_here>
``` you are on dapper still.

---

