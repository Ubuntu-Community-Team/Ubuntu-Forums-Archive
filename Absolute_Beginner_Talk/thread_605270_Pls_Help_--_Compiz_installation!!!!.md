---
title: "Pls Help -- Compiz installation!!!!"
date: 2007-11-06
forum: Absolute Beginner Talk
---

### Post by saggylj on 2007-11-06
Hello,

I am a new to ubuntu, infact to the linux community and i guess it will need lot of patience of anyone willing to help as i am absolute blank about configuration etc. i have installed ubuntu 6.06 got myself familiarised and now managed to install Gutsy successfully.

I am trying to make compiz work on my gutsy Desktop which is a DEll optilex GX280 with onboard Intel graphic card 910GL, but when i go to Appearance > visual effect and click on extra i get "desktop effects cannot be enabled" error.

When i type 'compiz' in the terminal i get 'XGL: not present error.

Can anyone help me get this working. Also i would appreciate if you can direct me to some documentation of some sort to start learning 'editing conigurations and installing drivers etc on ubuntu/linux.

All help will be much appreciated.

Thanks you 

saggy

---

### Post by Hospadar on 2007-11-06
what happens when in a terminal you type "glxgears"  Also have a look at the restricted drivers manager in System->Administration.  My guess is that you arn't using the proprietary drivers for your graphics hardware.

---

### Post by Maestro23 on 2007-11-06
Intel Section of the wiki might come in handy: [http://wiki.compiz-fusion.org/Hardware/Intel](http://wiki.compiz-fusion.org/Hardware/Intel)

---

### Post by akiratheoni on 2007-11-06
> **Hospadar said:**
>  Also have a look at the restricted drivers manager in System->Administration.  My guess is that you arn't using the proprietary drivers for your graphics hardware.

I have an intel card, but I think it might be a newer model. IIRC, Intel has open source drivers so the restricted drivers manager isn't necessary.

The drivers that come with Ubuntu should be sufficient for your computer, I haven't heard of any proprietary drivers for Intel cards.

---

### Post by saggylj on 2007-11-06
> **Hospadar said:**
> what happens when in a terminal you type "glxgears"  Also have a look at the restricted drivers manager in System->Administration.  My guess is that you arn't using the proprietary drivers for your graphics hardware.


Thanks for the quick help !!! You are correct Hospadar! i went to the graphic hardware and selected the correct hardware.. i am able to get compiz working now.. but when i ran compiz from the terminal i still got 
Checking XGL:not present error. I am able to enable the visual effects and get compiz runnig but now working towards installing compizconfig settings manager and get the cube effect working. Please send any suggestions.

Thank you

saggy

---

### Post by jordanmthomas on 2007-11-06
```
Checking XGL:not present
```
That is not an error, just a notification.  Don't worry about it in the least.  (actually, it's better if you're NOT using XGL)

---

### Post by saggylj on 2007-11-06
> **akiratheoni said:**
> I have an intel card, but I think it might be a newer model. IIRC, Intel has open source drivers so the restricted drivers manager isn't necessary.

The drivers that come with Ubuntu should be sufficient for your computer, I haven't heard of any proprietary drivers for Intel cards.

Thanks for the input Buddy, i have chosen the correct driver now and compiz seem to be working i am getting the wavy effect when i drag the windows but now trying to install compiz settings manager.

Any suggestions??

Thanks Again

---

### Post by jordanmthomas on 2007-11-06
```
sudo apt-get install compizconfig-settings-manager
```
doesn't work?

---

### Post by ubnewbie2 on 2007-11-06
> **saggylj said:**
> Thanks for the input Buddy, i have chosen the correct driver now and compiz seem to be working i am getting the wavy effect when i drag the windows but now trying to install compiz settings manager.

Any suggestions??

Thanks Again

go to add/remove programs, select "All available applications"  search for "compiz".  Select and install "Advanced Desktop Settings (ccsm)"

---

### Post by saggylj on 2007-11-07
> **ubnewbie2 said:**
> go to add/remove programs, select "All available applications"  search for "compiz".  Select and install "Advanced Desktop Settings (ccsm)"

HI! I tried doing that but when i mark it for installation it says 'this application has conflict with other application, please remove the conflict from synaptic adn try again' but it does not mention which application has a conflict.

---

### Post by saggylj on 2007-11-07
> **jordanmthomas said:**
> ```
sudo apt-get install compizconfig-settings-manager
```
doesn't work?

HI, Yesterday i was getting the wobbly effect but now when i run compiz it gives me 'Error: Couldn't load plugin 'ccp', now all the application windows are locked. i cannot even move them. :(


yesterday i was trying to install 'python compizconfig' but it gave error saying cannot install python compizconfig.

---

### Post by ubnewbie2 on 2007-11-07
> **saggylj said:**
> HI! I tried doing that but when i mark it for installation it says 'this application has conflict with other application, please remove the conflict from synaptic adn try again' but it does not mention which application has a conflict.

Strange.  What happens if you try installing it using Synaptic instead?

---

### Post by saggylj on 2007-11-09
> **ubnewbie2 said:**
> Strange.  What happens if you try installing it using Synaptic instead?

I get this

Depends: python-compizconfig but it is not going to be installed. now i am trying to install python comizconfig.. but from where i have downloaded .. it is not working gives error..

I tried to install a package named Bulletproff compiz install" which contained all teh necessary packages. but now i am getting this when i run compiz i get this
Checking for Xgl: not present. 
Detected PCI ID for VGA: 00:02.0 0300: 8086:2582 (rev 04) (prog-if 00 [VGA])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x1024) to maximum 3D texture size (2048): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Starting gtk-window-decorator
/usr/bin/compiz.real (core) - Warn: Unable to parse XML metadata from file "core.xml"


Also any window i open it is stuck tu the top panel and i cannot move it.

Any help please.?

Thanks

---

