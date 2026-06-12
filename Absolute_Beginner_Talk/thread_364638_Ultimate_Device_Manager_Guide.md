---
title: "Ultimate Device Manager Guide"
date: 2007-02-18
forum: Absolute Beginner Talk
---

### Post by insyted on 2007-02-18
I am a linux newborn. Never used it.
Installed Ubuntu this morning.
I have spent all morning trying to find a guide to the device manager.
I am trying to understand how it works.
How can I tell if a device is working properly or not.

I have not installed any drivers. How do I add hardware, and automatically install drivers for them?

Do I just insert my mobo driver cd? I cannot tell if my hardware is recognized or not in device manager.

---

### Post by TriggerHappyChewie on 2007-02-18
You do not need to install any drivers, hardware should be recognized automatically.  Are you having problems with certain hardware?  Is there something that isn't working correctly?  Also, you cannot use any driver CD's that came with your harware, they are meant for Windows.

---

### Post by jvc26 on 2007-02-18
Your mobo cd will as usually is the case be designed for Windows. Do you have a more specific issue?
Il

---

### Post by insyted on 2007-02-18
Yes hello. How do I find out if my hardware is working properly?
Whatabout all of my motherboard drivers? In Windows, when I install XP, I have to insert the motherboard driver cd to install the motherboard drivers. This allows the onboard hardware to work such as sound, ethernet, etc.

Furthermore, there is the drivers for the video card and sound card that also need to be installed.

How can I check my hardware with Ubuntu, and have it install the necessary drivers if any?

---

### Post by TriggerHappyChewie on 2007-02-18
In linux, you don't have to install drivers like you do in XP.  Ubuntu should recognize everything, and if you want to know if your harware is working, just test it.  In other words, test your onboard ethernet by trying the internet, test onboard sound by playing a sound file, etc.

---

### Post by insyted on 2007-02-18
Thanks!


How do I test my graphics card?
I tried to access the internet with firefox, and it didn't work.
Sound is not working either.

---

### Post by kinematic on 2007-02-18
sound:play a sound file
video:if you see the desktop that means that your video card is working using a generic open source driver ;) (wich doesn't support 3d) 
as for ethernet....did you setup your ip address and such?
also what's the output of > lspci | grep Ethernet

---

### Post by insyted on 2007-02-18
Please undertsand that I have never used much less seen Linux before.
I do not understand that code.


This is all of my hardware:
Intel G965SS Motherboard.
Asus EN6200TC256/64 Video Card
Echo Gina 3G Sound Card



The motherboard came with a notice saying I have to go to Intel to update all of my drivers. I checked the Intel site which asked me to choose the OS. They had Linux systems such as Red Hat. They had Debian, but they didn't have Ubuntu. They also have an option for Linux.

As for getting online with my onboard ethernet, what should I do? I just opened the browser, and it didn't go.

The Video Card information is showing up in the Device Manager. Just don't know if the driver is installed for proepr performance.

Then there is the sound card which I tried to test using the Sound Preferences menu. The sound tests didn't seem to be doing anything. None of the system sounds were playing.


Please help me get all of this hardware working.

---

### Post by insyted on 2007-02-18
It seems buggy.
For example, when I wnet into Ubuntu Device Database to do some tests, I tested that the mouse was working properly. I went to the next screen to test ethernet, and it still asked me the previosu question "is your mouse working properly?". Furthermore, I do not see a "Login Window" option in my Administration or Preference menu. Nor do I see a "Security" option.

Is this because it is a 64bit install or is it like this in 32bit?

---

### Post by kinematic on 2007-02-18
i would advice you to get the 32bit version and continue from there setting up the proprietary video driver and such with the help from the forum.
the 64bit version can cause problems from what i've read from time to time on this forum.

---

### Post by insyted on 2007-02-18
Hi. formatted my computer, and installed the 32-bit version of Ubuntu. It did everything exactly the same way as I described above.

All the exact same errors occurred in the exact same way.

---

### Post by The Noble on 2007-02-18
Obviously, your graphics card is in a somewhat usable state right now, as you can actually use your desktop. Good idea to go with the 32 bit version of ubuntu, as that will save a bunch of headaches later, especially if you are new to linux.  When people tell you to input a command into the terminal, look at the top panel of the desktop. Ya see the Applications menu? Press it, and under the Accessories sub-menu is the terminal. Don't be scared though! It's not as bad as it looks, and is a viable alternative to the GUI most of the time, and will help you tremendously when you use the desktop. You can copy and paste things from the terminal using ctrl+shift+C/V. 

Ok, introduction out of the way, you need some help getting internet on the box. If you can get this taken care of, you have done one of the more difficult procedures required in getting a set up linux box. I am assuming you are using a wired connection through the ethernet port on the back of the computer. If you are trying to use a wireless connection, you may have a little trouble if your setup is not supported. 

**Setting up the internet connection:**

1. Click System, and navigate to the Networking button. This is where you will enable the connection. It will ask for your password, so input your user password.

2. You should see several selections for using the internet, all currently disabled. We want to enable the Wired Connection, so highlight it and click properties on the right hand side. 

3. Another box should come up, everything grayed out except a little checkbox that says "Enable this connection", so check it and make sure the configuration is set to DHCP, unless you have a static IP (if you don't know what that is, use DHCP). Close that little box

4. Now next to the highlighted 'Wired connection', there is a little box, click it until you see a check mark in it. Close the Networking Box.

5. You have successfully enabled your wired connection, so now you want to use it. At the top right of the screen is the button to shut down your computer. To the left is a little computer icon; you want to double click it. The "Name" it shows should be 'lo'. Change 'lo' to 'eth0' (or possibly eth1).

6. Try connection to the internet! Hopefully now you will have a connection if everything is plugged in.

**Sound**
How did you test the sound? Did the system make any noise when you logged in or shut down your computer? If it did, then everything is working. It is pretty rare that you would have a computer that doesn't have sound working, especially if you have a pre-built system.

Also, welcome to Linux and Ubuntu! It takes a while to get used to, but you will learn a lot and it will get really simple after a while.

---

### Post by insyted on 2007-02-18
Yes. I've checked out the terminal. It's similar to the UI of DOS which I am definitely not scared of. The hard part I think is getting to know the commands of this new OS. Obviously, I cannot type in "c:" to take me to my c drive. Then "dir" to see my files. etc.

Obviously, I need a real good primer on simple commands like that so I can do similar tasks that I am adept at in DOS.


Other than that, I was wrong about my internet. To my surprise, it works perfect. I simply forgot to plug my ethernet cable in. Woops. You can shoot me now.


I'm using an Echo Gina 3G PCI card. There is zero sound coming out of the speakers whatsoever. It doesn't seem to be recognized in the device manager although the device manager is difficult for me to understand. Are there any ultimate guides for understanding the device manager?

Anyways, any help with the sound situation will help.
Now that I am online, I can go to Intel, and download the drivers as stated in the insert of the my motherboard packaging.
Ubuntu is not on their list.
Should I choose Linux or Debian?
Or do I not need to install anything at all? not sure what I shoud do.


As for my vid card. In my experience, vid cards always tend to work in basic mode until you install all the drivers. Because I cannot understand the device manager to tell if this device is working properly, how can I test it out?

---

### Post by igknighted on 2007-02-18
> **insyted said:**
> Yes. I've checked out the terminal. It's similar to the UI of DOS which I am definitely not scared of. The hard part I think is getting to know the commands of this new OS. Obviously, I cannot type in "c:" to take me to my c drive. Then "dir" to see my files. etc.

Obviously, I need a real good primer on simple commands like that so I can do similar tasks that I am adept at in DOS.


Other than that, I was wrong about my internet. To my surprise, it works perfect. I simply forgot to plug my ethernet cable in. Woops. You can shoot me now.


I'm using an Echo Gina 3G PCI card. There is zero sound coming out of the speakers whatsoever. It doesn't seem to be recognized in the device manager although the device manager is difficult for me to understand. Are there any ultimate guides for understanding the device manager?

Anyways, any help with the sound situation will help.
Now that I am online, I can go to Intel, and download the drivers as stated in the insert of the my motherboard packaging.
Ubuntu is not on their list.
Should I choose Linux or Debian?
Or do I not need to install anything at all? not sure what I shoud do.


As for my vid card. In my experience, vid cards always tend to work in basic mode until you install all the drivers. Because I cannot understand the device manager to tell if this device is working properly, how can I test it out?

Ubuntu supports multiple sound cards, so I would guess that your issue is that Ubuntu sees the PCI device and the onboard mobo sound and is using the mobo sound device as default.  To get around this, first plug into the mobo sound jack to check if this is in fact the problem, then either (a, and recommended) restart your computer, go into the BIOS and disable onboard audio, or (b) right click the volume control on the panel, then open volume control.  go to file -> change device and select the one you want.  You might need to unmute it and mute the mobo sound.

As for the mobo drivers, I wouldn't bother unless you have a problem, as that is really what they are there for.  If it comes to it, I would choose Debian and then carefully examine any required packages and install them.  Others may disagree with this assessment, but the general linux drivers will probably require a compilation, which is a little trickier than the debian package.

---

### Post by The Noble on 2007-02-18
If you have a sound card form intel, i am sure that they have open source drivers. One thing we should mention: The linux kernel that is prebundled with Ubuntu has been patched with almost all of the opensource drivers out there. That is why a fully functional system is capable without installing the drivers later. Do what igknighted sais, and i bet your problem will be solved.

You noted that linux (the terminal) is like Dos, and that is definately true. If you know Dos commands, that will help a lot. Dir works, ls works, cd works, a bunch of those commands actually work. If you want to learn quickly, just stick the the tutorials and figure out what they are trying to accomplish, and you will learn quickly.

---

### Post by insyted on 2007-02-19
Sweet about the Terminal commands being similar to DOS!

As for mobo drivers, the main thing I am concerned about is that Edgy Eft was released before I pruchased my mobo which came with a slip saying that the drivers have recently been updated. If that is so, could it be possible that Intel released updated versions of their drives before edgy eft was released? Either way, I don't have a great understanding of drivers.
Here is the download site: [http://downloadfinder.intel.com/scripts-df-external/Product_Filter.aspx?ProductID=2376](http://downloadfinder.intel.com/scripts-df-external/Product_Filter.aspx?ProductID=2376)

Firefox is running way faster than my IE browser on my old computer. Not sure if it is the browser or the hardware, but my internet is running great.

As for the sound, I searched my whole bios interace, and found nothing in terms of audio. My graphics, USB, peripherals were all there including front panel audio. But nothing for actual audio.

I also checked to see if I can change my screen resolution. The video card is capable of 2048 x 1536 which is not an option there. The options go up to 1024 x 768. This is a typical situation for a vid card that does not have all the drivers installed. I'm not sure how to get it working at full capacity.

---

### Post by insyted on 2007-02-19
My audio has been working fine from my mobo integrated sound. I just plugged in a set of regular speakers.
As for my pro speakers plugged into my Echo Gina 3G sound card, I'm still not getting anything.

---

