---
title: "Sharing files between Ubuntu and Mac OS X"
date: 2006-08-21
forum: Apple PPC Users
---

### Post by Tofu on 2006-08-21
My apologies for asking such a basic question, but I've searched for hours for an answer, but can't find it.

I just want to share files between a Ubuntu machine and an OS X machine on the same home network.

I read that **AFP** is Apple's standard file sharing protocol, and that the old **AppleTalk** is basically dead (being dropped by Apple).

I read that Ubuntu uses **NFS**.

I read that Windows uses **SMB** (Samba). In earlier threads, some people say "just use Samba", but it doesn't seem to make sense to use a Microsoft format when linking a Linux box to an OS X box. Also, OS X throws up warning messages that "using Windows sharing will cause your password to be stored in an insecure manner.

So I assume I should get the Ubuntu machine to read AFP, or the Mac to read  NFS. Are both possible? Is one better than the other? Would it be easy to implement Apple's Rendezvous in the mix?

I found an Apple Support Document [25344]("http://docs.info.apple.com/article.html?artnum=25344") that shows how to access NFS. When I tried it, nothing happened. Another [recent thread]("http://www.ubuntuforums.org/showthread.php?t=221342") says the export config file must be changed, but doesn't say how to do it.

I think it would be worthy of including something in the Ubuntu user documentation about how to network with Macintosh OS X computers.

---

### Post by stmiller on 2006-08-21
Yes, NFS is probably the way to go. I think there's a free app called NFS Manager for OS X. That helps on the OS X side. SMB is somewhat poor in mac OS X, even in the latest Tiger, I have found.

---

### Post by tidris on 2006-08-21
I normally use FTP for that purpose. Tried SMB at one point but the transfers were very slow for some unknown reason and I gave up on it.

---

### Post by Welles on 2006-08-21
Tofu,

This may not be helpful but I have a small LAN with Mac OS 10.4.7, Windows XP, Xandros Desktop on an x86 machine and Ubuntu on a Power PC G4 Mac. After much goofing around with file sharing, I just broke down and purcased licences from Lava Software for PC-Mac-Net FileShare.

[www.lavasoftware.com/fileshare.html](www.lavasoftware.com/fileshare.html)

There was only one drawback. The capacity of the file transfer to/from a Linux distro was written for x86 architecture, not Power PC so if your Ubuntu install is on a Mac it won't work. My solution was to use a USB flash drive which is recognized by all platforms.

Good Luck!

---

### Post by calum on 2006-08-21
> **Tofu said:**
> I read that Windows uses **SMB** (Samba). In earlier threads, some people say "just use Samba", but it doesn't seem to make sense to use a Microsoft format when linking a Linux box to an OS X box. Also, OS X throws up warning messages that "using Windows sharing will cause your password to be stored in an insecure manner.

So I assume I should get the Ubuntu machine to read AFP, or the Mac to read  NFS. Are both possible? Is one better than the other? Would it be easy to implement Apple's Rendezvous in the mix?

Samba is probably the easiest to set up, but it does have its drawbacks... apart from the cleartext password issue, it doesn't support Unix/Linux-style file permissions.

NFS is pretty much the standard for sharing between Unix/Linux machines, but can be a bit of a pain to set up.

Rendezvous is theoretically possible; it's just a flavour of the open Zeroconf standard, which exists for Ubuntu in the forms of Avahi.  Never tried it though so I don't know how it works in practice. See [http://www.linux.com/article.pl?sid=06/06/15/2012219](http://www.linux.com/article.pl?sid=06/06/15/2012219) for some more information about that.

---

### Post by liam_stoush on 2006-08-21
The solution I use for sharing files temporarily over a crossover cable is to SSH in, using Mac OSX's 'Preferences --> Sharing --> Remote Login'. Then there's either the terminal way:

```
$ ssh username@computername.local 
```

Or the GNOME way, Places --> Connect to Server... --> Service Type: SSH

---

### Post by Tofu on 2006-08-21
I got ftp working between Ubuntu & OS X. At least now I can bring my files across.

Here's some research on Avahi (Bonjour/Zeroconf for Ubuntu).

Wikipedia entry Avahi:
[http://en.wikipedia.org/wiki/Avahi_%28software%29](http://en.wikipedia.org/wiki/Avahi_%28software%29)

The Avahi website:
[http://avahi.org/](http://avahi.org/)

I downloaded Avahi. On launching, it immediately discovers the other Mac OS X machine on the network. But it doesn't seem to activate anything, or try to connect.

---

### Post by Torstein_V on 2006-08-22
But, is there a way for my PowerBook G4, running 10.4.7, to connect to Ubuntu, like Ubuntu connects to the PowerBook via "Connect To SErver" + "FTP with login"?

---

### Post by stmiller on 2006-08-22
NFS is not hard to set up. Just install the NFS pacakges needed, then in Gnome right click the folder you want to share, and click 'share.'

---

### Post by COL on 2006-08-23
Hi,

First post, so please be lenient if I'm not observing all the protocols.  I found that the OSX app Fugu was the easiest way to share between the two.  It uses SSH, is freeware and you can upload and download with no problem.  Seemed like an easy way for a non-techie to do this.

---

### Post by avtolle on 2006-08-23
Yeah, Fugu is how my older daughter and her husband share files between her PB and his Ubuntu box. They highly recommend it.

---

### Post by Tofu on 2006-08-24
> **COL said:**
> I found that the OSX app Fugu was the easiest way to share between the two.  It uses SSH, is freeware and you can upload and download with no problem.  Seemed like an easy way for a non-techie to do this.
Thanks, Col. I just looked up Fugu.

Here's the link, in case anyone else is interested:
[http://rsug.itd.umich.edu/software/fugu/]("http://rsug.itd.umich.edu/software/fugu/")

---

### Post by calum on 2006-08-24
> **stmiller said:**
> NFS is not hard to set up. Just install the NFS pacakges needed, then in Gnome right click the folder you want to share, and click 'share.'

It's easy to set up in that sense, but you often run into permission problems with the different uids on different machines, and that sort of thing.  (Even as I write I'm tearing my hair out with such a problem, see [http://ubuntuforums.org/showthread.php?t=242540](http://ubuntuforums.org/showthread.php?t=242540) if you think you can help....)

---

### Post by Torstein_V on 2006-08-26
Thanks! I'll look into Fugu. Hope it works :)

---

### Post by Christiaan on 2006-09-04
message deleted (couldn't find delete button)

---

### Post by mac57 on 2006-09-27
I took a run at this last night and focused on the SMB/Samba approach. It actually worked very well, very quickly, with only one small problem. 

First the approach. On the Mac, it is ridiculously easy - I went to the Sharing Preferences Pane, and click the "Windows Sharing" check box. Then I approved my userid for file sharing via the simple dialog on the same panel. That is it. All done. 

On the Ubuntu side (running on my x86 PC) it was a little more difficult. I loaded up pretty much every package I could find with "samba" in the name anywhere. Then, I did a "sudo modprobe smbfs" (which may or may not be needed). Then, after doing a few google's on the topic, I did the following:

Went to Nautilus, selected Go, Location

Typed smb://ip-address-of-my-mac/my-userid-on-the-mac

After a lo-o-o-o-o-o-n-g delay (minutes, not seconds) I was prompted for a password and I was in. Nautilus now presented a file manager window of the files on my Mac home directory. I have full read/write access and all is actually pretty zippy from a speed perspective. I added a Nautilus shortcut to this directory and now I can just double click the shortcut and I am there. Excellent.

Now for the fun. I decided it would be better if I could just get this into my /etc/fstab, and be able to use normal mount/umount commands to achieve the same result. After more googling, I added the following line to fstab and it worked:

//ip-address-of-my-mac/my-mac-userid   /media/my-mac   smbfs noauto,rw,users,username=my-mac-userid,password=my-mac-password  0 0

This worked brilliantly... almost. At an xterm, if I now type:

sudo mount /media/my-mac

after a l-o-o-o-o-o-n-g delay, plus an error message about a timeout, the Mac mounts correctly and I get a shiny new disk icon on my desktop. I can double click it and Nautilus presents the contents of my Mac's home directory. Subjectively, this feels a little faster than the Nautilus only approach I described above.

BUT I only have read access. No matter what I try, I can't get read/write access (i.e. can't create files or directories, or edit and save things, etc.). This limits the usefulness tremendously. After googling a bit more, I added options "uid=my-ubuntu-userid,gid=my-ubuntu-group-id" to the list of options in the fstab line (this is supposed to grant full read/write to the specified Ubuntu user) but it doesn't work. Still read only.

So, after this whole long winded story, a question. Has anyone managed to get full read/write via smbfs and fstab, to a Mac running OS X? If so, how did you resolve the read/write issue above? Thanks!

---

### Post by mac57 on 2006-09-28
I managed to resolve the "read only" issue for mounting the Mac disk via smbfs and thought I would post it here for the benefit of future readers.

Basically, you need add the following two options to the /etc/fstab line:

fmask=0644,dmask=0755

This sets the file (fmask) and directory (dmask) masks for file access. The default settings say they are taken from umask, but it would appear that they tend to the "safe" side. The above translates as:

0644 is rw-r--r--
0755 is rwxr-xr-x

This lets your userid create, delete, read and write files, while all others can only read the results, and lets you create, delete and use directories, while everyone else can only use them. 

Hope that this may help others trying this out.

Now, if I could only get rid of that long delay too!  :)

---

### Post by dppowell on 2006-09-30
I'm finding that Fugu app to do pretty much everything I need.  It might not be as slick as zeroconf-style file sharing, but if you're just looking for a quick & dirty way to move a whole lot of files between Ubuntu 1 and Mac 2, it's your ticket.

---

### Post by mike3k on 2006-10-01
I'm using my Ubuntu system as a file server for my Macs and I find NFS to be the most reliable file sharing method. There are a few things necessary to use NFS with Mac OS X: you need to specify insecure & no_auth_nlm on your export:

/home   192.168.0.0/24(rw,async,no_auth_nlm,insecure,all_squash)

There's one annoyance, which I haven't figured out a satisfactory solution for: Mac OS X & Linux don't use the same user IDs. On a Mac, the first user has the ID 501 while Linux uses 1000, so file ownerships are messed up. I haven't figured out how to set up user ID mapping so the file ownership will be correct both when I mount my home directory from my Mac and log in locally. On my old Linux box I set my user ID to 501, but that causes some problems with various scripts.

---

### Post by ORBiTrus on 2006-10-12
> **mac57 said:**
> Now for the fun. I decided it would be better if I could just get this into my /etc/fstab, and be able to use normal mount/umount commands to achieve the same result. After more googling, I added the following line to fstab and it worked:

//ip-address-of-my-mac/my-mac-userid   /media/my-mac   smbfs noauto,rw,users,username=my-mac-userid,password=my-mac-password  0 0


Two Appologies to everyone:
a) Sorry for bumping an old topic, forum.
b) This is kind of an aside.

I HIGHLY recommend avoiding using fstab when dealing with network file systems.  Instead, use AutoFS to mount them as needed, and have a timeout so they unmount when not in use.  (Really handy if a server goes down no to have to unmount everything).

For my Samba / NFS (v4) shares, my system looks like this:

```

# ls -l /mnt/solserv
-rw------- 1 root root 22 2006-10-11 19:32 auth
lrwxrwxrwx 1 root root 23 2006-10-11 21:45 homes -> /mnt/autofs/solserv/homes
lrwxrwxrwx 1 root root 22 2006-10-11 21:45 docs -> /mnt/autofs/solserv/zfs-docs
lrwxrwxrwx 1 root root 23 2006-10-11 21:45 pub -> /mnt/autofs/solserv/zfs-pub

```

So, all my shares stored by AutoFS in /mnt/autofs/solserv and my username and password stored in /mnt/solserv/auth.

```

# cat /mnt/solserv/auth
username=orbitrus
password=hidden

# ls -l /etc/auto.master
lrwxrwxrwx 1 root root 22 2006-09-04 01:11 auto.master -> /etc/autofs/auto.master

# ls -l /etc/autofs
-rw-r--r-- 1 root root  141 2006-09-03 23:55 auto.solserv
-rw-r--r-- 1 root root  419 2006-09-03 23:55 auto.master
-rw-r--r-- 1 root root   34 2006-09-03 23:55 auto.media

# cat /etc/autofs/auto.master
/mnt/autofs/media       /etc/autofs/auto.media          --timeout=10
/mnt/autofs/solserv     /etc/autofs/auto.solserv        --timeout=60

# cat /etc/autofs/auto.solserv
homes      -fstype=nfs                                  solserv:/home
zfs-docs   -fstype=smbfs,credentials=/mnt/solserv/auth  //solserv/Documents
zfs-pub    -fstype=smbfs,credentials=/mnt/solserv/auth  //solserv/Public

```

I'm using SMB shares since Solaris 10 uses NFSv4, and ZFS uses NFSv4-style ACL's.  I haven't updated my Linux systems to NFSv4 yet, and I want to make sure ACL's are enforced...

---

