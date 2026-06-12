---
title: "How to access Windows shares with Xubuntu"
date: 2008-01-22
forum: Absolute Beginner Talk
---

### Post by pthomas on 2008-01-22
I just finished installing Xubuntu but it doesn't seem to come with any method of browsing and accessing shares on a Windows network. So I guess I have to add that on, right? Now, as I understand it, I shouldn't need Samba just to access shares, I only need smbfs. How do I tell if I have that? Also, I looked for some kind of Windows network share browser in the supported packages under Add/Remove Applications and didn't find anything. Is browsing windows shares not supported under Xubuntu? What do I need to do to make this work?
PT

---

### Post by CheShA on 2008-01-22
In nautilus (the file browser) , from the "Go" menu, you can choose either "network" to browse visible shares (but this depends on correct Guest config on your Windows server, you might find that none show up) or you can choose "location" to manually enter a share to navigate to in the format:
```

smb://server/share
```
You'll then get prompted to enter a username / password

---

### Post by CheShA on 2008-01-22
...And what you "need" is smbclient, not smbfs; smbclient should be installed by default, smbfs maybe not.  smbfs allows you to mount an SMB share into your local file system.  Handy, but a bit more advanced that you're looking for!

you can check if you have either installed using something  like this:

```
dpkg --list | grep smbclient
```

One caveat is that you can't really play / stream media from an SMB share as is without copying it locally.  The best way to go about doing something like this is to install smb4k
```

sudo apt-get install smb4k
```

which will install a useful GUI program which will help you manage shares. Any shares you make in smb4k will allow you to play  media straight off the share.

---

### Post by CheShA on 2008-01-22
OOPS ! 

xubuntu! I should read properly

Sorry, you dont have nautilus but there should be something *very* similar in whichever file browser xubuntu does use... It's been a while since i used Xfce so I can;t rememebr off the top of my head. I'll just have a quick check and get back to you.

Installing smb4k will install some KDE libs so if you're using xubuntu because you're using a low end PC you might find that smb4k runs quite slow.  It should still solve your problem nicely either way.

Edit: Yup, just checked and you certainly do have "Go > Open Location" in XFCE.

---

### Post by pthomas on 2008-01-22
> **CheShA said:**
> In nautilus (the file browser) , from the "Go" menu, you can choose either "network" to browse visible shares (but this depends on correct Guest config on your Windows server, you might find that none show up) or you can choose "location" to manually enter a share to navigate to in the format:
```

smb://server/share
```
You'll then get prompted to enter a username / password

Thanks, but Xubuntu doesn't have Nautilus and it doesn't seem to be in the supported packages list. Is that required? Xubuntu has Thunar. Will that work?

---

### Post by zatlite on 2008-01-22
[http://ubuntuforums.org/showthread.php?t=304131&highlight=Thunar+Native+Windows+Network+Browsing](http://ubuntuforums.org/showthread.php?t=304131&highlight=Thunar+Native+Windows+Network+Browsing)

This is what I found.

---

### Post by CheShA on 2008-01-22
> 
Thanks, but Xubuntu doesn't have Nautilus and it doesn't seem to be in the supported packages list. Is that required? Xubuntu has Thunar. Will that work?

Yup, I noticed my mistake. and left another couple of posts... read on ;)

---

