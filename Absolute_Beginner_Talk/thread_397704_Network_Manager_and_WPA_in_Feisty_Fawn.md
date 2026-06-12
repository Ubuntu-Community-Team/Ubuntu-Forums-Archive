---
title: "Network Manager and WPA in Feisty Fawn"
date: 2007-03-31
forum: Absolute Beginner Talk
---

### Post by IsaacJ on 2007-03-31
Hello all.  I've dabbled with Ubuntu before (Edgy and Dapper) but wasn't entirely satisfied at the time.  I'm still pretty noobish, which is why I'm posting it in here.  :) Fawn sounded awesome, and since it sounds like they're almost ready to finish it, I downloaded it yesterday and tried it.

I'm having 3 issues:

1.
Whenever I update my packages, it seems that Network Manager gets broken.  I reinstalled Fawn and the manager breaks every time.  I can still get online with dhclient command, though the Network Manager still says there is no connection with my router.  Anyone else having this problem?  What can I do about it?

2.
I would really like to get WPA working.  I keep getting conflicting info about this one, but it appears that Feisty does come with WPA supplicant because I see it as "upgradable" in Synaptic Package Manager before I download the updages.  But the option to enable it doesn't appear in the Network Manager, only WEP security is available.  Note that it isn't greyed out or anything--it just isn't there at all.  My adapter works right out of the box with both Edgy and Feisty and I don't have to use NDiswrapper or any of that.  It's a Linksys WUSB54G.  The community article I read on WPA said that all you have to do is enable it and add your key in the Network Manager, just as you would with WEP.  WPA works fine in WinXP, BTW.  What am I doing wrong?

3.
Minor annoyance, but sometimes my keyboard keys appear to stick in Ubuntu.  It seems that letters never do it, only numbers and punctuation.  This never happens to me in Windows XP.  Is there a way to stop that?

Thanks a lot for any help.

IsaacJ

---

### Post by IsaacJ on 2007-03-31
Just wanted to add that I was able to check my syslog for anything relating to Network Manager or wpa supplicant.  I see the following errors repeatedly:

Network Manager:
nm_device_802_11_wireless_set_mode (): error setting card wlan0 to Infrastructure mode: Device or resource busy
Mar 31 00:02:51 UMordor kernel: [  421.550013] wlan0: starting scan
Mar 31 00:02:52 UMordor kernel: [  422.295942] wlan0: scan completed
.......

WPA Supplicant:
Mar 31 00:20:59 UMordor NetworkManager: <information>^Iwpa_supplicant(6133): tes of scan results (1 BSSes) 
Mar 31 00:20:59 UMordor NetworkManager: <information>^Iwpa_supplicant(6133): Scan results: 1 
Mar 31 00:20:59 UMordor NetworkManager: <information>^Iwpa_supplicant(6133): RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP]) 
Mar 31 00:20:59 UMordor NetworkManager: <information>^Iwpa_supplicant(6133): Wireless event: cmd=0x8b19 len=8 
.....

Is this of any help?  I'll gladly post everything in this rather large file if requested.  (Assuming there isn't something I should edit out, like a password or something?)


Thanks again.

IsaacJ

---

### Post by DSn0wMan on 2007-03-31
I stumbled on this when I first installed fiesty. In order to configure your WPA just click on the network icon in the taskbar (top right corner of your desktop) select your network, and enter your password. 

You don't actually have to configure it from network manager any more. In fact I am not sure if you ever could configure WPA from network manager.

In anycase just click the network icon it is running something called nm-applet. Use that and not network manager.

---

### Post by IsaacJ on 2007-03-31
I thought the icon in the upper right hand corner was the Network Manager.  If you're referring to the icon that normally tells you when you have made the wireless connection, which is near the upper right hand corner, then that's the one that I'm talking about as well.  It's right next to the icon that lets you know when updates are available.

After getting Feisty's updates, the network icon quit working.  I can not connect now unless I enter the commands in the terminal, but I could connect with it before Ubuntu asked me to get my updates.  It tries to connect at startup, or when I ask it to--but it never succeeds.  It does detect my network and my SSID, however.  Networking only functions through the terminal, and when I connect this way, the network icon still says I'm not connected.

I wasn't able to configure WPA using it either, though the guide I see on networking in feisty (found on this site) shows it there.  The only security option I can see is WEP, which is almost like having no security at all.  This hasn't changed since I got updates.  I have never been able to get WPA going, nor have I even seen an option to turn it on.  It appears to be missing altogether.

I also tried getting JUST the WPA-supplicant update without updating anything else after a fresh reinstall, but that didn't work either.

Is there a terminal command that activates WPA, maybe?  At least I could try that.

IsaacJ

---

### Post by IsaacJ on 2007-03-31
It seems that I'm not the only one having the Network Manager Applet problem with updates.  I guess something is broken in the latest updates for Fawn.  But I haven't found much about WPA.  Anyone have any suggestions for that?

WPA supplicant summary so far:

WPA security is not even offered as an option on my wireless right now.  Only WEP security, yet I see that WPA supplicant is installed.  Ubuntu offered to upgrade it for me, so it must have been there.  Reinstalling Ubuntu changed nothing.

And yes, my adapter does supports it in WinXP.  I am also using Ubuntu's own drivers, not ndiswrapper.  (Wouldn't the option show up even if it didn't support WPA on my adapter?)


IsaacJ

---

### Post by alicemoon on 2007-03-31
isaac I have a similar problem with feisty and thought it might be a driver conflict but what you are saying sounds the same - my wireless usb is detected, it sees the network but just cannot connect - I removed all security but still no luck. I am a complete newby so don't know how to connect via the terminal - can you tell me and I'll see if it gets me on the net

---

### Post by IsaacJ on 2007-03-31
Alicemoon,

I'm able to get online, though the Network Manager Applet is broken after getting updates.  WPA still doesn't work.  

If the Network Manager Applet isn't working (did you try connecting with it yet?) I don't know if these commands will work.  But you can try this command in the terminal:

**sudo iwconfig**

This will tell you the name of your card in Ubuntu.  (It will ask for your password before executing the command)  Mine is rausb0, but that's weird.  :-)  Yours might be wlan0.  Note that **sudo** lets you run the command as root (think Administrator in WinXP).

Then type 

**sudo dhclient** *the-name-of-your-card*

In my case, the command is:

**sudo dhclient rausb0**

Note that Ubuntu calls my card rausb0 (it's a wusb54g Linksys) but it might be something else in yours, like: 

**sudo dhclient wlan0**

In any case, it will take a few seconds for the command to complete.  Once it does, try running Firefox and navigating to any web page.  If it works, you're golden...though you will probably have to enter the command each and every time you boot up.  (There may be another way to do it automatically, like a script or something, but I don't know how yet)  This way, you don't have to set up ndiswrapper.  It works in Edgy as well as Fawn, though I never tried it with my card when I messed with Dapper.

Like me, this isn't enough to get wpa_supplicant working for you.  But getting your network running is key.  Just make sure you have encryption turned off in your router or this won't work.  Worry about encryption later.  And you might want to wait on getting those updates if you haven't already.  I'm finding that others across the board are having the same issue with Fawn after getting updates, where the Network Manager Applet breaks.

I'm a WinXP nerd, but quite new to Linux.  If you need much more help than that, I suggest you create your own thread and get help from people who know more than I do.

IsaacJ

---

### Post by IsaacJ on 2007-03-31
Alicemoon, more for you...

Since I'm not in Ubuntu right now (I'm in WinXP) I couldn't give you an example of what iwconfig  prints out.  But I found another example in the forums which I can post here to help you.

> kolslorr@kolslorr:~$ iwconfig
> lo        no wireless extensions.
> 
> wmaster0  IEEE 802.11g  Frequency:2.447 GHz  
>           RTS thr:off   Fragment thr=2346 B   
>           
> [COLOR="Red"]rausb0[/COLOR]    IEEE 802.11g  ESSID:""  
>           Mode:Managed  Frequency:2.447 GHz  Access Point: 00:13:10:23:49:F7   
>           RTS thr:off   Fragment thr=2346 B   
>           Link Signal level=-217 dBm  Noise level=-199 dBm
>           Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
>           Tx excessive retries:0  Invalid misc:0   Missed beacon:0
>

Bear in mind this isn't my printout, though it is for a similar card.  But whatever your terminal says in place of **rausb0** above is what you want when typing in **dhclient** *name-of-your-adapter*.  I think **wlan0** is a more common name for wireless cards in Ubuntu, so that's more likely what you will type in as the name of your adapter.  

Hope this helps.

Don't suppose anyone has any suggestions for me on WPA yet?  :) 

IsaacJ

---

### Post by alicemoon on 2007-03-31
isaac
thanks for the info - I'll see if it works - I already tried iwconfig and you are right mine is wlan0
I didn't mean to hijack your thread - hope you manage to sort the WPA - 
 Alice

---

### Post by DSn0wMan on 2007-03-31
If nm-applet is not helpfull in configuring WPA you can allways do it the old fashiond way. It involves editing a few files and fiddling with the wpasupplicant command, but it is how I used to do it.

This is the post I used to get it working before. [http://www.ubuntuforums.org/showthread.php?t=263136](http://www.ubuntuforums.org/showthread.php?t=263136)

please not that "wpa_supplicant" is a diferent package then "wpasupplicant"

---

### Post by IsaacJ on 2007-03-31
[I]please not that "wpa_supplicant" is a diferent package then "wpasupplicant"
[/I]

Thanks Dsn0wMan, I hadn't realized that.  So wpa_supplicant really doesn't come with Ubuntu Fawn, and it isn't in Synaptic Manager then, either.  (From what I've seen at any rate)  That could be useful information to me.  That must be why none of the hand edited config file methods have worked for me so far.

I've tried WICD as an alternative because it's supposed to more or less do the same thing as network manager, including WPA support.  But it was just as broken on my system as the regular manager.

Note that I tried the KDE version (KLAN) and it actually asked me for my WPA info!  But I didn't have WPA turned on in my router, so I went back into WinXP and turned it on to test this, but could never get KLAN to connect me again.  It never offered to set up WPA either.  I finally just reinstalled Ubuntu for the 3rd or 4th time.

Also, on this last reinstall, my adapter started showing up as wlan0 instead of rausb0.  Weird.  But it is working just like before so long as I don't get all the updates Ubuntu is asking me to.  When I tried manually editing config files for wpa_supplicant before, rausb0 wasn't on any of them even though it was the name of my adapter in Ubuntu.  Perhaps that will make a difference as well.

Dare to dream...:popcorn: 

IsaacJ

---

### Post by IsaacJ on 2007-04-02
Man, it feels like I've been beating my head against a wall for 4 days now.  I've tried all the guides I can find, but I haven't had much success.  I even tried using Ndiswrapper to see if the Windows drivers would work...but apparently I can't even get the Ubuntu driver blacklisted.  It just keeps on working, even after I enter the commands to blacklist it, so Ndiswrapper seems to fail.  I tried using the graphical took to install the drivers to save me some steps (and possible mistakes) but it never seems to detect my card.  Possibly because the built in drivers won't be blacklisted.  Do they go by a different in Feisty Fawn?

I can't believe this is so hard.  I thought I was on to something after my 5th reinstall of Ubuntu when, after trying all these different guides, I suddenly saw WPA appear as a security option on the network manager applet.  I thought I had done it.  So I went into Windows and reset my router with security enabled.  Then I rebooted into Ubuntu to try it out and I lost my adapter.  It wouldn't even light up.  

After fighting with this for so many hours, I think I might have actually blacklisted both the windows and Ubuntu drivers at some point.  I'm unsure now.  I doubt I could even think straight by that point.  But that may be why the adapter just died.  So I reinstalled Ubuntu again because I didn't know how to undo it (plus I wanted to undo some other things) and now I can't get the WPA option to work as before.  And I can't connect.

I'm clueless.  I'm just running around in circles now and repeating the same things.  If anyone has any ideas, I would really appreciate the help.  Many others have gotten WPA on a WUSB54G v4 Linksys adapter, so it's possible.  

I had such high hopes for Ubuntu, but sooner or later, I'm going to have to give up and start using my computer again. :( Thanks for the help so far, but I really need some new options if I'm going to make Ubuntu work for me.  If anyone knows of anything else to try, please let me know.  Thanks again.

IsaacJ

---

### Post by DSn0wMan on 2007-04-02
It can be difficult if your hardware is not supported. I am lucky to have hardware that is  all supported. 

If I where you I would make a new post in absolute beginner talk with WPA, and your network adapter in the subject. That way you may attract help from someone with the same hardware.

---

### Post by alicemoon on 2007-04-02
Isaac
I have been told that feisty beta has issues with networking which hopefuly will be solved in the stable version - I have now gone back to edgy as I know my wireless can work in this - hope you solve your problems 
Alice

---

### Post by IsaacJ on 2007-04-03
Thanks Alicemoon and DSn0wMan,

I will give Ubuntu a rest for a bit.  I'll surely try again when Feisty Fawn goes final, but I may try again before then.  Waging this little battle has taught me a lot about Ubuntu and Linux, so for that, it was worth something.  I'd love to know how I got the WPA option that one time, though.

If anyone else stumbles across this post, the WPA GUI didn't help me.  WPA Supplicant appeared to be working, but seemed to report that the adapter was already in use(?).  I know the WinXP drivers worked in Edgy for Ndiswrapper, but I couldn't get them going in Feisty.  

Blacklisting the Ubuntu built in drivers didn't seem to "take" somehow, so I couldn't try it with Ndiswrapper either.  The adapter kept right on working even after I blacklisted them.  After several reboots, the adapter suddenly stopped working.  Perhaps the blacklisting suddenly kicked in?  Either that, or WPA Supplicant killed it.  It was right after the WPA security setting became available in the NM-Applet that I lost the adapter on the next reboot.

As with many others, updating the kernel killed the NM-Applet.  I could still get online with **dhclient** command in the terminal, though.  WICD was also broken for me, whether I updated everything or not.  It didn't seem to matter whether I used the stable or beta releases.  Other users are reporting the same issue in the designer's forum.  Maybe the author will have luck getting that sorted out, and then WICD could be an alternative for users like me.  Others may wish to try it any way if they are having issues.  It seems to work for some, but not for others.  Maybe it would work better in Edgy?

Anyway, Ubuntu has been frustrating, but fun.  I think Fawn has a real chance at being the most openly available alternative to Windows for average users.  If they can work these last few kinks out of it, I might even make it my primary operating system.  I have no interest in Vista.  I might consider dual-booting with the next version of Windows, but I think I'll just skip Vista for now.  I don't care to have MS watching everything I do and I like having control over my own machine.  I think Ubuntu Linux can offer me that.  I'll be waiting.

Best of luck,

IsaacJ

---

