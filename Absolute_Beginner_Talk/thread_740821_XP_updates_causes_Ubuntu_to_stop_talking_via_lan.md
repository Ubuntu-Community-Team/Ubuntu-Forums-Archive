---
title: "XP updates causes Ubuntu to stop talking via lan"
date: 2008-03-31
forum: Absolute Beginner Talk
---

### Post by stinger30au on 2008-03-31
I have had my Ubuntu and XP pcs talking together nicely for months.

This evening i got tired of XP SP2 asking to to updates so i let it go.

After it finished d/l and installing all updates i can no longer talk from Ubuntu to XP pro.

The error i get on my Ubuntu box is "The folder contents could not be displayed" and under that is written "Sorry couldnt display all the contents of Windows network:encoder"

encoder is the name of one of my windows pcs.

any ideas what the updates have changed on the xp box???

thanks

---

### Post by Calash on 2008-03-31
It may have updated the Windows Firewall and is preventing Ubuntu from seeing the share.  Double check the settings there, and try disabling it too see if the problem goes away.

---

### Post by stinger30au on 2008-03-31
i turned the firewall off and still not happening.

i have got 2 xp boxes and my ubuntu box.
this morning i have come in and my 2nd xp box has finished installing the updates and now the xp boxes will not talk to each other

the error says that i dont have permissions to access the network resource. please contact administrator.

im the administrator. its my home lan.

wow. this is frustrating

---

### Post by stinger30au on 2008-04-01
Well, after much hunting on the net i found this and i tried it and everything is working again how it is supposed to

 If you are always getting Access Denied errors when trying to connect to a XP computer,
 and you know you have the correct user names and passwords on the computer,
 the solution may be a simple registry edit.
 
 1. Start Regedit
 2. Go to HKEY_LOCAL_MACHINE / SYSTEM / CurrentControlSet / Control / Lsa
 3. Change the value of a key called "restrictanonymous" to 0 instead of 1
 4. Don't change "restrictanonymoussam" value.
 5. Reboot

---

### Post by stinger30au on 2008-04-05
this handy tip should make Ubuntu win the network election everytime and help connectivity across lan

1) Open a command prompt
 
 2) Edit your samba config as root:
  Code:
 sudo gedit /etc/samba/smb.conf" 
3) At the very top of the file, add the lines (just copy and paste):
 
  Code:
 wins support = yes
local master = yes
preferred master = yes
os level = 99 
4) Save and exit
 
 5) Restart samba by issuing the command:
 
  Code:
 sudo /etc/init.d/samba restart

---

### Post by stinger30au on 2008-04-05
extra tip on sorting network issues

On the Linux box, open a terminal and type the following:
 
 nmblookup machinename
 
Do this for each of the NAMES of the machines on your network. See if it's finding them through the master browser. It should respond with the machine name and a matching IP. If it does it for the Linux box but not the Windows box, the problem is on the Windows box. If it fails for both, the problem is on the Linux box. That will at least tell us where to look.
 
 Check and make sure that the names of all machines (on all OSes) are 8 characters or less, and have no special characters or spaces in them.
 
 From here I really need to look at some log files to track down further issues. There's something screwey on your network. You haven't got the Windows firewall on or something silly like that have you?
 
 If possible, do the following from a command prompt on the Linux box:
 
 1) sudo apt-get install nmap
 
 2) sudo nmap -sS -vv -A <windows-box-ip>
 
That will tell you if the Windows box is listening on the correct TCP and UDP ports for SMB/NMB information, or if there's a network/firewall issue.

---

