---
title: "[SOLVED] Writing to a share"
date: 2007-08-06
forum: Absolute Beginner Talk
---

### Post by NeillHog on 2007-08-06
After three weeks with Ubuntu (and Linux) the problems are getting a little more complicated but with all your help I am solving them - thanks!

On a NSLU2 server (unix - 192.168.178.29) I have a share set up with the name &#8220;music&#8221;. The user &#8220;neill&#8221; has read write access to this share

Typing the following line does not produce any errors
sudo mount -t smbfs //192.168.178.29/music /home/neill/nmusic -o username=neill,password=[my password]

In the fstab file I have the following line:
//192.168.178.29/music /home/neill/nmusic smbfs username=neill,password=[my password]

Using Konqueror I can see the directory at /home/neill/nmusic and I can also use Amarok to play the music on this directory.

The directory nmusic has 
- type: mounted samba share, 
- owner root &#8211; root
- Permissions: drwxr-xr-x

My problem is that I do not have write access to the files. I can read (play) them but I can not make any changes such as editing the track information. I guess that the problem is that the owner is root. How can I either change ownership to neill or give myself write rights.

Thank you

---

### Post by lgambett on 2007-08-06
sudo chmod -R 777 /home/neill/nmusic should do, changing permissions to rwxrwxrwx for the directory and all the files inside.

---

### Post by NeillHog on 2007-08-07
Thank you for the answer.

I had already tried that (although without the option -R) 

With or without the -R, I receive the message ": Permission denied" every time.

This is going to drive me mad. I have been working on it on and off for 2 weeks now.

Thanks anyway.

---

### Post by NeillHog on 2007-08-07
Some more information
ls -l in the /home/neill directory tells me the following
...
drwxr-xr-x 1 root  root     4096 2007-08-07 08:36 nmusic
....

so I now KNOW that I can not write to the files but I still don't know how to change that.

Sorry!

Neill

---

### Post by hyper_ch on 2007-08-07
```

sudo chown neill.neill /home/neill

```

---

### Post by NeillHog on 2007-08-07
Thank you for that idea but that is also something that I have already tried

neill@NeillsPC:~$ sudo chown neill.neill /home/neill/nmusic
Password:
chown: changing ownership of `/home/neill/nmusic': Operation not permitted
neill@NeillsPC:~$

Something really bad is going on here and I am just not up to solving it. I am sure that in a year I will laugh about EASY thinks like this but right now - Aaarrgghh!

Thank you for the suggestion though.

Why is root the owner? Everything else under "/home/" belongs to me.

Going slowly mad here :-)

---

### Post by NeillHog on 2007-08-07
It doesn't work under Windows either. I mean that I can not write to the share under Windows either.

So I will take my questions off to the NSLU2 forums.

Thanks anyway.

---

### Post by DugieHowsa on 2007-08-07
Try using cifs instead of smbfs.

I had been having trouble mounting a Windows Share. I tried to mount using smbfs. I tried to mount using cifs. In the end, some one showed me this link:

[https://bugzilla.samba.org/show_bug.cgi?id=1920](https://bugzilla.samba.org/show_bug.cgi?id=1920)

Summary: "smbfs is unmaintained and known to be severely broken." That was posted back in 2004, so needless to say probably not much has happened with smbfs in the last 3 years.

So here is the man page for mount.cifs that lists all the options:

[http://www.die.net/doc/linux/man/man8/mount.cifs.8.html](http://www.die.net/doc/linux/man/man8/mount.cifs.8.html)

Many people here have also listed many good posts, giving several good examples, on how to properly utilize cifs:

[http://ubuntuforums.org/showthread.php?t=288534](http://ubuntuforums.org/showthread.php?t=288534)

This post solved the particular problem I was having:

[http://ubuntuforums.org/showthread.php?t=483184](http://ubuntuforums.org/showthread.php?t=483184)

In summary: USE CIFS. DO NOT USE SMBFS.

---

### Post by NeillHog on 2007-08-12
Thank you for your help.
I still can not reach the NSLU2 share but you have solved another problem that I had with not having write access on a share on a XP PC.

Using 
//XP1/tracks /home/neill/tracks cifs guest,rw,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0
I now have read and write access to this share :-)

---

### Post by bwtranch on 2007-08-12
Yeah, I know it can be a little frustrating. i have just got to the point that I know enough to help other people. But, it's good. You will notice that I am a testing user now and i have learned a lot. Every problem is a little different and I don't know everything. Nobody does. But, we usually work together and solve about, I don't know, I'd say 95%. When I get my buds around you can bet we are going to kick some ***. But, you know what? my buds aren't around right now. It's like 4:20 in the morning here in the central time zone. I can't beleive that I'm still up. but, I am.

So, I'll hang. I don't really understand what you are trying to do. I am a testing user and I have a backup computer in case something goes wrong. Please tell me what to do and I will try to figure out your problem or replicate it and post. OK? I have been asking these people to do this all night and not one person has done it because they don't understand that I am a testing person and I want a problem. They just want to get rid of their problem. 

I think I can narrow it down for them and crytalize it to two things. Dual boot and USB.

I don't really care about the spelling mistake. But, that is what it is dual boot and usb the first can be fixed by users the second has to be fixed by programmers.

---

### Post by bernied on 2007-08-12
What firmware are you running on the slug?

---

### Post by NeillHog on 2007-08-12
A bit later: 
Following the instructions at [http://www.nslu2-linux.org/wiki/Optware/Samba](http://www.nslu2-linux.org/wiki/Optware/Samba) I installed samba on the Slug, and copied the samba config file to the new directory. I then installed nano on the Slug and opened /opt/etc/samba/smb.conf file. I saw that for the share [music] read only was set to yes -

[music]
valid users=@"administrators",@"neill",@"everyone"
comment=All our music
path=/share/hdd/data/music/
read only=yes
write list=@"administrators",@"neill"

so I set it to no. After that everything worked but I carried out the other steps as well.

Even after a restart of the NSLU2 it worked!
Problem Solved (maybe) after only three weeks!

Thanks everyone for your patience and teaching me a lot.

Neill

---

### Post by NeillHog on 2007-08-12
Bernried wrote:
> What firmware are you running on the slug?

Logging in with Telnet I receive the following:
Welcome to Unslung V2.3R63-uNSLUng-6.8-beta
   ---------- NOTE: THIS SYSTEM IS CURRENTLY UNSLUNG ----------
BusyBox v0.60.4 (2005.03.22-06:52+0000) Built-in shell (ash)

bwtranch wrote:
> I don't really understand what you are trying to do.
I am (was) trying to access a share on an unslung NSLU2 (unix) from my Ubuntu system.
After three weeks of trying I would say that the problem was not Ubuntu.

The tip about using cifs helped me gain write access to a windows XP share that I was also having a problem with.

The entry in the smb.conf saying read only=yes was probably at the root of my problems there although not knowing how to mount with a username didn't help.

As I said. I have learnt a lot and maybe one day I will also understand more than 50% (dream on).

Neill

---

