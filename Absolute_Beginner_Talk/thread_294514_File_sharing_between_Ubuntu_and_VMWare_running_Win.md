---
title: "File sharing between Ubuntu and VMWare running Win XP"
date: 2006-11-06
forum: Absolute Beginner Talk
---

### Post by Ziggy72 on 2006-11-06
I have VMWare running Win XP on my Ubuntu Ext3 partition. I would like to share files between the 2 operating systems. Is samba the answer? Does samba work with VMWare and Ubuntu? If it does, I can't get samba to work after hours of reading and trying many edits of samba.conf - whatever I do, Windows always tells me that it can't find the folder in Ubuntu which I want to use to share the files. Detailed help would be much appreciated.

---

### Post by XPuntu on 2006-11-06
That's a good idea Zig. I just booted up my virtual XP and yep, I can access my ext3 directory. 

I just set up my samba network a couple days ago and I'm no expert. But some things you need to do are set up the XP machine as a valid user in Ubuntu (System, administration, users and groups)

Also you need to make sure the file/directory is being shared. Maybe you're trying to share a file that can only have it's settings changed by root? I'm only sharing my /home directory at the moment. I'll see if I can find the how-to I used and post it here for you.

Good luck

---

### Post by docshawnc on 2006-11-06
Hi Zig -
    I'm running XP out of VM Server with Samba installed (also using ntfs -3g) and it works great - you'll be very pleased

---

### Post by Ziggy72 on 2006-11-06
Thanks to both of you - I'll persist... Actually, I think the problem really is that I haven't been able to set up a static ip address properly. How do I do this please?

---

### Post by Ziggy72 on 2006-11-06
XPuntu - What do I need to put in users and groups for my VMWare XP?
TIA

---

### Post by cobray on 2006-11-06
If you setup your Windows XP as a shared folder and you install SAMBA on ubuntu you should be able to see it from the Network Servers option in ubuntu

---

### Post by Ziggy72 on 2006-11-06
cobray - thank you..  But I'm very, very new to Ubuntu. How do I actually set up my Windows XP as a shared folder?

---

### Post by XPuntu on 2006-11-06
> **Ziggy72 said:**
> XPuntu - What do I need to put in users and groups for my VMWare XP?
TIA

When you install XP you have to set up a user (unless you're just running as admin - a security no-no). This is the user you have to add in Ubuntu along with a password. 

Then from your XP-VMware session, go to "My computer" and then "My network places" it should show up. Or try "View workgroup computers" and you'll hopefully see the Samba box. When you double click it, it will probably prompt you for a password.

I'm sorry I'm not an expert at this. I've only just installed Ubuntu a couple months ago.

---

### Post by Ziggy72 on 2006-11-06
Thanks to you all or trying to help. I still see nothing and I'm so confused and have wasted so much time that I'm going to give up. This sort of thing is one of the main pitfalls of Ubuntu. I'm not thick and I'm reasonably experienced in all Windows operations, but not having clear, concise, instructions as to how to  do things that need to be done in Ubuntu leads to complete frustration. A computer is supposed to serve the needs of the user and its efficient operation should not be restricted to computer nerds and/or good luck. Samba seems to me to be a particularly bad and obscure program to use and configure - if you doubt this, you only have to look at the dozens of posts in this forum and the hundreds in Google to know that soething, somewhere, is very wrong indeed with that program.

---

### Post by docshawnc on 2006-11-07
Hi Zig -
     Let's see if I can help you with a bit more detail.
1.  First, make sure your user name exists in both Ubuntu and xp (let's call it ziggy).
2.  Add ziggy as a Samba user:  sudo smbpasswd -a ziggy  (this will ask for your Ubuntu password and then prompt you for a samba password for ziggy - keep it the same to avoid confusion)
3.  Go to System, administration, shared folders and add a folder on the Ubuntu side that you want to share with the xp side.
4.  Go to the zp side and share one of the folders (or drives) on the VM with the Ubuntu side.  Do this by right clicking on the folder/drive and choose Sharing and Security.  Make sure ziggy has permission to read/write to this folder/drive.

Notes:  you may find it works best to turn simple file sharing off (do this by opening windows explorer, tools, folder options, view (and way at the bottom of that list, uncheck simple file sharing).

Also - you may need to restart windows to set the new permissions within XP.  You should now be able to see each machine in the others network.  In Ubuntu, go to Places, Network Servers.  You should see your home network - click until you see the folder/drive that you've shared on the XP side.  In XP, click My Network Places and you should see the home network as well.  Click until you see your Ubuntu machine and the folder you shared on the Ubuntu side.  You will need to enter your password to see it's contents.

Hope this helps.

---

### Post by Ziggy72 on 2006-11-08
docshawnc.... Very many thanks for taking the trouble to try to assist. I hope you may be able to walk me through this, because I am still having trouble. May we take this step by step?...

1. First, make sure your user name exists in both Ubuntu and xp (let's call it ziggy).
Done - I'm an administrator in xp with the name paul and I've added myself in Ubuntu (System -> Administration -> Users and groups) as paul.

2. Add ziggy as a Samba user: sudo smbpasswd -a ziggy (this will ask for your Ubuntu password and then prompt you for a samba password for ziggy - keep it the same to avoid confusion).
Done - with no problems.

3. 3. Go to System, administration, shared folders and add a folder on the Ubuntu side that you want to share with the xp side.
Done - but here's the first question I have:
  What should the share folder properties be? I have:
    Share with SMB and
    Name share
    All other options are blank. 

    The Windows sharing sessions are:
    Host description server (Samba Ubuntu) [inserted by Ubuntu]
    Domain/Workgroup MSHOME [this is the same as in XP]

    Wins Server.... of the 3 options, I have checked:
      Do not use Wins server

4. Go to the zp side and share one of the folders (or drives) on the VM with the Ubuntu side. Do this by right clicking on the folder/drive and choose Sharing and Security. Make sure ziggy has permission to read/write to this folder/drive.

In xp I right-clicked on the folder \Download and clicked the box which said Share this folder on the network and also the box which said Allow network users to change my files.

I then rebooted xp and restarted samba.

In Places -> Network servers in Ubuntu I now see the name Windows Network, but double-clicking results in a nothing at all.

In xp, there is no reference anywhere to my shared /home/paul folder in Ubuntu.

So any suggestions will be gratefully received. Thanks once again...

---

### Post by Incie83 on 2006-11-09
Dunno if this will help you, but I actually checked something along the lines of 'This PC is WINS server' in the Samba sharing options. Works perfectly after a samba restart and XP reboot.
And another suggestion, if you get this stuff working: use separate partitions/disks for OS and your personal files. Makes for faster disk access, easier management of back-ups and in my case it eliminated the need for a XP>Ubuntu share, I'm only sharing the other way round.

Good luck

---

### Post by Ziggy72 on 2006-11-09
Incie83 - thank you. The Wins server info is another part of the riddle solved. I'll keep trying...

---

### Post by Ziggy72 on 2006-11-09
Once again, thanks to all who have helped with this problem. I've now got a successful connection between the two operating systems. Maybe I'll use a separate thread to let people know what I did.

---

### Post by Ziggy72 on 2006-11-10
Details of how I solved the problem are at:
[http://www.ubuntuforums.org/showthread.php?t=296668](http://www.ubuntuforums.org/showthread.php?t=296668)

---

### Post by chefounet on 2006-11-28
that rocks !
worked fine with me, absolutely no problems.
Thanks !

---

### Post by rozhman on 2007-08-19
> **docshawnc said:**
> Hi Zig -
     Let's see if I can help you with a bit more detail.
1.  First, make sure your user name exists in both Ubuntu and xp (let's call it ziggy).
2.  Add ziggy as a Samba user:  sudo smbpasswd -a ziggy  (this will ask for your Ubuntu password and then prompt you for a samba password for ziggy - keep it the same to avoid confusion)
3.  Go to System, administration, shared folders and add a folder on the Ubuntu side that you want to share with the xp side.
4.  Go to the zp side and share one of the folders (or drives) on the VM with the Ubuntu side.  Do this by right clicking on the folder/drive and choose Sharing and Security.  Make sure ziggy has permission to read/write to this folder/drive.

Notes:  you may find it works best to turn simple file sharing off (do this by opening windows explorer, tools, folder options, view (and way at the bottom of that list, uncheck simple file sharing).

Also - you may need to restart windows to set the new permissions within XP.  You should now be able to see each machine in the others network.  In Ubuntu, go to Places, Network Servers.  You should see your home network - click until you see the folder/drive that you've shared on the XP side.  In XP, click My Network Places and you should see the home network as well.  Click until you see your Ubuntu machine and the folder you shared on the Ubuntu side.  You will need to enter your password to see it's contents.

Hope this helps.
Thank you!It's work fine for me.

---

