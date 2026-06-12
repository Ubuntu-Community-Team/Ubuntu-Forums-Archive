---
title: "Got root?  I don't..."
date: 2006-08-06
forum: Absolute Beginner Talk
---

### Post by darkfired on 2006-08-06
I've been digging though on-line forums, but have no idea what state I've actually reached with Ubuntu.  I think I've managed to screw up something with user accounts, but I don't know what to look at and how to fix it.

I am trying to create a dual boot with Windows XP SP2 with each OS on its own drive and ntldr running the show.  After several tries, I managed to get it to work by using the manual settings during Ubuntu installation, which allowed me to force a separate /boot partition at the start of the secondary drive.  I then used bootpart to grab the start of the secondary drive and create the new entry in the Windows boot.ini file.  Both OSes appear to boot correctly, but Ubuntu won't let me do anything substantive to the system--I can't download updates, access user accounts, etc...

While loading Ubuntu with the expert settings, it forced me to create a root password and a user account/password.  From what I understand of Ubuntu, root should not be active.  I am guessing that my user account has no privileges and the root account is turned off.

If you've got some idea where I'm stuck, please let me know.

---

### Post by 23meg on 2006-08-06
What error do you get when you try launching an administrative app or when you enter a command that begins with sudo?

Check to make sure your user is part of the "admin" group.

---

### Post by catlett on 2006-08-06
sudo can be used by users in the administration group.
Try this. Boot into (recovery mode). This will give you root powers. Then add the iser to admin (I'll use darkfire for the example)
```
sudo adduser darkfire admin
```
You could also make a new user with sudo powers and work with that user.
At the recovery console
```
sudo adduser newuser
```
Then bring up the /etc/sudoers file in vi
```
 sudo visudo
```When the file comes up, add this line to the bottom of the file
```
newuser    ALL=(ALL) ALL
```
Actually you could just add this user to the admion group to get sudo powers as well
```
sudo adduser newuser admin
```
The dapper guide has a section on root and user accounts [http://doc.gwos.org/index.php/DapperGuide#How_to_add.2Fedit.2Fdelete_system_users](http://doc.gwos.org/index.php/DapperGuide#How_to_add.2Fedit.2Fdelete_system_users)

---

### Post by darkfired on 2006-08-07
Hmm...  I should note here I am on Breezy Badger (5.10) until I get the downloads working again.

/etc/group includes the following (among others):

root:x:0:
syslog:x:102:
sys:x:3:
adm:x:4:scott
floppy:x:25:scott,hal
sudo:x:27:
users:x:100:
scott:x:1000:

I presume adm is the administrative group, and it shows username "scott" belongs to that group (and that is how I am logged on).  It also shows a group called "scott."  But "scott" is not in the users group.

The GUI interface to ShowUpdates requests a password when I first click on it.  It fails to respond when the password is entered, and there is a lag (15 minutes?) before I can try again.  I get no response from actions like Users and Groups, Update Manager, Synaptic Packet Manager, Disks, and the like under the System-> Administration pulldown menus.

On the command line, sudo commands appear to work; that is, I get no error messages.  For example: "sudo adduser scott admin" asked for my password as expected but gave no errors.  (The listing above came after this command.)

Should the group "scott" be deleted?  Are any entries obviously amiss?

---

### Post by darkfired on 2006-08-07
Ha ha.  colon-ex- got translated to a face.  Sorry 'bout that.

---

### Post by darkfired on 2006-08-07
Still more confusing.

I tried giving "show updates" the wrong password, and I got an error message.  The correct password gets no response.  ::sigh::

---

### Post by darkfired on 2006-08-07
Okay, I've tried a number of things, and it appears the installation is in bad shape.  I can't boot into safe mode, because Ubuntu says safe mode was not installed!  I also am beginning to suspect that many of the other programs are in similar condition.  When I start trying to look at the disks, for example, it says "Starting Disks", hangs for 15 seconds, then the starting icon in the system tray disappears.  I presume the process is being killed off.

I presume I need to reload the entire thing.  Again.  ](*,)

---

### Post by catlett on 2006-08-07
You can try one last thing. This ended up working in another thread I was involved in. The one issue is your password not working but you can try it for the sake of it.
What you want to accomplish is getting into "Users and Groups". You can do it 2 ways.
1.) From the panel. Go to System<Administration<Users and Groups
2.) From the terminal enter```
 sudo users-admin
```
When (if) the window appears, click on your user name to highlight it. Then select the "properties" box. When that window appears select the "permissions" tab.
The issue the other person had was that all his users permissions were removed. When you select that tab, all those permissions should be checked off. If you get there and they ARE checked off then this isn't going to help you. If you get there and the boxes are unchecked, check them off.  Hopefully   the loss of your users permissions was it.
If this doesn't work then I do not know what else to say except you may want to back-up your data and re-install.


P.S. The smiley face in your post is caused by the smileys the forum uses. If you happen to type the string of characters that make a smiley, they appear. When this happens unimtentionally, you can select "disable smiles in text" in "Additional Options" under the "submit reeply" buttons.

---

### Post by darkfired on 2006-08-07
I tried opening Users and Groups again, to no avail.  sudo users-admin also got no response.  With either one, the first attempt gets a password request followed by no activity.  Subsequent attempts don't even request a password.  I suspect some critical code is not loaded or misplaced in the system.  

At this point I'll try reloading.  But thanks to everyone for their suggestions.  I appreciate the company.  :-)

---

