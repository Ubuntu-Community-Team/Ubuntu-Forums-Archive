---
title: "Accessing Windows Shares"
date: 2007-06-25
forum: Absolute Beginner Talk
---

### Post by kspn on 2007-06-25
I am having some issues with accessing the shares on my Windows Box.

I can access my Xubuntu box from my Windows Box but I haven't been able to locate the app to allow me the access the windows shares.

Any ideas anyone?
:popcorn:

---

### Post by vexorian on 2007-06-25
you probably already have it, sometimes windows' firewall prevents a computer from being listed when browsing the netword.

On nautilus I did smb://computername/sharedfoldername and it worked, I doubt the same wouldn't work if you used it in the Xcfe filebrowser.

---

### Post by kspn on 2007-06-25
Thanks for the Reply.

I am running Windows 2000 so Firewall is not an issue, the question I have is more on the 'How do I browse the network'

I saw the smb:// item but couldn't work out where to execute it.

Is that from the Terminal or from the web browser or ??? (and is there an app/task I need to install to get it working)

---

### Post by vexorian on 2007-06-25
hmm try running "xfsamba4"

---

### Post by bucktron on 2007-06-25
I've recently accessed a windows share from ubuntu. I set up samba according to this how-to : [http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605). But when trying to browse the windows network i had set up from the menu Places->Network menu it wouldn't show me the windows share. Even when typing smb://windowscomputername/sharename into the Nautilius file browser. So I had to mount it using this command: > mount -t smbfs -o username=windows_user_name,password=windows_password //Server_name/share /mount_point Changing the details to mine of course. And I can now browse my windows share.

---

### Post by kspn on 2007-06-25
I had to install smbfs (I don't know why it wasn't there already!!!!!)

---

### Post by kspn on 2007-06-26
I finally workedout all the bugs :-s

I had to define the Username in a Credentials file, as well as the uid of my user so that I had write access but in the end I was able to get the shares working from in the fstab file

```
//%WindowsPC%/%ShareName% /home/shares/%WindowsPC%/%ShareName% smbfs uid=kspn,credentials=/etc/credfile,rw 0 0
```

---

