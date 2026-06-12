---
title: "a few questions from a newbie"
date: 2007-03-11
forum: Absolute Beginner Talk
---

### Post by OldManCloudy on 2007-03-11
ok so I'm extremely interested in running a linux OS on my system and from what i've read elsewhere, heard from other linux users is Ubuntu is relatively easy for a *nix newbie to get started on.
a question though.
is it terribly difficult to get this machine(once i install ubuntu) networked with a windows machine to share resources ( print, internet etc.) my partner is very set in her ways ( it took me 6 months to convince her to upgrade from Win ME to XP I'm hardly likely to get her to move away from windows at all)

---

### Post by xyz on 2007-03-11
Hi and Welcome!
See this [Illustrated Dual Boot]("http://users.bigpond.net.au/hermanzone/")
For instance, you could have Windows on 1 partition, another FAT 32 for sharing and Ubuntu on a third.
It is also possible now to read/write your Win partition from Ubuntu.
[HOWTO: NTFS with read/write support using the ntfs-3g (easy & safe method)]("http://www.ubuntuforums.org/showthread.php?t=217009")

---

### Post by OldManCloudy on 2007-03-11
oh no, it seems one of two things have happened, either I wasn't clear enough in my original post, or you misread it. 
I'm fine with the dual boot that was one of the first things I looked up before i posted
my question is, my home network (wired) has two PC's this one ( which i want to install ubuntu on in a dual boot config(again I'm pretty sure I'm up to speed on that) and my partners PC which is windows and very likely to remain that way. is it possible and relatively simple to set these two computers up so we can share resources( the internet through mine (in a very ugly set up) and the printer through hers) so that she has internet access and i have printer access.

---

### Post by xyz on 2007-03-11
Sorry OldMan...my mistake.
So I guess this would be more what you need:
[HOWTO: Setup Samba peer-to-peer with Windows]("http://www.ubuntuforums.org/showthread.php?t=202605")

---

### Post by steve.horsley on 2007-03-11
All the sharing you want is possible.

I find accessing windows shares from Linux extremely easy. Personally, I don't mount them so that they appear as a drive, but I open them in the file exprlorer (nautilus) and drag/drop back and forth. Do it like this:

Open a nautilus window (on your home folder will do). Click the button below Back to get a text location URL. Enter into the URL, a line like:
**smb://DOMAIN;USER@1.2.3.4/C$**
Replace DOMAIN and USER with your domain and user names of course, and use the right IP address. The "DOMAIN;" is apparently optional, but I have never succeeded without it. 
If you miss the "/C$" you get a list of all shares on the box.

You can create a desktop launcher to open this - the command in the launcher goes like:
nautilus smb://DOMAIN;USER@1.2.3.4/C$


I have yet to find a howto that tells you the whole story about sharing files on Linux so Windows can see them, but since is's my Linux and my files, I just do the drag/drop from Linux if I know a windows machine wants the files. That said, a quick look at the HOWTO that XYZ posted looks very thorough, and seems to mention lots of things that most HOWTOs forget. In fact, it looks so damn good I'm bookmarking it.

---

### Post by silkstone on 2007-03-11
I'm using Ubuntu Edgy on a home network (Netgear DG834G modem/router) and two other machines running XP - a desktop and a (wireless) laptop. I'm also a noob to all this. :)

In Ubuntu, If I click on Places > Network Servers, and then keep double-clicking on what it shows in the window that appears, I can access shared folders on the Windows machines. (It sometimes takes a while to recognise and display the network at first, but once it has you can navigate around the shared folders very quickly.) 

You can read and write to the folders on the Windows machine, even though they're on an NTFS drive, but you have to allow sharing of those folders from the Win machine first. So far I've not tried to do it the other way around and access the Ubuntu machine from Windows.

I can also use the printer attached to the XP machine - an HP 970Cxi. That involves installing a new printer as a network printer (System > Administration > Printing > New Printer) and also downloading the appropriate Linux driver which you are prompted to do. Unfortunately the range of printers that are fully supported is rather limited - the HP 970C works fine, but some newer models, especially photo printers, are not supported directly.

To use these you'll probably need TurboPrint which supports most makes and models of printers. You have to pay for the full version of TurboPrint, but the cost is reasonable and you can have a free trial.

HTH.

---

### Post by siciliancasanova on 2007-03-11
Yeah I just installed ubuntu a couple days ago and took my tower over to a friends house to... umm.. borrow some files.  Anyway, yeah just clicked **Places > Network Servers** , as you are sure aware of the need to change the workgroup for windows machine.  In my 2 day experience I saw all of the networks files in under 1 minute.  I just made sure in **Shared Folders** that I had the same workgroup name.  Nice thing in my 2 day experience that I've learned is that there is no need to restart your machine when you switch workgroups.  Took me under 1 minute to synch on Linux.  10 minutes to get the Windows machines to sync.

---

### Post by HereInOz on 2007-03-11
I have a Windows XP machine, with 2 printers attached, as well as an Ubuntu machine.  I can see files on the Ubuntu machine through My Network Places on the XP machine, I can print to the printers on the XP machine from the Ubuntu machine, and I can access files on the XP machine from Ubuntu.

Is this what you want to do?  If so, then seeing as we appear to be in a similar time zone and geographical area, I would be happy to give you a bit of assistance, if you need it.

PM me if you want some assistance

Cheers,  Alan

---

### Post by OldManCloudy on 2007-03-11
thanks alan I'll probably take you up on that offer in the next couple of days (when i get the time to actually sit down and do it)

---

