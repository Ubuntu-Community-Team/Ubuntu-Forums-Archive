---
title: "Access Ubuntu from a Windows PC"
date: 2006-09-22
forum: Absolute Beginner Talk
---

### Post by Contrid on 2006-09-22
Hi everyone,

I need some urgent help on how to access my Ubuntu box sitting right next to me from my Windows PC.

I've installed xampp apache server with php, mysql, etc... on my Ubuntu box, and I can successfully access that via my browser using [http://contridi/](http://contridi/) (where "contridi" is the computername of my Linux box)

These two computers are on a LAN through a router.

So when I go to "My Network Places" on Windows, and enter the workgroup (MSHOME), I see the following :

[IMG]http://www.tribulant.com/IMG/mshome.png[/IMG]

When I double click on the Linux box which is "contridi" it asks me for a username and a password. I've tried my main account username and password, but it doesn't seem to work.

[IMG]http://www.tribulant.com/IMG/login.png[/IMG]

The same goes for FTP. I can access the Linux computer from my Windows computer with my FTP application, but it seems like I don't have permissions to do anything.

Could someone please be so kind to help me with this issue.
It will be greatly appreciated, since I really want to get this set up.

Thanks in advance for any advice.

All the best,
Contrid.

---

### Post by jslatton on 2006-09-22
Have you tried accessing using root?

I assume you want to just access files?  You'll need some samba shares setup in order to see any files upon connection.

If you just want to access the computer remotely (kinda like rdp), you can use a program called freenx.  It's by far the best remote utility out there.  I've had great success with it on many different linux platforms.  It has a windows client.

- Jeremy

---

### Post by Contrid on 2006-09-22
I'm not sure what the root details are.

I've shared a drive with Samba, but I don't see it anywhere. All I see is the computer in "My Network Places" but it's prompting for a username and password. I've tried everything...

There has to be a way for me to grant permissions somewhere.

---

### Post by hyper_ch on 2006-09-22
Well, I'm using NAT and have WinXP in VmWare and I also installed sambe:

sudo apt-get install samba

and then I edited the smb.conf

sudo nano /etc/samba/smb.conf

and added following configuration

> 
[global]
workgroup = WORKGROUP
security = share

[appz]
comment = Appz
path = /home/appz
read only = Yes
guest ok = Yes

[exchange]
comment = Exchange
path = /home/exchange
read only = No
guest ok = Yes


I know this has no security things either but right now I can access the samba shares from my winxp virtual server...
this should give you enough to start sharing... but then you still have to look about securing that thing... if you are in a lan where you can trust all others that should be fine I think... but I'm no expert on samba... I just started playing around with it yesterday....

Oh, and don't forget to:

sudo /etc/init.d/samba restart

---

### Post by siman on 2006-09-22
Maybe the easies thing for you is this:

install a ssh server on your linux box and access it from windows via a programm like winscp.

1) sudo apt-get install openssh-server
2) get winscp running on your win machine

---

about the root thing: per default the root account is disabled in ubuntu. search for "enable root access" or "set root password" to find threads about that... once your root account is active, you can login as root to access all files (dangerous...) or as your normal user

---

### Post by Contrid on 2006-09-22
I never saw these messages/posts...but in the meantime I figured out how to get it to work after quite alot of reading all over the net.

The solution was to install SSH on the Linux box and then simply use SFTP with SSH2 support though my FTP application (CuteFTP...or anything for that matter)

It's totally amazing!!! I can access both PC's from one another, and write and read both ways. Who said that you can't write to NTFS from Ubuntu??? Now you can! ;) Simply use SSH.

I'm a happy man now. I have my XAMPP Apache server installed on my Linux box...so all my developments get run from there. PHP, MySQL, etc...

Since I haven't been able to install and configure SMTP on Linux...I use my Windows SMTP server, which is running through PostCast SMTP server software.

What a breeze. Thanks for the responses guys...the people around here are always helpful and friendly!!! ;)

Question :
Will all of this still work if I install Windows x64 on my one PC? The only reason why I removed Win x64 is because of SMTP, FTP, MySQL, PHP and Apache issues locally. (I can now run all of that through my Ubuntu box)

---

### Post by chrisfay on 2006-09-22
I had the same problem; couldn't access my Linux shares from windows and kept getting the same username and password box like you. It was as simple as adding a samba user:

smbpasswd –a user

Then all was good.....

---

### Post by Contrid on 2006-09-22
> **chrisfay said:**
> I had the same problem; couldn't access my Linux shares from windows and kept getting the same username and password box like you. It was as simple as adding a samba user:

smbpasswd &#8211;a user

Then all was good.....

Could you be so kind to be more specific on how you did that?

I have http:// access and ftp:// access...but I still cannot access the Linux box from "My Network Places"

It would be really nice if you could pass some instructions.

Thanks alot! ;)

---

### Post by lawcox on 2006-09-22
I had the exact same difficulty at first, and adding a Samba user solved it.  A search on the Ubuntu wiki probably has the answer, but here is a quick article from a google search on it:
[http://linux.about.com/od/ubusrv_doc/a/ubusg33t09.htm]("http://linux.about.com/od/ubusrv_doc/a/ubusg33t09.htm")

---

### Post by crokett on 2006-09-22
> **Contrid said:**
> 
I have http:// access and ftp:// access...but I still cannot access the Linux box from "My Network Places"


You need to have Samba server installed and configured.  There is tons of information on the internet to do this.

---

### Post by chrisfay on 2006-09-22
> Could you be so kind to be more specific on how you did that?

Open up a terminal prompt in your Ubuntu pc and do the following:

Make sure samba is running:

```
ps aux | grep samba
```
You should see an instance of the daemon running; if no output, then you need to start it using:
```
sudo /etc/init.d/samba start
```

Once you've verified that Samba is running, you need to create a samba user that you can access your Ubuntu box with from Windows. To do that, type:

```
smbpasswd –a user
```
Replace 'user' with the Linux username you log into your Ubuntu system with. Then create a password per the following prompts.

If you use the same username for samba that you log into Windows with then authentication will occur automatically; otherwise you will have to enter the info into that dialog box you get when trying to access your share from Network Places.

This should allow you to access shares on your Ubuntu pc through Windows Network Places.

---

### Post by ubbu on 2006-09-23
I tried the following all went OK but it didn't ask me a password line for the user ? ANy idea why or how will I complete it

or how can I allow any connection to my ubuntu shared folders from any computer on the network without asking username or password ?

thanks in advance

---

