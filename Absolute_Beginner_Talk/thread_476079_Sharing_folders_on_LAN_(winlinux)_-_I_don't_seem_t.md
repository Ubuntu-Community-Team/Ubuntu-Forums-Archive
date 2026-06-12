---
title: "Sharing folders on LAN (win/linux) - I don't seem to get it going"
date: 2007-06-16
forum: Absolute Beginner Talk
---

### Post by vavroom on 2007-06-16
I would appreciate any help available.  If there's a clear step by step tutorial out there, could you point me to it?  I've been sifting through but can't seem to find anything.

I've read through the official docs, and through the community docs, but I must be missing something :(

Here's my situation.  I have a LAN, one machine is Windows XP, one machine is dual booting Windows XP / Feisty, and one machine that is dual booting Windows Vista / Feisty.

When in Ubuntu mode, I can see the shared folders of the Windows machines, no worries.  But when in Windows, I can't see any folders in Ubuntu.  In fact, the Ubuntu machines don't even show in the network (though they are quite obviously connected).

I created a folder, named "shared", and right clicked on it, selected to share, which prompted me to install the sharing applications (I selected both SMB and NSF).  

When I try and share on NSF (which I realise will only allow me to see from Ubuntu to Ubuntu), I'm asked for a hostname, but I'm at a loss as to what name to put there.  When I try and share on SMB, I'm asked for the folder name, and any comments, and have a read-only tick box available.  But even checking that doesn't seem to make it work.

Any assistance would be greatly appreciated.

---

### Post by skymera on 2007-06-16
i cant read linux either in XP.
when i do see it in My Compooter
it asks me to format, big no no

sorry mate, i don know.

---

### Post by srt5 on 2007-06-16
Hey guys - i managed to get file sharing working between XP and Ubuntu after starting a different thread last week. I hope this sheds some light on the situation for you :)

[take a look here :)]("http://ubuntuforums.org/showthread.php?t=469646")

Edit: It was Austin_KW's post which allowed me to access the shared folder on ubuntu from the xp machine

---

### Post by aktiwers on 2007-06-16
Or here
[http://ubuntuforums.org/showthread.php?t=202605&highlight=samba](http://ubuntuforums.org/showthread.php?t=202605&highlight=samba)

Havent done it my self, but heard that it worked for some.

---

### Post by vavroom on 2007-06-16
srt5, thanks for that, not sure I follow what you did to make it work.

aktiwers, thanks for that link, it looks exactly like the kind of tutorial I was looking for but coudn't find!  I'll be spending a few hours trying that out later this afternoon.  

Thanks a bunch

---

### Post by srt5 on 2007-06-16
> **vavroom said:**
> srt5, thanks for that, not sure I follow what you did to make it work.

aktiwers, thanks for that link, it looks exactly like the kind of tutorial I was looking for but coudn't find!  I'll be spending a few hours trying that out later this afternoon.  

Thanks a bunch

Sorry, perhaps the thread wasn't very clear. I was able to see the devices attached to the network but I was having trouble with the authentication between the machines. Setting a samba password enabled me to access the shared files from the XP machine. And configuring the firewall on the XP machine allowed me to access shared files from the ubuntu laptop. Good luck and I hope the guide solves your problem :)

---

### Post by bren on 2007-06-16
there is a great step by step guide on ubuntu forums by "stormbringer" that covers this topic very  well.

search will find it... 
it worked for me...

bren

---

### Post by vavroom on 2007-06-16
> **bren said:**
> there is a great step by step guide on ubuntu forums by "stormbringer" that covers this topic very  well.

Yes, someone provided that link :)  Looks good

> **bren said:**
> search will find it... 

Unfortunately, I can't seem to find *anything* using the search feature, unless I want to go through page after page.  Multiple search words are all interpreted as "or", not "and", and when I do put "and" in the search, that doesn't work any better <shrug>

---

### Post by djchandler on 2007-06-16
Vavroom,

Where is the shared folder in Ubuntu? I've done a lot better with sharing under Samba since I started making the shared folder in the main directory as su. That is the directory you get when you click on "Filesystem." Note  path in example below. Ubuntu restricts making folders in the main directory, so you must be root or super user. Press the key combination "Alt-F2" to bring up a command line window, and type in

gksu "nautilus"

Then I give myself (my main account, not root) ownership and full permissions so I can change permissions again without having to be su or root. If you put it in a user's home directory, it seems to be harder, at least for me, to get to it from Windows, especially if you use duplicate user names on both platforms. Samba can get confused very easily. I've also found that sharing a folder on removable devices in Windows can make it impossible to reach any folders on that Windows box, even if they were previously available. I think Samba has a lot of bugs, but there are workarounds. Here is an example smb.conf file that gives wide open netbios access on the Linux share.

# rename to smb.conf and copy to  the /etc/samba/ directory as root or su
#Start file

[global]
workgroup = YOURGROUP
netbios name = YOURCOMPUTER
server string = YOURSTRING

security = share
local master = yes
os level = 35
wins support = no

# check path for shared folder(s)

[yourthing]
path = /yourfolder
available = yes
browsable = yes
public = yes
writable = yes

#End file

CAUTION: No security, no passwords, no users list, totally unrestricted. Once you know there's no hardware or firewall conflict, then you need to change the security. Any thing that begins with "YOUR" or "your" needs to be changed to fit your setup.

---

