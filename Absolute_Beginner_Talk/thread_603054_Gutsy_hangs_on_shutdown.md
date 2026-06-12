---
title: "Gutsy hangs on shutdown"
date: 2007-11-04
forum: Absolute Beginner Talk
---

### Post by caughran on 2007-11-04
One of several reasons for quitting Windows was that it wouldn't shut down smoothly.

Since updating to Gutsy, I've been having a problem with shutdown on Ubuntu. It goes through the graphic screen, then displays a character screen and hangs. The last several lines (the visible part) are:

```
NetworkManager: <WARN> nm_hal_deinit(): libhal shutdown failed - Connection is closed

NetworkManager: <info> Caught terminiation signal                             [sic]

NetworkManager: <debug> [1193452447,463366] nm_print_open_socks(): Open Sockets List:

NetworkManager: <debug> [1193452447,463498] nm_print_open_socks(): Open Sockets List Done.

NetworkManager: <info> Deactivating device eth0.

NetworkManager: <WARN> nm_dbus_init():  nm_debus_init() could not get the system gus. Make sure the message bus daemon is running!

NetworkManager: nm_dbus_signal_state_change: assertion `connection != NULL` failed
NetworkManager: nm_dbus_signal_state_change: assertion `cb_data->data->dbus_connection' failed
NetworkManager: nm_dbus_signal_state_change: assertion `cb_data->data->dbus_connection' failed

```

What went before this -- 2 or 3 screens -- is, of course, off the screen. I took a photo of the screen, so could reproduce it.

---

### Post by theuion on 2007-11-05
Gutsy is hanging for me as well.
```

NetworkManager: <WARN>  nm_hal_deinit(): libhal shutdown failed - connection is closed

NetworkManager: nm_dbus_signal_device_status_change: assertion `cd_data->data->dbus_connection' failed

```

---

### Post by dysphasi on 2007-11-06
Same or at least similar problem here....can anyone provide a workaround?

The only thing is, as long as there's no external display/monitor plugged in when I start up the computer shutdown works no hitch.

As soon as I plug in and start using an external monitor I get this hang at shutdown.

xrandr --output VGA --off will supposedly turn off the external display but doesn't stop the hang.

Is there a way to completely disable external displays when shutting down?

---

### Post by danielsbrewer on 2007-11-09
I'm getting the same behaviour, but only every so often.

---

### Post by dysphasi on 2007-11-09
Unfortunately it seems I'm getting this every now and again even without an external display.....it's getting just a tad annoying and no solution!

---

### Post by Pulka on 2007-11-09
same here. It hangs almost every time i try to shutdown or reeboot. I´ve seen some ways to solve it, but the problem is that forcing the shutdown, for some reason, disconnects my wireless card. So, that´s not an option for me

---

### Post by Derek Djons on 2007-11-09
Allow me to add myself to the list of shutdown / sleep / reboot problems. 
When ever I select shutdown or reboot from the menu my screen turns black but the notebook keeps running. Whether it hangs or still runs I do not know. Also when I select the sleepmode the same problem occurs. 

Hope that they will have this issue fixed soon :D ... I don't think it's that nice for your file structure and what not if it gets hanged and then shutdown by holding the power button for seconds.

---

### Post by xpod on 2007-11-09
One of ours does the same thing.
I dont know if it`s relevant at all but it`s only the P4 desktop that does it and none of the others,which are all Athlon XP`s.

I also have an Elitegroup laptop there with Gutsy just now,it`s never done it either.

---

### Post by maddentim on 2007-11-11
same here...

the system when shutting down starts to display a series of messages from the network manager.  I t does not happen every time and the messages are not always the same ...

---

### Post by Ronin69 on 2007-11-13
Hangs on shutdown when the wireless is connected.  Using rt61 wireless chip with seamonkey driver and rutilt.

If wireless is not connected shutdown works fine.

Tried adding reboot=b to grub -- no luck.  Working on a few other possible solutions, will post if I find success.

---

### Post by SouthernPott on 2007-11-14
Try adding "acpi=force" to your kernel line in /boot/grub/menu.lst while I look for the bug report if it exists. My memory isn't the greatest so I may be mistaken.  From post 14 in the discussion linked below.  There is a bug report that goes back several generations but I have misplaced that.

[http://ubuntuforums.org/showthread.php?t=5193](http://ubuntuforums.org/showthread.php?t=5193)


I found the above from a much earlier discussion and I think it may work for me but I don't know how to add it yet.  In the same discussion they discussed adding apm to the /etc/modules list and apm=power off to the boot kernel.

I am refurbishing an old 500mhz HP desktop  and part of this was to use Ubuntu 7.10.  Most of it is excellent so far including an Airlink wireless card.  The computer starts to shut down then stops and leaves the monitor, CD, and power supply on.   On boot up I get a message something to the effect of:

(0.000000)ACPI:  no DMI BIOS year:  acpi=force is required to enable acpi.

There were several discussions about enabling acpi in the bios but I didn't find it in the bios setup up anywhere. 

Anyway, as a new user, I am having some difficulty understanding EXACTLY how and where to add these things.  Read that as I need specific 1,2,3 directions like double click on "file system", double click on "GRUB", double click on "menu.lst".  Find line "x,y,z" and do the following.  Or open terminal and do the following 1,2,3.

Thanks for any help.

Malcolm

---

### Post by dysphasi on 2007-11-14
Basically, from what I gather, you should be doing as follows:

[1] In a terminal enter: ```
 sudo gedit /etc/modules 
```

[2] At the very bottom of the file opened, add the following line:
```
apm power_off=1
```save and exit.

[3] Back in the terminal, enter ```
 sudo gedit /boot/grub/menu.lst 
```

[4] Maximize the window to better see everything and search for the line: ```
End Default Options
```

[5] Just below this line you will see paragraphs listing: title, root, kernel, initrd to the left side, something like below:
```

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=419086cc-9136-45e9-9369-d7fe44edff76 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic

```
Each of these paragraphs represents one of your login options at the grub boot menu when you power on. It is the first one (the one that you log into ubuntu with) that you'll need to add any options to.

[6] At the end of the line beginning "kernel" add the text:
```
acpi=off apm=power_off
``` 
Using my example above, my paragraph would now appear as follows:
```

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=419086cc-9136-45e9-9369-d7fe44edff76 ro quiet splash [color=red]**acpi=off apm=power_off**[/color]
initrd		/boot/initrd.img-2.6.22-14-generic

```
(nb...this is where you add any of the lines you might find, from the info you found for example, you'd want to add [color=red]**acpi=force**[/color] instead)
Save, exit, power off, restart, log in and try it out.

ps: Doesn't work for me and I've tried all the options I could find! :(
Hope it helps you out!

---

### Post by philinux on 2007-11-14
In the General Help forum there's a stick for known bugs in gutsy

[http://ubuntuforums.org/showthread.php?t=591229](http://ubuntuforums.org/showthread.php?t=591229)

and there a bug report, with some workarounds.


[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/133118](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/133118)

Good luck guys.

---

### Post by SouthernPott on 2007-11-14
Thank you Dysphasi,

I followed your directions and put the "apm power_off=1" at the bottom of the modules file and saved it.

Tried the "acpi=off apm=power_off" at the very end of the kernel line but it did not correct the shutdown problem.

Tried "acpi=force apm=power_off" at the end of the kernel line and IT WORKED!!!  At least once anyway.

EXCELLENT!!  It worked a second time too.

Your instructions were exactly what I needed to see.  Very direct which is perfect for me.  

Again, my sincerest thanks.

Malcolm

---

### Post by dysphasi on 2007-11-14
Glad to help Malcom! Wish it would work for me! ... might try again soon.

A dentist in training you see, I've got plenty of practice instructing people on how to clean their teeth ;)

---

### Post by sports fan Matt on 2007-11-14
That fix worked perfectly...Sorry others are having issues with it...

---

### Post by SouthernPott on 2007-11-15
I have been working on this one for the last few days.   It was a project for the neighbor's two school age boys, ages 10 and 15.  They don't have an internet connection and since I added an access point a couple of months ago, then set up my computer with Ubuntu a couple of weeks ago, thought I would give it a try.  

Their older brother gave them an old HP with Win98 and tons of junk on it but no one knew what to do with it so it was collecting dust in the garage.   Took it apart, cleaned it up a little, replaced the RAM with a couple of old sticks, and added the wireless card which was my only hard expense at about $25.00.  Most importantly cleared out the hard drive and installed Ubuntu.

I finally got everything put back together and set up in their house this evening.  We had to set the box up on a counter next to the desk in the living room to get signal and  it picked it up at about 73% which was fantastic  as that was about all I was getting set up in my house 8 feet from the access point.  The distance now is probably 25 feet.  I was just happy it worked.  More than adequate for internet and email.  

We made a feeble attempt at a new user computer class and I did come prepared with some printouts listing their login info for Ubuntu and the access point plus some basic info about the computer.  We made some toolbar buttons, looked at Ubuntu forums, Google searches, etc.  The older one wanted to know about LimeWire and MySpace, the little one wanted to find the Cartoon Network website.    I gave them the third degree on using the internet responsibly because it was my connection.    Mostly they half listened, farted on each other, and argued over whose turn it was.    Guess we will have to repeat the class in the next few days plus I am going to have to add a printer to it at some time.

I had forgotten what it was like to be that age and I realized just how old I am getting.    My brothers  might still fart on me but they wouldn't tell me about it now.  Just laugh.

Now I need to learn how to use Ubuntu better.  Getting the hang of it and while most of the information and help I am getting from this forum is still way over my head, a little is sinking in.  

Thanks again for the help.  I showed the boys this thread and while they didn't get it, they did understand that there is always help if you ask the right questions.  



Malcolm

---

### Post by dysphasi on 2007-11-15
Lol, sounds like you've got your hands full there malcom with those two little tikes! Good luck!

Ok, back to the hanging problems. Whilst originally I thought I'd got this down to only happening when an external display was attached, then finding it happened even without on occassion. I think I've now got a little further towards confining the cause. 

I've noticed that without anything but power plugged in it all closes fine, but it seems that aside from having an external display, as soon as I have anything plugged into the usb port (excepting basic peripherals like a mouse/keyboard) the problem also recurs.

Is Ubuntu just not capable of shutting everything down properly, preventing a full shutdown? Is there something in the order that it does this that messes things up?

---

### Post by bernieszu on 2007-11-15
Same problem here! I posted the message below to the kubuntu forums - will post back if I get a fix or a workaround


Upgraded to 7.10 with no big problems but can't shut down properly and the fix that worked on earlier versions doesn't work now.
Here's what I'm seeing:
Network Manager: <WARN> nm_signal_handler(): Caught signal 15 shutting down normally
Network Manager: <info> Caught termination signal
Network Manager: <debug> [1195139730.818198] nm_print_open_socks():Open Sockets List
Network Manager: <debug> [1195139730.818382] nm_print_open_socks():Open Sockets List Done
Network Manager: <info> Deactivating device eth0
Network Manager: <WARN> nm_hal_deinit(): libhal shutdown failed - Connection is closed
Network Manager: nm_dbus_signal_device_status_change: assertion 'cb_data_>data->dbus_connection' failed
Network Manager: nm_dbus_signal_device_status_change: assertion 'cb_data_>data->dbus_connection' failed

Any ideas?

---

### Post by bernieszu on 2007-11-24
Ah - dysphasi's solution has worked for me (I was doing it wrong at first - changing the code in the wrong menu)!  Shutting down perfectly now.

---

### Post by Ingo88 on 2007-11-24
Thanks, dysphasi! Your solution saved me :D

I was not far from losing hope before I happened to find this thread :)

---

### Post by justken on 2007-11-24
I have had the same problem (with the message about shutting down the network adapter, blank screen, flashing cursor but everything powered down except the case fans).  I was pretty sure mine was a BIOS issue.

I disabled ACPI in the grub menu (ACPI=off) then disabled powernowd in the services menu before re-enabling ACPI (simply removing the line in the grub menu).  Problem solved.  I then encountered the shutdown problem again, which choked back the cheering a bit.  I tried various of the fixes recommended here before realising that 'ACPI=off' had somehow found its way back into the grub menu.  After editing it out again, shutdown is working properly.

There is a similar thread here [http://ubuntuforums.org/showthread.php?t=603054&highlight=shutdown](http://ubuntuforums.org/showthread.php?t=603054&highlight=shutdown) with a lot of the same ideas but one or two variations.

I have also just flashed my BIOS and will probably try re-enabling the powernowd option to see what happens.  

Regards,

Ken

---

### Post by dysphasi on 2007-11-29
Ok, thought I'd give it another good go. Undeterred by my past failures to bring about a successful, complete shutdown of my laptop I sifted through more websites than I even knew existed (well slight exaggeration), but anyhow, I think I have tried pretty much any option that one can in their grub menu.lst, but no joy.

Has anyone here got a VAIO VGN-C2S properly shutting down with Gutsy 7.10? I'm getting a bit close to the end of my tether.

I also notice that [color=red] _ [this bug report](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/119308)_[/color] only shows a medium priority, how long do such things normally take to get ironed out? Do the ubuntu chaps that work on these bugs never turn of their computers? Because I thought the whole on/off thing was the absolute basis of a fully functioning computer/electronic device, not quite managing the 'off' part seems to be a fairly major flaw. 

Is there some magic that microsoft work that just makes things ...... work? I really like ubuntu, but using a laptop, turning off is something I need to do regularly. 

It's also a pain if, for example, I want to set a shutdown timer if I'm using it to record a show with mythv.

Anyhow, main thing is, anyone with a laptop similar to mine and working, I'd love to hear what you did to make things work. Heck, if you tried *anything* different to the usual acpi=off / force, disabling powernowd and it has worked please let me know.

---

### Post by fatality_uk on 2007-11-29
Hello! Woah, first post!!! Anyway, ditched Windows XP, 2003 and Vista on my various PC's/laptops this week in favour of an ALL Linux world :D. The common install problem thread is that the one's with P4 CPU's, DO hang. AMD CPUs don't seem to have this problem. Has to be connected, don't know quite how but a "fix" of sorts on one of the machines was to enable ACPI management in the BIOS and that curred it, *touch wood*

dysphasi that's my M.D.'s laptop. Seeing as I am head of IT round there, I guess a clean install of 7.10 as a "TEST" might be in order. I'll try and post what I find out. I'll have to restore his copy of vista afterwards of course :)

---

### Post by dysphasi on 2007-11-29
That'd be excellet, thank you!

lol, now I've got all my exams over (and passed...miracles happen!), I was actually going to scrap vista and just use ubuntu / xp with virtualbox, perhaps suggest he does the same ;) 

I tried pretty hard to like vista, but it just started driving me nuts, wireless didn't work very well and can't customize anything at all anywhere in the blooming thing (open with menus locked to one prog/can't even pop a videos folder in my start menu under pictures/games folders there). It's kinda like trying to sit in someone's worn in sofa, it's just great for them, but all lumpy and bumpy for anyone else, m$ don't like the word 'choice' do they?

Anyhow, I digress. I'm a bit lacking in understanding in how powering off works, but why is it that just issuing a halt command, ie "sudo halt stop" will turn off the computer, but powering off in the normal fashion won't? Is there perhaps anything that can be edited to troubleshoot what it is preventing the normal shutdown procedure from completing ?

---

### Post by crjackson on 2007-11-29
Add me (or rather my wife) to the list.  Sony VIAO.  I did disable the splash screen and it shut down fully for the 1st time.  I haven't had much of a chance for further testing.  Has anyone else tried turning off the splash to see what happens?

---

### Post by dysphasi on 2007-11-30
Ok, halt aside etc.. I've played around a lil and it really does just seem to be my usb tv-tuner being plugged in that stops a proper shutdown.

How can I disable the device? If I just unplug it, ubuntu seems to think it's still there. If only I could disable it, I think I could circumvent this whole not shutting down milarky.

---

### Post by fatality_uk on 2007-11-30
Afraid the news is not good :( Same issue on two of the Sony Vaio's we got here. The third works like a charm. Its a vxg somet or other!!! Gonna do a shutdown -v later and try and pickup if anything something that might be hanging

---

### Post by dysphasi on 2007-11-30
:-s not sounding ideal! 

As I said though, mine seems to be shutting down a-ok every time now as long as I've not plugged my usb tuner in. 

If only I knew how to disable the device from the terminal or such like after I've finished using it, I'd be some way towards having a workaround for myself. Any ideas?

---

### Post by mpince on 2007-12-07
I'm encountering this problem, too.   (No VIAO here)

It was working fine for a few weeks, but now when I shutdown I get this series of error msg.

None of the various fixes posted here seem to help. :confused:

Mine seems related to the Ethernet crossover cable that's connected to my roomate's mac.

---

### Post by wardog99 on 2007-12-11
Seems I have fixed mine, having the same thing happening on shutdown.  In my BIOS I changed the ACPI Aware O/S setting from "NO" to "YES".  Also disabled a setting called "Power Management/APM".  And now I haven't had it hang on shutdown for a couple of days.  Not sure which setting did the trick, but I'm happy, so I ain't gonna mess around with it.:)

---

### Post by dysphasi on 2007-12-11
> **wardog99 said:**
> Seems I have fixed mine, having the same thing happening on shutdown.  In my BIOS I changed the ACPI Aware O/S setting from "NO" to "YES".  Also disabled a setting called "Power Management/APM".  And now I haven't had it hang on shutdown for a couple of days.  Not sure which setting did the trick, but I'm happy, so I ain't gonna mess around with it.:)

A similar thing worked on my desktop...had to disable the options for allowing pci and usb devices to wake the computer in the acpi settings menu of the bios.

.... if only I could get this darn laptop to work! .... why is it that VAIOs have no options in their blooming bios? It's sooo frustrating. Still not found a way to properly eject usb devices such as my usb tv tuner in ubuntu either. This is getting a mite frustrating!

---

### Post by koveitan on 2007-12-13
I have a similar problem.
running gusty on IBM thinkpad R50e 
i think that this problem is related to network manger and hal
the errors that are displayed are from network manager / dbus
my wireless card is intel 2200BG (module ipw2200)
tried the solution posted here but it did not help 
anyone have another solution ? 
is there a bug open on this ?
thanks

---

### Post by dysphasi on 2007-12-13
I think the network manager return might be a bit of a misnomer, I gather from reading other posts around the net that whilst an error regarding it is returned, its removal and use of alternative managers removes the error message but doesn't stop the hanging.

There is a bug report [here](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/119308).

---

### Post by cchevy on 2007-12-16
i did it with acpi=force

can somebody tell me what is apm=power_off? what it does?

10x

---

### Post by dmizer on 2008-03-25
> **dysphasi said:**
> Basically, from what I gather, you should be doing as follows:

[1] In a terminal enter: ```
 sudo gedit /etc/modules 
```

[2] At the very bottom of the file opened, add the following line:
```
apm power_off=1
```save and exit.

[3] Back in the terminal, enter ```
 sudo gedit /boot/grub/menu.lst 
```

[4] Maximize the window to better see everything and search for the line: ```
End Default Options
```

[5] Just below this line you will see paragraphs listing: title, root, kernel, initrd to the left side, something like below:
```

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=419086cc-9136-45e9-9369-d7fe44edff76 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic

```
Each of these paragraphs represents one of your login options at the grub boot menu when you power on. It is the first one (the one that you log into ubuntu with) that you'll need to add any options to.

[6] At the end of the line beginning "kernel" add the text:
```
acpi=off apm=power_off
``` 
Using my example above, my paragraph would now appear as follows:
```

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=419086cc-9136-45e9-9369-d7fe44edff76 ro quiet splash [color=red]**acpi=off apm=power_off**[/color]
initrd		/boot/initrd.img-2.6.22-14-generic

```
(nb...this is where you add any of the lines you might find, from the info you found for example, you'd want to add [color=red]**acpi=force**[/color] instead)
Save, exit, power off, restart, log in and try it out.

ps: Doesn't work for me and I've tried all the options I could find! :(
Hope it helps you out!

thanks a ton, that's the ticket.

---

### Post by schettj on 2008-03-26
> **dysphasi said:**
> Basically, from what I gather, you should be doing as follows:

[1] In a terminal enter: ```
 sudo gedit /etc/modules 
```

[2] At the very bottom of the file opened, add the following line:
```
apm power_off=1
```save and exit.


That alone was sufficient for me when my hp/comaq 8510w decided to stop shutting down. It seems an ugly hack (forcing it to use amp to shut down instead of acpi) but it works...

---

### Post by davegod75 on 2008-03-26
having this same problem.  There is not even a wireless card in my system.

The hack is nice but will we see a fix?

---

### Post by dmizer on 2008-03-27
> **davegod75 said:**
> having this same problem.  There is not even a wireless card in my system.

The hack is nice but will we see a fix?

this is not really a hack.  for machines with older bios versions and using acpi, it's necessary to force apm in place of acpi.  this is a simple matter of bios being too old to handle a modern kernel.

---

### Post by eel on 2008-04-12
Oh dear...

I tried dysphasies step-by-step and now i can't boot properly. 
I get stuck with something called BusyBox and an exotic sounding (initramfs)
Which reminds me that i should really back up once in a while. The only reason that i don't back up is because i have no idea how to but i always felt sort of stupid for that so i never asked. But since the dysphasie the dentist seems someone who can really explain stuff.... :)

---

### Post by eel on 2008-04-12
BOOYAH!!!

tricked hardy in to letting me in again to undo the changes i made (:

---

### Post by Mahyar on 2008-04-20
I don't know if this is relevant, but I was having the same troubles with shutting down in Hardy, and had tried everything on these forums to no avail.

I simply removed the last programme I had installed (Keytouch) and now it's back to normal.

---

### Post by JCM3000 on 2008-05-06
I was having these problems, along with lsusb hanging.  Seems Hardy doesn't like my Belkin bluetooth dongle, no probs once that's taken out.  Gutsy was fine with it though!

---

### Post by steppen wolf on 2008-05-08
Hi dysphasi, thank you so much for the step-by-step instructions. I am using Xubuntu Hardy Heron, had the same problem, and they worked just fine with me with a few modifications (started on 3, and used mousapad instead of gedit).

Thanks!

---

### Post by neslot on 2008-05-21
Having the same problem here on my desktop, Dell T3400.  Seems that it only hangs up if I have let the screensaver, and/or power management do it's thing.  If I stay active, it shuts down normally.  am trying the things listed above, and acpi=forced didn't do it..  trying "=off" now.  
My son has 2 dells like mine, one at home and one at work.  His work one is running in 32 bit and was upgraded from gutsy to hardy.  His home one is running 64 bit, but was upgraded from gutsy to hardy.  Mine is 64 bit and running a fresh install of hardy..  Don't know if this matters to anyone, but a bit more info none the less.. Mine is the only one of the 3 that does this..
later..
T


Neslot

That didn't work either..  sigh..I might just have to fresh install, 'cause it didn't do it at first..

---

### Post by steppen wolf on 2008-05-21
Hi neslot,

try this out. It worked for me. Just a reminder: this is for Xubuntu Hardy Heron. So if you are using Ubuntu, you will need to use a different text editor, not Mousepad. Refer to the directions given by dysphasi for the first couple of steps. I hope this helps you solve your problem.

> **steppen wolf said:**
> 

I found a way to do this - I am posting it just in case somebody has the same problem. I'd like to thank user [dysphasi]("http://ubuntuforums.org/showthread.php?t=603054&highlight=ACPI+BIOS&page=2"), as my solution is based on the indications provided in his/her reply. And thanks  for your help bill.

Here is what you do if you are running Xubuntu Hardy Heron:

1) Go to the terminal (Applications/System) and enter this line of code:

 **sudo mousepad /boot/grub/menu.lst**

2) Now a Mousepad file will open. Scroll down all the way till you see 

**End Default Options**

3) Find the paragraph where it says something like:

[B]Ubuntu 7.10, kernel 2.6.22-14-generic
(hd0,0)
/boot/vmlinuz-2.6.22-14-generic root=UUID=419086cc-9136-45e9-9369-d7fe44edff76 ro quiet splash
/boot/initrd.img-2.6.22-14-generic

[/B]
4) See where it says "splash"? Enter a space, then write (on the same line):

**[COLOR=red][B]acpi=force apm=power_off**[/COLOR][/B]

5) Save the document, exit, restart the computer, log in again and try to shut down. It might just work.

---

### Post by neslot on 2008-05-21
OK, got it back.  Somewhere along the line, a redhat strain of the kernel got on my machine..  dunno how..  I prolly screwed something up pretty good to do it.  My menu had this:  kernel  /boot/vmlinuz-2.6.24-16-rt and also the generic kernel..  kernel  /boot/vmlinuz-2.6.24-16-generic  I ended up doing an apt-get remove linux-rt and an 
apt-get install linux-generic.  editing needed to be done to the grub menu and cleanup of other files.  My son did that by shelling in and cleaning up my mess.:)
Thanks steppen!.

---

### Post by Ski-lleR on 2008-05-25
Hi there

A people on french forum experience this problem, or a similar. Watch the screenshot:
[IMG]http://uploads.imagup.com/03/1209810848_IMGP2598.JPG[/IMG]

I translated the workaround in french for help him, with no success. He also tried "force", and the change in the bios, nothing more.

When he goes in gdm 2.20.5, the problem disapear.

Anyone can help ?

Thanks

Note: For now he have frozen in 2.20.5, because no bug, but it's not a long time solution

---

### Post by dmizer on 2008-05-25
Ski-lleR, just disable NetworkManager according to these directions:
[https://help.ubuntu.com/community/WifiDocs/NetworkManager?#head-1de145d05f957ff659f5fdb58974ec3e5864def5](https://help.ubuntu.com/community/WifiDocs/NetworkManager?#head-1de145d05f957ff659f5fdb58974ec3e5864def5)

---

### Post by alejaaandro on 2008-05-25
i got the same problem out of the blue: i had left my computer on while i went down to grab a bite, only to come back and find out it had rebooted... probaly a short power failure or something (hopefully!!)... so, the next time i tried to shut it down it just wouldn't...

anyway, the trick in the "login window" preferences worked like a charm... 

thnx guys...

---

### Post by steppen wolf on 2008-05-26
Hey Ski-lleR,

that should not be a problem with shutdown. In fact, I see the same screen at shutdown, but as long as you add this line of code as exaplined in my post above, you should manage to shut down regardless of the issue with the Network Manager. Here is the line:

Code:
acpi=force apm=power_off

dmizer, thank you for the suggestion, I will try it out myself.

---

