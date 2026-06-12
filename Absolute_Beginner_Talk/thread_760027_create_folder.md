---
title: "create folder"
date: 2008-04-19
forum: Absolute Beginner Talk
---

### Post by muldengold on 2008-04-19
Hi,

I want to create a public folder to which every user has read and write access to (e.g. for fotos, shared documents etc.). However, it seems not possible to do this outside my home folder. 

What can I do?

Thanks!

---

### Post by quirks on 2008-04-19
1. Open a terminal: go to Applications -> Accessories -> Terminal.
2. Enter this command:
```
gksu nautilus
```
3. Create a folder.
4. Right-click it and select **Properties**. Switch to the **Permissions **tab and give permissions to whomever you want.

Now you have a file browser with superuser privileges. You can create folders wherever you want.
**But be careful! You can do a lot of harm to your system, if you don't know what you are doing!**

---

### Post by Oldsoldier2003 on 2008-04-19
> **muldengold said:**
> Hi,

I want to create a public folder to which every user has read and write access to (e.g. for fotos, shared documents etc.). However, it seems not possible to do this outside my home folder. 

What can I do?

Thanks!
create a group for users you would like to have shared access. then
```
sudo mkdir /publicfolder
sudo chown <yourusername>:<usergroupforsharing> /publicfolder
chmod 777 /publicfolder
```
then add the all of your users to the group

---

### Post by muldengold on 2008-04-19
Thanks for the quick reply. I was able to create the folders and gave me and others permission to write and read files. However, if I go to the folder (outside nautilus) I cannot create any subfolders etc. although I should have permission to do so, or shouldn't I? Where am I wrong?
Thanks again!

---

### Post by Oldsoldier2003 on 2008-04-19
> **muldengold said:**
> Thanks for the quick reply. I was able to create the folders and gave me and others permission to write and read files. However, if I go to the folder (outside nautilus) I cannot create any subfolders etc. although I should have permission to do so, or shouldn't I? Where am I wrong?
Thanks again!

it depends on what you set as the ownership and permissons of the folder. If you own the folder and have write permissions you should be able to add a subfolder. If you are in the owning group  and have write permissions then you should be able to create a subfolder.
please show us the permissions of the share folder and the result of
```

id <yourusername>
```

---

### Post by muldengold on 2008-04-19
that's what I got back. It adds a bit to my confussion, I'm afraid:
uid=1000(sandro) gid=1000(sandro) Gruppen=1000(sandro),4(adm),20(dialout),24(cdrom),25(floppy),29(audio),30(dip),44(video),46(plugdev),104(scanner),108(lpadmin),110(admin),115(netdev),117(powerdev),119(sambashare)

---

### Post by quirks on 2008-04-19
Can you also post the permissions of the directory you created?
```
ls -ld /full/path/to/directory
```

---

### Post by muldengold on 2008-04-19
Thanks quirks and oldsoldier, it works now. What exactly is nautilus? I'll find out.
thanks again.

---

### Post by Oldsoldier2003 on 2008-04-19
> **muldengold said:**
> Thanks quirks and oldsoldier, it works now. What exactly is nautilus? I'll find out.
thanks again.

Nautilus is the gui file manager that comes with Ubuntu

---

### Post by quirks on 2008-04-19
Nautilus is the file browser in Gnome. It's the application that appears when you go to Places -> Home Folder, for example.

---

