---
title: "Virtual Box Folder shared issues"
date: 2007-05-30
forum: Absolute Beginner Talk
---

### Post by elpichi on 2007-05-30
alright i had this problem for some time now, i have windows xp as guest inside ubuntu with virtual box, but the only problem i had so far is that i cannot copy massive numbers of files at a time from the shared folder that i make. to import files from the host(ubuntu) to the guest(windows xp)

i heard this was a bug, but is there any way to circumvent this problem? another way to transfer files without windows crashing with the blue screen of death?

edit: on the guest i'm using the NET command on DOS command prompt to set a drive for the shared folder

---

### Post by yabbadabbadont on 2007-05-30
I can't help with the details, but you might try installing Samba on the host and creating a share that can then be accessed from XP.  You would have to enable and configure networking in virtualbox though.

---

### Post by elpichi on 2007-05-30
alright i'll try that thanks

---

### Post by hoheszeh on 2007-05-30
> **elpichi said:**
> alright i had this problem for some time now, i have windows xp as guest inside ubuntu with virtual box, but the only problem i had so far is that i cannot copy massive numbers of files at a time from the shared folder that i make. to import files from the host(ubuntu) to the guest(windows xp)

i heard this was a bug, but is there any way to circumvent this problem? another way to transfer files without windows crashing with the blue screen of death?

edit: on the guest i'm using the NET command on DOS command prompt to set a drive for the shared folder

Have you installed the "Virtual Box Additions" ("Devices"->"Install Guest Additions")? I tried quite some time to get the "shared folders" up and running before i installed them. No way. After the installation it was easy and works even without network connection!

---

