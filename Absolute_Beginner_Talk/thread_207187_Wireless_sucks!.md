---
title: "Wireless sucks!"
date: 2006-07-01
forum: Absolute Beginner Talk
---

### Post by rtfmviolator on 2006-07-01
I have an HP laptop which I have already had running wireless with Ubuntu 5.10 at one time. I went out and bought a wireless card (Linksys) and used NDISWrapper to get it to work. Strangest thing is that what I did to activate Linksys ended up making my onboard Broadcom wifi work. Linksys just froze. Took back Linksys; however later I redid my machine and then upgraded to Dapper. I figured that Dapper would make my machine work automatically without doing anything. NOT!!! I'm not a very experienced user either. A friend helped me with NDSISWrapper last time. However, I see instructions for Broadcom and Airlink101, whish is what I am trying now. Hooking up to a wireless network with WEP is so easy, why won't it work??? Do I have to somehow change the inner workings of Linux and my computer first??? No matter what I try the damn thing won't find my router. Installed Automatix with laptop support....still nothing. Do I have to give it an IP, MAC address, some other numbers? A friend of mine uses the same card in his laptop and it works just fine. Instructions on the internet are so simple. Most people don't talk about doing anything but the simple SSID number, and basically just enable the card. I love using Ubuntu on my desktops, but this wireless issue really just pisses me off.

Help!!!

---

### Post by nickpaton on 2006-07-01
Hi - I too have an HP laptop (NX6125) which is currently residing on my lap whilst connected to the Netgear wireless router 2 floors up; I'm also running Dapper.  
The reason why I'm saying this is to encourage to persist.

To check one or two things (and I apologise in advance if some of the questions sound patronizing - definitely not the idea!!)

1. You say that you tried a Linksys card coz it appeared that the built in Broadcom wireless adaptor was not working, and then worked.  Is the blue light on, on the 'Wireless' on button at the top of the keyboard?  Does it work wirelessly in windows (if you use Windows)?

2. The next thing you need to do is to obtain the Broadcom Windows .inf Driver, and if your laptop is similar to mine, it will be the bcmwl5.inf file which can be found in Windows XP by doing a file search whilst in Windows and saving it into an appropriate FAT32 partition or onto a CD or your Ubuntu /Home<yourname> folder etc.  
Note that it has to be easily accessible within Ubuntu at the end of the day.
If you have a problem obtaining the .inf file, get back to me & I'll see what I can do.  Also do a search within these forums since I'm sure there's a link to directly download a version.  I'll post if I can find it.

3. You have already downloaded the Wireless GUI from Automatix which is excellent, and when installed will be found under System>Administration>Windows Wireless Drivers (WWD).

4. Click on WWD program, and after the login you will be presented with the Wireless Network Drivers (WND) box.

5. Click on 'Install new Driver' button which will take you to the 'Install Driver' box.

6. In this box navigate to the location where you saved bcmwl5.inf file and click on it.  Click on 'Install' button, and it should now appear back in the main window on the WND box.

7. Click on 'Configure Network' button which will take you to the 'Network Settings' (NS) box.  This is the slightly tricky part to get going and I suggest that you make a couple of chang es to your router before proceding:

Enter the wireless settings within the router, and note and temporarily disable any wireless encryption settings. 
Whilst you are there, note the SSID Network name.

8. Back in NS box you should see an Ethernet connection which is stated as being an active Eth0 (for example) interface.  The Default Gateway should also be indicated as that same Eth0. connection.

9. You should also see 'Wireless Connection' as being not active, so simply click on the 'Activate' button. (Make sure your blue Wireless light is on, on the laptop!).

10. It should now activate as a Wlan or Eth interface or similar (on my laptop it's Eth1).

11. REMOVE ANY LAN LEADs FROM THE LAPTOP (for emphasis not shouting!), so that you will now work on wireless.

12. Still within 'Network Settings', highlight 'Wireless Connection' and enter 'Interface Properties' (IP) box via the 'Properties' button.

13. Within IP ensure 'Enable this Connection' is ticked (should already be so), and complete the Network Name SSID (as noted in your router settings in (6)).
Set 'Key Type' to Hexidecimal (for when / if you add a WEP key), and leave the WEP key blank.  
Note I suggested that you clear your WEP key settings temporarily from your router in (6) above to assist in setting up.
'OK' the 'Interface Property' button to take you back to the NS box.

14. Within NS change the 'Default Gateway' to be the same as is indicated against your Wireless Connection Interface (ie Eth1 on my laptop example in (9) above.
OK the button, and you should now be connected.  It initially took a couple of minutes for everything to connect, and it could be worth doing a reboot of your laptop.

_General Notes_

I found it to be initially tempremental to connect, and played around with the Eth0 Eth1 Default Gateway settings. 
However to work wirelessly it should be set to the same as indicated for the wireless connection.
Also setting up without any encryption key cuts out any errors made in typing in wrong characters etc and preventing it all from working.  

Once you are satisfied it is working OK as an open connection, it is essential that you apply a WEP key ASAP for security purposes.  
First set up a WEP key within the router, and note the character set.
Back to Interface Properties box and apply the same WEP number in the WEP Key box.
Set 'Configuration' to be DCHP'.
OK all the way out.
And if the WEP key has altered from before you started, alter the WEP key settings within Windows as well.

Also you will note that in the top right corner of the desktop a 2nd Ethernet connection indication will have appeared representing the new wireless connection.  
On my laptop both it and the disconnected wired Ethernet connection are inexplicably shown as being disconnected.  The wireless connection is working though!

Setting the Default Gateway to the Wireless Connection does disconnect the wired Ethernet connection, and to use it you will need to change it over to the Ethernet Connection gateway setting for wired LAN operation.  In reality I work 100% of the time wirelessly now so not a real issue.

If you are using Firefox the following post gives a raft of settings to increase connection speeds:

[http://ubuntuforums.org/showthread.php?t=179540&highlight=firefox](http://ubuntuforums.org/showthread.php?t=179540&highlight=firefox)

Let me know how you get on - persistence is the name of the game here, and ask any questions - pleased to assist if possible.

(Added correct URL and some spelling errors)

---

### Post by Papa-san on 2006-08-10
I have a different system, but the same wifi. I saved the bcmwl.inf and .sys files right to my desktop, which made my upgrade a lot easier. What I ran into is that in trying to be helpful to us bcom users, the developers put in the proper driver. There wasn't an option to not use the 'new' driver, so I had to go through the ndiswrapper thing,  because of the tweaks I needed to make it work... I really need to upload this driver to a part of my site where people can just download the one I have ready for use! (I don't know how to do this though :(   )

---

