---
title: "Mounting Windows Share with Spaces in Name..."
date: 2007-06-25
forum: Absolute Beginner Talk
---

### Post by ResumeMan on 2007-06-25
...or at least I think that's the problem

Hi all,

First post, total Linux noob here. Been playing around with Ubuntu for a couple weeks, and have gotten most of what I need from these forums, the [Ubuntu Guide]("http://ubuntuguide.org/wiki/Ubuntu:Feisty"), and the *Beginning Linux* book by Keir Thomas.

I'm running up against one wall though, and I'm not finding what I need in search.

I'm running Ubuntu on a laptop, which is connected to a Windows network. I very much want to mount three folders from the network on my file tree. Their names in the Windows network are: 

LACIE (F) -- This is an external HD which is the F: drive on the Windows computer
SharedDocs
SharedDocs/Incoming Tunes

If it matters, these are all part of the network called "Villa". The windows computer's IP is //192.168.1.5/

So I attempted to follow the procedures outlined [here]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_mount_network_folders_on_boot-up.2C_and_allow_all_users_to_read") . The windows computer doesn't have any particular permissions assigned to it, so in the /root/.smbcredentials file I put my Ubuntu username and password.

I created the following drives using mkdir:

/media/dell/F
/media/dell/shared_docs
/media/dell/incoming_tunes

So following the procedures, when I entered 

> //192.168.1.5/SharedDocs   /media/dell/shared_docs  smbfs  credentials=/root/.smbcredentials    0    0

in /etc/fstab and rebooted, all seems to be well. I've got the shared_docs folder both on my desktop and my file tree.

But the same process didn't work for the other two folders. I imagine this has to do with the spaces in their names (though I'm not sure). But I tried modifying them using quotes:

> //192.168.1.5/"LACIE(F)" /media/dell/F  smbfs  credentials=/root/.smbcredentials    0    0
//192.168.1.5/SharedDocs/"Incoming Tunes"   /media/dell/incoming_tunes  smbfs  credentials=/root/.smbcredentials    0    0

But that didn't work either (is that even close to right???). I also tried it without the quotes but with underscores for the spaces.

Now, for kicks, I also tried the approach featured [here]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_mount.2Funmount_network_folders_manually.2C_and_allow_all_users_to_read"), and entered into the terminal:

> sudo mount //192.168.1.5/"LACIE (F)" /media/dell/F

And lo and behold, it worked!! The F drive was available on the desktop and in the tree. Of course, when I rebooted it went away :(

I sat down at the Windows computer and tried to change the names of the folders, but in the "Share Name" field under "Properties" it wouldn't take the edits.

So...any suggestions? Am I missing something basic here???

Thanks in advance for your advice!!

---

### Post by kspn on 2007-06-25
If you have a space in the name you can use the Backslash Character to get around it,
```

//192.168.1.5/SharedDocs/Incoming\ Tunes /media/dell/incoming_tunes smbfs credentials=/root/.smbcredentials 0 0
//192.168.1.5/LACIE\ (F) /media/dell/F smbfs credentials=/root/.smbcredentials 0 0

```

That may work for you.

---

### Post by atria on 2007-06-25
Adding quotes should work too.
For example sudo mount "\\192.168.x.x\sharename" as opposed to \\192.168.x.x\"sharename"

---

### Post by kspn on 2007-06-25
> **atria said:**
> Adding quotes should work too.
For example sudo mount "\\192.168.x.x\sharename" as opposed to \\192.168.x.x\"sharename"

Would that work in the **fstab** file?:?:

---

### Post by ResumeMan on 2007-06-25
Wow, thanks for the quick replies! This forum does move amazingly fast.

Unfortunately, neither of those suggestions worked :( From what I can tell it certainly seems like they should have, but no luck

But I did a little more Googling relative to the Windows side of things. I found out that in Windows I can select the properties of my shared folder, un-select the share option, accept that, then go back and select share and can then input a new (space-less) name.

So that's what I did, and it seems to have worked fine. Kind of a lame fix, but it did work! (more reasons to think that Linux is a better solution than Windows :) )

---

