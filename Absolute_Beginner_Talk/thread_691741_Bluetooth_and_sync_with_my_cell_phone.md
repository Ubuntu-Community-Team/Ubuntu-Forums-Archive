---
title: "Bluetooth and sync with my cell phone"
date: 2008-02-08
forum: Absolute Beginner Talk
---

### Post by alquimista on 2008-02-08
Hi,

I installed Kubuntu 7.10 in a Toshiba Satellite A60. I'm testing the Bluetooth connection to my Samsung D836 phone, which have a cute Windows software to backup the phone data and eventually have it on synch with MS Outlook. 
Using the Bluetooth tools provided out of the box in Kubuntu, I was able to see my phone and push files into it, but did not to see its contents nor file strucutre. When I clicked on the phone icon, Dolphin opens showing no contents. Bluetooth is activated in the phone, and I have marked photos and Contact info so I can see them somehow in Kubuntu, but that does not happen. 
I need to have some mean in Kubuntu to sync the phone contact info, or at least have it stored/backed up in my PC. I have CrossOver Office and I was thinking on trying to install the cell Software on it, but I don't know if it will detect the Bluetooth adapter I connect through USB. 
Any ideas on how can I manage/sync my cell info (Contacts, Tasks, images) with my Laptop in Kubuntu?

Thank you,
Guillermo

---

### Post by finer recliner on 2008-02-09
try bitpim:
[http://arstechnica.com/journals/linux.ars/2007/12/10/using-a-bluetooth-phone-with-linux](http://arstechnica.com/journals/linux.ars/2007/12/10/using-a-bluetooth-phone-with-linux)

---

### Post by alquimista on 2008-02-11
Using BitPim, and trying to locate the phone, the phone detects the call from the PC and prompts for permission to allow it. I press ok, but then a window appears on BitPim saying "No phone detected/recognized". I enter and try to configure it with no success.

Using MultySinc, when searching for the phone, it founds it but displays "No IrMC synchronization"; and when testing the connection, it fails. MultySinc would be very important for me, since it is the mean by which I'd sync the phone with Evolution.

On the Bluetooth icon that appears in the Kubuntu desktop, when I click it, a Konkeror window appears with my phone icon in it; yet when clicking on it, I get a header "sdp://[00:17:d5:a0:36:9b]/", and no contents appear.

I installed KMobileTools 0.5 After several runs of the Bluetooth connection Wizard, I finally got it detecting the phone, but I can't see any of its contents (SMS nor Contacts).

I really need to sync my phone with my laptop... I'd appreciate very much your help.

Regards,
Guillermo

---

### Post by sanitycheck on 2008-02-12
With the Konqueror solution, you may need to press F5 (refresh) at each window/level as you move through the phone's directories.  It initially shows up blank for me but things appear with an F5.  Konqueror seems to time out before Bluetooth can respond.

I had a Feisty 64-bit install that showed me an icon to allow me to browse for Bluetooth devices under Network Folders, but this Gutsy 32-bit install does not have an icon there.  Maybe the Bluetooth icon by the clock replaced it.

I use Dolphin now so I created a bookmark icon on the left (bluetooth:/) just for Bluetooth browsing.

---

