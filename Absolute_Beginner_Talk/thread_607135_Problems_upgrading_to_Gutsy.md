---
title: "Problems upgrading to Gutsy"
date: 2007-11-08
forum: Absolute Beginner Talk
---

### Post by jondecker76 on 2007-11-08
Out of 5 computers that I own, only one would upgrade through Update Manager.. The rest get various errors...

So I"m going to try to fix them one at a time..

This one is for my Daughter's computer..  When I hit the Upgrade button from the Update Manager, it downloads 2 files then nothing happens.  When launching from terminal, I can see there are errors:

```

samantha@samantha-desktop:~$ update-manager
extracting '/tmp/tmpQ8XUrC/gutsy.tar.gz'
Traceback (most recent call last):
  File "/usr/lib/python2.5/site-packages/UpdateManager/UpdateManager.py", line 914, in on_button_dist_upgrade_clicked
    fetcher.run()
  File "/usr/lib/python2.5/site-packages/UpdateManager/Core/DistUpgradeFetcherCore.py", line 160, in run
    if not self.extractDistUpgrader():
  File "/usr/lib/python2.5/site-packages/UpdateManager/Core/DistUpgradeFetcherCore.py", line 98, in extractDistUpgrader
    tar = tarfile.open(self.tmpdir+"/"+os.path.basename(self.uri),"r")
  File "/usr/lib/python2.5/tarfile.py", line 1144, in open
    raise ReadError("file could not be opened successfully")
tarfile.ReadError: file could not be opened successfully





```

What can I do to get this to upgrade?
This computer is currently in the Feisty release, with no modifications at all - only repository added software...

thanks,

Jon

---

### Post by bks on 2007-11-08
Try running the same terminal command with 'sudo'.

```

sudo update-manager

```

---

### Post by markharding557 on 2007-11-08
ubuntu upgrading is unreliable it is easier to have a separate home partition and then do fresh installs

---

### Post by markharding557 on 2007-11-08
> **bks said:**
> Try running the same terminal command with 'sudo'.

```

sudo update-manager

```

update manager runs with root privaledge anyway dosen't it

---

### Post by jondecker76 on 2007-11-08
Reinstalling in absolutely UNACCEPTABLE

If it does not work, it should not be a part of Ubuntu, period. I'm not going to try to back up 100+ gigs of personal data because upgrading doesn't work - nobody should have to.

Can anyone help me fix this?

---

### Post by Mondoman on 2007-11-08
You note > . When I hit the Upgrade button from the Update Manager, it downloads 2 files then nothing happens. 
Could you give more detail on the "nothing happens" part?  I know when I updated from Feisty, it took about 36 hours because of the load on the servers.
Also, I seem to remember reading that you need to have all updates to Feisty installed *before* updating to Gutsy.

---

### Post by jondecker76 on 2007-11-08
I mean nothing happens..  The dialogs disappear and absolutely nothing is going on..

However, running sudo update-manager from the terminal is working for some reason.  It did have a dbus error, but nothing that is stopping the upgrade from stating..

I'm still curious why it works running root from the terminal, but not from System->Administration->Update Manager

---

