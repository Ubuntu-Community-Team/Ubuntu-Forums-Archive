---
title: "Update to Edgy Eft"
date: 2007-09-20
forum: Absolute Beginner Talk
---

### Post by .Panic on 2007-09-20
Hello good people of Ubuntu. Before I ask for you help, I want to say thanks for helping me. :)

I'm trying to update from Dapper Drake to Edgy Eft.

[list=1][*]I type this in the terminal as root or su
```
update-manager -c
```

[*]It then looks for all updates.
[*]It finds the update for 6.10
[*]I click upgrade.
[*]It fetches the files for the upgrade,
but then bam. I get this message. 

[IMG]http://i9.tinypic.com/66t2vbm.png[/IMG][/list]

Please help me fix this.

Thanks,



.Panic

---

### Post by FuturePilot on 2007-09-20
I'm not sure but it looks like you're still running Breezy. It's trying to make sure the current system is up-to-date before upgrading but it can't find the Breezy repos since they've been taken off line. At least the main ones have. You might be able to find one on a different server somewhere. Assuming you are running Breezy you'll have to upgrade to Dapper before going to Edgy. So you might want to just change Breezy to Dapper in your sources.list

---

### Post by .Panic on 2007-09-20
> **FuturePilot said:**
> I'm not sure but it looks like you're still running Breezy. It's trying to make sure the current system is up-to-date before upgrading but it can't find the Breezy repos since they've been taken off line. At least the main ones have. You might be able to find one on a different server somewhere. Assuming you are running Breezy you'll have to upgrade to Dapper before going to Edgy. So you might want to just change Breezy to Dapper in your sources.list

Uhh... how do I go about changing the sources.list. 

Thanks.

---

### Post by Maestro23 on 2007-09-20
> **.Panic said:**
> Uhh... how do I go about changing the sources.list. 

Thanks.

Upgrading Breezy to Dapper: [https://help.ubuntu.com/community/DapperUpgrades](https://help.ubuntu.com/community/DapperUpgrades)

---

### Post by Sef on 2007-09-21
> Assuming you are running Breezy you'll have to upgrade to Dapper before going to Edgy. So you might want to just change Breezy to Dapper in your sources.list

If you want to upgrade more than one version, it is easiest to do a clean install, i.e., install from a cd.

---

### Post by .Panic on 2007-09-22
> **Sef said:**
> If you want to upgrade more than one version, it is easiest to do a clean install, i.e., install from a cd.

Okay. I just ordered the CD. I can you close/lock the thread. 

Thanks guys.

---

