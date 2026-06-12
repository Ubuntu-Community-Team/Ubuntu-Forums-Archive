---
title: "Firestarter Question"
date: 2006-07-03
forum: Absolute Beginner Talk
---

### Post by Apple 101 on 2006-07-03
Is Firestarter activated even when the icon is not in the system tray panel?  Or does it need to be opened?

---

### Post by woedend on 2006-07-03
no, the icon need not be there...this is a bad windows thinking.  The icon/gui is just to configure.  test for yourself by rebooting, then running from terminal
sudo /etc/init.d/firestarter status
just to make sure.

---

### Post by HereInOz on 2006-07-03
Firestarter is only a front end, a GUI if you like, for the IPTables firewall which is inbuilt in to most, if not all, Linux distributions.  Ubuntu, to my knowledge, activates the IPTables firewall as a default.   

You use Firestarter to modify the settings of IPTables, instead of using the command line editing of the IPTables configuration file.

So while the Firestarter program does not actually start when you boot up, the Firestarter service starts, setting up the configuration of IPTables, so yes, there is a firewall active from boot up, which you can then monitor and modify with Firestarter.

Hope this helps.

Alan

---

### Post by Apple 101 on 2006-07-03
Great.  Just checked.  It has been started.

---

### Post by Apple 101 on 2006-07-04
All of a sudden, after installing the network-manager-gnome package, Firestarter does not automatically start on bootup when I check with the  *sudo /etc/init.d/firestarter status* command.  Yet when I open Firestarter, the firewall is active.  Which one should I believe?

---

### Post by HereInOz on 2006-07-04
I can't help you with why this has happened, but there is a way that you can test the firewall.

If your Ubuntu box is connected directly to the Internet, and not through a NAT router, then disregard point 1. in this list.

1.  Get in to your NAT router, whatever it may be (may be part of your modem) and set up a port forward of Port 143 to your Ubuntu box.  I am assuming that you can do this, if not, you will need to check the documentation of your router to achieve this.

2. Go to Steve Gibson's site [http://www.grc.com](http://www.grc.com) and when you get past the intro spash screen, scroll down until you see Shields Up! and click on it.

3. Follow the trail through a couple of pages until you get the option to check your security and do a check of "Common ports"

If your firewall is active and properly configured, you should get a full stealth rating, whereas if your machine responds to a ping, or worse still any port is listed as anything but "stealth", then your firewall is not functioning, or is not properly configured.

This is a bit of a run around, but you sound like you want to find out, so this will allow you to test your security. 

It is also good for testing port forwards that you set up.  You can test the port and see if the firewall on the machine you have forwarded to gets hit.  If it does, the port forward is working properly.

Cheers, 

Alan

---

### Post by Apple 101 on 2006-07-04
I'll try it later.  Thanks.

---

### Post by RRS on 2006-07-04
[Here's]("http://www.grc.com/x/ne.dll?rh1dkyd2") a shortcut to the Shield's Up! port testing page.

---

### Post by woedend on 2006-07-04
@Apple - most likely because you have it set to "Activate the firewall" upon gui startup.  (its an option in firestarter).
if status says off, its off.

---

### Post by Apple 101 on 2006-07-05
[QUOTE=woedend]@Apple - most likely because you have it set to "Activate the firewall" upon gui startup.  (its an option in firestarter).
if status says off, its off.[/QUOTE]Okay.  I'll look for an option like that, woedend.

---

### Post by woedend on 2006-07-05
The exact preference is a checkbox, something to the extent of
Start/Restart Firewall on program startup

---

