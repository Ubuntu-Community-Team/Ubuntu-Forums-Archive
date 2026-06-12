---
title: "umask is 002, why can Group member write?"
date: 2006-11-07
forum: Absolute Beginner Talk
---

### Post by szf on 2006-11-07
Both my wife & I have 'umask 002' in $HOME/.bash_profile - but when our digicam uses the default Gnome-based file import - the imported files are not writable for the (local) group. What am I missing? I expect that apps would create new directories with a 775 permissions set, allowing easy file usage between us...

---

### Post by po0f on 2006-11-07
szf,

Are you and your wife in the safe primary group?  Usually Ubuntu creates users with their username as their primary group as well.  It might also depend on how you created the directory, ie making a new folder in Nautilus as opposed to `mkdir folder` in the terminal.  Sometimes a modified environment (is this the word?) is used in a desktop session, overwriting whatever your defaults are.

The umask might just be applied on top of the default one as well, pretty much cancelling your umask out.

---

### Post by szf on 2006-11-08
We are in the same primary group. The photo import utility creates an import folder in the media share owned by username : primarygroup (i.e. owner = szf; group = localgroup), but the 'Number view' of the folder is 1600755 rather than 1600775 (full perms owner & group)...

---

### Post by po0f on 2006-11-08
szf,

According to [this](http://www.cse.msu.edu/cgi-bin/man2html?profile?4?/usr/man), you can set your umask in ~/.profile.  This should work as long as your gid and your wife's gid are the same, as you said they were.  Note that this will affect *all* files/folders created by you.

[EDIT]

Can you post the relevant bits of the script that creates the folders?

---

### Post by szf on 2006-11-09
Thanks for the replies po0f -

I'm guilty here of not understanding what's underneath the handlers... The handler is gnome-volume-properties (GUI), and it's leveraging the gthumb application for the PTP (camera) import. Maybe I'm wrongly thinking that a $HOME/.bash_profile entry is referenced by the import utility, I simply don't know, and don't know where to look.

---

### Post by szf on 2006-11-09
hrrmm, you did point out $HOME/.profile and did so explicitly - I never tried that. I will do so now.

---

### Post by szf on 2006-11-09
Ah, the same, the same. Number ID of the import folder is 1600755.

---

### Post by po0f on 2006-11-09
szf,

Is there any way you can access the camera directly ala USB mass storage device?

---

### Post by szf on 2006-11-10
Yes. The handler app jumps in first - and it's welcome to do so, but I've got something to fix when it does (group perms).

As a USB mass storage drive, I can create a folder with the expected 775 permissions - but then I've got to drag & drop the photos from the device.

---

### Post by po0f on 2006-11-10
szf,

I think your issue lies with gnome-volume-manager if you want to solve the problem the way you want it solved.  I've tried googling for information but have come up empty-handed, maybe you will have better luck.  :)

---

### Post by szf on 2006-11-10
Thanks for the support - this is one for me to ruminate upon - as I've come up empty handed, too.

---

