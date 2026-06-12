---
title: "samba problems"
date: 2007-03-19
forum: Absolute Beginner Talk
---

### Post by dynacrylic on 2007-03-19
I installed samba and configured the workgroup in /etc/samba/smb.conf. Samba starts but when I try to access the share from another computer I'm not able to read or write to the share.  What am I overlooking?

thanks for the help in advance...

---

### Post by LanDan on 2007-03-19
configuring samba is very easy, as soon as you know which of the thousand options to choose  ;)

can you run "testparm" in the terminal and show us here?

---

### Post by dynacrylic on 2007-03-19
> **LanDan said:**
> configuring samba is very easy, as soon as you know which of the thousand options to choose  ;)

can you run "testparm" in the terminal and show us here?

Load smb config files from /etc/samba/smb.conf
Processing section "[printers]"
Processing section "[print$]"
Loaded services file OK.
WARNING: passdb expand explicit = yes is deprecated
Server role: ROLE_STANDALONE
Press enter to see a dump of your service definitions

---

### Post by DoorGunner on 2007-03-19
WARNING: passdb expand explicit = yes is deprecated means nothing to the samba user. Just ignore this.... .

[http://www.enterprisenetworkingplanet.com/netsysm/article.php/3621876](http://www.enterprisenetworkingplanet.com/netsysm/article.php/3621876)

I think this person said the same thing about this warning.

This site might help a bit depending on what you want to do. It was intended to help install printers on ubuntu on a network where windows clients reside.

---

### Post by scxtt on 2007-03-20
if you've got samba running in ubuntu and you're trying to access it from windows, or anywhere else running a smb-client - you have to make sure you've enabled an account to connect w/ on the samba server ...

basically, issue the following command on the ubuntu samba-server and use it to access the samba shares: **sudo smbpasswd -a $USERNAME**

---

### Post by DoorGunner on 2007-03-20
dynacrylic what is the purpose of you samba..... Maybe i missed it but what is the Samba config for: a server for your computer part or is there a server you wish to connect to? Could you elaborate on the set up you wish to use. Are there windows machines involved? I am just trying to understand where you are going so I can help.

---

### Post by Vandorius on 2007-03-20
How do i edit /etc/samba/smb.conf and what to do next to share files between XP and Ubuntu?

---

### Post by DoorGunner on 2007-03-20
to edit samba config

> 
sudo cp /etc/samba/smb.conf /etc/samba/smb.conf.backup
sudo gedit /etc/samba/smb.conf

replace everything with this to start

> [global]
	workgroup = Your_Workgroup_Name
	netbios name = Netbios_Name_Here
	server string = Our Family Server
	hosts allow = 192.168.1.
	security = share
	load printers = yes
	printing = cups
	printcap name = cups

[share1]
	path = /media/share/sharedstuff
	comment = files for everyone
	read only = no
	browseable = yes
	guest ok = yes
	writable = yes

This is a basic connection that will allow you to share on your computer.

change the following values:
workgroup = to the name of your workgroup
netbios name = to reflect your net bios name (computer name)
server string = coment on what you might like to say as a comment.
allow hosts should be set to what ever your router is set to in the example i used 192.168.1 Leave the last digit or digits out

note: My Share file is located on another partition. you will see this in [share1] Path

notice that security = share. you can change this later if you wish. For now it is a good way to view if you samba works.

> sudo /etc/init.d/samba restart
-------------------------------------------------------------------------------------------------
once you have done this you go to the XP computer

My Network Places

you should have your share 1 file listed 
if not try view workgroup computer (listed on the right)

If you have this then go on to the next step if not repost
-----------------------------------------------------------------------------------------------------

If you have your samba server showing up in My Network Places you can then go to 
My Computer > tools > Map Network Drive
Pick an available drive...... I use s drive for mine. 
then browse for the folder you wish to use or Just type in \\YOUR_NETBIOS_NAME\FILE TO SHARE
mine looks something like this \\DoorGunner\share 1

Your xp machine will now have your share mounted on My Computer.

That should get you going. 

Where is your printer located. On the Ubuntu machine or XP?

---

### Post by Vandorius on 2007-03-20
Sorry for the long time to respond. The priner is set to my comp by default and it works from XP machine too like a charm. But with sharring its currently like this... I did what u told me (trippple checked to be shure its right). In my network places i dont see any file shared from Ubuntu PC. But if i go and click microsoft win network it displays Mshome if i click it i see my comp but if i click it displays warning u might not have permissions to use the network resource.

If i go to map and do it like u said it prompts me for username and password..... ihave tried the same that i have for ubuntu but doesnt work.

---

### Post by DoorGunner on 2007-03-20
Sorry My Computer and My Network Places from XP .... not Ubutnu. It means your getting connection. 

You need to sudo chmod 777 YOUR_FILES_YOU_ARE_SHARING. Once you do that than restart samba again. It may take a min or so for MS to catch up with the change.

---

### Post by Vandorius on 2007-03-20
Nope doesnt work. Just not my day or something. Thanks alot for your effort guys.

---

### Post by clapper65 on 2007-03-20
Doorgunner, Thanks for the basic smb.conf file.  That's exactly what I needed to get started.  I'm sharing files with my WinXP machine and using my Linux printer from XP.

---

### Post by dynacrylic on 2007-03-20
> **scxtt said:**
> if you've got samba running in ubuntu and you're trying to access it from windows, or anywhere else running a smb-client - you have to make sure you've enabled an account to connect w/ on the samba server ...

basically, issue the following command on the ubuntu samba-server and use it to access the samba shares: **sudo smbpasswd -a $USERNAME**

Rock on! thanks so much.  Now my XP box can access my Ubuntu box.  I just can't get the Ubuntu to access XP but this will work just the same.

thanks so much!!

---

### Post by DoorGunner on 2007-03-20
hey ..... who says you cant kill two birds with one stone.... :lolflag:

---

### Post by scxtt on 2007-03-21
> **DoorGunner said:**
> You need to sudo chmod 777 YOUR_FILES_YOU_ARE_SHARING. Once you do that than restart samba again. It may take a min or so for MS to catch up with the change.there's NO WAY this is necessary ... you don't need to give EVERYONE read/write/execute permissions just for samba ...

and as far as configuring samba shares, you should be able to right-click on a non-samba-shared folder and share it - as long as you're not doing anything too complicated, if you are - editing smb.conf would be necessary ...

---

### Post by cowlip on 2007-03-21
There's a bug for this smbpassword problem here for anyone interested:  [https://bugs.launchpad.net/ubuntu/+source/samba/+bug/32067](https://bugs.launchpad.net/ubuntu/+source/samba/+bug/32067)

I just want to note that nautilus-share used to have a UI to do all this for SUSE or Red Hat.. [http://gentoo.ovibes.net/nautilus-share/mediawiki-1.4.4/index.php/Accueil#Nautilus-Share_:_A_quick_and_easy_way_to_share_your_folders.21](http://gentoo.ovibes.net/nautilus-share/mediawiki-1.4.4/index.php/Accueil#Nautilus-Share_:_A_quick_and_easy_way_to_share_your_folders.21)

---

### Post by scxtt on 2007-03-21
i don't use gnome, but KDE - and i can easily create a basic samba share by right-clicking on a folder ... i imagine gnome does the same ...

and i don't see how smbpasswd has a problem, in the sense that there's a bug ...

---

### Post by cowlip on 2007-03-21
well just that there's no GUI to do it, so it's not very discoverable for Windows users IMO.

---

### Post by DoorGunner on 2007-03-21
scxtt

Your absolutely right. you dont have to do it the way i just showed.  There are many ways and configurations. It really depends on the target for his samba share. In this case i believe it was his family that was using it. It was my intent to get samba up and running the easily to a point were he could build security and still be able to fall back to the last known workable solution. And like you said "if you arent planning on anything too complicated".

 At some point people like to learn more and go beyond what a gui can do for your. Understanding the config files is important and this was a good start in learning. The origional config that come with samba can be overwhelming when you first try to get your head into it. I believe in an approach that gets people started bit by bit allowing room  for one to build on previous knowledge.

This is just my point of view, not a right or wrong way of doing things. I leave it up to the reader to decide what is best for them.

---

### Post by scxtt on 2007-03-21
chmodd'ing files to 777 is not a real solution - period - that's my point :)

i have no issue w/ anything you said about smb.conf, tho i didn't read it closely ...

---

### Post by DoorGunner on 2007-03-21
so what is your suggestion then?

---

### Post by scxtt on 2007-03-21
to what problem?  the OP seems to be content ...

giving the WORLD rwx permissions on files is a bad idea, it just shouldn't be done - not for samba, not for anything ... i'm sure there are smb.conf options that can be worked out in lieu of that being a "solution" - that's all i'm saying ...

as long as your PC is aware of the WORKGROUP you want to connect to, in general, users can right-click on a folder (in Gnome and KDE) and "share" it w/ samba - or NFS if that's intstalled/configured/running ... there are def. more options for smb.conf, but how many "noobs" have some complicated samba setup?

---

### Post by DoorGunner on 2007-03-21
You made a comment here.

> chmodd'ing files to 777 is not a real solution - period - that's my point

As far as i know chmodding  a file should only affect what happens internally on you own computer. If I had multiple people logging in on my computer I might be a little more concerned. Its not the same as giving up your root password. 

As far as Samba is concerned... the share will only display what is in the share folder not the folder itself. For instance in in my share it has folders X, Y and Z.. On the other computers only the drive and X,Y and Z show up. However, it doesnt display the share itself. So, i guess what i am looking for is how is why you feel that chmod 777 such a bad idea? If it so bad then why is it even allowed. Or is there a place for it?

I just thought it was a bold statement with no real reason as to why. It just leaves the reader wondering why. Maybe what you would suggest that might be better.

---

### Post by scxtt on 2007-03-21
no, it's not the same as giving up your root p/w - but chmodding files/directories to 777 allows anyone to do whatever they want w/ any file/folder that is in that state - sure it's not a big deal if you're the only one who uses the computer, but it's not a REAL solution to a problem, any problem, even if it isn't samba specifically we're talking about - it's just bad advice ...

as far as shares are concerned, you share a folder, let's say /home/gunner/samba_share as "gunner_samba" - when you connect to that share (if your IP is 192.168.1.100) it's of the form \\192.168.1.100\gunner_samba ... then anyone who has smb "access", via **sudo smbpasswd -a $USER** (has to be valid from /etc/passwd) can access your shares (provided you don't put per-user restrictions in smb.conf ... maybe you're circumventing that by making all samba shared files 777, but like i said chmod 777 is NOT a solution - it's a unsecure workaround ...

---

### Post by DoorGunner on 2007-03-22
are you talking about the contents of the gunner_samba file or the gunner file itself?

---

### Post by scxtt on 2007-03-22
we're not talking about single files, in terms of sharing - samba shares are generally (if not always) directories ...

linux directory = /home/gunner/samba_share
samba share name = gunner_samba

so as far as samba (on the whole) is concerned, /home/gunner/samba_share = gunner_samba ...

any files/directories contained in /home/gunner/samba_share will be shared via: **\\192.168.1.100\gunner_samba**

so if you have a file /home/gunner/samba_share/my_song1.mp3, you'll access it via:

\\192.168.1.1.00\gunner_share\my_song1.mp3

additionally, if you have /home/gunner/samba_share/directory2/my_song2.mp3, you'll access it via:

\\192.168.1.100\gunner_share\directory2\my_song2.mp3

etc., etc., etc. ...

it's quite possible if **/home/gunner/samba_share/my_song1.mp3** has -rw------ permissions any samba user who ISN'T you can't view it - that's easily solvable, change it to -rw---r-- ... AGAIN, chmod 777 is a BAD idea ...

---

### Post by DoorGunner on 2007-03-22
I did a little experiment on my system. I changed the chmod of my share.  The share is on a partition and is fstabed into a /media file. Chmod 755 was as low as i could go before things became forbiden. At that point samba wouldnt work at all. 

So 755 is owner can change and modify and everyone else can view. The interesting thing i found was after restarting samba, I could still read/write into files even though the /gunner_share file was still limited by chmod 755.   I was able to cut and paste, delete and change things  with in the share file despite the chmod. This is why i say chmod 777really makes no difference on the linux directory = /home/gunner/samba_share where the samba share name = gunner_samba

I believe that as long as samba can get into the folder the chmod of the linux directory = /home/gunner/samba_share doesnt matter as long as it isnt forbidden. 

However, I was able to change chmod to the contents of samba share name = gunner_share. I could cause files to be read only or be non viewable. That does exactly what you are talking about. 

However as you see that this is not a black and white issue. You may want some to edit and others to view the same file.  That is were samba is able to make a difference. You can edit people individually  as to the needs of the system and that is the point I am tring to make. 

If you want to limit who goes on samba you can change security = share to security = user. Then you will need to have password access. You can also limit the hosts allow = 192.168.1. to

 hosts allowed= 192.168.1.100
 hosts allowed= 192.168.1.101
 hosts allowed= 192.168.1.102 etc for specific ips allowed on.

As i mentioned you can also specify user priviledges in samba. 


This was from an XP machine and a second Ubuntu machine.

---

### Post by scxtt on 2007-03-22
> So 755 is owner can change and modify and everyone else can view. The interesting thing i found was after restarting samba, I could still read/write into files even though the /gunner_share file was still limited by chmod 755. I was able to cut and paste, delete and change things with in the share file despite the chmod. This is why i say chmod 777really makes no difference on the linux directory = /home/gunner/samba_share where the samba share name = gunner_sambawhat user were you, the owner of the share itself?  all the same properties apply ... for your linux user, 777 and 755 are the same thing - but if you try to connect to your share as a user that's NOT you, you'll find different results - which i did using my share of my ~/ directory and server 2003 ...

_ftp is the only other user in my /etc/passwd_
~scxtt/ @ 700 as "scxtt" - it all works as usual
~scxtt/ @ 705 as "scxtt" - it all works as usual
~scxtt/ @ 700 as "ftp" - can map it, but can't browse or cd into it
~scxtt/ @ 705 as "ftp" - can read, cd - but can't change/write

moral of the story - if you don't care about the files, chmod them 777 ... if you do, don't even consider it ...

---

