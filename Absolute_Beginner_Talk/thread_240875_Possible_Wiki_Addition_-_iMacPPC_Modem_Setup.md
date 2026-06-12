---
title: "Possible Wiki Addition - iMac/PPC Modem Setup"
date: 2006-08-21
forum: Absolute Beginner Talk
---

### Post by GREGMACKENZIE on 2006-08-21
Hi,

I've been tinkering with Ubuntu, anyway I noticed that the simple way to set up an iMac internal modem isn't really covered anywhere. Anyway I took a run at the text for a wiki and I'd be interested in any opinions of the text, additions etc. There are some graphics but I don't imagine I'd be able to include them here unless they were posted somewhere to the net? I'm kind of puzzled too about adding graphics to a wiki. Do they have to be already on the net somewhere?

Greg

- - -

Configuring The Dialup Modem in Ubuntu With Network Settings or Gnome-PPP

Network Settings

From the panel at the top of the desktop window press System/Administration/Networking to open the networking panel.  You will be asked to enter the administrator's password to proceed. The following panel is displayed after the password is accepted.

Graphic 

In the Network settings panel to use dialup you must first create a new location. Click on the arrow at the right of Location, choose Create Location. The select location name dialog box will appear which prompts you to enter the location name. This can be anything you like, I entered Erewhon. Enter a name for your location and click on OK.

Graphic 

The next step is to select Modem Connection and click on Properties. Notice in the following panel that the Modem connection says that “The Interface ppp0 is not configured.
 
Graphic

The Interface properties panel appears. In the General tab you must check the box that says “this device is configured” to enter the internet service provider data. Enter information into each of the fields. Enter the telephone number without any dashes e.g. 1234567,  Dial Prefix e.g. 9, Your internet account username, and the password used to connect to the internet.

Graphic 

In the Modem tab click on Autodetect to find the modem. On an iMac this is automatically detected because the modem is hardware inside the iMac. Note as in following panel the setting for the modem appears if the modem is detected. Alternatively the string could be entered into the dialog box if the user knows what it should be.

Graphic

Finally, in the Options tab we have the last setting, which is the default route to the internet. Note that there has been a caution associated with checking the box. On dialup sometimes the computer will attempt the dialup connection during the computer boot. To prevent this uncheck this box. However, I leave it set since I turn off the modem using deactivate.

Grahic 

Click on OK to set the properties and return to the Network Settings panel. This is not a guarantee the next time the user logs on after rebooting that the settings will still remain. They may have to be re-entered! However, we have been successful in entering our information so notice that the Modem connection says that it is not active. When we began it said that it was not configured. If you return to the Network settings panel, choose your Location, and see that the message says “The interface ppp0 is not configured” your settings have been lost somehow.

Graphic
 
On returning to the Network Settings panel you must now press Activate to initiate the dialup connection. If you are successful and have entered your dialup service provider information properly you should now have an active connection. In the following dialog box “The interface device ppp0 is active is displayed. and the Deactivate button will highlight. Click on OK. We can now surf the net to double check our progress. Select Applications/Internet/Firefox Web Browser from the top panel of the desktop to launch the web browser.

Graphic 

When you wish to disconnect from the internet  you must re-open the Network Settings and click on Deactivate.

Observations

Note that on the whole I didn't like this unreliable panel. I decided the Network settings panel was unreliable after it lost my settings several times, connected to the internet on its own during boot up, and was just too slow, the connection speed dragged.  So after establishing a connection with it I used Synaptic to install Gnome-PPP.

Gnome-PPP

I like this so much it I think it should be included in Ubuntu by default. Since we're stuck with the Network settings by default  you have to negotiate with that and get it working before you can use Synaptic to include the extra repositories, reload them, and then find and install Gnome-PPP. That's a separate wiki. 

Here's how to configure Gnome-PPP once its installed. Choose Applications/Internet/Gnome-PPP. If you like you can drag its icon to the desktop thereby creating a shortcut. The following panel appears.

Graphic 

As before, enter  your dialup service provider information. Also, click on Setup to really configure your modem! The following setup panel appears:

Graphic 

As with the Networking settings, you can auto detect the modem, click on Detect. Alternatively, you can choose your setting from the list. Note that the speed is set to 115200. This refers to the communication speed between my iMac motherboard and the 56k modem and is not the actual communication speed. I used the first panel to set the telephone number so I didn't set any using the phone numbers button. Click on Init Strings to enter the iMac modem string. Note that the line Init 2 appears as the default, or first line in the list of Init Strings.
 
Grahic

Attention: The apple modem string illustrated above is different than the default string. I prefer the apple string as it seems to make the modem faster, so I entered it instead into Init 2. The illustration above shows the apple init string.

For illustration, the Networking panel is shown, but I left its settings at their default.

Graphic
 
I also left the settings under the Options tab at their defaults.

Graphic

Click Close to return to Gnome-PPP.  In your panel the service provider information will be entered into the boxes. Click Connect to start your dialup connection. The interface will then show it is dialing, waiting for prompt, and then an active connection.

Graphic

If you are successful the following panel will appear:

Graphic
 
The nice thing about Gnome-PPP is it shows how long you've been online. When you want to stop using the dialup connection, click on Disconnect.

Notes

These procedures were tested on an early model Tray Loading iMac G3, bondi blue 333 mhz, with rage pro video and 288 mb of ram running Ubuntu Hoary 5.0.6

According to reports the iMac modem is sensitive to line noise, so it is recommended that it not share it's line with other devices. A good quality phone line is essential.

If the modem appears unresponsive, which happened to me at least once, unplug it and replug it back into the iMac.

---

