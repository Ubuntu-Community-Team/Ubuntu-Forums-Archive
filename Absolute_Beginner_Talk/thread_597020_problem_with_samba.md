---
title: "problem with samba"
date: 2007-10-30
forum: Absolute Beginner Talk
---

### Post by rtoobtoo on 2007-10-30
hi,
we have suse linux running on our fileserver. it uses samba in order for the windows client to connect and share files. my question is if i change my OS from Windows to Ubuntu 7.04 , how can i access the samba server ? are there any configuration? 

 thanks !

---

### Post by bubbalouie on 2007-10-30
Yes you can easily access a samba server, KDE provides beautiful in built samba browsing without any configuration needed at all, network printers in KDE are a snap too. The same may be true of Gnome, but I can't say for sure.

I found the following tute to be very nice for setting as permanent samba mount (makes it look like a share is bolted straight on your file system):

[http://ubuntuforums.org/showthread.php?t=288534&highlight=mount+samba+shares+for+read+write+access](http://ubuntuforums.org/showthread.php?t=288534&highlight=mount+samba+shares+for+read+write+access)

Good Luck :)

---

### Post by finer recliner on 2007-10-30
you dont need windows to host a samba server. linux can be the server if you want.

i remember i used this site to help me:
[https://help.ubuntu.com/community/ComprehensiveSambaGuide?highlight=(samba](https://help.ubuntu.com/community/ComprehensiveSambaGuide?highlight=(samba))

but i dont think it explains how to set up a samba serber on linux. i forgot where i found that info. :-/

---

### Post by rtoobtoo on 2007-10-30
the samba server is running for some time now and i dont have any idea how will the users regain access to their respective folders on the suse linux fileserver.

we have been using windows xp to access the files on the server, so im worried they cant access they folders anymore because the os had changed

---

### Post by finer recliner on 2007-10-30
does the policy "if it isn't broke, don't fix it" not apply here? just stick with windows if you're that worried about it. linux samba is very compatible with windows SMB

---

### Post by Orbital75 on 2007-10-31
What a great answer, that really helped him out.  :KS

Don't worry, you'll be able to access your servers files. 
You can either Mount the Server Shares to your Ubuntu 
or just browse to that folder. Your best option would be 
to add the shared files to the Fstab file on your Ubuntu Machine,
this would Mount the Shared files on Boot and show up where ever
you decide to mount the drive such as your Desktop or your Home
folder. Very simple to do.

Create a file either on your Desktop in your Home Folder.
This do this in the Terminal.

This will open your fstab file so you can edit it.
```
sudo gedit /etc/fstab
```

Now all you have to do is enter in your mount points.

---

### Post by HermanAB on 2007-10-31
Make sure that user names and passwords are the same on the new machine.  If you don't know what the passwords are, create the user accounts the same and then reset the passwords all the same using 'smbpasswd' on the samba server.

Do go and read the 'Official Howto'  on the samba web site.

'Hope that helps!

Herman

---

