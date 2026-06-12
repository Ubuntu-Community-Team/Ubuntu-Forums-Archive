---
title: "[SOLVED] Connecting to Windows XP shared directory from Ubuntu"
date: 2007-07-28
forum: Absolute Beginner Talk
---

### Post by ewarmour on 2007-07-28
I have a shared directory on my windows XP box which is in a simple work group called @HOME. Connecting to this share from windows would be like so:

\\titan\D$\share

On my Ubuntu laptop I go to Places/Network and see a Windows Network Icon. I launch this and get a File browser window with Location: smb///

So I type in smb:///titan/D$/share or smb:///titan/D/share or smb:///titan/share and I get “” is not a valid location. How do I connect to my shared windows directory?

I've searched the forums but haven't found what I'm looking for.

Thanks -E

---

### Post by armandh on 2007-07-28
I created a small fat32 partition and formated it from XP [right button menu]
access from both xp and ubuntu in a dual boot also a file on my NSLU2 Hdd
but xp can be a pita.

---

### Post by ewarmour on 2007-07-28
> **armandh said:**
> I created a small fat32 partition and formated it from XP [right button menu]
access from both xp and ubuntu in a dual boot also a file on my NSLU2 Hdd
but xp can be a pita.

I don't understand what you are saying. How does this help me?

Thanks, E

---

### Post by sloggerkhan on 2007-07-28
I would use the 'connect to server' button from the same menu.

The one thing to keep in mind is that if you are on a domain, using the domain address seems to work better than using the workgroup address (compname.subdomain.domain.net vs. \\workgroup\compname\share ). I don't think this really matters if you aren't in special circumstances, though.

When browsing through the GUI, you often don't have passwords needed assosciated with your profile.

---

### Post by ewarmour on 2007-07-28
> **sloggerkhan said:**
> I would use the 'connect to server' button from the same menu.

The one thing to keep in mind is that if you are on a domain, using the domain address seems to work better than using the workgroup address (compname.subdomain.domain.net vs. \\workgroup\compname\share ). I don't think this really matters if you aren't in special circumstances, though.

When browsing through the GUI, you often don't have passwords needed assosciated with your profile.

OK, thank you. 

Using Connect to server

Server: Titan

Duh. Thank you very much for your help, that was easy.

Solution:
Set up your windows shared directoy(ies)
Go to places/connect to server
enter server name (in my case Titan)
and you get a list of shares.

So easy a caveman could do it. :lolflag:

Thanks slogger!

---

### Post by sloggerkhan on 2007-07-28
No problem. It took me a while to figure out how easy it was, actually.

---

### Post by ewarmour on 2007-07-28
I take it this is samba correct? 

Any way to speed up this type of networking?

---

### Post by sloggerkhan on 2007-07-30
Not sure what you mean.

---

### Post by wookaru on 2007-08-09
I too have a windows share on another computer that I'm trying to access from my Ubuntu desktop.  From any other XP computer on our home network I access the share by typing "\\wooktop" into an explorer address bar.  Then I am prompted for my user name (guest) and password (***) then I can all my shared folders.  Heres what I have tried from Ubuntu:

Places->Connect to Server...

Server Type: Windows share
Server: wooktop
Share:  (blank)
Folder:  (blank)
User Name: guest
Domain Name: (blank)
Name to use for Connection: (blank)

Click Connect

Then what happens is a folder appears in Nautilus thats named wooktop with a SMB folder icon.  But when I try to open that folder I get an error: 
"Nautilus cannot display "smb://wooktop/" Please select another viewer and try again"

What am I doing wrong?  The crazy thing is I can access my samba share on the desktop from the laptop, but its like the desktop cant see the laptop.  

(PS i have a workgroup setup named 'WORKGROUP')

---

