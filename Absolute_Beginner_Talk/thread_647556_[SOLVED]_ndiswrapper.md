---
title: "[SOLVED] ndiswrapper"
date: 2007-12-22
forum: Absolute Beginner Talk
---

### Post by jamestang on 2007-12-22
Hello, I just installed 7.10. I installed ndiswrapper using System/Administration/Synaptic Package Manager but can't seem to find System/Windows Wireless Drivers. Thanks.

---

### Post by wieman01 on 2007-12-22
You need to get hold of the drivers yourself, they do not come with "ndiswrapper". Have you got a CD or something?

Take a look at my Ralink tutorial as a reference (signature).

---

### Post by ashishgoel on 2007-12-22
u'll need windows driver after installing ndiswrapper, which u can download from company's site or u can direct the prog to CD...

---

### Post by jamestang on 2007-12-22
I downloaded a driver on to Windows. How can I get it to Ubuntu? I'm trying to get my wireless connection working so no Internet access on Ubuntu. Thanks.

---

### Post by anewguy on 2007-12-22
I would imagine that the driver is compressed into a .exe for Windows.  But before we go any further, tell us the wireless card type and we might be able to point you to things specific to it.  On your Linux box,  do "lspci" while in a terminal window, then look for your wireless card amongst that list and post back here.  We may be able to give you very specific instructions once we know that.  I've installed/used ndiswrapper many times with no failures.:)

---

### Post by jamestang on 2007-12-22
It's a Dell Wireless 1500 Draft 802.11n WLAN Mini-Card. My computer is a Dell Inspiron E1705.

---

### Post by RomeReactor on 2007-12-22
Hi. NdisWrapper is a command line program; to get a menu entry for "Windows Wireless Drivers" in "System->Administration", you need to install NdisGTK, which is NdisWrapper's graphical interface; look for it in Synaptic, or to install it from the terminal:
```
sudo apt-get install ndisgtk
```

---

### Post by anewguy on 2007-12-22
I'm looking at the download right now and hope to post back some instructions for you in a little while.  I'll need to break for supper sometime, so it might an hour or two but I will get back to you!:)

---

### Post by anewguy on 2007-12-22
Okay, here is what I would try:

(1) Download the driver from Dell.  I selected the one that said it was for the 1500 with "n" support.  Just let it download to your desktop.  In your case, I beleive you had to download it to Windows.  Burn a CD of it from Windows, then put the CD in the laptop drive for Linux.  You can drag the file from the CD to your desktop in Linux.

(2) When the download finishes, right-click to the file on your desktop and select open with another application and select archive manager

(3) Double-click on "DRIVER" folder

(4) Select/highlight the 5 files that come up in that window, then select "Extract" and when the window comes up select "Desktop" as the place to put the extracted files.

(5) Open a terminal window (Applications/Accessories/Terminal)

(6) Type:
ndiswrapper -l  (that's a lower case "L") and press enter.

If anything shows in this list, remove it (them????) using:
sudo ndiswrapper -r xxxxxx  (where xxxxxx is the item showing) and press enter

Once the list is blank you can continue

(7) Type:
sudo ndiswrapper -i ~/Desktop/bcmwl5.inf  (that's a lower case "I") and press enter

(8) Type:
sudo depmod -a  and press enter

(9) Type:
sudo modprobe ndiswrapper

(10) Type:
sudo ndiswrapper -m


You should have a network icon on your top bar - it may look like a terminal.  Click on that and see if your wireless network is listed.  If so, click the circle in front of it.  If a network password, etc., is needed, your will get another window.  Enter in your network password and be careful of the default encryption type - mine defaults to 128-bit on the screen but I'm only using 64-bit so I have to change it to 64-bit on that screen.


Post back what happens and/or any problems!:)

---

### Post by jamestang on 2007-12-22
This worked and I was able to get Ubuntu to recognize my wireless card. Thank you so much for this.

I wasn't able to get connected to my wireless network. On the Wireless Network Key Required window, I have the settings as:

Wireless security: WEP 64/128-bit hex
Key: ********
Authentication: Open System

The Login to Network button is grayed-out and I can't continue.

---

### Post by RomeReactor on 2007-12-22
Maybe the driver doesn't support encryption; try temporarily disabling encryption in your router and try to connect without WEP.

---

### Post by jamestang on 2007-12-22
I'm using a 2Wire Wireless Gateway which uses 64-bit Hex WEP.

---

### Post by anewguy on 2007-12-22
I'm also using a 2 Wire wireless gateway - I got it with my ATT/Yahoo DSL.  If you have not changed the defaults for your router/gateway, then try this:

click on the network icon
click on "Connect to another wireless network" (wording may be slightly different)
a window should open up asking 2 things initially:

(1) the Network Name -> this is the SSID and by default on the 2WIRE it should be 2WIRExxx where xxx are the last 3 digits of the serial number.  Remember that "WIRE" must be in upper case.

(2) Wireless Secutiry -> the WEP and by default on the 2WIRE it should be the the 10digit number located under the serial number.  This is a 64-bit hex string, so you should click the arrow down on the window and click on "WEP 64/128-bit Hex".  This will open a couple of more boxes.

(3) Key:  ->This is where you enter the 10 digit WEP code as mentioned above

(4) Show key -> clicking this box allows you to see the key you typed in so you can verify it to the 10-digit code under the serial number

(5) Authentication: -> by default this should be left at "Open System"

When you have completed those things the "Connect" button will become usable.  It knows the network requires a key and grays out the button until you enter something in the key field.

Click "Connect".


Try that and see what happens.  Post back with any questions/problems or just to let us know it worked!:)

---

### Post by jamestang on 2007-12-23
I had changed the network name and key with Windows. I tried to enter those but still had the grayed-out box. I also tried to enter the original 2WIRE743 network name and the original WEP key but it would not connect.

---

### Post by anewguy on 2007-12-23
> **jamestang said:**
> I had changed the network name and key with Windows. I tried to enter those but still had the grayed-out box. I also tried to enter the original 2WIRE743 network name and the original WEP key but it would not connect.

Let's check one other thing:

Click System/Administration/Network on the top bar.

A network setting box should open up.  Does this show a "Wireless connection" that says "Roaming mode enabled"?  If it shows "Wireless connection" but doesn't say "Roaming mode enabled", click once on "Wireless Connection" then click "Properties" and check the box that says "Enable roaming".

When you changed the network name (i.e., SSID) and network key in Windows, did you do anything else such as enable MAC filtering?  Did you hide the network name?  I had prblems similar to yours when I tried to hide the network name (SSID) by not broadcasting it.

Also - you do have the network icon on the top tray, right? (I assume you wouldn't have been able to follow my instructions otherwise but thought I'd ask anyway).

When you click on the network icon on the top tray, what does it show for Wireless Networks that are available?

Seems like I had this problem once, but I've got to try to shake the cobwebs a little to remember what I may have done.  I'll keep thinking on it while waiting for you to post back with the results from this post.:)

---

### Post by anewguy on 2007-12-23
Also, if the above doesn't get you anywhere, try completely turning off all security (WEP, MAC filtering, etc.) at the router and then click the network icon and select "Connect to Other Wireless Network" even if your's is visible in the list.  What we want to do is create a "clean" connection.  It may even just automatically connect to it.

---

### Post by jamestang on 2007-12-23
On the network setting box, it does show a box with Wireless Connection and Roaming Mode is enabled.

I had changed the name and key about a year ago. I don't remember but I really don't think I would have changed anything else besides the name and key.

When I clicked on the network icon, it listed 6 networks available. At the top was a network without a name listed. The next couple networks appear to be my neighbors. There was one other network that was named "Default".

I tried turning off security but still no luck.

---

### Post by anewguy on 2007-12-23
Hmmmmm.... let me think on this for a little while.  I was wondering how your gateway, dns, etc., is set up.  If you go to System/Administration/Network, does it show stuff under the DNS tab?

I know you've already been through this, but please bear with me.  Log in to your router and change the network name (SSID) to something like "MYTEST", be sure encryption is off and MAC filtering is off, save the changes on each menu, reset the router (there's an option on my 2WIRE menu that let's me reset it, or you could cycle power) then check on your Linux laptop and see if "MYTEST" shows in the network list under the networking icon on the top bar.  If so, click on it to connect and copy down everything it says and post it back here.  I know it's a lot of work, but please bear with me.  I seem to remember having a similar problem when I first put in Linux and tried out my wireless, I just can't remember yet what I did (too many "good" bad things when I was younger have messed with my memory :) ).

I'll keep trying to remember........thanks for being patient!

EDIT:  Did your network name appear in the list, or is the one without a name (this would indicate that the SSID broadcast is turned off)?  If it's the one without the name, you have to enter that SSID name (correct case, etc., of course) when you are trying to connect (use the "Connect to Other Wireless Network: option).  This is also the option I had problems with - I wanted my network name private, so I turned off broadcasting of the SSID at the router, but then I wasn't able to connect to it.  I had to go back to broadcasting the SSID and never did figure that one out.  Maybe I should try again and see what happens.

---

### Post by jamestang on 2007-12-23
Good news! I did the above and I was able to connect.

But, I went back and turned my encryption back on. It connected but then I received a window that locked up my computer. The window was titled "Unlock keyring" with a message "Enter password for default keyring to unlock. The application 'nm-applet' (/usr/bin/nm-applet) wants access to the default keyring but it is locked."

---

### Post by anewguy on 2007-12-24
> **jamestang said:**
> Good news! I did the above and I was able to connect.

But, I went back and turned my encryption back on. It connected but then I received a window that locked up my computer. The window was titled "Unlock keyring" with a message "Enter password for default keyring to unlock. The application 'nm-applet' (/usr/bin/nm-applet) wants access to the default keyring but it is locked."

Glad that got around the big problem.  The keyring is where it stores the password key for your network, and is itself protected by a password.  If you haven't read some of the stuff on PAM you may want to.  I think it's included and on it Gutsy, as I don't remember installing it when I went to 7.10.  That keyring file is stored in a file (~/.gnome2/keyrings/login.keyring) which you can delete if you forgot the password, but you can manage it via "System/Administration/Keyring Manager".  So, if you want, you can delete the key there and then it will recreate it the next time it has to reconnect to your network.  It may ask for a password then - if so, just remember that is the password you will need to enter later when it wants to unlock the keyring.  I know for 7.10 (in my case anyway) and if you use PAM in an earlier release, the password to the keyring will be set to your logon password,so it will just automatically unlock the keyring and use the password there to log on to your network.  I hope I've explained that enough.

You could also just try your logon password at the prompt you mentioned above and see if it works.

Let me know what happens.:)

---

### Post by jamestang on 2007-12-24
I created a password with Keyring Manager and the wireless connection works as it should. Thank you so much for taking the time to help me. Not sure I could have done it without you.

---

### Post by anewguy on 2007-12-24
Glad it's all working for you!  It can be an adventure, but you actually learn little things along the way.  Be sure to use the thread tools and marked this as solved so others with the same type of problems may be able to find answers.:)

---

