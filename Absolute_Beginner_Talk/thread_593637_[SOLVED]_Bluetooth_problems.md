---
title: "[SOLVED] Bluetooth problems"
date: 2007-10-27
forum: Absolute Beginner Talk
---

### Post by Inxsible on 2007-10-27
In Feisty, I had installed the Bluetooth File Sharing app from the Add/Remove and everything worked great. I could send and receive files.

In Gutsy, however, the default install came with an app called 'Bluetooth Analyzer'.  So I think I don't need any other apps to get my bluetooth phone working with my computer.

I have successfully got my phone paired with my machine, but when I search from my phone to send a file to my computer, it never finds my computer.

On the flip side, when I right click the Bluetooth Analyzer icon in the tray and select 'Browse Device' and then select my phone, I get this error message
     ```

     "obex://[00:16:b3:46:d4:71]" is not a valid location.
Please check the spelling and try again.
```Can someone please tell me what may be missing?

Or do I have to install additional packages ?

---

### Post by MrHippocampus on 2007-10-27
Installing "gnome-vfs-obexftp" from synaptic should make it work.

---

### Post by Inxsible on 2007-10-27
> **MrHippocampus said:**
> Installing "gnome-vfs-obexftp" from synaptic should make it work.

I did connect once after I installed the package. but since then I get a different error message
```
Couldn't display "obex://[00:16:b3:46:d4:71]".
Check if the service is available.
```I do have my phone's bluetooth enabled and in search/find mode

---

### Post by Inxsible on 2007-10-27
bump.

---

### Post by taecha on 2007-10-28
I had the same problem but everything seems to work fine after installing [_[COLOR="Navy"]Bluetooth Manager[/COLOR]_]("http://blueman.tuxfamily.org").

Hope it works for you, too.

---

### Post by TheIdeaMan on 2007-10-30
The gnome-bluetooth package in universe did the trick for me. After installing, run, "Applications | Accessories | Bluetooth File Sharing" (assuming that's what you want to do). A try icon will appear. Then use your device to send files to your other bluetooth device.

The actual app is called gnome-obex-server (for the curious).

---

### Post by Joakim Stokland on 2007-10-30
Hi! I had the exact same problem as you, and TheIdeaMan's solution worked for me (thanks!).

Good luck!
Joakim

---

### Post by pat_can_vault on 2008-02-25
Thanks a lot. That solution, sort of worked. I can now send items to my PC :). but I still can't browse the device, getting the same error message :

Couldn't display "obex://[00:05:c9:dd:f1:15]".

check to see if the service is available

---

### Post by AmericanYellow on 2008-02-25
Thanks for the help guys. My PC can now connect to my phone.

---

