---
title: "[SOLVED] How to open ports..."
date: 2007-12-03
forum: Absolute Beginner Talk
---

### Post by loverman210 on 2007-12-03
Hello everyone...

I was wondering how I could set an internal IP adress to my computer and then open a port in "firestarter" so that Azureus can work...

- I don't have a static IP - 

Please explain it as simple as possible

Thanks in advance

---

### Post by mikewhatever on 2007-12-03
> **loverman210 said:**
> Hello everyone...

I was wondering how I could set an internal IP adress to my computer and then open a port in "firestarter" so that Azureus can work...

- I don't have a static IP - 

Please explain it as simple as possible

Thanks in advance

Check out the screenshot below. The default set of ports is 6881-6889, so make sure Azureus uses one of those, or change appropriately.

---

### Post by Sarteck on 2007-12-03
1: Open a file in your init.d directory that will get loaded every time you boot.  We'll call this "iptables_azureus".```
sudo nano /etc/init.d/iptables_azureus
```


2: Next, we'll paste the code in there that you'll be using.  Copy and past this into there:```
  (sleep 220
    /sbin/iptables -I INPUT -p tcp --dport ##### -j ACCEPT
    /sbin/iptables -I INPUT -p udp --dport ##### -j ACCEPT ) &
```


3: Edit the **#####** for the top TCP entry to be your TCP port.  Edit the second to be your UDP port.


4: Press **Ctrl + X** to exit.  Press **Y** to tell it to save the changes.  Press **Enter** to save it as that filename.


5: Run it with the following command: ```
sudo  /etc/init.d/iptables_azureus
```


6:  Test Azureus under "Tools -> NAT/Firewall Test"


7:  Post here, saying if that worked


8:  Make me a cup of coffee.

---

### Post by philinux on 2007-12-03
This is weird init. I tried azureus and it would not connect to internet even playing with my router. So gave up and installed deluge and it connects no problem. So deluge must open ports by itself :confused:

---

### Post by mikewhatever on 2007-12-03
> **philinux said:**
> This is weird init. I tried azureus and it would not connect to internet even playing with my router. So gave up and installed deluge and it connects no problem. So deluge must open ports by itself :confused:

I very much hope Deluge can't open ports in your router, cause if it could, it would be a serious security breach.

---

### Post by Phosphoric on 2007-12-03
> **mikewhatever said:**
> I very much hope Deluge can't open ports in your router, cause if it could, it would be a serious security breach.

Isn't that what UPNP does?  If your router is UPNP compatible and your bittorrent client supports UPNP then it does forward whatever port it requires.  I believe that's the whole point.

---

### Post by loverman210 on 2007-12-03
I will try "mikewhatever" solution first cause it is the simplest one...if it fails, I will go to the more "space" one from "Sarteck"...

So, to begin with, my first problem is described by the above picture where firestarter doesn't provide me with the options which mikewhatever's picture has...

[IMG]http://i18.tinypic.com/80oarmp.png[/IMG]

Secondly, this command from sarteck doesn't work:

```
sudo  /etc/init.d/iptables_azureus
```

It says "bad command"

---

### Post by rune0077 on 2007-12-03
Here's another way, using the Firestarter GUI. First, make sure you know which port you want to open. Then open the Firestarter GUI and click the Policy tab. From here, right-click on an empty space in the middle box (it says something like:
    Allow service | Port | For
and select Add Rule. From the new dialogue box, simply type in the portnumber under Port, then click Add (or OK or whatever its called). Then remember to click Apply Policy, and you have opened the port for all services.

---

### Post by loverman210 on 2007-12-03
@rune0077:

I know but as you see in the picture my friend I don't have the options to do this...

let alone that I did something and now my firewall blocks everything when it's on...

---

### Post by mellowd on 2007-12-03
> **Phosphoric said:**
> Isn't that what UPNP does?  If your router is UPNP compatible and your bittorrent client supports UPNP then it does forward whatever port it requires.  I believe that's the whole point.

UPNP is a gigantic security hole. It should never be used!

You should always open up and forward the required ports yourself. Never let it be done autiomatically.

---

### Post by rune0077 on 2007-12-03
> **loverman210 said:**
> @rune0077:

I know but as you see in the picture my friend I don't have the options to do this...

let alone that I did something and now my firewall blocks everything when it's on...

Oh, that's strange (couldn't see the pic before, it was a bit small). Best bet: try uninstalling and reinstalling Firestarter, 'cause my version of it does not look like yours.

---

### Post by loverman210 on 2007-12-03
did it already ... still the same...

I don't know how to configure my network settings....

---

### Post by mellowd on 2007-12-03
> **loverman210 said:**
> did it already ... still the same...

I don't know how to configure my network settings....

What firewall/router do you have? How is your network set up? Have a look here: [www.portforward.com](www.portforward.com)

---

### Post by loverman210 on 2007-12-03
OK! problem solved!! I had forwarded the port to the wrong ip in my router!
many sorry for your trouble and many thanx for your time!!

---

