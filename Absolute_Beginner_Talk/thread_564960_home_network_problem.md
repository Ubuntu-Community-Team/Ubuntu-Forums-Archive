---
title: "home network problem"
date: 2007-10-01
forum: Absolute Beginner Talk
---

### Post by ubunoobie on 2007-10-01
Hi, I am having a problem setting up my ubuntu machine on my home network with other windows machines. I read in other threads that the simplest way is to right click on a folder and click on "Share folder..." and just follow the prompts, which I did, but then I got an error message that said "Could not apply changes! Fix broken packages first."

What now?

Any help is appreciated, thanks!

---

### Post by por100pre1 on 2007-10-01
Try this in terminal:

```
sudo dpkg --configure -a
```

EDIT: If samba is not present:

```
sudo aptitude install samba
```

---

### Post by ubunoobie on 2007-10-01
> **por100pre1 said:**
> Try this in terminal:

```
sudo dpkg --configure -a
```

EDIT: If samba is not present:

```
sudo aptitude install samba
```

Hi, thanks for this... now, once I've done this, what do I do?

I typed the first instructions into the terminal and nothing happened, so then I typed the second set of instructions into the terminal and I was asked to download samba. What do I do next?

---

### Post by gamerteck on 2007-10-01
Go to System >> Administration >> Shared Folders.

Or you can navigate to the folder you want to share, right click it and then select **Share Folder**.

---

### Post by coolen on 2007-10-01
You should have been prompted to install either Samba or NFS (or both) when you first tried to share a folder. With them installed, other users should see you on the network, and be able to get a neat little password prompt. You'll need to setup a password (smbpasswd *user* I think), although mine always complained. You could also go fiddle with smb.conf and try to get anonymous sharing.

---

### Post by ubunoobie on 2007-10-01
> **gamerteck said:**
> Go to System >> Administration >> Shared Folders.

Or you can navigate to the folder you want to share, right click it and then select **Share Folder**.

Ok, thanks! So then I'm done with the terminal?... I don't need to mess with samba anymore?

Now I can see my windows machines on the network from my ubuntu machine, but from my windows machine I can't see the ubuntu machine... any reasons for this?

---

### Post by ubunoobie on 2007-10-01
Aha! I noticed when I click on "View workgroup computers" in my windows network, the ubuntu machine shows up... now when I try to access, a dialog box asks me for a username and password.

---

### Post by coolen on 2007-10-01
You'll need to set the password with smbpasswd, or there's an option in smb.conf to sync with the Unix passwords (in which case, restarting samba will be necessary):
```
sudo /etc/init.d/samba restart
```
That'll probably do the trick.

---

### Post by elgalloloco on 2007-10-29
> **coolen said:**
> You'll need to setup a password (smbpasswd *user* I think)

Thanx u sir, this did the trick!

---

