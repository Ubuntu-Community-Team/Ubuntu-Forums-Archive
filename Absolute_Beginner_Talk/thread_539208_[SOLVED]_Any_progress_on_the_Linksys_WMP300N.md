---
title: "[SOLVED] Any progress on the Linksys WMP300N?"
date: 2007-08-30
forum: Absolute Beginner Talk
---

### Post by Brightbelt on 2007-08-30
I have a Linksys WMP300N Adapter for wireless on my HP tower. I've done much searching and studying    ...and yes, I've tried the 'Bcm4306' Howto and I haven't been able to get it to work.  

That is a long, tedious and very difficult 'Howto'.  I can't figure out how to save certain files that you have to alter in the Howto; there are no save options in the menus nor below in the indexes.  

I'm in a situation now where I can't even get on wired to download whatever lastest Madwifi or Ndiswrapper version might help this out. 

I figure Linux may arrive at the N Adapters eventually?? How long are we looking at before a Deb package comes along that can handle this? Or just in general, before the Linux gurus create a more general, workable solution?

Will Gutsy Gibbons even approach the N Adapters?

Just Curious if anyone has heard anything on this topic,...

Many Thanks, Frank B.

---

### Post by Spr0k3t on 2007-08-31
I have a wireless N card that seems to be very alpha in the madwifi specs.  The chipset is an AR5008 device.  The problem is, the specification is still not locked in stone and the HAL documentation is yet to be finalized.  It's hard to develop for a moving target.  The best thing to do is to keep tabs on the kernel and the wifi developers to see when this happens.  In gutsy, the card shows up, but I still can't do anything with it.

---

### Post by Brightbelt on 2007-08-31
I appreciate your report on things Spr0k3t. It just feels better to know what other folks are experiencing on a common issue.

It sounds like Gutsy is a step in the right direction. This is one of my beefs with Linux though. I know they are in a hard position and it is not necessarily their fault that they don't receive driver-related information from the manufacturers.

But Linux folks will say 'oh but isn't that a real new technology?' - as if that excuses a 9 month to 2 year wait for drivers.  Just because a technology is new, it does not mean that only a few people
have it. Many thousands of folks upgrade their systems in different ways every year.

I'm sorry but if MS and Mac have it, then Linux should have it by that time as well.  It's the only way it's going to happen folks.

BTW, my Linux experimenting and test-driving has dwindled down to one dual boot with Vista on a PC I'm about to sell.  There's just too much frustration because of the amount of things you have to fight for in Linux.

Hardliners might throw out statements that I'm obviously not committed enough to Linux to solve its problems or that I'm not willing to dig in and do the work it takes. I have solved a LOT of hardware issues...I've even configured a scanner by following a Howto on a French Ubuntu Site. 

And it's not just the hardware configuration; it's that plus software advances. IE, doing things more on the newer wave of technology, like onCD Printing. I actually have a driver for onCD printing from Turboprint, but the software interface which they suggest to do it with is lame at best.

If you read my rant, Many Thanks, Frank B.

---

### Post by anewguy on 2007-08-31
I have something for you to try - it may work, it may not.  Since I don't have your hardware I have no way to tell.

(1) Open System/Administration/Synaptic Package Manager

(2) Click "Search"

(3) Enter "ndiswrapper" in the search string and click "find"

(4) Be sure the main ndiswrapper package is marked and that the ndiswrapper-utilities-xxxxxx (don't know what yours will say) is also checked.  If not, click in  the box in front of each and say to mark for installation

(5) On the left-hand side of the screen, click on the "All"

(6) Click "Search"

(7) Enter "network-manager" in the search string and click "find"

(8) Be sure both the main network-manager package and the network-manager-gnome package are checked.  If not, click in the box in front of each and say to mark for installation

(9) If you had to check any of the boxes in steps (4) or (8), click "Apply" and wait for the software to install.

(10) Exit Synaptic Package Manager

Now download the archive attached to this message and extract it to your desktop.  It will create a folder called "wmp300n" on your desktop.

(1) Open a terminal window

(2) Type:

ndiswrapper -l  <--- lower case "L".  For anything that shows in that list, do the following:

-            sudo ndiswrapper -r xxx    where xxx is an item returned above

repeat (2) until nothing shows in the ndiswrapper list

(3) Type:

 sudo ndiswrapper -i ~/Desktop/wmp300n/bcmwl5.inf
  sudo depmod -a
  sudo  modprobe ndiswrapper
  sudo ndiswrapper -m

(4) Type:

 gksudo gedit /etc/modprobe.d/blacklist

This will open an editor window.  Go to the bottom of that list and add the following if they are not already there:

# broadcom default no firmware, using ndiswrapper instead
blacklist bcm43xx

Be sure to press "enter" once or twice after the last line, then save the file, exit the editor, exit the terminal window and restart your PC.

Once your PC is back up and you are logged on, click the network-manager icon on the top bar and see if any wireless networks are listed - if so, your card should be working now and you should be able to connect to a wireless network by clicking the circle in front of the name.  If the network uses WEP or WPA protection, you'll need to specify the key type and the key when you try to connect.

Let me know if this works or not.:)

---

### Post by anewguy on 2007-08-31
Sorry - told it to post before I attached the file.  It's attached to this message.

---

### Post by Brightbelt on 2007-08-31
One Key Question:
Keeping in mind that I have no internet connection, will I still be able to do all that which you specified in the Synaptic Package manager?

Thanks, Frank B.

---

### Post by anewguy on 2007-08-31
Oops - my bad!  Do you have access to a 6.10 LiveCD?  I haven't been able to get anything off the 7.04 CD, but I know if you load up the 6.10 CD while Ubuntu is running, it will say a software volume has been detected do you want to run package manager.  At that point you can say yes and run package manager from that disk - it should find those files.  Short of that, I'm not sure.  Are you able to hardwire to the router to try this?  If not, I'll need to see if there is an offline way of installing those packages.

Sorry about that!  I guess I wasn't thinking about no access.  I'll see what I can find out.:)

---

### Post by anewguy on 2007-08-31
BTW - are you running 7.04?  if so, I think network-manager is installed by default.  Aslo, try the "ndiswrapper -l" command and see if it works (it may return nothing, but as long as it doesn't say unknown command we might be alright).:)

Thanks!:)

---

### Post by anewguy on 2007-08-31
Hey, I did find this link for getting ndiswrapper when you have internet access on another PC but not on the one you want to install it to.  You may want to check this out and see what happens:

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper")

---

### Post by Brightbelt on 2007-08-31
Hey aNewguy, it Worked !!!!!! 
I am writing this through the WMP300N Wireless. You definitely need to post your instructions as a Howto. 

Some of what also helped all this was that I had a backup in my flash drive of the recent Ndiswrapper 1.47 package.  So once I realized I had already installed that earlier today and I knew (like you said via 7.04) that I already had Network manager, I figured it was OK to proceed.

I did find a bcmwl5.inf when I did the ndiswrapper -l.  I had tried an install of it earlier and it didn't go through so obviously it had to be removed. Then everything proceeded as you instructed.

One interesting but strange fact occurred. I have WPA Personal 2 wireless protection and when I was signing onto the wireless network in Network Manager, I was only getting one green light. And it got stuck there and I couldn't get the second green light to light up. 

That had never happened to me before, so I tried restarting. and still just the one green light. And after a while with one green light the passphrase login would always reappear for me to try again.  

Finally I tried choosing WPA Personal INSTEAD of WPA 2 Personal. And then Voila !! It went through. So I have no idea why, but who cares? I'm online!

Many, Many Thanks for your help. I know there are others like me who need this card configured, so you should definitely post this as a Howto.

Again, Many Thanks !!! Frank B.

---

### Post by anewguy on 2007-08-31
Well, like I said, I am far from being any kind of expert - just went off the experiences I had with my own wireless card.  To help everyone who might be searching later and find this post, could you edit your title now to include SOLVED! in front of the title.  I forget exactly how to do that but I think you can only see it if you select "edit" for your 1st post and then there is some option there.  Post back if you need help and I'll see if I can figure that out.

I'm just glad it worked for you!:)

---

### Post by anewguy on 2007-08-31
Hey, I thought of something else you might be interested in.  When you entered your network key, it probably came up and said something about entering a password for the keyring.  The keyring is file where it keeps the network ids and keys for the various encrypted wireless networks you use.  If you enter the same password for it as your log on password, you can install PAM and it will automatically log you on to your wireless network when you start up your PC.  If you didn't enter the same password, you can remove the file via:

rm ~/.gnome2/keyrings/default.keyring

The next time you log on to the network it will want your network key and type, and then prompt for a keyring password again.  Just put in your log on password and PAM should work.  See post #6 in this thread:

[http://ubuntuforums.org/showthread.php?t=192281]("http://ubuntuforums.org/showthread.php?t=192281")

hope that helps you out as well!:)
Dave E.

---

### Post by Brightbelt on 2007-08-31
Thanks anewguy - I needed that reference because I am familiar with the Pam_Keyring thing. I had already set my keyring passphrase to be the same as my login because I knew that would be my next step. 

Many Thanks, Frank B.

---

### Post by Brightbelt on 2007-08-31
There is a Thread Tools menu at the beginning of the thread by which I have marked this thread as 'Solved'.

Again, Many Thanks !!! Frank B.

---

### Post by swarm on 2007-09-07
Thanks for your help, guys!

I am trying to get mine working, and it says the driver is already installed, but I don't have the wireless option in the iwconfig. It says it is not configured. I have tried redoing this twice. Any ideas?

---

### Post by Palerider07 on 2007-09-18
When my Ubuntu was updated, and I restarted, I logged back in to see that my friver didn't work anymore. Any idea on what happened? I followed your instructions and it worked before.

---

### Post by quodlibetor on 2008-01-29
> **Palerider07 said:**
> When my Ubuntu was updated, and I restarted, I logged back in to see that my friver didn't work anymore. Any idea on what happened? I followed your instructions and it worked before.

I'm guessing you didn't add "ndiswrapper" (without the quotes) to /etc/modules to make it so you don't have to "sudo modprobe ndiswrapper" every time you turn on your computer. (Since that wasn't part of the instructions given.)

```
gksudo gedit /etc/modules
```

add "ndiswrapper" (noquotes) to the end of the file and save. 

To make it work before you restart you can obviously: ```
sudo modprobe ndiswrapper
```

This worked for me, anyway.

---

### Post by Jonathan.Simpson on 2008-02-01
Hi. I've been working on installing Ubuntu today and I have a WMP300N. I've followed both of the howto's, verifying everything is correct. I'm actually showing that I am connected.. But, my adapter isn't actually working. Does that make any sense? It shows me connected but the wireless adapter lights aren't on and I can't get any connectivity to the internet. It's rather strange. But, I'm at my wits end here with what to do. Any one have any ideas? Thanks in advance!

---

### Post by dx1919 on 2008-02-21
Im having the same problem except when i do the "ndiswrapper" installtion it is saying that the "bcmwl5.inf" is not a directory.
Any ideas???

---

### Post by GGIII on 2008-03-28
Well, I must say that this guide was great and *mostly* solved my problems. However, when I attempt to actually connect to a network...

1: If it has security enabled, Ubuntu fails to get a network key and asks me again for the network's passcode.
2: If security is disabled, it "connects" fully to the network, but disconnects before it can actually be used.


Any thoughts?

---

### Post by mstuber on 2008-04-07
Thank you.  

This worked for me.   I got nowhere trying to use the ndiswrapper (System -> Administration-> Windows Wireless Drivers) in 8.04 and the bcmwl5.inf file I had extracted from a download directly from the Linksys website ("Invalid Driver").  But entering the sequence you recommended on the command line and the files you had in the attachment worked.

I am using a Dell Inspiron 531 with a dual AMD64 Athlon processor.

Having a network connection definitely improves the usability of Ubuntu hugely.

Thanks!

---

### Post by berman56 on 2008-04-17
I can't tell you how much I appreciate the help.  The wireless now works great.:)

---

### Post by pHreaksYcle on 2008-04-29
Can anyone create a clean cut guide for the WMP300N specifically?
Or **will that previous guide on page 1 work still if I bought that piece now? I noticed that the guide is from a long time ago**, and I am looking to buy this N card. The WMP300N looks good, but I need to know that it will work when I buy it!! Thanks so much for everyones efforts.

---

### Post by berman56 on 2008-05-18
> **pHreaksYcle said:**
> Can anyone create a clean cut guide for the WMP300N specifically?
Or **will that previous guide on page 1 work still if I bought that piece now? I noticed that the guide is from a long time ago**, and I am looking to buy this N card. The WMP300N looks good, but I need to know that it will work when I buy it!! Thanks so much for everyones efforts.

The WMP300N does indeed work using ndiswrapper and the guide in this thread.  With that said, I am sorry to report it has not been fully stable.  I dual boot and windows gives me 80% signal strength and is rock solid.  Unfortunately, in ubuntu 8.04 I get around 40% signal and the connection drops periodically.  Once it drops, I am usually unable to get it working again without restarting.  Does anyone out there have similar trouble?

---

### Post by coleca on 2008-05-19
This advice got my wmp300n up and running in Ubuntu 8.04.  Thanks!

---

### Post by Brainal on 2008-05-25
> **berman56 said:**
> The WMP300N does indeed work using ndiswrapper and the guide in this thread.  With that said, I am sorry to report it has not been fully stable.  I dual boot and windows gives me 80% signal strength and is rock solid.  Unfortunately, in ubuntu 8.04 I get around 40% signal and the connection drops periodically.  Once it drops, I am usually unable to get it working again without restarting.  Does anyone out there have similar trouble?

I'm having the EXACT same problem. I am fortunately able to get it going again without restarting but it's still a pain. I just go into the Windows Wireless Drivers tool thing in System > Administration and then delete the driver, and reinstall it. It only seems to cut out when I'm downloading something or if the device is in heavy use. I'm still trying to dig around finding a permanent way on getting it stable. So far, I haven't gotten too far.

---

### Post by insuusvenerati on 2008-06-19
I have this card with the wmp300n and I think i'm using the x64 version of 8.04 hardy haron. Does it matter if it is x64 or x86?

---

### Post by Patbon on 2008-06-29
I also am having problems actually connecting to the network. Installed fine, am able to select my network from the list, but it won't actually connect me to it, whether I have security or leave it open.  Very strange.

---

