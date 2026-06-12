---
title: "application for only one account"
date: 2007-01-27
forum: Absolute Beginner Talk
---

### Post by Oki on 2007-01-27
Hi

I have two accounts. Is it possible to install a program so it will only show up for one of them? Is it possible to hide one harddrive and/or a part ion for one of them?

As always thanks:-)

---

### Post by guysmiley25 on 2007-01-27
I'm not to sure what you mean.

When I only want a application to show up in the menu of one of my accounts what I do is goto 

```
/usr/share/applications/
```

Find the .desktop file and move it to ~/.local/share/applications

eg

```
sudo mv /usr/share/applications/XMMS.desktop ~/.local.share/applications
```

In the account you want to have the application.

Hope that helps.

PS I'm using xfce with edgy so I'm not sure if it will be the same for you.

---

### Post by max.diems on 2007-01-27
Use the source version to install to only one account. Only users with execute permissions in the install dir can use it. (Set it to 700 and only that user and root can use it)

---

