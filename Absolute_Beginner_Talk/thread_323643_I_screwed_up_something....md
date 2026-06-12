---
title: "I screwed up something..."
date: 2006-12-22
forum: Absolute Beginner Talk
---

### Post by Jussi01 on 2006-12-22
I just tried to install skype, and it would have gone smoothly, if I hadnt been so stupid. Halfway through the install, I, being neat and tidy kinda guy, decided the .deb would be better in a different directory than my desktop - so I moved it. This screwed up my synaptic and my update manager. can someone help me fix it?

---

### Post by PriceChild on 2006-12-22
```
sudo apt-get -f install
```Tell me what that says...

---

### Post by Jussi01 on 2006-12-22
Here you are

```
jussi@jussi-laptop:~$ sudo apt-get -f install
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package skype needs to be reinstalled, but I can't find an archive for it.
jussi@jussi-laptop:~$ 
```

---

### Post by dannyboy79 on 2006-12-22
what about just moving it back?

---

### Post by PriceChild on 2006-12-22
Please try to reinstall the package as it suggests :)

---

### Post by Jussi01 on 2006-12-22
Yeah, Ive tried moving it back, when I open synaptic it says:

E: The package skype needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.

If i try double clicking on the package  it says:

Could not open "skype debian..."

The pakage might be corrupted or you are not allowed to open the file. check the permissions on the file.

Help?

I have treid downloading a new file from skyp but this is still no good... :(

---

### Post by Jussi01 on 2006-12-22
Ok, resolved it - I added the skype repo's and then did apt-get update and apt-get install skype and it fixed it :):)

---

### Post by az on 2006-12-22
Were you using the GUI to install the deb or the command line.

Perhaps file abug about this.  Dpkg (or at lease Gdebi) should handle that more elegantly....

---

### Post by PriceChild on 2006-12-22
> **azz said:**
> Were you using the GUI to install the deb or the command line.

Perhaps file abug about this.  Dpkg (or at lease Gdebi) should handle that more elegantly....+1

Please file a bug at bugs.ubuntu.com

---

