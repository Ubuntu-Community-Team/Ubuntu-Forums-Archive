---
title: "Still Attempting to Network - this time with NFS"
date: 2007-03-23
forum: Absolute Beginner Talk
---

### Post by Robynsveil on 2007-03-23
Hi,
Still at it - getting nowhere. I’ve been trying to connect my dual-boot laptop to my dual-boot desktop for the past week, using Samba and NFS.

I've been running into snag after snag with Samba, so I thought I'd have a go with NFS. No luck. I read this tutorial that tried to make it sound like using NFS is a no-brainer:

[http://ubuntu-tutorials.com/2006/10/20/network-file-system-nfs-ubuntu-606-610/](http://ubuntu-tutorials.com/2006/10/20/network-file-system-nfs-ubuntu-606-610/)

...and I'm thinking: *yay! I can do this*. The instructions read:


> 
Below are quick steps on installing and configuring an NFS share on your network. I set this up last night in about 5 minutes to share my media (video and audio) to the other machines on my network.
* sudo aptitude install nfs-kernel-server


I had to figure out on my own that I needed to log in as root and *how* to log in as root, because just entering 'sudo' generated errors (and after the errors Terminal asked if I was logged in as root). I finally got those files *installed*. I was a bit surprised that I had to install NFS, because I thought that NFS would kinda install with Ubuntu.
Then, I did part 2:

```

sudo gedit /etc/exports

```

…in which I placed the following entry:

/media/NFS_deskdocs*(rw,sync)

Here’s where I started to get confused - a state I find myself in all the time these days brought out a lack of understanding of the syntax of the examples. I don't know if I'm the only one that has this issue, but to *me* the example give doesn't really give me much of a clue what to actually enter - a place-holder word like 'example.hostname:' leaves me wondering what do they mean by that? Is the host the name of the box, the share folder, the ICS computer, What?!??
BTW, I specifically gave the Ext3 partition "NFS_deskdocs" that name because I was forgetting which folders on my desktop were actually NTFS partitions mounted with NTFS-3g and which were Ext3. I suspect that the NTFS partitions cannot be shared using NFS, am I right?

Now, in my /etc/fstab file is the statement:

> 
flight:/media/NFS_deskdocs /media/NFS_deskdocs nfs rw,hard,intr 0 0


…and here is where the confusion manifests itself... I'm assuming in the example that the author gave in that article that I should replace 'example.hostname:' with ‘flight:’, as that is the name of the desktop box, and replace 'share_location' with ‘/media/NFS_deskdocs’, and then '/mount_location' with ‘/media/NFS_deskdocs’ as the mount location. BTW, there *is* a '/media/NFS_deskdocs' folder.

I checked in System --> Administration --> Services to make sure the NFS server is running: it is. However, when I try to log on to this box from the laptop, I can *see* the box in the network folders region, but when I try to access it, I get:

[COLOR="Red"]**The folder contents could not be displayed. Sorry, couldn't display all the contents of "Windows Network: flight".**[/COLOR]

:confused: 
Is it just me? Why am I having such a hard time figuring this out? Being a total n00b, the:

> 
example.hostname:/share_location /mount_location nfs rw,hard,intr 0 0


didn’t really give me a clue as to what I should be entering… colour me thick. I noticed in the article the author included a manual mount in Terminal - I suppose that was to test it, which I did, but it kept returning an error, like for ‘flight’, the name of my desktop:

```

sudo mount flight:/media/NFS_deskdocs /media/NFS_deskdocs
mount: can’t get address for flight

```

and then, if I tried media:

```

sudo mount media:/media/NFS_deskdocs /media/NFS_deskdocs
mount: can’t get address for media

```

At this point, I gave up. :-k I just *know* I’m missing something quite central, here. Where did I go wrong?

Thanks for any help you can give…

Cheers,
Robyn

---

### Post by lemonsCC on 2007-03-23
you could always try the ip address of the host machine.  hostname is refering to the name of the box at which your files are stored on.  like my hostname on this laptop is "laptopPB"  the ip is 192.168.1.115   i could use either for the purpose of setting up the sharing.  BUT keep in mind that your router will assign ip's "at random"   unless you setup a static ip.....a whole different topic.

Summary...in terminal type "ifconfig"  get the ip address for the box with the files and use that in the spot where hostname goes. (FOR NOW)  Post back if it works.

---

### Post by lemonsCC on 2007-03-23
just read the line about the windows network.  this is ubuntu to ubuntu or windows to ubuntu sharing?

---

### Post by Robynsveil on 2007-03-24
==> LemonCC:
Did the ifconfig, and was able to ping the sharing computer with the laptop, no problems, using:

ping 192.168.0.186

This is Ubuntu to Ubuntu. My query stems from the error message:

[COLOR="Red"]The folder contents could not be displayed. Sorry, couldn't display all the contents of "_Windows Network_: flight".[/COLOR]

But Windows isn't even running on that machine. Must be the ICS computer that is saying: "I've got a Windows box named 'flight' as someone I've got permissions for, so if a pc named 'flight' happens along, it must be that Windows box..." but I named my desktop box 'flight' in Ubuntu as well.... is it possible the problem stems from the dhcp service the ICS machine is performing?

---

### Post by hoheszeh on 2007-03-25
If connecting two PCs and sharing data between them with ssh would as well be an option for you have a look at [http://ubuntuforums.org/showthread.php?t=392153](http://ubuntuforums.org/showthread.php?t=392153) and my post there.

---

### Post by lamalex on 2007-03-25
its my understanding that NFS is for linux to linux, samba is windows to linux. windows to windows is the smb protocol so samba is the linux equivalent. I might be wrong, but I'm pretty sure samba is your only choice for windows to linux sharing. or ftp, but that's not much of a solution. what samba problems are you having.

---

### Post by lemonsCC on 2007-03-25
> **Iamalex said:**
> its my understanding that NFS is for linux to linux, samba is windows to linux. windows to windows is the smb protocol so samba is the linux equivalent. I might be wrong, but I'm pretty sure samba is your only choice for windows to linux sharing. or ftp, but that's not much of a solution. what samba problems are you having.

Right now I am pretty sure samba (aka smb) is universal.  I use it to share Mac to Windows to linux daily.

---

### Post by lamalex on 2007-03-25
thats irrelevant. you still can't go win to lin with NFS. mac probably has smb installed so it can communicate with windows and nfs since it's bsd based.

---

### Post by Jose Catre-Vandis on 2007-03-25
> **Iamalex said:**
> thats irrelevant. you still can't go win to lin with NFS. mac probably has smb installed so it can communicate with windows and nfs since it's bsd based.


Oh yes you can! :-)

XP and Vista both have an NFS Client you can install, which then allows you to access NFS shares on a linux box on the network.

I had so much trouble with using Samba that I switched to NFS for my network shares, and used NFS clients on Windows boxes to provide access and file sharing when on windows.

I followed this howto 
[http://www.ubuntuforums.org/showthread.php?t=249889](http://www.ubuntuforums.org/showthread.php?t=249889)
to set up NFS on my Linux server and clients, and wrote this howto
[http://www.ubuntuforums.org/showthread.php?t=310168](http://www.ubuntuforums.org/showthread.php?t=310168)
 for XP setup. 

NFS under Vista is found in the Windows Features.

Suggest the OP goes back to the beginning and starts over following these two howtos. Ubuntu gives you read of local NTFS partitions.

I also use Ext2IFS_1_10c.exe in windows to access Ext3 shares locally.

HTAH

I'll admit, because I trust all the users on my lan, I haven't tied down the security, but you can set read only if you need to.

---

### Post by Robynsveil on 2007-03-26
Hi Jose,
Thanks for your post. I'll have to admit to being a complete newbie, so some of the terms in the article here:

[http://www.ubuntuforums.org/showthread.php?t=310168](http://www.ubuntuforums.org/showthread.php?t=310168)

...went a little over my head. I'll eventually address them one-by-one, but I should probably have this one key question answered, if that's okay: this whole exercise assumes that the Ubuntu Linux boxes have each a static IP address - is that correct?

At this point, the Windows 2000 Professional box that forms the connection to the Internet on this little home LAN acts as a sort of dhcp server - I guess it's part of ICS. When I try to set a static IP address for any of the other PCs (all running XP except for my two) ICS seems to fail for them. Not sure if there is a way around that. I mean, eventually I'll be setting up a Ubuntu box to act as Interface/Gateway computer, but if I did that now with my sketchy knowledge of how networking and all that works, I'd be facing mutiny.

Thanks for any ideas on this...
Cheers,
Robyn

---

### Post by Jose Catre-Vandis on 2007-03-26
Recommend you get yourself a standalone ADSL/router, which once setup = 0 headaches :-)

Yes, you need a set and defined location if you want to persistently share, and not have to first find out what each machines IP is today, and then type in the mounts.

I have forgotten everything I knew about ICS, but it does need dynamic IPs in order to do its thing. 

Not sure if you can setup a kind of dynamic dns type thing on your LAN?

This might help to shed some light:

[http://www.securitypronews.com/it/networksystems/spn-21-20030731Windows2000ICSNATandIAS.html](http://www.securitypronews.com/it/networksystems/spn-21-20030731Windows2000ICSNATandIAS.html)

---

### Post by Robynsveil on 2007-03-28
> **Jose Catre-Vandis said:**
> Recommend you get yourself a standalone ADSL/router, which once setup = 0 headaches :-)


Not really an option at this point: although routers have come down dramatically in price, here in Oz they are still a bit beyond my budgetary reach, ATM. I have some older bits ... a motherboard, CPU, box, RAM, and hard drives --- gee, think I'll build a server! ... lying around, and am thinking of building a Ubuntu-based connection box - replacing our tired old Win 2K box - with two NICs that will perform the NAT (instead of ICS, which invokes dhcp) function - and firewall and file server and maybe even mail server - for my little LAN.

> **Jose Catre-Vandis said:**
> 
Yes, you need a set and defined location if you want to persistently share, and not have to first find out what each machines IP is today, and then type in the mounts.
I have forgotten everything I knew about ICS, but it does need dynamic IPs in order to do its thing. 


I'm sure that there are a fair few of us with the same sort of workgroup topology as mine - one box doing the ICS (using dhcp) function and a switch or two. I've been trying to find articles and information on this exact issue... googling didn't bring any enlightenment. You are the first to actually come out and say a static IP address is essential to NFS working... and Thank You. Gotta clear that all up before trying to go on. Since Windows 2000 Professional does not include NAT as an option - only ICS - there is no way the Windows box will accept anything but what it delivers in the way of IP addresses via dhcp.
Buggah!
SO, perhaps I should be barking up the "The Idiot's Guide To Building A Linux Server" or "DIY Linux BOHO LANs - It's Easier Than You Think" tree... :) I kinda figured it would eventually come to that. Good job I've got all those spare bits lying around... but putting together this box is the *easy* part. Looks like I've got a fair bit of studying ahead!

Cheers
Robyn

---

### Post by Jose Catre-Vandis on 2007-03-28
Check distrowatch for a linux router distro, or search the forum to see if someone has done it with Ubuntu, they are out there...

Also, I have not tried seeing what happened if I set the host names for PC's serving up NFS shares, and then switch to dynamic IPs

It might work???

---

### Post by jerryrw on 2007-03-28
Your mounting errors most likely  stem from hostname resolution.  Assuming that you are not using a local DNS you need to put the names -> ips of the boxen that you want to NFS together into the /etc/hosts file of both machines.  Trying to do NFS with dynamic IPs is problematical at best.

Samba has the NMB protocol that does the name resolution for you.

---

