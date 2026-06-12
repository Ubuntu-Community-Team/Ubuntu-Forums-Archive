---
title: "Windows' shared folders / Samba / Xbox Media Center"
date: 2007-11-21
forum: Absolute Beginner Talk
---

### Post by mikebeecham on 2007-11-21
Hi Guys...after 2 days working on this, I am at a loss and hope you may be able to help me:

For a long time, I have been using Windows on my PC upstairs.  In this PC I have two HDDs.  My first HDD (Primary) has two partitions...Windows and Linux Gutsy Gibbon.  My second hard drive (Media) contains all my media, such as movies, mp3s, etc contained within a number of shared folders.  These folders are called:

[LIST]
[*]MP3s
[*]TV Shows
[*]Movies
[*]My Pictures
[*]Clips
[*]Podcasts
[/LIST]

Downstairs I have my xbox media center set with a static IP address, and it has logged all of these folders , so that when I click for example, the 'Music' Button, it will know to look inside the shared folder "MP3s".  All is well when I am logged into Windows.

However, when I am logged into Linux, the xbox media center cannot access any of the shared folders.  I have been told that I need to set up samba...but I am a little confused. When logged into Linux, I can already see, add, remove and edit the shared media folders (In linux it's path is /media/hdb1)...so I know that Linux is able to access the shared folders.

So, I am at this point where I can see those folders within nautlius, but the xbox media center cannot access them.  I have been through a small number of different things, such as installing firestarter and opened the 5 IP address range in it...so I know the firewall is not the issue.

I am not at the stage of being told that I need to configure them in Samba...but I really dont know where to start.  I have been into Windows and taken note of all relevant computer information, such as windows login details, computer name, full computer name and workgroup name....

Can anyone help?



Thanks

---

### Post by renzokuken on 2007-11-21
in ubuntu click on System - Admin - Shared Folders.........use this to share the folders. it will install samba automatically for you and configure your smb.conf to share the appropriate folders

---

### Post by mikebeecham on 2007-11-21
I have been in there, and I can only get as far as hdb1...I cannot progess further than that to the actual foldes I want.

---

### Post by jonandrews on 2007-11-21
I've put my simple guide to integrating Ubuntu PC's into a wired Windows home network 

onto a website:

[www.europe.eclipse.co.uk/Ubuntu/](www.europe.eclipse.co.uk/Ubuntu/)


Let me know if it is helpful.

---

### Post by BassKozz on 2007-11-21
> **jonandrews said:**
> I've put my simple guide to integrating Ubuntu PC's into a wired Windows home network 

onto a website:

[www.europe.eclipse.co.uk/Ubuntu/](www.europe.eclipse.co.uk/Ubuntu/)


Let me know if it is helpful.
I was having the same issue, your guide helped and now it's working :D
Just a quick question thou... do I need to enter```
sudo smbpasswd -L -a logname
sudo smbpasswd -L -e logname
```
Everytime I reboot?

---

### Post by mikebeecham on 2007-11-21
I have tried to do this as best as I can, but I think I have narrowed the issue down to my smb.conf.

I have provided a link to my SMB...wouild someone mind looking at this and telling me where I am going wrong?


[http://pastebin.com/m20d04651](http://pastebin.com/m20d04651)


Thanks very much





Mike

---

### Post by bijanafx on 2007-11-21
i have a similar setup. don't know if this will help, but i have to choose Workgroup (SMB) Network as the media source in XBMC, not SMB Network Share......

---

### Post by Bigbird999 on 2007-11-21
Is your shared media drive mounted in Linux?? If not, can you mout it?

BB

---

### Post by mikebeecham on 2007-11-22
BigBird...

My Media drive is mounted when I boot into linux...I cant seem to unmount as it tells me I dont have the privileges to do that for some reason?

---

### Post by Spirale23 on 2007-11-22
Guys, 
Check this one ! 

your xbox don't really need to be in static IP actually ... 

i'm on it too, little troubles with my samba shares ...

---

### Post by Spirale23 on 2007-11-22
oops  i've forgot the link : [http://ubuntuforums.org/showthread.php?t=438577&highlight=xbmc&page=2](http://ubuntuforums.org/showthread.php?t=438577&highlight=xbmc&page=2)

---

