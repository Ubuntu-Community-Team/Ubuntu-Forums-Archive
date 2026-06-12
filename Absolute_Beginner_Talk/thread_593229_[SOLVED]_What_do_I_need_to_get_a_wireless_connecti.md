---
title: "[SOLVED] What do I need to get a wireless connection?"
date: 2007-10-27
forum: Absolute Beginner Talk
---

### Post by voteforpedro36 on 2007-10-27
I posted this in the networking & wireless forum, but I'm afraid that I got confused and scared there, and thought I may get more help here.

Anyway, I have a wired connection to a PC running XP. I also have a laptop with Ubuntu/Mandriva, and would like to get wireless on it through a USB wifi adapter, since I don't want to mess with the router that I currently have working. My ethernet card is a Broadcom 4306, although that number doesn't mean anything to me, maybe it will help.

I'd like to be able to get something at a local CircuitCity or Radioshack, so does anyone have any idea of what I should get?

---

### Post by SpiritIsReality on 2007-10-27
howdy
should be able to find a workable usb here
[http://www.google.ca/search?hl=en&q=site%3Ahelp.ubuntu.com%2Fcommunity%2FWifiDocs+usb+wireless&btnG=Search&meta=](http://www.google.ca/search?hl=en&q=site%3Ahelp.ubuntu.com%2Fcommunity%2FWifiDocs+usb+wireless&btnG=Search&meta=)
hope it helps
trails

edit:
I saw noob12 refer to using this, broadcom the easy way
[http://ubuntuforums.org/showthread.php?t=405990](http://ubuntuforums.org/showthread.php?t=405990)

the rest of the ways
[https://help.ubuntu.com/community/WifiDocs](https://help.ubuntu.com/community/WifiDocs)

---

### Post by Halfling Rogue on 2007-10-27
Haven't used USB wifi adapters, just wireless cards, but maybe you can find something [here]("https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported#head-603c9481d6c6288b6b674cc50132d21f6d539c53")?

---

### Post by Threbus5 on 2007-10-27
Hi,

The USB WiFi would seem a little too "interesting" to me.
Why not swap the wired eth0 card with a wireless card? The cost for a WiFi USB and real wireless card are about identical. 

If you really enjoy experimenting the first response to your post should prove useful.

Take care.

---

### Post by voteforpedro36 on 2007-10-27
What exactly is a wireless card? If you tell me that, and how it works, I'll be interested.

---

### Post by mdpalow on 2007-10-27
I think you're saying that you want wireless on your laptop, which has broadcom hardware on/in it, right?

Ubuntu 7.10 now has drivers for broadcom in it. I've never been able to get a Linux OS to work on my laptop because it didn't see my Broadcom hardware. With Ubuntu 7.10 my wireless light came on immediately after install and I was connected to the Internet once I entered my password.

What version of Ubuntu are you using? I would bet that if you are using 7.04 or below your wireless isn't working, but if you upgrade it will.

If bottom line is you will use USB Wireless adapter or Wireless card, you can get either at Walmart for $50 or less. However, you still have to enter your password once it finds your signal assuming you've secured your router.

Also, my first instinct would probably be to go with the USB adapter because my gut tells me the card might have driver issues. I would think the USB would work much more easily if you get a name brand one.

If it were me, I would update to 7.10 first and if I already had it and my wireless wasn't working, I would get the USB adapter.

good luck,

---

### Post by H3retic on 2007-10-27
I've been using this airlink 101 with ubuntu 7.10, and was pleasantly surprised when it "just worked".  It was detected, isntalled automatically, and I just had to select my wireless network.  I recommend it strongly, if you can find one.

[http://www.airlink101.com/products/awll3026.html](http://www.airlink101.com/products/awll3026.html)

---

### Post by voteforpedro36 on 2007-10-27
What if I got a Linksys wireless router? Would it, my Broadcom hardware, and Ubuntu 7.10 work together?

And also, I have a Mandriva partition. Anyone know if it will work with it?

---

### Post by mdpalow on 2007-10-27
Edit:

******** SEE MY LAST RESPONSE ON PAGE TWO OF TWO ************

******************************************************************

******************************************************************

---

### Post by voteforpedro36 on 2007-10-27
> **mdpalow said:**
> The router type doesn't really matter. I have had a couple and currently use a Linksys. The important thing is will Ubuntu 7.10 see your Broadcom wireless stuff. It does in mine and 7.10 added a lot of stuff just for Broadcom, so I think you have a VERY good chance that your computer will work once you install 7.10. 7.04 won't work directly after an install with Broadcom; 7.10 will work with no configuration needed.

That's good to know.
> Just remember, install 7.10 with the CAT5 cable plugged in your laptop. After the install take the cable out and click "wireless network connection" (two monitors icon in taskbar) and change the setting to wireless. Enter your password if you created one (you should) and let it connect.

I already have 7.10 set up, is this going to be a problem?

> By the way, you don't have to load any cd software with the router if you get a new one and it comes with a disk. It works when you turn it on and you can access it from your browser. See you book/pamphlet for the IP address you have to enter into your browser to connect to the admin section.

Ok... this part confuses me. I hook the router to the modem (although I have a router [not wireless] that already plugged in, I suppose there are 2 ports). Now what? Turn it on? After that, I'll need the IP address (from the book that comes with the router, you say?) for what? Will Ubuntu automatically detect it's there, or will I have to enter the IP in from somewhere inside the OS?
ll going to pretty much have the same interface, so you'll be alright with whatever you get.

> 
Good luck,

P.S. Why do you have Mandriva? Can't tell you anything about that as I only use Ubuntu 7.10.

Thanks. And I installed Mandriva so I could see the difference between different Linux distros, and kept it since it has Amarok (stupid reason, I know, but I like it better especially since I didn't have to manually install it and the KDE libraries that I would have had to in Ubuntu, without internet access).

I will 3/4 times be back tomorrow for more questions, that is if I do pick it up then.

Oh, I forgot to say: I went and looked at routers today, and this guy told me loads of stuff, suggested that I get the router, but it went on sale ($10 US off) tomorrow, whereas a different brand was on sale today :).

---

### Post by mdpalow on 2007-10-27
ok, so you already have 7.10 installed. Does your laptop have a light to show you that the wireless Hardware (H/W) is on and working? Mine has a little button in the very front with a light next to it. I can push the button to turn wireless on/off.

If you have a light then you're good to go and just need the wireless router. If you don't have a light then we need to figure out if 7.10 has recognized your wireless h/w.

When you get the router you will have 4 ports in the back for CAT 5 wired connections and an Internet port to plug your MODEM into. Take a CAT 5 cable and go from MODEM to Internet port in back of router and then plug in router power supply.

If you want to run a CAT 5 cable from laptop to router that's fine too if you want to log into admin section. Once plugged in, bring up your browser and put this in the address bar:

192.168.1.1

A window will pop-up asking for userid/password. This is how you configure your router. Skip the User and put "admin" in for the password and you're in. Later you'll want to change this password in the configuration.

When you're in, click on WIRELESS and change your WIRELESS NETWORK MODE to MIXED

Change your WIRELESS NETWORK NAME by typing in "Home" or your name, or something you will recognize (remember, this name can be seen by others), 

Change your SSID to channel 3 (better than default)

Click on SAVE SETTINGS


Then, under WIRELESS tab you'll see WIRELESS SECURITY

Here you'll add a password for the signal being transmitted and received. Don't recommend you change this at first, but wait until you're done setting up a connection and know it's working.

When ready:

 Change SECURITY MODE to WEP

KEY is = 1

WEP ENCRYPTION = 128 bits 64 HEX digits

Type or Enter 26 numbers that you can remember. I used a pin number with 2 zeros in front of it and typed that in 4 times and then added 99 at the end. So, let's say you have a pin number that is 1234. You could put 001234 in 4 times and then end it with 99 and that would give you 26 numbers. Get it? :)

SAVE SETTINGS and you're done.

Now click on WIRELESS NETWORK CONNECTION in task bar (two monitors icon) and select and select the name you put in. If you don't see one - then click on CONNECT TO OTHER WIRELESS NETWORK.

Enter your Network name
Security = WEP 64/128-bit Hex
Key = your password (26 numbers you entered)
Authentication = Open System

and click CONNECT

If your laptop wireless is working, it should get the signal and connect.

If no joy, power down MODEM, ROUTER, and laptop. Then....

Power up MODEM - wait 15 seconds or until you see the cable light steady.
Then power up Router and wait 15 seconds.
Then power up laptop again.

Should work... If not, you'll never connect to the Internet.

Just kidding.... ;)

If not, the first thing I'd want to know is if my laptop wireless was working. I can always tell 'cause I have a light that comes on if the drivers loaded and it's working. If you have a light on you're close as I said, but if not than you will have to do some driver configuring or get that USB wireless adapter for a quick fix.

Hope this helps.. will check in tomorrow to see if you've posted anything....

Good luck,

---

### Post by voteforpedro36 on 2007-10-28
Well, here's the funny part. I got this computer second-hand from my aunt. She gave it to me because her internet wasn't working. I just figured it was the Ethernet port... but the light that used to be on before her internet stopped working doesn't come on anymore. The wireless router works though, as far as I know that is.

So now I need a USB wireless adapter or a PCI adapter thing, I suppose. That's what the guy at RadioShack told me ($50 more on this). Will a Linksys one work w/Ubuntu?

---

### Post by mdpalow on 2007-10-28
Just because the light didn't come on with her doesn't mean it's broke. If she didn't have the drivers loaded, the light wouldn't come on. The same goes for you.

Anyway, get the USB adapter and you should be fine. I think if you get a Linksys you'll be ok. However, I believe someone already wrote you a post in this thread telling you which one he got at Walmart and he confirms it works.

One last thing... When you installed 7.10, did you allow it to install restricted drivers at the very end? Check by clicking SYSTEM -> ADMINISTRATION -> RESTRICTED DRIVERS MANAGER

See if there is anything NOT CHECKED. If so, you might not have allowed Ubuntu to intall the driver(s) for your Broadcom wireless hardware. If anything is unchecked, go ahead and check it and reboot.

Ok, if everything above fails and you want to take the easy road, go ahead and get your USB adapter.

Good Luck,

---

### Post by voteforpedro36 on 2007-10-28
You were right, this is my fault. The driver wasn't enabled, but when I try to enable it it says:

"The software source for the package bcm43xx-fwcutter is not enabled"

I bet this has something to do with sources.lst... I went to System->Preferences->Software Sources and checked them all, but still same thing. Any hints?

EDIT: I also found a .deb of it for Fiesty at [http://packages.ubuntu.com/feisty/utils/bcm43xx-fwcutter]("http://packages.ubuntu.com/feisty/utils/bcm43xx-fwcutter"), but, it is for Fiesty.

I also found something else to help, but it said I n.eed a wired connection, which I obviously don't have (weird that I need internet to install internet, eh?)

---

### Post by mdpalow on 2007-10-28
I'm hoping I remember this right, but you probably do have Internet with a CAT5 cable plugged into your laptop. What you don't have is Broadcom WIRELESS, but I think if you plug a cable into your laptop, you'll connect.

Switch your Wired Network Connection back to Wired if you put it on wireless and reboot your machine. Bring up Firefox and see if it connects. If so, try enabling that restricted driver again. Also do that sources thing you were talking about again and see if you can get to it with a cable.

I think you're really close to getting the wireless to work. If it detected you don't have the driver running/installed then it's at least recognizing it, which is the biggest hurdle.

Good luck,

BTW - "The software source for the package bcm43xx-fwcutter is not enabled."  I think that might have been because you didn't have your CAT5 cable plugged into your laptop. When installing 7.10, you should always have a CAT 5 Ethernet cable plugged into your desktop/laptop.

P.P.S. Next time you do an install, NEVER discount your computer when it's telling you it wants to install DRIVERS. When a computer sees something and wants to install drivers; that's a very good thing. ;)

---

### Post by voteforpedro36 on 2007-10-28
Ok, since my last post (I figured I had to be fairly close), I decided to try what you suggested: Plug in the internet. I never thought this worked, but alas, it did. I updated the system, the repos, and finally downloaded the driver. I installed it, and unconnected.

Now I got to the wireless part. At first, it didn't work. But I remembered that when I installed the new router, I had to unplug the modem for 10 seconds and plug in back in a minute later for the PC to regain access to the internet. I got a connection then and there.

So then I run into an ungoing problem I noticed, well, yesterday. All the while after I installed Gutsy Gibbon, Firefox never worked. I ran from the terminal /lib/firefox/firefox, but still nothing. It just doesn't open. Luckily there was an update... but it still didn't open. Me, however being a smart one, went to Add/Remove and installed Opera. I am now posting wirelessly on Ubuntu 7.10!


Finally, thanks for all your help. I don't know how I would have gotten through it without the help. I will search a bit more for the bit on Firefox, but I like Opera better (if it goes as fast... which the Windows version never seemed to do).

Thanks again.

---

### Post by mdpalow on 2007-10-28
Alright! Congratulation...

And to think, I've only been using Linux/Ubuntu now for 10 days and was able to help you. You, by the way, are my FIRST "Solved" member, so be sure to update your thread as such.

I'm trying to think why your Firefox wouldn't work, which is weird, but I'm also confused by what you said in your last post.

Did you do a fresh install of Ubuntu 7.10? If you didn't, I would do it all over again using 7.10 from the get go with no upgrade. Also, I would like to know how you have your Hard Drive (HD) partitioned. The reason I ask is because I've learned that partitioning correctly from the start is the best way to go. Since I'm thinking you don't have a lot installed on your computer right now, it would be VERY easy to just start over from scratch and have everything running like it should.

If you did start over, you could be up and running again in ~20 minutes. I did a fresh install on my laptop and it took 18 1/2 minutes to be up and running again and it's an older laptop. It would be worth your time to do this especially if you're not partitioned right and if you upgraded to 7.10 from 7.04.

I'm also thinking a fresh install would solve your Firefox problem for sure.

If you want to do it, let me know and I'll send you instructions for the beginning when it asks you how you want to partition your HD.

Lastly, open a terminal window and type " firefox " in it without the quotes and hit the Enter/Return key. Let me know if it comes up. You shouldn't have to type the path etc. to get it to come up.

I'll keep an eye out for you if you reply tonight...

Edit:

LOL... I JUST noticed - you DID put SOLVED already. How funny. Well good deal. Glad I was able to help and save you some money.

---

### Post by voteforpedro36 on 2007-10-28
No, I was going to do an upgrade from Fiesty, but after hearing that it wasn't the best idea, and wanting to try Mandriva out, I went for a clean install. You don't want me to do another fresh install, do you? I have quite a bit of music on the Mandriva partition...

Running 'firefox' doesn't do diddly squat. No errors, no "Firefox is starting", nothing. It's weird. I googled it (ended up installing a driver though), and someone said to type in the path. I don't know how to even make it spit up errors, but I will read the man page later (Opera is better IMO, at least if it's as fast). 

Oh, as for the partitions:

```
   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1        1337    10739421   83  Linux
/dev/hda2            4583        4864     2265165    5  Extended
/dev/hda3   *        1338        4582    26065462+  83  Linux
/dev/hda5            4724        4864     1132551   82  Linux swap / Solaris
/dev/hda6            4583        4723     1132519+  82  Linux swap / Solaris

```

Oh hold on a sec. Am I reading that that says /dev/hda3 (Ubuntu, I'm guessing by the star), is larger? This means I may move my music collection. Lol I was thinking Ubuntu was on a smaller partition.


I can't believe only 10 days. I've been using it since the beginning/middle of August, but still don't know which way is left! (Well, when it comes to wireless and partitioning/installing... the rest I've got down I believe)

---

### Post by mdpalow on 2007-10-28
I can't remember what you told me before about the reason you had Mandriva, but if it were me, I would copy the music to a cd for backup and then ditch the Mandriva now that you know you have an internet connection.

You can then load it back later. :)

You have a lot of partitions, which really are that necessary.

I would do a MANUAL partition when asked and consider it this way:

/               EXT3 file type and make this about 10 gigs (REALLY doesn't need to be more)
/home      EXT3 file type (use remaining space for this MINUS say... 7 gigs)
/Windows  Fat32 file type (use 5 gigs for this from the 7 gigs above you saved)
/swap       Don't think there is a file type for this one (use the remaining 2 gigs for this)

I'm a little torn on the /Windows partition because you should have it if you're running dual boot and want to have both OS's able to write to a partition, which they can both read, BUT if you don't have Window$ do you still need it for Wine applications?? I say go for it anyways since in the long run it's the safer bet and it's only 5 gigs.

Also, when you put the /Windows partition it doesn't let you select /Windows on the first go around. Just create it and then select it again and then for file type click the drop down menu and then it'll finally show up as a selection you can make.

Also, if you have your music and important stuff backed-up - after you create the partition click on the little box you'll see in the FORMAT column and you'll see it update with a check mark, which means it's going to format that drive now as well. No check mark, no format. You want to format.

Last point here.... make sure you delete all the partitions you see when you enter this section. That way, when you put them back in, they will all be in numerical order as you create them (ie. hda1, hda2, hda3).

The first time you do this, take your time looking at everything and get it just like you want. You can always go back and change it, but then you have to start over. I actually took about 30 minutes my first time 'cause I was brand new to this OS and didn't really understand how it worked since I was never big into partitioning with Window$. Now, I can zip through this screen in about a minute.

At the end when it asks you about the restricted drivers... ENABLE THEM! ;)

Remember to have your cable plugged into the lap top from the beginning so it can access the Internet to download whatever it needs. 20 minutes later when it's done, reboot after the drivers part, take the updates it wants to install, unplug the CAT5 cable, switch from wired network to wireless, click on Firefox, and browse the Internet! ;)

And finally, don't forget to put the secure password (WEP Key) on your router to secure it... AND don't forget to CHANGE your admin password in Linksys or someone like me who knows Linksys default password is "admin" could log into your router and change your settings without you knowing it.

I'm sending you a Private Message as well, so check your control panel.

Good luck,

---

