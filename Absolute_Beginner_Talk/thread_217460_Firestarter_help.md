---
title: "Firestarter help"
date: 2006-07-17
forum: Absolute Beginner Talk
---

### Post by goodfren on 2006-07-17
I have install firestarter firewall, when i turn on the firestarter, it will block me from excessing the internet using adsl connection.

Please guide on the firewall setup that allowed me to excess internet and able to download file.

Thks

---

### Post by goodfren on 2006-07-17
Any advice!

---

### Post by Apple 101 on 2006-07-17
How is your ADSL connection linked to your computer?  LAN, USB, etc.?  You also need to tick the box that says something about DHCP renew (look in Preferences).

---

### Post by HereInOz on 2006-07-17
Open the Firestarter GUI, then click on Policy.  Where it says "Editing, click on the selection box to display the Outbound Traffic Policy.  It should  be set at "Permissive by default, blacklist traffic" as a starting point.

If it is set at this setting, this means that it is allowing all traffic outbound through your ADSL modem/router.

The other thing you may need to do, depending on the setup, is to, in the same area, now select the Inbound traffic Policy, and right click in the area below "Allow Connections from Host" and then select "Add rule"

In the box that shows up, enter the IP address of your gateway - the modem/router IP address. Click Add, and then click the Apply button.

See how you go. If this doesn't fix it, then there is something strange going on.  Have a look in the Events tab, and see what traffic is being blocked.  This might give you some clues as to what is going on.

---

### Post by goodfren on 2006-07-17
> **Apple 101 said:**
> How is your ADSL connection linked to your computer?  LAN, USB, etc.?  You also need to tick the box that says something about DHCP renew (look in Preferences).
It was through LAN, have tried your way but failed. One thing i notice, there are no renew word in DHCP

---

### Post by goodfren on 2006-07-17
> **HereInOz said:**
> Open the Firestarter GUI, then click on Policy.  Where it says "Editing, click on the selection box to display the Outbound Traffic Policy.  It should  be set at "Permissive by default, blacklist traffic" as a starting point.

If it is set at this setting, this means that it is allowing all traffic outbound through your ADSL modem/router.

The other thing you may need to do, depending on the setup, is to, in the same area, now select the Inbound traffic Policy, and right click in the area below "Allow Connections from Host" and then select "Add rule"

In the box that shows up, enter the IP address of your gateway - the modem/router IP address. Click Add, and then click the Apply button.

See how you go. If this doesn't fix it, then there is something strange going on.  Have a look in the Events tab, and see what traffic is being blocked.  This might give you some clues as to what is going on.
Have tried your way and not working, i see no event. My adsl will change to new ip everytime there is login, so how i am going to add ip rules? What host name? how to input host name? Give some example if you can, thks

---

### Post by ProjectGod on 2006-07-17
just skimmed all the posts here... and picked up DHCP on and firestarter blocking some traffic...
hmmmmm :-k try adding udp ports 67 and 68 to the incoming rule. on firestarter... i use static IPs, theyre so much easier to share resources in a work group enviro. especially if MS windows is the prominent OS.

furthermore make sure you've got OUTBOUND TRAFFIC under POLICY as PERMISSIVE BY DEFAULT... 

let me know how you go... sorry bearly read anything above!

---

### Post by goodfren on 2006-07-17
> **ProjectGod said:**
> just skimmed all the posts here... and picked up DHCP on and firestarter blocking some traffic...
hmmmmm :-k try adding udp ports 67 and 68 to the incoming rule. on firestarter... i use static IPs, theyre so much easier to share resources in a work group enviro. especially if MS windows is the prominent OS.

furthermore make sure you've got OUTBOUND TRAFFIC under POLICY as PERMISSIVE BY DEFAULT... 

let me know how you go... sorry bearly read anything above!
No it failed to work as well

---

### Post by Apple 101 on 2006-07-18
Are you behind a router, or is it a direct connection?

---

### Post by goodfren on 2006-07-18
> **Apple 101 said:**
> Are you behind a router, or is it a direct connection?
Thks for your concern, i have decided to remove fs as it is too complicated for me.

I have try guarddog now but i cannot see it icon around my application, do i need to also install guidedog as well for guarddog to works? Or guarddog just running behind without seeing it? As i read it description, it say it can protect automatically.

---

