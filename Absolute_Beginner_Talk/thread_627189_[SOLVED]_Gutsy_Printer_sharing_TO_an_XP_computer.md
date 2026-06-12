---
title: "[SOLVED] Gutsy Printer sharing TO an XP computer"
date: 2007-11-29
forum: Absolute Beginner Talk
---

### Post by willz06jw on 2007-11-29
Ugggh!  

Is there anyway to share my printer to an XP computer _without_:
Either Making my Ubuntu box's  (with the printer on it) IP Address static
or Editing SAMBAs smb.conf file by hand - setting up users and guessing at settings

Thanks!  My wife is trying to force me off of Ubuntu if I can't share the damn printer!

Will

---

### Post by vikram on 2007-11-30
you can configure samba using a GUI. when i looked at the screen shots it does have options to configure printers.

[http://ksambakdeplugin.sourceforge.net/](http://ksambakdeplugin.sourceforge.net/)

---

### Post by stchman on 2007-12-02
> **willz06jw said:**
> Ugggh!  

Is there anyway to share my printer to an XP computer _without_:
Either Making my Ubuntu box's  (with the printer on it) IP Address static
or Editing SAMBAs smb.conf file by hand - setting up users and guessing at settings

Thanks!  My wife is trying to force me off of Ubuntu if I can't share the damn printer!

Will

It is actually very easy.  I cannot say a whole lot for Gutsy, but Feisty is very easy.  Samba is not needed, but you will need to give your PC a static IP address.

To do it in Feisty simply follow this:

System--->Administration--->Printing

Then select Global Settings--->Share Printers

This will open up port 631.

Go to your Windows (or Linux machine) and select network printer and type the following:

```
http://<PC IP address>:631/printers/<printer exact name in Ubuntu>
```

easy as pie.  You will have to have the correct drivers to have the printer work in Windows.

Now you will have to leave your Ubuntu machine on all the time and logged in.  If you wish you can get a USB/parallel print server and hook it up to your router.

---

### Post by willz06jw on 2007-12-02
> **vikram said:**
> you can configure samba using a GUI. when i looked at the screen shots it does have options to configure printers.

[http://ksambakdeplugin.sourceforge.net/](http://ksambakdeplugin.sourceforge.net/)

When I tried to install the SAMBA GUI .deb file from that website it required a dependency that couldn't be found from the repos (Actually it could be found but when I installed it the deb file still said it couldn't find the dependency).

I am about to try stchman's article after I figure out how to assign my computer a static IP (ugggh!).

Thanks for both of your help,
Will

---

### Post by jimrz on 2007-12-02
Does your router offer "address reservation" or words to that effect in it's configuration utility? If so, use that to "reserve" a specific IP for your ubuntu box. This gives you "static" IP functionality without the hassel of trying to configure it. My netgear router has this feature (as do most relatively recent routers) that recogizes each comp by name/mac address and assigns the specified IP each time that machine connects. I have been using this method for all of my computers since breezy and it works splendidly for printer sharing or ssh or whatever.

---

### Post by willz06jw on 2007-12-02
I don't think my Linksys has that option (or it's called something else).  I set a static address and used the "Connect from a Printer on the Internet" and then followed stchman's advice.

Thanks everyone

---

### Post by stchman on 2007-12-03
I have a Linksys router and yes it does not give you an option to set a static IP address.  The way around that it to set a static IP in Ubuntu that is outside the range of the router's DHCP.  Say your router has a DHCP range of 192.168.1.100 to 192.168.1.149 set a static IP to say like 192.168.1.180.

---

