---
title: "How do I network with macbook using Edgy"
date: 2007-04-12
forum: Absolute Beginner Talk
---

### Post by niallcd on 2007-04-12
I have tried to read guides on the subject and figure it out on my lonesome but to no avail.

I Have been trying to connect to my mac book using Edgy and not gotten anywhere. I have tried to configure things in my shared folders tab and created what I assume is a root folder "/" and a folder that reads /home/niall.

Under the General Properties tab it said Mshome. It no longer says this.

On the mac book end however its a little different.

The mac sees my computer however when I try to connect I get " The alias "Kronos" could not be opened, because the original item cannot be found. 

Then it gives these options:  

"Delete the Alias" (which if I choose will not let me delete because I do not have sufficient privileges to delete "Kronos" 

"Fix Alias" which does nothing

"OK" which does nothing

I'm up a creek here. Any help would be welcome.

---

### Post by dstew on 2007-04-13
Are you trying to share files on Edgy with your Macbook? That is, you want to sit at your Macbook, and open a directory that is on your Edgy system, correct?

If that is the case you need to do three things. First, enstall the Samba system:

```
sudo apt-get install samba smbfs
```

Second, you have to select a folder to share using Samba. For example, to create a shared folder on your desktop, right-click and select Create Folder. Name it Shared if you like. Then, right-click the folder you just created, select Share Folder, select Share Through Windows Network (SMB), then give it a name (can use Shared again).

Last, you have to enable Windows sharing on your Macbook. Go to System Preferences --> Sharing, and activate Windows Sharing.

Have you done these things? Or do you want to do something more complicated?

---

