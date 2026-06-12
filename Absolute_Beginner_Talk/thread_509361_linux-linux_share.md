---
title: "linux-linux share"
date: 2007-07-25
forum: Absolute Beginner Talk
---

### Post by enfantterrible on 2007-07-25
hello all,

apparently it's much easier to share folders between linux and windows rather than from linux to linux!!

i am behind a router, desktop is wired connected to it (192.168.2.102) and laptop is wireless connected to the router (192.168.2.100)

i go to system/administration/shared folders and share the one i need. i chose NFS and give permission to IP 192.168.2.100

then i go on the laptop, try to explore the network but it sees only a windows network (which i dont have).

how do i make my laptop see the desktop shared folder?

oh, they both ping perfectly each other.

thanks

---

### Post by bernied on 2007-07-25
have you tried just entering the address in the address bar of your file browser?
nfs://192.168.2.102/ShareName

---

### Post by bbzbryce on 2007-07-25
> **enfantterrible said:**
> i go to system/administration/shared folders and share the one i need. i chose NFS and give permission to IP 192.168.2.100

I have a NFS share setup that I use without problems, however it does not appear under the Network browser. It is my understanding that NFS shares aren't discoverable, though I may be wrong about that.

To manually connect do something similar to the following:

```
bryce@ubuntu:~$ cd /media/
bryce@ubuntu:/media$ sudo mkdir temp
bryce@ubuntu:/media$ sudo mount servie:/home temp

```

Where servie is the name of the computer with the nfs share, and home is the path that's setup to share.

See the following for more:
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#NFS_Server](http://ubuntuguide.org/wiki/Ubuntu:Feisty#NFS_Server)

---

### Post by enfantterrible on 2007-07-25
hi guys... unfortunately i tried both and it's not happening.

if i try looking for the file in the file browser (nautilus) i get this message:
"nfs://192.168.2.102/media/hdc1" is not a valid location

if i try to mount the shared folder from the terminal, i get :wrong fs type, bad option, bad superblock on ...."


sorry guys i really have no clue how to proceed now!

---

### Post by enfantterrible on 2007-07-25
quick update: mounting actually gives me a different error message: moun to NFS server failed: server is down

which is pretty rare as i restarted the nfs server couple of times and the laptop is allowed within the firewall and i can ping the two machines ?

---

### Post by punx45 on 2007-07-25
i know you are trying to do this the GUI way, but lets get a look at /etc/exports  (from the machine you enabled NFS share on)
paste it up here.

---

### Post by enfantterrible on 2007-07-25
hei thanks for a very quick reply!

this is the result:

# /etc/exports: the access control list for filesystems which may be exported
#		to NFS clients.  See exports(5).
#
# Example for NFSv2 and NFSv3:
# /srv/homes       hostname1(rw,sync) hostname2(ro,sync)
#
# Example for NFSv4:
# /srv/nfs4        gss/krb5i(rw,sync,fsid=0,crossmnt)
# /srv/nfs4/homes  gss/krb5i(rw,sync)
#
/media/hdc1     192.168.2.100(rw)

---

### Post by punx45 on 2007-07-25
hmm. seems in order.   is your laptop DHCP configured? did its IP change?

or maybe the NFS server went down somehow?
try restarting the NFS server too:
```
sudo /etc/init.d/nfs-kernel-server restart
```

---

### Post by scxtt on 2007-07-25
try **mount -t nfs 192.168.1.100:/media/hdc1 /media/temp** -- and be sure *192.168.1.100:/media/hdc1* has read access for "other" ... you might also need more options in /etc/exports than just (rw) ... not sure yet.

you can also use **showmount -e <hostname or IP>** to see what NFS mounts are offered.

---

### Post by enfantterrible on 2007-07-26
hello

the server is up and running, but i think there are (also) some other issues

a) one of the folders i want to share is called My Documents. Linux screws up a bit the space in the name
b) for some reason i cannot change the permission of /media/hdc1 (which is a whole drive, fat32) for "other"
c) i tried sharing my home folder, with the right permissions and no spaces in the path - same results: nfs server is down.

it might be something net related - but again, i ping without problem and firewall on the desktop is set to receive connections from the laptop

---

### Post by TeaSwigger on 2007-07-26
> b) for some reason i cannot change the permission of /media/hdc1 (which is a whole drive, fat32) for "other"

Just tossing in that I seem to recall coming across mention that FAT32 never had provision for some aspects of permissions. If I'm recalling rightly, everything's working okay, you're up against a limitation of the FAT32 file system.

---

### Post by scxtt on 2007-07-26
what are the results of showmount? from the "client" to the "server"?

client:$ **showmount -e <server_IP>**
(if you don't have showmount. **sudo apt-get install nfs-common** should take care of it)

---

### Post by enfantterrible on 2007-07-26
result of the showmount is none - it just shows the command line again

---

### Post by scxtt on 2007-07-26
then something tells me it's not happy w/ the options (or lack thereof) in your /etc/exports ... try this:

/media/hdc1 *(rw,sync,no_root_squash,no_subtree_check)

and then restart nfs ...

---

### Post by enfantterrible on 2007-07-26
nothing happens, also showmount is still empty

---

### Post by scxtt on 2007-07-26
turn off any firewall on the box hosting NFS ... this def. works and all that really is left is that you have some network roadblock ...

on nfs host:
-- make sure /etc/exports contains the following: **/media/hdc1 *(rw,sync,no_root_squash,no_subtree_check)**
-- restart nfs server: **sudo /etc/init.d/nfs restart** (note, this may be nfsd or nfs-kernel-server - restart whichever you have)
-- do a **ps -ef | grep nfs** and you should see a handful of nfsd processes ...

on client:
-- make sure nfs-common is installed, then do **showmount -e <IP of nfs host>**
-- if you get something returned, do **sudo mount -t nfs <ip of NFS server>:/media/hdc1 /media/hdc1** and it should be mounted ...

of course if for some reason fat32 can't be NFS mounted, you're SOL - don't know if that's even a possibility - i haven't had a fat32 partition in years ...

---

### Post by rich.bradshaw on 2007-07-26
Just my 2 cents:

I set both computers up as ssh servers. (use openssh), then use the connect to server dialog in the places menu.

Benefit is that this works over the internet as well, so I can get files anywhere.

---

### Post by enfantterrible on 2007-07-26
hmmm i turned off firestarted and still does not work, but one more thing i noticed:

ping does not work anymore and when i click on the connection icon on the panel to get network info, i get (on both computers) this error message: Error displaying the correct information. could not find some required resources (the glade file) !

(exclamation mark is included..)

---

### Post by scxtt on 2007-07-26
firestarter is just an iptables frontend, not sure if just quitting it will clear the rules ... do an **sudo iptables -L** to see ... this seems like a network issue more than an NFS issue ...

---

### Post by enfantterrible on 2007-07-26
thank you all guys for help - i really feel bad for being so ingorant !

i agree it's probably a network issue 

anyway, firewall is definitely off - now apparently network is screwed (even though i am online and torrenting pretty fast) i think i might try to reboot later on to see what happens but, to say it in wiser words than mine "i have a bad feeling about this"...

---

### Post by enfantterrible on 2007-07-26
thing is... once i am a bit more accustomed to linux, what i would like to do (Easily) woudl be

a) connecting from my laptop to my desktop, opening a real session there (terminal AND gui) wiht my user, my password etc... i used to do that in windows with ULTRAVNC out of the box
b) transfer files back and forth the two machines
c) keep all the music on the desktop and playing it in songbird on the laptop, maybe even synicing libraries between the two computers and the ipod.

am i asking too much? it's 2007... :) and i am not intentioned to go back to windows. the main reason i use ubuntu is that it is free... dual boot to me makes no sense - i would go windows only, in that case.

---

### Post by rich.bradshaw on 2007-07-26
a) connecting from my laptop to my desktop, opening a real session there (terminal AND gui) wiht my user, my password etc... i used to do that in windows with ULTRAVNC out of the box

Ubuntu has VNC out of the box installed - it's in system, remote desktop somewhere.

b) transfer files back and forth the two machines

I use SSH for this, as it's easier for me.

c) keep all the music on the desktop and playing it in songbird on the laptop, maybe even synicing libraries between the two computers and the ipod.

If you open Rythmnbox on both computers you can share music as in iTunes (might have to turn it on in Ryhtmnbox, can't remember!)

In the end I just used ssh again, as it's so simple to do this.

---

### Post by scxtt on 2007-07-26
"am i asking too much?"

no, i'm doing all of that as we "speak" ...

1. i use rpd/vnc to connect to linux VMs/hosts on my network at any time ... uses tightvnc and rdesktop.
2. i use smb / nfs / ssh to xfer files all the time
3. i'm listening to music on my laptop via a smb share on my gentoo desktop ...

it's all possible, and not that hard, but your basic network setup has to be in order 1st ... if you're behind a router, and not forwarding all sorts of ports - turn off all firewalls till you can selectively turn things on/off and know what they directly effect ...

---

### Post by enfantterrible on 2007-07-26
i am really stuck...

the two machines ping each other
if i do port scan from the laptop to the desktop i see port 2049 is open on the desktop for nfs
firestarter i stopped firewall (which i guess it's not exiting the GUI, it's just stopping firewalling) but still no help there...

i am getting frustrated. thanks again for all input, but i am really out of options at the moment !

---

### Post by enfantterrible on 2007-07-26
update, dont know if it can help

while i was palying around i decide to try VNC. it works just fine, so i am not so sure anymore that the problem is in the network: the 2 pc talk to each other fine! (and fast)

---

### Post by punx45 on 2007-07-26
im still stumped on the NFS issue.   but i have an "is it plugged in" type suggestion for the /media/hdc1.
im guessing by the disk's mount point that it was automatically detected and mounted at installation, in which case it would be owned by root, meaning that you would have to chmod it with sudo.

---

### Post by enfantterrible on 2007-07-26
i also think hdc1 is owned by root, but i am trying with other folders as well - with no luck.
further, i think that if it was a permission problem, i would get a "permission denied" error rather than a "server is down" error... but at this moment i am very confused

---

### Post by punx45 on 2007-07-26
you cant chmod other folders either?   or you mean you are having no luck sharing other folders.

i agree that permissions arent the problem.  you may have to resort to reinstalling NFS.   but, since you are getting along ok with VNC now, you might not even need to bother with it anymore.

---

### Post by enfantterrible on 2007-07-26
can i use  vnc to move files from one pc to the other? when i used ultravnc in windows, there was a two-window file manager who copied evertyhing from everywhere to everywhere, shared or not shared...

---

### Post by scxtt on 2007-07-27
what NFS package do you have installed? (post the output of **aptitude search nfs**) ...

also, what's the output of the following:

ps -ef | egrep "nfs|stat|rpc"
sudo iptables -L

i doubt you can use the version of VNC offered to xfer files. really doubt it ...

---

### Post by enfantterrible on 2007-07-28
hi everybody

unfortunately (ahaha) i am on vacation visiting my parents, all trials will have to wait a couple of weeks...

it might be worth trying reinstalling the server... i will keep you posted!

thanks again to everybdy from a sunny italy

---

### Post by punkybouy on 2007-08-13
You might try installing Wireshark as root  and then run a network trace and see what is happening at the packet level.  I used Wireshark to fix a Samba problem.

---

