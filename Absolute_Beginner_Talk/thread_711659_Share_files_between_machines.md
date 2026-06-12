---
title: "Share files between machines"
date: 2008-02-29
forum: Absolute Beginner Talk
---

### Post by siroche on 2008-02-29
OK all - new to Ubuntu so probably obvious and dumb questions here:

I have XP running on a desktop, Ubuntu on a laptop that I have just done last weekend.

I want to copy music etc... from the XP machine to this one (laptop). The machines access the internet through a Dlink router (cabled).

So how to ? 
I see something about SAMBA - have downloaded it to desktop but don't know how to install it.
I really need step by step instructions. The XPmachine is for networking nwith a wrkgroup, comp.name etc...
I can ping the other machines IP address

---

### Post by glennric on 2008-02-29
Here is a guide to setup samba.
[https://help.ubuntu.com/community/SettingUpSamba?highlight=%28samba%29]("https://help.ubuntu.com/community/SettingUpSamba?highlight=%28samba%29")

---

### Post by herbster on 2008-02-29
Do you want to have your network share permanently mounted?

If you just want to browse your network shares, open a nautilus file browser, click Computer and double-click Network, then Windows Network and your pc should show up, you can browse it from there and transfer files to/from.

---

### Post by siroche on 2008-02-29
Whats a Nautilus? Where do I get it? Do I need it? Like I said - I'm a beginner !

---

### Post by brijith on 2008-02-29
> **siroche said:**
> Whats a Nautilus? Where do I get it?

 Nautilus is a file browser. By default it will be  installed in your system. You do one thing Double click on the home folder in your desktop. a window will popup. It is Nautilus..


:)

---

### Post by siroche on 2008-03-01
cheers, got through to the Computer but not icon or anything "Network"

---

### Post by ekendra on 2008-03-01
same here. no 'network' icon when i click computer.

---

### Post by Graphite on 2008-03-01
Guys - Go to "Places" > "Network". This will open a window to show the computers on your network.

...I think. It's empty for me.

EDIT:
I'll post my problem here rather than start a new thread.

I know this should be trivial, but how can I share files between two Ubuntu computers?

I have some large folders (approx 50gb) on a pc running Ubuntu 6.06 (Gnome). This computer has a static IP of 192.168.2.4 Its hostname is bugs-desktop
I want to transfer these files to a laptop running Ubuntu 7.10 (Gnome). This laptop has a dynamic IP, currently 192.168.2.2 Its hostname is bugs-laptop
The two computers are conected to a router, through which they share a net connection. Each computer can ping the other.

On the desktop I right-clicked on the folder I want to share (~/music), clicked "share" and chose NFS. I installed the stuff I was prompted to. In the "allowed hostname" box I put "bugs-laptop".
Then on my laptop I Click on the "Places" menu, select "Network"... and see nothing there.

What have I missed? How can I make the laptop see the shared folder on my desktop?

Thanks,
Graphite

---

### Post by ekendra on 2008-03-03
?

---

### Post by dark_harmonics on 2008-03-03
To access files from an xp computer on your ubuntu computer, do the following:

Share the files on your XP computer (Properties on the folder and add a share)

On your ubuntu computer:
Install samba and cifs
sudo apt-get install samba smbfs
then create a folder to mount it to with:
sudo mkdir /media/<foldername> For example i did sudo mkdir /media/laptopfiles
then mount the drive with sudo mount //ipaddressornetbiosname/sharename /media/<foldername> -o user=xpusername,pass=xppass
For example my full mount command was:
sudo mount //192.168.1.2/share /media/laptopfiles -o user=administrator,pass=notrealpassword

For ubuntu to ubuntu shares lookup setting up NFS. Its very simple to do but beyond the scope of my post here.

Also,

If you want to have it mount automatically when you next boot then you will need to add an entry to your /etc/fstab here is an exampl of an fstab entry for one of my shares:

//192.18.1.200/d$ /media/ydfs01 cifs user=linux,pass=notreal 0 0

---

### Post by ekendra on 2008-03-03
here's how i finally got this working. 

- I went to 'Places -> Connect to Server ...'
- I set the 'Service type:' to 'Windows share'
- I typed in the IP address of my Windows Vista box in the 'Server' field
- closed that screen
- Now a folder launcher appears on my desktop and under 'Places' with the IP address as a title. I can navigate all my shared windows folders through there.

hope this helps someone.

---

### Post by siroche on 2008-03-14
Been a couple of weeks since I had timeto get back to this.
How do I edit that fstab bit thing?

ALso, I installed a heap of updates and I can now see my XP machine but can't get to any of the shared directories there

---

### Post by siroche on 2008-03-14
I installed a heap of updates and now I get where I can see my xp machine but when I drill in to it I get this message "Sorry, couldn't display all the contents of "Windows Network: mshome"."

---

### Post by kujaabi on 2008-03-14
It worked great! Good instructions!  Thanks!!!!

---

### Post by RebelwithoutaClue on 2008-03-14
Similar issue so I will avoid starting another thread...

I can and have mounted my Music folder from my 2003 server and can access no problem.

I can even access the rest of the directories and shares on the server.

However, I can ping both my server and my XP box but when I open network/windows network I see nothing.

Physically they are there, as I have said I can ping them and I have seen the domain controller previously.

Any idea what may have gone wrong as I can no longer [I]see[I] my windows network as I did previously.  Nothing has changed Windows/router end and the only changes I have made Ubuntu end have been to get the animations working and try to speed up boot up with preload and an article on here, so nothing I would anticipate taking away graphical representations of windows domains.

:confused:

---

