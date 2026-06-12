---
title: "Drivers for monitors"
date: 2008-02-18
forum: Absolute Beginner Talk
---

### Post by cybertron3000 on 2008-02-18
How do I install the correct driver for my new Samsung Syncmaster monitor?

---

### Post by zerhacke on 2008-02-18
Monitors in Linux don't really use a driver.  What it uses is some settings in /etc/X11/xorg.conf that tell the computer how to set up the monitor.

---

### Post by RedRat on 2008-02-18
For Gutsy Ubuntu 7.10: Go to **System** on the tool bar at the top of your screen. Open the menu and select "**Administration**", you will have to login with your password then open "**Screens and Graphics**". A pop up window will open and select the "**Screen**" tab. 

You will see on the left "**Screen1**" and to its right will be "**Monitor**", Click on the space where the name of your monitor should be, you may have some generic in there right now. When you click on the space, another popup will come and you can then select from the long list. There is a quite a long list of Samsung monitor models to choose from. Select your monitor and model and then click on **OK**.

You will want to select the correct resolution for your LCD monitor, you should always use the Manufacturers recommended native resolution. For example, mine is a Samsung 191t, and its native resoultion is 1280x1024. 
After you do that, click ok. You may have to restart your computer for the settings to take affect.

---

### Post by cybertron3000 on 2008-02-18
So I don't need to make any settings changed in the "Screens and Graphics" menu?  My screen is a bit fuzzy regardless of changing the resolutions.

---

### Post by cybertron3000 on 2008-02-18
I tried that, actually, and my brand must be too new for the list.  Mine is a 932bw model.  I tried something close to it, and fried my 2nd copy of Ubuntu.  Fortunately I have this back-up of Ubuntu.

---

### Post by zerhacke on 2008-02-18
> **cybertron3000 said:**
> So I don't need to make any settings changed in the "Screens and Graphics" menu?  My screen is a bit fuzzy regardless of changing the resolutions.

That would be a hardware problem and not software.  You're not going to correct that with software.

Try another monitor and see if it works.  If need be (the X server won't start) at a command line type sudo dpkg-reconfigure xserver-xorg

---

### Post by mivo on 2008-02-18
> **cybertron3000 said:**
> So I don't need to make any settings changed in the "Screens and Graphics" menu?  My screen is a bit fuzzy regardless of changing the resolutions.

"Fuzzy" usually means you have selected a screen resolution that is not the native resolution of your LCD/TFT monitor. What's the exact model name of your Syncmaster?

---

### Post by cybertron3000 on 2008-02-18
Okay - worth a shot.

---

### Post by cybertron3000 on 2008-02-18
My exact brand is Samsung Synchmaster 932BW.  It may be fuzzier because my old HP Pavilion 521c desktop doesn't have a DVI connection so it is analog.

---

### Post by RedRat on 2008-02-18
For Gutsy Ubuntu 7.10: Go to **System** on the tool bar at the top of your screen. Open the menu and select "**Administration**", you will have to login with your password then open "**Screens and Graphics**". A pop up window will open and select the "**Screen**" tab. 

You will see on the left "**Screen1**" and to its right will be "**Monitor**", Click on the space where the name of your monitor should be, you may have some generic in there right now. When you click on the space, another popup will come and you can then select from the long list. There is a quite a long list of Samsung monitor models to choose from. Select your monitor and model and then click on **OK**.

You will want to select the correct resolution for your LCD monitor, you should always use the Manufacturers recommended native resolution. For example, mine is a Samsung 191t, and its native resoultion is 1280x1024. 
After you do that, click ok. You may have to restart your computer for the settings to take affect.

---

### Post by mivo on 2008-02-19
> **cybertron3000 said:**
> My exact brand is Samsung Synchmaster 932BW.

Okay, that's a 19" wide screen monitor, so its native resolution is 1440x900. Are you offered this resolution in System -> Preferences -> Screen Resolution? If not, you may need to edit xorg.conf a little, or better yet, run the config program from the terminal, like so:

```
sudo dpkg-reconfigure xserver-xorg
```

It's relatively self-explanatory and you can usually go with the defaults. Make sure that 1440x900 is selected as the highest supported resolution. Every other resolution will look fuzzy on your monitor.

Try what RedRat suggested first, but if you are still not offered 1440x900, edit xorg.conf or run the above command, which will do it for you. :)

---

