---
title: "Sharing with Samba, login problems..."
date: 2007-11-13
forum: Absolute Beginner Talk
---

### Post by GeneticFlea on 2007-11-13
hey everyone, ive been trying to find a solution to this problem and none seem to be working, so i thought id post and hopefully get it working.

Im curently trying to set up samba on 7.10 to share my files over a network to many windows computers. I followed a video instruction guide on youtube that was very informative that involved these steps: 
first set computer name and domain/workgroup through admin/network
 then in terminal open the smb.conf and change browsable and writeable to yes, and uncomment.  
then in terminal type sudo smbpasswd -a <user> (ive tried many here, from simple guest to the same name as my own username)
then it asks you to set a password and confirm, at first this didnt work, but when i just tried it to recreate the error it now said added user guest. 
then i navigated to the folder i wanted to share and right clicked chose share folder, chose samba and read only. 
then i tested it on a windows xp computer. I had my friend navigate to my workgroup and to my computer all of which worked. when he tried to login using the new username and password(guest, guest) windows brought up an error. 

any idea what im doing wrong? Ive searched these forums and there doesnt seem to be a clear solution. Im also pretty confused as to what i did when i typed smbpasswd -a. not sure what it was for.


thanks!

---

### Post by reckless2k2 on 2007-11-13
this should help as samba is not terribly confusing. follow word for word and you should get the idea where you went wrong with your users or smb.conf. 

[https://help.ubuntu.com/community/SettingUpSamba?highlight=%28samba%29](https://help.ubuntu.com/community/SettingUpSamba?highlight=%28samba%29)

---

### Post by GeneticFlea on 2007-11-16
ill give it a shot...thanks!

---

