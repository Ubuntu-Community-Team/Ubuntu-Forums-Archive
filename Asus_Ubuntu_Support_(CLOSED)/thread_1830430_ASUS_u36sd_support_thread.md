---
title: "ASUS u36sd support thread"
date: 2011-08-21
forum: Asus Ubuntu Support (CLOSED)
---

### Post by nwadams on 2011-08-21
Link to the wiki for u36sd 
[https://help.ubuntu.com/community/Asus_U36SD](https://help.ubuntu.com/community/Asus_U36SD)

So it turns out that I had a usb 3.0 problem with mine so I do not know when or even if I will be getting a u36sd with ubuntu. 

**Works out of the box**
Audio
Audio out port
Internal microphone
Mic port
HDMI port
Video (without desktop effects)
USB
Wireless Networking
WiFi switch (Fn+F2)
VGA port
Card reader
Brightness control (Fn+F5/F6)
LCD on/off switch (Fn+F8)
Multitouch touchpad (two finger scrolling, activate via System Settings)
Intel Turbo Boost (to test, run turbostat from the package acpidump)

**Does not work out of the box**
Desktop effects
Nvidia card
Volume control (Fn+F10/F11/F12)
Multimedia controls (Fn+Up/Down/Left/Right)
Suspend
Bluetooth

**Helpful Tips and Tweaks**
Unity 3D and Nvidia graphics support: Do NOT, I repeat, do NOT install the Nvidia graphics drivers. It will not work. 
Options:
1. use [this]("http://ubuntuforums.org/showpost.php?p=10557451&postcount=5") to disable the nvidia gpu and just use the intel gpu.
2. Install bumblebee/Ironhide for dual graphics support.

How to fix webcam orientation. Follow the instructions [here]("https://help.ubuntu.com/community/Asus_U36JC") to fix webcam orientation.

**Frequently Asked Questions**
Will the Nvidia Graphics drivers work? No they will not. Nvidia is not supporting Optimus in Linux so the official Nvidia drivers will not work with this laptop. Do NOT install them, it will only create problems. The only way to make use of the Nvidia graphics card in Linux is to use Bumblebee/Ironhide otherwise you are stuck using the Intel hd3000 that is integrated with the cpu.

If anyone has a u36sd already please post what works/what doesn't work and any extra configuration/tweaks you had to do to get things to work properly. I will add your advice and instructions to this main post so we can make a comprehensive guide for other owners. 

**Thanks to:**
Martin Juhl - Bumblebee/Ironhide ([http://www.martin-juhl.dk/](http://www.martin-juhl.dk/))

---

### Post by adrien214 on 2011-08-22
Hello, 
I just installed 11.04_desktop_amd64 fresh on my U36SD after wiping clean the harddrive and merging all partitions with gparted live.

The first problem that appeared was that the hardware was not sufficient for running unity. This issue has to do with the dual intel onboard/nvidia graphics. I just discovered [bumblebee]("https://github.com/Bumblebee-Project/Bumblebee/blob/master/README") and [Nouveau]("http://ubuntuforums.org/showthread.php?t=1046504") and am going to look into this later. The best thing to do to have the thing running with intel is to disable unity upon logon (ubuntu-standard option) or install unity 2D (sudo apt-get install unity-2d).


EDIT : not all Fn keys shortcuts work (yet);)

---

### Post by popsch on 2011-08-22
I also plan on getting that ASUS notebook. Have you tried these drivers?

[http://www.nvidia.com/object/linux-display-amd64-275.21-driver.html](http://www.nvidia.com/object/linux-display-amd64-275.21-driver.html)

---

### Post by nwadams on 2011-08-22
> **popsch said:**
> I also plan on getting that ASUS notebook. Have you tried these drivers?

[http://www.nvidia.com/object/linux-display-amd64-275.21-driver.html](http://www.nvidia.com/object/linux-display-amd64-275.21-driver.html)

That won't work. The u36sd has nvidia optimus which nvidia is not supporting. You will need to use the intel drivers and acpi_call to disable the nvidia gpu OR use some form of bumblebee.

---

### Post by popsch on 2011-08-22
Does Nvidia have a good track history of building Linux drivers? It's pity otherwise, because the Asus looks really good.

---

### Post by adrien214 on 2011-08-23
now bumblebee has forked to [Ironhide ]("https://launchpad.net/~mj-casalogic/+archive/ironhide/")as well...

---

### Post by arneanka on 2011-08-24
I've recently ordered a u36sd but havnt recieved it yet. Looking at this thread I get kind of suspicious though... isnt the u36sd just the u36jc but with the sandy bridge processor? I manage to see no other difference in terms of hardware... So wouldnt one of all the guide for u36jc ubuntu work on the u36sd?

Thanks in advance!

---

### Post by adrien214 on 2011-08-24
it would [indeed ]("http://ubuntuforums.org/showthread.php?t=1705406"):) thanks for pointing it out ! I'll try [the setup guide for 10.10]("https://help.ubuntu.com/community/Asus_U36JC") as well, some issues might have similar solution.

and just a quote from the setup guide :

> 
Lima November
[QUOTE]
Boot splash

As usual with Intel cards, Plymouth boot splash will show too late in the boot process. If you want it to appear earlier, type this in a console window:

sudo echo FRAMEBUFFER=y > /etc/initramfs-tools/conf.d/splash
sudo update-initramfs -u

You might get a little bit slower boot, but it will look much consistent (IMHO). [/QUOTE]

---

### Post by arneanka on 2011-08-24
> **adrien214 said:**
> it would [indeed ]("http://ubuntuforums.org/showthread.php?t=1705406"):) thanks for pointing it out ! I'll try [the setup guide for 10.10]("https://help.ubuntu.com/community/Asus_U36JC") as well, some issues might have similar solution.

and just a quote from the setup guide :

Thats awesome! I was so scared that the u36sd wouldnt work while the u36jc would that I almost cancelled my order to get the u36jc instead, thats how much I want ubuntu! 

Please keep us posted in how things are working out for you both with 11.04 and 10.10.  Myself I havnt, from the looks of it, grown too attracted to unity but it would be interesting to know if it works on the u36 with the nvidia gpu disabled. Somebody told me compiz works that way, so I guess unity should too right? Or do we have to use 2d unity? I heard that that one had a horrible graphic for the workspaces. 

Gosh, I really cant stand the wait for my u36sd :D

---

### Post by nwadams on 2011-08-24
> **arneanka said:**
> Thats awesome! I was so scared that the u36sd wouldnt work while the u36jc would that I almost cancelled my order to get the u36jc instead, thats how much I want ubuntu! 

Please keep us posted in how things are working out for you both with 11.04 and 10.10.  Myself I havnt, from the looks of it, grown too attracted to unity but it would be interesting to know if it works on the u36 with the nvidia gpu disabled. Somebody told me compiz works that way, so I guess unity should too right? Or do we have to use 2d unity? I heard that that one had a horrible graphic for the workspaces. 

Gosh, I really cant stand the wait for my u36sd :D

With the new bumblebee/ironhide we are going to be able to take advantage of the dual graphics as well instead of just disabling the nvidia card. So that will be different from the u36jc instructions (bumblebee/ironhide didn't exist then)

But I created this thread in case asus threw a curveball at us with the new model. I suspect the instructions will end up being very similar though.

---

### Post by arneanka on 2011-08-24
> **nwadams said:**
> With the new bumblebee/ironhide we are going to be able to take advantage of the dual graphics as well instead of just disabling the nvidia card. So that will be different from the u36jc instructions (bumblebee/ironhide didn't exist then)

But I created this thread in case asus threw a curveball at us with the new model. I suspect the instructions will end up being very similar though.

Taking advantage of the dual graphics just seems like a dream. But does the fn-key really not work? I thought they did in u36jc, is there any known difference between the models in this aspect?

---

### Post by adrien214 on 2011-08-24
the fn key thingy should be updated in the first post as I haven't had the time to fix this on mine (i discovered the u36jc setup guide just today) and used another fix for it.

also dual graphics im not too sure about it yet, i installed ironhide and i think i messed up the config when choosing the output screen so i had to remove it and it messed up the whole system to point of non-return (e.g. fresh install).

---

### Post by arneanka on 2011-08-24
> **adrien214 said:**
> the fn key thingy should be updated in the first post as I haven't had the time to fix this on mine (i discovered the u36jc setup guide just today) and used another fix for it.

also dual graphics im not too sure about it yet, i installed ironhide and i think i messed up the config when choosing the output screen so i had to remove it and it messed up the whole system to point of non-return (e.g. fresh install).

I kind of feel like I could survive without dual graphics too as long as stuff doesnt look horrible (will just dual boot in W7 for games, which I hardly ever play).

But how does things work out? Compiz? Does the Unity Wokrplace manager run smoothly?

Greatly thankful for your time and answers!

---

### Post by adrien214 on 2011-08-24
I've sadly only managed to run my machine with failsafe graphics until now so I dont know if the intel HD onboard can manage compiz. Gotta install or unity-3d unity-2d (sudo apt-get install unity-2d and then select unity-2d in login window options).

Also if you plan on disabling the nvidia, please read the setup guide above as well as[this page]("http://ubuntuforums.org/showpost.php?p=10557451&postcount=5").

but I have to say that I find unity deeply repulsive, I need a normal desktop and compiz is a waste of time ^__^ I mean, glitters are for windows because the inside is hiding the ugly and rusty carcasse of 3.1, but I disgress.

---

### Post by olof_ on 2011-08-24
hello out there! Im so glad I found this thread, and its only some hours old:) 

On my first install I was able to get the real Unity (Unity 3d) to work (I do love it...) but then I tried to install the latest nvidia drivers from the [nvidia website ]("http://www.nvidia.co.uk/object/linux-display-ia32-280.13-driver-uk.html") and gdm/x died on me. 

After a ubuntu reinstall (solving problems the easy way...) unity 3d does not work anymore. 

When installing ubuntu for the first time I first started Windows 7 and there selected the nvidia 520m (performance mode) and then rebooted and installed ubuntu. Then Unity 3d worked. the second time I first had ubuntu without any GUI and then formatted the drive and reinstalled. then unity 3d did not work.

I confirm that the fn keys does not work, and in skype the video is upside down. But the multitouch seems to work though:)

---

### Post by arneanka on 2011-08-24
> **olof_ said:**
> hello out there! Im so glad I found this thread, and its only some hours old:) 

On my first install I was able to get the real Unity (Unity 3d) to work (I do love it...) but then I tried to install the latest nvidia drivers from the [nvidia website ]("http://www.nvidia.co.uk/object/linux-display-ia32-280.13-driver-uk.html") and gdm/x died on me. 

After a ubuntu reinstall (solving problems the easy way...) unity 3d does not work anymore. 

When installing ubuntu for the first time I first started Windows 7 and there selected the nvidia 520m (performance mode) and then rebooted and installed ubuntu. Then Unity 3d worked. the second time I first had ubuntu without any GUI and then formatted the drive and reinstalled. then unity 3d did not work.

I confirm that the fn keys does not work, and in skype the video is upside down. But the multitouch seems to work though:)


Well what is ubuntu without a little fidgeting? Haha... Well Im glad FN-keys are working.

There are ways to get the webcam to work for the U36JC, and also a guide on how you turn of the nvidia graphics (dont run these drivers!!) - did you check it out? Hopefully it will make things easier for you. 

Link
[http://ubuntuforums.org/showthread.php?t=1705406](http://ubuntuforums.org/showthread.php?t=1705406)

---

### Post by olof_ on 2011-08-24
> **nwadams said:**
> 
**Does not work out of the box**
Fn shortcut keys - adrien214


there are several fn-keys and quite alot of them are actually working.

[SIZE="2"]Working[/SIZE]
[LIST]
[*]&#8220;ZZ&#8221; Icon (F1): Places the Notebook PC in suspend mode.
[*]Radio Tower (F2): Toggles theinternal wireless LAN on.
[*]Sun Down Icon (F5): Decreases the display brightness.
[*]Sun Up Icon (F6): Increases the display brightness.
[*]LCD Icon (F7): Toggles the display panel on and off.
[*]LCD/Monitor Icons (F8): Toggles between the Notebook PC&#8217;s LCD display and an external monitor.
[*]Num Lk (Ins): Toggles the numeric keypad on and off.
[*]Scr Lk (Del): > **AbtZ said:**
> Scroll Lock works. At least it shows up in when running "xev" -- none of the other non-working keys do.
[/LIST]


[SIZE="2"]Not Working[/SIZE]
[LIST]
[*]Crossed-out Touchpad (F9)
[*]Crossed Speaker Icons (F10)
[*]Speaker Down Icon (F11)
[*]Speaker Up Icon (F12)
[*]Stop (Up Arrow)
[*]Play/Pause (Down Arrow)
[*]Next (Right Arrow)
[*]Previous (Left Arrow)
[/LIST]

observe that this is with an out of the box setup. Ubuntu 11.04, x86.

---

### Post by olof_ on 2011-08-24
> **arneanka said:**
> 
There are ways to get the webcam to work for the U36JC
[http://ubuntuforums.org/showthread.php?t=1705406](http://ubuntuforums.org/showthread.php?t=1705406)

Well, not anymore...

> **chaltain said:**
> Everything went fine until I got to the command "sudo apt-get install gtk-v4l". When I run this command, I get the message "Unable to locate package gtk-v4l". Note that I added the repository OK and that I was able to install libv4l-0.

the same happens for me, there is no package named gtk-v4l in that ppa anymore.

---

### Post by adrien214 on 2011-08-25
> **olof_ said:**
> 
When installing ubuntu for the first time I first started Windows 7 and there selected the nvidia 520m (performance mode) and then rebooted and installed ubuntu. Then Unity 3d worked. the second time I first had ubuntu without any GUI and then formatted the drive and reinstalled. then unity 3d did not work.

this is really really interesting, it means there's a bios switch available, just have to find it I guess.

anyway, follow updates for bumblebee [on twitter]("https://twitter.com/#!/Team_Bumblebee"). latest release yesterday.

---

### Post by jadahl on 2011-08-26
Anyone bought the one with an SSD drive (I think usually a 160GB one) instead of the magnetic disk hard drive? In that case, what manufacturer and model is it? I've been trying to find this out, but seems almost like some kind of secret, which makes me reluctant to buying.

---

### Post by nwadams on 2011-08-26
> **jadahl said:**
> Anyone bought the one with an SSD drive (I think usually a 160GB one) instead of the magnetic disk hard drive? In that case, what manufacturer and model is it? I've been trying to find this out, but seems almost like some kind of secret, which makes me reluctant to buying.

ask the retailer thats selling it

---

### Post by jadahl on 2011-08-26
I asked the web shop staff of two different shops. They didn't know. I asked them to ask their supplier, and they replied they probably don't know either. I made a technical inquiry to the ASUS support, and they just said ask the retailer. Something funny with that SSD drive!

---

### Post by nwadams on 2011-08-26
> **jadahl said:**
> I asked the web shop staff of two different shops. They didn't know. I asked them to ask their supplier, and they replied they probably don't know either. I made a technical inquiry to the ASUS support, and they just said ask the retailer. Something funny with that SSD drive!

don't buy it with the ssd then.

---

### Post by jadahl on 2011-08-26
> **nwadams said:**
> don't buy it with the ssd then.
That doesn't help me in getting a new laptop with an SSD drive. (No, putting one there myself is not an option since it will void the warranty).

---

### Post by nwadams on 2011-08-26
> **jadahl said:**
> That doesn't help me in getting a new laptop with an SSD drive. (No, putting one there myself is not an option since it will void the warranty).

apparently replacing the ssd doesn't void the warranty. But i'd confirm that with asus

---

### Post by jadahl on 2011-08-26
> **nwadams said:**
> apparently replacing the ssd doesn't void the warranty. But i'd confirm that with asus

That's exactly what I did, and the reply was that it indeed does void warranty. Since it's a slim model, the storage device is placed in a quite inconvenient place. It's one of those "detach the whole upper part including keyboard and what not" procedures.

---

### Post by nwadams on 2011-08-26
> **jadahl said:**
> That's exactly what I did, and the reply was that it indeed does void warranty. Since it's a slim model, the storage device is placed in a quite inconvenient place. It's one of those "detach the whole upper part including keyboard and what not" procedures.

Hmm, shitty. From what I have read about replacing the u36sd hard drive and the u36jc hard drive is that you will probably have to put the original back in for warranty work but there is no warranty is void stickers or anything that you have to tear.

My dell on the other hand has removing the CD tray as a warranty sanctioned replacement. It involves taking the screen off and the keyboard off. But dell made nice instructions for it and its actually really easy. Its just a some dis-assembly required project.

---

### Post by jadahl on 2011-08-26
> **nwadams said:**
> Hmm, shitty. From what I have read about replacing the u36sd hard drive and the u36jc hard drive is that you will probably have to put the original back in for warranty work but there is no warranty is void stickers or anything that you have to tear.
...
So the warranty is voided if you change the storage device, except there is no way of telling if I put back the original one after it broke?

Anyway, what the staff of the webshop and the ASUS support person said, I cannot change the storage device.

---

### Post by condefenring on 2011-08-26
I have the following issues with my u33jc.

1) i only can see a GPU with LSPCI . I can change BIOS value to jump from nvidia to intel card without problem but visibility with both cards is impossible. I guess this is the reason bumblebee project does not work for me.
Thats normal. It is needed a bios update in order to make work bumblebee.????
2) HDMI output does not work with Intel card. If i change bios to boot up with  nvidia (nouveau driver)  then output works but HDMI sound output does not work. Some know a workaround for this problem????.

                      Thanks in advance.

---

### Post by another_sam on 2011-08-27
I'm also interested in having HDMI output. With any one of the cards.

---

### Post by olof_ on 2011-08-29
> **condefenring said:**
> I have the following issues with my u33jc.


Not to be rude or anything, but I think this thread is called "ASUS u36sd support thread" for a reason... It is because just this thread is about just ASUS u36sd. 

Try starting one for just your model, or search to see if anyone else already done it.

---

### Post by olof_ on 2011-08-29
> **another_sam said:**
> I'm also interested in having HDMI output. With any one of the cards.

I will buy a hdmi/dvi cable in this week, but for now I can only confirm that with bumblebee installed the vga connector works like a charm using both the intel and the nvidia gpu.

---

### Post by olof_ on 2011-08-29
Also, talking about things that work. 

Hardware that works out-of-the-box:

tested:
[LIST]
[*]Microphone jack
[*]Headphone jack 
[*]VGA port (as I mentioned in my previous post) 
[*]USB 2.0 ports 
[*]Ethernet port 
[*]Memory card reader (tested only with SD-card)
[*]Wireless connection
[*]Built-in microphone
[*]Built-in speakers
[/LIST]

not tested (yet):
[LIST]
[*]HDMI 
[*]USB 3.0 port
[/LIST]

---

### Post by arneanka on 2011-08-29
> **olof_ said:**
> Also, talking about things that work. 

Connectors that works out-of-the-box:

tested:
[LIST]
[*]Microphone jack
[*]Headphone jack
[*]VGA port (as I mentioned in my previous post)
[*]USB 2.0 ports
[*]Ethernet port
[*]Memory card reader (tested only with SD-card)
[/LIST]

not tested (yet):
[LIST]
[*]HDMI
[*]USB 3.0 port
[/LIST]



Got my ASUS u36sd today, charging it at the moment, can't wait to get started!  Thanks alot for your opdates in this thread olof!

---

### Post by arneanka on 2011-08-30
Has anybody come up with a fix for the fn-keys yet? Many of them seem to work but I cant get the volume ones to do! 

Also, am I supposed to install the nvidia restricted drivers and then bumblee, or just bumblee straight away?

Thank you! :)

---

### Post by ms.shams on 2011-08-30
Guys,

I'm planning to buy this model of ASUS, because of its special advantages.
I'm a web designer and i use ubuntu primarily.
please tell me about problems, are problems Annoying the user?
are you hoping for fixing problems in the new version of ubuntu? :icon_frown:

---

### Post by AbtZ on 2011-08-30
> **olof_ said:**
> there are several fn-keys and quite alot of them are actually working.

[SIZE="2"]Working[/SIZE]
[LIST]
[*]“ZZ” Icon (F1): Places the Notebook PC in suspend mode.
[*]Radio Tower (F2): Toggles theinternal wireless LAN on.
[*]Sun Down Icon (F5): Decreases the display brightness.
[*]Sun Up Icon (F6): Increases the display brightness.
[*]LCD Icon (F7): Toggles the display panel on and off.
[*]LCD/Monitor Icons (F8): Toggles between the Notebook PC’s LCD display and an external monitor.
[*]Num Lk (Ins): Toggles the numeric keypad on and off.
[/LIST]


[SIZE="2"]Not Working[/SIZE]
[LIST]
[*]Crossed-out Touchpad (F9)
[*]Crossed Speaker Icons (F10)
[*]Speaker Down Icon (F11)
[*]Speaker Up Icon (F12)
[*]Stop (Up Arrow)
[*]Play/Pause (Down Arrow)
[*]Next (Right Arrow)
[*]Previous (Left Arrow)
[/LIST]

[SIZE="2"]Not Tested (yet)[/SIZE]
[LIST]
[*]Scr Lk (Del)
[/LIST]

observe that this is with an out of the box setup. Ubuntu 11.04, x86.
Scroll Lock works. At least it shows up in when running "xev" -- none of the other non-working keys do. 

Doesn't anyone know how to fix them, or how to start at least? 'Twould be nice to get at least the volume keys to work.

---

### Post by olof_ on 2011-08-30
> **ms.shams said:**
> Guys,

I'm planning to buy this model of ASUS, because of its special advantages.
I'm a web designer and i use ubuntu primarily.
please tell me about problems, are problems Annoying the user?
are you hoping for fixing problems in the new version of ubuntu? :icon_frown:

My biggest issues atm are:
[LIST=1]
[*]That the fn-key for disabling the touchpad does not work
[*]And that the media fn-keys does not work.
[*]Also that the web camera is upside down
[/LIST]

for more details, see my previous posts: [here for example](http://ubuntuforums.org/showpost.php?p=11183644&postcount=17). I also recommend you to read through the whole thread.

---

### Post by olof_ on 2011-08-30
> **arneanka said:**
> 
Also, am I supposed to install the nvidia restricted drivers and then bumblee, or just bumblee straight away?

Thank you! :)

First, read [this](https://launchpad.net/~bumblebee).

then add this ppa: [Stable Bumblebee releases](https://launchpad.net/~bumblebee/+archive/stable)

```
sudo apt-add-repository ppa:bumblebee/stable
```
```
sudo apt-get update
```
```
sudo apt-get install bumblebee
```

then, restart. 

to switch between the internal gpu and the nvidia gpu:
```

sudo apt-get install git

```

```

git clone [email]git@github.com:mkottman/acpi_call.git[/email]
cd acpi_call
make
sudo insmod acpi_call.ko

```

I do not know if the following steps are really neccesary actually, but just to be shure:

then first make a script executable:
```

chmod +x ./test_off.sh

```
Now run this script:
```

./test_off.sh

```


to turn off the discrete graphics card:
```
echo '\_SB.PCI0.PEG0.GFX0.DOFF' > /proc/acpi/call
```

to turn it back on:
```
echo '\_SB.PCI0.PEG0.GFX0.DON' > /proc/acpi/call
```

I got this information from the following place: [a linux-hybrid-graphics.blogspot.com post](http://linux-hybrid-graphics.blogspot.com/2010/07/using-acpicall-module-to-switch-onoff.html)

---

### Post by FirstByté on 2011-08-31
> **arneanka said:**
> Has anybody come up with a fix for the fn-keys yet? Many of them seem to work but I cant get the volume ones to do! 

Also, am I supposed to install the nvidia restricted drivers and then bumblee, or just bumblee straight away?

Thank you! :)

[This]("http://ubuntuforums.org/showpost.php?p=10997488&postcount=9") should fix the fn-key issues

```

git clone git://git.iksaif.net/acpi4asus-dkms.git
cd acpi4asus-dkms
make
sudo make install
sudo modprobe asus-nb-wmi

```

Though I have a diff. hardware (Asus U41S), the post has helped to get the ALL the fn-keys working even right up to 'xev'

Good luck

Follow Olf_'s instruction about Bumblebee.

---

### Post by ms.shams on 2011-08-31
thank you for your replies :)
So as I realized, this laptop has two graphic card, and ubuntu can't switch between them itself.
But this problem has been solved by Bumblebee. right?

---

### Post by jadahl on 2011-08-31
I created and started writing [https://help.ubuntu.com/community/Asus_U36SD](https://help.ubuntu.com/community/Asus_U36SD) . I only added parts that I have managed to test and fix so far, and since I got it yesterday, I haven't had time for much yet. Feel free to help out.

---

### Post by AbtZ on 2011-08-31
Does suspend to ram work for you guys? For me it just goes to a blank, black screen and the only way to get out of it is to do a hard reset with the power key.

I am using Bumblebee/Ironhide as opposed to pure Bumblebee, though I'm not sure it would make a difference.

---

### Post by jadahl on 2011-08-31
> **AbtZ said:**
> Does suspend to ram work for you guys? For me it just goes to a blank, black screen and the only way to get out of it is to do a hard reset with the power key.

I am using Bumblebee/Ironhide as opposed to pure Bumblebee, though I'm not sure it would make a difference.

Have you tried to follow the steps on [https://help.ubuntu.com/community/Asus_U36JC](https://help.ubuntu.com/community/Asus_U36JC) ? I haven't confirmed that it works, but could be worth a try.

---

### Post by AbtZ on 2011-08-31
I just tried it and I can confirm that suspend works after following the guide -- sweet! :) I would also recommend people do the hard drive power management fix, unless they want their drive to die all-to-soon.

Now, if only I could fix the "jumpy" behaviour of two-finger scrolling I would be all set.

---

### Post by olof_ on 2011-08-31
> **AbtZ said:**
> I am using Bumblebee/Ironhide as opposed to pure Bumblebee, though I'm not sure it would make a difference.


[QUOTE=Samsagax]
This will be "Bumblebee" developed for stability in the first place, with a new organization and support for as many distros as we can. We have rolled back all unstable features and made an all-way configurable installer (or we tried at least ;) ).

"Ironhide" is MrMEEE's new project, forked from the former and outdated/bugged MrMEEE/bumblebee repo. There are tons of forks for that repository and that's one of the reasons it became unstable. MrMEEE itself explains that situation and why he came up with his new project (best wishes btw :) )

[/QUOTE]

taken from "What is the difference between MrMEEE/bumblebee, Bumblebee-Project/Bumblebee and ironhide?", [issue #52](https://github.com/Bumblebee-Project/Bumblebee/issues/52) on github.

---

### Post by olof_ on 2011-08-31
> **FirstByté said:**
> [This]("http://ubuntuforums.org/showpost.php?p=10997488&postcount=9") should fix the fn-key issues

```

git clone git://git.iksaif.net/acpi4asus-dkms.git
cd acpi4asus-dkms
make
sudo make install
sudo modprobe asus-nb-wmi

```


Well, it does actualy fix almost every key, exept the "disable the touchpad" (fn+f9) key.

thank you!

---

### Post by olof_ on 2011-08-31
> **ms.shams said:**
> thank you for your replies :)
So as I realized, this laptop has two graphic card, and ubuntu can't switch between them itself.
But this problem has been solved by Bumblebee. right?

Close to. See my [previous post.](http://ubuntuforums.org/showpost.php?p=11203583&postcount=39)

---

### Post by jadahl on 2011-08-31
> **AbtZ said:**
> I just tried it and I can confirm that suspend works after following the guide -- sweet! :) I would also recommend people do the hard drive power management fix, unless they want their drive to die all-to-soon.

Now, if only I could fix the "jumpy" behaviour of two-finger scrolling I would be all set.

Did you use the exact same script as on the U36JC wiki page, or did you change it some how?

Because, it seems to not to do the trick on my U36SD. Instead of never suspending, mine suspends, but fails to resume. Instead it boots up the regular way after I try to wake it up by pressing space or enter.

I noticed that the third bus serial number 07:00.0 probably has changed to 04:00.0 on U36SD (I compared lspci -v outputs and the USB 3 bus sits on 04:00.0 on U36SD and 07:00.0 on U36JC).

However, changing the BUSES3 variable doesn't solve the problem.

Did you tweak anything else, for example the asus-wmi kernel module (fn-keys) or the nvidia on/off tweaks?

---

### Post by _karo on 2011-08-31
I can confirm that the HDMI output works out of the box on 11.04, with the default Intel drivers. I have bumblebee installed, but haven't used it yet. I've tried the HDMI out with my LCD TV and 22" LCD monitor, and the image is fine. Haven't tried whether I could also get sound through the HDMI output.

However, I haven't been able to disable the Nvidia card yet. None of the methods presented in [here]("http://linux-hybrid-graphics.blogspot.com/") work - I get an error message "Permission denied (publickey)." when trying to install acpi_call or asus-switcheroo. [The commands suggested by olof_]("http://ubuntuforums.org/showpost.php?p=11203583&postcount=39") result in the error message "bash: /proc/acpi/call: No such file or directory".

So has anyone actually managed to switch the Nvidia card off, and see a difference in battery life? If yes, how?

---

### Post by AbtZ on 2011-08-31
OK, I have added the Fn-key and Suspend fixes to the wiki.

---

### Post by AbtZ on 2011-08-31
> **jadahl said:**
> Did you use the exact same script as on the U36JC wiki page, or did you change it some how?

Because, it seems to not to do the trick on my U36SD. Instead of never suspending, mine suspends, but fails to resume. Instead it boots up the regular way after I try to wake it up by pressing space or enter.

I noticed that the third bus serial number 07:00.0 probably has changed to 04:00.0 on U36SD (I compared lspci -v outputs and the USB 3 bus sits on 04:00.0 on U36SD and 07:00.0 on U36JC).

However, changing the BUSES3 variable doesn't solve the problem.

Did you tweak anything else, for example the asus-wmi kernel module (fn-keys) or the nvidia on/off tweaks?

The only modification I made was to change the file name to "20_custom-asus-u36sd". Not sure whether that would have any effect however.

Before gettings suspend to work I installed a bunch of other packages as well -- laptop-mode-tools, pm-utils etc etc. Not sure if they helped somehow.

---

### Post by jadahl on 2011-08-31
> **AbtZ said:**
> The only modification I made was to change the file name to "20_custom-asus-u36sd". Not sure whether that would have any effect however.

Before gettings suspend to work I installed a bunch of other packages as well -- laptop-mode-tools, pm-utils etc etc. Not sure if they helped somehow.

If you run "grep 0000:07:00.1 /var/log/pm-suspend.log" does it give you any messages such as "No such device"? If not, could you attach a file containing the output of the command "lspci -v"?

---

### Post by AbtZ on 2011-08-31
That grep command returned nothing.

I assume it's the nvidia part you want?

lspci -v:
```
01:00.0 VGA compatible controller: nVidia Corporation Device 1050 (rev a1) (prog-if 00 [VGA controller])
	Subsystem: ASUSTeK Computer Inc. Device 1682
	Flags: fast devsel, IRQ 16
	Memory at db000000 (32-bit, non-prefetchable) [size=16M]
	Memory at c0000000 (64-bit, prefetchable) [size=256M]
	Memory at d0000000 (64-bit, prefetchable) [size=32M]
	I/O ports at d000 [size=128]
	Expansion ROM at dc000000 [disabled] [size=512K]
	Capabilities: [60] Power Management version 3
	Capabilities: [68] MSI: Enable- Count=1/1 Maskable- 64bit+
	Capabilities: [78] Express Endpoint, MSI 00
	Capabilities: [b4] Vendor Specific Information: Len=14 <?>
	Capabilities: [100] Virtual Channel
	Capabilities: [128] Power Budgeting <?>
	Capabilities: [600] Vendor Specific Information: ID=0001 Rev=1 Len=024 <?>
	Kernel modules: nvidia-current, nouveau, nvidiafb



```

---

### Post by olof_ on 2011-08-31
Yeah!
the webcamera issue is solved:

```
sudo add-apt-repository ppa:libv4l

```

```

sudo apt-get update

```

```

sudo apt-get install libv4l-0

```

```

sudo gedit /etc/environment

```

and add "LIBV4LCONTROL_FLAGS=3" to the end.

mine looks like this now:

PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games"
LIBV4LCONTROL_FLAGS=3

then reboot, and then cheese will work ok.

but to get skype to work:

if you are on a x86 system as I am, start skype through terminal with the following command: ```
LD_PRELOAD=/usr/lib/i386-linux-gnu/libv4l/v4l1compat.so skype
```

---

### Post by jadahl on 2011-08-31
> **AbtZ said:**
> That grep command returned nothing.

lspci -v:
...


Interesting. This differs from mine. Yours doesn't contain any USB 3.0 Host Controller.

```

04:00.0 USB Controller: Fresco Logic FL1000G USB 3.0 Host Controller (rev 04) (prog-if 30 [XHCI])
        Subsystem: ASUSTeK Computer Inc. Device 1039
        Physical Slot: 3
        Flags: bus master, fast devsel, latency 0, IRQ 48
        Memory at dd200000 (32-bit, non-prefetchable) [size=64K]
        Capabilities: [50] Power Management version 3
        Capabilities: [68] MSI: Enable+ Count=1/1 Maskable- 64bit+
        Capabilities: [80] Express Endpoint, MSI 00
        Kernel driver in use: xhci_hcd
        Kernel modules: xhci-hcd

```

---

### Post by olof_ on 2011-08-31
> **_karo said:**
> However, I haven't been able to disable the Nvidia card yet. None of the methods presented in [here]("http://linux-hybrid-graphics.blogspot.com/") work - I get an error message "Permission denied (publickey)." when trying to install acpi_call or asus-switcheroo. [The commands suggested by olof_]("http://ubuntuforums.org/showpost.php?p=11203583&postcount=39") result in the error message "bash: /proc/acpi/call: No such file or directory".

So has anyone actually managed to switch the Nvidia card off, and see a difference in battery life? If yes, how?

sorry, I missed some parts when I wrote how to do it.


> 
to switch between the internal gpu and the nvidia gpu:
```

sudo apt-get install git

```

```

git clone [email]git@github.com:mkottman/acpi_call.git[/email]
cd acpi_call
make
sudo insmod acpi_call.ko

```

I do not know if the following steps are really neccesary actually, but just to be shure:

then first make a script executable:
```

chmod +x ./test_off.sh

```
Now run this script:
```

./test_off.sh

```


to turn off the discrete graphics card:
```
echo '\_SB.PCI0.PEG0.GFX0.DOFF' > /proc/acpi/call
```

to turn it back on:
```
echo '\_SB.PCI0.PEG0.GFX0.DON' > /proc/acpi/call
```

I got this information from the following place: [a linux-hybrid-graphics.blogspot.com post](http://linux-hybrid-graphics.blogspot.com/2010/07/using-acpicall-module-to-switch-onoff.html)


i have updated the [post]("http://ubuntuforums.org/showpost.php?p=11203583&postcount=39") now. I solved the "Permission denied" by just doing a ```
sudo ls
``` before, as the authorization is saved a while.

---

### Post by jadahl on 2011-08-31
> **AbtZ said:**
> That grep command returned nothing.

I assume it's the nvidia part you want?


Actually what the suspend/resume script does is unbind/bind the USB buses before suspending and after resuming. Does your laptop have a USB 3.0 port? On your original attachment I could see no USB 3.0 controller, which might be the reason suspend works for you but not for me.

The command "ls -l /sys/bus/usb/devices/usb*" gives me
```

lrwxrwxrwx 1 root root 0 2011-08-31 23:54 /sys/bus/usb/devices/usb1 -> ../../../devices/pci0000:00/0000:00:1a.0/usb1
lrwxrwxrwx 1 root root 0 2011-08-31 23:54 /sys/bus/usb/devices/usb2 -> ../../../devices/pci0000:00/0000:00:1d.0/usb2
lrwxrwxrwx 1 root root 0 2011-08-31 21:54 /sys/bus/usb/devices/usb3 -> ../../../devices/pci0000:00/0000:00:1c.3/0000:04:00.0/usb3

```

Is the output of the above command the same for you?

---

### Post by nwadams on 2011-08-31
awesome work guys. Can someone with a usb 3.0 hard drive try to do some long transfers with it (play a movie from it or something) because I tried two u36sd's and both of them had the drive reset after some time of playing the video. This happened for me in windows. I was hoping someone could test both in windows and Ubuntu for me and see if I should try another u36sd or if its a problem with all of them and go find another laptop. 

Sorry I have been super busy and sick, I promise I will get around to updating the first post later this week.

---

### Post by AbtZ on 2011-08-31
> **jadahl said:**
> Actually what the suspend/resume script does is unbind/bind the USB buses before suspending and after resuming. Does your laptop have a USB 3.0 port? On your original attachment I could see no USB 3.0 controller, which might be the reason suspend works for you but not for me.

The command "ls -l /sys/bus/usb/devices/usb*" gives me
```

lrwxrwxrwx 1 root root 0 2011-08-31 23:54 /sys/bus/usb/devices/usb1 -> ../../../devices/pci0000:00/0000:00:1a.0/usb1
lrwxrwxrwx 1 root root 0 2011-08-31 23:54 /sys/bus/usb/devices/usb2 -> ../../../devices/pci0000:00/0000:00:1d.0/usb2
lrwxrwxrwx 1 root root 0 2011-08-31 21:54 /sys/bus/usb/devices/usb3 -> ../../../devices/pci0000:00/0000:00:1c.3/0000:04:00.0/usb3

```

Is the output of the above command the same for you?
This is strange, and I do not know what to make of it. First when I ran the command, I did not have the third usb device listed, but after trying to plug a USB thumb drive into the port, it started showing up. The thumb drive did not work in the port however.

---

### Post by jadahl on 2011-08-31
> **AbtZ said:**
> This is strange, and I do not know what to make of it. First when I ran the command, I did not have the third usb device listed, but after trying to plug a USB thumb drive into the port, it started showing up. The thumb drive did not work in the port however.

Did it have identical numbers as I had? Does it show up in lspci after you plugged some device in?

---

### Post by AbtZ on 2011-08-31
Nah, now it just shows up all the time:
```
lrwxrwxrwx 1 root root 0 2011-09-01 02:08 /sys/bus/usb/devices/usb1 -> ../../../devices/pci0000:00/0000:00:1a.0/usb1
lrwxrwxrwx 1 root root 0 2011-09-01 02:08 /sys/bus/usb/devices/usb2 -> ../../../devices/pci0000:00/0000:00:1d.0/usb2
lrwxrwxrwx 1 root root 0 2011-09-01 00:09 /sys/bus/usb/devices/usb3 -> ../../../devices/pci0000:00/0000:00:1c.3/0000:04:00.0/usb3

```
Seems the same to me. Btw, I edited the other post to include a file with the full lspci output.

---

### Post by jadahl on 2011-09-01
> **AbtZ said:**
> Nah, now it just shows up all the time:
```
lrwxrwxrwx 1 root root 0 2011-09-01 02:08 /sys/bus/usb/devices/usb1 -> ../../../devices/pci0000:00/0000:00:1a.0/usb1
lrwxrwxrwx 1 root root 0 2011-09-01 02:08 /sys/bus/usb/devices/usb2 -> ../../../devices/pci0000:00/0000:00:1d.0/usb2
lrwxrwxrwx 1 root root 0 2011-09-01 00:09 /sys/bus/usb/devices/usb3 -> ../../../devices/pci0000:00/0000:00:1c.3/0000:04:00.0/usb3

```
Seems the same to me. Btw, I edited the other post to include a file with the full lspci output.

Could you try to use the following script (/etc/pm/sleep.d/20_custom-asus-u36sd) instead of the one from the wiki?
```

#!/bin/sh

BUSES="0000:00:1a.0 0000:00:1d.0"

case "${1}" in
    hibernate|suspend)
        # Switch USB buses off
        for bus in $BUSES; do
            echo -n $bus | tee /sys/bus/pci/drivers/ehci_hcd/unbind
        done
        ;;
    resume|thaw)
        # Switch USB buses back on
        for bus in $BUSES; do
            echo -n $bus | tee /sys/bus/pci/drivers/ehci_hcd/bind
        done
        ;;
esac

```

What it does is avoid unbind/bind of the non-existing USB3 controller at 0000:07:00.0 (and if it exists, it exists on 0000:04:00.0 but I remember seing somewher that XHCI suspend/resume issues requiring that hack has been fixed at least in 2.6.38 (which is the default one in Natty).

---

### Post by FirstByté on 2011-09-01
> **olof_ said:**
> Well, it does actualy fix almost every key, exept the "disable the touchpad" (fn+f9) key.

thank you!

You are welcome.

Currently, I put [finding a fix for my 'failing resume']("http://ubuntuforums.org/showpost.php?p=11208600&postcount=2") issue on a highly scale of things to do.

Well, my hardware is GT540M CUDA (Optimus); so I might be alone.

---

### Post by jadahl on 2011-09-01
> **FirstByté said:**
> You are welcome.

Currently, I put [finding a fix for my 'failing resume']("http://ubuntuforums.org/showpost.php?p=11208600&postcount=2") issue on a highly scale of things to do.

Well, my hardware is GT540M CUDA (Optimus); so I might be alone.

Did you try the script in in my last post? If you need to know what to do with it, look at [https://help.ubuntu.com/community/Asus_U36SD#Suspend](https://help.ubuntu.com/community/Asus_U36SD#Suspend) but use the one above instead of the one there. 

My theory is that one don't need to start/stop the XHCI (USB 3.0) controller. On my laptop it doesn't make any difference start/stopping it or not at all. However it seems more necessary to do so with the USB 2.0 controllers (which is what the script in my last post does).

Resume, though, does not work. It just boots up like normal when trying to wake it up.

I tried the /sys/power/vm_trace debug tool, but it have me no information I could make sense out of (different or non hash matches after different tries).

---

### Post by jadahl on 2011-09-03
A couple of progress reports.

Regarding the toggle touchpad keyboard button I have found out that it works perfectly fine. By running "synclient -l | grep TouchpadOff" one can observe that it changes between "1" and "0" when one presses the key repeatedly. The problem however is that the setting is ignored. Haven't looked into how to solve that yet.

Suspend resume works partly for me now. I'm using the updated script from the wiki page ([https://help.ubuntu.com/community/Asus_U36SD#Suspend](https://help.ubuntu.com/community/Asus_U36SD#Suspend)) which is a subset of the original. My computer suspends without problems, but resume only seem to work if I wait for a while before resuming again. I only tested waiting either ~15s and it will reboot instead, or around 10min and resume works fine.

---

### Post by _karo on 2011-09-03
> **olof_ said:**
> 
i have updated the [post]("http://ubuntuforums.org/showpost.php?p=11203583&postcount=39") now. I solved the "Permission denied" by just doing a ```
sudo ls
``` before, as the authorization is saved a while.

Thanks. But it still doesn't work for me. First I give the "sudo ls" command, and then...

```

karo@alpha:~$ git clone git@github.com:mkottman/acpi_call.git
Cloning into acpi_call...
Permission denied (publickey).
fatal: The remote end hung up unexpectedly

```Sudo git is probably a bad idea, so how do I solve this problem?

---

### Post by glindste on 2011-09-03
> **_karo said:**
> Thanks. But it still doesn't work for me. First I give the "sudo ls" command, and then...

```

karo@alpha:~$ git clone git@github.com:mkottman/acpi_call.git
Cloning into acpi_call...
Permission denied (publickey).
fatal: The remote end hung up unexpectedly

```Sudo git is probably a bad idea, so how do I solve this problem?

I got that error too, you probably need to set up an account and ssh-key for git by following this guide: [http://help.github.com/linux-set-up-git/](http://help.github.com/linux-set-up-git/)

---

### Post by FirstByté on 2011-09-03
> **jadahl said:**
> A couple of progress reports.

Regarding the toggle touchpad keyboard button I have found out that it works perfectly fine. By running "synclient -l | grep TouchpadOff" one can observe that it changes between "1" and "0" when one presses the key repeatedly. The problem however is that the setting is ignored. Haven't looked into how to solve that yet.

Suspend resume works partly for me now. I'm using the updated script from the wiki page ([https://help.ubuntu.com/community/Asus_U36SD#Suspend](https://help.ubuntu.com/community/Asus_U36SD#Suspend)) which is a subset of the original. My computer suspends without problems, but resume only seem to work if I wait for a while before resuming again. I only tested waiting either ~15s and it will reboot instead, or around 10min and resume works fine.

Thanks, it solved my suspend. However the 'wait-for-the-golden-20sec' still holds else the suspend is ruined.

I've been perusing through the 'udev' docs for the keysym's keymaps for the touchpad(fn-f9). 

Great work. Keep it up I'll keep guys up to date if I can fix the mapping too.

I'm yet to re-map my media button to 'XF86MediaAudio'

As for my bumblebee/ironhide I made 'auto-load' script just add this to your 'asusxxx.sh' that you use for turning off nVidia such as:

```
sudo cp /path/to/your/your_asusOn-Off-script.sh /etc/init.d/
```
```
sudo chmod +x /etc/init.d/*your_asusOn-Off-script.sh*
sudo update-rc.d *your_asusOn-Off-script.sh*
```
This will create the script for all the necessary runlevels (I find this wasteful, but who knows, Debian might change their runlevels someday so I left :) )

I modified '/etc/init.d/*my_asus-On-Off-script.sh*' to ensure 'acpi_call' module is loaded before I call it.
from:
```
#!/bin/sh
# Power control for Asus U41SV Optimus
# by Ashon iKON
if ! lsmod | grep -q acpi_call; then
    echo "Error: acpi_call module not loaded"
    exit
fi
```
to
```
#!/bin/sh
# Power control for Asus U41SV Optimus
if ! lsmod | grep -q acpi_call; then
    echo "I: acpi_call module not loaded"
    echo "I: loading acpi_call..."
    echo result=$(modprobe acpi_call)
    echo "I: Done loading acpi_call"
fi
```

Hope someone also find this helpful
Cheers.

---

### Post by FirstByté on 2011-09-03
> **glindste said:**
> I got that error too, you probably need to set up an account and ssh-key for git by following this guide: [http://help.github.com/linux-set-up-git/](http://help.github.com/linux-set-up-git/)
Try downloading directly

[**mkottman / acpi_call**]("https://nodeload.github.com/mkottman/acpi_call/tarball/master")

and untar it.

---

### Post by olof_ on 2011-09-04
> **jadahl said:**
> 
Regarding the toggle touchpad keyboard button I have found out that it works perfectly fine. By running "synclient -l | grep TouchpadOff" one can observe that it changes between "1" and "0" when one presses the key repeatedly. The problem however is that the setting is ignored. 


> **FirstByté said:**
> I've been perusing through the 'udev' docs for the keysym's keymaps for the touchpad(fn-f9).

did you find anything? could you please post a link on where to find it, and I might try to read some of it too? What are there to do if I want to help?

---

### Post by jadahl on 2011-09-05
> **olof_ said:**
> did you find anything? could you please post a link on where to find it, and I might try to read some of it too? What are there to do if I want to help?

I'm guessing that what is needed to make it work is to have the synaptic driver or whatever respect the TouchpadOff setting. The keyboard button does change it, but it doesn't change the "off-ness" of the actual touch pad.

---

### Post by AbtZ on 2011-09-05
Jadahl, I've tried your script and it works as well. Perhaps the script on the wiki page should be updated, then?

Also, perhaps I should have stated that I'm not running vanilla Ubuntu, but a derivative of Ubuntu -- Linux Mint.

Btw, does anyone else have a problem with shutting down? I get to a blank, black screen, fans and hdd spun down, but it won't shut itself off. Also, I have that infamouse Ubuntu hard drive Load Cycling issue, does anyone else experience this?

---

### Post by jadahl on 2011-09-05
> **AbtZ said:**
> Jadahl, I've tried your script and it works as well. Perhaps the script on the wiki page should be updated, then?

I updated the wiki after I made it work locally, but thanks for the reminder.

---

### Post by AbtZ on 2011-09-05
I now run Ubuntu Natty, and suspend works flawlessly after the fix is applied. No need to wait, I can go suspend->resume immediately with no issues.

---

### Post by AbtZ on 2011-09-05
I just tested HDMI+sound. Seems to work out of the box.

---

### Post by jadahl on 2011-09-05
> **AbtZ said:**
> I now run Ubuntu Natty, and suspend works flawlessly after the fix is applied. No need to wait, I can go suspend->resume immediately with no issues.

It would be interesting to know the specific hardware differences between the models where this is possible and where it is not. Not sure how to organize that though :P

---

### Post by AbtZ on 2011-09-05
One possible cause might be if you are running the 64-bit version of Ubuntu? I opted for 32 bit since it works better with all the crappy bank login-software we have here in Sweden.

---

### Post by jadahl on 2011-09-05
> **AbtZ said:**
> One possible cause might be if you are running the 64-bit version of Ubuntu? I opted for 32 bit since it works better with all the crappy bank login-software we have here in Sweden.

That, indeed, I do. I will try the 32 bit one from a USB memory just to try to confirm this.

Regarding crappy bank login.. I didn't think of that :P but it seems possible by using nspluginwrapper. I might give [http://fribid.se/](http://fribid.se/) a try as well.

---

### Post by jadahl on 2011-09-05
I tried booting up from a 32 bit installer. I added the fix-usb-controllers and it managed to suspended, but resume still didn't work if i triggered it within the magic time period.

---

### Post by adrien214 on 2011-09-08
I just wanted to add that I've tested USB 3 hardware on the usb 3 port and it doesnt work on a 64bit system. lsusb just hangs.

here the [bug report]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/797455"), already made by asus U36JC users.

but there is a fix [here]("http://ubuntuforums.org/showthread.php?t=1705406") (bottom of first post, section usb 3.0)

it works.

---

### Post by ThomasArildsen on 2011-09-09
> **adrien214 said:**
> I just wanted to add that I've tested USB 3 hardware on the usb 3 port and it doesnt work on a 64bit system. lsusb just hangs.

here the [bug report]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/797455"), already made by asus U36JC users.

but there is a fix [here]("http://ubuntuforums.org/showthread.php?t=1705406") (bottom of first post, section usb 3.0)

it works.
I can confirm this fix. Thanks!

---

### Post by epqr on 2011-09-09
I'm trying to use this method to disable the nvidia graphics card. As reffered to in the first post. 

> Using acpi_call module to switch on/off discrete graphics card in Linux

One of the hybrid-graphics-linux Launchpad team members has
created a Linux kernel module to call ACPI methods through
/proc/acpi/call. The code is here:

[http://github.com/mkottman/acpi_call](http://github.com/mkottman/acpi_call)

You can try it by installing the module and calling it like this:

git clone [http://github.com/mkottman/acpi_call.git](http://github.com/mkottman/acpi_call.git)

cd acpi_call

make

sudo insmod acpi_call.ko

./test_off.sh 


when i try to do the 'make' command, all I get is this error:

```
make -C /lib/modules/2.6.40.4-5.fc15.x86_64/build M=/home/jones/acpi_call modules
make: *** /lib/modules/2.6.40.4-5.fc15.x86_64/build: No such file or directory.  Stop.
make: *** [default] Error 2

```

Any idea on how to fix it? Thanks.

---

### Post by adrien214 on 2011-09-09
> **epqr said:**
> I'm trying to use this method to disable the nvidia graphics card. As reffered to in the first post. 




when i try to do the 'make' command, all I get is this error:

```
make -C /lib/modules/2.6.40.4-5.fc15.x86_64/build M=/home/jones/acpi_call modules
make: *** /lib/modules/2.6.40.4-5.fc15.x86_64/build: No such file or directory.  Stop.
make: *** [default] Error 2

```

Any idea on how to fix it? Thanks.

do you have build-essential and kernel headers installed ?

---

### Post by adrien214 on 2011-09-09
> **ThomasArildsen said:**
> I can confirm this fix. Thanks!

Now i can also confirm my system has lost BT utility and also network.... not sure if it has anything to do with the usb 3.0 fix... go dammit.

EDIT, had to rollback because this fixes usb 3.0 but screws the rest of the system...for some reason I did this on a previous install and it worked fine. I also had to do the entire BT procedure again to recover BT connectivity.

---

### Post by jlebla01 on 2011-09-09
Hey guys,

Keep up the good work, almost everything is working.

One thing I cannot seem to get working is the USB 3.0 port.  I see that the directions are not on the wiki page yet, so I'm curious if other people have had success.

I've tried the u36jc workaround which is to modify the grub script to include

GRUB_CMDLINE_LINUX_DEFAULT

With the pci-nomsi,noaer command, so that the file now has a line that looks like

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash pci-nomsi,noaer"

This doesn't appear to work. Is there something wrong with the formatting of this line? Spacing, etc...  The usb port doesn't work with any device, USB 3 or not.

I'm really confused by this issue, since lspci -v returns

04:00.0 USB Controller: Fresco Logic FL1000G USB 3.0 Host Controller (rev 04) (prog-if 30 [XHCI])
    Subsystem: ASUSTeK Computer Inc. Device 1039
    Physical Slot: 3
    Flags: bus master, fast devsel, latency 0, IRQ 46
    Memory at dd200000 (32-bit, non-prefetchable) [size=64K]
    Capabilities: <access denied>
    Kernel driver in use: xhci_hcd
    Kernel modules: xhci-hcd

everything looks correct to me.... I am running 64 bit ubuntu, so is there something special I need to do?

thanks in advance.

---

### Post by ubacux on 2011-09-09
Hi,

I want to change HD to my U36SD. I saw the images on how do that [URL="http://www.sweclockers.com/forum/112-barbara-datorer-koprad/1018104-asus-u36sd/index17.html#post11252173"]here
[/URL]But that's in swedish and i don't know that.
Someone in this forum can help me to translate it word by word in english.
below is the text ...

 2. Lossa snäppena på den breda flatkabeln, de svarta pluttarna petas bakåt  i pilarnas riktning med en liten mejsel för att låsa upp kontakten.

[IMG]http://pic.xfastest.com/NB/ASUS/U36JC/U36JC-14.jpg[/IMG]

**3.** På den lilla flatkabel ska den svarta låsbygeln rakt upp,  enkelt det också med en liten mejsel. Det sitter en sorts eltejp eller  liknande som man lossar lite utan problem för att komma åt.

[IMG]http://pic.xfastest.com/NB/ASUS/U36JC/U36JC-15.jpg[/IMG]

thanks a lot in advance !!!

---

### Post by ubacux on 2011-09-09
about fix usb 3.0 i think the right sintax is

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash pci=nomsi,noaer"
after pci put =
however maybe is better "quiet splash pci=nomsi", because some people putting "noaer" have experienced problems in using usb supports and have been obliged to format it.
but i'm not sure. So try at the moment with pci=nomsi and if you see that's usb 3.0 port doesnt work well try to add "noaer".

bye

---

### Post by nwadams on 2011-09-09
Hey everyone,

Thanks for the great work. So it turns out that I had a usb 3.0 problem with the TWO asus u36sd's that my parents tried on my behalf...I might try another or I might end up getting a different laptop. I will try to keep things updated as best as possible.

---

### Post by jlebla01 on 2011-09-09
> **ubacux said:**
> about fix usb 3.0 i think the right sintax is

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash pci=nomsi,noaer"
after pci put =
however maybe is better "quiet splash pci=nomsi", because some people putting "noaer" have experienced problems in using usb supports and have been obliged to format it.
but i'm not sure. So try at the moment with pci=nomsi and if you see that's usb 3.0 port doesnt work well try to add "noaer".

bye

Sorry, I typed wrong in my previous post. I DID have

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash pci=nomsi,noaer"

I've changed it to

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash pci=nomsi"

and it seems to be working fora usb 2 device. so I'll check the usb 3 functionality when I can.  Thanks!

---

### Post by epqr on 2011-09-09
> **adrien214 said:**
> do you have build-essential and kernel headers installed ?

Great! Thanks alot :) Linux newbie right here, haha. But i think it worked, I got trough all the steps.

The command 'lspci -vnnn | grep VGA' gave me

```
00:02.0 VGA compatible controller [0300]: Intel Corporation Device [8086:0116] (rev 09) (prog-if 00 [VGA controller])
01:00.0 VGA compatible controller [0300]: nVidia Corporation Device [10de:1050] (rev a1) (prog-if 00 [VGA controller])

```
Before 

and

```
00:02.0 VGA compatible controller [0300]: Intel Corporation Device [8086:0116] (rev 09) (prog-if 00 [VGA controller])
01:00.0 VGA compatible controller [0300]: nVidia Corporation Device [10de:1050] (rev ff) (prog-if ff)

```
After


Also anyone know what you would do if you wanted to enable the card again? With the acpi_call method that is.

---

### Post by jadahl on 2011-09-09
Somewhat rough translations. Term translation credits goes to Wikipedia.

> 
 2. Lossa snäppena på den breda flatkabeln, de svarta pluttarna petas bakåt  i pilarnas riktning med en liten mejsel för att låsa upp kontakten.

"2. Loosen the hooks on the wide ribbon cable. To disconnect, the black thingies are pushed backwards in the direction of the arrow by using a screwdriver."

> 
 3. På den lilla flatkabel ska den svarta låsbygeln rakt upp,  enkelt det också med en liten mejsel. Det sitter en sorts eltejp eller  liknande som man lossar lite utan problem för att komma åt.

"3. On the small ribbon cable the black lock hoop should be go straight upwards, which is also easily done with a screwdriver. There is some kind of electrical tape there that can be loosened to get access without problems."

---

### Post by jadahl on 2011-09-09
Since the bluetooth fix only works until you reboot, I created a boot service that does it automatically when I start my computer. This will, AFAIK, not be needed in 11.10 since the correct USB ID already is known to the driver in question, but makes it work after a fresh boot on 11.04 (and other distributions running 2.6.38 (can enable other kernels easily).

The boot script is the following:

```

#! /bin/sh
### BEGIN INIT INFO
# Provides:          ath3011-workaround
# Required-Start:    $local_fs
# Required-Stop:     $local_fs
# X-Start-After:     bluetooth
# X-Stop-After:      bluetooth
# Default-Start:     2 3 4 5
# Default-Stop:      0 1 6
# Short-Description: Atheros AR3011 work around.
# Description:       Manually adds Atheros AR3011 with sflash firmware to
#                    the ath3k kernel module.
### END INIT INFO

. /lib/init/vars.sh
. /lib/lsb/init-functions

# Configure
DEFAULT_ENABLE_FOR=2.6.38
DEFAULT_USB_ID="13d3 3304"

ENABLE_FOR=${ATH3K_WORKAROUND_ENABLE_FOR-$DEFAULT_ENABLE_FOR}
USB_ID=${ATH3K_WORKAROUND_USB_ID-$DEFAULT_USB_ID}

SCRIPTNAME=ath3011-workaround

module_loaded()
{
    egrep -q "^$1 " /proc/modules
}

unload_module()
{
    module_loaded $1 || return 0
    rmmod $1
    case "$?" in
	0)
	    return 0
	    ;;
	*)
	    [ "$VERBOSE" != no ] && log_failure_msg "Couldn't unload module $1"
	    return 2
	    ;;
    esac
}

load_module()
{
    modprobe $2 $1
    case "$?" in
	0)
	    return 0
	    ;;
	*)
	    [ "$VERBOSE" != no ] && log_failure_msg "Couldn't load module $1"
	    return 2
	    ;;
    esac
}

fail()
{
    log_failure_msg "$1"
}

check_workaround_enabled()
{
    for x in $ENABLE_FOR
    do
	uname -r | egrep -q "^$x" && return 0
    done
    return 2
}

do_start()
{
    check_workaround_enabled || return 0

    unload_module btusb || return 2
    unload_module ath3k || return 2
    load_module ath3k -a || return 2
    echo "$USB_ID" > /sys/bus/usb/drivers/ath3k/new_id
    case "$?" in
	0)
	    ;;
	*)
	    [ "$VERBOSE" != no ] && \
	       	log_warning_msg "Couldn't add new USB ID to ath3k module"
	    ;;
    esac
    load_module btusb || return 2

    return 0
}

case "$1" in
  start)
	[ "$VERBOSE" != no ] && log_daemon_msg "Starting $SCRIPTNAME"
	do_start
	case "$?" in
		0|1) [ "$VERBOSE" != no ] && log_end_msg 0 ;;
		2) [ "$VERBOSE" != no ] && log_end_msg 1 ;;
	esac
	;;
  stop)
	[ "$VERBOSE" != no ] && log_daemon_msg "Stopping $SCRITPTNAME"
	[ "$VERBOSE" != no ] && log_end_msg 0
	;;
  status)
       exit 0
       ;;
  restart|force-reload)
	log_daemon_msg "Restarting $DESC" "$NAME"
	do_start
	;;
  *)
	echo "Usage: $SCRIPTNAME {start|stop|status|restart|force-reload}" >&2
	exit 3
	;;
esac

:

```

How to install and enable it:

```

gksu gedit /etc/init.d/ath3011-workaround

```
Paste the script above save and quit.

```

sudo chmod +x /etc/init.d/ath3011-workaround
sudo update-rc.d ath3011-workaround defaults

```

These two commands makes the script executable and adds it to all relevant runlevels.

Now, even after a reboot or halt/boot, Bluetooth should just work.

---

### Post by adrien214 on 2011-09-10
> **jadahl said:**
> ...

These two commands makes the script executable and adds it to all relevant runlevels.

Now, even after a reboot or halt/boot, Bluetooth should just work.

thank you Sir !! EDIT ACHHHH ! lost BT again...

Also, the fix for Fn keys doesn't allow control of VLC, in my case...

---

### Post by jadahl on 2011-09-11
> **adrien214 said:**
> EDIT ACHHHH ! lost BT again...

Also, the fix for Fn keys doesn't allow control of VLC, in my case...

Lost BT again, how?

Regarding VLC, does it even have built in support for multimedia keys?

---

### Post by adrien214 on 2011-09-11
> **jadahl said:**
> Lost BT again, how?

Regarding VLC, does it even have built in support for multimedia keys?

I dont know, I was browsing through BT connected to my mobile phone and then disconnected from it and plugged in the wire and somehow afterwards I noticed the icon was greyed out... now it's back on again... weird.

---

### Post by jadahl on 2011-09-11
If you want to be able to enable "Disable touchpad while typing", you can follow the instructions here: [https://bugs.launchpad.net/ubuntu-release-notes/+bug/582809/comments/144](https://bugs.launchpad.net/ubuntu-release-notes/+bug/582809/comments/144)

---

### Post by olof_ on 2011-09-12
> **jadahl said:**
> If you want to be able to enable "Disable touchpad while typing", you can follow the instructions here: [https://bugs.launchpad.net/ubuntu-release-notes/+bug/582809/comments/144](https://bugs.launchpad.net/ubuntu-release-notes/+bug/582809/comments/144)

wonderful! thank you alot.

---

### Post by awilu on 2011-09-21
I have big troubleshooting with openoffice or Libreoffice.

When I edit a presentation with impress or edit a tablesheet with calc, my computer freezes. I can do anything (mouse, keyboard), the only thing is to do a hard reboot.

It happen realy often (perhaps 2 times in 15 minutes).

I try libreoffice and openoffice, same trouble, less often with openoffice.

Anybody can help me ?

Awilu
Linux Mint 11 - asus U36S

---

### Post by daveg on 2011-09-21
Thanks to all the great work of this thread, I'm the happy user of a new U36SD on Ubuntu. There's one thing that's been nagging me though. Does the CPU fan in everyone's U36SDs always run? Its not particularly loud but I can constantly feel the hot air getting pushed out of it.

---

### Post by adrien214 on 2011-09-22
> **awilu said:**
> I have big troubleshooting w...

I try libreoffice and openoffice, same trouble, less often with openoffice.

Anybody can help me ?

Awilu
Linux Mint 11 - asus U36S

Hi,maybe [this]("http://www.worldofnubcraft.com/1326/when-libreoffice-causes-ubuntu-to-lock-up/") ? next time, google, this is not the place for this laptop o  os

---

### Post by adrien214 on 2011-09-22
> **daveg said:**
> Thanks to all the great work of this thread, I'm the happy user of a new U36SD on Ubuntu. There's one thing that's been nagging me though. Does the CPU fan in everyone's U36SDs always run? Its not particularly loud but I can constantly feel the hot air getting pushed out of it.


it's not on mine... could you add the CPUfreq applet to the panel and check at what speed your cpus are running ?

or more simply type in a command line when not running any power demanding app: 

grep "cpu MHz" /proc/cpuinfo

andpaste the outcome

---

### Post by nwadams on 2011-09-23
so I ended up getting a u36sd and it works great in linux. I do have a few issues however

1. The brightness controls work but hey do not interact with the OS.

2. the USB 3.0 port does not work after suspend/resume

3. The left hardware key for the performance/power saving setting in windows does nothing in Ubuntu and I am wondering if I can assign it to something some how.

4. Has anyone had any luck getting dual graphics to work in Ubuntu (Ironhide or Bumblebee)

5. Anybody come up with a more reliable fix for the inverted webcam?

---

### Post by MarcusW on 2011-09-27
Wow, thanks for this thread. I'm running Fedora 15 on my U36SD. I was just starting to give up on being able to deactivate the nvidia card and fixing suspend. Now it's working great. :)

---

### Post by AbtZ on 2011-09-27
> **nwadams said:**
> 3. The left hardware key for the performance/power saving setting in windows does nothing in Ubuntu and I am wondering if I can assign it to something some how
The button is for performance/power saving or what appears to be some sort of quick launch (I haven't used the laptop in Windows, so I wouldn't know). In any case, because of its quick launch appearance, I bound it to make gnome-do appear. :)

I'm not sure if you need to apply the Asus function key fix to make Ubuntu aware of the key however.

---

### Post by nwadams on 2011-09-27
> **AbtZ said:**
> The button is for performance/power saving or what appears to be some sort of quick launch (I haven't used the laptop in Windows, so I wouldn't know). In any case, because of its quick launch appearance, I bound it to make gnome-do appear. :)

I'm not sure if you need to apply the Asus function key fix to make Ubuntu aware of the key however.

I'm not sure if I needed to apply the Asus function key fix, but It works after applying the fix. I have figured out that I can assign it to something, I just haven't decided what yet...and there's that fn+c key with the screen thing on it to apply to somewhere too...hmm decisions decisions.

Does anyone know if the left hardware button has an LED like the right one?

---

### Post by TweFoju on 2011-09-28
Sweet!!

my 36SD will arrive tomorrow, got my SSD and 8GM ram sitting ready for the baby to come :D

cant wait to try out all the fixes you guys have discovered!

just a question though, so the SSD i have now contain Windows XP, and i plan to clean install it and only use uBuntu

can i just do that when i am installing uBuntu and just say "clean install uBuntu"  or something like "remove everything" 

will that automatically erase all the Windows?

thanks!

---

### Post by TweFoju on 2011-09-28
Guys, anyway, i have a couple of questions

so this is my 1st time using Bumblebee

it told us to add these before installing the Bumblebee PPA

> sudo apt-get purge nvidia-current> sudo add-apt-repository ppa:ubuntu-x-swat/x-updatesbut before i do this, should i remove the nVidia Accelerated graphics driver under the "Additional Driver" ?

as it says it's active but it's not currently in use?

and what does this mean? 

"To see if it works, run during around 30s:
glxspheres"

run during around 30s? i dont get what he's trying to say..

thanks!

---

### Post by dirtylobster on 2011-09-29
> **TweFoju said:**
> just a question though, so the SSD i have now contain Windows XP, and i plan to clean install it and only use uBuntu

can i just do that when i am installing uBuntu and just say "clean install uBuntu"  or something like "remove everything" 

will that automatically erase all the Windows?

Yes. Just follow the instructions in the installer, it's easy!

---

### Post by TweFoju on 2011-09-29
> **dirtylobster said:**
> Yes. Just follow the instructions in the installer, it's easy!
yep, i spent 1/2 hour on the partitioning area figuring things out, was confusing at 1st, but after a while, i understand the way of it, 

anyway, yeah, i am just more curious about my question for the Nvidia part

so do i have to remove the Nvidia driver on the Additional driver before i do any of those steps?

---

### Post by nwadams on 2011-09-29
> **TweFoju said:**
> yep, i spent 1/2 hour on the partitioning area figuring things out, was confusing at 1st, but after a while, i understand the way of it, 

anyway, yeah, i am just more curious about my question for the Nvidia part

so do i have to remove the Nvidia driver on the Additional driver before i do any of those steps?

Yes, you need to remove the Nvidia restricted driver before installing bumblebee or Ironhide. Let me know how bumblebee works because I might be switching to it from ironhide.

---

### Post by TweFoju on 2011-09-29
i will try it once i got home, but just so you know, i am a real newbie in uBuntu/Linux, so it might take a while for me to research very deep before i start installing as i dont plan to screw anything haha

---

### Post by nwadams on 2011-09-29
> **TweFoju said:**
> i will try it once i got home, but just so you know, i am a real newbie in uBuntu/Linux, so it might take a while for me to research very deep before i start installing as i dont plan to screw anything haha

thats fine. Let us know if you have an questions or need any help along the way

---

### Post by TweFoju on 2011-09-29
yes i do,

there are so many different version of how to install the Bumble bee, i am not sure which one is the best one?  and the most proper way ?

like there are this one

[http://askubuntu.com/questions/37590/nvidia-drivers-not-working-after-upgrade-why-can-i-only-see-terminal](http://askubuntu.com/questions/37590/nvidia-drivers-not-working-after-upgrade-why-can-i-only-see-terminal)

then a couple of more on the net

which one you would recommend me to follow?

thanks!


--- update ---

hello

i tried the "git clone [email]git@github.com:mkottman/acpi_call.git[/email]"

but i got this message:

Cloning into acpi_call...
The authenticity of host 'github.com (207.97.227.239)' can't be established.
RSA key fingerprint is 16:27:ac:a5:76:28:2d:36:63:1b:56:4d:eb:df:a6:48.
Are you sure you want to continue connecting (yes/no)? yes
Warning: Permanently added 'github.com,207.97.227.239' (RSA) to the list of known hosts.
Permission denied (publickey).
fatal: The remote end hung up unexpectedly

---

### Post by TweFoju on 2011-09-29
sorry goddamn INTERNET, sorry guys dont mean to do triple post

---

### Post by TweFoju on 2011-09-29
everything finally works!

> twefoju@Wils:~/acpi_call$ sudo insmod acpi_call.ko
[sudo] password for twefoju: 
twefoju@Wils:~/acpi_call$ chmod +x ./test_off.sh
twefoju@Wils:~/acpi_call$ ./test_off.sh
Trying \_SB.PCI0.P0P1.VGA._OFF: failed
Trying \_SB.PCI0.P0P2.VGA._OFF: failed
Trying \_SB_.PCI0.OVGA.ATPX: failed
Trying \_SB_.PCI0.OVGA.XTPX: failed
Trying \_SB.PCI0.P0P3.PEGP._OFF: failed
Trying \_SB.PCI0.P0P2.PEGP._OFF: failed
Trying \_SB.PCI0.P0P1.PEGP._OFF: failed
Trying \_SB.PCI0.MXR0.MXM0._OFF: failed
Trying \_SB.PCI0.PEG1.GFX0._OFF: failed
Trying \_SB.PCI0.PEG0.GFX0.DOFF: works!
twefoju@Wils:~/acpi_call$ 
although i use the latest Bumblebee

not this one:

sudo apt-add-repository ppa:bumblebee/stable 
but this one:


[LIST]
[*]**sudo apt-add-repository ppa:mj-casalogic/bumblebee**
[*][B]sudo apt-get update && sudo apt-get install bumblebee 
[/B]
[/LIST]
from

 [http://www.omgubuntu.co.uk/2011/06/bumblebee-gets-a-ppa-brings-nvidia-optimus-graphics-switching-to-ubuntu/](http://www.omgubuntu.co.uk/2011/06/bumblebee-gets-a-ppa-brings-nvidia-optimus-graphics-switching-to-ubuntu/)

anyway yeah. the "works!" appear

and im so happy!

just 1 question though

i use the Additional Driver from the Bumblebee, is that fine? i actually activate it ( the nVidia Experimental 3D support )

because it's from Bumblebee that is why i used it as you guys say not to install the nVidia one

----

however, when i restart the laptop, then i want to turn it off/on

it just say "bash: /proc/acpi/call: No such file or directory"

do i have to run the call again to turn it on? so basically whenever i turn off my laptop

i have to restart all these?

> cd acpi_call
make
sudo insmod acpi_call.ko

chmod +x ./test_off.sh

./test_off.sh


---

### Post by adrien214 on 2011-09-30
Hello TweJofu,
"works!" means that acpi_call has found a way to shutdown your nvidia, not that bumblebee works. About losing the settings,I have the same problem here and from what I have read it looks like it's a file permission issue but I haven't figured it out...

---

### Post by TweFoju on 2011-09-30
so you're saying that the Bumblebee is still not working?

how so? because isn't Bumblebee the one making the switch? i dont get it. :confused:

---

### Post by TweFoju on 2011-10-01
Guys, a quick question for you all

are you guys experiencing any desktop crashes using 11.04 with your u36sd?

because i am starting to believe that the laptop is incompatible because i know 11.04 crashes a lot

but i revert back to 10.10, but i still get the same crash

i refuse to believe that it's hardware problem as using Win7 is fine

the random crash that will make your mouse cant even move, that kind of crash

i seen a lot of people with different crash with 11.04, but yea

are your 11.04's working fine on your laptop? because if it is, i might reconsider to return this latop and exchange with the new one

---

### Post by nwadams on 2011-10-01
> **TweFoju said:**
> Guys, a quick question for you all

are you guys experiencing any desktop crashes using 11.04 with your u36sd?

because i am starting to believe that the laptop is incompatible because i know 11.04 crashes a lot

but i revert back to 10.10, but i still get the same crash

i refuse to believe that it's hardware problem as using Win7 is fine

the random crash that will make your mouse cant even move, that kind of crash

i seen a lot of people with different crash with 11.04, but yea

are your 11.04's working fine on your laptop? because if it is, i might reconsider to return this latop and exchange with the new one

ya. i'm getting crashes once and a while.

---

### Post by hhwangbo on 2011-10-03
> **nwadams said:**
> ya. i'm getting crashes once and a while.

Same here.  I'm getting random lock-ups where my mouse and keyboard don't appear to be working. 

It requires a hard reset.

Any idea how I can debug this or find out why it's locking up on me?

---

### Post by nwadams on 2011-10-03
> **hhwangbo said:**
> Same here.  I'm getting random lock-ups where my mouse and keyboard don't appear to be working. 

It requires a hard reset.

Any idea how I can debug this or find out why it's locking up on me?

thats exactly what I have, no idea how to debug it either.

Anybody else have any info?

---

### Post by Awaking on 2011-10-04
After installing Ubuntu 11.04 the Unity desktop and Compiz was  turned off. I removed nVidia drivers, after that Unity and Compiz became running. But there are many lags :( For example while moving a window.  Is there anyone with similar problem?

---

### Post by TweFoju on 2011-10-05
u guys know what? just forget about the Natty

Oneiric is in 9 days, i uninstalled my 11.04, now using windows back, waiting for 11.10

hoping that it will not crash anymore hehe

and hopefully, there will be a better GPU support ( although unlikely )

---

### Post by stayfrosty555 on 2011-10-07
> **Awaking said:**
> After installing Ubuntu 11.04 the Unity desktop and Compiz was  turned off. I removed nVidia drivers, after that Unity and Compiz became running. But there are many lags :( For example while moving a window.  Is there anyone with similar problem?

Have you tried bumblebee explained earlier in this thread?

---

### Post by jadahl on 2011-10-07
> **Awaking said:**
> After installing Ubuntu 11.04 the Unity desktop and Compiz was  turned off. I removed nVidia drivers, after that Unity and Compiz became running. But there are many lags :( For example while moving a window.  Is there anyone with similar problem?

Did you try the work around described here? [https://help.ubuntu.com/community/Asus_U36SD#Desktop_effects](https://help.ubuntu.com/community/Asus_U36SD#Desktop_effects)

---

### Post by cleaton on 2011-10-08
I am interested in buying this laptop, but I am curious how 11.10 will work on it. Has anyone tried installing the latest beta?

---

### Post by jadahl on 2011-10-08
> **cleaton said:**
> I am interested in buying this laptop, but I am curious how 11.10 will work on it. Has anyone tried installing the latest beta?

I tried booting the beta2 installer from a USB drive and it worked pretty much as well as with 11.04, except you don't need for example the bluetooth hack. I ran [checkbox]("https://launchpad.net/checkbox") and there were some tests that failed (don't recall which ones), but that's partly because I didn't apply some of the hacks needed in 11.04.

---

### Post by adrien214 on 2011-10-10
Twefoju, you will have to wait for 12.04 for better optimus support with the Wayland display system from what i have read...

---

### Post by crysman on 2011-10-10
I would like to thank to all people making *Ubuntu* such a user supporting-oriented system. I've been a bit disappointed with my *ASUS U36SD* and *Ubuntu* - not working USB3, not working Fn keys, suspend problem...

But almost everything is explained here, how to fix.. Thanks.

I am about to wait a few days for final *Ubuntu 11.10* to see what will be left to solve in the new release. I suppose lot of things will be working there just out-of-the-box (except for the *Nvidia* vs *Intel* graphic card problem). Or am I wrong?

Greetings
crysman
(currently on Xubuntu 11.04)

---

### Post by crysman on 2011-10-12
> **nwadams said:**
> Link to the wiki for u36sd 
[https://help.ubuntu.com/community/Asus_U36SD](https://help.ubuntu.com/community/Asus_U36SD)

So it turns out that I had a usb 3.0 problem with mine so I do not know when or even if I will be getting a u36sd with ubuntu. 

**Works out of the box**
Audio
Audio out port
Internal microphone
Mic port
HDMI port
Video (without desktop effects)
USB
Wireless Networking
WiFi switch (Fn+F2)
VGA port
Card reader
Brightness control (Fn+F5/F6)
LCD on/off switch (Fn+F8)
Multitouch touchpad (two finger scrolling, activate via System Settings)
Intel Turbo Boost (to test, run turbostat from the package acpidump)

**Does not work out of the box**
Desktop effects
Nvidia card
Volume control (Fn+F10/F11/F12)
Multimedia controls (Fn+Up/Down/Left/Right)
Suspend
Bluetooth

...

If anyone has a u36sd already please post what works/what doesn't work and any extra configuration/tweaks you had to do to get things to work properly. I will add your advice and instructions to this main post so we can make a comprehensive guide for other owners. 
...


Hi, I am waiting for Xubuntu 11.10 to get some issues fixed automatically on my U36SD, then I'll post more.
BUT... there is no info about the **fingerprint reader - how to get it working**?

Thanks a lot
crysman

---

### Post by nwadams on 2011-10-12
> **crysman said:**
> Hi, I am waiting for Xubuntu 11.10 to get some issues fixed automatically on my U36SD, then I'll post more.
BUT... there is no info about the **fingerprint reader - how to get it working**?

Thanks a lot
crysman

I didn't even know this model had a fingerprint reader option. Mine and I guess everybody else's doesn't currently have one.

---

### Post by crysman on 2011-10-12
> **nwadams said:**
> I didn't even know this model had a fingerprint reader option. Mine and I guess everybody else's doesn't currently have one.

Yes it does (some models - like mine), _[look e.g. here]("http://www.netbooklive.com/wp-content/uploads/2011/07/asus-u36s-1.jpg")_... I would really like to make it work under Ubuntu.

I've tried *fprint*, but it does not work :(
```

$ apt-cache pkgnames | grep fprint
xfprint4
libfprint-dev
fprint-demo
libpam-fprint
libfprint0

```

---

### Post by nwadams on 2011-10-13
Your best bet is to find out the part that is used and then see if there are generic instructions for the part or other laptops that use the part. I'm sorry I can't be more help, but it doesn't seem that many people have the model with the fingerprint reader.

On another note, I am going to upgrade to 11.10 tonight and will update on how that goes.

---

### Post by crysman on 2011-10-13
> **nwadams said:**
> Your best bet is to find out the part that is used and then see if there are generic instructions for the part or other laptops that use the part. I'm sorry I can't be more help, but it doesn't seem that many people have the model with the fingerprint reader.

On another note, I am going to upgrade to 11.10 tonight and will update on how that goes.

Fingerprint reader> what a pitty :((
"..to find out the part that is used.." - how, please?

upgrade to 11.10> Great. I've just updated. Have to go sleep, but so far I've seen:
[LIST=1]
[*]Fn keys are working (except of disabling touchpad).
[*]**temperature (acpitz-0) is now +10 °C** greater than before (raised from 51 to 61) - no CPU load!! What is that? :( Could it be somehow connected with NVIDIA graphic card drivers? I do not know which one is active or if both..
[/LIST]

```

$ lspci
00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200/2nd Generation Core Processor Family PCI Express Root Port (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
00:16.0 Communication controller: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB Controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 (rev 05)
00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 05)
00:1c.0 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 (rev b5)
00:1c.1 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 2 (rev b5)
00:1c.3 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 4 (rev b5)
00:1c.5 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 6 (rev b5)
00:1d.0 USB Controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 (rev 05)
00:1f.0 ISA bridge: Intel Corporation HM65 Express Chipset Family LPC Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 6 Series/C200 Series Chipset Family 6 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller (rev 05)
01:00.0 VGA compatible controller: nVidia Corporation Device 1050 (rev a1)
03:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
04:00.0 USB Controller: Fresco Logic FL1000G USB 3.0 Host Controller (rev 04)
05:00.0 Ethernet controller: Atheros Communications AR8151 v2.0 Gigabit Ethernet (rev c0)

```

PS: After booting 2.6.38-12-generic temperature again 51. Strange... But must be fixed - not only because of the fan noise :(

---

### Post by Awaking on 2011-10-15
> **jadahl said:**
> Did you try the work around described here? [https://help.ubuntu.com/community/Asus_U36SD#Desktop_effects](https://help.ubuntu.com/community/Asus_U36SD#Desktop_effects)
Yes

> **stayfrosty555 said:**
> Have you tried bumblebee explained earlier in this thread?
Not yet.

I have installed Ubuntu 11.10.
As for me 11.10 is more stable.
Avarage temperature is 57-60*C. Fan noise is clearly heard =( 
Unity, USB 3.0, almost all FN keys, bluetooth, wifi work out of box. nVidia driver is not activated automatically. But there are many troubles connected with Unity. There are some lags of interface.


While changing the virtual desktop u can see this funny effect (i use two monitors):
[[IMG]http://s013.radikal.ru/i323/1110/c7/b3ad8214391at.jpg[/IMG]](http://radikal.ru/F/s013.radikal.ru/i323/1110/c7/b3ad8214391a.png)

---

### Post by stayfrosty555 on 2011-10-15
I can't seem to get that much battery life out of 11.10. I reinstalled bumblebee and the acpi_call, ran the test script and it says it found a way to turn nvidia-card off and then i turned it off. The battery life went from 4 hours to 5 hours. I got 7 hours+ on Ubuntu 11.04. 

What do you get out of the battery and what have you done?

---

### Post by nwadams on 2011-10-15
> **stayfrosty555 said:**
> I can't seem to get that much battery life out of 11.10. I reinstalled bumblebee and the acpi_call, ran the test script and it says it found a way to turn nvidia-card off and then i turned it off. The battery life went from 4 hours to 5 hours. I got 7 hours+ on Ubuntu 11.04. 

What do you get out of the battery and what have you done?

There are battery issues in 11.10. Hopefully they get resolved soon.

---

### Post by Awaking on 2011-10-16
I have tried to install Ubuntu 11.04 and 11.10, Xubuntu 11.10, Kubuntu 11.10, Linux Mint 2011 and what can I say... KDE with its visual effects is faster than Gnome-based distributives. I have tested it with no any nVidia drivers installed. Only Intel HD3000.  Is there anybody who have good perfomance with Gnome?
And one more note. All these operating systems heats CPU more than WIndows 7. As the result - fan noise is louder =) For example if you copy any files, Ubuntu can heat CPU up to the 70*C, while Windows keeps CPU temperature  ~50-52*C.

---

### Post by stayfrosty555 on 2011-10-16
> **nwadams said:**
> There are battery issues in 11.10. Hopefully they get resolved soon.

After a quick google I found a post made by user tista on this forum, which actually helps getting about 2 more hours of battery life, [http://ubuntuforums.org/showpost.php?p=11346775&postcount=7](http://ubuntuforums.org/showpost.php?p=11346775&postcount=7)

---

### Post by patrikt on 2011-10-18
Hello. Just installed 11.10 on my new u36sd and atleast for me the Volume control (Fn+F10/F11/F12) works "out of the box". Put a note about that in the original post.

---

### Post by crysman on 2011-10-18
> **stayfrosty555 said:**
> After a quick google I found a post made by user tista on this forum, which actually helps getting about 2 more hours of battery life, [http://ubuntuforums.org/showpost.php?p=11346775&postcount=7](http://ubuntuforums.org/showpost.php?p=11346775&postcount=7)

I've added all three _[i915-like parameters]("http://www.phoronix.com/scan.php?page=article&item=intel_i915_power&num=1")_ to GRUB. That brought the temperature back to to á 50°C.

Moreover, I applied some of these tips:
[http://www.lesswatts.org/](http://www.lesswatts.org/)
[http://www.thinkwiki.org/wiki/How_to_reduce_power_consumption](http://www.thinkwiki.org/wiki/How_to_reduce_power_consumption)

resulting in á 13W discharge rate instead of previous 24W(measured by *powertop*)!

Great!

---

### Post by nwadams on 2011-10-18
> **crysman said:**
> I've added all three _[i915-like parameters]("http://www.phoronix.com/scan.php?page=article&item=intel_i915_power&num=1")_ to GRUB. That brought the temperature back to to á 50°C.

Moreover, I applied some of these tips:
[http://www.lesswatts.org/](http://www.lesswatts.org/)
[http://www.thinkwiki.org/wiki/How_to_reduce_power_consumption](http://www.thinkwiki.org/wiki/How_to_reduce_power_consumption)

resulting in á 13W discharge rate instead of previous 24W(measured by *powertop*)!

Great!

I hate to be a newb but where did you put the parameters. The battery life still isn't as good. I get like 5 hours now instead of 8...

---

### Post by crysman on 2011-10-18
> **nwadams said:**
> Link to the wiki for u36sd 
[https://help.ubuntu.com/community/Asus_U36SD](https://help.ubuntu.com/community/Asus_U36SD)

...

**Works out of the box**
Audio
Audio out port
...

**Does not work out of the box**
Desktop effects
Nvidia card
Volume control (Fn+F10/F11/F12)
...

**Helpful Tips and Tweaks**
...

How to fix webcam orientation. Follow the instructions [here]("https://help.ubuntu.com/community/Asus_U36JC") to fix webcam orientation.

**Frequently Asked Questions**
...

**Thanks to:**
Martin Juhl - Bumblebee/Ironhide ([http://www.martin-juhl.dk/](http://www.martin-juhl.dk/))

OK, I've switched to Xubuntu 11.10 and would like to update the information here.

What I see has been fixed and/or [COLOR="DarkGreen"]IS now working in 11.10[/COLOR]:
[LIST=1]
[*]USB 3.0
[*]these Fn key kombinations: F2, F5-F8, F11, F12, arrows
[*]bluetooth
[/LIST]

What [COLOR="DarkRed"]IS NOT working[/COLOR] in 11.10:
[LIST=1]
[*]these Fn combinations: F9 (touchpad disable) and F10 (mute).
Mute works just in direction -> mute. Second press - to unmute - keeps it muted. I've find out that, while muting, the Fn+F10 affects both the "HDA Intel PCH (Alsa mixer)"'s Master channel and "Playback: Internal Audio Analog Stereo (PulseAudio Mixer)"'s Master. BUT, while unmuting, it unmutes only the first one, leaving the second one muted. When I click the XFCE menu panel sound button and "Unmute", it unmutes both of them.
Any ideas?
[*]fingerprint reader (tested with *fprint 0.4*)
[*]suspend - does not turn the computer into standby, I have to hard switch off with a long press of power button. After turning it on again, there are filesystem checks etc... this is really bad :(
[*]hibernate - does not turn the computer off, remains "dead" with just non-blinking cursor upper left. I have to hard switch off with a long press of power button. After turning it on again, session is restored. Any ideas?
[*]webcam - picture is upside-down (tested with *Camorama version 0.19*). [LD_PRELOAD trick]("https://help.ubuntu.com/community/Asus_U36JC#What_works_but_needs_tweaking") cannot be applied, because the path "..../libv4l/v4l1compat.so" is invalid on my system.
[/LIST]

[COLOR="Navy"]In addition[/COLOR], I had to do [this GRUB tweak(s)]("http://www.phoronix.com/scan.php?page=article&item=intel_i915_power&num=1") to regain normal acpitz-0 temperature around 50°C and good battery life again after upgrading to 11.10 from 11.04. Kernel 3.0.0-12-generic in 11.10 seems to have some problems with Sandy Bridge.

I use [*acpi_call*]("http://linux-hybrid-graphics.blogspot.com/") to turn off dedicated (Nvidia) graphics and make the notebook running just on integrated Intel graphics. I will play around with graphic issues and Nvidia later on, I do not need it now - as I am focused on long battery life for now.

```
$ uname -a
Linux crysmanoov 3.0.0-12-generic #20-Ubuntu SMP Fri Oct 7 14:56:25 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux

```

[Here are my GRUB boot options]("http://ubuntuforums.org/showpost.php?p=11364047&postcount=145").

PS: After solving ths problems... could this [Ubuntu Community Documentation]("https://help.ubuntu.com/community/Asus_U36SD") be updated to support 11.10, too, please?

--

---

### Post by crysman on 2011-10-18
> **nwadams said:**
> I hate to be a newb but where did you put the parameters. The battery life still isn't as good. I get like 5 hours now instead of 8...

into boot options in GRUB. [See here for more information]("https://help.ubuntu.com/community/Grub2"). I've created a new GRUB menu entry like this:

```
$ cat /etc/grub.d/40_custom
#!/bin/sh
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.

menuentry 'Ubuntu, with Linux 3.0.0-12-generic i915 hacks' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root 466b9306-8ceb-4da6-89aa-b1865130dfda
	#linux	/vmlinuz-3.0.0-12-generic root=UUID=3bcf2fa7-cf9d-4b55-8211-13c5f17f81bf ro  vga=771  quiet splash vt.handoff=7
	linux	/vmlinuz-3.0.0-12-generic root=UUID=3bcf2fa7-cf9d-4b55-8211-13c5f17f81bf ro i915.i915_enable_rc6=1 i915.i915_enable_fbc=1 i915.lvds_downclock=1
	initrd	/initrd.img-3.0.0-12-generic
}
```

And regarding to 8 hrs battery life... I don't think its real. Is it? I will test it some day, after I tweak the power consumption more deeply - with the help of [*powertop*]("http://www.linuxpowertop.org/").

--

---

### Post by AbtZ on 2011-10-19
> **nwadams said:**
> I hate to be a newb but where did you put the parameters. The battery life still isn't as good. I get like 5 hours now instead of 8...

The best way, IMO, to edit GRUB parameters is through the file /etc/default/grub. Find the line GRUB_CMDLINE_LINUX_DEFAULT="quiet splash" and add/remove whatever parameters you wish, for example:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash relatime"
```

Then save the file and run 
```
sudo update-grub
```

After a reboot, you should be all set :)

---

### Post by AbtZ on 2011-10-19
> **Awaking said:**
> While changing the virtual desktop u can see this funny effect (i use two monitors):
[[IMG]http://s013.radikal.ru/i323/1110/c7/b3ad8214391at.jpg[/IMG]](http://radikal.ru/F/s013.radikal.ru/i323/1110/c7/b3ad8214391a.png)

What you have there is a bug in Unity with multiple monitors -- not with the ASUS U36SD specifically.

---

### Post by Awaking on 2011-10-19
AbtZ, Yes of course, but it's pretty funny)
What really works good with multiple monitors it's KDE.

---

### Post by nwadams on 2011-10-19
> **crysman said:**
> 

And regarding to 8 hrs battery life... I don't think its real. Is it? I will test it some day, after I tweak the power consumption more deeply - with the help of [*powertop*]("http://www.linuxpowertop.org/").

--

8 hours battery life is legit in windows and 11.04 with light usage.

I applied the tips. It seems to help but the battery life is bad and I get tons of heat after a suspend/resume. So I will have to look into that.

---

### Post by jadahl on 2011-10-19
I updated the wiki page with some 11.10 info (from here, and my own install). Please do correct if you find an error :)

---

### Post by Awaking on 2011-10-19
Display output switch (Fn-F8 ) works both with 11.04 and 11.10

---

### Post by patrikt on 2011-10-20
Here is a easy guide on how to get two finger scolling to work in Ubuntu (works in 11.10). 

[http://mixeduperic.com/ubuntu/ubuntu-1004-how-to-setup-two-finger-scroll-on-laptop-touch-pad.html]("http://mixeduperic.com/ubuntu/ubuntu-1004-how-to-setup-two-finger-scroll-on-laptop-touch-pad.html")

---

### Post by jadahl on 2011-10-20
> **patrikt said:**
> Here is a easy guide on how to get two finger scolling to work in Ubuntu (works in 11.10). 

[http://mixeduperic.com/ubuntu/ubuntu-1004-how-to-setup-two-finger-scroll-on-laptop-touch-pad.html]("http://mixeduperic.com/ubuntu/ubuntu-1004-how-to-setup-two-finger-scroll-on-laptop-touch-pad.html")

You don't need to do it that way. You can just enable the option via the Mouse & Touchpad dialog in the System Settings. Worked for me both with 11.04 and 11.10.

---

### Post by haakon on 2011-10-22
In Kubuntu 10.11, two-finger scrolling works out of the box.

One thing that doesn't work, is waking up from hibernation. When I press the power button, the machine simply boots normally instead of waking up. Wakeup from suspend seems to work fine. Is there any fix for hibernation that I haven't seen?

---

### Post by jadahl on 2011-10-22
> **haakon said:**
> In Kubuntu 10.11, two-finger scrolling works out of the box.

One thing that doesn't work, is waking up from hibernation. When I press the power button, the machine simply boots normally instead of waking up. Wakeup from suspend seems to work fine. Is there any fix for hibernation that I haven't seen?

I haven't tried hibernation myself, just seen people reporting it working. If this is incorrect we should probably update the wiki.

Regarding your problem, did you try to wait for a magical number of minutes before trying to resume after hibernation? This is the only way I can make suspend work on my machine.

---

### Post by nwadams on 2011-10-22
> **jadahl said:**
> I haven't tried hibernation myself, just seen people reporting it working. If this is incorrect we should probably update the wiki.

Regarding your problem, did you try to wait for a magical number of minutes before trying to resume after hibernation? This is the only way I can make suspend work on my machine.

I never use hibernation but suspend seems to work for me without waiting. Although if I have certain things plugged in, my phone for instance it suspends for 1 second and then powers back on again...

---

### Post by crysman on 2011-10-23
> **nwadams said:**
> 8 hours battery life is legit in windows and 11.04 with light usage.

I applied the tips. It seems to help but the battery life is bad and I get tons of heat after a suspend/resume. So I will have to look into that.

OK, I've made a script which makes my U36SD drain only about 9W (measured by *powertop*), which **really brings me to 8 hours** of light usage. [The script is available here]("http://ubuntuforums.org/showpost.php?p=11382925&postcount=120"), please post updates there, if any (would be great).

---

### Post by crysman on 2011-10-24
> **jadahl said:**
> I updated the wiki page with some 11.10 info (from here, and my own install). Please do correct if you find an error :)

Please, add:
[LIST]
[*]webcam problem (upside down)
[*]fingerprint reader (not working) - although not every U36SD has the fingerprint reader, some (as mine) do, so it would be great to be fixed
[/LIST]

-- crysman

---

### Post by crysman on 2011-10-24
> **crysman said:**
> OK, I've switched to Xubuntu 11.10 and would like to update the information here.

What I see has been fixed and/or [COLOR="DarkGreen"]IS now working in 11.10[/COLOR]:
...

What [COLOR="DarkRed"]IS NOT working[/COLOR] in 11.10:
[LIST=1]
[*]these Fn combinations: F9 (touchpad disable) and F10 (mute).
Mute works just in direction -> mute. Second press - to unmute - keeps it muted. I've find out that, while muting, the Fn+F10 affects both the "HDA Intel PCH (Alsa mixer)"'s Master channel and "Playback: Internal Audio Analog Stereo (PulseAudio Mixer)"'s Master. BUT, while unmuting, it unmutes only the first one, leaving the second one muted. When I click the XFCE menu panel sound button and "Unmute", it unmutes both of them.
Any ideas?
[/list]
...

In addition, I had to do ...

...
[see the whole post here]("http://ubuntuforums.org/showpost.php?p=11363930&postcount=144")
...


Please, anybody has same problems with 1. ? Meaning unmute via Fn+10 not working? I am unable to fix it :( 

--crysman

---

### Post by adrien214 on 2011-10-27
> **crysman said:**
> OK, I've made a script which makes my U36SD drain only about 9W (measured by *powertop*), which **really brings me to 8 hours** of light usage. [The script is available here]("http://ubuntuforums.org/showpost.php?p=11382925&postcount=120"), please post updates there, if any (would be great).

The script looks impressive, I need to try that i915 thing. However, I just wanted to point out that powerTOP is as good as the command 

```
/proc/acpi/battery/BAT0/state
```

to estimate the power consumption. Also, I sometimes reach as low as 8,7W of power consumption, if I don't have much apps open, so I'm kind of wondering about the script... Sometimes, the power would jump and hangs to 24 or even 27W for no good reason though...

---

### Post by jadahl on 2011-10-27
Has anyone managed to get HDMI output working with resolution set to 1920x1080? It seems to work perfectly fine with the VGA port, but on the HDMI port I can only get 1360x768.

---

### Post by M@s on 2011-10-28
I've had some trouble with my Wifi ever since I installed 11.04. If I use the network only by web browsing, chatting etc it works quite well, but when I do a heavy load by downloading major files, it only works for a few minutes before it stops responding. It is still connected, but it is no longer responding and all transfer speeds drops to 0, web pages wont load. I have to reconnect to the network in order to get it working again for a few minutes before it freezes again.

Anyone with a solution?

---

### Post by looch on 2011-10-28
Is there a way to watch videos using vdpau with optimus?
And have anyone compared power and cpu usage while using VA-API and vdpau? Perhaps I could just stop on VA-API, though never used it..

---

### Post by adrien214 on 2011-10-28
> **M@s said:**
> I've had some trouble with my Wifi ever since I installed 11.04. If I use the network only by web browsing, chatting etc it works quite well, but when I do a heavy load by downloading major files, it only works for a few minutes before it stops responding. It is still connected, but it is no longer responding and all transfer speeds drops to 0, web pages wont load. I have to reconnect to the network in order to get it working again for a few minutes before it freezes again.

Anyone with a solution?

this is not a support thread for networking. but my best guess is that it's not your computer. can you try downloading from another network to confirm this diagnose?

---

### Post by jadahl on 2011-10-29
> **M@s said:**
> I've had some trouble with my Wifi ever since I installed 11.04. If I use the network only by web browsing, chatting etc it works quite well, but when I do a heavy load by downloading major files, it only works for a few minutes before it stops responding. It is still connected, but it is no longer responding and all transfer speeds drops to 0, web pages wont load. I have to reconnect to the network in order to get it working again for a few minutes before it freezes again.

Anyone with a solution?

I experienced this issue in 11.04 some times, but so far not in 11.10. Maybe you could experiment with the Live CD/USB stick to do some tests if the problem has been solved there?

---

### Post by M@s on 2011-11-02
> **jadahl said:**
> I experienced this issue in 11.04 some times, but so far not in 11.10. Maybe you could experiment with the Live CD/USB stick to do some tests if the problem has been solved there?It seems to be working on the 11.10 Live! My previous experiences with 11.10 hasn't been too good, but I'll give it another try. Thanks!

---

### Post by kirkley on 2011-11-05
> **crysman said:**
> ...
webcam - picture is upside-down (tested with *Camorama version 0.19*). [LD_PRELOAD trick]("https://help.ubuntu.com/community/Asus_U36JC#What_works_but_needs_tweaking") cannot be applied, because the path "..../libv4l/v4l1compat.so" is invalid on my system.--
...

I use [this trick ]("https://aeminium.org/slug/software/tips/skype-asus-flipped.html")to fix my webcam. Now my camera is not upside-down %)

---

### Post by jacek88 on 2011-11-06
First of all I'd like to thank you all for this thread. I was terrified about my battery lifetime when I've installed ubuntu 11.10 for the first time on my laptop. Fortunately it works much better now.

Anyway there is still one annoying issue which I can't manage to solve. Anytime I change brightness by fn keys it returns the default brightness after a while. For example, when I use the batter saving script written by one of you and set maximum brightness it comes back automatically to minimum brightness within 15 seconds. 

Have you ever encountered this problem ?

---

### Post by FrenkT on 2011-11-06
Hello, I'm new on this forum, and I've also been using Ubuntu for just a few weeks so I hope you could be patience. 

I'm using Ubuntu 11.10 on my u36sd, and I've been looking for a way to improve the battery life, and I tried the acpi_call, but this method just stopped the nvidia and needed to be used at every restart. 
So I read that Bumblebee tries to work like the nvidia optimus software on windows, but I don't understand the differences.
So my question are: if I want to improve the buttery lifetime, is bumblebee a good solution? At the same time, does bumblebee activate the nvidia when I run some application that needs it? 

Thanks

PS: I have another problem. I'm trying to change the command that launches Skype in order to fix the webcam problem. In Ubuntu 11.04 I did that through the System Preferences, but now I can't find that anymore. How can I do this using the Terminal?

---

### Post by icek on 2011-11-06
Hi, I installed ironhide and disabled nvidia card, then I added parameters to grub. Result is battery live cca 7:30. I can't find page where I found how to disable nvidia card, but maybe you figure it out when configuring ironhide.

---

### Post by torsades on 2011-11-07
Hi, I just bought my u36sd today. Although mine has the i7-2620, which is the only iteration sold in my country.

 Im looking forward to getting linux up and running on it soon. I tried ubuntu 11.10 on my netbook and didnt like unity or gnome3 and so defected to mint 11. Going to fire up mint on this beast too.
 
Great to see so many problems being fixed already. Looking forward to having the equivalent of optimus soon hopefully. Thanks a million to everyone for sorting out the issues.

---

### Post by stayfrosty555 on 2011-11-12
> **jacek88 said:**
> First of all I'd like to thank you all for this thread. I was terrified about my battery lifetime when I've installed ubuntu 11.10 for the first time on my laptop. Fortunately it works much better now.

Anyway there is still one annoying issue which I can't manage to solve. Anytime I change brightness by fn keys it returns the default brightness after a while. For example, when I use the batter saving script written by one of you and set maximum brightness it comes back automatically to minimum brightness within 15 seconds. 

Have you ever encountered this problem ?

Have you switched off "Dim display when idle" and "Reduce backlight brightness" under Power Management?

---

### Post by crysman on 2011-11-12
> **stayfrosty555 said:**
> Have you switched off "Dim display when idle" and "Reduce backlight brightness" under Power Management?

This is not the proper solution. We actually WANT dim display idle and reduced brightness. We need to figure out, how to make Ubuntu resore the same brightness level after...

I know that when changing brightness via
```
/sys/class/backlight/acpi_video*/brightness
```
(set it to <0,10>)

the brightness level is restored properly after dim idle display state. The problem occurs only when using FN+F[5|6] :(

Maybe there would be some way how to make FN+F[5|6] to change */sys/class/backlight/acpi_video*/brightness* files (?)

--
crysman

---

### Post by Fr4gg0r on 2011-11-12
Does someone has this fix [https://bugs.launchpad.net/ubuntu-release-notes/+bug/582809/comments/144](https://bugs.launchpad.net/ubuntu-release-notes/+bug/582809/comments/144) working on 11.10?
For me patch 203-xorg.conf.d_snippet.patch fails when running dpkg-buildpackage =/

---

### Post by adrien214 on 2011-11-15
my laptop is trying to **electrocute me** !!! It happens at both lower corners of the casing (on each sides on the trackpad)... anybody else ???? it's doing this constantly, on battery or AC. :confused:

edit: prolly some bad earthing in the electric system of the house.

---

### Post by jadahl on 2011-11-15
> **adrien214 said:**
> my laptop is trying to **electrocute me** !!! It happens at both lower corners of the casing (on each sides on the trackpad)... anybody else ???? it's doing this constantly, on battery or AC. :confused:

I have never noticed any such problems (using battery only, or on AC). Maybe ASUS support actually might be able to help you with this (if you strategically avoid the topic of Operating System choice).

---

### Post by jadahl on 2011-11-15
> **Fr4gg0r said:**
> Does someone has this fix [https://bugs.launchpad.net/ubuntu-release-notes/+bug/582809/comments/144](https://bugs.launchpad.net/ubuntu-release-notes/+bug/582809/comments/144) working on 11.10?
For me patch 203-xorg.conf.d_snippet.patch fails when running dpkg-buildpackage =/

Looks like someone made a PPA. See here: [https://bugs.launchpad.net/ubuntu-release-notes/+bug/582809/comments/275](https://bugs.launchpad.net/ubuntu-release-notes/+bug/582809/comments/275)

---

### Post by Darwichee on 2011-11-20
Yesterday i tried the ubuntu 11.10 for the first time, and i liked it ALOT, but the only problem i have right now is the optimus thing, because i also have the asus u36sd.

The only usefull guide i found, was this:

[http://www.ivegotavirus.com/blog/2011/11/06/how-to-get-optimus-working-on-ubuntu-11-10-oneiric/](http://www.ivegotavirus.com/blog/2011/11/06/how-to-get-optimus-working-on-ubuntu-11-10-oneiric/)

And i have to say that this looks hard to follow, and i don't know which guide is the best either. I've heard that ironhide is newer then bumblebee, so i quess ironhide is better?

I would be VERY thankfull if someone could show me a easy guide i could follow.

thanks

---

### Post by jadahl on 2011-11-20
> **Darwichee said:**
> Yesterday i tried the ubuntu 11.10 for the first time, and i liked it ALOT, but the only problem i have right now is the optimus thing, because i also have the asus u36sd.

The only usefull guide i found, was this:

[http://www.ivegotavirus.com/blog/2011/11/06/how-to-get-optimus-working-on-ubuntu-11-10-oneiric/](http://www.ivegotavirus.com/blog/2011/11/06/how-to-get-optimus-working-on-ubuntu-11-10-oneiric/)

And i have to say that this looks hard to follow, and i don't know which guide is the best either. I've heard that ironhide is newer then bumblebee, so i quess ironhide is better?

I would be VERY thankfull if someone could show me a easy guide i could follow.

thanks

Best is if you can try to follow some guide. Anyway, there is a chance that this could work:

```

sudo add-apt-repository ppa:mj-casalogic/ironhide
sudo apt-get update
sudo apt-get install ironhide

```

Then to play a game:
```

optirun thegame

```

---

### Post by Darwichee on 2011-11-20
> **jadahl said:**
> Best is if you can try to follow some guide. Anyway, there is a chance that this could work:

```

sudo add-apt-repository ppa:mj-casalogic/ironhide
sudo apt-get update
sudo apt-get install ironhide

```Then to play a game:
```

optirun thegame

```

Im not that  into these things so i think you'll have to explain. It's like the Windows CMD right? Instead the name is "Terminal", so i open it and copy the text you wrote, and just paste it and press enter?

thanks

---

### Post by jadahl on 2011-11-20
> **Darwichee said:**
> Im not that  into these things so i think you'll have to explain. It's like the Windows CMD right? Instead the name is "Terminal", so i open it and copy the text you wrote, and just paste it and press enter?

thanks

Yes, open the Terminal program. For every line I posted above you should copy paste it into the terminal and press Enter.

So for example, the first line from my previous post, copy paste the following into the terminal:
```
sudo add-apt-repository ppa:mj-casalogic/ironhide
```
Then press the enter key. It might ask you for your password. When the command has finished (you'll get the prompt (might be something like "user@host:directory $ ") you can paste the next command and press enter to run.


The last part is a bit more tricky, because you need to know how to run the program (read game) from command line. Check /usr/games/ if you find it there.

---

### Post by Darwichee on 2011-11-20
After everything i got to type it said at the end, ironhide is now confgured. How do i know if i did it right?

I know this sound stupid, but i've never done this before.

---

### Post by jadahl on 2011-11-20
> **Darwichee said:**
> After everything i got to type it said at the end, ironhide is now confgured. How do i know if i did it right?

I know this sound stupid, but i've never done this before.

If you manage to run a game with the optirun command, as I described, if the game runs faster than without it means it works.

---

### Post by Darwichee on 2011-11-20
> **jadahl said:**
> If you manage to run a game with the optirun command, as I described, if the game runs faster than without it means it works.

the thing is i don't play. But i still want the Optimus for programs that uses the nvidia graphic card, but is there not any test out there, where you can see if this does work?

Or can i properly install ironhide, because as i see it right now, it's only the optimus thing that keeping med with the win 7.

---

### Post by jadahl on 2011-11-20
> **Darwichee said:**
> the thing is i don't play. But i still want the Optimus for programs that uses the nvidia graphic card, but is there not any test out there, where you can see if this does work?

Or can i properly install ironhide, because as i see it right now, it's only the optimus thing that keeping med with the win 7.

I think if you run your program (be it game or anything else) with optirun as described, it will use the nvidia graphics card for OpenGL calls, thus, if the program works, it means that you are using the nvidia card.

There are no programs available that directly uses the nvidia card automatically (aka optimus thing) but any program can be made to use it via the optirun command.

(This discussion has gone a bit too off-topic (not related to U36SD) so I suggest you ask in some ironhide / bumblebee / optimus thread if you want to know more how these things currently work).

---

### Post by Fr4gg0r on 2011-11-21
> **jadahl said:**
> Looks like someone made a PPA. See here: [https://bugs.launchpad.net/ubuntu-release-notes/+bug/582809/comments/275](https://bugs.launchpad.net/ubuntu-release-notes/+bug/582809/comments/275)

I did
sudo add-apt-repository ppa:sergio91pt/synaptics+clickpads
and then followed these [https://help.ubuntu.com/community/Asus_U36SD](https://help.ubuntu.com/community/Asus_U36SD) steps. Wouldn't compile. :/
(I am on xubuntu 11.10)

I figured out that I can set the screen brightness with /sys/class/backlight/intel_backlight/brightness, the problem is, if I add "echo -n 600 > " to rc.local, it does not work, the value is probably overwritten after the script is executed. =/
Any idea how to fix that?


Btw: What discharge values to you get from powertop with screen on lowest brightness, wifi enabled, bluetooth disabled and "all other tweaks enabled"?

---

### Post by Niihau on 2011-11-22
> **Fr4gg0r said:**
> 
Btw: What discharge values to you get from powertop with screen on lowest brightness, wifi enabled, bluetooth disabled and "all other tweaks enabled"?

I have 8,6W
[http://img39.imageshack.us/img39/3910/capturedu20111122164010.png](http://img39.imageshack.us/img39/3910/capturedu20111122164010.png)

Does someone know how to disable the ambient light sensor?

---

### Post by cloutz on 2011-11-22
there are problems with 10.4 LTS?
or they are the same documented for 11.04, 12.04?

honestly i buyed u36sd for the long battery duration, so i think LTS is better than other version (it uses previous kernel, isn't it?)

Thanks, sorry for my bad english :D

---

### Post by torsades on 2011-11-22
My hibernate wasnt working properly. It would take ages on a blank screen and would require me to hit the power button a second time to sort of remind it. Then after logging in it would promptly logout again and require me to log in a second time.     

After a bit of googling i tried this solution to assign the swap partition to be used for hibernation, and it appears to have solved the problem.    

Source: [https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq) 
> 
[U]Activating the swap partition:
[/U] (If  your swap is on your primary hard drive, you don't need to do anything  here.) Now you need to find what partition your swap is on and what its  UUID is. UUID?! you say? Well that's the Universally Unique IDentifier  for the partition so you can reference it even if it's on a different  mount point from boot-to-boot due to adding disks, etc. 

[LIST=1]
[*]Pull up a terminal and run gksu gparted & and enter your root password. The & lets this process run while still giving you access to the command line.
[*]Right-click  on your swap partition and choose *Information*. You should see the  **Path** and **UUID** listed there. Keep this open for further  reference.
[*]Run gksu gedit /etc/fstab &  and look for the line that has *swap* in it. It should be the third  column, separated by spaces or tabs. You can either use the path or the  UUID to tell Linux where to find your swap partition. I recommend UUID  because it'll stay constant even if you move the partition around or the  disk somehow becomes sdb instead of sda or something like that. Make  the appropriate edits and save the file. Your line should look something  like this if you used UUID (with your UUID instead, of course):
[LIST]
[*]UUID=41e86209-3802-424b-9a9d-d7683142dab7 none swap sw 0 0
[*]or this if you used path: /dev/sda2 none swap sw 0 0
[/LIST]
 
[*]Save and reboot to make sure the new swap gets activated properly at startup
[/LIST]
_Making the swap partition work for hibernate: _
You only need to do this if you want to use your new, bigger swap partition to hibernate your computer. 

[LIST=1]
[*]Pull up a Terminal again and run cat /proc/swaps  and hopefully you see the path to your swap partition listed there. If  not chances are something went wrong in the steps above. Here's my  output:
[/LIST]
Filename                                Type            Size    Used    Priority /dev/sda2                               partition       2676732 73380   -1
[LIST=1]
[*]gksu gedit /etc/default/grub & to pull up the boot loader configuration
[*]Look for the line GRUB_CMDLINE_LINUX="" and make sure it looks like this (using your UUID of course) GRUB_CMDLINE_LINUX="resume=UUID=41e86209-3802-424b-9a9d-d7683142dab7" and save the file
[*]sudo update-grub and wait for it to finish
[*]gksu gedit /etc/initramfs-tools/conf.d/resume & and make sure its contents are resume=UUID=41e86209-3802-424b-9a9d-d7683142dab7 (with your UUID of course in place of mine). Save the file!
[*]sudo update-initramfs -u
[*]Reboot!
[/LIST]
Now you should be able to hibernate and resume!

---

### Post by torsades on 2011-11-23
Does anyone else get the brightness set to maximum after every single resume from sleep or hibernate? Is there a fix? Its really annoying to be blinded every time i resume.

---

### Post by Fr4gg0r on 2011-11-23
Anyone else having trouble to power off the laptop?
Killing all processes returns fail
then after "Will now halt" and "[xxxx] Power down." the screen stays on.

---

### Post by torsades on 2011-11-28
Nope, no problems shutting down. But there are still major issues with resuming from hibernating and sleep. It appears to be a ubuntu 11.10 problem. Ive tried xubuntu, kubuntu, pclinuxos and pinguy before finally settling on mint 12. (which is the most useable one imho)The same issues are present on all these variants. Id love for the hibernate issue to be solved because I use it alot.

By the way, does anyone else feel like the u36sd seems to randomly get really hot and has its fan constantly running while not really running any intensive processes in linux?  (didn't happen in win7) Only a restart seems to kill the fan and reduce the temperature

---

### Post by Chia-Hua Ho on 2011-11-29
I also encountered a similar problem. The laptop can hibernate, but we need to push the power button to turn it off. Although sometimes it wakes up correctly, other times it doesn't.

---

### Post by mbeltagy on 2011-12-01
I am running Kubuntu 11.10 64bit. I did the tweaks in the [wiki]("https://help.ubuntu.com/community/Asus_U36SD"), however I still have the following problems:
1. No audio recording
2. The camera does not flip the picture, the directory /usr/lib/i386-linux-gnu/libv4l/ does not exist on my system
3. After suspend, the usb 3 port does not work 
4. After suspend, I can not get the nvidia graphics to work. When I trying running optirun, I get ```
FATAL: Error inserting nvidia_current (/lib/modules/3.0.0-13-generic/updates/dkms/nvidia_current.ko): No such device
.
``` 

Any help is appreciated.

---

### Post by haakon on 2011-12-11
A strange problem has started to appear for me recently. In many applications, the window simply stops redrawing until I force it by alt-tabbing, moving something over the window etc. This happens in Konsole as well as in YouTube videos. Konsole continues to accept input, but it's not reflected in the window. Very annoying. I run just the intel graphics driver, and use Kubuntu 11.10. Any idea?

Edit: I think I solved it by upgrading the Intel driver, details here: [http://robbyx.net/blog/?p=275](http://robbyx.net/blog/?p=275)

Edit2: Today the problem returned, at least in YouTube, and Choqok :-( Probably in Konsole as well, if I use it for a while.

---

### Post by torsades on 2011-12-17
The sleep/hibernate issue appears to have been fixed somehow. I am happily running gnome shell 3.2 installed over xubuntu 11.10 and the resume from sleep is just as snappy as anyone could expect. 

Battery life is much improved and the laptop temperature is much reduced with the installation of the [jupiter applet.]("http://www.webupd8.org/2011/09/jupiter-applet-finally-available-for.html") It supposedly make the asus super hybrid engine work with linux.

Does anyone else experience random instances where the cursor goes crazy and vibrates wildly in the horizontal plane with varying amplitude for a few seconds or minutes at a stretch before aborting? I can't seem to see any pattern to it that might suggest a trigger. It isnt just a gnome shell problem because I experienced it with xfce and lxde too.

---

### Post by Awaking on 2011-12-30
Does anybody else have a trouble when CPU fan starts rotating at full power regardless of CPU temperature (48*C for example)? And even if you restart your PC it will not help. The only way is to shutdown it and startup again.

---

### Post by icek on 2011-12-31
I dont have this problem. But i recently switched from unity to gnome-shell and it seems like I got some extra batery life. Now with minimum brightness I get about 9 hours

---

### Post by Henri Lebesgue on 2012-01-04
After I did the 'High end graphics card(Nvidia)'-step alt-shift-tab is not working anymore. What to do?

---

### Post by jadahl on 2012-01-04
> **Henri Lebesgue said:**
> After I did the 'High end graphics card(Nvidia)'-step alt-shift-tab is not working anymore. What to do?

Follow the steps under "Desktop effects" here: [https://help.ubuntu.com/community/Asus_U36SD#Desktop_effects](https://help.ubuntu.com/community/Asus_U36SD#Desktop_effects)

For making actual use of the nvidia card read the section after that.

---

### Post by Henri Lebesgue on 2012-01-04
> **jadahl said:**
> Follow the steps under "Desktop effects" here: [https://help.ubuntu.com/community/Asus_U36SD#Desktop_effects](https://help.ubuntu.com/community/Asus_U36SD#Desktop_effects)

For making actual use of the nvidia card read the section after that.

When I'm running the command in 'Desktop effect' I get this "E: Unable to locate package nvidia". And the section after 'Desktop effect' is what made the alt-shift-tab to stop working. I was only able to run unity 2d before that.

I don't follow acctually. What in those steps would make my alt-shift-tab work in unity again?

---

### Post by jadahl on 2012-01-04
> **Henri Lebesgue said:**
> When I'm running the command in 'Desktop effect' I get this "E: Unable to locate package nvidia". And the section after 'Desktop effect' is what made the alt-shift-tab to stop working. I was only able to run unity 2d before that.

I don't follow acctually. What in those steps would make my alt-shift-tab work in unity again?

Make that: "sudo apt-get remove nvidia-current" instead. Don't know why the wiki states nvidia, because I have no such package either. Please confirm if it works, so I can change the page.

Before trying to experiment with the high end graphics card I suggest getting 3D acceleration working using the Intel card first.

---

### Post by Henri Lebesgue on 2012-01-04
> **jadahl said:**
> Make that: "sudo apt-get remove nvidia-current" instead. Don't know why the wiki states nvidia, because I have no such package either. Please confirm if it works, so I can change the page.

Before trying to experiment with the high end graphics card I suggest getting 3D acceleration working using the Intel card first.

Okay, I tried it. And it worked. But for what purpose did you tell me to do it? What am I supposed to do to get the 3D acceleration to work? New to ubuntu, been doing alright so far. But these graphics drivers is pretty tricky.

---

### Post by jadahl on 2012-01-04
> **Henri Lebesgue said:**
> Okay, I tried it. And it worked. But for what purpose did you tell me to do it? What am I supposed to do to get the 3D acceleration to work? New to ubuntu, been doing alright so far. But these graphics drivers is pretty tricky.

With worked, do you mean that you get Unity (not Unity 2D) working as well? (Together with the blacklist stuff).

FYI, unity2d and unity are two different programs that look very similar. unity is built with "compiz" while unity2d is a QT application.

---

### Post by Henri Lebesgue on 2012-01-04
> **jadahl said:**
> With worked, do you mean that you get Unity (not Unity 2D) working as well? (Together with the blacklist stuff).

FYI, unity2d and unity are two different programs that look very similar. unity is built with "compiz" while unity2d is a QT application.

From start I was using Unity2D, without even knowing about Unity. When I installed IronHide it changed to Unity. The problem I have is that alt-shift-tab doesn't work in Unity, but works perfectly in Unity2D.

After I ran your command my battery consumption went higher so I still have something left to do with graphics drivers. The command removed IronHide as well.

But you mentioned something about 3D acceleration. You recommend me to do it before installing IronHide. I don't understand exactly what IronHide does, but some instructions says that you are supposed to remove all nvidia drivers before installing it. Am I mistaken here?

I really appreciate your help!

---

### Post by jadahl on 2012-01-04
> **Henri Lebesgue said:**
> From start I was using Unity2D, without even knowing about Unity. When I installed IronHide it changed to Unity. The problem I have is that alt-shift-tab doesn't work in Unity, but works perfectly in Unity2D.

After I ran your command my battery consumption went higher so I still have something left to do with graphics drivers. The command removed IronHide as well.

But you mentioned something about 3D acceleration. You recommend me to do it before installing IronHide. I don't understand exactly what IronHide does, but some instructions says that you are supposed to remove all nvidia drivers before installing it. Am I mistaken here?

I really appreciate your help!

I suppose Unity don't have that key-binding by default, while Unity 2D has. There are some inconsistencies between the two.

I recommend at least getting 3D acceleration using the Intel card working first. If you can run Unity (not 2D) you already succeeded with that, since it requires 3D acceleration to function. Full 3D acceleration using the nvidia card won't work right now, but you can selectively run programs (read games) so you'll still be able to run them.

Personally I don't run IronHide (I did, but found it more buggy than the alternative) but Bumblebee. If you want to run Bumblebee but already have IronHide installed, follow the instructions here: [https://launchpad.net/~bumblebee/+archive/stable](https://launchpad.net/~bumblebee/+archive/stable) . I also noticed that I forgot adding one of the commands to the wiki (usermod). Fixed now.

---

### Post by Henri Lebesgue on 2012-01-04
> **jadahl said:**
> I suppose Unity don't have that key-binding by default, while Unity 2D has. There are some inconsistencies between the two.

I recommend at least getting 3D acceleration using the Intel card working first. If you can run Unity (not 2D) you already succeeded with that, since it requires 3D acceleration to function. Full 3D acceleration using the nvidia card won't work right now, but you can selectively run programs (read games) so you'll still be able to run them.

Personally I don't run IronHide (I did, but found it more buggy than the alternative) but Bumblebee. If you want to run Bumblebee but already have IronHide installed, follow the instructions here: [https://launchpad.net/~bumblebee/+archive/stable]("https://launchpad.net/%7Ebumblebee/+archive/stable") . I also noticed that I forgot adding one of the commands to the wiki (usermod). Fixed now.

Okey! How do I get that for my intel card, how do I know which one I'm using? Ubuntu3D is working now, am I using the nvidia card? I have only done the 'nvidia high end' step and ran your command after that. Everything else is clean as a new installation of ubuntu.

---

### Post by jadahl on 2012-01-04
> **Henri Lebesgue said:**
> Okey! How do I get that for my intel card, how do I know which one I'm using? Ubuntu3D is working now, am I using the nvidia card? I have only done the 'nvidia high end' step and ran your command after that. Everything else is clean as a new installation of ubuntu.

It's using the Intel card. Currently there is no way of using the nvidia card for running the whole desktop environment (I think). If you run "optirun glxgears" in a terminal, does a glxgears window show up? If it say "command not found" or something, install mesa-utils. If so, you should be able to use the nvidia card via that command.

---

### Post by Henri Lebesgue on 2012-01-04
> **jadahl said:**
> It's using the Intel card. Currently there is no way of using the nvidia card for running the whole desktop environment (I think). If you run "optirun glxgears" in a terminal, does a glxgears window show up? If it say "command not found" or something, install mesa-utils. If so, you should be able to use the nvidia card via that command.

The command you gave me before removed Ironhide. I can't run optirun without Ironhide?

---

### Post by jadahl on 2012-01-04
> **Henri Lebesgue said:**
> The command you gave me before removed Ironhide. I can't run optirun without Ironhide?

Both Bumblebee and Ironhide provides a command named optirun. To install bumblebee, follow the guide here: [https://launchpad.net/~bumblebee/+archive/stable](https://launchpad.net/~bumblebee/+archive/stable)

---

### Post by Henri Lebesgue on 2012-01-06
> **jadahl said:**
> Both Bumblebee and Ironhide provides a command named optirun. To install bumblebee, follow the guide here: [https://launchpad.net/~bumblebee/+archive/stable]("https://launchpad.net/%7Ebumblebee/+archive/stable")

I tried to install Bumblebee but seems like it needs some further configuration after installation? At least my battery consumption stayed the same. So I installed Ironhide. Don't know how well it works but with it I have twice as long battery life so I'm happy : ))

---

### Post by Henri Lebesgue on 2012-01-08
Windows7 had one power mode called office mode. I feel like my computer is making a bit to much noise, does anyone have any tips on how to make it more quiet in ubuntu 11.10?

---

### Post by adrien214 on 2012-01-16
Henri, I'm gonna sum up what you need to do to get a decent 11.10 power 
consumption and low noise/heat:

```
sudo gedit /etc/hdparm.conf
```

and insert the following bloc of code at the bottom of the file ([source]("http://ubuntuforums.org/showthread.php?t=1705406")):

```
/dev/sda {
	    apm = 254
	    apm_battery = 254
	}
```

Then type ([source]("http://www.phoronix.com/scan.php?page=article&item=intel_i915_power&num=1")):

```
sudo gedit /etc/default/grub
```

add a blank space after 'splash' and 

```
i915.i915_enable_rc6=1 i915.i915_enable_fbc=1 i915.lvds_downclock=1 pcie_aspm=force
```

between the quotes in the line

RUB_CMDLINE_LINUX_DEFAULT="quiet splash"

then save the file and type in the command line: 

```
sudo update-grub
```

*EDIT : reboot your machine.

You should get a power consumption between 8 and 10W with reduced noise and heat, if you have installed Ironhide. Even with BT and WLAN enabled.

---

### Post by fuduntu on 2012-01-16
> **adrien214 said:**
> Henri, I'm gonna sum up what you need to do to get a decent 11.10 power 
consumption and low noise/heat:

```
sudo gedit /etc/hdparm.conf
```

and insert the following bloc of code at the bottom of the file ([source]("http://ubuntuforums.org/showthread.php?t=1705406")):

```
/dev/sda {
	    apm = 254
	    apm_battery = 254
	}
```

Then type ([source]("http://www.phoronix.com/scan.php?page=article&item=intel_i915_power&num=1")):

```
sudo gedit /etc/default/grub
```

add a blank space after 'splash' and 

```
i915.i915_enable_rc6=1 i915.i915_enable_fbc=1 i915.lvds_downclock=1 pcie_aspm=force
```

between the quotes in the line

RUB_CMDLINE_LINUX_DEFAULT="quiet splash"

then save the file and type in the command line: 

```
sudo update-grub
```

*EDIT : reboot your machine.

You should get a power consumption between 8 and 10W with reduced noise and heat, if you have installed Ironhide. Even with BT and WLAN enabled.

Add Jupiter and it might drop down to 6-8.

---

### Post by adrien214 on 2012-01-16
> **fuduntu said:**
> Add Jupiter and it might drop down to 6-8.



Speaking of Jupiter. Do you happen to know if all the possibilities in lesswatts.org are implemented in the app? Or is there some more stuff that needs to be done manually?

---

### Post by fuduntu on 2012-01-16
> **adrien214 said:**
> Speaking of Jupiter. Do you happen to know if all the possibilities in lesswatts.org are implemented in the app? Or is there some more stuff that needs to be done manually?

Most of them.  There is always "more" to do, nothing gets you 100% of the way there, not even Jupiter.

---

### Post by adrien214 on 2012-01-18
> **torsades said:**
> Does anyone else get the brightness set to maximum after every single resume from sleep or hibernate? Is there a fix? Its really annoying to be blinded every time i resume.

there is a [script]("http://blog.ishans.info/2011/09/25/set-brightness-automatically-at-the-startup-in-linux/") for setting the screen brightness at startup I don't know if it will work on resume. The thing is that regardless if I have a script doing something on startup or if I have a specific screen settings, ubuntu reverts to values I don't want every.single.time.

---

### Post by _karo on 2012-01-23
Ok, I need help. I've been running 11.04 on my U36SD with an external monitor and a TV connected to the HDMI output via a HDMI splitter and it's been working fine. Sometimes I want to use my laptop on the couch and then I'll have to disconnect the HDMI cable, and the laptop monitor goes crazy after that - vertical stripes, gray noise-like texture, or it just goes black. I usually just restart X when I do this, and the computer realizes it's not connected to another monitor anymore. Same thing when I plug the HDMI cable back in.

Yesterday I tried something different and turned the TV/monitor off from the Monitor Preferences before disconnecting the cable. It didn't prevent the laptop screen mess up after disconnecting the HDMI cable, so I just thought to myself, no need to do that again... But now, when I have reconnected the HDMI cable, it looks like Ubuntu doesn't even realize the HDMI port exists! When I press "detect monitors" in Monitor Preferences the external monitor doesn't get detected, and even xrandr says nothing about the HDMI port. Here is the xrandr output:

```
Screen 0: minimum 320 x 200, current 1366 x 768, maximum 8192 x 8192
LVDS1 connected 1366x768+0+0 (normal left inverted right x axis y axis) 293mm x 165mm
   1366x768       60.0*+
   1360x768       59.8     60.0  
   1024x768       60.0  
   800x600        60.3     56.2  
   640x480        59.9  
VGA1 disconnected (normal left inverted right x axis y axis)

```

What can I do to get my HDMI output back? I've rebooted the computer several times, with and without the HDMI cable connected, with and without the HDMI splitter, etc. etc. Is my only option to reinstall Ubuntu? All help is greatly appreciated!

---

### Post by Awaking on 2012-01-26
Does anybody have idea how can I use nVidia card instead Intel all the time long? Ubuntu interface is pretty laggy while using two monitors with Intel GPU.

---

### Post by crysman on 2012-01-26
> **Awaking said:**
> Does anybody have idea how can I use nVidia card instead Intel all the time long? Ubuntu interface is pretty laggy while using two monitors with Intel GPU.

Negative. I am running dualmonitor normally. Even flash videos do not lag. I am using XUbuntu, though... not Ubuntu.

-- crysman

---

### Post by torsades on 2012-01-27
Btw guys bumblebee 3.0 works perfectly. The jump in fps for the graphics tests is phenomenal. Its much easier to set up than ironhide which i was using previously.

[http://www.webupd8.org/2012/01/bumblebee-30-released-nvidia-optimus.html](http://www.webupd8.org/2012/01/bumblebee-30-released-nvidia-optimus.html)

On another note, does anyone else experience horrendous mouse jumpiness only when using the trackpad? I've not noticed this for a long time because ive been using a mouse but today when i took the laptop on the road, it became so bad to the point of being unusable. Rebooting temporaily fixes it but then i just comes back after a few minutes. Initially the cursor is just extremely jumpy so it is impossible to click on anything. Then the cursor becomes impossible to move in the vertical direction. Its really exasperating. Any ideas?

---

### Post by torsades on 2012-01-27
My above mentioned jumpy cursor problem goes away after i enter these commands, which i presume reset the mouse. 

```
sudo rmmod psmouse 
sudo modprobe psmouse
```Based on the fact that it can be solved this way, does anyone have any idea what could be causing the problem or how i may automate this resetting in the event it occurs?

Edit: Gahh i spoke too soon. It just comes back after a couple of minutes. Damnit

---

### Post by r4b00f on 2012-01-29
The USB3 port still doesn't work properly for me in 11.10. Initially it did not work at all,
but after adding the boot options pci=nomsi,noaer, it started working. Working until the
computer goes to sleep or hibernates. I skimmed this thread, but I can't recall seeing anything looking similar to my problem.

After resuming from a suspended state it seems that the mouse I have plugged in still 
receives power, but nothing registers in syslog when plugging it in and out. Same thing with a thumb drive.

Any ideas where to start looking?

---

### Post by torsades on 2012-02-03
I have the same problem with the usb 3.0 port on the right side. I dont have any usb 3.0 devices but sometimes the mouse fails to get recognised when plugged in there after resuming from suspend/hibernate.  The only solution seems to be a reboot or simply to plug the mouse in the usb 2.0 port on the left. Time to get a long usb cable.

There are a few other annoyances that occur especially after resuming from a suspended state such as having to log in twice in a row, but what really drives me nuts is the jumpy cursor when using the trackpad after resuming. Goes away for a while on a fresh boot up. Two-finger scrolling seems to trigger it. I've tried turning off the option to disable trackpad when typing. Then it just becomes less frequent.

---

### Post by r4b00f on 2012-02-04
Are you by any chance using xorg-edgers (or similar) packages for X.org?

I tried to get an old program running by upgrading to a bleeding edge X.org 
version and Intel drivers. Not only did the program not work, but the newer
drivers totally destroyed the performance of Intel graphics (glxspheres at 2-3 fps vs.
ca. 56 normally) Also the trackpad became a lot more jumpy as a consequence, but it 
was consistent, not manifesting intermittently.

---

### Post by demarsjcd on 2012-02-04
Concerning the mouse problem, I have not had an issue with it thankfully however on Win7 there was no two finger scroll, the mouse was very inconsistennt, and the one finger scroll was very very bad.  I fixed it by getting rid of synaptics driver and using a mac driver.  Not sure if this is any help at all, just throwing it out there.  Heres the site I found the solution on:
[http://forum.notebookreview.com/asus/626006-u36sd-touchpad-issue.html](http://forum.notebookreview.com/asus/626006-u36sd-touchpad-issue.html)

---

### Post by demarsjcd on 2012-02-05
I know this is way off topic but I installed ubuntu onto my external hard drive and everything worked perfect.  I later tried installing archlinux onto the same external drive.  The only thing I did different that time was that I made the mistake of installing grub onto the SSD which over wrote the windows booter.  Do any of you guys know either how to restore the windows booter or get rid of grub on sda drive?  thanks.  BTW I got grub error 21 and I've looked all over the internet.

---

### Post by r4b00f on 2012-02-11
Good news (for me atleast)

I got the USB3.0 suspend / hibernate problem solved. After checking the other Asus hibernate related threads on the forum it seemed that the problem is not model specific, but rather a more general issue. The script in this blog post did it for me:

[http://thecodecentral.com/2011/01/18/fix-ubuntu-10-10-suspendhibernate-not-working-bug](http://thecodecentral.com/2011/01/18/fix-ubuntu-10-10-suspendhibernate-not-working-bug)

I also had an issue with flash content being really choppy and laggy. This seems to be related to the Intel GPU drivers rather than straight to Adobe, so I'd expect this problem to be fixed for good some time in the future. As for now, I had to modify grub command line parameters slightly.

Adding i915.semaphores=1 made the problem go away at first, but after waking up from sleep the problem was back, so I experimented a bit and found out that setting i915.i915_enable_fbc=0 solved the issue. For completeness' sake, here's the full list of boot 
parameters I use:

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash pci=nomsi,noaer i915.i915_enable_rc6=1 i915.i915_enable_fbc=0 i915.lvds_downclock=1 i915.semaphores=1 pcie_aspm=force"

Finally everything seems to be working nicely.

EDIT: I spoke too soon. The flash problem is back after the computer was in sleep mode over the night. Crap.

---

### Post by r4b00f on 2012-02-17
Recent update came with some changes to xserver-xorg packages, now it seems that
either the update, or upgrading the xserver-xorg-video-intel package to 2.17 via a PPA
helped with the choppy flash problem. 

However, the xserver-xorg update totally destroyed glxspheres performance on the intel
GPU: instead of the normal ca. 55 fps, I now get barely 3 fps. I already had the newer intel
driver installed when the xserver updated, so I'm thinking that the problem is not the
intel driver package, but some other xserver component. Unfortunately I have no idea
which. Any suggestions welcome, also regarding the correct place to report this as a bug.

---

### Post by demarsjcd on 2012-02-22
Is this thread still being updated?  I ended up getting rid of Ubuntu because I had a bad problem with the graphics stop drawing all the time.  There was big triangular glitches popping up all the time.  I ended up trying out Linux mint and haven't had one problem except when ever I'm watching a video or playing an online game it gets really hot

---

### Post by nwadams on 2012-02-24
my fault for not updating the main post. But the information in the wiki is good.

Good news in 12.04. the webcam isn't flipped anymore and we can use the fn+f9 button to turn the touchpad on and off. 

I think with the sandy bridge kernel fixes and bumblebee 3 we can get decent battery life out of the system now too.

---

### Post by mbeltagy on 2012-03-04
> **r4b00f said:**
> Good news (for me atleast)

I got the USB3.0 suspend / hibernate problem solved. After checking the other Asus hibernate related threads on the forum it seemed that the problem is not model specific, but rather a more general issue. The script in this blog post did it for me:

[http://thecodecentral.com/2011/01/18/fix-ubuntu-10-10-suspendhibernate-not-working-bug](http://thecodecentral.com/2011/01/18/fix-ubuntu-10-10-suspendhibernate-not-working-bug)

I also had an issue with flash content being really choppy and laggy. This seems to be related to the Intel GPU drivers rather than straight to Adobe, so I'd expect this problem to be fixed for good some time in the future. As for now, I had to modify grub command line parameters slightly.

Adding i915.semaphores=1 made the problem go away at first, but after waking up from sleep the problem was back, so I experimented a bit and found out that setting i915.i915_enable_fbc=0 solved the issue. For completeness' sake, here's the full list of boot 
parameters I use:

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash pci=nomsi,noaer i915.i915_enable_rc6=1 i915.i915_enable_fbc=0 i915.lvds_downclock=1 i915.semaphores=1 pcie_aspm=force"

Finally everything seems to be working nicely.

EDIT: I spoke too soon. The flash problem is back after the computer was in sleep mode over the night. Crap.
I had the flash problem too. It mainly had to do with ndiswrapper. I often ended up typing 
> killall ndiswrapper
and refreshing the webpage that has with the flash content. 
However, recently with updates from a week ago, "ndiswrapper" has disappeared and browser/flash integration is much better.

---

### Post by nwadams on 2012-03-04
> **mbeltagy said:**
> I had the flash problem too. It mainly had to do with ndiswrapper. I often ended up typing 

and refreshing the webpage that has with the flash content. 
However, recently with updates from a week ago, "ndiswrapper" has disappeared and browser/flash integration is much better.

this will be the native 64bit flash support, not requiring ndiswrapper any more.

---

### Post by nwadams on 2012-03-05
has anyone figured out how to get the fn+f5/fn+f6 brightness controls to interact with ubuntu. They work at a hardware level and adjust the brightness but don't interact in the OS.

---

### Post by sanz on 2012-03-07
> **nwadams said:**
> has anyone figured out how to get the fn+f5/fn+f6 brightness controls to interact with ubuntu. They work at a hardware level and adjust the brightness but don't interact in the OS.

Yes. Fn+F5/6 controls the brightness correctly, but the adjustment made them is ignored by OS. I had to disable the auto-dim function. But every time of boot, I have to decrease the brightness manually.

---

### Post by nwadams on 2012-03-07
> **sanz said:**
> Yes. Fn+F5/6 controls the brightness correctly, but the adjustment made them is ignored by OS. I had to disable the auto-dim function. But every time of boot, I have to decrease the brightness manually.

ya, thats as far as I am too. I'm going to play with it once 12.04 comes out.

---

### Post by saunterteo on 2012-03-10
hi all.
I've just bought an asus u36sd and I'm trying to install ubuntu 11.10 on it.
I wrote the iso image on a usb pen with LiLi usb creator and unetbootin.
I managed to boot from usb, but after choosing "install ubuntu" the screen went black and nothing happened.
Can anybody help me?
Thank you everybody!

---

### Post by nwadams on 2012-03-10
> **saunterteo said:**
> hi all.
I've just bought an asus u36sd and I'm trying to install ubuntu 11.10 on it.
I wrote the iso image on a usb pen with LiLi usb creator and unetbootin.
I managed to boot from usb, but after choosing "install ubuntu" the screen went black and nothing happened.
Can anybody help me?
Thank you everybody!

try clicking the try ubuntu button. there will be a install icon on the desktop to install from there.

---

### Post by saunterteo on 2012-03-10
thank you for the help, actually I solved by changing some options in the bios.

---

### Post by nwadams on 2012-03-10
> **saunterteo said:**
> thank you for the help, actually I solved by changing some options in the bios.

good luck with everything. I recommend checking out 12.04 as soon as possible as well. Lots of fixes including built in RC6 enable with the new kernel so better power management. Also install bumblebee or some other method of turning off the nvidia graphics so your battery life is decent.

---

### Post by foxy123 on 2012-03-17
Does anyone know how to disable bluetooth permanently. I cannot find any options in BIOS.

---

### Post by nwadams on 2012-03-20
> **foxy123 said:**
> Does anyone know how to disable bluetooth permanently. I cannot find any options in BIOS.

As far as I know there is no way to permanently disable the bluetooth.

---

### Post by Barbalras on 2012-03-20
Hi everyone!

I've just installed ubuntu on my U36SD. I followed the instructions to install bumblebee and apparently it went fine.
Anyway, when I connect the laptop to a monitor through VGA, the image looks a little blurrier compared to my other laptop's VGA's output. Have you noticed this? Is there anything that can be done?

Right now that's the only thing that it bugging me about this laptop

---

### Post by krustenBrot on 2012-03-22
> Hi everyone!

I've just installed ubuntu on my U36SD. I followed the instructions to install bumblebee and apparently it went fine.
Anyway, when I connect the laptop to a monitor through VGA, the image  looks a little blurrier compared to my other laptop's VGA's output. Have  you noticed this? Is there anything that can be done?

Right now that's the only thing that it bugging me about this laptop 	

Hey Barbalras

had the same issue with my U36SD running Win7. Could not find a fix, but its all good when using the hdmi port.

It seems to be either the VGA port itself (concerning all models - build quality?, some strange graphic card issues?)  or some faulty models like mine or yours.
Anyone else experienced this?
Have you tried contacting ASUS? What did they say?

---

### Post by Barbalras on 2012-03-22
Nice! Seems I'm not alone. Today I'm going to buy an hdmi cable

thank you krustenBrot

EDIT: I got the hdmi cable and image got much better. It looks perfect

---

### Post by krustenBrot on 2012-03-22
I finally figured out how to use the additional key above F1 to switch power modes ( similiar to "power 4 gear" on win7 ) using Jupiter.

given that you already got Jupiter installed and running:

1.go to "All Settings" - "Keyboard" - "Shortcuts" Tab **OR** simply type "keyboard" into to Dash search and click on the Icon -> then click the "Shortcuts" tab.
2. Click on "Custom Shortcut" - Click the **+** on the bottom left 
3. Name it whatever you like, copy the following command into the "command" field: 
> sudo /usr/lib/jupiter/scripts/cpu-control 4. Assign a key by clicking on "Disabled" - press the key
 ...and thats it.

Additions:
You can also assign different commands as given in the Jupiter Wiki. see: [http://sourceforge.net/apps/mediawiki/jupiter/index.php?title=Keybindings](http://sourceforge.net/apps/mediawiki/jupiter/index.php?title=Keybindings)

I personally dont like the long timeout of the notification pop-up especially if you are switching 2 modes up or down. 
Fixing this requires a "patched NotifyOSD" - for instructions see: > [http://www.webupd8.org/2010/07/patched-notifyosd-updates-option-to.html](http://www.webupd8.org/2010/07/patched-notifyosd-updates-option-to.html)After installing these, type into a terminal:
> gksu gedit /usr/lib/jupiter/scripts/notify gedit opens up the script file search for the following lines:
> ....$ICON **-t 700**.....the number behind **"-t" - **in my case 700  - defines the amount of time the notification will display in milliseconds.

Hope you enjoy your Asus u36sd and Ubuntu. I do. :) 
Thanks for this awesome thread ;) ):P

---

### Post by johnitsa on 2012-03-28
I've manage to pretty much set up everything properly on my new U36SD. Thanks to the community guide and this thread, battery is up to somewhere around 6 hours.

There's only one thing that's just weird. The libs requried to fix the reversed webcam issue on oneiric pretty much fixed it for everything except skype. While in apps like Cheese the webcam looks perfectly fine, I'm still upside down.

I'm just curious if any of you guys experienced this until now and if (and how) you've managed to fix it. It's no rush to get it fixed though, since I read the problem's been fixed for precise pangolin.

---

### Post by nwadams on 2012-03-28
> **johnitsa said:**
> I've manage to pretty much set up everything properly on my new U36SD. Thanks to the community guide and this thread, battery is up to somewhere around 6 hours.

There's only one thing that's just weird. The libs requried to fix the reversed webcam issue on oneiric pretty much fixed it for everything except skype. While in apps like Cheese the webcam looks perfectly fine, I'm still upside down.

I'm just curious if any of you guys experienced this until now and if (and how) you've managed to fix it. It's no rush to get it fixed though, since I read the problem's been fixed for precise pangolin.

Check out the webcam section [https://help.ubuntu.com/community/Asus_U36JC](https://help.ubuntu.com/community/Asus_U36JC)

Also I believe this is fixed by default in 12.04.

---

### Post by johnitsa on 2012-03-29
> **nwadams said:**
> Check out the webcam section [https://help.ubuntu.com/community/Asus_U36JC](https://help.ubuntu.com/community/Asus_U36JC)

Also I believe this is fixed by default in 12.04.

Thanks for your reply. That's what I was saying: that I installed libv4l, but for some reason it doesn't seem to fix the issue, even with LD_PRELOAD.

It's alright anyways. I'll wait for 12.04 to go stable and then upgrade.

---

### Post by msaleiro on 2012-03-29
Hi! I'm having issues with the USB3.0 port in Asus U36S with Ubuntu 11.10. I have tested it with a pen drive and it works ok (did not test the data transfer speeds but it works) but when I connect a Logitech C510 webcam I only get rubbish data. It recognizes the webcam, I can open a video stream with VLC but the images that I get are complete rubbish. The camera auto white balance is working because when i cover the camera with my hand the "rubbish" gets darker. If I connect it in a USB 2.0 port the camera works fine. I tried to connect the same camera to a USB3.0 port with Ubuntu 11.10 in a n Asus ZenBook and it works fine too. I tried that thing with pci=nomsi and didn't notice any change. Anyone has any clue on how to solve it? (I really need to use the webcam in this port because I'll need two webcams simultaneously streaming and I'll need to put them in different USB buses to make it work)

---

### Post by SfShab on 2012-03-30
I recently purchased an Asus U36SD laptop. At start up I receive an  error message about the Splendid video enhancement. I have downloaded  the drivers for it, and have tried several times to uninstall and  reinstall them, but the process freezes after a while. Any idea what the problem is?

---

### Post by Naugas on 2012-04-13
> **saunterteo said:**
> hi all.
I've just bought an asus u36sd and I'm trying to install ubuntu 11.10 on it.
I wrote the iso image on a usb pen with LiLi usb creator and unetbootin.
I managed to boot from usb, but after choosing "install ubuntu" the screen went black and nothing happened.
Can anybody help me?
Thank you everybody!
> **saunterteo said:**
> thank you for the help, actually I solved by changing some options in the bios.What did you change? I'm having the same problem and can't see any settings that should matter... :confused:

I tried the daily build too, but same problem - just a blank screen and no apparent disk activity after selecting "Try Ubuntu without installing". It just freezes.

edit: this was with 64-bit builds. Just tried a live x86 version and it ran fine.

edit 2: solution: boot through bios - uefi boot is broken, see post at [http://ubuntuforums.org/showpost.php?p=11863942&postcount=261](http://ubuntuforums.org/showpost.php?p=11863942&postcount=261)

---

### Post by mp.maghribi on 2012-04-14
> **johnitsa said:**
> Thanks for your reply. That's what I was saying: that I installed libv4l, but for some reason it doesn't seem to fix the issue, even with LD_PRELOAD.

It's alright anyways. I'll wait for 12.04 to go stable and then upgrade.

Hi. I used ubuntu 11.10 on my u36s and have upgraded to latest update provided by ubuntu and google. And now my webcam view on google+ fixed (it's not displayed upside down anymore).

---

### Post by Naugas on 2012-04-14
I've been trying 64-bit live usb 11.10 and daily builds, but it just freezes up after selecting "Try Ubuntu without installing". x86 versions runs normally.

Is this happening to the rest of you?

(I used unetbootin to create the usb flash drives, seemed to work fine.)

---

### Post by nwadams on 2012-04-15
> **Naugas said:**
> I've been trying 64-bit live usb 11.10 and daily builds, but it just freezes up after selecting "Try Ubuntu without installing". x86 versions runs normally.

Is this happening to the rest of you?

(I used unetbootin to create the usb flash drives, seemed to work fine.)

i have no issues with 64bit live versions. what bios settings are you using? Also have you tried a different usb stick? I have found that one of my usb sticks doesn't like to boot properly sometimes. 

good luck

---

### Post by Naugas on 2012-04-16
Default bios settings except moving up my flash drive in the boot list. But really, what is there to change? See my post a little bit further up asking someone that apparently changed something...

I tried two different sticks, both boot with 32 bit 11.10 and daily 12.04.

Any suggestions of how to narrow this down and test for different problems? I guess I have to be able to run 64-bit things while in some way boot up in 32-bit...? Or maybe try some simpler 64-bit recovery linux versions and see if that works first?


edit: solution: boot through bios - uefi boot is broken, see post at [http://ubuntuforums.org/showpost.php?p=11863942&postcount=261](http://ubuntuforums.org/showpost.php?p=11863942&postcount=261)

---

### Post by nwadams on 2012-04-16
> **Naugas said:**
> Default bios settings except moving up my flash drive in the boot list. But really, what is there to change? See my post a little bit further up asking someone that apparently changed something...

I tried two different sticks, both boot with 32 bit 11.10 and daily 12.04.

Any suggestions of how to narrow this down and test for different problems? I guess I have to be able to run 64-bit things while in some way boot up in 32-bit...? Or maybe try some simpler 64-bit recovery linux versions and see if that works first?

ya. i'm really not sure what you could have changed because it just works for me. I've never actually tried a 32 bit image but I'm sure it would work as well. 

In your first post you said it freezes after selecting try ubuntu without installing. Is this in the GUI or on the command line that you make that selection? 

Also what is your model, u36sd-a1 or what? I'm just trying to see what cpu and such you have, maybe there is some unique hardware issue somewhere.

---

### Post by Awaking on 2012-04-20
> **adrien214 said:**
> Henri, I'm gonna sum up what you need to do to get a decent 11.10 power 
consumption and low noise/heat:

```
sudo gedit /etc/hdparm.conf
```and insert the following bloc of code at the bottom of the file ([source]("http://ubuntuforums.org/showthread.php?t=1705406")):

```
/dev/sda {
        apm = 254
        apm_battery = 254
    }
```Then type ([source]("http://www.phoronix.com/scan.php?page=article&item=intel_i915_power&num=1")):

```
sudo gedit /etc/default/grub
```add a blank space after 'splash' and 

```
i915.i915_enable_rc6=1 i915.i915_enable_fbc=1 i915.lvds_downclock=1 pcie_aspm=force
```between the quotes in the line

RUB_CMDLINE_LINUX_DEFAULT="quiet splash"

then save the file and type in the command line: 

```
sudo update-grub
```*EDIT : reboot your machine.

I did all this steps. 
Then I have installed Jupiter and Bumblebee. Turn on the power saving mode. And now I have a problem:
When I connect power cable to the notebook, the message "Power savings mode" pops up. After that interface becomes very laggy.
If I disconnect power cable, the same message pops up and then (~after 20 sec. ) system interface becomes fast. .
Why interface perfomance is higher with battery powered?
The same result even in "Maximum perfomance mode" and "Power on demand mode".
I notice that interface was fast in Live-CD mode and became laggy after installing.

---

### Post by Naugas on 2012-04-21
> **nwadams said:**
> ya. i'm really not sure what you could have changed because it just works for me. I've never actually tried a 32 bit image but I'm sure it would work as well. 

In your first post you said it freezes after selecting try ubuntu without installing. Is this in the GUI or on the command line that you make that selection? 

Also what is your model, u36sd-a1 or what? I'm just trying to see what cpu and such you have, maybe there is some unique hardware issue somewhere.

I haven't been poking around anything more, but it should be grub it boots up in. And it is indeed the a1 version, if that is to any help. 8 GB memory.

---

### Post by nwadams on 2012-04-21
> **Awaking said:**
> I did all this steps. 
Then I have installed Jupiter and Bumblebee. Turn on the power saving mode. And now I have a problem:
When I connect power cable to the notebook, the message "Power savings mode" pops up. After that interface becomes very laggy.
If I disconnect power cable, the same message pops up and then (~after 20 sec. ) system interface becomes fast. .
Why interface perfomance is higher with battery powered?
The same result even in "Maximum perfomance mode" and "Power on demand mode".
I notice that interface was fast in Live-CD mode and became laggy after installing.

try without jupiter running/installed. Are you using 12.04 or 11.10?

---

### Post by Naugas on 2012-04-22
OK, got the 64-bit live usb version to work now, apparently it wasn't the default bios settings I have used. I have been trying too boot using uefi and not through the old plain bios. I had no idea something else than bios even existed...

Removing the usb disk from the boot priority list in the boot section of the bios, removing the uefi boot option, rebooting, then going to the save and exit part on the bios settings and going for the usb disk in the boot selection there did the trick. It booted up in unetbootin's boot menu, and though it took a while to start up, I'm now writing from the live system. No graphics problems or anything else so far.

---

### Post by nwadams on 2012-04-22
> **Naugas said:**
> OK, got the 64-bit live usb version to work now, apparently it wasn't the default bios settings I have used. I have been trying too boot using uefi and not through the old plain bios. I had no idea something else than bios even existed...

Removing the usb disk from the boot priority list in the boot section of the bios, rebooting, then going to the save and exit part on the bios settings and going for the usb disk in the boot selection there did the trick. It booted up in unetbootin's boot menu, and though it took a while to start up, I'm now writing from the live system. No graphics problems or anything else so far.

glad to see that you got it working. Let me know how your installation goes

---

### Post by Azyx on 2012-04-23
> **Naugas said:**
> 
Removing the usb disk from the boot priority list in the boot section of the bios, removing the uefi boot option, rebooting, then going to the save and exit part on the bios settings and going for the usb disk in the boot selection there did the trick.

Where do i find to remove UEFI-booting in BIOS/UEFI?

---

### Post by Naugas on 2012-04-23
I don't know what your bios settings looks like, but on mine there is an option at the very top of the "boot" section where I can enable/disable uefi boot.

Note that I still experienced a problem even if it was disabled when the usb device was left in the boot priority list (I didn't confirm this, but it worked the next time when I had removed it), that's why I point out that step in my description.

---

### Post by Azyx on 2012-04-25
> **Naugas said:**
> I don't know what your bios settings looks like, but on mine there is an option at the very top of the "boot" section where I can enable/disable uefi boot.

Note that I still experienced a problem even if it was disabled when the usb device was left in the boot priority list (I didn't confirm this, but it worked the next time when I had removed it), that's why I point out that step in my description.

I cannot find it anywere, have searched in EZ-mode and Advanced mode. A'm I bind or may it be that you don't have a chois? The manual is here:
[http://www.manualowl.com/m/Asus/E45M1-M-PRO/Manual/262972](http://www.manualowl.com/m/Asus/E45M1-M-PRO/Manual/262972)

..Or is it Force BIOS???

Can not find how I not select the SD-card with UEFI, that in the UEFI/BIOS (they call it boot BIOS and UEFI..very confusing..

Cheers

PS. When I installed 11.10, it seems to bee as 'normal BIOS' cos the boot SATA-disk, are not marked as UEFI, as the liveUSB in UEFI/BIOS on the machine.

---

### Post by johnitsa on 2012-04-26
> **johnitsa said:**
> I've manage to pretty much set up everything properly on my new U36SD. Thanks to the community guide and this thread, battery is up to somewhere around 6 hours.

There's only one thing that's just weird. The libs requried to fix the reversed webcam issue on oneiric pretty much fixed it for everything except skype. While in apps like Cheese the webcam looks perfectly fine, I'm still upside down.

I'm just curious if any of you guys experienced this until now and if (and how) you've managed to fix it. It's no rush to get it fixed though, since I read the problem's been fixed for precise pangolin.

So, just upgraded to 12.04 and the webcam problem still hasn't gone. Aside from that, I managed to lose the capability to use any keyboard shortcuts with the Super key (note that I've seen a fix for unity, but it doesn't seem to work for gnome-shell).

Anybody else still experiencing the flipped webcam issue in 12.04? Would it make sense to whipe it and do a clean install?

---

### Post by Azyx on 2012-04-27
> **Naugas said:**
> I don't know what your bios settings looks like, but on mine there is an option at the very top of the "boot" section where I can enable/disable uefi boot.

Note that I still experienced a problem even if it was disabled when the usb device was left in the boot priority list (I didn't confirm this, but it worked the next time when I had removed it), that's why I point out that step in my description.


How do I take away UEFI tags on the USB-memory?

---

### Post by johnitsa on 2012-04-27
> **johnitsa said:**
> So, just upgraded to 12.04 and the webcam problem still hasn't gone. Aside from that, I managed to lose the capability to use any keyboard shortcuts with the Super key (note that I've seen a fix for unity, but it doesn't seem to work for gnome-shell).

Anybody else still experiencing the flipped webcam issue in 12.04? Would it make sense to whipe it and do a clean install?
Nevermind the webcam issue. The libv4l-0 now magically works. I was hoping there won't be any need for LD_PRELOAD in 12.04, but I can live with it :)

---

### Post by nwadams on 2012-04-27
> **johnitsa said:**
> Nevermind the webcam issue. The libv4l-0 now magically works. I was hoping there won't be any need for LD_PRELOAD in 12.04, but I can live with it :)

so it works perfectly or it needs LD_PRELOAD? I haven't tested skype, but chrome worked properly for me a few days before release with beta.

---

### Post by johnitsa on 2012-04-27
Unfortunately skype still needs LD_PRELOAD. Chrome, on the other hand, handles the webcam just fine (tested with the google talk plugin).

---

### Post by nwadams on 2012-04-27
> **johnitsa said:**
> Unfortunately skype still needs LS_PRELOAD. Chrome, on the other hand, handles the webcam just fine (tested with the google talk plugin).

of course...stupid skype. at least the LD_PRELOAD fix works

---

### Post by foxy123 on 2012-04-28
Did you guys update through the Update Manager? Do you have Bumblebee installed? I have updated my other Asus laptop (K53) but it did not go well so I had to do fresh install.

---

### Post by nwadams on 2012-04-28
> **foxy123 said:**
> Did you guys update through the Update Manager? Do you have Bumblebee installed? I have updated my other Asus laptop (K53) but it did not go well so I had to do fresh install.

I just did a clean install. Installed bumblebee. used [http://thecodecentral.com/2011/01/18/fix-ubuntu-10-10-suspendhibernate-not-working-bug](http://thecodecentral.com/2011/01/18/fix-ubuntu-10-10-suspendhibernate-not-working-bug) instead of the wiki instructions for suspend. (steps one and two in the link) and suspend + usb3.0 works great. 

Overall everything works for me. Those were the only tweaks I've done. However I do not have stock wifi/bluetooth or hdd or ram so you might need extra tweaks for some of those.

---

### Post by bstr on 2012-05-11
I guys,
I have bought an ASUS U36S which has both the integrated video card and  the Nvidia GeForce 610M. I have installed ubuntu 12.04 and there is no  way to make use of the Nvidia drivers. I read a lot in the web and it  seems to me that there is no possibility to run the Nvidia  because I can not disable the intel card form the BIOS.
Actually I am interested in using the Nvidia card for computations only  (CUDA C etc) not games, not 3D. I am aware that one possibility to use the Nvidia card is  to install Bumblebee, but I gues that it is not suitable for my  purposes.
Do you have any suggestions other than running under Windows?
Bests,
Bustra

---

### Post by haakon on 2012-05-11
I can't seem to get USB3 working on my U36SD. I have a Western Digital MyPassport USB3 disk, and when I connect it to the USB3 port, it is powered on but never mounted.

lsusb says:
```

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
```

I have 12.04, pretty much stock, no bumblebee or anything like that. How do I get USB3 working?

---

### Post by adrien214 on 2012-05-12
Bustra, 
I remember a thread on the nvidia dev forums about a guy who successfully ran CUDA jobs with Ironhide/Bunblebee but I cannot seem to find it anymore.

---

### Post by adrien214 on 2012-05-12
haakon,

can you post the outpu of 
```
lscpi -v | grep "USB 3.0" 
```
and if nothing shows up just 
```
lspci 
```
and copy/paste the paragraph for the USB 3.0 controller?

Also, I just tried my external LaCie USB 3.0 in 12.04 and it works out of the box (live session, others have reported it to work fine as well, see above). What I need to do to have my external drive working is to first power the device by plugging in the extra USB 2.0 power cable and wait a few seconds and then plug the USB 3.0. You might wanna try this is you have extra power supply capability for your Passport as well.

---

### Post by haakon on 2012-05-12
> **adrien214 said:**
> haakon,

can you post the outpu of 
```
lscpi -v | grep "USB 3.0" 
```
and if nothing shows up just 
```
lspci 
```
and copy/paste the paragraph for the USB 3.0 controller?

Nothing did show up for "USB 3.0". Here's the entire output of lspci:

```
00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200/2nd Generation Core Processor Family PCI Express Root Port (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
00:16.0 Communication controller: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 (rev 05)
00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 05)
00:1c.0 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 (rev b5)
00:1c.1 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 2 (rev b5)
00:1c.3 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 4 (rev b5)
00:1d.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 (rev 05)
00:1f.0 ISA bridge: Intel Corporation HM65 Express Chipset Family LPC Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 6 Series/C200 Series Chipset Family 6 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller (rev 05)
01:00.0 VGA compatible controller: NVIDIA Corporation GF119 [GeForce GT 520M] (rev a1)
03:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
```

I've tried grepping around dmesg, but only see references to USB 2.0 and high-speed. I've tried modprobing various modules, and looked through BIOS to see if there's anything to enable, but I can't find anything.

Here are also the parts about USB in lshw:

```
-usb:0
             description: USB controller
             product: 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:16 memory:df608000-df6083ff
*-usb:1
             description: USB controller
             product: 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:23 memory:df607000-df6073ff

```

> **adrien214 said:**
> Also, I just tried my external LaCie USB 3.0 in 12.04 and it works out of the box (live session, others have reported it to work fine as well, see above). What I need to do to have my external drive working is to first power the device by plugging in the extra USB 2.0 power cable and wait a few seconds and then plug the USB 3.0. You might wanna try this is you have extra power supply capability for your Passport as well.

This drive has only one USB port and is supposed to get all its power from that, but thanks for the suggestion.

---

### Post by johnitsa on 2012-05-12
The USB3.0 port works for me after I went through the steps on the _[community page for the U36SD](https://help.ubuntu.com/community/Asus_U36SD#USB_3.0)_.

The only issue that I still have with it is that it randomly decides not to work after the laptop's been in sleep, but it gets fixed after a reboot.

> **haakon said:**
> I can't seem to get USB3 working on my U36SD. I have a Western Digital MyPassport USB3 disk, and when I connect it to the USB3 port, it is powered on but never mounted.

lsusb says:
```

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
```

I have 12.04, pretty much stock, no bumblebee or anything like that. How do I get USB3 working?

---

### Post by haakon on 2012-05-12
> **johnitsa said:**
> The USB3.0 port works for me after I went through the steps on the _[community page for the U36SD](https://help.ubuntu.com/community/Asus_U36SD#USB_3.0)_.

I tried with pci=nomsi,noaer (even if it says it's only for 11.04), but it made no difference.

---

### Post by bstr on 2012-05-14
> **adrien214 said:**
> Bustra, 
I remember a thread on the nvidia dev forums about a guy who successfully ran CUDA jobs with Ironhide/Bunblebee but I cannot seem to find it anymore.
Thank you very much. I searched on the web but I did not find something.
However, for those interested in runnig CUDA stuff with Bunblebee, here it comes my solution:
-install cudatoolkit and gpucomputingsdk;
-install Bunblebee;
(I must say that, so far, I am not able to compile the deciceQuery script wich tells you if everything is all right with your Nvidia card. )
-compile your file.cu with nvcc (e.g nvcc file.cu -o out.o)
 -run out.o with optirun ./out.o
Bests,
Bstr

---

### Post by adrien214 on 2012-05-14
Haakon, 

the controller usb-0 is fine but the one controlling the usb 3.0 port (usb-1) should be using the **xhci** driver and not the **ehci** like in your case, that's the problem, I belive but I have noclue how to fix this, maybe google "xhci ehci USB 3.0 driver" or something like that.

---

### Post by lemurian on 2012-05-18
I've also run into trouble with the USB 3 port. Before I try a solution, I want to post for posterity some of the symptoms I've been experiencing so that if someone else runs into the same problems, they'll have an idea of what is causing it.

If I plug my Logitec G11 keyboard into my USB 3 port, I get the following symptoms:

1. I get a kworker process eating the CPU up to about 75%.

2. Running "perf top" shows the kernel spending its time as follows:

```

             samples  pcnt function                            DSO
             _______ _____ ___________________________________ _________________

             4740.00 26.9% acpi_os_read_port                   [kernel.kallsyms]
             2768.00 15.7% acpi_ex_system_memory_space_handler [kernel.kallsyms]
             1387.00  7.9% acpi_os_write_port                  [kernel.kallsyms]
             1202.00  6.8% acpi_ns_search_one_scope            [kernel.kallsyms]
              420.00  2.4% acpi_ns_check_for_predefined_name   [kernel.kallsyms]
              342.00  1.9% intel_idle                          [kernel.kallsyms]
              284.00  1.6% __ticket_spin_lock                  [kernel.kallsyms]
              225.00  1.3% kmem_cache_alloc                    [kernel.kallsyms]

```

Unplugging the keyboard does nothing.

Workaround: To get rid of the runaway kworker process, I put the laptop to sleep and resume.

Just like haakon, my USB 3 port is driven by ehci instead of xhci.

---

### Post by emilflygare on 2012-05-20
Hi

I'm relatively new to Ubuntu and definitely new to these forums.
Since the upgrade to Precise, i haven't been able to put my asus u36sd to sleep. Hibernate mode doesn't work either.

Both those things worked fine under 11.10. I have followed the instructions on the Ubuntu help page regarding the problem with the USB buses, without any luck.

So my question is if some of you have any ideas to what might be the problem? I have read everything posted in this thread since the launch of 12.04 but if the solution was mentioned sometime before that, I apologize.

---

### Post by adrien214 on 2012-05-21
Hi Emil, please follow the howto [here]("http://thecodecentral.com/2011/01/18/fix-ubuntu-10-10-suspendhibernate-not-working-bug"). It's quite straighforward but don't hesitate to post if you encounter any trouble.

---

### Post by emilflygare on 2012-05-21
I have followed the instructions in the link without any success. Sleep and hibernate still doesn't work. :(

Do you have any other ideas? It is rather annoying to have to power off the computer every time I need the battery life.

---

### Post by adrien214 on 2012-05-22
Hi Emil, 
not sure what happened here but it seems there are at least three version of the script around the thread...

this is the one I am running:

```
BUSES="0000:00:1a.0 0000:00:1d.0"
XHCIBUSES="0000:04:00.0"

case "${1}" in
    hibernate|suspend)
        # Switch USB buses off
        for bus in $BUSES; do
            echo -n $bus | tee /sys/bus/pci/drivers/ehci_hcd/unbind
        done
        for bus in $XHCIBUSES; do
            echo -n $bus | tee /sys/bus/pci/drivers/xhci_hcd/unbind
        done
        ;;
    resume|thaw)
        # Switch USB buses back on
        for bus in $BUSES; do
            echo -n $bus | tee /sys/bus/pci/drivers/ehci_hcd/bind
        done
        for bus in $XHCIBUSES; do
            echo -n $bus | tee /sys/bus/pci/drivers/xhci_hcd/bind
        done
        ;;
esac
```

the rest is the same as in the howto.

---

### Post by emilflygare on 2012-05-22
I erased a file in /etc/pm/sleep.d/ and that solved the problem and now it sleeps like a kitten :)

Thank you for the link adrien

---

### Post by demontager on 2012-05-23
I used suspend script as described in wiki. Laptop goes to suspend well now, but power button LED continue blinking and this bit annoying, is any way to remove blinking ?  I like normal hibernate functionality when everything off, but hibernate not available. I use Gnome 3.

BTW. How to use left top button ? I pressed nothing happened, assume it servers for power mode changing.

---

### Post by johnitsa on 2012-05-24
Here's how you set up the power mode switcher button: [http://ubuntuforums.org/showthread.php?p=11786225#post11786225](http://ubuntuforums.org/showthread.php?p=11786225#post11786225)

---

### Post by demontager on 2012-05-24
I tried Jupiter and set cpu-control for top left button, seems works ok, but notification persist in bottom bar. Anyway I decided to remove this bindings because cpu power managed fine by self, when i use browsing or reading CPU remains at 800 Mhz.
  Any ideas about blinking power LED ?

---

### Post by johnitsa on 2012-05-24
I don't think the blinking led is something you can control. As far as I know, it doesn't have anything to do with any OS that you're using, but it's tightly connected with some motherboard circuitry.

But please correct me if I'm wrong :)

---

### Post by csmggl on 2012-05-24
Hi everyone, I installed Precise on my u36sd, i still didn't read all the thread, but on my machine multimedia keys and volume keys works fine, the suspend worked following the instruction on the wiki page.
What doesn't work in the brightness, which remains alway at maximum, and using (Fn+) F5 &F6 key affects the brightness but i can't see the notification... 
I still didn't try usb 3

---

### Post by johnitsa on 2012-05-25
Your best bet for now is to go to *System Settings > Brightness and Lock* and uncheck the *Dim screen to save power* option, as pointed before by sanz.

This way, the brightness doesn't get reset every few minutes. What I also did was to change the brightness level from the same settings screen to a value I usually work with, so that I don't have do decrease the brightness manually after each boot.

> **sanz said:**
> Yes. Fn+F5/6 controls the brightness correctly, but the adjustment made them is ignored by OS. I had to disable the auto-dim function. But every time of boot, I have to decrease the brightness manually.

---

### Post by krustenBrot on 2012-05-25
Hi everyone,

since i updated to precise everytime i reboot my screen resolution is set to 1024x768 and i have to change it manually. Anyone happens to have the same issue? Any idea how to fix this?

Greetings

//edit: Nevermind it somehow got fixed with the last update :)

---

### Post by crysman on 2012-05-26
> **johnitsa said:**
> Your best bet for now is to go to *System Settings > Brightness and Lock* and uncheck the *Dim screen to save power* option, as pointed before by sanz.

This way, the brightness doesn't get reset every few minutes. What I also did was to change the brightness level from the same settings screen to a value I usually work with, so that I don't have do decrease the brightness manually after each boot.

Hi, I've been experiencing the same problem, so what I did was that I wrote a short script:
```

#! /bin/bash
# set brightness

if ! [[ $1 =~ ^[0-9]+$ ]]; then
	echo " usage: $0 <0-10>"
	exit 1
fi

if [[ ( $1 -gt 10 ) || ( $1 -lt 0 ) ]]; then
	echo " usage: $0 <0-10>"
	exit 1
fi

blevel=$1
echo -n "setting brightness to $blevel"
echo "0%"
sudo blevel=$blevel sh -c 'for i in /sys/class/backlight/acpi_video*/brightness; do echo -n $blevel > $i; done'

```

So I can use some display power management and system always returns to the script-set value.

#crysman

---

### Post by demontager on 2012-05-27
Guys, is someone noticed that maximum CPU frequency stays not more than 2 400 Mhz ? I tried to play Left 4 Dead 2 and Oil Rush, and CPU not rising. I assume that Turbo Boost not working, is it ?

---

### Post by krustenBrot on 2012-06-02
Does anybody know how to resume from suspend without pushing the power button? Just opening the lid?

---

### Post by johnitsa on 2012-06-03
Just push any other button on your keyboard? :)

---

### Post by krustenBrot on 2012-06-03
> **johnitsa said:**
> Just push any other button on your keyboard? :)

you're right! How was i able to miss that? :)
Thanks.  :)

But i was wondering if there is a config file somewhere to resume as soon as the lid is opened without pushing ANY button?

---

### Post by johnitsa on 2012-06-03
You can read the lid state from:```
/proc/acpi/button/lid/*/state
```

but I doubt that you can get anything to search for state changes while your laptop is actually in sleep. *(i.e. I have no idea how or if that could work)*

---

### Post by krustenBrot on 2012-06-04
After extensive googling based on your suggestion:
> **johnitsa said:**
> /proc/acpi/button/lid/*/state

i discovered that it seems to be a very popular problem, if you look at

```
/proc/acpi/wakeup
```you can enable devices which are responsible for responding to input in a suspended state.
Usually you can fidn something like 
```
LID0       S3           *disabled
```change it to **enabled* and it should work.

found that on WOL threads with a few additions you have to make but these are irrelevant right now because: there isn't a LID entry on my U36 or it is somehow called different e.g. HDEF,PEGx?

//edit: Could someone with mad bash skills take a look at:  */etc/acpi/lid.sh . *From what i understand the script is asking for the lid state (*So theres definitely something to handle the lid why isn't it in /proc/acpi/wakeup?*) if its closed its going into the if ... if not the else... is going to happen ...

---

### Post by jadahl on 2012-06-08
For the record, I have reported a bug that I have experienced since I first got this computer:

 Resume results in a reboot if one tries to resume soon after suspending.

I don't know if (m)any other experience the same bug, but anyway, here it is:
[https://bugs.launchpad.net/ubuntu/+source/pm-utils/+bug/1010337](https://bugs.launchpad.net/ubuntu/+source/pm-utils/+bug/1010337)

---

### Post by adrien214 on 2012-06-11
> **jadahl said:**
> 

 Resume results in a reboot if one tries to resume soon after suspending.



this is a variation of an old classic.
However, I just came acorss this GRUB parameter : 

**elevator=deadline**

My laptop feels faster altogether. Did anybody else try it?

---

### Post by davejg on 2012-07-03
Hi!

I have an ASUS U36SG. I think it is very similar to the U36SD, but with i7. (if not, excuse me for
the off-topic)

I've a lot of problem with my battery. I've tried all.
Rc6, kernel 3.4-rc6, bumblebee... but my notebook consume always 15/20W (tested
with powerstat.

Can someone help me?
I don't know what to do now...

Thank you very much!
David

---

### Post by patrikt on 2012-07-04
Hi!

I've noticed that my U36SD is getting really hot with just normal use, e.g. browsing web. The problem grew when I updated to Ubuntu 12.04. Before, I used Win 7 and didn't notice this heat problem at all.

Anyone else has this problem? I wonder if it could be a setting in Ubuntu that not triggers the fans or something like that?

---

### Post by cenaar on 2012-07-07
> **patrikt said:**
> Hi!

I've noticed that my U36SD is getting really hot with just normal use, e.g. browsing web. The problem grew when I updated to Ubuntu 12.04. Before, I used Win 7 and didn't notice this heat problem at all.

Anyone else has this problem? I wonder if it could be a setting in Ubuntu that not triggers the fans or something like that?

Yup, I have the same problem and I came here to figure out why. The battery does not last very long - max 1.5-2 hours with normal usage like web browsing or watching video (running only VLC).

The fan seems to be running constantly and after a while the air flowing out of the fan is very hot, as is the surfaces surrounding the fan.

---

### Post by crysman on 2012-07-08
> **cenaar said:**
> Yup, I have the same problem and I came here to figure out why. The battery does not last very long - max 1.5-2 hours with normal usage like web browsing or watching video (running only VLC).

The fan seems to be running constantly and after a while the air flowing out of the fan is very hot, as is the surfaces surrounding the fan.

The answer is already here somewhere. It is very probably because of the incorrect settings. I would suggest:
[LIST]
[*]install *lm-sensors* and watch the temperature (*watch 'sensors | grep temp'*) - my system is around 52 °C on normal activity, it goes above 58 only on higher CPU/GPU usage.
[*]make a fresh latest (12.04) Ubuntu install
[*]try the power hints - boot with *i915.i915_enable_rc6=1* (but should not be necessary on 12.04)
[*]install *bumblebee* to optimize graphic cards power and so temperature
[/LIST]

This is what works for my ASUS U36SD running Xubuntu 12.04. Bumblebee and newest kernel is crucial. If you do not have newest kernel you should boot with that i915 option...

#crysman

---

### Post by Flapse on 2012-07-11
Hey! I've, after some trouble i might say, managed to install ubuntu some months ago. The problem was mainly due to something with BIOS and booting. Now I want to install the latest Ubuntu 12.04, but is unable to boot from USB or SD-card. I'm planning to call asus about this, but do you think it's BIOS related or hardware? The USB/SD card ports work otherwise...

Thanks

---

### Post by crysman on 2012-07-12
> **Flapse said:**
> Hey! I've, after some trouble i might say, managed to install ubuntu some months ago. The problem was mainly due to something with BIOS and booting. Now I want to install the latest Ubuntu 12.04, but is unable to boot from USB or SD-card. I'm planning to call asus about this, but do you think it's BIOS related or hardware? The USB/SD card ports work otherwise...
Thanks

Hi, on my ASUS U36SD I have to make some adjustments in BIOS every time I want to boot from USB flash. BTW, I don't think booting from a memory card is possible - use USB flash instead.

---

### Post by krustenBrot on 2012-07-17
Anyone got the USB 3.0 port running under 12.04?

---

### Post by crysman on 2012-07-18
> **krustenBrot said:**
> Anyone got the USB 3.0 port running under 12.04?

On my U36SD it works out of the box - no special settings required. I had made a fresh Xubuntu 12.04 install and it just worked... Before, on 11.10, I remember I had to make some adjustments, but it's not actual any more.

#crysman

---

### Post by cenaar on 2012-07-19
> **crysman said:**
> The answer is already here somewhere. It is very probably because of the incorrect settings. I would suggest:
[LIST]
[*]install *lm-sensors* and watch the temperature (*watch 'sensors | grep temp'*) - my system is around 52 °C on normal activity, it goes above 58 only on higher CPU/GPU usage.
[*]make a fresh latest (12.04) Ubuntu install
[*]try the power hints - boot with *i915.i915_enable_rc6=1* (but should not be necessary on 12.04)
[*]install *bumblebee* to optimize graphic cards power and so temperature
[/LIST]

This is what works for my ASUS U36SD running Xubuntu 12.04. Bumblebee and newest kernel is crucial. If you do not have newest kernel you should boot with that i915 option...

#crysman

Hm, OK. After my post I went on to Linux Mint. But I have the same issue - or, perhaps it's an issue just to me. Right now, for instance, my laptop feels unacceptably hot, but **watch 'sensors | grep temp' **says it's 53.0 °C. Oh well, thanks anyway! I'm still happy having learned about the **watch** command (:

---

### Post by ntesla123 on 2012-07-21
I don't know if this has been answered, but how do I get wired network connections to work?

I have ubuntu 12.04, and there is no reaction when I plug in a network cable.

---

### Post by adrien214 on 2012-07-21
> **ntesla123 said:**
> I don't know if this has been answered, but how do I get wired network connections to work?

I have ubuntu 12.04, and there is no reaction when I plug in a network cable.

That ain't normal. Even the most basic laptop from back in 2000 would run ubuntu with LAN support out of the box (my experience). Are you certain there is a working LAN at the other end of your RJ45 cable? Please report the output of the two following commands (Ctrl-Alt-T to open the terminal, then select txt woth mouse and right click to copy):

```
lspci | grep Ethernet
ifconfig | grep -A 5 eth0
```

---

### Post by crysman on 2012-07-24
> **cenaar said:**
> 

Hm, OK. After my post I went on to Linux Mint. But I have the same issue - or, perhaps it's an issue just to me. Right now, for instance, my laptop feels unacceptably hot, but **watch 'sensors | grep temp' **says it's 53.0 °C. Oh well, thanks anyway! I'm still happy having learned about the **watch** command (:

Hello again,
and have you successfully installed *bumblebee*? Because NVIDIA graphic card likes to make your computer's internals hot...

In which particular location(s) is your U36SD hot? Left to touchpad?

#crysman

---

### Post by Awaking on 2012-08-14
Does anybody have a trouble when CPU fan starts rotating at full power regardless of CPU temperature (48*C for example)? And even if you restart your PC it will not help. The only way is to shutdown it and startup again.

---

### Post by crysman on 2012-08-25
> **Awaking said:**
> Does anybody have a trouble when CPU fan starts rotating at full power regardless of CPU temperature (48*C for example)? And even if you restart your PC it will not help. The only way is to shutdown it and startup again.

Unfortunately, yes :( I had no problems with the fan speed before, but now it behaves like you said - CPU fan starting to rotate at maximum speed regardless to CPU temperature (even at 48*C), then slowly returning back to quiet, then a bit below a minute remains quiet and then repeat..

I do not know what happened, it is really annoying :( Maybe it is connected with some actualization? We definitely need more users and some tests...

What a pitty, this wonderful notebook CAN be quiet - and had been for a long time!

#crysman

---

### Post by foxy123 on 2012-08-26
I wonder if anyone successfully turned U36jc into a wifi hotspot? I tried all how-tos I have managed to find to no avail.

---

### Post by crysman on 2012-08-28
> **crysman said:**
> Unfortunately, yes :( I had no problems with the fan speed before, but now it behaves like you said - CPU fan starting to rotate at maximum speed regardless to CPU temperature (even at 48*C), then slowly returning back to quiet, then a bit below a minute remains quiet and then repeat..

I do not know what happened, it is really annoying :( Maybe it is connected with some actualization? We definitely need more users and some tests...

What a pitty, this wonderful notebook CAN be quiet - and had been for a long time!
#crysman

Hmm, it seems that this kind of problems occurs only after hibernation... Also, hibernation has stopped to work properly recently - now the laptop does not shut down, I have to press and hold the power button to make it shut down. After power on it resumes. I used to have this problem before (another kernel), but then it got working. Now it is broken again... Also, furthemore, when resumed from hibernation, WiFi is disabled, I have to re-enable it via network settings.

So it seems there are some problems with devices/services not being waken up after hibernation. I think it is connected somehow also with the fan problem.

#crysman

---

### Post by foxy123 on 2012-09-10
Does anyone experience disappearing camera in Skype? Basically camera sometimes disappears in Skype (showing something like 'no video device' in Options) but appears again after a reboot. Not a major issue but annoying.

---

### Post by marshcast on 2012-09-20
> **Naugas said:**
> OK, got the 64-bit live usb version to work now, apparently it wasn't the default bios settings I have used. I have been trying too boot using uefi and not through the old plain bios. I had no idea something else than bios even existed...



Solved for me. Would like to have a link in here to complain about the intel/microsoft collusion that is creeping in...

---

### Post by poetgrant7 on 2012-09-23
Are there any new options for the graphics drivers, now that 12.04 is out. I have tried Bumblebee and it only screwed up my display.

---

### Post by crysman on 2012-09-30
> **poetgrant7 said:**
> Are there any new options for the graphics drivers, now that 12.04 is out. I have tried Bumblebee and it only screwed up my display.

Bumblebee has been working for me even on 11.10 and it's still on 12.04. Maybe you did some non-standard steps before installing it. I think bumblebee does not like NVIDIA proprietary drivers, so if you installed them prior to bumblebee, that could be problem...

I suggest you reading the bumblebee documentation and FAQ maybe?
#McZ

---

### Post by orymd on 2012-10-20
Hi at all! I'm a new ubuntu user. I have this NB and i want to ask if there will be a wiki for 12.10... There are many issues with this NB :(

---

### Post by dirtylobster on 2012-10-20
> **orymd said:**
> Hi at all! I'm a new ubuntu user. I have this NB and i want to ask if there will be a wiki for 12.10... There are many issues with this NB :(

Have you read [https://help.ubuntu.com/community/Asus_U36SD](https://help.ubuntu.com/community/Asus_U36SD) ?

---

### Post by orymd on 2012-10-20
> **dirtylobster said:**
> Have you read [https://help.ubuntu.com/community/Asus_U36SD](https://help.ubuntu.com/community/Asus_U36SD) ?

Yes, but the "support" is up to 12.04...

---

### Post by olof_ on 2012-10-23
> **krustenBrot said:**
> Anyone got the USB 3.0 port running under 12.04?

Got the same issue on 12.10, the fix on the wikipage does not work. It was not working before update either though. 

If someone got it working, could you please post your /etc/default/grub file or anything else that could be of any help?

---

### Post by crysman on 2012-11-05
> **olof_ said:**
> Got the same issue on 12.10, the fix on the wikipage does not work. It was not working before update either though. 

If someone got it working, could you please post your /etc/default/grub file or anything else that could be of any help?

USB3 (the port on the right) has been running without problems since 11.10 I think. If I remember well, I just disabled some "constant power" function or what in BIOS - the feature which enables to give power to USB even when the laptop is not running. I do not need it anyway... Give it a try.
#crysman

---

### Post by bratikoff on 2012-11-06
Hi all,

i have problem with wake up in kubuntu 12.10. System wakes up, but then it freezes. I found, that problem occurs only when i have bluetooth enabled and connected 1 device to it (mouse). If bluetooth disabled, or even when enabled, but no devices connected - all works fine. In kubuntu 12.04 all was great. Tried tweaks on wiki page about suspend/resume and also bluetooth, but it takes no effect. Have anybody such problem? Thanks for help

ASUS U36SG, kubuntu 12.10, 3.5.0-18-generic #29-Ubuntu SMP Fri Oct 19 10:26:51 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

---

### Post by crysman on 2012-11-14
> **crysman said:**
> USB3 (the port on the right) has been running without problems since 11.10 I think. If I remember well, I just disabled some "constant power" function or what in BIOS - the feature which enables to give power to USB even when the laptop is not running. I do not need it anyway... Give it a try.
#crysman

Hmm, it seems the USB3 port stops working when you suspend. After resuming, only USB ports on the left are working.

In addition, it also seems that the memory card reader stops working after resume!!

This might be a bug... Anybody could confirm?
#crysman

---

### Post by krustenBrot on 2012-11-23
Thanks for that little piece of information: >  I just disabled some "constant power" function or what in BIOS - the  feature which enables to give power to USB even when the laptop is not  running. I do not need it anyway... Give it a try. **finally** since 11.10 i could at least get the USB 3.0 working for a short time, after disbaling the *charger+* feature in Bios.
But yes, same here, [B]stops working after suspend.

[/B]*Update:  *I just tried enabling the 11.04-fix from the wiki. Still doesn't work after suspending. :(

---

### Post by krustenBrot on 2012-11-24
Update 2:
I tried the SuspendFix script from the wiki. Still does not work.
Here is my *lspci -v* output **before** suspending:
> 
04:00.0 USB controller: Fresco Logic FL1000G USB 3.0 Host Controller (rev 04) (prog-if 30 [XHCI])
    Subsystem: ASUSTeK Computer Inc. Device 1039
    Physical Slot: 3
    Flags: bus master, fast devsel, latency 0, IRQ 19
    Memory at dd200000 (32-bit, non-prefetchable) [size=64K]
    Capabilities: <access denied>
    Kernel driver in use: xhci_hcd

and **after **resuming from suspend:
> 04:00.0 USB controller: Fresco Logic FL1000G USB 3.0 Host Controller (rev ff) (prog-if ff)
    !!! Unknown header type 7f
    Kernel driver in use: xhci_hcd


Any Ideas?

---

### Post by cloutz on 2012-12-30
Hi i'm using lubuntu 12.10 x64 on u36sd.

Someone knows how to rotate the webcam in skype?
I already tried this [https://help.ubuntu.com/community/Asus_U36SD#Webcam_issue](https://help.ubuntu.com/community/Asus_U36SD#Webcam_issue)
but it didn't worked.

Thanks

---

### Post by haakon on 2012-12-30
> **cloutz said:**
> Someone knows how to rotate the webcam in skype?
I already tried this [https://help.ubuntu.com/community/Asus_U36SD#Webcam_issue](https://help.ubuntu.com/community/Asus_U36SD#Webcam_issue)
but it didn't worked.

That works for me. Kubuntu 12.10, x86_64.

---

### Post by crysman on 2013-01-01
> **cloutz said:**
> Hi i'm using lubuntu 12.10 x64 on u36sd.

Someone knows how to rotate the webcam in skype?
I already tried this [https://help.ubuntu.com/community/Asus_U36SD#Webcam_issue](https://help.ubuntu.com/community/Asus_U36SD#Webcam_issue)
but it didn't worked.

Thanks

There used to be a problem with this, but I think it got fixed in 12.04 already (using Xubuntu)... Or maybe Skype released some fix itself by that time.

But both in *camorama* and *ekiga* camera runs just fine out-of-the-box. I cannot tell anything about Skype any more, because I stopped to use it completely and switched to [Ekiga]("https://www.ekiga.net/"), because Skype is not open source.

---

### Post by cloutz on 2013-01-03
Thanks crysman, haakon for the replies

Maybe it does not work for me because i use Lubuntu x64?
I think the solution should work anyway


This is what i get:
```
tinga@ubuntu:~$ sudo apt-get update && sudo apt-get install libv4l-0
Ign http://security.ubuntu.com quantal-security InRelease
Ign http://it.archive.ubuntu.com quantal InRelease                                                                                                          
Ign http://ppa.launchpad.net quantal InRelease                                                                                                              
Ign http://dl.google.com stable InRelease                                                                                       
Ign http://extras.ubuntu.com quantal InRelease                                                                                  
Trovato http://security.ubuntu.com quantal-security Release.gpg                                                                 
Ign http://it.archive.ubuntu.com quantal-updates InRelease                                                                      
Ign http://ppa.launchpad.net quantal Release.gpg                                                                                
Trovato http://extras.ubuntu.com quantal Release.gpg                                                                            
Trovato http://security.ubuntu.com quantal-security Release                                                                     
Ign http://it.archive.ubuntu.com quantal-backports InRelease                                                                                           
Ign http://archive.canonical.com quantal InRelease                                                                                                     
Ign http://ppa.launchpad.net quantal Release                                                                                    
Trovato http://it.archive.ubuntu.com quantal Release.gpg                                                                        
Trovato http://extras.ubuntu.com quantal Release                                                                                
Trovato http://security.ubuntu.com quantal-security/main Sources                                                                                                                     
Trovato http://security.ubuntu.com quantal-security/restricted Sources                                                                                                               
Trovato http://archive.canonical.com quantal Release.gpg                                                                                                      
Trovato http://dl.google.com stable Release.gpg                                                                                 
Trovato http://extras.ubuntu.com quantal/main Sources                                                                           
Trovato http://it.archive.ubuntu.com quantal-updates Release.gpg                                                                
Trovato http://security.ubuntu.com quantal-security/universe Sources                                                            
Trovato http://dl.google.com stable Release                                                                                                                   
Trovato http://extras.ubuntu.com quantal/main amd64 Packages                                                                                                                        
Trovato http://archive.canonical.com quantal Release                                                                                                          
Trovato http://dl.google.com stable/main amd64 Packages                                                                                                       
Trovato http://security.ubuntu.com quantal-security/main amd64 Packages                                                         
Trovato http://it.archive.ubuntu.com quantal-backports Release.gpg                                                              
Trovato http://extras.ubuntu.com quantal/main i386 Packages                                                                                                                            
Trovato http://dl.google.com stable/main i386 Packages                                                                                                                                 
Trovato http://security.ubuntu.com quantal-security/restricted amd64 Packages                                                                                 
Trovato http://archive.canonical.com quantal/partner Sources                                                                                                  
Trovato http://security.ubuntu.com quantal-security/universe amd64 Packages                                                                                   
Trovato http://security.ubuntu.com quantal-security/main i386 Packages                                                                                   
Trovato http://archive.canonical.com quantal/partner amd64 Packages                                                                                      
Trovato http://security.ubuntu.com quantal-security/restricted i386 Packages                                                    
Trovato http://security.ubuntu.com quantal-security/universe i386 Packages                                                      
Trovato http://archive.canonical.com quantal/partner i386 Packages                                                              
Trovato http://it.archive.ubuntu.com quantal Release                                                                            
Trovato http://it.archive.ubuntu.com quantal-updates Release                                                                                                                                    
Trovato http://it.archive.ubuntu.com quantal-backports Release                                                                                                                                  
Trovato http://it.archive.ubuntu.com quantal/main Sources                                                                                                                                       
Trovato http://it.archive.ubuntu.com quantal/restricted Sources                                                                                                                        
Trovato http://it.archive.ubuntu.com quantal/universe Sources                                                                   
Trovato http://it.archive.ubuntu.com quantal/main amd64 Packages                                                                
Ign http://dl.google.com stable/main Translation-it_IT                                                                          
Ign http://dl.google.com stable/main Translation-it                                                                                                           
Ign http://dl.google.com stable/main Translation-en                                                                                                           
Trovato http://security.ubuntu.com quantal-security/main Translation-en                                                                                       
Ign http://extras.ubuntu.com quantal/main Translation-it_IT                                                                                                   
Trovato http://it.archive.ubuntu.com quantal/restricted amd64 Packages                                                               
Ign http://archive.canonical.com quantal/partner Translation-it_IT                                     
Trovato http://security.ubuntu.com quantal-security/restricted Translation-en                                                        
Ign http://extras.ubuntu.com quantal/main Translation-it                                                                             
Trovato http://it.archive.ubuntu.com quantal/universe amd64 Packages                                                                 
Ign http://extras.ubuntu.com quantal/main Translation-en                                               
Err http://ppa.launchpad.net quantal/main Sources                                                      
  404  Not Found
Trovato http://security.ubuntu.com quantal-security/universe Translation-en                            
Trovato http://it.archive.ubuntu.com quantal/main i386 Packages               
Err http://ppa.launchpad.net quantal/main amd64 Packages                      
  404  Not Found
Err http://ppa.launchpad.net quantal/main i386 Packages                                                     
  404  Not Found
Ign http://archive.canonical.com quantal/partner Translation-it                                             
Trovato http://it.archive.ubuntu.com quantal/restricted i386 Packages         
Ign http://ppa.launchpad.net quantal/main Translation-it_IT                   
Ign http://ppa.launchpad.net quantal/main Translation-it                                                    
Ign http://archive.canonical.com quantal/partner Translation-en                                             
Trovato http://it.archive.ubuntu.com quantal/universe i386 Packages           
Ign http://ppa.launchpad.net quantal/main Translation-en                      
Trovato http://it.archive.ubuntu.com quantal/main Translation-it                   
Trovato http://it.archive.ubuntu.com quantal/main Translation-en                   
Trovato http://it.archive.ubuntu.com quantal/restricted Translation-it
Trovato http://it.archive.ubuntu.com quantal/restricted Translation-en
Trovato http://it.archive.ubuntu.com quantal/universe Translation-it
Trovato http://it.archive.ubuntu.com quantal/universe Translation-en
Ign http://security.ubuntu.com quantal-security/main Translation-it_IT
Trovato http://it.archive.ubuntu.com quantal-updates/main Sources
Ign http://security.ubuntu.com quantal-security/main Translation-it
Ign http://security.ubuntu.com quantal-security/restricted Translation-it_IT
Trovato http://it.archive.ubuntu.com quantal-updates/restricted Sources
Ign http://security.ubuntu.com quantal-security/restricted Translation-it
Ign http://security.ubuntu.com quantal-security/universe Translation-it_IT
Trovato http://it.archive.ubuntu.com quantal-updates/universe Sources
Ign http://security.ubuntu.com quantal-security/universe Translation-it
Trovato http://it.archive.ubuntu.com quantal-updates/main amd64 Packages
Trovato http://it.archive.ubuntu.com quantal-updates/restricted amd64 Packages
Trovato http://it.archive.ubuntu.com quantal-updates/universe amd64 Packages
Trovato http://it.archive.ubuntu.com quantal-updates/main i386 Packages
Trovato http://it.archive.ubuntu.com quantal-updates/restricted i386 Packages
Trovato http://it.archive.ubuntu.com quantal-updates/universe i386 Packages
Trovato http://it.archive.ubuntu.com quantal-updates/main Translation-en
Trovato http://it.archive.ubuntu.com quantal-updates/restricted Translation-en
Trovato http://it.archive.ubuntu.com quantal-updates/universe Translation-en
Trovato http://it.archive.ubuntu.com quantal-backports/main Sources
Trovato http://it.archive.ubuntu.com quantal-backports/restricted Sources
Trovato http://it.archive.ubuntu.com quantal-backports/universe Sources
Trovato http://it.archive.ubuntu.com quantal-backports/main amd64 Packages
Trovato http://it.archive.ubuntu.com quantal-backports/restricted amd64 Packages
Trovato http://it.archive.ubuntu.com quantal-backports/universe amd64 Packages
Trovato http://it.archive.ubuntu.com quantal-backports/main i386 Packages
Trovato http://it.archive.ubuntu.com quantal-backports/restricted i386 Packages
Trovato http://it.archive.ubuntu.com quantal-backports/universe i386 Packages
Trovato http://it.archive.ubuntu.com quantal-backports/main Translation-en
Trovato http://it.archive.ubuntu.com quantal-backports/restricted Translation-en
Trovato http://it.archive.ubuntu.com quantal-backports/universe Translation-en
Ign http://it.archive.ubuntu.com quantal/main Translation-it_IT
Ign http://it.archive.ubuntu.com quantal/restricted Translation-it_IT
Ign http://it.archive.ubuntu.com quantal/universe Translation-it_IT
Ign http://it.archive.ubuntu.com quantal-updates/main Translation-it_IT
Ign http://it.archive.ubuntu.com quantal-updates/main Translation-it
Ign http://it.archive.ubuntu.com quantal-updates/restricted Translation-it_IT
Ign http://it.archive.ubuntu.com quantal-updates/restricted Translation-it
Ign http://it.archive.ubuntu.com quantal-updates/universe Translation-it_IT
Ign http://it.archive.ubuntu.com quantal-updates/universe Translation-it
Ign http://it.archive.ubuntu.com quantal-backports/main Translation-it_IT
Ign http://it.archive.ubuntu.com quantal-backports/main Translation-it
Ign http://it.archive.ubuntu.com quantal-backports/restricted Translation-it_IT
Ign http://it.archive.ubuntu.com quantal-backports/restricted Translation-it
Ign http://it.archive.ubuntu.com quantal-backports/universe Translation-it_IT
Ign http://it.archive.ubuntu.com quantal-backports/universe Translation-it
W: Impossibile recuperare http://ppa.launchpad.net/libv4l/ppa/ubuntu/dists/quantal/main/source/Sources  404  Not Found

W: Impossibile recuperare http://ppa.launchpad.net/libv4l/ppa/ubuntu/dists/quantal/main/binary-amd64/Packages  404  Not Found

W: Impossibile recuperare http://ppa.launchpad.net/libv4l/ppa/ubuntu/dists/quantal/main/binary-i386/Packages  404  Not Found

E: Impossibile scaricare alcuni file di indice: saranno ignorati o verranno usati quelli vecchi.

```

And if i try to execute skype as said there i get this log in terminal:
```
tinga@ubuntu:~$ LD_PRELOAD=/usr/lib/i386-linux-gnu/libv4l/v4l1compat.so skype
ERROR: ld.so: object '/usr/lib/i386-linux-gnu/libv4l/v4l1compat.so' from LD_PRELOAD cannot be preloaded: ignored.
ALSA lib conf.c:3314:(snd_config_hooks_call) Cannot open shared library libasound_module_conf_pulse.so
ALSA lib pcm.c:2217:(snd_pcm_open_noupdate) Unknown PCM default
ALSA lib dlmisc.c:254:(snd1_dlobj_cache_get) Cannot open shared library /usr/lib/i386-linux-gnu/alsa-lib/libasound_module_pcm_pulse.so
ALSA lib dlmisc.c:254:(snd1_dlobj_cache_get) Cannot open shared library /usr/lib/i386-linux-gnu/alsa-lib/libasound_module_pcm_pulse.so
ALSA lib pcm_dmix.c:957:(snd_pcm_dmix_open) The dmix plugin supports only playback stream
ALSA lib pcm_dmix.c:957:(snd_pcm_dmix_open) The dmix plugin supports only playback stream
ALSA lib pcm_dmix.c:957:(snd_pcm_dmix_open) The dmix plugin supports only playback stream
ALSA lib pcm_dsnoop.c:551:(snd_pcm_dsnoop_open) The dsnoop plugin supports only capture stream
ALSA lib pcm_dsnoop.c:551:(snd_pcm_dsnoop_open) The dsnoop plugin supports only capture stream
ALSA lib pcm_dsnoop.c:612:(snd_pcm_dsnoop_open) unable to open slave
ALSA lib pcm_dsnoop.c:551:(snd_pcm_dsnoop_open) The dsnoop plugin supports only capture stream
ALSA lib pcm_dsnoop.c:612:(snd_pcm_dsnoop_open) unable to open slave
ALSA lib dlmisc.c:254:(snd1_dlobj_cache_get) Cannot open shared library /usr/lib/i386-linux-gnu/alsa-lib/libasound_module_pcm_pulse.so
ALSA lib dlmisc.c:254:(snd1_dlobj_cache_get) Cannot open shared library /usr/lib/i386-linux-gnu/alsa-lib/libasound_module_pcm_pulse.so
ALSA lib dlmisc.c:254:(snd1_dlobj_cache_get) Cannot open shared library /usr/lib/i386-linux-gnu/alsa-lib/libasound_module_pcm_pulse.so
ALSA lib dlmisc.c:254:(snd1_dlobj_cache_get) Cannot open shared library /usr/lib/i386-linux-gnu/alsa-lib/libasound_module_pcm_pulse.so
ALSA lib pcm_dmix.c:957:(snd_pcm_dmix_open) The dmix plugin supports only playback stream
ALSA lib pcm_dmix.c:957:(snd_pcm_dmix_open) The dmix plugin supports only playback stream
ALSA lib pcm_dmix.c:957:(snd_pcm_dmix_open) The dmix plugin supports only playback stream
ALSA lib pcm_dsnoop.c:551:(snd_pcm_dsnoop_open) The dsnoop plugin supports only capture stream
ALSA lib pcm_dsnoop.c:551:(snd_pcm_dsnoop_open) The dsnoop plugin supports only capture stream
ALSA lib pcm_dsnoop.c:612:(snd_pcm_dsnoop_open) unable to open slave
ALSA lib pcm_dsnoop.c:551:(snd_pcm_dsnoop_open) The dsnoop plugin supports only capture stream
ALSA lib pcm_dsnoop.c:612:(snd_pcm_dsnoop_open) unable to open slave
ALSA lib dlmisc.c:254:(snd1_dlobj_cache_get) Cannot open shared library /usr/lib/i386-linux-gnu/alsa-lib/libasound_module_pcm_pulse.so
ALSA lib dlmisc.c:254:(snd1_dlobj_cache_get) Cannot open shared library /usr/lib/i386-linux-gnu/alsa-lib/libasound_module_pcm_pulse.so
ALSA lib dlmisc.c:254:(snd1_dlobj_cache_get) Cannot open shared library /usr/lib/i386-linux-gnu/alsa-lib/libasound_module_pcm_pulse.so
ALSA lib dlmisc.c:254:(snd1_dlobj_cache_get) Cannot open shared library /usr/lib/i386-linux-gnu/alsa-lib/libasound_module_pcm_pulse.so
ALSA lib pcm_dmix.c:957:(snd_pcm_dmix_open) The dmix plugin supports only playback stream
ALSA lib pcm_dmix.c:957:(snd_pcm_dmix_open) The dmix plugin supports only playback stream
ALSA lib pcm_dmix.c:957:(snd_pcm_dmix_open) The dmix plugin supports only playback stream
ALSA lib pcm_dsnoop.c:551:(snd_pcm_dsnoop_open) The dsnoop plugin supports only capture stream
ALSA lib pcm_dsnoop.c:551:(snd_pcm_dsnoop_open) The dsnoop plugin supports only capture stream
ALSA lib pcm_dsnoop.c:612:(snd_pcm_dsnoop_open) unable to open slave
ALSA lib pcm_dsnoop.c:551:(snd_pcm_dsnoop_open) The dsnoop plugin supports only capture stream
ALSA lib pcm_dsnoop.c:612:(snd_pcm_dsnoop_open) unable to open slave
ALSA lib dlmisc.c:254:(snd1_dlobj_cache_get) Cannot open shared library /usr/lib/i386-linux-gnu/alsa-lib/libasound_module_pcm_pulse.so
ALSA lib dlmisc.c:254:(snd1_dlobj_cache_get) Cannot open shared library /usr/lib/i386-linux-gnu/alsa-lib/libasound_module_pcm_pulse.so
ALSA lib dlmisc.c:254:(snd1_dlobj_cache_get) Cannot open shared library /usr/lib/i386-linux-gnu/alsa-lib/libasound_module_pcm_pulse.so
ALSA lib dlmisc.c:254:(snd1_dlobj_cache_get) Cannot open shared library /usr/lib/i386-linux-gnu/alsa-lib/libasound_module_pcm_pulse.so
ALSA lib pcm_dmix.c:957:(snd_pcm_dmix_open) The dmix plugin supports only playback stream
ALSA lib pcm_dmix.c:957:(snd_pcm_dmix_open) The dmix plugin supports only playback stream
ALSA lib pcm_dmix.c:957:(snd_pcm_dmix_open) The dmix plugin supports only playback stream
ALSA lib pcm_dsnoop.c:551:(snd_pcm_dsnoop_open) The dsnoop plugin supports only capture stream
ALSA lib pcm_dsnoop.c:551:(snd_pcm_dsnoop_open) The dsnoop plugin supports only capture stream
ALSA lib pcm_dsnoop.c:612:(snd_pcm_dsnoop_open) unable to open slave
ALSA lib pcm_dsnoop.c:551:(snd_pcm_dsnoop_open) The dsnoop plugin supports only capture stream
ALSA lib pcm_dsnoop.c:612:(snd_pcm_dsnoop_open) unable to open slave
ALSA lib dlmisc.c:254:(snd1_dlobj_cache_get) Cannot open shared library /usr/lib/i386-linux-gnu/alsa-lib/libasound_module_pcm_pulse.so
ALSA lib dlmisc.c:254:(snd1_dlobj_cache_get) Cannot open shared library /usr/lib/i386-linux-gnu/alsa-lib/libasound_module_pcm_pulse.so

```

Some help?:-?

---

### Post by cloutz on 2013-01-04
> **cloutz said:**
> Hi i'm using lubuntu 12.10 x64 on u36sd.

Someone knows how to rotate the webcam in skype?
I already tried this [https://help.ubuntu.com/community/Asus_U36SD#Webcam_issue](https://help.ubuntu.com/community/Asus_U36SD#Webcam_issue)
but it didn't worked.

Thanks


Solved on *buntu x64,
posted here my solution, if needs:
[http://forum.ubuntu-it.org/viewtopic.php?f=95&t=546530&p=4284546#p4284546](http://forum.ubuntu-it.org/viewtopic.php?f=95&t=546530&p=4284546#p4284546)

It is in Italian, but thanks God code is international ;)

---

### Post by ntesla123 on 2013-02-05
When I put a network cable into the machine while using ubuntu, nothing happens. Whan I use windows, the cable is detected perfectly.

Test output:
```

lspci | grep Ethernet

```gives the output:
```

05:00.0 Ethernet controller: Atheros Communications Inc. AR8151 v2.0 Gigabit Ethernet (rev c0)

``````

ifconfig | grep -A 5 eth0

```gives the output
```
eth0      Link encap:Ethernet  HWaddr 54:04:a6:3c:30:69  
               UP BROADCAST MULTICAST  MTU:1500  Metric:1
               RX packets:0 errors:0 dropped:0 overruns:0 frame:0
               TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
               collisions:0 txqueuelen:1000 
               RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

---

### Post by dirtylobster on 2013-04-25
Anyone using 13.04? Is it worth upgprading from 12.04?

---

### Post by ThomasArildsen on 2013-05-02
> **dirtylobster said:**
> Anyone using 13.04? Is it worth upgprading from 12.04?

I just did that. The step from 12.04 to 12.10 made the "launcher" on the left and the top bar disappear from Unity, and they are still gone in 13.04. I have not yet figured out how to fix this :-(

---

### Post by dirtylobster on 2013-05-02
I'm planning to do a clean install if I do it. How's all the hardware working? USB3, suspend, hotkeys etc?

---

### Post by Naugas on 2013-05-02
> **crysman said:**
> Hmm, it seems the USB3 port stops working when you suspend. After resuming, only USB ports on the left are working.

In addition, it also seems that the memory card reader stops working after resume!!

This might be a bug... Anybody could confirm?
#crysman

Here - [http://ubuntuforums.org/showthread.php?t=1977033](http://ubuntuforums.org/showthread.php?t=1977033) - is a year old thread about suspend issues with usb3. I actually haven't tried usb3 under ubuntu yet, would be nice if it can be made to work reasonably well.

(I just discovered usb3 stop working after suspending under win7 for me, but then it functions as a usb2 port, it doesn't stop working all together. But the win7 drivers have been very buggy and nearly useless with my WD Elements 2" drive. Now it's not disconnected immediately when trying to write to it at least, but it's nearly as slow as using usb2.)

---

### Post by ThomasArildsen on 2013-05-02
> **dirtylobster said:**
> I'm planning to do a clean install if I do it. How's all the hardware working? USB3, suspend, hotkeys etc?

There's some info here: [https://help.ubuntu.com/community/Asus_U36SD](https://help.ubuntu.com/community/Asus_U36SD) (I can't see right now if it has already been mentioned in this thread), but it doesn't say anything about Ubuntu 13.04 (yet).
Suspend seems to work, i.e. it comes back to life after having the lid closed. The USB3 port (on the right) works here, both before and after suspend. Suspend and USB3 may be affected by fixes I applied in an earlier Ubuntu version according to the above link since I upgraded and did not install from scratch, so I suppose some settings may be left from before.
I have solved my issues with Unity now - check here how I did it: [http://askubuntu.com/questions/288235/launcher-and-panel-missing-ubuntu-13-04/289498#289498](http://askubuntu.com/questions/288235/launcher-and-panel-missing-ubuntu-13-04/289498#289498)
The only weird thing left for now is that the WiFi indicator light is inverted: it's off when WiFi is on and vice versa. BTW, the WiFi hotkey works - I haven't checked the others.

---

### Post by gmcle454 on 2013-05-07
I noticed the same problem with the reversed wifi light on a clean install of 13.4.

---

### Post by delineated on 2013-06-08
I've searched everywhere, but either I don't know the right keywords or nobody else has had this problem.

My laptop has functioned perfectly for nearly 2 years from 11.04 to 12.10, release-wise. I attempted to format recently and decided to tool around with elementary OS (Ubuntu-based). My live USB stick (latest image + Unetbootin) worked perfectly, but when I installed it my touchpad wouldn't work, I couldn't get any of my USB devices (multiple flash drives and a mouse) to be recognized, and when I attempted to connect to wifi to download updates (no ethernet available in this dorm) I found out that the OS wasn't even recognizing the hardware.

I thought it might just be elementary OS, so I tried remaking the USB stick with a 12.10 image I have backed up and when that didn't work I tried it with a 13.04 image I grabbed at the library. Same problem. No touchpad, no wifi hardware, can't mount any media (manually as well). I have no idea how to fix this. I'm not entirely clear on what kinds of logs and outputs might be helpful in diagnosing my issue, but I'll provide any that are necessary.

I'd greatly appreciate any advice that you could possible provide. Thanks!

---

### Post by crysman on 2013-10-27
Hello,

does anyone know how to solve this (higher temperatures and fan always on after resume from hibernation) problem?

I am hibernating via ```
sudo pm-hibernate
```.
Normally, I have around 50°C (*acpitz-virtual-0*), but after resuming from hibernation it's persistently around 66°C. My CPU is almost idle all the time :(

I have *bumblebee* installed and running.

---

### Post by valentt on 2013-12-06
Hi, I'm running 13.04 (Raring) and everything works perfectly on Asus U36SD after installing support for Bumblebee, prior to that I had really bad battery life because NVidia gpu was running all the time. Now with NVidia powered off I get excellent battery life with Intel graphic card.

I have one really irritating issue, sound just stops working! My audio mixer works, volume keys work, but there is just no sound. If I reboot into bios and turn volume in bios (this is first time I see volume control in bios) then sometimes audio plays trough speakers...

I use suspend a lot but this happens also when I completely power off and power on Asus U36SD.

Any ideas how to fix this audio issue?!?

---

### Post by crysman on 2013-12-07
> **valentt said:**
> ...
I have one really irritating issue, sound just stops working! My audio mixer works, volume keys work, but there is just no sound. If I reboot into bios and turn volume in bios (this is first time I see volume control in bios) then sometimes audio plays trough speakers...
I use suspend a lot but this happens also when I completely power off and power on Asus U36SD.
Any ideas how to fix this audio issue?!?

Are you running genuine Ubuntu or some of its spins? Because e.g. in case of Xubuntu it might be a [problem related to this]("http://askubuntu.com/questions/360806/volume-indicator-issue-after-xubuntu-13-10-upgrade")...
What do you mean by volume in BIOS? I have no such a thing in my BIOS...
And one extra question: aren't you experiencing any [temperature/fan issues as I do after hibernation]("http://ubuntuforums.org/showthread.php?t=1830430&p=12830289#post12830289")?

---

