---
title: "How Do I Create a ShortCut?"
date: 2007-04-05
forum: Absolute Beginner Talk
---

### Post by kc5hwb on 2007-04-05
I want to create a shortcut from a secondary SATA drive folder to put on the desktop.  When I right-click on that folder from the file browser, the "make link" option is grayed out.  If I drag it, it simply creates a new folder that isn't linked to the SATA drive.

---

### Post by mssever on 2007-04-05
There's a foolproof way to make symlinks from the command line.
```
ln -s /path/to/target destination
```

---

### Post by kc5hwb on 2007-04-05
That works perfectly, thanks.

How about creating a shortcut from a network share to put on the desktop?

---

### Post by mssever on 2007-04-05
> **kc5hwb said:**
> That works perfectly, thanks.

How about creating a shortcut from a network share to put on the desktop?

If your network share is listed in /etc/fstab, the same method works. If you used nautilus (the file browser) to connect to it, things are more difficult if the make link menu item is disabled.

One option is to list the network share in fstab. See [How to fstab]("http://ubuntuforums.org/showthread.php?t=283131") for details.

Another option is to create a .desktop file (analagous to a Windows shortcut):[LIST=1]
[*]Browse to the intended target of your .desktop file and hit Ctrl+L. Make note of the full path for later.
[*]Open up a text editor and create a file with a .desktop extension. The filename can be whatever; it won't be shown. (If you want to edit this file later, you'll have to use the terminal or some other trickery to open it. Stupidly, GNOME won't let you edit it directly.)
[*]Put the following into the file: ```
[Desktop Entry]
Version=1.0
Encoding=UTF-8
Name=Whatever you want to call it
Exec=nautilus /path/to/target/that/you/noted/earlier
Icon=gnome-fs-client
Terminal=false
StartupNotify=true
Type=Application
```
[*]Save and exit[/LIST]

---

### Post by kc5hwb on 2007-04-05
Wouldn't it be better to use fstab?  I think that I would rather do this and learn *how* to do it, but I read through that link you gave and don't quite understand it all.

Here is the last entry in my current fstab file:
> # /dev/sda5
UUID=bc9fd14a-eafb-44a8-93c7-1ba9edd4cc95 none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0

So I think, if I am reading this How-To correctly, that I should create an entry that says:
> server:/shared_directory /mnt/nfs nfs <options> 0 0

Is that all?

---

### Post by mssever on 2007-04-05
> **kc5hwb said:**
> Wouldn't it be better to use fstab?  I think that I would rather do this and learn *how* to do it, but I read through that link you gave and don't quite understand it all.

Here is the last entry in my current fstab file:


So I think, if I am reading this How-To correctly, that I should create an entry that says:


Is that all?
Yes, fstab is the method I prefer. Here's a line from my fstab for reference: ```
192.168.1.50:/home/scott/webmaster      /home/scott/webmaster   nfs     rw,hard,intr    0 0
```Remember, the mount point *must* exist, or mounting will fail.

Just insert your NFS line somewhere in your fstab, then do a ```
sudo mount -a
```By the way, if you type ```
man mount
``` you'll find a list of the possible mount options. man is short for manual, and you can put it before most commands and many config files for more info.

---

### Post by kc5hwb on 2007-04-05
I realize that I am probably making this more difficult than it needs to be, so thanks for the help.  But here is the tricky part...  I am running SAMBA, not NFS, because I am realistically on a windows network, even though the box I am trying to fstab to right now is another Ubuntu box.  And on that box, I have the shares setup under another username ID.  While you were typing your last reply, I found that thru Nautilus I could browse over the network to the folder I wanted to shortcut to, right-click on the folder and choose "connect to server" and this DID put the folder that I wanted on my local desktop.  However, since I am browsing as one username, not the one with full rights share permissions, it would only let me READ ONLY in the folder.

So....... if I setup the fstab file, it will need to connect to the network share as another username, yes?  Or should I simply go onto that machine and enable my same username as I have on this local box with full share permissions?  Someone once told me not to do that, but I don't remember why now.  :(

---

### Post by mssever on 2007-04-05
To make Samba work, you need to connect with the proper credentials. You can do this through fstab. First, you need to install smbfs if you haven't already. Then, use smbfs as the filesystem type in your fstab entry, and read man smbmount for the options you can set.

---

### Post by kc5hwb on 2007-04-05
I added this to the fstab file:
> 
# 10.10.10.86:/drives/Ydrive 
smbfs username=jsamba password=password  0  0
/home/jason/Desktop 


What now?

---

### Post by HereInOz on 2007-04-05
Also, if you want to mount the Samba shares on boot up using an entry in fstab, you will need to install smbfs using synaptic.  This is not installed as a default when you install Samba.

Here's how to mount a Samba share:

Mount Samba share using terminal:

sudo smbmount //server/share /path/to/mount/point -o username=samba_username,password=samba_password

To mount the share permanently: 

Add a line in /etc/fstab to make Samba mount permanent:

// server/share / path/to/mount/point smbfs auto,credentials=/root/.credentials,uid=1000,umask=000,user   0 0

Then create a file, using nano, or your favourite text editor, named:-   /root/.credentials    & containing the following text
username=your_samba_user_name 
password=your_samba_password

Make it readable only by root:
sudo chmod 600 /root/.credentials

---

### Post by kc5hwb on 2007-04-05
smbfs wasn't installed, so I installed it thru Synaptic.  I am going to try these steps now.

---

### Post by kc5hwb on 2007-04-05
I tried just doing it the one time and I get this error :

**Could not resolve mount point /drives/Ydrive**

---

### Post by mssever on 2007-04-05
> **kc5hwb said:**
> I tried just doing it the one time and I get this error :

**Could not resolve mount point /drives/Ydrive**

Does the directory /drives/Ydrive exist? Remember that Linux is case-sensitive.

---

### Post by kc5hwb on 2007-04-05
> **mssever said:**
> Does the directory /drives/Ydrive exist? Remember that Linux is case-sensitive.

Yes.  That is my mount point on the server.

---

### Post by mssever on 2007-04-05
> **kc5hwb said:**
> Yes.  That is my mount point on the server.

Your fstab line is looking for that path on the local machine, not the server. Perhaps you could post the appropriate fstab line.

By the way, it's best if you surround stuff like this in [code] tage when you post them, that way the formatting is preserved.

---

### Post by kc5hwb on 2007-04-05
This is what I have...

```
# 10.10.10.86:/drives/Ydrive 
smbfs username=jsamba password=password  0  0
/home/jason/Desktop
```

---

### Post by mssever on 2007-04-05
> **kc5hwb said:**
> This is what I have...

```
# 10.10.10.86:/drives/Ydrive 
smbfs username=jsamba password=password  0  0
/home/jason/Desktop
```
OK. Try this: ```
10.10.10.86:/drives/Ydrive /home/jason/Desktop smbfs username=jsamba password=password  0  0
```First, everything needs to be on a single line. Second, a # at the beginning of the line marks a comment. Not what you want if you want the line to do something. Third, your parameters are out of order. The mount point should be the second field. Finally, if you set your mount point to ~/Desktop, then anything that's currently on your desktop will become unavailable whenever your partition is mounted. Normally you want the mount point to be an empty directory.

---

### Post by kc5hwb on 2007-04-05
ok, done.  I created a folder on the desktop called "Shares"  And I added that to the fstab, all on 1 line, no # in the beginning.

I open up that folder and nothing is there.  Now that the fstab file is set, do I use the "make link" feature?

---

### Post by kc5hwb on 2007-04-05
I am still getting "could not resolve mount point"

---

### Post by mssever on 2007-04-05
Mounting sambfs is sonething I haven't done in a long while. It appears that I've told you wrong. See [this tutorial]("http://doc.gwos.org/index.php/HowToMountsmbfsSharesPermanently") for info.

Basically, it looks like you have to use Windows-style notation, not NFS-style. Here's the sample fstab entry from the link I'm giving you: ```
//servername/sharename /mountdirectory smbfs username=windowsuserename,password=windowspassword 0 0
```

---

### Post by kc5hwb on 2007-04-05
This is good info and I will need it later, but right now I am trying to mount another LINUX share, not a windows one.

I have 2 Ubuntu boxes and 4 windows boxes on my network.  I run them with SAMBA so they can all see each other, which they can...I can browse around in them now all I want to.  I am simply trying to put a shortcut on my Ubuntu Desktop that links to the share folders on my other Ubuntu machine.  Yes, they are both being shared with SAMBA, but no they are not windows shares.

---

### Post by mssever on 2007-04-05
Samba is a Windows protocol. If you don't need your stuff to be readable by Windows, than you're better off using NFS, because NFS supports Linux stuff like file permissions and the like.

Once I stopped using Windows altogether, I stopped using Samba, so I'm not all that competent in Samba. I've pretty much told you what I know. If it isn't enough to get you up and running, you might try searching a bit more.

The link that I gave you, though, is OS-agnostic. From the perspective of mounting Samba shares, it makes no difference whether the server is a Windows computer or a Linux machine running Samba.

---

### Post by kc5hwb on 2007-04-06
I am running windows machines also.

I tried running this thru Terminal and I got the error "invalid share"  I tried connecting to a Linux box and also to a Windows box, and got the same error.

```
//servername/sharename /mountdirectory smbfs username=windowsuserename,password=windowspassword 0 0
```

---

### Post by mssever on 2007-04-06
Hmm... as I said earlier, I've pretty much gone to the extent of my Samba knowledge. Perhaps starting a thread specifically on Samba would catch the attention of someone more knowledgable on this than I.

---

### Post by kc5hwb on 2007-04-06
Thanks for all your help.  I learned several things from your instructions.

---

