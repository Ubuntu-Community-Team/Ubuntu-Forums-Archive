---
title: "Copying files to a Windows PC from Ubuntu over the network"
date: 2007-09-27
forum: Absolute Beginner Talk
---

### Post by pitseleh on 2007-09-27
I have an ISO on my Ubuntu laptop that I want to transfer over the network to my Windows XP PC. There are no other media alternatives because my jump drive is too small for this file and my laptop does not have any sort of CD-Drive. I tried to go the easy route, hoping that by opening up my XP box, sharing folders (and allowing people to write to them) and such would allow my Ubuntu laptop to see it, but no go. And it just crossed my mind, if I were to see it, could I even copy to it's NTFS drive over the network?

So, can I copy from Ubuntu to an XP PC over the network- if so, how do I set it up? If that's not possible, I know I can use Samba on my Ubuntu laptop to allow Windows to copy *from* my laptop, but how do I go about setting this up?

I'm lost... thanks in advance!

---

### Post by whitewizardcoder on 2007-09-27
hi,
you have two options here, set up a share on your windows pc and copy to it or set up a share on your ubuntu pc and copy from it.  When shared, a drive will be accessed the same, independent of the file system.

The easiest option would probably be to set up a share on your windows pc and copy files to it using the ubuntu pc.  If your windows pc does not show up in the "Network Places" area on your ubuntu machine, press Alt+F2 and run "smb://<ip_to_host>" where <ip_to_host> is the ip address of the windows machine.  This should bring up a nautilus window with your share.

If you want to set up samba on ubuntu, things get a little more complicated.  First, you need to install samba by running
```
sudo apt-get install samba
```
in a terminal.  Then, click "System"->"Administration"->"Shared Folders".  Click "Add", then select the path to the share you want to add.  Click "OK" and close the shared folders window.  Now, if you want to access the share without having to enter a password, open a terminal and run
```
sudo gedit /etc/samba/smb.conf
```
scroll to the end of the file, and you should find your share.  Add the following lines to the end of the section containing your share (or make sure they are there):
```
available = yes
browsable = yes
public = yes
writable = yes
force user = <your_user_name>
force group = <your_user_name>
read only = No
guest ok = Yes
```
Replace <your_user_name> with the name you use to log in to your computer.  Note that this method will expose the share for reading and writing by a potential unauthorized user, but if you are only going to be operating on a home network, it should be fine.  If you need more security, do a search in the forums for smbpasswd.

Hopefully this helps!

---

### Post by rivalarrival on 2007-09-27
No, you don't have to worry about the various filesystems in this situation. Basically, once your operating system is configured to access the drive, the filesystem doesn't matter. You can freely transfer files between drives, partitions, and network shares with different filesystems - your operating system (and the server's operating system in the case of network shares) handles the "translation". For example, most web servers operate on linux and linux filesystems, but windows machines can download and save these files.

You tried to gain access to a shared folder on your windows computer from Ubuntu... How did you do this? I usually use the following procedure, but there are other ways as well:

After you share the folder in windows, you should be able to (on your ubuntu machine) go to Places > Connect to Server...

For Service type, select "Windows Share" 
Enter your Windows machine's IP address in the box marked "Server"

I usually run into problems when I try to browse for windows shares, and occasionally when I use the computer name instead of the IP address.  Using the IP address has never given me any problems, so I always use it. 

Enter the share name in the box marked "Share"
You can leave "Folder" blank
Enter your Windows user name.
Enter an arbitrary name in the last box (name to use for connection)

This should put an icon on your desktop. When you click it, it should ask you for a password - this is your windows password. 


As far as setting up Samba for file sharing on your ubuntu box:
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#Samba_Server](http://ubuntuguide.org/wiki/Ubuntu:Feisty#Samba_Server)

You could also set up an FTP or HTTP server and move the iso to the shared web folder. Apache is a piece of cake to set up, and you could use a web browser on your windows machine to download the file. FTP is a little more difficult to set up but it could work too.

---

### Post by pitseleh on 2007-09-27
> **rivalarrival said:**
> 
You tried to gain access to a shared folder on your windows computer from Ubuntu... How did you do this? I usually use the following procedure, but there are other ways as well:

After you share the folder in windows, you should be able to (on your ubuntu machine) go to Places > Connect to Server...

For Service type, select "Windows Share" 
Enter your Windows machine's IP address in the box marked "Server"

I usually run into problems when I try to browse for windows shares, and occasionally when I use the computer name instead of the IP address.  Using the IP address has never given me any problems, so I always use it. 

Enter the share name in the box marked "Share"
You can leave "Folder" blank
Enter your Windows user name.
Enter an arbitrary name in the last box (name to use for connection)

This should put an icon on your desktop. When you click it, it should ask you for a password - this is your windows password. 

This worked brilliantly! I'm copying over my ISO to the Windows share right now. Thanks for the explanation on the file systems in this situation. I didn't think it would be a problem, but I was not sure.

Originally, I had tried to access those Windows Share folders by first creating the share on Windows and just hoping it might show up when I browsed the network via Ubuntu. I was not really sure how the "Network" thingy under Places compared to the Windows Network function.... but I thought I'd try just in case it was that easy.

Thanks again! I really appreciate the help.

---

### Post by MrFSL on 2007-09-28
I see that the originator has already gotten an answer, but I'd like to post real quickly for others that might trip across this post.

I don't know if installing samba just to transfer one file across the network is exactly the easiest or most efficient way of doing things.

I would suggest using ssh. I know that I have ssh installed on all my boxes, but if you don't you can:
```
apt-get install openssh-server
```

Then you can use winscp [http://winscp.net/eng/index.php](http://winscp.net/eng/index.php) , which is a free sftp/ftp client for windows (which you don't have to install, just run the exe) to browse the whole hard drive of the Linux box.

Less configuration. Probably faster. Secure file transfer (not that its needed in this case).

Just my two cents ;)

---

### Post by HermanAB on 2007-09-28
Hmm, instead of winscp, I'd suggest filezilla: [http://filezilla-project.org/](http://filezilla-project.org/)

You could also install the Filezilla server on Windoze and do the ftp from Linux.

---

### Post by MrFSL on 2007-09-28
filezilla is  good app. I have used it before. I was just thinking of making things less complicated. Less configurations. Less installing applications. etc.

Winscp is not a bad app and is loosely GPL. Plus there are A LOT of benefits of running an ssh server in Linux.

---

### Post by BertP on 2007-09-28
Hmmmmm  very strange.  :confused:

A few days ago when I first installed Thunderbird,  I quickly got tired of the "beep" for new mail, so I just opened up Nautilus and easily copied my Windows sounds that I had placed in a shared directory on my Windows machine....  Tonight it was a different story,  no matter what I did I couldn't get nautilus to list any files on my  Windows share..  Eventually I found this thread  and I am happy to report that adding the ip to the location box on Nautilus did the trick!  However  I am somewhat disappointed about the apparent inconsistent behavior in Ubuntu....  

Thankyou  guys for the great answers and thankyou  pitseleh  for posting my question 4 hours  in advance :)     

.

---

### Post by MrFSL on 2007-09-28
> owever I am somewhat disappointed about the apparent inconsistent behavior in Ubuntu.... 

Trust me it's not Ubuntu thats being inconsistent... It's Windows crappy file sharing. Read on Windows forums and you'll find this exact behavior between Windows machines; where a share is created and everything works - and then suddenly stops for no reason.

Thanks to Ubuntu you didn't have to reformat your HDD to fix it though!! :lolflag:

---

