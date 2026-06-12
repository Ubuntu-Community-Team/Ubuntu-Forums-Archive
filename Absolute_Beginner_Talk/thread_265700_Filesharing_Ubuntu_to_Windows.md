---
title: "Filesharing Ubuntu to Windows"
date: 2006-09-26
forum: Absolute Beginner Talk
---

### Post by syborfical on 2006-09-26
File sharing Ubuntu to Windows

I have spent the last 2 hours reading and trying things with Samba. Like WTF.

I can view files from my windows box on my Ubuntu. 

Everytime I try to acess a share on my Ubuntu box I get a user name and password box come up. I have made samba passwords for my users using 
Sudo smbpassword &#8211;a username 
And I still get the same error.

Let me simplify this
I have 2 machines.

One ill call PC ( running windows)  the on other linux ( running Ubuntu 6.06.1) .

From linux I can browse my shares on pc read and write to them ect.

From PC I try and browse linux \\linux\share 
&#61672;	then i get a window poping up asking for a user name and password.


How do I get my PC to connect to my linux box? Is there any easy way that works? 

All I want to be able to do is share a few folders on my linux box is that to hard to ask?

---

### Post by JNowka on 2006-09-26
Ok I think I can answer you question.  If all you want to do is share files without "any security" measures then do the following.

goto the command line and type "sudo gedit /etc/samba/smb.conf"

Change your security line to look like this:
security = share

Have your shares follow this:
[Share]
path = /path/to/share/
public = yes
writable = yes

And this should make it accessible without a password.

Once done go to terminal again and type
/etc/init.d/samba restart

Good Luck!.

---

### Post by JNowka on 2006-09-26
One more thing, make sure you also do this at the command line:
"sudo chmod 777 /path/to/share"

This will make the folder availible to everyone on both machines. And not require a password.

---

### Post by Ben Sprinkle on 2006-09-26
Any linux **cannot** write to any NTFS system (WinXP), this may be why your having trouble. There may be distros or apps that can in the future but as of now they can't.

---

### Post by JNowka on 2006-09-26
Thing is the share he is trying to write to is on his linux box.  He is unable to write to the network drive because his permissions and possibly his smb.conf file was not configured correctly.  Samba acts like a middle man between linux and windows allowing them to exchange data.  This isn't a case of trying to write to a harddrive, but trying to share files over a network, which can be done with Linux and WinXP because each operating system takes care of thier own drive.

---

### Post by crokett on 2006-09-26
> **syborfical said:**
> File sharing Ubuntu to Windows
Everytime I try to acess a share on my Ubuntu box I get a user name and password box come up. I have made samba passwords for my 

And I still get the same error.


Samba asking for a username and password is not an 'error'. It will do this depending on how you have Samba configured.   Have you tried entering a username and password?  What happens when you do?  Can you post your smb.conf file?

---

### Post by bigken on 2006-09-26
sudo aptitude install samba
sudo smbpasswd -a (your name)
sudo smbpasswd -e (your name )
sudo /etc/init.d/samba restart ;)

---

