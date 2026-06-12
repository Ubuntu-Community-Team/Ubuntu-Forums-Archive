---
title: "Mac OS 10.3.9/SAMBA woes"
date: 2005-06-23
forum: Apple PPC Users
---

### Post by Uta on 2005-06-23
Although I am running Kubuntu (KDE 3.4.1) as a stand alone OS on a Dell Laptop, I am trying to get file sharing going between my other computers which are 'all' Macs running 10.3.9. I have gotten as far as my LINUX laptop seeing all my Macs and can take and write files but my Mac, sees the Linux shares via it's Network Browser but when it goes to write something to the mounted Linux share it says "You cannot copy some of these items to the destination because their names are too long or contain invalid characters for the destination. Do you want to skip copying these items and continue copying the other items"
Well that is just coo-coo because I am only trying to share one file and it's name is 'uta1.jpg' , it's not too long and no invalid characters? Any ideas why this error message and how to correct it? Thank you.

---

### Post by elvis on 2005-06-24
Are the permissions via your smb.conf as well as the physical file/directory permissions allowing the user you've logged in as (or if no login, the "nobody" user full access to that location?

---

### Post by Uta on 2005-06-24
I now have bi-directional sharing. The truth is I am not sure why I am able to share now and could not previous.
The only thing I changed in the config file was I added this line: available = yes
Thanks for responding to the post--

---

### Post by ltmon on 2005-06-24
I'm having trouble sharing (one-way) between Kubutu and OSX 10.4.

The Mac can see my Linux box, but on clicking "Connect" I just get the spinning coloured circle and have to kill the Finder to keep working.

If you've got this working would you mind posting some short instructions or your smb.conf, as nothing I've found so far has been any help.

Thanks in advance,

L.

---

### Post by Uta on 2005-06-25
First my disclaimer;the steps I took to get sharing via SAMBA with my Macs (10.3.9) and my Linux laptop (Kubuntu) work for my setup and I can't claim that my setup and steps will work for anyone else or that they are 'secure'!
I am Mac centric and a new (enthusiastic-adventurous) Linux newbie so follow my steps at your own risk!

1. On the Mac side make sure you have 'Personal File Sharing and Windows Sharing' enabled. (I do not have a Firewall running on my Macs)
(with Windows Sharing enabled, if hilited gives you your network name, usually an IP number\username, use that name for an account on the Linux side) for simplicity sake I used that name and the same password set on my Mac for the Linux account.

2. On the Linux side,set up an account for the Mac (use the account name you found(know) on the Mac side)make sure the SAMBA server is running (I personally had (fixed now, [http://ubuntuforums.org/showthread.php?t=43330](http://ubuntuforums.org/showthread.php?t=43330)) issues with SAMBA not starting on boot but having to be enabled from the command line,'/etc/init.d/samba start' 

3. On the Linux side create a folder to share at root level, '/root/MYSHARE'. MYSHARE is just an example name, call it anything you want but don't use spaces or more than 8-10(?) characters. I created this folder as 'root'. Do this by, 'Root Terminal' type, 'konqueror' then go to 'Home Folder. Once the folder is created you need to set it to share and the permissions;right click the created folder 'MYSHARE'. My folder has these permissions, Owner and Group Can View & Modify Content and I actually made the ownership, the account name from my Mac side. This is assuming you have already set up an account(Linux side) with the Mac account name and created a password (I did this via SAMBA, see next step) I know this is probably a little out of order but I went back and forth so many times I can't remember at what step I created an account for my Mac, it was probably the 'FIRST' step.

4. As 'root' open up your SAMBA app.,then go to 'Settings'--> 'Internet & Network' --> 'SAMBA'. You should see (Base Settings, tab)under Server Identification, WORKGROUP, your NetBIOS name, Server string, under Security Level, 'I' chose 'Share' and Further Options Guest account: is the mac account name I have set up (not sure that is really necessary but that's what I did). (The Share, tab) if you don't see your shared folder, use the 'Add New Share' button and then the 'Edit Share' button. What I see is the path to my shared folder and it's name under the 'Identifier' and the 'Main Properties' section I have selected Public,Browseable and Available.

That should do it. On the Mac side, it does take a moment or so for the Linux share to show up in the Network Browser window. Hope this helps!

---

