---
title: "Permissions on samba shares"
date: 2006-09-09
forum: Absolute Beginner Talk
---

### Post by kgeil on 2006-09-09
Hi, I am experimenting with Ubuntu, my second Linux os.  My first was Fedora, which I scrapped partly because I could never get samba file sharing to work.  Much to my dismay, I have gotten no further with Ubuntu.  I've spent an embarrassing amount of time trying to do this, and I hope someone can help.

I installed samba, then followed directions carefully trying to share files.  I backed up the original smb.conf file, and got my windows box to see files in the ubuntu box.  The only problem is that the files are read only.  I have not found any clear information on how to adjust those permissions.  I have seen a little information on chmod and chown, but when I change permissions using those commands, my files still show in windows as read-only.

My big questions are:

Where am I changing permissions? In Samba? In Ubuntu? In Both?

Once that one is answered, How do I change them?




I also backed up my second smb.conf and followed stormbringer's How to setup samba peer to peer, and that was pretty much like frying pan into the fire, when I try to map a network drive in windows, I just get "the network path could not be found" errors from windows.  I'm planning to scrap that smb.conf file for my old one, but do I need to redefine samba users?

---

### Post by blueopal on 2006-09-10
Change permissions in Ubuntu using the File Browser application, Properties  -> Permissions. How you set them depends on how you use your local network, security etc.  Checking all the Owner / Group / Others boxes will open them wide up to anybody, so be careful.
I had trouble with SAMBA on Ubuntu (connecting to Ubuntu shares from a Windows XP machine) until I understood why it was always asking for authentication: SAMBA has its own set of users. I followed this process:

Install SAMBA  (use Synaptic Package Manager)
	-use WINS  (not set by default)

Add folder shares and set permissions (use File Browser)

Add SAMBA user(s)
	You will have to add a user like this for each user  account you want to connect to this SAMBA domain server. For example:
	1) Add a linux user tom:
		sudo useradd tom -m -G users
	2) Add the linux user tom to the SAMBA password database:
		sudo smbpasswd -a tom

Nothing worked until I completed this last step.

---

### Post by yellowbeard on 2006-09-11
thank you thank you, I think this is going to solve my problem as well.

---

