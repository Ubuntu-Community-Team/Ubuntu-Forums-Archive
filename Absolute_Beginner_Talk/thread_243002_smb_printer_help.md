---
title: "smb printer help?"
date: 2006-08-24
forum: Absolute Beginner Talk
---

### Post by jaybmx on 2006-08-24
I have a HP PSC 1410v all in one printer connected to my windows box. It is shared over my network and I can print to it fine from all my windows boxs...
I can add this printer in Ubuntu (dapper) and it seems to have the correct drivers (psc1400).  Everything seems fine... then I try to print or do a test print.
everything seems fine from the Ubuntu boxs but the print fails and gets stuck in the list of print jobs on the windows box.  It seems like it tries to print, but stops. The printer actually makes noise but never prints...  
Then if i try to delete or cancel the print job on the windows box it wont let me...makes the printer unusable until i unplug usb, delete print drivers from windows box, reinstall and start over... very frustrating!
Anyone have any idea what i am missing?  What is happening to my print jobs?
Thanks

---

### Post by Iowan on 2006-08-24
[http://www.ubuntuforums.org/showthread.php?t=26166]("http://www.ubuntuforums.org/showthread.php?t=26166") Does this one help any?

---

### Post by jaybmx on 2006-08-24
thanks for the link...
i tried the guest user with no password like the like you post said and it does the same thing...
the link led me to other post from people with the exact same problem...no one ever finds and answer! 
this seems like it should be very straight forward...
i hate giving up on stuff like this but i dont even know what to try next!:confused:

---

### Post by John.Michael.Kane on 2006-08-24
This may offer some help
[**Sharing A Linux Printer With Windows Machines**]("http://www.faqs.org/docs/Linux-HOWTO/SMB-HOWTO.html#s9") 

Heres others:
[**Windows Printer With Linux Machines**]("http://tldp.org/HOWTO/SMB-HOWTO-10.html")
[**Debian-and-Windows-Shared-Printing**]("http://www.faqs.org/docs/Linux-mini/Debian-and-Windows-Shared-Printing.html")

---

### Post by artinla on 2006-09-14
Enable the guest account on the XP machine.

Right click on My Computer, select "Manage" and "Users and Groups"

Right clich "Guest", select properties and uncheck the "Account is Disabled" checkbox.

Close the Microsoft Management Console and then try again.

---

### Post by bucket on 2007-02-14
If your printer is stalling at 64.0kb/(however big printer job is it) It's because you have a windows printer option enabled that the linux stuff doesn't like talking to.

FIX -- In windowsXP , right click printer, Properties, Advanced, Ports and DESELECT "Enabled bidirectional support"..

it'll stop clicking and whirring and print properly.

---

