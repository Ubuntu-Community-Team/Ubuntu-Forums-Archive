---
title: "Moving Evolution Configuration"
date: 2006-12-21
forum: Absolute Beginner Talk
---

### Post by stuman on 2006-12-21
Installed edgy in a new vm.  I would like to to move my evolution setup from 6.06.  I have copied the ~/.evolution folder and the ~/gconf/apps/evolution folder, but the accounts did not show up.  What am I missing?](*,)

---

### Post by bluefrog on 2006-12-21
if memory serves there is a third one involved indeed but don't remember where. must be somewhere in ~/ though

James

---

### Post by stuman on 2006-12-21
I'm also looking for a way to retrieve a saved password for a pop3 account.  I saved the password for retrieving mail, but did not have a need to send any through that account until after I forgot the password.  If I can locate the encrypted password store, I might be able to hack it into the send password store and be ok.  Just trying to do this the easy way.

---

### Post by greymoose58 on 2007-01-07
> **bluefrog said:**
> if memory serves there is a third one involved indeed but don't remember where. must be somewhere in ~/ though

James

If you haven't found it yet I think the third file is ~/.gnome2_private/Evolution

---

### Post by stuman on 2007-01-07
Problem solved.  I actually found an obscure note to the missing password that allowed me to simply configure my new machine without "moving" evolution configuration information.  Thanks to all who provided tips on where to look...it may prove useful in the future.

---

### Post by nab on 2007-02-11
If you want to move a Evolution configuration do it in two steps:

**On the old installation:**

1.) open a terminal
2.) shutdown evolution: evolution --force-shutdown
3.) archive the following folders: 
.evolution
.evolution2 (sometimes)
.gconf/apps/evolution and
.gnome2_private/Evolution
4.) move archive to new installation

**On the new installation**

1.) open a terminal
2.) shutdown evolution: evolution --force-shutdown
3.) shutdown the gconftool-2: gconftool-2 --shutdown
4.) unpack archive in your HOME-directory
5.) start your evolution on the new installation

hope this helps,
Nikolaus

---

### Post by stuman on 2007-02-13
Thanks for the information.  It will prove useful the next time I need to move my evolution setup.

---

