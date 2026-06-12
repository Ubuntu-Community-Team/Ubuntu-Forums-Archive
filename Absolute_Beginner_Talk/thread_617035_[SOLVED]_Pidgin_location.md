---
title: "[SOLVED] Pidgin location"
date: 2007-11-18
forum: Absolute Beginner Talk
---

### Post by jordank on 2007-11-18
i'm having some problems with pidgin, so i want to completely remove it. I've already tried removing it from synaptic manager, but that saves some settings somewhere. Can someone tell me exactly where pidgin is stored in my computer, and exactly how i would remove every aspect of it?

---

### Post by jasay on 2007-11-18
You could try the following.  The first command removes pidgin and it's config files.  The second should remove any packages that only pidgin depended on.

```
sudo apt-get --purge pidgin
sudo apt-get autoclean
```

What problems were you having?

---

### Post by jordank on 2007-11-18
well i put linux on my girlfriends computer. She wanted to organize her pidgin, and made a bunch of groups.  the next time she tried to log on, her computer froze and got the error that these contacts were not part of the server list, but only part of the local list.

every time we reinstall we get an error, the computer opens a million windows trying tocorrect these buddy groups, and it freezes again.

Even after typing the codes you gave me, pidgin still remembers her email account.  I want to delete pidgin, and everything about pidgin so that it does NOT remember the email account i last signed in with it when i reinstall.  Any help is awesome.

Reinstall from add/remove does not work either.  Or synaptics.

---

### Post by jordank on 2007-11-18
what is pidgin's directory?

---

### Post by jordank on 2007-11-18
sudo apt-get remove -purge pidgin pidgin-data
...
E: couldn't find package -purge

---

### Post by RomeReactor on 2007-11-18
Hi. Try deleting the **.purple** folder on your home directory. Press CTRL+H to see it (it's a hidden file), and then run Pidgin again.

---

### Post by jordank on 2007-11-18
haha yeah just tried that, except i only needed to delete the accounts file. All is good now. thanks.

---

### Post by jasay on 2007-11-18
> **jordank said:**
> sudo apt-get remove -purge pidgin pidgin-data
...
E: couldn't find package -purge

Sorry. Forgot a word.  My bad.
```
sudo apt-get remove --purge pidgin
```

The user specific data is stored under the home directory in a hidden folder(hit ctrl+h in nautilus to view it) called .purple (at least in Gutsy).

Edit.  Too slow.

---

