---
title: "Probably easy command line question?"
date: 2007-12-09
forum: Absolute Beginner Talk
---

### Post by pjones0404 on 2007-12-09
i have a windows pc on my network and it is sharing files. when i go to places-network i see it there and i am able to manipulate files via nautilus. how do locate these files via terminal? does it mount the files somewhere or do i need to use samba or something. maybe attempt to locate via host name or IP?

any help here is appreciated.

---

### Post by eriksallstrom on 2007-12-09
A script I use for mounting a windows network folder:

sudo mkdir /media/mountpoint
sudo chmod 777 /media/mountpoint
sudo mount -t cifs //server/folder /media/mountpoint  -o username=[YOUR USERNAME],password=[YOUR PASSWORD],dir_mode=0777,file_mode=0777

You may have to install smbfs before it works:
sudo apt-get smbfs

Good luck!

---

### Post by pjones0404 on 2007-12-10
thanks for the reply. 

will this do it automatically in the future or is this a one time thing? once i run this will i then be able to go to media and it will be mounted there?

---

### Post by stchman on 2007-12-10
> **pjones0404 said:**
> i have a windows pc on my network and it is sharing files. when i go to places-network i see it there and i am able to manipulate files via nautilus. how do locate these files via terminal? does it mount the files somewhere or do i need to use samba or something. maybe attempt to locate via host name or IP?

any help here is appreciated.

Since you are able to see the files on your Windows machine over the network you must have these shares mounted.  Open a terminal in the Nautilus window by doing File--->Open Terminal

Type pwd in the terminal window.  With will give you the path to the windows share.

If you don't have an option to open a terminal in Nautilus then install the nautilus-open terminal.

```
sudo apt-get -y install nautilus-open-terminal
```

---

### Post by eriksallstrom on 2007-12-10
Those lines will only mount the drive until you reboot. If you want to mount the drive when you start the computer, you need to modify /etc/fstab and add ONE line looking something like

//192.168.44.100/origin /home/username/destination cifs username=netuser,password=hiddenword,_netdev,uid=a_user_name,gid=users 0 0

---

### Post by pjones0404 on 2007-12-11
thanks for the replies. 

i tried the open in terminal plugin for nautilus and i am able to open my local files but none of the files being shared on my windows machine. 

i know that i can set up samba to do this. I am more curious as to why i can see them in nautilus without doing samba. does nautilus do something in the background while it is connecting or something. i just want to understand why one works and the other does not. 

thanks again.

---

### Post by pjones0404 on 2007-12-12
just another bump for this one. 

i am now more curious as to why nautilus is able to see these shares on my windows machine with out needing to setup samba. i always thought that you had to have samba installed to share files w/ windows. i had not installed it though. i thought it was included in ubuntu and did not need to be setup. 

i would like to know is nautilus doing something in the background? can i duplicate what it is doing via terminal or do i have to manually setup samba to be able to access these files via terminal. and if so do i need to enable samba and then also mount the directory where i want it.

I appreciate all the help.

---

### Post by JillSwift on 2007-12-12
I believe (and I may be wrong, but am certain enough to make the statement) that samba-client is set up by default on installing Ubuntu. Nautilus just uses it to resolve URIs like "smb://server/AutoloadTorrent".

Samba-server requires a lot more setup to work, but isn't necessary unless you want Windows machines to get to data on your Ubuntu box.

Not all programs know how to make use of smb: URIs, though. Firefox comes to mind as an example. To let them directly access files on windows machines you do need to mount the remote share (as described by the good folks above) so that it's part of the filesystem.

Hope this helps some. =^_^=

---

### Post by pjones0404 on 2007-12-14
one more  bump for any other explanations. i will let it die after this and wait for a later time to understand.

just to summarize. Why am i able to see shares on my windows machine via nautilus but not via the command line? is samba the only way to do it over the command line? why, if nautilus does it without it?


thanks again.

---

### Post by niteshifter on 2007-12-14
> Why am i able to see shares on my windows machine via nautilus but not via the command line? is samba the only way to do it over the command line? why, if nautilus does it without it?

Nautilus is part of Gnome and is using Gnome's VFS - Virtual File System. Search on "Gnome VFS" - there's a lot of material on it.

I won't so far as to say it's the only way via the command line - sure as I do someone will point out some app that can deal with smb:// URIs. However, using samba (smbclient and smbfs) is the easiest way to deal with shared Windows files - they are presented as being part of the local file system. That way access via Nautilus (bookmark that mount point!) or via command line is simple and easy.

---

