---
title: "Get SWAT going"
date: 2007-01-10
forum: Absolute Beginner Talk
---

### Post by happyhacker on 2007-01-10
I type in [http://localhost:901/](http://localhost:901/) in FFox and page is not found. Help on SWAT ([http://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/install.html](http://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/install.html)) says this is what I should do.

How do I get SWAT going to edit my smb.conf file?

Thanks

---

### Post by scrooge_74 on 2007-01-10
I never really liked SWAT, the times i neede to config samba  I did it from the command line after reading the HOWTO.

Did you installed SAMBA and SWAT?

---

### Post by mykalreborn on 2007-01-10
> I type in [http://localhost:901/](http://localhost:901/) in FFox and page is not found. Help on SWAT ([http://www.samba.org/samba/docs/man/...n/install.html](http://www.samba.org/samba/docs/man/...n/install.html)) says this is what I should do.

How do I get SWAT going to edit my smb.conf file?

Thanks

off-topic:
really funny nickname dude!!

---

### Post by scheuri on 2007-01-10
> **cantthinkofanickname said:**
> I type in [http://localhost:901/](http://localhost:901/) in FFox and page is not found. Help on SWAT ([http://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/install.html](http://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/install.html)) says this is what I should do.

Did you install SWAT?
Try on command line (CLI) the command: "aptitude install swat"
Everything necessary will be installed.

Then you need to edit your /etc/inetd.conf (by using the command "sudo vi /etc/inetd.conf"). There the service for SWAT is mentioned but probably still offline (having ### in front of the line).
You need to "uncomment" the line and then restart inetd.conf by typing "sudo /etc/init.d/inetd restart".

After that you should be able to get to SWAT on localhost on that port.
However, you may need to activate the root password, because SWAT needs root to work with it.

Greetings
stefan

---

### Post by happyhacker on 2007-01-10
Do I need to? smb.conf is in place

Nickname only one which is acros forums (no one's thought of it before!

---

### Post by scrooge_74 on 2007-01-10
SWAT is going to need the root access by way of "su", the other thing you can do is confiure smb.conf by hand

---

### Post by The Mekon on 2007-01-10
This [link]("http://www.ubuntuforums.org/showthread.php?t=58434&highlight=samba+swat") helped me to get Swat going. Look for fabioleitao,s post.

He recommends root control  of Swat.

Brian

---

### Post by happyhacker on 2007-01-16
OK I have installed SWAT and this is the inetd.conf file. What do I do next?

#<off># netbios-ssn	stream	tcp	nowait	root	/usr/sbin/tcpd	/usr/sbin/smbd
swat		stream	tcp	nowait.400	root	/usr/sbin/tcpd	/usr/sbin/swat

PS I have looked at my network and I can see this PC from the BT Home hub (acting as DHCP) but the hub ssid is 'BT ...@ and the two linux) PCs here (on the other side of a dg834g) are ssid 'susey'. My XP Pro PC connected to the BT hub is also 'susey'.

should these all be the same and if so  am a little bit wary of changing th BT setup?

Thanks

---

