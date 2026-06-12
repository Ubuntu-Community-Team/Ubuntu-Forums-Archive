---
title: "How to print over network"
date: 2006-01-18
forum: Absolute Beginner Talk
---

### Post by utab on 2006-01-18
Hi there,

I am trying to print over a network on an hp laserjet 1320tn or an hp laserjet 4000N. Could you please help on configuring?

Many thanks in advance.

---

### Post by Kimm on 2006-01-18
Hi,

I dont use gnome (XFCE4), so I'm not sure if I get the menu hierarchy right, but it should be something like this:

System -> System -> Printing

Then, select the type of printer, for example, if the printer is connected to a Windows computer, you want to select "Windows Printer"

Then, set the host as the computer with the printer connected to it, the computer name or local IP works fine.

The username and password should be the same as the username and password you use to log into your user.

Now you can pick the printer brand (Hp should be Hevlet Packard), and the printer name, the program will suggest a driver (if the printer is supported). And thats pretty much it.

---

### Post by bscbrit on 2006-01-18
To print to the HP 4000 over an ethernet network, select Network Printer, port 9100 and the IP address that you have given the printer.

---

### Post by utab on 2006-01-18
Hi  again

I can select the computer but no printer comes in the list window below(I have entered my user id and pswd 3 times before this step)

What is wrong?

thx

---

### Post by bscbrit on 2006-01-18
Are you trying to access the HP4000 over ethernet using DirectJet, or are you trying to access the printers which are connected to another computer?  If the latter, have you set up the share using samba?  I'm not quite sure how you have configured your network and printers.

---

### Post by utab on 2006-01-18
Hi

I am trying to connect to a printer that is connected to another computer(Win 2000 I dont know if needed does not sound reasonable) on a network.

So samba set up how?

thx

---

### Post by utab on 2006-01-18
I chose Windows Printer(SMB)

SMB = Samba ?????????

OR????????

thx

---

### Post by bscbrit on 2006-01-18
yes SMB = SAMBA

On the windows machine, have you set the printer up as shared?  I am not a SAMBA expert so I will have to get the books out to find out the details of setting it up.  If you mark a directory (folder) as shared on the windows machine, does that show under your computer name over the network?

---

### Post by bscbrit on 2006-01-18
[https://wiki.ubuntu.com/MountWindowsSharesPermanently](https://wiki.ubuntu.com/MountWindowsSharesPermanently)

This thread should help.

---

### Post by utab on 2006-01-18
I guess so because everyone in the office uses that printer so that must be shared as well.

I can also use it when I am on Win side

thx

---

### Post by bscbrit on 2006-01-18
[https://wiki.ubuntu.com/MountWindowsSharesPermanently](https://wiki.ubuntu.com/MountWindowsSharesPermanently)

This thread should help.

---

