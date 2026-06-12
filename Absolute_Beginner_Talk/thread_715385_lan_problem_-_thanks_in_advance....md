---
title: "lan problem - thanks in advance..."
date: 2008-03-04
forum: Absolute Beginner Talk
---

### Post by systemOAD on 2008-03-04
i just installed ubuntu gutsy and have it working well. but i have two problems, i have a pc which my family uses in the same home network as my laptop which has gutsy running on it. the prblem is that i cannot access my desktop, or the three other laptops we have in the house that have windows on them. (im slowly trying to convert my family to linux)i cannot access those from my laptop and vice versa. so my ubuntu cannot access the pcs and the pcs cannot access my ubuntu machine, and i tried installing samba but it was worthless and did not function at all despite all the tutorials i read. so if anyone can help we set up my network so i can have interaction with my pc and ubuntu machine that would be appreciated thanks in advance!

sorry for the post being long...just wanted to get this fixed. thanks.



long live open source

---

### Post by Joeb454 on 2008-03-04
I think this might be an issue with Samba...

For example I can access my Windows shares (I added samba through synaptic) but they cannot access my Ubuntu shares.

It might not be samba, if somebody could clarify that'd be great :)

---

### Post by mrsteveman1 on 2008-03-04
Samba is basically just a server, to use the Linux machine to access other shares or windows machines you need to use an SMB client, and one of them happens to come with Ubuntu (the network shares/places thing in the menu).

However to access shares on linux machines from anywhere else, samba does need to be configured correctly. Samba isn't the easiest thing to setup, thats for sure. If you can't even see the machines, its a netbios name problem and you probably need to be running NMBD somewhere.

What does your /etc/samba/smb.conf file look like?

---

### Post by ryanhaigh on 2008-03-04
Can you ping between the windows and ubuntu machines?
systemOAD are you talking about accessing shared folders or something else like remote desktop?

---

### Post by systemOAD on 2008-03-04
ryanhaigh,

i can neither ping from ubuntu to pc nor from pc to ubuntu, but pretty much i am talking about accessing shared folders because i have a lot of music on the desktop(pc) which i want to access with my laptop (ubuntu).

p.s. i also have a few questions about remote desktop which im trying to set up but thats a whole another topic lol. once i get my network working...i ll ask about that. thanks a lot.

---

### Post by ryanhaigh on 2008-03-04
What hardware are you using to connect the computers?
Do you know how network addresses are being assigned?
Once we establish a network connection we will work on samba and rdp both of which are quite simple for a basic setup such as the one you want.

---

### Post by systemOAD on 2008-03-04
i dont know what kind of network addresses are being assigned but as far as hardware goes, im using a netgear wireless router which is hardwired into the desktop, and my laptop has an intel pro wireless network adapter.

i dont really know what network addresses assigning is and rdp is, can you explain real quick? thanks.

---

### Post by paydaydaddy on 2008-03-05
This is the best how-to for samba file sharing that I have seen.
[http://ubuntuforums.org/showthread.php?t=202605&highlight=stormbringer](http://ubuntuforums.org/showthread.php?t=202605&highlight=stormbringer)

---

### Post by ryanhaigh on 2008-03-05
network address assignment is how computers on a network get an ip address which is needed for communication between the comptuers, on a small network such as yours the ip should be similar with the last digits different. network addresses can be assigned either statically or automatically which is most likely the case here where your router is doing the assigning, you can confirm this on xp by looking at the status of the lan connection (control panel>network connections >local area conn. right click status and the support tab should show you your ipaddress and that it was assigned by dhcp, make a note of the ip address, subnet mask and default gateway and post them here)

RDP = remote desktop protocol

So when running the laptop under ubuntu can you connect to the wireless router? 
Can you browse the web?
What is the ip address of the ubuntu computer when connected (right click on the wirless indicator on the panel and go to connection information)?

---

### Post by oedha on 2008-03-05
can you open places - home folder
then change the location into text box......(by click on paper pencil icon)
type smb:///
did you see anything ?
if yes...maybe you can try to explore that windows network
and make sure your windows folder have been shared

---

### Post by systemOAD on 2008-03-05
paydaydaddy: 
i went to the link you posted, followed the instructions letter to letter word to word and still did not work so i uninstalled samba and gave up; btw this happened before i started this post. thanks for your reply though.

oedha:
places > homefolder > typed in smb:/// and nothing happened

ryanhaigh:
so from ubuntu, i can access the web, and my laptop does connect to my router no problem. i just cannot access my desktop and the other pcs. but i do have internet connection from my ubuntu machine, and it does connect to my netgear router.

btw,
my ip is 192.168.0.3 (ubuntu)

---

### Post by ryanhaigh on 2008-03-05
Have you got a software firewall on your windows xp machine. It seems very strange to me that you cannot ping between the two machines on the same network when the network itself is obvioulsly working. How did you try to ping between them.

Can you ping the ubuntu machine using the ip address from the windows machine
start>run>ping 192.168.0.3 -t (press ctrl+c to stop the pinging and close the window)

What is the ip address of the windows machine? Find that out and then try accessing the windows machine by that ip from ubuntu.
smb://ip.add.goes.here

If that doesn't work the only thing that I can think of is that your windows machine is blocking windows file sharing or you aren't actually sharing anything, have you ever connected to a share using another computer, I know you have other laptops there but it is not clear whether you have used filesharing between them.

---

### Post by systemOAD on 2008-03-05
ryan thanks a lot!
the smb://ipaddress worked, and i was able to ping both ways. does this mean i have samba installed on my computer? what is really going on behind the scenes?
just one tiny problem though...
i can access the music on my desktop, but i cannot play it in banshee for some reason. i can play it in movie player, but not banshee for some reason. do you know why that could be?
either way, thanks for resolving the problem.

i also want to set up remote desktop on my ubuntu machine, such that i can access my laptop from anywhere and i am able to control the mouse and keyboard, and etc.. i tried ssh, but that did not help. 
also, i was wondering if FROM my ubuntu machine, can i access my friends computer who lives on the other side of town? 

thanks again for all your help.

---

### Post by mrsteveman1 on 2008-03-05
Most ISPs block the SMB ports because of security concerns, the only way to use samba shares across the internet is to do more complicated setups like VPN, tunneling etc.

---

### Post by ryanhaigh on 2008-03-06
It means that samba client is working, but if you aren't able to connect using the name I believe this is something to do with netbios, what happens if you do
```
nmblookup windowscomputername
```

Banshee will not be able to play because of a limitation in the way gnome handles remote filesystems, this may be fixed in the next release of ubuntu, until then you can try to live with using totem (the movie player) or mount the samba share permanently so that it looks like a local filesystem. [This thread]("http://ubuntuforums.org/showthread.php?t=280473") may help you with that but I don't know how it handles this if you are not on the network (taken laptop to work), this forum or google can probably give you info on that.

Remote desktop:
To control your ubuntu machine go to system>preferences>remote desktop and enable it. You will then need vnc client on windows to access the ubuntu desktop. [More info here]("https://help.ubuntu.com/community/VNC").
To control a windows computer: if its windows xp pro you can connect to the built in remote desktop client otherwise I use vnc for that as well. I personally use tightvnc as my parents connection is quite slow and its available for windows and linux. If you want to look at doing this accross town you will need to know about port forwarding, the VNC howto I linked to has information on how to do this.

If you are in fact talking about filesharing over the internet to your mates pc then the best solution is probably ssh. Obviously there is an ssh server for ubuntu but there are also free windows ssh servers. Then you can use [winscp ]("http://portableapps.com/apps/internet/winscp_portable") to access ubuntu shares and use ssh://friends.internet.address in ubuntu.

---

### Post by systemOAD on 2008-03-07
when i type nmblookup mydesktopname, i get an error message - "name_query failed..."
any clue? 
thanks

---

### Post by ryanhaigh on 2008-03-07
Can you please see if you have nmbd running. It is the netbios name server that is used to do lookups by computer name.
```
ps ax  | grep nmbd
```
You should get a line with something like:
/usr/sbin/nmbd -D

I noticed that you said you have uninstalled samba and as nmbd is part of that suite I don't know whether you would have removed it by removing samba, 

You may also want to make sure you are using the same workgroup for both systems. Go to system>admin>shared folders > general tab and put in you workgroup.

---

### Post by systemOAD on 2008-03-07
yeah i noticed that i dont have nmbd, how do it go about getting it?
also, just a quick question on the side - can i have clam antivirus running on my linux partition even though i have norton running on my windows partition? or is this going to cause some kind of a problem?

---

### Post by ryanhaigh on 2008-03-07
As far as the anti-virus is concerned the only thing I can think of is that clamav will try and do something with nortons quarantined items, but I don't know what sort of an impact that will have as I do not use AV on my windows vm.

To install nmdb you will probably have to install samba, I would move the /etc/samba folder to /etc/samba_old or something so that maybe it will generate a new config for you and you can use ubuntus GUI tools to try sharing the folders you want. Don't forget to use:
```
smbpasswd -a -e yourusername 
```
This enables you to connect to the shares via a user/password. Once done, try connecting by computername to the windows box and from win to ubuntu by both IP and computer name and let us know how it goes.

---

