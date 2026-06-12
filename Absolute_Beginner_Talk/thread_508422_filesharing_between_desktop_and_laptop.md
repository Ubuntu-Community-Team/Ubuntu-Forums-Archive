---
title: "filesharing between desktop and laptop"
date: 2007-07-24
forum: Absolute Beginner Talk
---

### Post by calymea on 2007-07-24
Hi, I have a desktop and a laptop (this one) and I want to share the files on the desktop with the l/top. Could someone tell me what I have to do? I know nothing about sharing between Windows and Linux,so please make it as easy to understand as possible. Thanks everyone.

---

### Post by einversuchisteswert on 2007-07-24
Hi,

well you can use this one (in konqueror):

smb://WinMachineIp/yourfolder

example:

smb://192.168.0.2/shares

but it must be a shared folder.

In Nautilus is an option to connect to Winfolders (File->Connect to Server->then you can choose the Windows Share), search a bit.

I hope it works ;)

---

### Post by bernied on 2007-07-24
You have not said which machine is windows, and which is linux.

[This](https://help.ubuntu.com/7.04/user-guide/C/gosnautilus-515.html) or [this](https://help.ubuntu.com/community/MountWindowsSharesPermanently) might help if the desktop is windows.

[This](https://help.ubuntu.com/community/SettingUpSamba?highlight=%28samba%29) might help if the desktop is linux and you want to share files from it.

What is it that you want to do?

---

### Post by calymea on 2007-07-24
hi, the desktop is windows and the l/top is linux (Ubuntu). I want to share files on the desktop with the l/top.
Thanks Bernied.

---

### Post by bernied on 2007-07-24
It's not so hard - just use Nautilus, unless you want permanent access, in which case use that second link in my last post.

---

### Post by Zeronine on 2007-07-24
I have a similar question, so I thought I would add mine to this thread rather than start a new one and clutter up the forum.

My situation is slightly different, I have a desktop which dual boots XP and Ubuntu Feisty.  The machine is on a wired ethernet connection to a Linksys wireless router.  The windows OS is set up to share a couple folders and one drive partition with a laptop that is XP only, and on a wireless connection.

I want to be able to share a folder on the Linux desktop, as well as access the windows shared folders (if possible) when I have Ubuntu running.

So far, I have ensured that Samba is installed, and have taken the step to make sure they are on the same workgroup name (pardon my ignorance if that's a unnecessary step).  

I don't necessarily want to setup my linux distro to be a "server" but simply be able to transfer files back and forth.  From what I read at the link posted in one of the posts above, it seems like samba may not be necessary, is this true?

So far I can't see either computer over the network from either machine.  In Ubuntu, if I use the gui network viewer, I can see that the network is detected (lets say for this discussion that it's named "PIPELINE"), abut double clicking on it has no result.  There's another one listed though, named "mshome", and it appears my linux shared folder is listed there.

I'm just now attempting to learn this linux thing (hoping to convert over entirely), so please pardon my breathtaking ignorance about this issue.

---

### Post by calymea on 2007-07-25
Hi, could you detail a bit more about using Nautilus for file sharing between the two computers. Like I said I know nothing about file sharing. Thanks again.

---

### Post by bernied on 2007-07-25
[This page](https://help.ubuntu.com/7.04/user-guide/C/gosnautilus-515.html) explains it much better than I could.

---

### Post by bernied on 2007-07-25
Zeronine, if I understand your question properly, then you want to do something like this (read it all before trying any of it, this is quite sketchy):

- check to see what you already have mounted - try the command 'mount', or navigate about in the /media and /mnt folders with Nautilus. Some of the following might already have been done during your install.

- create some mountpoints (empty directories), say you want one for the partition that you share, and one for each of the other shared folders. You also want one for the partition that contains those shares (I'm assuming that's the main Windows partition - the C: drive?).
```
sudo su
cd /media
mkdir share
mkdir windowsC
mkdir share/store
mkdir share/pics
mkdir share/vids
```(you should change those names to something meaningful)

- edit /etc/fstab ('gksu gedit /etc/fstab'), create lines for each of the shares that you want to access. To do this you will need to know something about the format of the filesystems and where they are located, according to linux. The location will be something like /dev/sda1 (the first partition on the first drive) or /dev/sdb3 (the third partition on the second drive). You can get this information possibly from gparted (should be in your menu somewhere). The format will probably be NTFS, the standard Windows format, or they may just possibly be FAT32 or FAT16 (linux would call this vfat). You might want to do a bit of research on mounting NTFS partitions, it is fairly new in linux because it is a proprietary microsoft format, and this is not something I am familiar with.  Anyway, your new lines would look something like this (any line starting with # is a comment):
```
# your windows C drive, probably at /dev/sda1
/dev/sda1 /media/windowsC ntfs rw,auto 0 0
# the partition that you share
/dev/sdb1 /media/share/store ntfs rw,auto 0 0
#the folders in the windows C: drive that you want to share
/media/windowsC/Documents\ and\ Settings/My\ Documents/My\ Pictures /share/pics none bind,auto 0 0
/media/windowsC/Documents\ and\ Settings/My\ Documents/My\ Videos /share/vids none bind,auto 0 0
```(this example is for two ntfs file systems and it will probably not work without some modification. You will probably need to add some more options to the lines that mount the two ntfs partitions, you need to research on this, because I don't know what you need. Start with 'man fstab' for how this file works, but this will probably not have the information about ntfs that you need, try google for that)

- check that the shares mount properly. All of the folders should end up on /media/share and all the important windows stuff should not be in that location, it will be at /media/windowsC
```
sudo mount -a
```then navigate to /media/share and see if you can find your stuff. Also see if you can read and write files at this point. 

Don't continue until you can access everything from your ubuntu box.

Once you've got the folders working properly, then you can move on to sharing them. For this, you will need samba, and it will be acting as a server. There is a samba admin tool in kde, or you can use swat (samba web administration tool).

Google is your friend.

---

### Post by buntunub on 2007-07-25
Samba was and always has been for me, the devil! I finally got Samba working smoothly only after I created user and smbpasswd accounts on all my machines that matches, including passwords. After I did that, it has worked like a champ ever since, although its very slow. I found another, much better solution however. Its called sshfs. There is a guide on the ubuntu wiki  that clearly details how to set that up. Your server(s) will need to have the sshd daemon installed and running, which for me took all of about 30 seconds to setup. I struggled with the fstab entries but it was my error for not reading the guide properly. Anyway, all my secure shares mount up almost instantly, and file sharing happens almost as if it was on the same machine. Movies from one machine play as if they were on my lappy, etc. Responsiveness is unreal and the fact that its over an ssh means its encrypted and secure (use shared rsa keys). BTW, you CAN do that as well between linux to windows and vica versa.

Edit: Forgot to mention that my setup includes a BCM Wifi lappy, WPA2 encrypted, and 3 file servers (Xubuntu ,Sabayon, and XP  machines), all of which have sshfs mounts setup and fully functioning 2-way.

---

### Post by bernied on 2007-07-25
I agree with buntunub, sshfs is probably easier to setup than samba.

On a windows machine, you can use something like [WinSCP](http://winscp.net/eng/index.php).

The only disadvantage I can think of is that you will have to start up a new application (like WinSCP) to access your files, they won't be available in My Computer. Maybe I'm wrong about this. Anyone?

---

