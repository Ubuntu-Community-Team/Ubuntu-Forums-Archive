---
title: "Wireless network bridging: Using wi-fi with older hardware [g3 + g4]"
date: 2013-07-15
forum: Apple Hardware Users
---

### Post by imacg3ppc on 2013-07-15
Don't buy a wireless network bridge for $150

I have come to find out that the older airport cards (airport classic, extreme) have problems connecting to certain networks and wifi devices and hotspots under lubuntu. My problem was that the airport classic card I have only supports WEP, and I needed WPA2-PSK to be able to connect to my 4gLTE Hotspot. After doing some research i have found very useful information when it comes to networking with older apple machines. This is also useful for other devices such as XBOX or anything with a LAN port.

What we're going to be doing is using almost any old router to use to connect to our access point or hotspot thru our LAN port, instead of messing with or buying an airport card.

The first step is to get your old wireless router out of the garage. You tossed it aside when you upgraded to Cox, Verizon FiOS, or comcast and they provided you a new proprietary one. You will need a router capable of broadcasting a wireless B or G network. If you have a hotspot that utilizes wireless-N, this is also supported, but we are going to focus on b/g.

Get the information off of the bottom of the device you are going to use. You want to know the model #, the and the build version. This will work with almost any wireless router.
The best router to use will be any Linksys WRT54G model. They are available on ebay, thrift stores, garage sales etc. I bought mine for $14 at Savers with lan cable and power cable, after I realized I already had one and threw it out!

Note: If you have a linksys wrt54g version 1 or 2, you will be using Sveasoft Alchemy Firmware. If you have v3 or above, we will be using the more widely supported dd-wrt firmware to update our router to transform it into a wireless "client" that will receive our signal from our hotspot.

[Short backstory: Linsksys released the firmware source code for their wrt54g (based on a broadcom chipset) router a few years back. Sveasoft created the alchemy firmware under the GPL license and made this possible.]

!! If you have a wrt54g v1 or 2 we are going to head to [HTML]http://wrt54g.thermoman.de/[/HTML] to get the firmware we need and follow those links for set up !!

As my example we are using a Linksys WRT54G v3.1. Get the info off your router and head over to [HTML]http://www.dd-wrt.com/wiki/index.php/Supported_Devices[/HTML]
Find your brand, model, and version number using the table. There are different "flavors" of the dd-wrt firmware based on the version and the capacity of the internal flash memory.
My WRT54G uses what they call the dd-wrt "MINI" v24 firmware build.

Once you locate your router, click the installation instructions on the right side of the table. This will tell you what version you need, what optional versions you can use, and the basic setup instructions.

In the case of Linksys, (which is probably the best choice to use for this project) you need to know how to reset your router first. We need to do what's called a 30/30/30 reset. Plug in the power and let the cycle complete until router is at rest.
-Hold The reset button for 30 secs.
-While continuing to hold reset button, unplug power cable for 30 secs.
-Still continue to hold reset button and plug cable back in, holding for another 30 secs.
You have now done a "hard reset" on your router which has flashed it back to default settings.

Now you are ready to update the firmware on the device.

Clear your browser cache and disable any networking. Plug in a LAN cable from the router's output #1 jack. Plug into your machine.
[NOTE: Many walk-thrus tell you to set a static IP address to your computer before you start the setup. I did not have to do this, as the router connected to my machine and assigned it an IP]

Turn on networking and the router should now be active to your LAN port. Give it a minute to connect.

Next, we access the router setup screen. For linksys, the default is '192.168.1.1' - type this into your browser.
[NOTE: It is also possible to login to the router via telnet or SSH, but we are not going to get into that.]

You will see the linksys [or belkin, or whatever] control panel, settings, status monitors etc.
You want to click the 'Administration' Tab. There will be an option to update the firmware. Choose the firmware file that you downloaded based on the table for your router. Click 'Update' and you may see a graphic that says processing, or you may just see your browsers status bar slowly moving. Do not do anything for at least 6 minutes! Even if it says it has completed.

The interface should refresh. If not, after 6 minutes, head back to 192.168.1.1 (or your routers address if different).

It should ask you to change the default password. Go ahead and do so. If it does not have you change it right away, you have not correctly done your hard reset, try again.
If you encounter any other errors at this point, you have not correctly done your hard reset. Try it again.

You are done with the hardware setup!

The rest of the setup process will now depend on the router and firmware build you have.
Generally you will want to make sure you have the router in "Client Mode" and you can then enter in the ssid and password info for the network you want to connect to via the setup tabs. I am not going to cover anything further regarding this because there is so many variants depending on your home or office network. Please read dd-wrt documentation for your specific application.

Once I entered in SSID in the client setup, and the password in the security tab (mine happens to be wpa2-psk), my hotspot assigned an IP to my linksys dd-wrt bridge and my dd-wrt bridge gave my computer an IP. Done. I clicked firefox, google came up and i had finally gotten my awesome special edition imac online with lubuntu 12.04.

Check out [HTML]http://www.dd-wrt.com[/HTML] for in-depth instructions.
There are many types of setups and specialized applications for using dd-wrt, and many possibilities for why or where you may want to use this. Even if you don't need a wireless bridge, scan thru the pages because you will find a use for this technology.

Please let me know if anyone finds this of use!
Happy bridging.

---

### Post by imacg3ppc on 2013-07-16
Also be sure to check out [https://openwrt.org/](https://openwrt.org/) for even more wireless bridging options.

---

### Post by imacg3ppc on 2013-08-06
Update:

I have been using this setup for more than 3 weeks now, and it has proven reliable, quick, and easy.
Even when I encountered a power surge and lost power to the router, I was able to just turn everything back on and did not have to set up a thing. 
The linksys WRT54G equipped with dd-wrt firmware connects to my 4g hotspot instantly, automatically, as soon as i turn it on. 

This was an easy project and I spent only $14.99, and about 1 hour, which would take me now about 20 minutes to set up a new machine.
Additional machines can be added by simply plugging in to the routers LAN ports so I am installing Xbox Linux on an old Xbox to get streaming and extra storage on my network.

PPC FTW.

---

