---
title: "Rhythmbox Remote Android help"
date: 2012-10-20
forum: Any Other OS
---

### Post by mrpr3sid3nt on 2012-10-20
Hi, I'm trying to get the android app Rhythmbox Remote working on my HTC Desire.

Computer:
Linux mint 13 Maya
Rhythmbox 2.96
Connected to the internet through a wireless router

Phone:
HTC Desire
Oxygen ROM 2.3.2
Android 2.3.7

I have done the following:

Installed the Rhythmweb plugin for Rhythmbox and selected it in the plugins menu.
Rebooted machine.
Restarted Rhythmbox and checked plugin is still enabled.
Installed the android app.
Found my IP address.
Typed my IP into the app: 192.XXX.X.X (all numbers)
Typed in the port number: 8000

I get the following error in the app:

'Rhythmbox isn't reachable! Make sure that Rhythmbox is running and the provided port:8000 match'

So I tried running some network tools to see if I had the right port, the output looks like this:

Port           State          Service
22/tcp       open           ssh
80/tcp       open           http
139/tcp     open           netbios-ssn
445/tcp     open           microsoft-ds
3689/tcp   open           rendezvous
8000/tcp   open           http-alt

When I close Rhythmbox and rescan the ports the bottom two disappear from the list.
I tried entering 3689 into the app as the port but that did not work either, I got the same error. I tried entering each of the other ports in turn but still nothing.

If I go to my web browser and type in my IP followed by the port number 8000 (192.XXX.X.X:8000) I can access Rhythmbox. This doesn't work if I type in 3689, so I think I have the correct port.  I don't know what else to try, any help would be welcome.

Is this an app problem or a person in chair problem?!

I'm still new to linux, so if there is a lot to do I'm afraid I will need some relatively simple instructions!

Thanks,
mr p.

---

### Post by Perfect Storm on 2012-10-21
Moved to Other OS/Distro Talk.

---

### Post by davidmohammed on 2012-10-25
Fire-up your android web-browser and issue a 

[http://[your](http://[your) rhythmbox ip address]:8000

If Rhythmweb appears successfully - then it is an application issue on your android.

If it doesnt appear then you have a network issue to be resolved.

---

