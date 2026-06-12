---
title: "Media sharing in linux"
date: 2008-01-31
forum: Absolute Beginner Talk
---

### Post by sayakb on 2008-01-31
IN Windows, I used Windows Media Player 11 to share media on LAN and play content from other computers w/o downloading them -- Just buffering and playing. How do I do that on Linux.. I enabled DAAP sharing but that seems to be sharing my music only (though I never actually tried it, just read the docs).. I am using gnome desktop, and I mainly use Banshee or rhythmbox.

---

### Post by LowSky on 2008-01-31
try a program called VLC it can play every type of media with little to no issue, and can even be used for streaming media. (also availible for Windows if yo want to give it a try) UIt in ubuntu's repos...

As for the content, is the media in question being stored on a Windows Computer/Network? If yes you will need to get a program called SAMBA that can handle Windows' SMB network.

---

### Post by sayakb on 2008-01-31
> **LowSky said:**
> try a program called VLC it can play every type of media with little to no issue, and can even be used for streaming media. (also availible for Windows if yo want to give it a try) UIt in ubuntu's repos...

As for the content, is the media in question being stored on a Windows Computer/Network? If yes you will need to get a program called SAMBA that can handle Windows' SMB network.

I use VLC for my video files. I have SAMBA installed. I am trying to access files from a Windows computer.. (I am the only one with linux here :( )

---

### Post by sayakb on 2008-01-31
Also, I am a bit dumb so help me out with this.. While sharing media with Windows, all I did is went to sharing, and checked on "Share my media".. To access other's media, I opened "My Network Places" and waited for the sharing server to be discovered. As the icon read "Media sharing on MADDY" (where MADDY is my friend's PC on which the songs are stored which I would be accessing), I just double clicked on the Icon and the name MADDY showed up in my Windows Media Player Library. I could play all files normally as I could on my own library...
The question: How do I do this with VLC since I dont know the port numbers etc..

---

### Post by jaytek13 on 2008-01-31
Are you trying to host these files on an internal network?

---

### Post by sayakb on 2008-01-31
> **jaytek13 said:**
> Are you trying to host these files on an internal network?

Well, not actually.. Hosting would be secondary to me than accessing other PCs music resources. I am trying to access music stored on other PCs in my network.. But they are all on Windows.

---

### Post by white3454 on 2008-01-31
If you have SAMBA installed, open VLC, go to File Open or Open Directory.  There is a text field where you can type or paste the direct path to the share you are trying to access.  I'm assuming your trying to open mp3's and such...

---

### Post by jaytek13 on 2008-01-31
> **LinuxIsInnovation said:**
> Well, not actually.. Hosting would be secondary to me than accessing other PCs music resources. I am trying to access music stored on other PCs in my network.. But they are all on Windows.

ah well... you would first create a mount point

mkdir /home/you/mountpoint

and then you would mount the windows share to the mountpoint you just created

mount -t smbfs -o uname=uname,passwd=passwd //computer/share /home/you/mountpoint

where uname = the windows username, passwd = the windows password, computer = the hostname of the computer, share = the file that they are hosting (music, for example)

Of course technically if you have samba installed you should just be able to go to places->network and see everyone's computer on there and the files they are sharing. And technically everything I just posted probably won't work if you can't see the computers on the network.

---

### Post by sayakb on 2008-02-01
> **jaytek13 said:**
> ah well... you would first create a mount point

mkdir /home/you/mountpoint

and then you would mount the windows share to the mountpoint you just created

mount -t smbfs -o uname=uname,passwd=passwd //computer/share /home/you/mountpoint

where uname = the windows username, passwd = the windows password, computer = the hostname of the computer, share = the file that they are hosting (music, for example)

Of course technically if you have samba installed you should just be able to go to places->network and see everyone's computer on there and the files they are sharing. And technically everything I just posted probably won't work if you can't see the computers on the network.

```

glade@Muzic-Jukebox:~$ sudo mount -t smbfs -o uname=glade,passwd=iamalone //MUZIC-JUKEBOX/music /home/glade/test/
mount: wrong fs type, bad option, bad superblock on //MUZIC-JUKEBOX/music,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

glade@Muzic-Jukebox:~$ 

```
What to do now..??

---

### Post by kwacka on 2008-02-01
Repeat the command, then when you get the error message try the suggestion in the last line: type dmesg | tail.

This should give you an idea of the problem, e.g. is samba installed?

---

### Post by sayakb on 2008-02-02
> **kwacka said:**
> Repeat the command, then when you get the error message try the suggestion in the last line: type dmesg | tail.

This should give you an idea of the problem, e.g. is samba installed?

```
root@Muzic-Jukebox:~# sudo mount -t smbfs -o uname=glade,passwd=iamalone //MUZIC-JUKEBOX/music /home/glade/test/
mount: wrong fs type, bad option, bad superblock on //MUZIC-JUKEBOX/music,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

root@Muzic-Jukebox:~# dmesg | tail
[  737.224307] Inbound IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:60:6e:cf:0c:e3:08:00 SRC=192.168.14.32 DST=192.168.14.255 LEN=202 TOS=0x00 PREC=0x00 TTL=128 ID=35 PROTO=UDP SPT=138 DPT=138 LEN=182 
[  737.259602] Inbound IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:60:6e:cf:0c:e3:08:00 SRC=192.168.14.32 DST=192.168.14.255 LEN=78 TOS=0x00 PREC=0x00 TTL=128 ID=37 PROTO=UDP SPT=137 DPT=137 LEN=58 
[  738.009017] Inbound IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:60:6e:cf:0c:e3:08:00 SRC=192.168.14.32 DST=192.168.14.255 LEN=78 TOS=0x00 PREC=0x00 TTL=128 ID=38 PROTO=UDP SPT=137 DPT=137 LEN=58 
[  738.196537] Inbound IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:0f:ea:97:da:ca:08:00 SRC=192.168.14.78 DST=192.168.14.255 LEN=244 TOS=0x00 PREC=0x00 TTL=128 ID=9730 PROTO=UDP SPT=138 DPT=138 LEN=224 
[  738.757775] Inbound IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:60:6e:cf:0c:e3:08:00 SRC=192.168.14.32 DST=192.168.14.255 LEN=78 TOS=0x00 PREC=0x00 TTL=128 ID=39 PROTO=UDP SPT=137 DPT=137 LEN=58 
[  741.522082] Inbound IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:60:6e:cf:0c:e3:08:00 SRC=192.168.14.32 DST=192.168.14.255 LEN=202 TOS=0x00 PREC=0x00 TTL=128 ID=41 PROTO=UDP SPT=138 DPT=138 LEN=182 
[  741.549842] Inbound IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:60:6e:cf:0c:e3:08:00 SRC=192.168.14.32 DST=192.168.14.255 LEN=78 TOS=0x00 PREC=0x00 TTL=128 ID=43 PROTO=UDP SPT=137 DPT=137 LEN=58 
[  742.298593] Inbound IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:60:6e:cf:0c:e3:08:00 SRC=192.168.14.32 DST=192.168.14.255 LEN=78 TOS=0x00 PREC=0x00 TTL=128 ID=44 PROTO=UDP SPT=137 DPT=137 LEN=58 
[  743.047387] Inbound IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:60:6e:cf:0c:e3:08:00 SRC=192.168.14.32 DST=192.168.14.255 LEN=78 TOS=0x00 PREC=0x00 TTL=128 ID=45 PROTO=UDP SPT=137 DPT=137 LEN=58 
[  756.758995] smbfs: mount_data version 1835101813 is not supported
root@Muzic-Jukebox:~# 
```

And yes, Samba is installed.. Still aint workin good :(

---

