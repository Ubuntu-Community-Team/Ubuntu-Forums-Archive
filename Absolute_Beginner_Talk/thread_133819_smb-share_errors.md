---
title: "smb-share errors"
date: 2006-02-20
forum: Absolute Beginner Talk
---

### Post by lexa on 2006-02-20
Hello!

I'm having some problems browsing other computers' shares over my LAN. When I go to Places -> Network servers -> Windows network (all the other computers are running various flavors of Windows), I can see the computers there, but when I try to open the shared folder on my desktop (WinXP, NTFS) I get the following error: 

"Cannot open (COMPUTERNAME): The filename "(COMPUTERNAME)" indicates that this file is of type "desktop configuration file". The contents of the file indicate that the file is of type "x-directory/smb-share". If you open this file, the file might present a security risk to your system.

Do not open the file unless you created the file yourself, or received the file from a trusted source. To open the file, rename the file to the correct extension for "x-directory/smb-share", then open the file normally. Alternatively, use the Open With menu to choose a specific application for the file. "

The icon for the computer then turns from a page with a notepad and pencil into an orange folder with "SMB" on it. If I try open with-> file browser, it opens a new window and looks promising for a moment, but then another error appears: "The folder contents could not be displayed: Sorry, couldn't display all the contents of "(COMPUTERNAME)" and the window stays blank. 


The XP desktop does not have Windows firewall enabled. The shared folder is not password-protected. If I try to use the syntax "smb://computers_ip/sharename" to get straight into it, the run dialogue box disappears, but nothing happens - no errors, just... nothing. So, I don't know what to try next.

(Edit: I should mention that the same errors appear with the other computers as well - I did not mean to give the impression that the XP desktop was the only one I could not browse. It's just the one I'm mainly concerned with.)

---

### Post by Robgould on 2006-02-20
Here is a link that should help.
 
[http://www.ubuntuforums.org/showthread.php?t=131561]("http://www.ubuntuforums.org/showthread.php?t=131561")

---

### Post by lexa on 2006-02-20
Thank you for the really quick reply. However, that thread appears to deal with mount syntax - I'm not even to the mounting step yet; I'm still trying to make sure the connection to the other computers works. Is it necessary to mount shares before you can browse them?

---

### Post by dickohead on 2006-02-20
browse to the IP address of the machine, don't use windows network browser.

ie:

go to: \\192.168.1.x or whatever the address is.

---

### Post by lexa on 2006-02-20
When I try to go->location and enter "\\192.rest.of.address" the following error occurs: "Couldn't find "/\\192.rest.of.address"." Am I supposed to be using different syntax?

---

### Post by Robgould on 2006-02-21
You will be better off if you ditch that gui and use the terminal and the mount statement. It just works much better.   I'm normally all about the gui, but not in this case.

---

