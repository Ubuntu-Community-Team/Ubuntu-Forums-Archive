---
title: "networking"
date: 2006-06-24
forum: Absolute Beginner Talk
---

### Post by OrganicPanda on 2006-06-24
this is almnost painfully embarrasing to ask but how do you network in ubuntu, i have 2 ubuntu machines 192.168.1.101 and 192.168.1.104 and both have the Desktop folder shared to eth0 network 192.168.1.0/255.255.255.0 using nfs but in the networking browser tool all i see is 'windows network' and my website ftp folder, how can i access one machine from another??

im really lost here i dont even know what to type in an address bar to access the other machine im too used to unc in windows networks like //server-name-or-ip/sharename, so whats ubuntus deal?

---

### Post by fmo on 2006-06-24
[QUOTE=OrganicPanda]this is almnost painfully embarrasing to ask but how do you network in ubuntu, i have 2 ubuntu machines 192.168.1.101 and 192.168.1.104 and both have the Desktop folder shared to eth0 network 192.168.1.0/255.255.255.0 using nfs but in the networking browser tool all i see is 'windows network' and my website ftp folder, how can i access one machine from another??

im really lost here i dont even know what to type in an address bar to access the other machine im too used to unc in windows networks like //server-name-or-ip/sharename, so whats ubuntus deal?[/QUOTE]

If you have already enabled the sharing on the machines, Go to "Places" and Select "Connect to server" fill in the details and it will create a desktop shortcut that will allow you to connect to your server.

---

### Post by OrganicPanda on 2006-06-24
but the machine doesnt use ssh, ftp, http, https and its not a windows share so i dont really see an option for it

---

### Post by OrganicPanda on 2006-06-24
is it somehow possible that my router doesent allow nfs, this is really bugging me and thats the only thing i can think of

---

### Post by OrganicPanda on 2006-06-24
well i guess networking just doesn't work in ubuntu, had to just use samba which i dont like doing atall but it seems like my only option in this case, so can ubuntu really not function in a lan scenario, took me 2 hours to send some files to my other computer and i still haven't figured out how to do it properly. this has got to be the first thing i really don't like about ubuntu, it's a sad day

---

### Post by Apple 101 on 2006-06-24
Make sure that the workgroup used by both computers is the same, and make sure that a firewall isn't blocking access (if you use one).

---

### Post by falcon15500 on 2006-06-24
[QUOTE=OrganicPanda]well i guess networking just doesn't work in ubuntu, had to just use samba which i dont like doing atall but it seems like my only option in this case, so can ubuntu really not function in a lan scenario, took me 2 hours to send some files to my other computer and i still haven't figured out how to do it properly. this has got to be the first thing i really don't like about ubuntu, it's a sad day[/QUOTE]

  I think it's probably a little too early in the game for you to be either a) giving up, or b) slagging the distro.  I think you probably need to do a little more research on NFS shares - this forum is one way, certainly.  Have you tried searching the forum for NFS?  What about google?

  I don't have another machine here to try, but I believe with NFS you have to mount the shares just as you would a local drive, with the mount command.  You can also have the shares attempt to be mounted at boot, if you put them into your fstab.

falc

---

### Post by Herman on 2006-06-24
> well i guess networking just doesn't work in ubuntu, had to just use samba which i dont like doing atall but it seems like my only option in this case, so can ubuntu really not function in a lan scenario, took me 2 hours to send some files to my other computer and i still haven't figured out how to do it properly. this has got to be the first thing i really don't like about ubuntu, it's a sad day 
It's easy! Just use SSH Networking, it seems to be a well-kept secret for some reason, but I guess it's so good that no-one has any problems with it, so the topic doesn't come up too often in the forums.
[***Click here***]("http://users.bigpond.net.au/hermanzone/p11.htm") for a web-Page about how to set up a home SSH network.

Good luck with it, I hope it helps, I've been doing this for ages, it works great for me. Regards, Herman :D

---

### Post by OrganicPanda on 2006-06-25
thank you for the replies i realise im comming off a bit pesimistic her...

@apple yeah the workgroups are the same even the same case just to make sure of compatibility

[QUOTE=falcon15500]I think it's probably a little too early in the game for you to be either a) giving up, or b) slagging the distro.  I think you probably need to do a little more research on NFS shares - this forum is one way, certainly.  Have you tried searching the forum for NFS?  What about google?

  I don't have another machine here to try, but I believe with NFS you have to mount the shares just as you would a local drive, with the mount command.  You can also have the shares attempt to be mounted at boot, if you put them into your fstab.

falc[/QUOTE]

i have tried looking up nfs but it just returns heaps of how to do x and y with nfs rather than 'nfs: get it working 101' which i'm looking for, and in regards to mounting - that is good but whats the point of a nertwork browser in gnome if you need to mount network shares, that is illogical.

i will look into shh although i'm not sure thats entirely what i'm after either, cheers herman, falcon and apple for you help

---

### Post by OrganicPanda on 2006-06-25
herman thats a very good guide, cheers

ok i guess ssh will have to do itr looks really good but seems a bit extreme for transferring files across my lan, is there a file manager type application that will let me drag and drop files because nautilus will let me view the files from the other machine but wont allow me to transfer files, i know i can do this from the command-line but i'm looking for a graphical way, anyone know of any good ones, or anyones atall?

---

### Post by Apple 101 on 2006-06-25
Open Synaptic and make sure that all of the NFS packages are installed.  To make it quick - search for NFS.

---

### Post by OrganicPanda on 2006-06-25
ok i will give that a shot cheers, i think something should be done about this though, the first time you try to share a folder it gives you the options (samba smb or nfs) and then installs whichever you choose, this kind of gives you the impression that everything is going to work without installing extra packages, stop me if i'm expecting too much here but this is very very basic stuff made overly complex

---

### Post by Herman on 2006-06-26
> ok i guess ssh will have to do itr looks really good but seems a bit extreme for transferring files across my lan, is there a file manager type application that will let me drag and drop files because nautilus will let me view the files from the other machine but wont allow me to transfer files, i know i can do this from the command-line but i'm looking for a graphical way, anyone know of any good ones, or anyones atall? It's just the same as mounting another partition or opening a folder, you can drag and drop, copy and paste with SSH, I don;t think you can play a music fils from another computer, but you can do most things. It doens everything I want. The best thing is it's pretty secure, you don't have to know all about IPTables.
Regards, Herman

---

### Post by OrganicPanda on 2006-06-26
oh ok, i must have something set-up wrong then, i can browse but not edit, cheers for letting me know

---

### Post by Herman on 2006-06-26
Did you log in as the owner of the other computer using the other computer's original user's name and password?
Otherwise you can work with 'Users and Groups' and 'Directory Permissions' to allow yourself or have the other computer's user allow you the priveleges they may wish to allow for you. Normally, that would be the way to set things up.
The way I do it is simply to log in as the other user, with full priveleges. That's the simplest and best if it's your own computer or the other computer user  is very trusting. 
Regards, Herman :D

---

### Post by polarice on 2006-06-26
[QUOTE=OrganicPanda]well i guess networking just doesn't work in ubuntu, had to just use samba which i dont like doing atall but it seems like my only option in this case, so can ubuntu really not function in a lan scenario, took me 2 hours to send some files to my other computer and i still haven't figured out how to do it properly. this has got to be the first thing i really don't like about ubuntu, it's a sad day[/QUOTE]

I know very little about computers and software but I've got Ubuntu and Windows PCs all talking to each other - perhaps I'm just lucky ;)

I thought it was bad enough when I only used Windows but I got real;y frightened by the jargon when I started with Ubuntu recently. I got it all set up in Breezy, largely by trial and error, but in Dapper it seemed easy (sorry if this upsets you, hearing a "learner" saying it's easy when it's driving you mad).

Maybe you want to do it one particular way and that causes the trouble, whereas I would do anything as long as it got my PCs networked!

If I remember correctly, it went like this. I started by going to Administration, Shared Folders. A dialog came up telling me to download Samba or NFS, so I got Samba because I wanted to network Windows as well as Ubuntu. Also smbfs because I read somewhere that I needed that too (I did warn you that I was a learner!). Then In Shared Folders I set up the folders that I wanted to share, clicked SMB and Allow browsing folder.

In the smb.conf file I set security = share
In the Properties, Permissions menu of the shared folders I ticked "Write" for the Group and Other boxes.
I left the workgroup name as MSHOME in smb.conf

Having done this I can read, edit, move, copy files across my network between the PCs, whether Ubuntu or Windows. I'd be willing to accept criticism that this is a poor way to do things but, as I beginner, I find it works!

---

### Post by AndyCooll on 2006-06-26
For linux to linux boxes with fixed IP addresses I find it's easiest to configure using a combination of methods:

On the server (i.e. the pc with the share) I install nfs-common and nfs-kernel-server (not sure if this last one is needed or not). And then set up the share. This can be done either by Administration-->Shared Folders or editing the /etc/exports file. I add a line to "exports" something like this:
```
/home/andy/share 192.168.2.0/255.255.255.0(rw)
```

rw gives read and write permissions. 

Then on the client I install nfs-common and using the terminal I make a mount point and edit fstab:
```
sudo mkdir /mnt/share
sudo gedit /etc/fstab
``` 

I add a line to fstab like this:
```
192.168.2.2:/home/andy/share /mnt/share nfs defaults 0 0
```

That says the folder home/andy/share that is on box 192.168.2.2 should be mounted at /mnt/share on this pc. Adding to fstab means it will be automatically mounted each time the pc is booted up.

However you can mount it immediately by:
```
sudo mount -a
```

There are a multiude of ways to modify these settings but this simplistic approach seems to work well for me.

:cool:

---

### Post by enyaw on 2006-06-26
[QUOTE=Herman]It's easy! Just use SSH Networking, it seems to be a well-kept secret for some reason, but I guess it's so good that no-one has any problems with it, so the topic doesn't come up too often in the forums.
[***Click here***]("http://users.bigpond.net.au/hermanzone/p11.htm") for a web-Page about how to set up a home SSH network.

Good luck with it, I hope it helps, I've been doing this for ages, it works great for me. Regards, Herman :D[/QUOTE]

Herman...Great help....Thx:D 

p.s.  The Avatar...What make is the computer

---

### Post by OrganicPanda on 2006-06-27
ok ok i understand it's all possible, i have samba working perfectly but i don't want to emulate a windows' network, i want nfs to work, i keep re-trying with no luck so i guess samba will have to do. although when i try to access one of my servers shares from a windows machine it doesnt even ask me to log in, it just says i have no permissions and boots me out, i'm sure thats something i've set up wrong, that smb.conf file is rediculas .. i want native linux networking.

anyway enough complaining it does kinda work so i can move files about 

@herman yes i only ever use 1 username/password on my machines because as much as security is important i think i trust my familly not to mess everything up .. but i will look into those things you said

@andycooll thats all good but i have no interest in mounting in this context but thanks anyway

@polerice, thanks for that information but samba bugs the hell outta me

---

