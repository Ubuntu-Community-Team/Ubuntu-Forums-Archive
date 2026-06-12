---
title: "Anyone know password and username of CUPS?"
date: 2007-01-24
forum: Absolute Beginner Talk
---

### Post by Busta999 on 2007-01-24
OK I'm a linux noob...

Trying to setup printer sharing, so others can print on the printer attached to the Ubuntu box.

I print a test page successfully from /System/Printing/ OK - looks good.

I would like to share the printer so started [http://localhost:631](http://localhost:631) went to Admin page checked the 'Share published printers connected to this system' then selected the change settings option - it hen asks for the CUP username and password.

I had already added my user to the lpadmin group and cupsys to the shadow group.

It won't accept my username and password and just asking me to keep entering it - obviously this gets me nowhere.

So plan B

Already had Samba files sharing working over the LAN with windows PCs accessing the files no problem.

Windows XP can 'see' the printer when browsing but when I try to print a test page nothing happens.

Now I have followed the instruction slavishly, again and again and after 12 hours of trying this I could really do with some advise besides dump Linux.

Anybody got any clues - this is very basic stuff and I cannot work out why it is failing so miserably.

Arrrrrrghh](*,)

---

### Post by mexlinux on 2007-01-24
It should accept your username and password (as you do with sudo).
Have you given root account a password, or mdified something like that?

---

### Post by Busta999 on 2007-01-24
Yes I added a password for Root, I was spending too long constantly sudo

Does CUPs admin not work if you have Root as a user?

Thanks

M

---

### Post by Busta999 on 2007-01-24
I have had to reinstall CUPS it died and wouldn't start after reboot.

I have also disbabled Root by sudo passwd -l root

So will try all over again ( for the 8th time) and try to get this working somehow or start looking for a more stable Linux version.....

---

### Post by Busta999 on 2007-01-24
I have had to reinstall CUPS it died and wouldn't start after reboot.

I have also disbabled Root by sudo passwd -l root

So will try all over again ( for the 8th time) and try to get this working somehow or start looking for a more stable Linux version.....

---

### Post by Busta999 on 2007-01-24
Worked around flakey CUPS and shared it through Samba instead.

Whooooo  got something to work!!!!!!!

---

### Post by rccharles on 2007-01-25
> **Busta999 said:**
> Yes I added a password for Root, I was spending too long constantly sudo



So, you do not want to type sudo before every command... 

You can enter:

sudo bash

You can now enter all the commands you want until you enter:

exit

Robert
:D

---

### Post by haiku99 on 2007-01-25
this fix from bennyj worked for me under Dapper...FWIW no cups pw trouble w/ Edgy

[B]I was having the same problem with the user and password not being accepted in the cups web interface.This is what fixed it for me.

open a terminal
type in "adduser cupsys shadow" (without quotes)press enter.dont forget sudo!
then type in /etc/init.d/cupsys restart

You should see it restarting in the terminal.
now browse to the cups web interface and add your printer.

Hope this helps
Benny[/B]

---

### Post by ramjet_1953 on 2007-01-25
I got around it by doing this:

1. In a console type : sudo passwd root

2. Follow the directions to make a root password.

3. Type su

4. Type: adduser cupsys shadow

5. Re-boot

When you bring-up cupsys, use the username "root" and the password that you nominated for the root account.

ps Obviously this also gives you root access for other things, so be warned.

Regards,
Roger 8-)

---

### Post by Busta999 on 2007-01-25
Thanks guys tried all the above with mixed joy.

My problem here is how inconsistent it is, it makes it very hard to diagnose when it reacts differently each time you try something.

The CUPS admin page states it is sharing the printer, but noting can connect to it. It also states that Remote Admin is enabled but nothing can connect to the IP:631.

I soooo wanted Linux to be ready for primetime so that Vista would get its *** wiped but it ain't never going to be Aunt Mable's OS. Now the MAC has it right, they got linux working with a GUI, Ubuntu at least feels like a CLI with some pretty stuff on top a bit like where Windows was with version 2.

It seems to me, as a noob to linux that it is trying to have too much and needs to focus in on some core features that it can do well and avoid being so flakey. I will stick with it becuase I have so many late nights invested in it, but it is not something I could recommend to someone I liked.

Maybe I just started with the wrong distro, maybe I would have been better off with a mainstream one.

---

### Post by mexlinux on 2007-01-25
> **Busta999 said:**
> Thanks guys tried all the above with mixed joy.
Maybe I just started with the wrong distro, maybe I would have been better off with a mainstream one.

Seems to be that you started with a bad practice: Activate root account, and use it as your default account is they windows way of life.

---

### Post by jonny on 2007-01-25
It's probably a bit late, but the recommended approach on Ubuntu is to use the standard Gnome tools.  This works for me:

On the print server, ensure System --> Administration --> Printing --> Global Settings --> Share Printers is ticked.

On the client PC, ensure System --> Administration --> Printing --> Global Settings --> Detect LAN Printers is ticked.

To find out the address that Windows boxes can use to access the printer, go to System --> Administration --> Printing, right click on the printer, view its properties and look at the URI on the Connection tab.

This is all very Grandma friendly and, to my mind, no harder than setting up print sharing on Windows.

---

### Post by Busta999 on 2007-01-26
OK thanks for the input guys.

Never did get the CUPS web admin to accept a username/password. Even if it was Root, username in lpdadmin and cupsys added to shadow.

On my implementation of Ubuntu Dapper Drake the System/Admin/Printer Global settings only has one option Detect LAN Printers, there is no option to enable Share printers as someone suggested earlier.

I fixed it by wiping and reinstalling the CUPS stuff and editting two files, cupsd.conf in /etc/cups and  the ports.conf in /etc/cups/cusp.d directory.

sudo gedit  /etc/cups/cupsd.conf

and chnaged the following section to:

<Location />
Order Deny,Allow
Deny All
Allow 127.0.0.1
Allow 192.168.0.*
</Location>

and then 

sudo gedit /etc/cups/cups.d/ports.conf

Listen 631
browsing the Network Tree in Explorer - seeing the server 
then goto System/Admin/Printing Global Settings enable 'Detect LAN Printers'

and all came to life!!

The Samba settings I had previously setup to share CUPS printers kicked in and I was able to print from LAN MACs and XP boxes no problem. This was done by the normal windows way of adding a networked printer.

Oh by the way found out why I could never get the SAMBA web admin to work, it needs to have indetd installed. I had assumed that when I installed Samba and Swat it would install all the they needed as dependencies, obviously not the case.

So, as I said, Linux/Ubuntu is a challenge and I still can't see Linux being Aunt Mable's OS of choice, but I could definitely see her using a MAC.

---

### Post by jonny on 2007-01-27
> **Busta999 said:**
> 
On my implementation of Ubuntu Dapper Drake the System/Admin/Printer Global settings only has one option Detect LAN Printers, there is no option to enable Share printers as someone suggested earlier.


You found the right way to do it on Dapper, and it ain't pretty.  The slick option got added in Edgy as it was recognised that editing config files wasn't the best way forward for Aunty Mabel

---

