---
title: "How do I connect Ubuntu to a lan?"
date: 2006-10-22
forum: Absolute Beginner Talk
---

### Post by Graybeard on 2006-10-22
I have two boxes, one running WinXP Pro SP2, the other running Ubuntu 6.06 LTS. They both connect to the internet via a BEC-7402-t DSL Router. Connecting them was as simple as plugging in the cables and letting each box do it's own thing. The tech support at the ISP that provided the DSL Router tells me that yes, the device can be used as a router for sharing files between the two computers but they provide support only for the DSL functions. 

From the XP box I ran the Network Setup Wizard and then set the data partition on that box to be shared on the lan.

Newbie questions: 
How do I set up the Ubuntu box to connect to the router?
How do I share data on the Ubuntu box on the lan?
How do I set up Ubuntu to use the printer connected to the XP box?
Do I need to "mount" the router or the Data partition on the XP box? If so, how?

My hunch is that the answers are so elementary or so obvious that I'm looking right past them but I've been banging my head for two days now without any progress.

Thanks, from the ignorant to the patient knowledgeable.

---

### Post by SoloSalsa on 2006-10-22
I haven't done this myself, but I think people always point to Samba.  I don't know how to get it, probably a quick search will take care of it.  Anyway, Samba is a program that lets Windows and Linux 'see' each other on the network.
The printer will also work, but it's not as obvious.  I don't know how to go about doing it; I just know it *can* be done.

---

### Post by bigken on 2006-10-22
open a terminal type 

sudo aptitude install samba

then type 

sudo smbpasswd -a (your name)

type a password 

then type 

sudo smbpasswd -e (your name)


sytstem/administration/ shared folders to add your shares ;)

---

### Post by Graybeard on 2006-10-22
> **bigken said:**
> open a terminal type 

sudo aptitude install samba

then type 

sudo smbpasswd -a (your name)

type a password 

then type 

sudo smbpasswd -e (your name)


sytstem/administration/ shared folders to add your shares ;)

OK, I installed Samba using Synaptic Package Manager, then opened a terminal and did:

bob@bob-dell:~$ sudo smbpasswd -a bob
Password:
New SMB password:
Retype new SMB password:
Unable to open/create TDB passwd
Unable to open/create TDB passwd
pdb_getsampwnam: TDB passwd (/var/lib/samba/passdb.tdb) did not exist. File successfully created.
Segmentation fault
bob@bob-dell:~$

Do these messages mean I have a problem?

Will I have to do this every time I begin a session or will it all happen automatically?

P.S. There is reason why I posted this in "absolute beginners"

bob

---

### Post by rccharles on 2006-10-22
> **Graybeard said:**
> 
Do I need to "mount" the router or the Data partition on the XP box? If so, how?



In Ubuntu:
 Places -> Network Servers -> Windows Networks


( The word places appears at the top of the display. )

Robert

---

### Post by bigken on 2006-10-23
> **Graybeard said:**
> OK, I installed Samba using Synaptic Package Manager, then opened a terminal and did:

bob@bob-dell:~$ sudo smbpasswd -a bob
Password:
New SMB password:
Retype new SMB password:
Unable to open/create TDB passwd
Unable to open/create TDB passwd
pdb_getsampwnam: TDB passwd (/var/lib/samba/passdb.tdb) did not exist. File successfully created.
Segmentation fault
bob@bob-dell:~$

Do these messages mean I have a problem?

Will I have to do this every time I begin a session or will it all happen automatically?

P.S. There is reason why I posted this in "absolute beginners"

bob


dont know does it work :-k

---

### Post by louieb on 2006-10-23
Just wondering. I have a couple of questions.
 > How do I set up the Ubuntu box to connect to the router?
If the linux box can connect to the internet then it is connected to the router.
> How do I set up Ubuntu to use the printer connected to the XP box?
SAMBA was set up automaticly when I installed Ubuntu. Have you tried: System>Adminstration>Printers>Add Printer>Network Printer?
You will need to provide it with an XP User and if the user has one the password. Unless you have a Lexmark printer that should work.

---

### Post by Graybeard on 2006-10-23
"Does it work?"

As far as I can tell, no, but I understand so little that brief instructions leave so much unsaid that steps that may seem obvious to others are not obvious at all to me. It may be that I just don't know what to do to **try** to make it work.

The XP box "sees" the router as a router but doesn't "see" the partitions on the Ubuntu box that I set to be shared.

The Ubuntu box accesses the internet via the router but as far as I can tell doesn't "see" the shared partitions on the XP box.

I guess what I really need (given my ignorance) is a detailed check-list of tasks to perform. 

FYI, if I enter the IP address in a browser tab from the Ubuntu box it does connect to the router interface and provides a wealth of information that I understand very little of.

bob

---

### Post by Graybeard on 2006-10-23
> **louieb said:**
> Just wondering. I have a couple of questions.
 
If the linux box can connect to the internet then it is connected to the router.

SAMBA was set up automaticly when I installed Ubuntu. Have you tried: System>Adminstration>Printers>Add Printer>Network Printer?
You will need to provide it with an XP User and if the user has one the password. Unless you have a Lexmark printer that should work.
I tried Louieb's advice.
I got as far as "select a PPD file" and had no idea what to do next, not knowing what a PPD file is or where to find one.
bob

---

### Post by louieb on 2006-10-25
Ok two more things to check.
In windows is shareing turned on for the printer?
If yes the back to linux.
System>Adminstration>Printers>Add Printer>Network Printer?
After you click the network printer radio button. Click on the drop down box to the right and choose SMB windows printer.
It will ask for user and password.
Next you will see a screen with host and printer dropdown boxes. 
Click the host drop down. If things go right a list of computers on your network will show up. Click on the one that the printer is attached to.
Click on the printer drop down box. If things are still going really right the printer will be listed. Click on it. 
At this time it might ask some questions about printer drivers. Just go with the defaults. 
At this point it will offer to print a test page. 
If that work you are setup.

---

### Post by Graybeard on 2006-10-25
> **louieb said:**
> 

Louieb,
Thanks for sticking with me.

Since my last post I got a USB KVM switch that solved the printer problem. The printer connects to the KVM and both boxes can use it.

The remaining problem, which is the bigger problem, is to get the Linux box to read and write to a FAT32 partition on the XP box. I don't go online from a Microsoft OS---too many holes. So to download or upload data from the XP box's FAT partition, the Linux box needs to read and write to the XP box's FAT partition. 

I've been the dual-boot route; I've used Win4Lin from within Xandros; I've used a Ubuntu appliance in VMware Player. All of them have serious drawbacks. So when I discovered that my DSL interface was also a router I decided to put Linux on an older box and network it to the better box running XP. Now I need to get them to talk to each other in a more elegant way than CD's or FLASH sticks.

Right now, both boxes are able to access the internet via the DSL/router but neither one can "see" the file systems on the other.

bob

---

### Post by louieb on 2006-10-26
Like you I have an XP box and a Linux box, both connected to a router with wire. The good news is somehow I finally got to the point where I can see files on them over the network. The bad news is I don't exactly remember what I did to get there. 
My XP Box uses NTFS exclusively. In XP I had to mark the folders I wanted Linux to read/write as being shared. After I did that then Linux could see the shared folder on my XP box 
@ Places>NetworkServers>WindowsNetwork>NetworkName>CompterName>FolderName.

Start by trying that. I got to go to work now. I will get back later. 

Since Fat32 does not support file sharing permissions at the folder or file level I assume you will have to tell XP to share the drive.

---

### Post by Graybeard on 2006-10-26
Further poking around has made progress, but not success yet.

I went to Places>Network Servers.
There I found "Windows Network."
Right clicking and selecting "properties" and then clicking the "Permissions" tab I find that   Owner, Group, and Others have "read" access but not "write" or "execute" privileges. It also shows file owner and group as "unknown" and of course won't let me change the permissions. Note, this is not permissions for the partitions or directories on the XP box, it is permissions for the Windows Network in Ubuntu.

Double clicking Windows Network, then "bob" (my user name) then "FLY" (the name of the XP box) it displays the partitions on the XP box and allows me to navigate to documents and open them, but not to write back to the location. This is definitely progress--I now know that I do have a functioning network even if it's not currently usable.

A corresponding problem is that even if I get the permissions granted, the "save file" window displayed by a Linux application has no obvious way of navigating to the network. How do I manage that????  My guess is that it is somewhere in the wilderness of the Linux file system but I don't even know what to search for. Hopefully, once found, I can put a link to it on the Linux desktop.

bob

---

### Post by louieb on 2006-10-27
I was just looking around my network trying stuff out. 
[LIST]
[*]Linux has an icon on the desktop for one of my windows shared folders.
[*]Linux can see my shared direcories but can't read them
[*]In XP: MyComputer>NetworkPlaces>ViewWorkgroupComputers(on the left)>gameu(my linux computer name) I can see and read my shared files.
[/LIST]
I am going through the Samba section of O'Reilly's Running Linux.
It appears that geting windows and Linux to talk smoothly is going to require some more work. There is some stuff about DNS and WINS servers setup, using static IP addressing. When I find the time to do it will get back to you. 
If you find some set by step directions on how to make XP and Ubuntu share files easily let me know and I will do the same. 
I guess it time fore me to follow my own advise and Google it.

---

### Post by Graybeard on 2006-10-27
Louieb,
I have to be gone until Sunday PM.  I, too, will do some more research including a careful look through "HOW-TO: Setup Samba peer-to-peer with Windows" and post anything that seems important.
b

---

### Post by louieb on 2006-10-28
I finally figured out how to read/write/edit files stored on the XP box from the Ubuntu box. We were so close.
[LIST]
[*]In windows open up my computer. and for each folder you want to edit from Linux Right click>Sharing and Security. There is a section called network sharing and security. Check both boxed in this section and give the folder a share name. I found that I had to check the write access box in order to read the files in the folder too. 
[*]Now back to Linux Places>NetworkServers>WindowsNetwork>ServerName>
[*]You now have a list of the folders you marked as shared in windows.
[*]Right Cick > Connect to this Server. and now when you display your desktop there will be an icon for that folder.
[/LIST]

---

### Post by Graybeard on 2006-10-29
Louieb,
Great! I can now read and write to files on the XP box's VFAT partition. From the Ubuntu box I get to them via the Places>Network Servers> and so on routine. I can then open them in a suitable app, modify them, and save them with the changes. The Ubuntu box obviously knows where to save them because I can switch back to the XP box, open the changed file with an app on the XP box, and the changes made on the Ubuntu box are there. 

The one remaining hurdle is specifying a location for "save as" or saving a new document on the XP box. The productivity apps all use the Nautilus File manager to find locations and I can't find my way to the Windows Network from the Nautilus file manager. I mentioned this a couple posts ago where I said "...the "save file" window displayed by a Linux application has no obvious way of navigating to the network. How do I manage that???? My guess is that it is somewhere in the wilderness of the Linux file system but I don't even know what to search for. Hopefully, once found, I can put a link to it on the Linux desktop." 

I suppose I could create a folder in the Ubuntu file structure and save to that, then go to Places>Network Servers etc. and drag and drop but there must be a more elegant way to do it directly. Do you happen to know how? or have any suggestions?

b

---

### Post by louieb on 2006-10-30
I just opened an text file in gedit and then I did a save as just to see what was there. Clicked browse other folders. guess what?  The shared folders on my XP PC were listed. I clicked on one of them and save the file on the XP box. I went over to the XP machine and it is there.
So try File>SaveAs>BrowseOtherFolders and see if that works for you.

In XP its File>SaveAs>MyNetworkPlace to get a list of Shared folders on the network (including your Linux machine shares).

Earlier in the day I use Places>ConnectToServer to establish an FTP connection to the server that host my web site. 
Not only were my local nerwork shares listed but the FTP connection was listed to. Verry nice.

---

### Post by Graybeard on 2006-10-30
That's exactly what I did expecting exactly the results that you got, but didn't. When I open "Browse other folders" the XP box shares don't appear and there's no way to navigate to them. 

To get to the XP box from "Places" I have to click "Network Places" and then burrow down. From the File Save window of applications, including gedit, I can't get to the network at all.  There must be something I haven't done in setting this up, and I don't know what it might be.

bob

---

### Post by Graybeard on 2006-10-31
Louieb,

Oh, foolish, foolish me. Finding that I could read and write to a folder on the XP-box, I assumed that I was "connected" to that box. But in this Alice-in-Wonderland world of Linux, words take on meanings that one might never suspect. 

In an idle moment I violated my basic rule of "Don't fix what ain't broke" and went to Places>Connect-to-Server and "connected" to the XP-box that I could already read and write to. 'Lo and behold, the desired drive on the XP-box appeared on the Linux-box desktop and can now be accessed from the "Save" window of an Ubuntu application on the Linux box.

Problem solved, irritation not yet subsided. Many thanks for sticking with me through this journey. We definetely aren't in Kansas anymore.

bob

---

