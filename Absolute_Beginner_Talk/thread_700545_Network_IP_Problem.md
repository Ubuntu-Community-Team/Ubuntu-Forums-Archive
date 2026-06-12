---
title: "Network IP Problem"
date: 2008-02-18
forum: Absolute Beginner Talk
---

### Post by sipso on 2008-02-18
Hi, I created a network with an my XP laptop and an Ubuntu Gutsy Gibbon Laptop. All it well, I have shared folders that I can access from either end and I share a printer that is hooked up to my XP. I liked the setup and the ability to move files on a network without cds or jumpdrives, I also liked not having to unplug my printer and plug it into my ubuntu laptop every time I wanted to print something. So i decided to add my Wife's XP Laptop to this ethernet network, so she can print over the network and share files. She does a lot of photo editing for me and so it is nice to be able to send pictures back and forth over a network. Recently though, I noticed a problem. When my XP laptop is not on or plugged in, my wife's XP can't get an IP (limited connectivity) and therefore is unable to share files with my Ubuntu Latptop, even though they are both plugged in.  First of all i don't understand why this is a problem and second I want to know if there is something that I can change so that my Ubuntu Laptop is supplying the IP Address instead.  Thanks!

---

### Post by OffAxis on 2008-02-18
what does your network look like?

Do you have a router than also functions as a DHCP server (assigns IP addresses to the machines)?

If I'm reading this properly you've got 3 laptops connected, 2 XP 1 Gutsy, and one of the XPs is connected to the printer.

Are all connections wired?

Are you using any ad-hoc wireless connections?

---

### Post by sipso on 2008-02-18
I will answer that the best I can. They are all on a wired ethernet switch.  When i originally set up the first network (XP+Ubuntu) I set the connections on the Ubuntu to DHCP for the wired connection and simply ran the network wizard for the XP machine. When I added my wife's computer (network now is XP+Ubuntu+XP) I just ran the network wizard for hers too. All three computers have the ability to connect to the internet wirelessly and they do, I have turned off the file sharing for the internet connections though the wireless for security.  Both XP machines get disconnected from the wired connection regularly for travel, only the Unbuntu one stays plugged in all the time and that is why I want it to be able to be connected to all of the time.  hope that helps in answering my post

---

### Post by OffAxis on 2008-02-18
Sorry, I'm still confused.
> All three computers have the ability to connect to the internet wirelessly and they do
So you use the wireless to access the internet (through an access point like a router),and then use a wired connection just for file transfer?

Or is the wireless just used while travelling?

---

### Post by Iowan on 2008-02-18
You *should* be able to enable the Ubuntu laptop as a DHCP server (if you don't want to assign static addresses), but you'll need to insure that it's the only machine handing out addresses (I presume your XP laptop must be doing that now).

---

### Post by sipso on 2008-02-18
Sorry, that's my fault I didn't answer that very well. I live in some college apartments and the college provides us with free wireless connection to the internet. So I connect wirelessly through their router in the building.  But I also do connect to other internet sources when I travel wirelessly. 

So At home I connect to a wireless router in the building for internet, but then I have a small wired network set up in my apartment just to transfer files and share the printer among the three laptops.  This network is not connected to the internet.  The computers only connect to the internet wirelessly.

Does that clear it up for you?

Thanks for being patient with me (as you can probably tell I am very new to ubuntu and networking).

---

### Post by sipso on 2008-02-18
> **Iowan said:**
> You *should* be able to enable the Ubuntu laptop as a DHCP server (if you don't want to assign static addresses), but you'll need to insure that it's the only machine handing out addresses (I presume your XP laptop must be doing that now).

How do I insure that it is the only machine handing out IPs and that my XP is not doing it instead?

---

### Post by OffAxis on 2008-02-18
MUCH clearer. Thank you.
Each connection (wired or wireless) can be handled differently; dhcp assigned ip or static ip.
You currently have dhcp on the wireless; no need to mess with that.
You don't even need to have a dhcp server on the wired connection; just assign each computer a static IP on the same subnet.

For example;
Computer #1 IP: 192.168.1.3
netmask 255.255.255.0

Computer #2 IP: 192.168.1.4
netmask 255.255.255.0

Computer #3 IP: 192.168.1.5
netmask 255.255.255.0

Since they're all local addresses I don't think you need to have a default gateway on that connection, either (although I could be wrong on that).

I'm not quite sure what's going on there with the need for your XP machine to be there; you may have done an 'Internet Connection Sharing' through the wizard or some such thing. Neither XP nor Ubuntu have a DHCP server setup out of the box, so it shouldn't be getting assigned one from your XP laptop.
Anyway, give the static IP thing a shot. Just make sure you're putting the static IP on the wired connection and not the wireless.
It should work.

---

### Post by sipso on 2008-02-18
Well it took me a little to figure out how to set the ip on the XP machines through the command prompt, I would have to say it is a lot easier in ubuntu and it seemed to work...until I tried to access the shared folders on either XP machine from the ubuntu machine, the folder fails to show contents. But either XP machine can open the shared folder on the Ubuntu machine and they can open folders on each other, But the ubuntu machine can't open the folders on either XP.  setting the static IP did solve the original problem, the connection is maintain when my laptop is unplugged and my wife can still get to the ubuntu machine.  But any idea why I cannot access either XP machine from the ubuntu machine now?  I am using Samba, you probably guessed that, but i thought I would throw it in there (i don't really know what is important).

---

### Post by OffAxis on 2008-02-18
```
smbclient -W <workgroup name> -L <computer name>
```

should show all available shares on the specified computer.

Sometimes the icons don't seem to show up properly in the network; you can try accessing the folder by putting 
**smb://servername/foldername**

as the location's url in your system browser.

---

### Post by sipso on 2008-02-18
The problem isn't with seeing them in the graphical interface, I have located them both that way and thru the terminal. But after I locate them I cannot gain access to them. When I try I get a message that says "The folder contents could not be displayed.  Sorry, couldn't display all the contents of 'SharedDocs.'" Which is odd, since I have no problem with accessing these folders with the XP Machines.   Any thoughts?

---

### Post by OffAxis on 2008-02-18
what username are you using for the connection?
I think folder viewing is universal, but folder access is limited.

```
smbclient //servername/foldername -U username
```

---

### Post by sipso on 2008-02-18
I don't know how to answer your last post. I tried typing your last code in a terminal, replacing the fields. It then asks for a password and whether I type one or not, it brings up a smb:  \> prompt.  I typed "dir" and then tried "open *a document in the dir*", I am not really sure how to use the command line part of ubuntu yet, so i don't know if that should have done anything or not, but it didn't do anything.  It never mentioned a username or anything...  So like I said, I am not sure how to reply to your last post...  sorry.

---

### Post by OffAxis on 2008-02-18
sorry, I should have elaborated.
the **smb:>** prompt works much like an ftp prompt. If you got that far; you're in.
Basic shell commands like
**ls **and **cd **will work in this enivonment. Type **exit **to leave.
If you can **ls **and have the files show, then the username that you supplied has access to read, where your default username did not.

I gotta go, but hopefully someone else will jump on and help you out.

---

### Post by sipso on 2008-02-18
> **OffAxis said:**
> sorry, I should have elaborated.
the **smb:>** prompt works much like an ftp prompt. If you got that far; you're in.
Basic shell commands like
**ls **and **cd **will work in this enivonment. Type **exit **to leave.
If you can **ls **and have the files show, then the username that you supplied has access to read, where your default username did not.

I gotta go, but hopefully someone else will jump on and help you out.

Well I am able to access my XP through the terminal, At least I am pretty sure, I can bring up the dir of the folders and stuff, so I am pretty sure that I am in (I don't fully understand how to actually open a file/document from the terminal).  But what I don't understand is why I can see the dir and folders in the terminal, but I can't access them thru the places/network when I type in the complete address, there I just get that message of being unable to open the contents of the folder.  Any idea of what can be wrong and why.  Before I made the IP Static on all three machines, I couldn't see either XP machine in places/network but if I typed in smb://*computername*/*folder* it would open the folder with no problem.  So what would changing the IPs to static do to cause me not to be able to access the folders on the XP machines via place/network?

Thanks for your help

---

### Post by sipso on 2008-02-19
Well I have sort of found a solution. I decided to try using SMB4K since someone suggested it to me when i was having problems with my connection a few weeks ago, I never used it because I found out a different way around my previous problem.  But I decided to give it a try since I could access files through the terminal and thought it might work.  It did, so while it doesn't really answer my question, it does provide a workable solution. So i can live with it.  If anyone has an answer why I can't open the file simply by going to places/network, I would be interested in it, but thank OffAxis for all your help.

---

### Post by Iowan on 2008-02-19
> **sipso said:**
>  If anyone has an answer why I can't open the file simply by going to places/network, I would be interested in it, but thank OffAxis for all your help. Try the "Connect to Server" option.  Select "Windows Share", then "Browse Network".  This doesn't *always* work for me - but more often than the "Network" option.

---

