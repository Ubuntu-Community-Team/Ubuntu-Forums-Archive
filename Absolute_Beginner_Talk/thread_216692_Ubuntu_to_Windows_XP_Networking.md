---
title: "Ubuntu to Windows XP Networking"
date: 2006-07-15
forum: Absolute Beginner Talk
---

### Post by metaltailz on 2006-07-15
Hi once again,

I was wondering if anyone could tell me how to connect my Xubuntu computer to my Windows XP Home SP2 computer.

If anyone has a tutorial or Howto it would be greatly appriciated.

I have a Linksys Network Everywhere NR 041-CA Broadband 4 Router.

---

### Post by molly_001 on 2006-07-16
metal --
As I understand your question, you want to use that router to share a single internet outside connection, between two computers: one which runs WinXpsp2 and the other which runs Ubuntu.

Disconnect your Ubuntu machine from this router.  Then go to the Windows XP machine, and run the CD software that came with the router.  Follow the directions on-screen from Linksys for this.

So now you will have one Xp machine, using an internet connection which goes through a router, and that router is between the PC and the cable modem (or DSL modem).

Now shut off the XP machine.

Hook the Ubuntu machine to the router.

Turn on the XP machine.  Allow Windows to load.
Turn on the Ubuntu machine.

You now have the two computers sharing one internet connection.

If your intended question was to *network* the two machines together, let me know.

---

### Post by metaltailz on 2006-07-16
Well thank you very much, but I was hoping to get the two computers to network together as in I share a file/folder on ubuntu and windows is able to see those files/folders and copy them.

So if anyone knows how to do that it would be much appreciated.

Oh I also have a printer connected to the windows XP computer so if anyone knows how to print through the network to that printer that would be very helpful.

---

### Post by Malac on 2006-07-16
Search for "Samba" on the forum there are many howto's and walkthrough's depending on your system one should fit.

Hope this helps.

---

### Post by crispy_420 on 2006-07-16
This is actually really simple for both tasks. Just make sure you have samba and cups installed first.

File sharing is a matter of enabling it in samba. For that we will mainly use a GUI program. 

System -> Administration -> Shared Folders

Pick which folder you want to share here. Then you'll want to edit a text file. I think you can just skip this and got to the next step.

> sudo gedit /etc/samba/smb.conf

At the end of this file I have my shared folder which looks like this:

> [crispyhomefolder]
path = /home/crispy
available = yes
browseable = yes
public = yes
writable = yes
guest ok = yes
comment = samba share


That is a basic howto from me and I'm no pro. Just do a simple search on these forums or these two souces:

[http://doc.gwos.org/index.php/Main_Page](http://doc.gwos.org/index.php/Main_Page)

[https://wiki.ubuntu.com/](https://wiki.ubuntu.com/)

The printer sharing is just simple. You said it is on your windows computer right? So in windows go the start menu -> control panel -> Printers and other hardware -> view installed printers

Right click the one you want to share and select sharing. Here select "Share this printer" and name it. Then hit OK. If you look around that page you find other advanced options but get it up and running first before you start tweaking it.

Now back to your ubuntu system.

System -> Administration -> Printing

Select add new printer "New Printer". Select the network option and Windows Printer [smb]. At this point you'll be asked for a username and password. I'm not sure if that is your ubuntu one or windows. So just try both.

Select your host, the system with the printer.

Select your printer you setup to share.

The next screen will want to know which driver to use. Search these forums for your printer model to see what people have had luck with or check here:

[http://linuxprinting.org/](http://linuxprinting.org/)

The final step will be the printer's name, description and location. Don't think these are a big deal. 

Now there still may be some issues you need to sort out. That will be security stuff. Make sure your windows firewall will allow all this. But then again if you found the printer on the network it may not be an issue. Also the router may need some settings enabled as well. For these I can't help you.

To test:

System -> Administration -> Printing

Right click on your shared printer and select properties. On the new page you'll have an option to print a test page.

Good Luck

***** Keep in mind I may have missed a detail or two. So if someone else sees a problem, please correct me. *****

---

