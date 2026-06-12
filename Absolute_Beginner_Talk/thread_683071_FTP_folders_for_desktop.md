---
title: "FTP folders for desktop?"
date: 2008-01-30
forum: Absolute Beginner Talk
---

### Post by inverseroom on 2008-01-30
I haven't been able to figure this out in Gutsy...perhaps somebody could help me.  In XP, I used to be able to make folders that I could put on my desktop connected to various subfolders on my FTP.  This way I could upload, say, photos to my online photo folder by just opening up the folder and dragging the pictures in.

What's this even called in Ubuntu?  Actually I can't remember what it was called in XP, either.

Also...in XP, once those folders were open, I could never see the photos as thumbnails--just large icons.  Will Gutsy let me view thumbnails remotely in a folder?

Thanks all!  Couldn't find this with a search...

---

### Post by oldos2er on 2008-01-30
Nautilus' FTP will place folders on your desktop. Go to Places, Connect to Server.

---

### Post by inverseroom on 2008-01-30
I did indeed find that function...but I could only get it to open up the destination folder for me to move things in and out of.  How do you get it to make a permanent desktop folder, then attach the FTP location to it?

---

### Post by jordanmthomas on 2008-01-30
```
sudo apt-get install curlftpfs
sudo ln -s /usr/bin/curlftpfs /sbin/mount.curlftpfs #lets mount work properly
```
Then, make a folder on your desktop called ftp (or whatever you want, just remember what you name it)
```
mkdir [COLOR="Red"]/path/to/mountpoint[/COLOR]
```

Add this to your /etc/fstab
```
ftpusername:ftppassword@ftp.site.address [COLOR="Red"]/path/to/mountpoint[/COLOR] curlftpfs rw,allow_other,uid=userid,gid=groupid 0 0
```

```
sudo chgrp fuse [COLOR="Red"]/path/to/mountpoint[/COLOR]
sudo chmod g+w [COLOR="Red"]/path/to/mountpoint[/COLOR]
sudo addgroup username fuse #make sure you're in the fuse group
```

Now, mount it
```
sudo mount -a
```
You should now have a permanent folder at [COLOR="Red"]/path/to/mountpoint[/COLOR] that contains your ftp server that you can use as a local disk.

---

### Post by inverseroom on 2008-01-30
Excellent, thanks a lot!  Forgive me though, my Linux chops are exactly three days old...how do I make sure I'm in the fuse group?  I'm afraid I don't even know what that is.

EDIT: oh wait, I see, that code is in fact PUTTING ME IN the fuse group.  Thanks...

---

### Post by jordanmthomas on 2008-01-30
To check, you can type
```
groups
```
And if fuse shows up, you're in!
If not, you can type this:
```
sudo addgroup $USER fuse
```
To add the user who ran the command to the fuse group.  ($USER automatically fills out and becomes your user name.)

Fuse is a system that allows you to mount cool things as filesystems in Linux.  ssh, ftp, windows shares, etc, can all act as local disks and become a "part of your system".


edit
Also, kudos to you for asking when you're not sure of something instead of just blindly copying and pasting.

---

### Post by inverseroom on 2008-01-30
OK, everything went fine until I tried mounting, and the terminal read:

```
fuse: invalid parameter in option `uid=userid'
```

---

### Post by jordanmthomas on 2008-01-30
you can either remove the uid=userid option from the list in /etc/fstab or you can put in you userid 
```
echo $UID
``` will give you your uid, which you should put in instead of "userid"
This also works for your groupid, 
```
echo $GID
```
For me (not on Ubuntu, so it may be different numbers for you), my line would look like
```
ftpusername:ftppassword@ftp.site.address /path/to/mountpoint curlftpfs rw,allow_other,uid=1000,gid=100 0 0
```

Sorry for not pointing that out earlier.  It's my fault, really.  :)

---

### Post by inverseroom on 2008-01-30
Great, that worked!  Sorry, I didn't realize those were fields.  I ended up just eliminating the groupid field, since the echo didn't result in anything.

I appreciate your help with this...it's always useful to hone my chops in shellville.

---

### Post by inverseroom on 2008-01-30
And one more thing...unlike in Windows XP, the icons actually display as thumbnails.  FANTASTIC.

---

### Post by jordanmthomas on 2008-01-30
Awesome, glad it worked out for you.

---

