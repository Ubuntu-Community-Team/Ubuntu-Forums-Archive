---
title: "Howto best use folder permission for applications needs?"
date: 2007-01-11
forum: Absolute Beginner Talk
---

### Post by shareMenaPeace on 2007-01-11
Hello,
some applications needs extra folder permission to work (create files mostly).
Example applications azureus, nautilus ftp, only can save files once i set permission for the disired folder to group "create and delete".

I do this rather complicated with Alt F2 and than gksudo nautilus to have rights to set permission.

Is there another better way todo this?


Thx

---

### Post by taurus on 2007-01-11
Why don't you save all your downloads to your own $HOME directory?  Then, you don't need any other special permission.  Create a directory called download and save everything in there.

Applications -> Accessories -> Terminal
```
mkdir ~/download
```

---

### Post by shareMenaPeace on 2007-01-11
Thank you, so i assume the folder has teh right permission when under the home.
Ok thx, and yes i use this space for special content.

But i prefer to save i.e. incoming or libery files on a special partition.

Question what is the command for setting folder rights?

thx

ps.
I go and by a linux book soon! :p

---

### Post by taurus on 2007-01-11
You can save whatever you want to your own $HOME directory because it's yours.  But if you want to say save stuff to /opt/share, then you need to change the owner of that directory to your username and set the right permissions to it.

```
sudo mkdir /opt/share
sudo chown **shareMenaPeace**:**shareMenaPeace** /opt/share
sudo chmod 755 /opt/share
(assuming **shareMenaPeace** is your login name...)
```

---

### Post by shareMenaPeace on 2007-01-11
Hej thanks very cool just applied the settings!

---

