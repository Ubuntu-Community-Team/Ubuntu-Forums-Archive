---
title: "Hellanzb download permissions"
date: 2008-02-28
forum: Absolute Beginner Talk
---

### Post by cysco24 on 2008-02-28
I finally got hellanzb to work.  Had a problem with permissions to the created folders.  Now i have chown them and everything seemed to work. Now every download that gets unrar into my done folder is also locked and i need to chown that one just to move the files or delete them after i'm done.  I'm sure there is something i'm doing wrong, please help.

Thx

---

### Post by kellemes on 2008-02-28
> **cysco24 said:**
> I finally got hellanzb to work.  Had a problem with permissions to the created folders.  Now i have chown them and everything seemed to work. Now every download that gets unrar into my done folder is also locked and i need to chown that one just to move the files or delete them after i'm done.  I'm sure there is something i'm doing wrong, please help.

Thx

Never used hellanzb myself..
Do you start it as root? Or as a normal user?
When starting as root it will create these folders with root-permissions, I assume.

---

### Post by cysco24 on 2008-02-28
sudo hellanzb

that's how I start it.  When it was first run it created the folders for it to use with root permissions.  I then changed those permissions but when something new is downloaded it sets the root permissions only on the new folder it created (the download)

---

### Post by cysco24 on 2008-03-07
Saw this on another post.  Finally working.

Open terminal and type hellanzb without sudo
You might get an error that you don't have permission to a folder.

Navigate to that folder directory and use the sudo chown -R username:username folder/

repeat in terminal without the sudo command "hellanzb"
until hellanzb runs.

Now all the downloads are owned by me.  :)

---

