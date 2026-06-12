---
title: "Playing Remotely Hosted Music"
date: 2007-01-15
forum: Absolute Beginner Talk
---

### Post by madman1337 on 2007-01-15
I was wondering, what is a good media player to play music being remotely hosted across a home network and the server is windows? I can use Samba to view the files and I can copy the files over, but when it comes to playing them without having to copy them, it just doesn't happen. I have tried XMMS and Rythmbox and neither work.

---

### Post by Fitzy_oz on 2007-01-15
> **madman1337 said:**
> I was wondering, what is a good media player to play music being remotely hosted across a home network and the server is windows? I can use Samba to view the files and I can copy the files over, but when it comes to playing them without having to copy them, it just doesn't happen. I have tried XMMS and Rythmbox and neither work.

Hi there,
you will need to mount the windows share to a directory on your Ubuntu box - Similar mappiong drive in XP.  The smb mounting tool is not installed by default so you will need to install it - Jump to a terminal and type the following:
# sudo apt-get install samba
This will install the necessary tools to mount the drive.
Create a new folder on your desktop titled mp3
Then Use the following command:
sudo mount -t smbfs //<Windows Computer Name or IP address>/<share name>    /home/<your username>/Desktop/mp3
This will mount the windows share to the directory mp3 on your Desktop and can be browsed as if it were a folder on your Linux Box.

I have a windows server at home which I mount shares from like so:

sudo mount -t smbfs //windows_box/mp3 /media/mp3.

---

### Post by madman1337 on 2007-01-15
I keep getting an error :

mount: wrong fs type, bad option, bad superblock on //LAP/madman1337_files,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

I do have samba installed, and I have been using it to transfer stuff, and I went ahead and ran the install that you told me to and it said I had the latest version. I know that the directories are correct on the server and I know that the server is currently running and is working correctly

---

### Post by Fitzy_oz on 2007-01-15
> **madman1337 said:**
> I keep getting an error :

mount: wrong fs type, bad option, bad superblock on //LAP/madman1337_files,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

I do have samba installed, and I have been using it to transfer stuff, and I went ahead and ran the install that you told me to and it said I had the latest version. I know that the directories are correct on the server and I know that the server is currently running and is working correctly  -Sorry mate, i was just being thourough.

Try it this way:

sudo mount -t smbfs -o username=<windows username>,password=<your windows password>  [COLOR="Red"]//LAP/'madman1337_files'[/COLOR].  
The share names are case sensitive also and if there are spaces or anything in the names, the share name will need to be put inside '   ' instead of " " under windows.

---

### Post by RV7Charlie on 2008-02-16
> **Fitzy_oz said:**
> Hi there,
you will need to mount the windows share to a directory on your Ubuntu box - Similar mappiong drive in XP.  The smb mounting tool is not installed by default so you will need to install it - Jump to a terminal and type the following:
# sudo apt-get install samba
This will install the necessary tools to mount the drive.
Create a new folder on your desktop titled mp3
Then Use the following command:
sudo mount -t smbfs //<Windows Computer Name or IP address>/<share name>    /home/<your username>/Desktop/mp3
This will mount the windows share to the directory mp3 on your Desktop and can be browsed as if it were a folder on your Linux Box.

I have a windows server at home which I mount shares from like so:

sudo mount -t smbfs //windows_box/mp3 /media/mp3.

OK, I'm even earlier than beginner level, but here's my problem:
I just got a Mythbuntu box running both backend and frontend, and it's plugged into an existing Windows network. It sees the network name and I can browse the internet using Firefox. Samba (whatever that is:-) )appears to be installed. Using Thunar file manager, I can only see files & directories on the Myth box.

I'm trying to get the Myth box to play mp3 files that exist on a Windows box on this network. I've tried several variations on the commands listed above (pulled from these archives) & get various error messages. I've tried both the IP address of the windows box and its name, & both the actual windows C:...file path and the 'My Documents' naming conventions. So far, the command:
sudo mount -t smbfs //<name of windows computer>/'My Documents'/'My Music' /home/charlie/Desktop/mp3
(there's a space between 'My Music' and /home)

yielded the simplest error message:
Could not resolve mount point /home/charlie/Desktop/mp3
(charlie is the name I gave this computer when I installed Mythbuntu.)

Then I realized that I hadn't created the 'mp3' directory on the Desktop. I created it, re-ran the command, and got
timeout connecting to <IP address>:445
timeout connecting to <IP address>:139
error connecting to <IP address> (operation already in progress)
5843: connection to <name of windows computer> failed
SMB connection failed

Can anyone tell me what I'm missing? The router feeding both the windows box & the Myth box has its firewall turned on, and the windows box has its windows firewall turned on, but no passwords are needed within this network. I can play mp3 files from this windows box on other windows boxes on the network. 

Thanks,

Charlie

---

### Post by RV7Charlie on 2008-02-17
answering my own post: @%$^&$ Windows Update destroyed the shared setting for the MY Music folder (along with several other settings; that should have been a clue).
fixed that on the windows box, modified the recommended destination directory to match the default in MythTV's music function, & it will now play music from the windows pc.

I'm not too crazy about the user interface of Mythmusic, though. Maybe I just need to get familiar with it.

Charlie

---

