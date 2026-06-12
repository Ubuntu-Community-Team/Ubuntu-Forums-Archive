---
title: "Wireless problem with 7.10 on Tosh tecra"
date: 2007-12-03
forum: Absolute Beginner Talk
---

### Post by Paresh on 2007-12-03
Hi,

I'm new to ubuntu and I'm using it on my Toshiba Tecra A9.  I have Vista and Ubuntu 7.10 set up as a dual boot.

The problem is this:
When using the wireless connection, the connection manager will list my network as available but will not automatically connect.  If I click on the connection, it will try to connect and fail.  If I choose 'connect to other wireless network' and enter the SSID and password, it connects fine and I have full use until I close the lid (to suspend) and then when I re-open I have to repeat the procedure.

Everything works fine when I boot into Vista

For info, lspci reports my wireless card as Intel 3945ABG.

Other than this little annoyance, I am enjoying my Ubuntu experience.

Thanks in advance for any assistance.

Paresh

---

### Post by ferdostar on 2007-12-03
Why don't you try to install wireless radar, and configure you wireless network than?

---

### Post by Paresh on 2007-12-04
Can you guide me on how to install this?

I'm currently using ubuntu 7.10 'out of the box' with no enhancements, and I'm new to Ububtu (in fact, I'm new to Linux*)

---

### Post by ferdostar on 2007-12-04
> **Paresh said:**
> Can you guide me on how to install this?

I'm currently using ubuntu 7.10 'out of the box' with no enhancements, and I'm new to Ububtu (in fact, I'm new to Linux*)
The easier for you will be:
1) Go to Applications > Add/Remove...
2) Chose to show all avaible applications 
3) Type in the search wifi radar 
4) Check the box > apply and follow the instructions

Than I think you could manage your wireless network. Post when you done :)

---

### Post by scrooge_74 on 2007-12-04
> **Paresh said:**
> Hi,

I'm new to ubuntu and I'm using it on my Toshiba Tecra A9.  I have Vista and Ubuntu 7.10 set up as a dual boot.

The problem is this:
When using the wireless connection, the connection manager will list my network as available but will not automatically connect.  If I click on the connection, it will try to connect and fail.  If I choose 'connect to other wireless network' and enter the SSID and password, it connects fine and I have full use until I close the lid (to suspend) and then when I re-open I have to repeat the procedure.

Everything works fine when I boot into Vista

For info, lspci reports my wireless card as Intel 3945ABG.

Other than this little annoyance, I am enjoying my Ubuntu experience.

Thanks in advance for any assistance.

Paresh

Your is more of a problem of suspend and hibernate than of which app to use to connect to internet.

Check threads about acpi and suspend mode for your card model, your laptop model and gutsy

---

### Post by Paresh on 2007-12-06
Installed wifi radar.

It will see my network, but will not let me edit it.  Icon shows a ?

I can create new ones and edit them and I can't create one with the same SSID

---

### Post by Paresh on 2007-12-06
> **scrooge_74 said:**
> Your is more of a problem of suspend and hibernate than of which app to use to connect to internet.

Check threads about acpi and suspend mode for your card model, your laptop model and gutsy

It happens even when I power down, or switch from wired to wireless, so I don't think it's purely to do with acpi.

---

### Post by ferdostar on 2007-12-06
> **Paresh said:**
> Installed wifi radar.

It will see my network, but will not let me edit it.  Icon shows a ?

I can create new ones and edit them and I can't create one with the same SSID

I'm not sure, but I have two ideas:
1) Go to System > Admnistration > Network and check the properties of the mode you connect to your wireless network, and try to configure manually
2) Go in gconf-editor select the essid of the network you wish to edit. Right-click on the bssids key and choose Edit Key... Remove the bssid values of the access points that you do not wish to connect to, leaving the ones that you do wish to connect to. Click OK and then quit Gconf-editor.

You can take a look of this [https://help.ubuntu.com/community/WifiDocs/NetworkManager](https://help.ubuntu.com/community/WifiDocs/NetworkManager) and this [http://live.gnome.org/DarrenAlbers/NetworkManagerFAQ](http://live.gnome.org/DarrenAlbers/NetworkManagerFAQ)

Hoppe this will help you :confused:

---

### Post by Paresh on 2007-12-11
Thanks guys

That helped and my wireless now works correctly.

The solution was to remove the SSID for the wifi network and let network manager re-configure itself for that network.

After that it all worked fine, so I guess the settings were screwed somehow

---

