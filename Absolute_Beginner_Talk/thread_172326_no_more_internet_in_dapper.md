---
title: "no more internet in dapper"
date: 2006-05-08
forum: Absolute Beginner Talk
---

### Post by e1ektrob0y on 2006-05-08
i installed dapper and everything was working fine for a few days untill tonight i can't connect to the internet anymore. firefox starts but no connection. the only thing i changed tonight was the login. i set it to automatic (no password prompt). but when i changed it back i still can't connect. anyone know whats going on?? thanks

---

### Post by steve.horsley on 2006-05-08
First, can you post the output from the commands "ifconfig" and "route".

How do you connect ot the internet - LAN, wireless, modem etc?

---

### Post by e1ektrob0y on 2006-05-09
connection-specific DNS suffix.: home
ip address............................:192.168.1.4
subnet mask.........................:255.255.255.0
default gateway....................:192.168.1.1

i connect via a router and the internet still works in windows. just not in dapper. i'm not sure how...........the only other thing was that i opened gedit and changed a line from yes to no to stop the clock from automatically setting itself to GMT. i got it from the ubuntu starter guide from this site's wiki. i don't see how that would have caused my problem though. anyway i wouldn't hesitate to re-install dapper as i havn't saved anything yet. only thing that would suck is having to download all those updates again!! anyway..................thanks

---

### Post by pommattski on 2006-05-09
I would try pinging the router IP first (192.168.1.1), then if that works try pinging an external IP address (eg.  64.233.167.99 - this is a google IP) , then if that works try pinging a domain name (eg. google.com).

Post back what happens, and would think someone should be able to suggest a next step...

---

### Post by e1ektrob0y on 2006-05-09
[QUOTE=pommattski]I would try pinging the router IP first 

Post back what happens, and would think someone should be able to suggest a next step...[/QUOTE]
do you mean ping from in windows or ubuntu. if you mean ubuntu then how do i do that? thanks

---

### Post by JKoder on 2006-05-09
[QUOTE=e1ektrob0y]do you mean ping from in windows or ubuntu. if you mean ubuntu then how do i do that? thanks[/QUOTE]

In Ubuntu is quite simple
in Application Menu->Accesories->Termina
open a termina and ttype: ping <domain_name>
where domain name could be : [www.google.com](www.google.com) or anything you wish.


Let me know if it si working

---

### Post by e1ektrob0y on 2006-05-09
[QUOTE=JKoder]In Ubuntu is quite simple
in Application Menu->Accesories->Termina
open a termina and ttype: ping <domain_name>



Let me know if it si working[/QUOTE]
i tried that but i tried to ping an ip address and it said command not found. can that be done or can i only ping a domain name?

---

### Post by e1ektrob0y on 2006-05-09
ok, tried that and i get a message that says network unreachable. also, i can't connect to download anything from synaptic. it says check network connections. i've been having some trouble with my windows network cause i use zonealarm and the ip of both my PCs gets changed all the time because of DHCP. so one day its 192.168.1.3 and another day its 192.168.1.4..........anyway could that have anything to do with it??

---

### Post by e1ektrob0y on 2006-05-09
ok, i got it working. i had to type the command network-admin and add my ip, subnet mask and gateway. somehow it had all dissapeared but yeah......................all good now. i just had to find that network admin tool.

---

### Post by Malcolm on 2006-06-03
[QUOTE=e1ektrob0y]the only thing i changed tonight was the login. i set it to automatic (no password prompt). but when i changed it back i still can't connect.[/QUOTE]

I just had a strange experience that sounds similar: I used gdmsetup to change my GDM login theme. After that, everything was fine until I rebooted. After the reboot, the internet wasn't working anymore. All the settings were still there but no internet, and even no LAN! Pinging my router didn't work ("network is unreachable"), and my router couldn't see my computer on the network. From another computer I tried pinging this one, no reply. The connection on that one worked, and it also worked on this computer after rebooting to Windows XP.

I tried network-admin to see if something was wrong. Nothing was, so I didn't change anything. I typed ifconfig to see if something was wrong in the output, it didn't look like it was. /etc/resolv.conf had the correct settings as well. Discouraged, I tried the last move: I changed my GDM login theme again, and rebooted, and here I am back online.

I know it sounds weird, at least to me. How could the GDM theme have anything to do with networking? Oh well. I suppose I have to try changing the theme there again, and see if it happens.

---

### Post by Mustard on 2006-06-03
Hmm...interesting symptoms.  Tell us how you go.

---

### Post by Malcolm on 2006-06-04
Okay, I was able to replicate the bug.

First, I used gdmsetup, and changed the theme to the one I had decided to use yesterday, which is called CleanLinux (downloaded with gnome-art). Rebooted and everything was working.

Then I did what I had done yesterday. I used gdmsetup and tried several different themes. Logged in and out, switched user, changed session (from Window Maker to GNOME); always using a different theme, trying out 4 themes in total. I changed back to CleanLinux, rebooted, and the internet was not working (the whole networking, actually). I changed back to the default Human theme, rebooted, and now everything works again.

---

### Post by Mustard on 2006-06-04
[QUOTE=Malcolm]Okay, I was able to replicate the bug.

First, I used gdmsetup, and changed the theme to the one I had decided to use yesterday, which is called CleanLinux (downloaded with gnome-art). Rebooted and everything was working.

Then I did what I had done yesterday. I used gdmsetup and tried several different themes. Logged in and out, switched user, changed session (from Window Maker to GNOME); always using a different theme, trying out 4 themes in total. I changed back to CleanLinux, rebooted, and the internet was not working (the whole networking, actually). I changed back to the default Human theme, rebooted, and now everything works again.[/QUOTE]

It might be worth searching [http://launchpad.net](http://launchpad.net) for current bugs that might have been reported that have the same symptoms, or if you can't find any to report this bug yourself so that it can be addressed.

---

### Post by Malcolm on 2006-06-04
Okay, I will report the bug if it isn't there already, thank you.

---

