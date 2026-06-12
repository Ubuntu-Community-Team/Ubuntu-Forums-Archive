---
title: "Sharing a folder with my other XP computers"
date: 2006-10-12
forum: Absolute Beginner Talk
---

### Post by fern on 2006-10-12
Hi,

Just installed Ubuntu.  I honestly love it, because it is so "liberating".  But not all is perfect.

1.  I have a home network with 3 XP computers and now this Ubuntu machine.  I had no problem at all making "My Documents" in all three XP machines visible and usable to the other machines.

2.  Just installed Ubuntu in this fourth machine, and it is a pretty cool OS, which does quite a few things out of the box, so-to-speak.

3.  Very important:  Without doing absolutely anything, my Ubuntu machine can see the "My Documents" in my three XP machines.  It can also see that I have a home network with the name I gave it.  Most important, my Ubuntu machine can access the My Documents folders in all three XP machines without a problem, I can copy and paste, etc.

4.  I have created a folder in my Ubuntu machine called "My Documents Ubuntu" (lots of immagination, isn't it?), and I want to share this folder with my other three XP machines.  Following instructions I found, and some intuition, I did the right-clicking on the folder's name, Share Folder, and...

5.  I was asked to install the Ubuntu CD (install, not "run from CD") in the drive, and that installed Samba, I think. The folder sharing process was finished, apparently successfully.

6.  I cannot tell whether the folder is really shared, because when right-click on it and look at Properties, nothing there indicates to me that it is reallly shared.

7.  I, then, assume it is shared and go to any of my XP machines and...  can't see the shared folder "My Documents Ubuntu" at all.  In My Computer and My Network Places I can see the other XP machines, their shared folders, but the Ubuntu is a complete no-show.

So.

* I would like to know how to make my Ubuntu machine share its folders ("My Documents Ubuntu" in particular, but the process should apply to any folder I have the priviledge to share), and make them usable by the XP machines.  Considering that Ubuntu can see and use the XP shared folders, this should be a piece of cake.  No?

I have another request related to the "how-to".  Knowing nothing about the inner works of Ubuntu, I'd appreciate a step-by-step point and click procedure.  Of course I can type a name, but I honestly don't want to be typing coded command lines, things like "sudo this" and "sudo that", or "root-this-and-that".  I truly believe that if Ubuntu is to make it out there, it has to be as easy to use as Windows XP (yes, XP is easy to use).  Even if I end up knowing how to use the Terminal, the same way I know how to run ipconfig or msconfig, I am at a stage in Ubuntu where I need it to do fundamental funcions first, and those OUGHT to be simple to do.  I don't believe that users should have to have any "joy" in learning how to use The Terminal.   Later, if I have the time (of which I have lots), I will dive into the coded command line business, but not for now.  If Ubuntu can't share a folder in a point-and-click fashion, that is OK, I'll be happy just to know that.:D 
 

Please someone let me know how to make my Ubuntu really share its shared folders.

Thank you very, very much

Fern

---

### Post by kilgore t on 2006-10-12
bump because I have the same issue.  Installed Samba.

I can get to my winxp 'shared documents' folder from my ubuntu install, but not vice versa.

I can 'see' the ubuntu PC on my network from the windows PC (by searching for the ubuntu rig's static IP) but can't access it.  There is a login/pw but my root login/pw do not work.

---

### Post by adje on 2006-10-12
Ditto for me. Same issue. Any gurus out there?

---

### Post by fern on 2006-10-13
Hi, All

From the fact that there are others with the same problem, and the lack of enthusiastic responses...  is this an indication that the best solution for the simplest Ubuntu problems seems to be installing Windows XP?  Or should I not give up just yet?

I am willing to try even the "sudo-this" or "sudo-that" solutions, if there are any...


Thank you all for any help.

Fern

---

### Post by junglepeanut on 2006-10-13
OK, I am not doing any of the following things that you have done. But I have a little knowledge (means I am stupid and don't trust my answer).

Your terminal commands are basically what are distracting you, nobody feels the need to create a gui when the cli commands are straightforward configuring of a file. The only reason you need sudo is the file is protected. In other words you could edit it with anything if the anything program has root priviledges, (just like new the new windows os will be).

I just got this from doing a search on here and looking at what needed to be done. I would do it myself but I no longer have xp to test against and confirm to you a way that does not  involve the terminal minimally.

Junk below 
If the methods listed in the search do not work, (I am guessing here) then you have an xp issue. Similar to how Ubuntu will see an XP partition but XP does not see the ubuntu partition. The rememdy for this is downloading the proper XP software, I believe. So maybe it is a problem with XP.

Big Junk below
I can only say with guarantee that I can work and see with mac and linux both ways easily. Mostly when I help students with there windows programs it turns out they do not have the right software installed on their windows pcs to do everything needed.

---

### Post by willca on 2006-10-13
You are almost there. Installing Samba is one of way of file sharing with XP boxes. 

You need to configure your smb.conf (normally in /etc/smb.conf), that it has the same workgroup info as the XP boxes. From there you can also set which folders to share and even specify users.

HTH

Cheers-
-W

---

### Post by willca on 2006-10-13
Here is thread on how to do this. Good luck.

[http://www.ubuntuforums.org/showthread.php?t=202605](http://www.ubuntuforums.org/showthread.php?t=202605)

---

### Post by fern on 2006-10-14
Gosh...  I'm going back to being a geek...

Haven't tried the procedure yet, but I will.  I will.   I will.

Thanks!

Fern

---

### Post by usugar on 2006-10-14
Willca,

Appreciate the advice mate but can this really be the solution? Ubuntu provides us with a nice GUI-based way of configuring the share yet using it isn't quite enough... so we then have to navigate a complex set of sudo commands and editing of configuration files to actually get it working?  Surely not...

---

### Post by fern on 2006-10-14
Hi, All

Well...  If this is the best that Ubuntu can do to make itself visible in something as simple as a home net, then Microsoft definitely doesn't have anything to worry about.

Quite frankly, this editing of samba.config thing (or whatever it is called) with zillions of possibilities for a user to make a mistake is absurdly ridiculous.

As the last reply says, this Windows look-alike "human" interface is nothing but a make-believe, half-done presentation.

Every time there is a question of any kind at all in all the forums I've been, all answers are a bunch of command lines and a bunch of text editing Unix code language.  Gosh, fellows, this is worse than "last century".

This is OK for people like me, who don't have anything else to do, or for people who take this as entertainment. who have the time and the inclination to be hacking all over the place and blowing up the system everytime we edit something wrong.  This is definitely not OK for a system that has even the most basic responsibility to import a file in something as basic as a home network.

I know this is an "open system", all the work done by volunteers, and a beauatiful concept, no doubt, but it is time someone shake the tree and say "Set up of anything cannot require Terminal".

Having said that, I appreciate the help of those who kindly answered my question.  I'll keep trying, but very disappointed.

Thanks, all

Fern

---

### Post by Stettin on 2006-10-14
> **fern said:**
> Gosh...  I'm going back to being a geek...

Haven't tried the procedure yet, but I will.  I will.   I will.

Thanks!

Fern

That guide does work like a charm. It took me about 10-15mins to get everything set when I used it. For those that can't follow a simple guide and cut and paste text from a sample config file, they should probably stick to Winbloze.

---

### Post by usugar on 2006-10-15
> **Stettin said:**
> That guide does work like a charm. It took me about 10-15mins to get everything set when I used it. For those that can't follow a simple guide and cut and paste text from a sample config file, they should probably stick to Winbloze.

Stettin, with all due respect mate I think you're missing the point here.  If you have to edit a config file in a terminal window, then fair enough and I'm sure most of us could manage that.  But if that's what you have to do then what is the point of having a GUI facility to set up a share that doesn't, in fact, work and you have to go and edit files in a terminal window anyway?

Remember, Ubuntu is supposed to be an OS that "just works".  Comments like yours just reinforce the perception that the Linux community is only for clever people who understand command lines and configuration files, and the rest of us should give up and use Windows.  My understanding is that that's exactly the opposite of what Ubuntu's trying to achieve.

---

### Post by usugar on 2006-10-15
By the way, for everyone having this problem, the solution suggested by docshawnc here

[http://www.ubuntuforums.org/showthread.php?p=1620662#post1620662](http://www.ubuntuforums.org/showthread.php?p=1620662#post1620662)

worked perfectly for me.  Thanks docshawnc!

---

### Post by junglepeanut on 2006-10-15
You could write a gui for it then it could be added to the repositories or maybe even samba itself.

---

### Post by Stettin on 2006-10-15
> **usugar said:**
> Stettin, with all due respect mate I think you're missing the point here.  If you have to edit a config file in a terminal window, then fair enough and I'm sure most of us could manage that.  But if that's what you have to do then what is the point of having a GUI facility to set up a share that doesn't, in fact, work and you have to go and edit files in a terminal window anyway?

Remember, Ubuntu is supposed to be an OS that "just works".  Comments like yours just reinforce the perception that the Linux community is only for clever people who understand command lines and configuration files, and the rest of us should give up and use Windows.  My understanding is that that's exactly the opposite of what Ubuntu's trying to achieve.

](*,) 
I think you're missing the point also. I really have little understanding of what I actually did when following the guide. I don't know what all the switches and config setting are really doing. There is no need to understand command lines and config files like you state. All I did was copy/paste the commands in the order the steps were listed. Everything worked as described by the guide. I don't really see how that is any different than someone reading a guide for windows and completing the steps needed to set up a home network in XP. Sure there is console input, but it's not like you have to look up what the commands mean, you are just copy and pasting. 

I'll stick with my previous statement and add that if you can't copy and paste from a guide, maybe Ubuntu isn't for you. I'm sure Ubuntu or some other distro will eventually be as GUI friendly as M$, but I agree that is still a ways off.

---

### Post by SuperGrover21 on 2006-10-15
Please save political commentary for the school yard, after class. Let's stick to the Help Forum! Thanks all for the pointers, has helped me out.
;)

---

### Post by fern on 2006-10-15
First, GUI, forever.  The Terminal is something that should be avoided like the plague.  Period.

Having said that, I compiled all the how-tos I found in one procedure with ONLY ONE entry in The Terminal!  This entry is to create a password for the network user, which is necessary for logging into the Ubuntu system from one of the other systems in your home network (hidden information, like hiding the root user, but I found that one, too).  This Terminal entry is to modify SMB, the networking software.   There is a second entry in The Terminal, but that is just to create and edit a certain file for SMB, and it can be done with the Text Editor and a simple "Save". I listed the entry in The Terminal, and mention the possibility of doing it with the Text Editor.

The text is long.  It is written for someone who has, like me, no clue of what is going on, someone who just wants to be a user.

This procedure will add the Ubuntu system to the home network with other Windows XP machines, will allow it to access those machines' shared folers and printers, and will allow access to its own shared folders from the Windows XP systems.

Use it at your own risk.  I tested the procedure to the best of my ability and it seems to work an be repeatable.  I am no expert on this at all, just a user, but if you have any questions about the procedure send me an e-mail at [email]fernmarques@yahoo.com[/email].  If you don't like the procedure, don't use it. I didn't revise my typing too much, so please turn a blind eye to typos and grammar.  Here it goes.

Ubuntu

Installing an Ubuntu computer in a home network (with Windows XP machines)

I have aversion to The Terminal.  I don't accept that any set-up procedures should require the user to be typing coded commands, things like "sudo blah-blah-blah".  But I installed Ubuntu into an old laptop and I love it.  So, here is the procedure to home-network it, with a very minimum of "sudos". 

I will assume that the main purpose of a home network is to share information (folders that contain files) and resources (disk space and printers).

The procedure describe here will make folders and printers in another home network system available to the Ubuntu machine.

I will also assume that, when you login, you are the "initial user", who has privileges to do administrative funcions. (By the way, I do believe that hiding the "root" user from the owner of an Ubuntu machine is ridiculous, and I found out how to be the root user)

The home network requires a physical connection for all computers involved.  The most common that I know is a “router”.  A router is a box that functions as a "hub" for connecting more than one computer to a single Internet high-speed service.  The service provider will give you a land line and a modem, which has one connector for your computer.  The router, which you must buy separately from a computer store, connects to it through that connector, but it has various connectors for various computers, usually 4.  I know of two types of routers.  There are the ones that connect to the various computers using cables.  But many routers these days are “wireless”.  This means they connect to the modem via a cable, but connect to the various computers via radio waves.  The range is limited and the security issues may be important, but that is for another talk.  I believe the procedure described here is the same for both wired and wireless routers.

So, your computers are all physically connected to a router, via cables or "wireless".

The Home Network requires some setting up.  Do the Windows machine(s) first.

Start by "sharing" the folders / printers you want to be visible and usable from the other computers.  To share a folder in a Windows XP machine, rigth click on it and press "Share".  That should be a simple-enough procedure, but this is a "Ubunto" set up, so, you'll have to go somewhere else to figure it out if you can't do it by yourself.

The instructions for setting up a home network in a Windows XP machine are readily available from Microsoft.  If you don't know how, go to microsoft.com, search for “home network”, and pick “Setting up a home network”.  It is quite a comprehensive, step-by-step procedure, as procedures should be.  Follow the Microsoft instructions and, with the Netwok Wizard you'll have a home network in no time. 

I strongly recommend you use the default settings, including the name of your home network.  Leave it as the Wizard calls it, "mshome".  It will be easier that way. 

It is possible you only have one other computer running Windows XP, so you can't test your home network until you make the Ubuntu machine participate in it.

Surprisingly enough, the Ubuntu machine will “see” and be able to access those resources right away, at least the folders will be available.  But that is not enough, of course; you need to give the  Windows machine(s) access to the Ubuntu machine.

To test that, in your Ubuntu machine go

Places > Network Servers

A File Browser will open and it will be showing your Windows Network.   Doube-click on it and the browser goes "down one level", now showing "mshome" on the right side of the pane.  Double-click on that and the browser goes down one more level, showing, on the right side, the other machines participating in the mshome network.  Double-click one one of them and the shared folders it contains will be there, available for use.   I was amazed.  You can immediately accees the shared folders of those machines from your Ubuntu system.

To make the Ubuntu system visible and usable by the other Windows XP machines in your home network is a bit more involved.  I did the following:

*  "Share" a folder

*  Create a network user and give it a password

*  Add a "network" printer to your Ubuntu system, one that shared, connected to one of the Windows XP machines in the home network.

Then your Windows machine(s) will be able to access the Ubuntu system and vice-versa.

Let’s start by sharing a folder in your Ubunto system.  You can share more than one, of course, but start with one and go from there as you become more familiar with this stuff.

First, make sure the folder to be shared has a name with one word only.  Ubuntu gets all confused with names like “My Documents”.  I created a folder called “MyDocumentsU”, one single word.  From my other systems in the house I'll know that is the equivalent to my othe "My Documents", and the "U" indicates "Ubuntu".

After the folder is created:

Places

Navigate to the folder, Right click on it, Choose “Share folder”

A window opens

Share with SMB

SMB is some networking software affectionately called "Samba".

If you don't have Samba installed, you'll have to install it.  Relax, it is automatic and it comes in the same CD where you got Ubuntu from.

If this is the first folder you share, it will ask for Samba.  Keep clicking, following your intuition and it will ask for the Installation CD.  Put it in the CD drive and Samba will install by itself.  At the end of the install Samba (SMB) will be running, your computer will be part of the home network, but the folder isn't shared yet.  To really share it:

Go back to Places, Navigate to the folder, Right click on it, Choose “Share” again.

Enter the parameters:

Share with SMB

Verify the name is correct

Check “Allow browsing folder”

Click on Windows Sharing Settings

Host description is probably correct

Domain/Workgroup is “mshome” or “MSHOME”

WINS server, dot in “Do not use WINS server”

The folder is now shared.  To verify, go

System

Administration

Shared folders

A dialogue window will appear with your shared folder in it.

If you try now from the other machines in the home network, the Ubuntu machine will show up, but you still can't access anything.  Please note that it takes a while for the other machines to see the Ubuntu machine.  Here is what you do to see the Ubuntu system from a Windows XP machine in the mshome network:

With Windows Explorer, open My Network Places (just under My Computer)

My Network Places
Entire Network
Microsoft Windows Network
MShome

And there will be your Ubuntu machine listed

Double click on it, and it will show a window asking for username and password.  You are stuck.  But just for now.

For Ubuntu to share its folder with the other systems, you have to “log into” it from the remote machine.  To “log into” it, you need to create a “network user” in the Ubuntu machine.  It is ridiculous, but the only way I found how to do that is by using The Terminal.  Yes, I am a bit sarcastic about The Terminal, as if it was something evil from of a science-fiction story.

To create the first network user:

In the Ubuntu machine

Applications

Accessories

Terminal

Now type

sudo smbpasswd –a xxxxx     and press Enter


where "xxxxx" is the username of the user you want to create.  There is a space between “smbpasswd” and the “-“.  The recipe I got called for the same name as the initial username you login into Ubuntu with, so that is what I used.  I didn’t try a different name, but it will probably work, too.

I am not sure what this command do to SMB.  At a glance it looks like it is creating the user, xxxxx, and giving it a password, as it will ask for one (keep reading).  However, you'll have to create a user somewhere else as well, so...  keep reading.

After you press Enter you will be asked for your password first to get permission to do this.  This first password is your initial user login password.

Then you will be asked to enter some password for the new network user you are attempting to create.  The user password can be anything you want.  You will be asked to confirm the user password by entering it a second time.

NOTE: If you need to modify this network user's password later, you use exactly the same command.  You will be prompted for your password first (to check your permissions) then for the (new) password and the confirmation.

NOTE: If you want to get rid of a user altogether, the command is

sudo smbpasswd -x xxxxx	(to prevent xxxxx from logging in)

and xxxxx will no longer be able to log in from an outside computer.

Note that the "-x" is a real "x", a "swithc" that make the command smbpasswd do what it has to do.  The "-a" is also a switch, to create the password.

Now you need to create a file, in the same folder where Samba (SMB) is.  I am sure this could be created without The Terminal, using the Text Editor, but here is the recipe I found.  It worked, so I use it.

In The Terminal, type

sudo gedit /etc/samba/smbusers
with a “space” between “gedit” and the first “/”

This command will open the Text Editor, allowing you to create a file called "smbusers" in the folder /etc/samba.

In the Text Editor you type

xxxxx=”network username” 	(see text immediately below)

with quotes and everything, and where xxxxx is the same user name you used up there when you gave it a password, but the typing past the “ = “ is, literally, “network username”, not “network xxxxx”.  You, actually, type the word 'username', and you type the quotation marks as well. 

This will be the only line this file has, for now, if this is the first user you are creating.

In the Text Editor, go File, Save

Now you have a network user called xxxxx.

Wait a while for the rest of the machines in the network to see the Ubuntu machine.  Give it, say, 2 minutes.

Now go back to one of the Windows XP machines.  Again, with Windows Explorer, open My Network Places (just under My Computer)

My Network Places>\

Entire Network

Microsoft Windows Network

MShome

You will see the name of the Ubuntu machine.

Double click on it and you will be asked for a username and a password.

Enter xxxxx and the password you gave to it.  You’re in!




Now, for the Ubuntu system to see a printer in a Windows XP machine in the home network.

Go System

Administration

Printing

The Printers window opens.

In my case this laptop doesn't have a printer installed, so the only icon there will be New Printer.

Double-click on the New Printer icon, and what looks like a wizard will take you though the process or adding a printer to your Ubuntu system.  It is quite simple, really.  My printer was listed, it didn't ask me for a driver, or anything else.

Step 1 of 3

Printer type, put a dot in “Network Printer”
In the large button, make it “Windows Printer (SMB)”
Authentication required
Username: this is YOUR username, as you log in into Ubuntu, not as a network user.
Password: this is YOUR password as you log in into Ubuntu, not the network user's password.
Host: This is the name of the computer with the printer connect to it.
The Username and Passwords are there again, but they are already in, so I didn't have to enter them again.

Step 2 of 3

Manufacturer: You have to scroll/look for the manufacturer of your printer

Model: The model of my printer was listed, so I just clicked on it.

Step 3 of 3

Name: Name of the printer, in my case I called it the same as the Model.
Description:  I described it as “Printer”
Location: I entered the the name of my other computer where the printer is.

Once that was done, the networked printer became available to Ubuntu.  If you go

System

Administration

Printing

the printer will be there.

To print, just open any document with any application and go File, Print.  Walk to your printer and the document will be coming out.  Amazing, really.

---

### Post by Tux Aubrey on 2006-10-15
Well done fern!  I too had initial problems configuring shared files and went through a similar learning experience. Its great that you documeneted your solution as I had so many false tries that I lost track of what actually worked.

I'm with you on the lack of a good gui to do all this.  It just seems weird to me that the "Share Folder" gui only gets you half way and then you have to open and edit a config file with (apparently) undocumented commands.  

Nevertheless, I too love Ubuntu and won't dis the distro for being a little raw in this respect. It is difficult to wholeheartedly recommended it to others who don't already have the love and that saddens me a little.

---

### Post by Stephen_A on 2006-10-15
Also it states that a 'prerequisite' is a 'static IP address.' So what do you do if you don't have a static IP address, which most of us don't?

---

### Post by NeoGreen on 2006-10-16
I tried then realized that this how to was for static IP address.  Does anyone know if there is one for DHCP?

---

### Post by adje on 2006-10-16
Thank you so much for such a detailed note. After weeks of trying to work this out I was just about to give up on Ubuntu until you saved the day.

Thanks for the effot of typing it up for us all.

---

### Post by idaiki on 2006-10-16
I don't see the "prerequisite" for static IP's in Fern's instructions.:confused: 

Most routers handle DHCP and all you should need to share the files/printers is 2 systems on the same router (both using DHCP) and set them both for the same workgroup.

M

---

### Post by NeoGreen on 2006-10-16
Sorry, I wasn't talking about ferns tutorial (which I should have used in the first place).  I was referring to the tutorial at the beginning of the thread.  I tried Ferns tutorial and it worked great.  Thanks.:)

---

### Post by fern on 2006-10-16
Hi,Idaiki M

Perhaps you could outline a procedure on how to "set them both up for the same workgroup".

This in case I ever buy a DHCP router.

I don't know anything about this stuff.  I don't know what DHCP is (I guess I could look it up), and I didn't know I had static IP.  I went to the store and bought the simplest router they had.  It turned out to be a DLink box, with one connector with a cable to the high-speed modem, and four connectors with cables to the four machines I have in the house. DHCP?  Static IP?  Not a clue.  Not sure I want to get that deep into it, but I certainly should not have to.

As I looked around the Net for a way of making my Ubuntu machine part of my home network, I found that zillions of people had exactly the same problem.  (I guess they have static IP, too.)  When I managed to make it work, and I made notes as I went along, I thought that sharing the information was the least I could do. Even if it helps only one other person, I'll be glad.

Fern

---

### Post by Arevos on 2006-10-16
DHCP should not make any difference whatsoever to whether you can share your drive using Samba.

Also, whilst your guide is useful fern, your adversion to the terminal may have made your job much more difficult than it needed to be. The Ubuntu Guide details these instructions for setting up a Samba shared directory, and they seem a little shorter than your guide :) : [http://ubuntuguide.org/wiki/Dapper#How_to_share_public_folders_with_read_only_permission_.28Authentication.3DNo.29](http://ubuntuguide.org/wiki/Dapper#How_to_share_public_folders_with_read_only_permission_.28Authentication.3DNo.29)

However, I completely and utterly agree with you that there should be a GUI for this sort of thing. I was rather shocked to discover that there wasn't one. Perhaps something for Edgy, or Edgy+1.

---

### Post by idaiki on 2006-10-16
> **fern said:**
> Hi,Idaiki M

Perhaps you could outline a procedure on how to "set them both up for the same workgroup".

This in case I ever buy a DHCP router.

I don't know anything about this stuff.  I don't know what DHCP is (I guess I could look it up), and I didn't know I had static IP.  I went to the store and bought the simplest router they had.  It turned out to be a DLink box, with one connector with a cable to the high-speed modem, and four connectors with cables to the four machines I have in the house. DHCP?  Static IP?  Not a clue.  Not sure I want to get that deep into it, but I certainly should not have to.

As I looked around the Net for a way of making my Ubuntu machine part of my home network, I found that zillions of people had exactly the same problem.  (I guess they have static IP, too.)  When I managed to make it work, and I made notes as I went along, I thought that sharing the information was the least I could do. Even if it helps only one other person, I'll be glad.

Fern

All routers by there nature are DHCP.
If you just plug your computers into it and nothing more, by default, you are using the routers DHCP.
The only way to not use the routers DHCP is to set your network connection up as a "static" address.
Also if you use anything other then a router (switch or a hub mostly) there will be no DHCP and you will have to set static IP's. Routers where built for those that had little to no network knolage / experance in order to be a "plug and play" networking device.

*In case that wasn't confusing enough, you can also make Windows XP (and most other newer OS's) provide DHCP but you have to enable it.*

>Now some simple explanations (I hope):
DHCP is a type of server (we'll say for simplistic sake) that monitors what computers (on the network) are on. As computers are turned on they are assigned a number (in order) by the server.
IE. The first computer you turn on would be 01, the second 02, and so on and so forth.
Now in front of those given numbers give by the server are contextual notes. 192.168.x.x is one of the home network notes, as 64.102.x.x is an Internet note, 10.1.x.x is a business note.
These notes help the Internet function but have little to no impact to the normal user.

So DHCP is a server ^ static mean there is no server and thus you have to provide the 01, 02, and so on manually.
Thus you go into network properties and tell it you will provide the IP #. At this point you would type in the note (we will say home) "192.168.0." and the # you want to give the computer, we'll say 02. So you would have in the IP box 192.168.1.2. 
Doing this is called setting a static IP, as it never changes unless you go and manually change it.
**Caution, if you set up static IP's don't set two computers to use the same IP address.**
You can give 2 computers the same # (physically) but neither will work on the network, due to a collision, if they are both turned on. If you turn off one, the other one (still on) will "magically" appear. So always make sure the last number of the IP address (or last two or three on larger networks) is always unique.

So why even bother with Static IP's? Well for networks with lots of computers (like over 150) it actual makes the network faster as the computers don't have to keep asking the server where machine x is. For a home user there is little to no benefit.


Now that you have read this far I should tell you that, No you don't need to know this information to make you home network work. But aren't you glad that you now have a small understanding of it?


Your how to/guide was great. I plan on using this information to my advantage.
Although I know a fair amount about networking, I know about as much as a brick about software (read: code).

Thanks
M

*PS sorry if that was long, I didn't actual plan on writing that much. . . Guess Linux is rubbing off on me :)

---

