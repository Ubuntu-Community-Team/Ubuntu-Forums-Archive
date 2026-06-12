---
title: "Error Message in Synaptic..."
date: 2006-09-09
forum: Absolute Beginner Talk
---

### Post by happyisland on 2006-09-09
Hey again wonderful Ubuntu people. Here's a new problem.
When I click "reload" in Synaptic Package Manager (ie to let it scan to see what I need to update) I get the following error message:

W: Duplicate sources.list entry [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial/main Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_dapper-commercial_main_binary-amd64_Packages)


Everything seems to work fine anyway, but I was wondering if this is something I should be concerned about. If so, how should I fix it?

Thanks!
-HI

---

### Post by nudnik on 2006-09-10
Access the Synaptic Package Manager and click on the settings tab, then choose, repositories. A list should appear, browse it for what appear to be duplicate sources, uncheck the suspected duplicate source.

Be sure to make note of what you uncheck in the event deselecting it causes problems.

](*,) <<The Ubuntu Mascot :biggrin:

---

### Post by jordanmthomas on 2006-09-10
Something that may even be easier (or maybe not)
Press Alt + F2
```

gksudo gedit /etc/apt/sources.list

```
Find a line that says deb [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial/main Packages
Put a # at the beginning of it.
Save and exit.

---

### Post by mssever on 2006-09-10
> **jordanmthomas said:**
> ```

gksudo /etc/apt/sources.list

```
Actually, it should be:
```
gksudo gedit /etc/apt/sources.list
```

---

### Post by jordanmthomas on 2006-09-10
woops!  I'll change it.

---

### Post by mssever on 2006-09-10
> **jordanmthomas said:**
> woops!  I'll change it.

I've made that sort of typo on the command line many times...

---

### Post by happyisland on 2006-09-10
Thanks everybody! I made the change and now I no longer get the error message. Is there any possible problem I should be on the lookout for though now that I have removed the offending line?

---

