---
title: "Setting up a network printer in Gusty"
date: 2008-01-22
forum: Absolute Beginner Talk
---

### Post by Yes on 2008-01-22
I've got a networked printer that I'm trying to get set up in Ubuntu, but I'm lost.  I read this [https://help.ubuntu.com/community/NetworkPrintingWithUbuntu](https://help.ubuntu.com/community/NetworkPrintingWithUbuntu), but it says to go to Global Settings, and I don't see that.  Can anyone help?

Thank you!

---

### Post by reckless2k2 on 2008-01-22
are you just trying to add a printer to print to or setup a print server for other computers to use? the docs you reference are related to a print server....not printer setup. also, the "global" reference refers to 7.04. i think you're using 7.10...are you? 

are you just trying to add a printer to use in gusty? do you know the vendor...etc..yadda? how is it connected on your network? that depends on how you set it up and or find it on your network.

---

### Post by Yes on 2008-01-22
Yeah, I'm using 7.10.  I thought that article was for both, maybe that's why I'm having trouble >.<.

I know the vendor, and it's connected to the network router via Ethernet.

---

### Post by question_chick on 2008-01-22
So are you wanting to print to a static IP address loaded into the printer?

---

### Post by Yes on 2008-01-22
Yeah, exactly.  What would the connection type be?

---

### Post by question_chick on 2008-01-22
Forgive me if this is wrong (sitting at work on a windows box) but I'm prettly sure it's the Linux printing lls or something, where it says address just enter the IP of the printer, leave the cue blank and it should be good to go.

---

### Post by Yes on 2008-01-22
There's IPP which has a "Find queue" button and a Queue label, but when I put the IP address in the host box the Foward button stays blacked out.

---

### Post by bij33 on 2008-01-24
Make sure you can Ping the IP of the printer. In my case 192.168.0.102, then go to.
System->Administration->Printing
The Select Connection dialog will appear. Select “AppSocket/HP JetDirect” or “LPD/LPR Host or Printer” from the list. Either one should work, I prefer the first one because it is similar to Windows XP setup and will open/use port number 9100.
In the Hostname field, enter the URI of your printer (192.168.0.102), 
In the Printername field, enter the print server name, which in my case is lpt1.
Click the Forward button. Ubuntu will search for drivers. Tell Ubuntu what printer and driver you want to use (in my case, HP Photosmart 3200, recommended driver). Click Forward.
Enter the printer name, description, and location per the instructions in the dialog.
Next, go to the Policies tab and make sure Enabled, Accepting Jobs, and Shared are all checked in the State section.

---

### Post by Yes on 2008-01-25
I can ping the printer, but it still won't print.

---

