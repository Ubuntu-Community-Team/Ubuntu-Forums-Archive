---
title: "first server attempt some snags"
date: 2008-03-15
forum: Absolute Beginner Talk
---

### Post by Jnetty99 on 2008-03-15
I tried my first attempt to setup Ubuntu Server on a Dell Dimension 2400 Celeron 2.2ghz, 256mb ram, 40gb drive. Trying to setup a file server first, then hopefully torrent, ftp server, and print server. 
During the initial install I installed LAMP and OpenSSH only. I then used the following tutorial to try to setup Samba to make a simple home server but hit some snags. [http://howtoforge.com/ubuntu-home-fileserver]("http://howtoforge.com/ubuntu-home-fileserver")

I setup a static IP address, then it tells me to edit the /etc/hosts, then to do this command
echo server1.example.com > /etc/hostname
But when i do that it gives me access denied ( did put sudo first)
I ignore that and went on. 
I got to the point to adding users for samba
smbpasswd -a family but when ask for the password it gives me access denied. 

My other systems can see the server but I can't login obviously. I looked up several setup samba tutorials, I guess everyone has different methods. I just want to setup a way to have shares and hopefully be available by everyone at home without having to actually login.

---

### Post by Nythain on 2008-03-15
to resolve most of your permission denied problems you are going to need sudo
sudo echo server1.example.com > /etc/hostname

and smbpasswd might need a sudo in front of it also, but im not sure

as for allowing people to access without logging in... in your /etc/samba/smb.conf there's a line that looks like
security = user
change it to
security = share
that should allow people to access without needing to log in

---

### Post by Jnetty99 on 2008-03-15
> **Nythain said:**
> to resolve most of your permission denied problems you are going to need sudo
sudo echo server1.example.com > /etc/hostname

and smbpasswd might need a sudo in front of it also, but im not sure

as for allowing people to access without logging in... in your /etc/samba/smb.conf there's a line that looks like
security = user
change it to
security = share
that should allow people to access without needing to log in

I did sudo for everything and still access denied. i'll check the security settings thanks.

---

### Post by Jnetty99 on 2008-03-17
I'm going to start all over again. I'll be practicing on VMware at work before attempting again to do it on the actual machine.

If I want to make a File server, FTP, Torrent, and Print Server all-in-one, what order should I follow to install? I need LAMP for the FTP and Torrent correct? 

Also confused about SAMBA. I see so many tutorials but they all differ on installing SAMBA. They say install samba, smbfs, smbclient, and other stuff. Don’t I just need the main samba part or do I need all this other little parts? 

Your suggestions are appreciated.

---

### Post by Nythain on 2008-03-17
you dont necessarily need LAMP for ftp and bittorrent... LAMP = Linux and Apache MySQL PhP or some jazz... so if you dont need a webserver, or have a dire need for an actuall sql server, then lamp isnt really for your

on the samba note
smbclient = samba client and is installed by default in ubuntu i believe, no need to add it
samba = samba metapackage<?> (not sure if its actually a metapackage, but for the sake of understanding, ill explain it as one) and will install the samba server, im pretty sure it also installs along with it smbfs (for mounting samba shares and whatnot) and along with smbfs you will also get cifs (a samba alternative to mounting samba shares and whatnot)

thats abotu all i got right now... good luck to you, i hope you eventually get it
just ask if you have any more questions or problems

---

### Post by Jnetty99 on 2008-03-17
> **Nythain said:**
> you dont necessarily need LAMP for ftp and bittorrent... LAMP = Linux and Apache MySQL PhP or some jazz... so if you dont need a webserver, or have a dire need for an actuall sql server, then lamp isnt really for your

on the samba note
smbclient = samba client and is installed by default in ubuntu i believe, no need to add it
samba = samba metapackage<?> (not sure if its actually a metapackage, but for the sake of understanding, ill explain it as one) and will install the samba server, im pretty sure it also installs along with it smbfs (for mounting samba shares and whatnot) and along with smbfs you will also get cifs (a samba alternative to mounting samba shares and whatnot)

thats abotu all i got right now... good luck to you, i hope you eventually get it
just ask if you have any more questions or problems

yeah I don't need a Webserver. I thought Torrent needed MySql or PHP to access their menu through an online gui at another computer. I been just using different tutorials.

---

### Post by Nythain on 2008-03-17
ugh, thats an awful easy but complicated way of just administer bittorrent...
im assuming you are refering to fluxtorrent, wich so far has been about the only web based remote gui torrent client i've found for linux...

i personally run rtorrent (command line application with an actual interface) on a "screen", then i can detatch the screen, and remotely connect from anywhere via ssh (wich you definately need to look into installing for a server, in fact, the ubuntu-server edition might come with it already installed) and re-attatch the screen there...

screen is a lifesaver in command line environments and remote administration... with popular uses invovling rtorrent and irssi (a command line irc client)

for fluxtorrent you will probably need an sql server and php though, so lamp might be the way to go on that front... it really all boils down to what you need to run... see, we're figurin stuff otu for ya :)

---

### Post by Jnetty99 on 2008-03-17
> **Nythain said:**
> ugh, thats an awful easy but complicated way of just administer bittorrent...
im assuming you are refering to fluxtorrent, wich so far has been about the only web based remote gui torrent client i've found for linux...

i personally run rtorrent (command line application with an actual interface) on a "screen", then i can detatch the screen, and remotely connect from anywhere via ssh (wich you definately need to look into installing for a server, in fact, the ubuntu-server edition might come with it already installed) and re-attatch the screen there...

screen is a lifesaver in command line environments and remote administration... with popular uses invovling rtorrent and irssi (a command line irc client)

for fluxtorrent you will probably need an sql server and php though, so lamp might be the way to go on that front... it really all boils down to what you need to run... see, we're figurin stuff otu for ya :)

yeah TorrentFlux. I'll check out the one you use rtorrent. now the first thing is getting my file server portion working. So i'll start with Samba first and move in steps. 

thanks

---

### Post by Nythain on 2008-03-17
ok... sounds like a plan... im at work right now, but when i get home tonight (a lot later) i can work on finding some solid samba guides, and post my smb.conf to possibly help get ya started a bit

---

### Post by lavinog on 2008-03-17
> **Jnetty99 said:**
> 

I setup a static IP address, then it tells me to edit the /etc/hosts, then to do this command
echo server1.example.com > /etc/hostname
But when i do that it gives me access denied ( did put sudo first)


I think the greater than sign messes up sudo
it tells sudo to redirect the itself to /etc/hostname instead of echo...since it hasn't switched to the superuser yet it fails.

one work around is to do 
```
sudo su
echo server1.example.com > /etc/hostname
exit

```

---

### Post by Jnetty99 on 2008-03-17
> **Nythain said:**
> ok... sounds like a plan... im at work right now, but when i get home tonight (a lot later) i can work on finding some solid samba guides, and post my smb.conf to possibly help get ya started a bit

I got something going, very simple using several sites as reference. 
Installed Samba only. 
added two folders in /Home/Me/ 
backup and music folder
gave them 777 permissions

stopped the samba service and renamed the original file and created a new one.
opened smb.conf and added the following using another tutorial as reference.

[global] 
workgroup = workgroup
server string = Samba Server
security = share
name resolve order = lmhosts hosts

[Backup]
path = /home/me/backup
force user = me
force group = users
public = yes
writable = yes
create mask = 0777
directory mask = 0777

[Music]
path = /home/jnetty/music
force user = me
force group = users
public = yes
writable = yes
create mask = 0777
directory mask = 0777

this is showing me both the Backup and Music folder and anyone can access them on the local network. So got some baby steps going.

---

### Post by Jnetty99 on 2008-03-18
I installed Webmin today and now i'm able to access a web gui to access the Samba server. 

Webmin seems pretty cool, does anyone have problems against using it?

---

### Post by Jnetty99 on 2008-03-26
I think I finally have got pass my first hurdle of setting Samba for my home. 
I was having problems how to share folders properly. 

I created some folders in my /home/me/ directory 
music, pictures, documents. 

I then sudo smbpasswd -a me and gave a password. some tutorials say to go to the smbusers and add the user in there also. I didnt do that, should i? 
I then modified the smb.conf and changed workgroup name, activated security = user. 
added the following to share the folders

[music]
    comment = music files
    path = /home/me/music
    browseable = yes
    valid users = me
    writable = yes

I was able to access the shares but I was not able to write to them. I finally released by using ls -la that the folder i created had the root ownership because i did all of this as root. I deleted the folder and recreated them with my normal login account and now I can write to them. I hope this is proper procedure. 

Now i'm going to try to figure out FTP or rtorrent. rtorrent is very confusing after getting it install. can't find a very simple tutorial on how to use it.

---

### Post by Bachstelze on 2008-03-26
[http://kmandla.wordpress.com/2007/05/02/howto-use-rtorrent-like-a-pro/](http://kmandla.wordpress.com/2007/05/02/howto-use-rtorrent-like-a-pro/)

---

