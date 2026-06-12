---
title: "[SOLVED] swapping files between MS and Ubuntu"
date: 2008-01-06
forum: Absolute Beginner Talk
---

### Post by revpaul on 2008-01-06
I have 2 computers 1 laptop all on MSHOME network via Belkin wireless G mimo. All works fine in windows 1 hard wired 2 wireless. Network printer works well on all machines using windows and Ubuntu. I do have samba on both machines, it is important for me to share and swap files between laptop and desktop due to work and i would like to move away from windows as much as possible. 

So heres the problem 
1. The laptop and desktop with dual boot can not see or access private network but can connect to internet when using Kubuntu. 
2. Windows machine cannot see either when they are in Kubuntu, neither Kubuntu can see each other.
3. Email works well on Kubuntu but i would like to import address book from outlook and move away from outlook completely.

---

### Post by houstonbofh on 2008-01-06
> **revpaul said:**
> 1. The laptop and desktop with dual boot can not see or access private network but can connect to internet when using Kubuntu. 
2. Windows machine cannot see either when they are in Kubuntu, neither Kubuntu can see each other.
3. Email works well on Kubuntu but i would like to import address book from outlook and move away from outlook completely.
1 and 2) Windows file sharing is not very good.  Many large companies have constant problems with Windows file shares.  Samba has these problems and a few more.  Ubuntu has a few issues with samba...  All this means I do not use Windows file sharing...  I use proftpd on linux and fillezilla server on Windows, and filezilla client on both to share many files.  In Ubuntu you can also create a link in "Places --> Connect to Computer" that will make a folder to an FTP server.
3) Install Thunderbird in Windows.  Import your e-mail.  Copy the save file over to Linux in the Thunderbird hidden directory.  You now have all your mail, and address book. (and a good spam filter)

---

### Post by revpaul on 2008-01-06
> 3) Install Thunderbird in Windows. Import your e-mail. Copy the save file over to Linux in the Thunderbird hidden directory. You now have all your mail, and address book. (and a good spam filter) 
Thank you downloaded Thunderbird and swapping files so easy when your pointer in right direction works very well. :)

Problem 1 and 2 i need to be able to move files and work on files through open office and scribus. i also need to be able to access kids machine remotely.:confused:

---

### Post by houstonbofh on 2008-01-06
Well, we need to look closer...  Forgive me if this gets a little basic, but I want to make sure I cover everything.

To have a networking connection, you have to do two thinks, Find the computer, and have a compatible transport.  We will go in order of what happens...

**Name Services**
On the internet this is DNS.  It simply maps [www.google.com](www.google.com) to 64.233.187.99.  Most home routers also support a DNS forwarder.  This is a local cache, and a list of local addresses.  Anything it does not know is forwarded to the ISP DNS server.  Most routers place the names given in a dhcp request in this list as well.
Alternatively, there are host files (Manual lists on each machine) and directory services. (Like a WINS server on Windows)

So the first thing is to find out if you can see the other machines, and if not, why not.  How are you trying to see them?  Bring up a terminal (Applications --> Accessories --> Terminal) and type "ping conputername" and see what happens.  If Windows firewall is enabeled, you will see nothing, so turn it off for testing.  If this does not work, you will need some type of name resolution to make this work.  If you network is small, static IP addresses and host files may work.

**Access**
All access if via "services" like a web server, or file shareing server, and so on.  When you say "Access" do you me remote desktop? If so TightVNC works very well on Windows, and there is a builtin VNC client in Ubuntu.  If you mean files, there are 3 main choices.  Microsoft Networking is SMB/CIFS and is made to work on Linux with Samba.  However, Microsoft keeps moving the target, does not document the protocols, and they were non too good to begin with.  The basic Windows networking was developed in Windows for Workgroups 4.11, and still has a lot of that legacy.  The plus to it is that it solves the name resolution problem, *when it works...*
The most widely used way to move files is FTP.  There are clients and servers for every platform.  There are programs that allow most platforms to mount an FTP server as a remote filesystem. (Think network drive in Windows)  It is solid, stable, and will work over the internet if so configured.  However, it has some overhead...
The Unix way of file sharing is NFS. (Network File System...  Yes, Unix geeks are so creative...)  There is a NFS utility for Windows, but I know nothing about it.  However, for Linux it is top notch.

**File Access**
Now with duel boot machines you also have file systems hidden away.  There is a driver for Windows that will allow access to your Linux files at [http://www.fs-driver.org/](http://www.fs-driver.org/) and you can mount your Windows files from Linux.  However, be careful with virus scanners scanning the other OS.

So, no that we have a base to work from, what is "broken" in your setup?

---

### Post by revpaul on 2008-07-08
It was down to user access control I just needed to allow network to see folders I wanted to share with.

---

