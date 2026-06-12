---
title: "Small home network"
date: 2007-02-22
forum: Absolute Beginner Talk
---

### Post by madddonkey255 on 2007-02-22
Hello I'm trying to create a small home network to share files and a printer.  I'm also trying to set up a wireless router for the WEP or WPA key so it's secure.  In windows I know there is an option to click that will open up a wizard todo this for you.  i was just wondering if something like that exists in Ubuntu or if not how I would go about doing that.
Thanks,
Nolan

---

### Post by netkid91 on 2007-02-22
For wireless, you'll want to make sure you use WEP encryption, WPA is still troublesome under Linux.  As for setting it up, System->Administration->Networking, find your wireless connection and set it up.
As for printers, using System->Administration->Printers, selecting Add Printer will guide you through the process of setting up network printers.
If you only want to access shares on other PC's, just use Places->Network and browse through the network, to share stuff you can install the necessary stuff using System->Administration->Sharing.....

---

