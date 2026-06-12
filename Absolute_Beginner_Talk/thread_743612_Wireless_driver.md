---
title: "Wireless driver?"
date: 2008-04-02
forum: Absolute Beginner Talk
---

### Post by blasteryui on 2008-04-02
OKay so I have this [http://trendnet.com/langen/downloads/list_subcategory.asp?SUBTYPE_ID=1155](http://trendnet.com/langen/downloads/list_subcategory.asp?SUBTYPE_ID=1155)
it's for my desktop computer it allows me to connect to wireless networks. On Windows XP it automatically finds the driver and installs it, but it's obviously not going to on Linux so how do I get this working?

---

### Post by Tatty on 2008-04-02
Are you saying that youre wireless is not working in ubuntu?  If you have not tried it yet then do so first, most of the time it should work out of the box.

If not then check the restricted drivers manager in System->Administration->Restricted Drivers Manager, to see if there are any restricted drivers you can enable.

If that fails then try this link... [https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide?highlight=%28wifi%29%7C%28troubleshoot%29]("https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide?highlight=%28wifi%29%7C%28troubleshoot%29")

---

### Post by wolfen69 on 2008-04-02
[http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/](http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/)

---

### Post by blasteryui on 2008-04-02
> **Tatty said:**
> Are you saying that youre wireless is not working in ubuntu?  If you have not tried it yet then do so first, most of the time it should work out of the box.

If not then check the restricted drivers manager in System->Administration->Restricted Drivers Manager, to see if there are any restricted drivers you can enable.

If that fails then try this link... [https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide?highlight=%28wifi%29%7C%28troubleshoot%29]("https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide?highlight=%28wifi%29%7C%28troubleshoot%29")

I have a TRENDnet Wireless USB, and it's not in the restricted drivers manager, what do I do?

---

### Post by Tatty on 2008-04-02
ok first can you post the output of ```
lsusb
``` so we can see if ubuntu can see your device

---

### Post by blasteryui on 2008-04-02
> **Tatty said:**
> ok first can you post the output of ```
lsusb
``` so we can see if ubuntu can see your device

```
dexter@dexter-desktop:~$ lsusb
+Bus 004 Device 004: ID 0bda:8189 Realtek Semiconductor Corp. 
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 002: ID 046d:092e Logitech, Inc. 
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  

```

---

### Post by Mogurijin on 2008-04-02
> +Bus 004 Device 004: ID 0bda:8189 Realtek Semiconductor Corp.

That is your adapter. I think you might have to use the ndiswrapper.

Try this:
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper")

And so you don't have to search as much later for step 3.3, go here:
[http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list_o-z/]("http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list_o-z/")

And search for (ctrl+f) "Trendnet TEW-424UB"

---

### Post by blasteryui on 2008-04-02
> **Mogurijin said:**
> That is your adapter. I think you might have to use the ndiswrapper.

Try this:
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper")

And so you don't have to search as much later for step 3.3, go here:
[http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list_o-z/]("http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list_o-z/")

And search for (ctrl+f) "Trendnet TEW-424UB"

I'm really confused on what to do, I have no idea why it's so hard to do this, I have Wine can't I just install the windows version. Well I tried that though and it wouldn't exute the file for some error reason.

---

### Post by ugm6hr on 2008-04-02
> **blasteryui said:**
> I'm really confused on what to do, I have no idea why it's so hard to do this, I have Wine can't I just install the windows version. Well I tried that though and it wouldn't exute the file for some error reason.

You can't use Wine.

Do you have access to the internet from Ubuntu via any other route than wifi?

---

