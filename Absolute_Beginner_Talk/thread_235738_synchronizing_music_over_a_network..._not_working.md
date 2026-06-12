---
title: "synchronizing music over a network... not working"
date: 2006-08-13
forum: Absolute Beginner Talk
---

### Post by xxFelixDCatxx on 2006-08-13
Okay, I've recently installed the latest version of ubuntu, which finially supports all drivers on my laptop, I'm very excited about using linux in general, because I know in general it works far better than any other os.

That said, I'm having one issue that is going to drive me nuts.  I store all of my music on a remote windows server 2003, because my laptop severly lacks harddrive space.  Before, I distinctly remember being able to navigate to this remote folder and add these files to the library of any music program I chose to use.  Now however I cannot do this, and it's driving me nuts... in fact totem is the only one that will even play these files over the network, but it has no library at all.  

Does anyone have any suggestions at all?  I feel like I'm doing something wrong, and being as new as I am, probably am.

---

### Post by klytu on 2006-08-13
> **xxFelixDCatxx said:**
> Okay, I've recently installed the latest version of ubuntu, which finially supports all drivers on my laptop, I'm very excited about using linux in general, because I know in general it works far better than any other os.

That said, I'm having one issue that is going to drive me nuts.  I store all of my music on a remote windows server 2003, because my laptop severly lacks harddrive space.  Before, I distinctly remember being able to navigate to this remote folder and add these files to the library of any music program I chose to use.  Now however I cannot do this, and it's driving me nuts... in fact totem is the only one that will even play these files over the network, but it has no library at all.  

Does anyone have any suggestions at all?  I feel like I'm doing something wrong, and being as new as I am, probably am.

You are not doing anything wrong. You will need to install the smbfs package which allows you to mount network drives and folders as if they were local:

```
sudo apt-get install samba smbfs
```

After that is done see [this]("http://ubuntuguide.org/wiki/Dapper#How_to_mount_network_folders_on_boot-up.2C_and_allow_all_users_to_read"). Then you should be able to play your music files from the locally mounted network folder.

---

### Post by xxFelixDCatxx on 2006-08-13
okay so i followed the entire tutorial and i got this

cli_negprot: SMB signing is mandatory and we have disabled it.
10151: protocol negotiation failed
SMB connection failed

sooo... i'll have to check to make sure it didn't work, but I don't think that it worked.

---

### Post by xxFelixDCatxx on 2006-08-13
does the smbfs have to be installed on the remote computer?  it's a windows server 2k3 box... I don't think it does, so I must have screwed up somewhere.

---

### Post by klytu on 2006-08-14
> okay so i followed the entire tutorial and i got this

cli_negprot: SMB signing is mandatory and we have disabled it.
10151: protocol negotiation failed
SMB connection failed

> **xxFelixDCatxx said:**
> does the smbfs have to be installed on the remote computer?  it's a windows server 2k3 box... I don't think it does, so I must have screwed up somewhere.

This thread may help: [http://ubuntuforums.org/showthread.php?t=8479](http://ubuntuforums.org/showthread.php?t=8479)

Again, it doesn't appear you did anything wrong and no I don't think smbfs has to be installed on the remote computer. I don't use Windows Sever 2003 and I didn't know the set up steps I pointed you to would cause any problems. Read the whole thread above, and don't change anything on the remote box, except as a last resort. Following the solution in the thread (which mounts the share from the command line) you may have to modify /etc/fstab to mount the share as cifs instead of smbfs, if you want it to mount automatically boot-up. Note that the thread is from 2005, so if you are using Dapper or Breezy you don't want to modify your sources.list exactly as it is suggested there; in fact you probably don't need to touch that at all.

---

