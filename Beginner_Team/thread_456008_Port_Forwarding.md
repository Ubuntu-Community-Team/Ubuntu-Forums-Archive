---
title: "Port Forwarding"
date: 2007-05-27
forum: Beginner Team
---

### Post by carloslosgrande on 2007-05-27
Hi everyone, I've been using Ubuntu for a little while now and my learning curve has been steep.
I'm picking up things here and there as I come to a new hurdle, each one getting easier to jump.

However, I've tried to understand port forwarding and firewalling for at least 3 months without any progress. just when I think I've cottoned on to something I find I was on the wrong track.
I've looked at detailed descriptions, I've followed the Portforward.com site step by step without either success in result or in knowledge.
In short I'm still totally in the dark regarding this.
I, personally, need REALLY simple instructions and explanations regarding this.
I've recently setup Feisty for a couple of friends and my wife. The main difficulty they had was getting their printers working.
But I know they wouldn't even look at anything to do with firewalls etc.
Makes _my_ head spin.
Must it be so complex?
Well, that's my 2 cents.
Carlos.

---

### Post by seshomaru samma on 2007-05-27
which port are you trying to forward ,why and shich routerare you using?
I have a TPLINK router (Chinese) and two machines. If I want to fwd port 80 to the my server machine I open my browser ,put 192.168.1.1 as the URL and the router comes up (yours might have a different address) , I then go to the 'virtual servers' section (this might not be the exact wording on your router, this is a translation from Chinese)
choose 80 as the port , 101 as the address (you can find out your IP address by running the command ifconfig) and that's it.
I then open firestarter (the graphical interface of the firewall) , allow port 80 in incoming connections and I'm set.

---

### Post by carloslosgrande on 2007-05-27
Hi Seshomaru Samma. thanks for replying. I was actually posting here to give my opinions for the use of moderators of this forum.
However I certainly won't pass up this chance.
I had Gtk-gnutella installed and usually running but lately it wouldn't download because it was firewalled. To my knowledge it _always_ claimed to be firewalled but only lately stopped downloading.
Anyway I tried to forward port 50293 which it (gnutella) chose. No success.
Couldn't really get firestarter to do what I wanted as I'm unclear what the various screens and messages really mean
PortForward.com listed port 6346 for gnutella, so I tried this. No success.
My router is Netgear and I used this to set the forwarding as per PortForward.com instructions, no success as above.
In fact all the changes I tried made everything much worse as my net access slowed so much that almost any sites would time out before loading up. Uninstalling gnutella fixed this.
So I tried amule, which I can't figure at all, and azureus, which has a port test for its default port 16509. It says OK for this but the main azureus screen says no access!
The main difficulty is that none of this intuitive, in that I can't figure things out just by reading the windows/messages/errors etc. I'm not fluent in this stuff by any measure and it seems so very complex. Other parts of the system have much clearer method descriptions which I'm able to nut out reasonably well, often with help but this IP stuff seems unnecessarily codified! if you get my meaning.
I think I'm ranting now.
I currently trying frostwire.
Thanks.
Carlos.

---

### Post by motin on 2008-10-07
Install "guidedog" from the repositories. It's KDE-based, but allows easy configuration of port forwards. 

Cheers

EDIT: Just realized that Firestarter allows this as well. It's on the Policy tab at the bottom. Even easier to use than guidedog...

---

### Post by poomalairaj on 2008-11-09
Hi,
You should configure your router to allow forwarding port.
Check your router manual to do that. You can also search inter net to configure your router to forward desired port. 
Check [chennaigeekspot.blogspot.com]("http://chennaigeekspot.blogspot.com/2008/11/howto-configure-port-forwarding-on.html") site to configure beetel 220BX router cum modem. Most of the routers have more or less same configuration.

---

### Post by Ascii1979 on 2008-12-16
I was haveing an issue aswell with ports (my router was configured properly) and still wasnt working properly, i came across something telling me that all ports are closed default by Ubuntu and as stated above i found the easiest fix was Firestarter, and goto policies and right click inside appropriete box.   Thanks to previous posters

---

