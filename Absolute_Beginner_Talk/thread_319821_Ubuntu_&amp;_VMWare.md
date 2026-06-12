---
title: "Ubuntu &amp; VMWare"
date: 2006-12-16
forum: Absolute Beginner Talk
---

### Post by Mac70 on 2006-12-16
My dual-boot failed so Ive installed VMWare Server.My problem I cant get the VM tools to install. I keep getting a message telling me I dont have the right permissions to extract the files.
Ive tried the sudo thing but I cant be doing that right as I get command not found or words to that effect.Can someone help?](*,)

---

### Post by JayTee on 2006-12-16
in whatever folder  you've extracted the vmware tools type the command to install them but prepend it with ./   for example ./install and run it with sudo. Like this example, sudo ./install
, just replace install for whatever command you are supposed to run and see if that works for you.

---

### Post by Mac70 on 2006-12-16
Hi JayTee
             Im a complete novice with command lines but Ive got some info here. The Tools is in this location /home/scotty/Desktop. The command is ./vmware-install.pl 
So how do I write it exactly?
I take it I go to Accessories>Terminal to do this yes?

---

### Post by xyz on 2006-12-16
> Accessories>Terminal to do this yes?
Yes.

---

### Post by Mac70 on 2006-12-16
OK but what is the right command?Do I add the location?

---

### Post by nealeb on 2006-12-16
Check this link out...
[How To Install VMware Server On Ubuntu 6.06 LTS (Dapper Drake) - Page 2 | HowtoForge - Linux Howtos and Tutorials]("http://www.howtoforge.com/ubuntu_vmware_server_p2?")

---

### Post by Mac70 on 2006-12-16
Still hitting a brck wall.:mad: 
Ive changed the root password to the same as my user password but I just cant get going.
Ive tried "sudo mount /dev/cdrom /mnt/cdrom" and get asked for the password but when I hit enter it tells me "command point not found"

I tried "sudo apt-get install build-essential" but it then wants the Ubuntu cd which it then cant find!

And I tried the "sudo ./vmware-install.pl" which also does nothing.

Anyone with an idea or should I just give up?

---

### Post by useResa on 2006-12-16
I think there are clear instructions on how to install the VMWare Tools in [this thread](http://www.ubuntuforums.org/showthread.php?t=305821).

But to make sure:
Do I understand correctly that you have the file *VMwareTools-1.0.1-29996.tar.gz* on your desktop?

If so, and the instruction in the link are not fully clear, please reply back and I'll try to help you from what you describe.

---

### Post by Mac70 on 2006-12-17
Thanks for the offer of help but the VM is causing havoc with my XP(Home) so I think it will be much easier if I finish building my back up PC and make it wholly Ubuntu.
In the words of Arnie "Ill be back"8)

---

### Post by enopepsoo on 2006-12-17
> **Mac70 said:**
> Thanks for the offer of help but the VM is causing havoc with my XP(Home) so I think it will be much easier if I finish building my back up PC and make it wholly Ubuntu.
In the words of Arnie "Ill be back"8)

It took me a few tries to get it going.  I think I had to install xinetd and build essential before it would work.

---

### Post by derjames on 2006-12-17
Hi there, you can also check VWware knowledge base for installing WMware tools on a Linux guest virtual machine looking here:

[http://www.vmware.com/support/ws55/doc/ws_newguest_tools_linux.html](http://www.vmware.com/support/ws55/doc/ws_newguest_tools_linux.html)

Though it says VMware workstation, also applies for the server version...

cheers

---

