---
title: "How to log in as Root, or pretend..."
date: 2007-07-02
forum: Absolute Beginner Talk
---

### Post by RogerDavis on 2007-07-02
I'm trying to rename or delete a folder I put into  /usr/local/seamonkey. File Manager says it's not mine (belongs to root), so can't do it. How do I log in as root, or tell file manager to let me do it?

Thanks!

---

### Post by nutz on 2007-07-02
```
sudo -s
```

---

### Post by phizikal on 2007-07-02
Try using this command in your shell:

sudo chown YOURUSERNAME  /usr/local/seamonkey

---

### Post by nutz on 2007-07-02
Unless he means log in as root with X session and everything; that would be here...

Found under 'Administration/Login Window' in the system menu by default.

---

### Post by RomeReactor on 2007-07-02
Hi. You could also launch Nautilus as root from the command line:
```
gksudo nautilus
```
Note that you must be careful in what you do while Nautilus is open this way; don't delete or modify *anything* other than the file or folder you want.

EDIT: Logging in as root is *not* a very good idea, in my opinion...

---

### Post by nutz on 2007-07-02
> **RomeReactor said:**
> Hi. You could also launch Nautilus as root from the command line:
```
gksudo nautilus
```

Good to know...

---

### Post by RogerDavis on 2007-07-02
Using a terminal with "gksudo nautilus" worked, everything seems good, except see below:
----------------------------------------
(nautilus:5862): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.
Initializing gnome-mount extension

--- Hash table keys for warning below:
--> file:///root/.Trash

(nautilus:5862): Eel-WARNING **: "nautilus-metafile.c: metafiles" hash table still has 1 element at quit time (keys above)

--- Hash table keys for warning below:
--> file:///root/.Trash

(nautilus:5862): Eel-WARNING **: "nautilus-directory.c: directories" hash table still has 1 element at quit time (keys above)
root@Roger-Ubuntu-desktop:/home/roger# 
----------------------------------------------------------------------

So now the next time I boot the hard drive will spit flames?  Or?

Thanks!

---

### Post by Bachstelze on 2007-07-02
Those messages are normal. Well, more or less, but they're completely harmless.

---

### Post by RogerDavis on 2007-07-02
Is there a way to rate such messages on a scale of 1 to 10, from wierd but harmless and annoying (1) to medium concern (5) to complete system meltdown (10) ?

I'm pretty good at Windoze, but Linux has more confusing ways than I can handle in anything but small doses.  Scarey diagnostics that mean nothing are a worry that I, and I'm sure, many others don't need.

Thanks!

---

### Post by alienexplorers on 2007-07-02
I keep shortcuts on my desktop for both gksudo nautilus and root terminal for ease of use.

---

### Post by Bachstelze on 2007-07-02
> **RogerDavis said:**
> Is there a way to rate such messages on a scale of 1 to 10, from wierd but harmless and annoying (1) to medium concern (5) to complete system meltdown (10) ?

0.01 ;) In fact, they're not even errors but just warnings.

If you want to know, that's because, for some reason, Ubuntu adds lines about Wacom devices in your Xorg.conf by default. And since Xorg cannot find those devices, it throuws a warning.

---

### Post by nutz on 2007-07-02
> **HymnToLife said:**
> 0.01 ;) In fact, they're not even errors but just warnings.

If you want to know, that's because, for some reason, Ubuntu adds lines about Wacom devices in your Xorg.conf by default. And since Xorg cannot find those devices, it throuws a warning.

I don't have those devices in my xorg.conf and it still gave me the message.

---

