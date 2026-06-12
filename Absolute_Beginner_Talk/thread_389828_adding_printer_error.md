---
title: "adding printer error"
date: 2007-03-21
forum: Absolute Beginner Talk
---

### Post by robtrev on 2007-03-21
Hi,

My PC is connected to a network dell printer.  I have installed the correct drivers for the printer (other people use ubuntu, the drivers and the printer are fine) but I cannot seem to add the printer.

After going through the printer manager, I click the final apply / add and it returns to the manager but no printer gets added (added in the same way as other people on my network).

Running gnome-cups-manager from the console shows this output: 

```
** (gnome-cups-add:22486): WARNING **: Two ppds have driver == 'cdj550'
        ->foomatic:HP-DeskJet_932C-cdj550.ppd (HP DeskJet 932C Foomatic/cdj550[0]) and
        ->foomatic:HP-DeskJet_932C-cdj550.ppd (HP DeskJet 932C Foomatic/cdj550)[0]
Selected ppd file = foomatic:Dell-Laser_Printer_3100cn-Postscript.ppd

** (gnome-cups-add:22486): WARNING **: IPP request failed with status 1280

```

The first bit about the Two ppds comes up when I open the add printer, the selected ppd come up after choosing my driver  and the final IPP request failed 1280 comes up when I tried to add/apply the printer.

I cant figure out whats going wrong and I dont like the look of the first message.  Can anyone point me in the reight direction to fix this?  I am running the most up to date verwion of Ubuntu 6.10 Edgy Eft.

Is there a way to add the printer manually?  Other people using the network have got it working with no troubles and I used the same settings.  Are there any congifs I could copy over from someone elses machine to install the printer?

Thanks for any help, cheers.

---

### Post by steve.horsley on 2007-03-21
Try clicking OK (or is it Continue?) without clicking the Add Driver button. If the printer make is listed, a driver is already installed.

---

### Post by robtrev on 2007-03-22
Yeah, the printer / driver is already installed and when adding a new printer on Step 2 of 3 I have to select it from the driver list, it is present and everything seems to work fine until I Apply on step 3 out of 3, where i get that error in console and no printer added to the list :confused:

---

### Post by steve.horsley on 2007-03-23
Ok, I misunderstood your post, sorry. I'm out of ideas then. Hopefully this reply will bump your post and find someone who has more ideas that I.

---

### Post by 11hjpphty76lkjj on 2007-03-23
Can you try using hplip?

[http://hplip.sf.net](http://hplip.sf.net)

The Deskjet 932c is supported...

---

### Post by loucomballa on 2007-05-02
Hi all,
I've got the same problem with our Dell 5100 color network printer. The cups-add dialog 'checking database' freezes and when (somehow) sometimes the printer configuration dialog appears, it finally does not add the printer. Although it does not complain. On the console I've got the same errors:
gnome-cups-add:22486): WARNING **: IPP request failed with status 1280...
Finally I decided to copy the printer entry at /etc/cups/printer.conf from a colleague who had the printer installed in his previous Ubuntu version (I've got a Feisty). After restarting cups, everything is OK (as fas a as printing programs are concerned) but the cups-manager does no longer work (freezes).
Any suggestion?
Cheers,

lou

---

