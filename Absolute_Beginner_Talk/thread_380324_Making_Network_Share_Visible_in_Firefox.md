---
title: "Making Network Share Visible in Firefox ???"
date: 2007-03-09
forum: Absolute Beginner Talk
---

### Post by herbster on 2007-03-09
I have 2 XP networked computers on my home network, and I can see them and print to them and everything perfectly, so I did Place>Connect to Server and mounted 2 networked shares and they're on my desktop so it's all good.

But I want to be able to go into Firefox and right click>Save link as, and save a file directly onto the networked shares. What I did was, when the Save to Disk dialog box with the left bookmark menu and the drives and folders came up, I dragged one share onto the left side of the menu and nothing showed up. Then I dragged it again and a warning said "Bookmark already exists." I have closed and reopened Firefox, still can't see it there! Any ideas?? :(

Edit: I just opened Gxine player and the shares are visible on the left menu just fine.. it seems only Firefox is not cooperating?!?!

---

### Post by kelbizzle on 2007-03-10
so when you right click on a link. and click "save link as" Your network share doesn't show in the save in folder drop down? thats what I think I understand. I just checked mine and I'm able to see my network shares. Although I don't use the connect to server method. The method I use has been with sambafs.  

Assuming your computers name is "skooter" and the share is called "music"
Install smbfs
```
sudo apt-get install smbfs
```
This is where it will be mounted when were through
```
sudo mkdir /media/music
```
backing up is good
```
sudo cp /etc/fstab /etc/fstab_backup
```
editing and saving your fstab
```
gksudo gedit /etc/fstab
```
copy this line to your fstab changing the names you need to
```
//skooter/music /media/music smbfs username=guest,password=,uid=1000,isocharset=utf8,codepage=unicode  0  0
```

You can restart or ```
sudo mount -a 
``` to remount the fstab. I think a restart is needed so it will show on the desktop though.

EDIT: I just tried the connect to server way. and the little folder with smb on it shows in the save link as dialog box. Idk if thats due to me having smbfs installed. after clicking save it tried to mount the share and complained that only root can mount it whereever.  But the other way works fine for me.

---

### Post by herbster on 2007-03-13
> **kelbizzle said:**
> ```
//skooter/music /media/music smbfs username=guest,password=,uid=1000,isocharset=utf8,codepage=unicode  0  0
```

Hey man, thanks so much for your help. I am stuck at this line, though. I don't know what to change or what to change it to even.

/skooter/music    is skooter my username? Like my home is home/bobby. So should that be /bobby/music?

And what is the username and password, is that for Ubuntu when I login or for the share I am mounting (the Windows XP login on that PC??)

Thanks !!

---

### Post by kelbizzle on 2007-03-16
> **herbster said:**
> Hey man, thanks so much for your help. I am stuck at this line, though. I don't know what to change or what to change it to even.

/skooter/music    is skooter my username? Like my home is home/bobby. So should that be /bobby/music?

And what is the username and password, is that for Ubuntu when I login or for the share I am mounting (the Windows XP login on that PC??)

Thanks !!

Sorry about that. Skooter is the name of the computer on the network. Music is the name of the share. If the name of your xp machine is herbster and the share name is music.  Just change the first part to //herbster/music. and the reason I mount it at /media/music is so it will show up like removable media.
```
//herbster/music /media/music smbfs username=guest,password=,uid=1000,isocharset=utf8,codepage=unicode  0  0
```

I don't use a password on the local network for the xp machine.  You won't have to change anything but the name of your xp machine and share and the place you made a directory to mount it.

---

### Post by herbster on 2007-03-17
> **kelbizzle said:**
> Sorry about that. Skooter is the name of the computer on the network. Music is the name of the share. If the name of your xp machine is herbster and the share name is music.  Just change the first part to //herbster/music. and the reason I mount it at /media/music is so it will show up like removable media.
```
//herbster/music /media/music smbfs username=guest,password=,uid=1000,isocharset=utf8,codepage=unicode  0  0
```

I don't use a password on the local network for the xp machine.  You won't have to change anything but the name of your xp machine and share and the place you made a directory to mount it.

Okay, I'm not sure what my XP computer's name is, I'm guessing it's the name I see when I click Network Servers > Windows Network > MSHOME and it's there, it's called JAYPC. So I put //jaypc, and as for the share name, the share is "JAY C DRIVE," so I put "//jaypc/jay  c drive" and then the rest of the line. I did sudo mount -a and it gave me this:

```
bobby@bobby-ubuntu:/media$ sudo mount -a
Password:
[mntent]: line 18 in /etc/fstab is bad
```

So I must've gotten something wrong, hehe. Here's what I put in the fstab:

```
//jaypc/jay c drive /media/jaypc smbfs username=guest,password=,uid=1000,isocharset=utf8,codepage=unicode  0  0
```

I'm sure it's wrong, lol...

---

### Post by herbster on 2007-03-19
bump

---

