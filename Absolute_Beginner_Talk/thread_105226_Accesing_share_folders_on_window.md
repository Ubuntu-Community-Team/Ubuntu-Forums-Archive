---
title: "Accesing share folders on window"
date: 2005-12-17
forum: Absolute Beginner Talk
---

### Post by dannyngweekiat_85 on 2005-12-17
I just shited to ubuntu from xp. all of my friends here uses window xp. So i am now having problem in accesing their shared folders. I tried network server. They show window network but the inside is blank. Can anyone help out?.. :confused:

---

### Post by jimrz on 2005-12-18
you will need samba...it's in the repositories...use apt-get, or better yet Synaptic.

Check [this]("http://wiki.ubuntu.com/SettingUpSamba?highlight=%28samba%29") out.

---

### Post by dannyngweekiat_85 on 2005-12-18
already install it but still there is nothing at the windows network icon.... do i have to do any aditional setup? btw..can it be done by using connect to server.. command?

---

### Post by dannyngweekiat_85 on 2005-12-18
still have problem using the share folder..... can any1 help? really new to linux network.....

---

### Post by snellgrove on 2005-12-18
get them to check their firewalls, maybe its that.

I didn't install anything special (I dont think anyway :confused: ) but I've always been able to access the windows (xp pro) box in our house.

System menu > Administration > networking > General tab

do you have a domain in there? I dont, saw a mate use this and it seemed to throw up all sorts of extra authentication requests and problems - So I wouldn't bother with this, on a standard LAN / workgroup environment. I guess its only used to access domain controller type stuff.

---

### Post by dannyngweekiat_85 on 2005-12-18
still not getting the shared folders.... wierd.... nvm ... will try to fiddle with it more to try to get in to their folder c...

---

### Post by djur on 2005-12-18
You need to go to /etc/samba/ and edit the smb.conf file.  You should ensure that your computer is on the same workgroup.  I believe it will ask you for a login when you access the folders, and this login needs to be one that has access on the XP computers (possibly administrator access?).

---

### Post by dannyngweekiat_85 on 2005-12-19
[QUOTE=djur]You need to go to /etc/samba/ and edit the smb.conf file.  You should ensure that your computer is on the same workgroup.  I believe it will ask you for a login when you access the folders, and this login needs to be one that has access on the XP computers (possibly administrator access?).[/QUOTE]

For which setting and wat can change? the workgroup there shown is MSHOME which is the workgroup they using. So by accesing the file i just use network server rite?

---

### Post by dannyngweekiat_85 on 2005-12-19
I manage to get the network server goin somehow...
but every time i click on that ... it ask for password for my server.. wat is the password?.....but then i still cant access window share folder...

---

### Post by djur on 2005-12-27
I believe the password is for your ubuntu system, it should be the same as your user login.

---

### Post by rancourt on 2005-12-27
Hmm. I didn't see this option listed, so I thought I'd offer it here. I do indeed use Samba to access Windows shares from my Ubuntu system, but I did it a slightly different way.

In this example, the Windows share is \\bahamut\d with username "administrator" and password "secret", and the chosen mount point will be /bahamut. Of course, you'll want to replace these with your own appropriate settings.

First, I installed the smbfs package with apt-get (sudo apt-get install smbfs). 

Next, I created mount points for the shares I wanted to connect to. Much like the way Windows can map a share to a drive letter, Ubuntu can map shares to a directory in your file system. You can put these anywhere you like; I linked mine off of the root of the filesystem by changing directory to the root (cd /), and creating a directory there -- in my case, named "bahamut" -- in which to mount the share (mkdir bahamut). You may need to do this as root instead, depending on your file system permissions (sudo mkdir bahamut).

** If you want to automatically mount these shares on boot:

I wanted to automatically mount the share every time I started my laptop, so I edited the fstab file in /etc (sudo nano -w /etc/fstab). In this file, I created the following line near the end:

//bahamut/d      /bahamut     smbfs     user,dmask=777,fmask=777,credentials=/root/.smbcredentials    0   0

The first item on the line is the Windows-style UNC for the share, with backslashes changed to slashes -- \\bahamut\d became //bahamut/d. The second item is the mount point -- that directory we just created a moment ago. The third item is the file system type, smbfs.

The fourth item is a collection of parameters separated by commas (no spaces). I added "user" to allow everyone (not just root) to mount the share, set fmask and dmask to 777 to allow all users of the system full file system permissions (read and write), and referred to a file that hasn't been created yet -- /root/.smbcredentials -- where I'll put the username and password for the share.  We'll get to that in a moment. The two zeroes after this section specify dump and fsck order settings -- you won't need to change these.

Save the file (CTRL-X, Y, enter).

Finally, I created the /root/.smbcredentials file (sudo nano -w /root/.smbcredentials), and add the following two lines to it:

username=administrator
password=secret

Save the file (CTRL-X, Y, enter). If you have multiple shares with different passwords, create as many different .smbcredentials files as you need (perhaps calling them .smbcredentials-server1, .smbcredentials-server2, etc.). Just remember which file corresponds to which server, because you'll need to make sure the files match in the corresponding entries in /etc/fstab.

The shares should mount the next time you boot the system, or if you'd like to mount them right away, use the mount command (sudo mount -a).  

** If you don't want to automatically mount the shares on boot:

First, create the /root/.smbcredentials file (sudo nano -w /root/.smbcredentials), and add the following two lines to it:

username=[Windows share user name]
password=[Windows share password]

Replace the bracketed areas with the correct user name and password for your share. Save the file (CTRL-X, Y, enter).

Next, mount the share manually when you want to  (sudo mount -t smbfs //bahamut/d /bahamut -o fmask=777,dmask=777,credentials=/root/.smbcredentials).


Hope this helps you!

---

