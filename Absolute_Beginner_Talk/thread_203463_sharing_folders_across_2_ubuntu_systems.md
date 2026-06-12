---
title: "sharing folders across 2 ubuntu systems"
date: 2006-06-25
forum: Absolute Beginner Talk
---

### Post by kgee on 2006-06-25
How would I go about sharing a folder across 2 systems?

So far i've made a folder, clicked on the "share folder" option, picked samba (sp?) as a way of sharing, given it a title and description, and selected "allow browsing folder".

So I'm pretty sure the folder is set up to be shared, now how do I get to it from the other box?

The computer sharing is running dapper and the other is running breezy until I get around to updating.

I'm pretty sure its not a complicated question, and any help would be appreciated.

Thank you.

---

### Post by dlai on 2006-06-25
Places --> Network Servers --> Windows Network --> The other computer --> Shared Folder

---

### Post by kgee on 2006-06-25
hmm, when I go to "network servers" it asks me for 3 different logins, only one of which I know how to get into (I know all the system passwords, but two of the logins dont accept anything) when I click cancel, it shows me the windows network, but there is nothing in there. Do I have to configure the computers for the network? how would I do it?

---

### Post by kgee on 2006-06-25
hmm, I can get to everything using this method on the dapper computer but not the  breezy.

---

### Post by AndyCooll on 2006-06-25
Linux to Linux you can use Samba but NFS is easier and might be enough.

sudo apt-get install nfs-common (and nfs-kernel-server on the box you have the share)

Here are a couple of links you might find useful:
[URL="https://help.ubuntu.com/community/SettingUpSamba"]Setting up Samba
[/URL]
[Setting up NFS]("https://help.ubuntu.com/community/SettingUpNFSHowTo")

:cool:.

---

