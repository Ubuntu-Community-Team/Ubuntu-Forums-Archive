---
title: "No share yet"
date: 2007-09-14
forum: Absolute Beginner Talk
---

### Post by gimpguy2000 on 2007-09-14
Ok, scenario:

Two weeks ago or about there, I spent 7 hours trying to share a folder on my network. No one had an answer for me. I vowed to do away with Ubuntu and decided to give it a few more patience, now , about two weeks later, two ubuntu smashed iso disks, and a major headache, I still sit here trying to share a dang folder and this will be the last attempt else Ubuntu is no more so anyone who could point some steps out to me, please do. I have gone to all the "do it yourself ubuntu answers etc... and nothing seems to fit what I want to do. 


I have two computers, both running Ubuntu, "for now" ...

I have on my main PC, one shared folder. Now, on my other computer, I can see this folder, I can put files in this folder, on my main computer that I set the share up in, I can't see any files that were put in the folder from the other computer. I simply want to swap files in this folder, that's all. I have allowed read\write access on my main for this folder, I have allowed it on the other pc for the folder, but yet, it's a one way ticket. So to sum it up..

Computer A <created the share<can read and write but cannot see anything Computer B puts in the folder. Computer B can see computer A's material though and write to folder. So the computer B has full functionality as to where Computer A on where I set the dang folder to begin with, can't see all material.  

I keep getting told to run SMB but this is a Linux to Linux but will take advice from those who know. I just figured an L2L would be NFS so haven't even gone there as I have been told that NFS is wrong wrong wrong. So....no I haven't used NFS just SMB. 

I think I have been more than patient with this OS and so far no one can answer this let alone give me even a hint of info on it.  I have looked at most every link available and found nothing on my issue. 

So in last hopes of keeping Ubuntu and possibly doing physical harm to my PC, I ask that someone could please step through this. 

Thanks,

Paul

---

### Post by mikeyphi on 2007-09-15
So close and yet so far!!
You seem to be almost there - it must be just a simple item on one of the systems - I am also running two computers on Ubuntu with file sharing and all works OK.
What I did - under Systems/Administration/Services ticked Folder Sharing Service (Samba)
under Shared Folders - add the Folder to be shared, select properties and share through windows network (SMB), enter the 'owner' name of the Folder, ensure not Read only. In the General Properties tab - enter the domain name (whatever you called your workgroup on the network) and tick this computer is a Wins Server (don't know if that is necessary but it works for me)
Do that with appropriate answers on both computers - should work unless you have got a problem with permissions on one of your systems.

---

### Post by vanadium on 2007-09-15
I do not see what is wrong with nfs. The only issue is probably the security issue if you need to share over an insecure network. I am connecting to my desktop using nfs, and later I also discovered the sshfs way, which uses encrypted traffic. I used this procedure to set up sshfs:

[http://www.howtogeek.com/howto/ubuntu/how-to-mount-a-remote-folder-using-ssh-on-ubuntu/](http://www.howtogeek.com/howto/ubuntu/how-to-mount-a-remote-folder-using-ssh-on-ubuntu/)

and this one for nfs

[http://ubuntuforums.org/showthread.php?t=249889](http://ubuntuforums.org/showthread.php?t=249889)

I was a brand newbie (two, three weeks) at that time ...

---

### Post by gimpguy2000 on 2007-09-15
> **mikeyphi said:**
> So close and yet so far!!
You seem to be almost there - it must be just a simple item on one of the systems - I am also running two computers on Ubuntu with file sharing and all works OK.
What I did - under Systems/Administration/Services ticked Folder Sharing Service (Samba)
under Shared Folders - add the Folder to be shared, select properties and share through windows network (SMB), enter the 'owner' name of the Folder, ensure not Read only. In the General Properties tab - enter the domain name (whatever you called your workgroup on the network) and tick this computer is a Wins Server (don't know if that is necessary but it works for me)
Do that with appropriate answers on both computers - should work unless you have got a problem with permissions on one of your systems.

Thanks for the reply. Yep, did that numerous times :(  If I boot into Windows on both computers.."blah" ..but the network and file shares work fine so I know it's not a nic issue.  Plus at one point it will work as I stated, just not "all the way" then other times, even that share comes up, "unable to read folder contents, yadda yadda, maybe folder was moved or deleted" even though it's still there.  Then it will work another time. :confused:  Whatta mess...

TX

Paul

---

### Post by gimpguy2000 on 2007-09-15
> **vanadium said:**
> I do not see what is wrong with nfs. The only issue is probably the security issue if you need to share over an insecure network. I am connecting to my desktop using nfs, and later I also discovered the sshfs way, which uses encrypted traffic. I used this procedure to set up sshfs:

[http://www.howtogeek.com/howto/ubuntu/how-to-mount-a-remote-folder-using-ssh-on-ubuntu/](http://www.howtogeek.com/howto/ubuntu/how-to-mount-a-remote-folder-using-ssh-on-ubuntu/)

and this one for nfs

[http://ubuntuforums.org/showthread.php?t=249889](http://ubuntuforums.org/showthread.php?t=249889)

I was a brand newbie (two, three weeks) at that time ...


I just may try nfs and see what happens, however, I have no option to use it :( 

TX

Paul

---

### Post by Allysan on 2007-09-15
Not sure why you don't have the option of using NFS.  It works GREAT for me and sounds perfect for what you need.  The HowTo Vanadium posted is what I used to get it working and it's great.  I recommend automounting at startup from /etc/fstab (it just simplifies things).  Also go to page 16 of that thread and read the first post - the one about using the server's ip address instead of computername.domainname - this worked for me.

---

### Post by gimpguy2000 on 2007-09-15
> **Allysan said:**
> Not sure why you don't have the option of using NFS.  It works GREAT for me and sounds perfect for what you need.  The HowTo Vanadium posted is what I used to get it working and it's great.  I recommend automounting at startup from /etc/fstab (it just simplifies things).  Also go to page 16 of that thread and read the first post - the one about using the server's ip address instead of computername.domainname - this worked for me.

 Thanks, I just did a complete reinstall of my system yet again and some good news, I can share now, just not all the time, lol. Sometimes it's there even when already mounted, sometimes not. I still have no NFS option even though it asked to install it when I chose it, now the option is gone and I had to yet again use SMB but at least I can share on and off. 

Thanks again,

Paul

BTW, I tried that NFS link and all I get is no file found or command not found.... I'll just stick with this for now until I backup the system then try some other NFS things, it seems the better of the two for L2L sharing.

---

