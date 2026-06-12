---
title: "Printer troubles!"
date: 2006-10-02
forum: Absolute Beginner Talk
---

### Post by unsplosion on 2006-10-02
I am trying to get ubuntu to recognize a printer on my home network. THe printer is on a windows machine. The printer is a samsung ml-2010. The trouble is when I try to connect it it doesnt appear on the list! Any help is appreciated.

---

### Post by klytu on 2006-10-02
> **unsplosion said:**
> I am trying to get ubuntu to recognize a printer on my home network. THe printer is on a windows machine. The printer is a samsung ml-2010. The trouble is when I try to connect it it doesnt appear on the list! Any help is appreciated.

Have you enabled printer sharing on the Windows machine? If so, you should be able to add the printer (assuming Gnome desktop) with 

```
gnome-cups-add
```

which opens a GUI interface to add a printer. Click in the circle next to "Network Printer" and then use the arrows in the box to the right of "Network Printer" to select "Windows Printer (SMB)". Select the appropriate name of the Windows computer where the printer is connected in the "Host" field (if you enabled printer sharing and networking on the Windows computer, you would have been advised to select a name for both the network and the computer) and enter your username and password (for the Windows computer) when prompted. The printer connected to your Windows machine should now appear as a choice when you click the arrow to the right of the "Printer" field. You can then click "Forward" to proceed with selecting the appropriate driver (I think the driver is ML-200 for your printer, but you can check that when you choose the driver) and test your printer. 

Hope this helps.

---

### Post by unsplosion on 2006-10-02
Thanks, Im about to try that now :KS

---

### Post by unsplosion on 2006-10-02
Hmm... Still trouble! The printer just doesnt appear on the list

---

### Post by klytu on 2006-10-04
> **unsplosion said:**
> Hmm... Still trouble! The printer just doesnt appear on the list

OK. Which list do you mean? Does anything appear there or is it just blank?

---

