---
title: "switching between USB speakers and PCI sound card"
date: 2006-12-03
forum: Absolute Beginner Talk
---

### Post by wuziq on 2006-12-03
I am hoping someone can help me out with this.  I tried searching for related threads, but the ones I found were only somewhat related.

I have a Sound Blaster Live 5.1 card, as well as a set of USB speakers (MS Digital Sound System 80).  I've been using Win2k mainly, but have used Ubuntu for several months and recently switched to Kubuntu.  Anyway, my setup is that I have headphones plugged into the SBLive card, so that when my roommate is sleeping, I just switch from using the USB speakers to using the headphones; or, if I want to save power, I turn off the USB speakers, and use the headphones.

Doing this is no problem in Windows.  It's easy to tell Windows which audio device to use because there's only one setting to change.  I can even disconnect the USB speakers (causing Windows to automatically switch to the sound card), then reconnect USB speakers and switch to using them again.  Is it possible to do this same switching (including disconnecting and reconnecting the USB speakers) in Kubuntu?  I probably don't know what I'm talking about, but is it possible to "tell" ALSA which audio device to "use" or "be associated with"?  Do I have to reload USB audio modules or something, after I reconnect the USB speakers?

I don't really care about having multiple sounds play at the same time (only "nice to have", not what I'm looking for now).

I am using Kubuntu 6.06.

Thanks in advance!

---

### Post by shoagun on 2006-12-03
I've been looking for a solution to this too.  I don't think Ubuntu can do it.  Either that, or no one knows the answer.

---

### Post by wuziq on 2006-12-03
Yeah..  yours was one of the threads that was related.  There's got to be a solution!  hehe.

---

### Post by msak007 on 2006-12-03
I think I know what you're asking for, and I believe it's possible. I run Kubuntu and have a somewhat similar setup. My main speakers are plugged into my Sound Blaster Live card, and I have a set of headphones plugged into the speakers. But I also have a pair of USB headphones (with a microphone) that I used to use when playing online games. You already have your headphones plugged into your sound card directly so there is nothing to do there, and I assume you keep the speakers plugged in all the time and just turn them off when not being used. To switch between them do the following:

1. If you haven't already, start KMix (should be in your "Multimedia" group in KMenu).

2. Right-click on the KMix System Tray icon and select "Select Master Channel..."

3. You should see a drop-down list at the top with all of the detected audio devices. Just switch to the one you want the output to come from.

That's it! Unfortunately KMix doesn't recognize devices that are initialized after the app is started, so if you do plug in and unplug the USB speakers as needed you'll have to restart KMix when you plug / unplug the device. If you keep them plugged in, there's nothing to worry about.

---

### Post by shoagun on 2006-12-03
I should have mentioned that I discovered how to do that, but it doesn't seem to work.  Thanks anyway.

---

### Post by wuziq on 2006-12-03
msak007:  thanks for the response.  I've actually already tried that, since that is basically what I do in Windows.. but it doesn't work.  I have the SBLive selected in KMix, so the sound (in this case, playing MP3s in XMMS using ALSA) should be coming out of my headphones..  but it's coming out of the USB speakers.

---

### Post by wuziq on 2006-12-03
OK, semi-development.  I think I've sort of figured out how to get ALSA to use a specific device as "default".  Since I've set the apps I care about to use ALSA, this works for me.

In my ~/.asoundrc file, I have this:

```

pcm.!default {
    type hw
    card 1
}
ctl.!default {
    type hw
    card 1
}

```

"card 1" is my SBLive card.  If I want to switch to my USB speakers, I replace "card 1" with "card 0", save, and then restart whatever app I'm using (XMMS, Kaffeine, whatever).  It's not the most elegant solution, but I'm just excited cuz it works, haha.

Also, to list sound cards, I do ```
asoundconf list
```.  I think it lists them in order of card 0, card 1, etc, but to make sure, I just do:

```
alsamixer -c x
```, where "x" is 0, 1, 2..  and that tells me if card 0 is my SBLive card or my USB speakers.  Yes..  it's a lame way of doing it :mrgreen: 

So anyway, this method, albeit messy, works when I leave the USB speakers on/plugged in always.  It doesn't work if I turn the speakers off then on again - asoundconf will only list my SBLive as an available sound card at that point.  So, if I can figure out how to get Kubuntu to see my USB speakers again, I might be good..  :eek:

---

### Post by msak007 on 2006-12-04
Well you seem to have gotten somewhere, but there has to be an easier, more elegant solution. I apologize for not testing the whole KMix thing before recommending it, I wasn't sure if you knew of that option. The odd thing is I *swear* that it was working in Dapper. I rarely use that USB headset anymore, and just to see if it would detect it I plugged it in when I was running Dapper. Sure enough it detected, and I had sound coming out of it. I was able to switch back to my internal sound card, and hadn't tried it again since then until I saw your post. The only difference is that now I'm in Edgy. I'll keep looking for a way...

---

### Post by msak007 on 2006-12-04
I kind of figured out a roundabout way of doing the same thing. Not necessarily easier, but it's a different method. 

As you've already discovered if you do```
asoundconf list
``` it lists all your cards. Then what you can do is```
sudo asoundconf set-default-card <name of card>
```
It'll create a file called **.asoundrc**, which points to another file called **.asoundrc.asoundconf**. That file determines which sound card is the default. Normally changing the default card would require a reboot, but you can restart the sound server using Kubuntu System Settings. Click on "Sound System", then check / uncheck any box or change any option from the drop down and change it back so that "Apply" gets lit up again, then click Apply. Once the sound server restarts, your apps can use the default sound card you specified.

Once again I'm sure that there has to be an easier way of manipulating multiple audio devices, it's probably just broken. I wonder if Ubuntu / Gnome users can change between a built-in or PCI sound device and a USB sound device on the fly. If I find anything else I'll post here.

---

### Post by ctsdownloads on 2007-01-01
Here is a fix for ya; although not a GUI one perhaps - but it is clickable. ;)

open a shell and type

> asoundconf list

Then make a note of the sound cards you have.

In my case, I have 
CK8S
UART
Headset

Since I know that CK8S is my on-board sound card and the headset is -  A HEADSET, then I can create switches for each:

First new text file, write:

#! /bin/sh -f
sudo asoundconf set-default-card (your main soundcard - no brackets)
so mine looks like this:

> #! /bin/sh -f
sudo asoundconf set-default-card CK8S

OK, save this and then create one just like it for your headset.

Congrats, now you have two cool looking icons (Ubuntu Dapper) that do nothing whatsoever! Just kidding, go ahead and right click on each of them. Goto properties and then permissions. Under owner, check off the Execute option. Then click the close button at the bottom.

OK, are you ready? Click on the one for your headset - boom, it will ask you how you wish to run this. Choose "in the terminal" and then enter the password - you just changed the default sound card without needing to hack the .conf file manually. 

From here on out, just click as you wish to toggle between the two.  You may not have to enter the password each time, it's a timed sort of deal. ;)

If using to toggle media in a browser, you will need to close the browser with each new toggle. With on the desktop media files however, you will need to close whatever program you were using for the same affect.
[I]
In addition, this also seems to clean up sound issues that are assigned in Skype. In short, once assigned the settings in Skype are not staying set.[/I]

---

### Post by haiku99 on 2007-01-01
I tried the using the conf file , but had problems with the sound card assignments toggling on boot up, so it only assigned the correct default soud card half the time.  I gave up the conf file and gave the sound cards persistent assignments (the default should be 0 and the other card 1) using the info in this howto...lots of other good sound info there too...
[http://ubuntuforums.org/showthread.php?t=205449&highlight=2+sound+card+ubuntu+problem](http://ubuntuforums.org/showthread.php?t=205449&highlight=2+sound+card+ubuntu+problem)

---

### Post by ctsdownloads on 2007-01-01
I hear ya, but while it won't always be consistent on boot up, it works and *works without fail* if you follow the instructions exactly.

[http://www.ubuntuforums.org/showpost.php?p=1954446&postcount=10](http://www.ubuntuforums.org/showpost.php?p=1954446&postcount=10)

Again, it will do as it pleases on a reboot of course, but those switches work perfectly once you click them. Headset or soundcard - on demand. I use it every day and it works great, just as long as you understand that it needs to be re-clicked on a reboot. But clicking a button is not a big deal. :mrgreen:

---

### Post by haiku99 on 2007-01-01
Thanks very much, that does indeed work well, and will do the job until Ubuntu is fixed  (XP automatically uses my USB speakers if they are plugged in, and the onboard sound card if not).  FWIW Real player would not cooperate, but I could make it do so by starting it with **aoss realplay** ...same deal w/ Firefox


> **ctsdownloads said:**
> I hear ya, but while it won't always be consistent on boot up, it works and *works without fail* if you follow the instructions exactly.

[http://www.ubuntuforums.org/showpost.php?p=1954446&postcount=10](http://www.ubuntuforums.org/showpost.php?p=1954446&postcount=10)

Again, it will do as it pleases on a reboot of course, but those switches work perfectly once you click them. Headset or soundcard - on demand. I use it every day and it works great, just as long as you understand that it needs to be re-clicked on a reboot. But clicking a button is not a big deal. :mrgreen:

---

### Post by wuziq on 2007-01-02
ctsdownloads:  awesome!!  this is perfect, thanks for the tip.  also thanks for the link, haiku99  :)

---

### Post by FIREcracker on 2007-01-10
i've got problems with my sound card, and my usb-phone...
when i turn on my pc, all the outing sound goes by my phone..and i have to make alsaconf to set the sblive as default card...
how can i fix it? the solution you wrote could be cool...but there is a problem...asoundconf gives me no results...what can i do now?
M@

---

### Post by DoctorMO on 2007-01-16
This could do with a gui to be honest.

---

### Post by PJSingh5000 on 2008-02-04
Using Kubuntu Gusty x64, the on-board Intel sound chip did not recognize sound input from a connected microphone, so I purchased a Logitech USB Headset with microphone.

Although the USB Headset worked, switching between the on-board output (via connected speakers) and the Headset was cumbersome:  Some sounds would emanate from the attached speakers while other sounds would emanate from the Headset earphones.  I would also have to manually quit and restart KMix to pick up the USB device, once it was plugged in, if I needed to adjust the Headset volume.

Here is a solution, inspired and motivated by the posts above, that I used to automate switching between multiple sound devices using aesthetically pleasing icons on your desktop.

This example uses the following sound cards: Intel (on-board sound via external speakers), Headset (a Logitech USB headset with microphone).  But you could easily apply this to different kinds of sound devices.

**_Collect Information about Your Sound Cards_**

Make sure all of your sound devices are connected.
In a terminal window type the following:
```
$ asoundconf list
```
Make a note of the listed sound cards.

A sample output looks like this:
```
$ asoundconf list
Names of available sound cards:
Intel
Headset
```

**_Setup an Icon for "Headset" (Using Logitech USB Sound Device)_**

[LIST=1]
[*]In your home folder, create a file called ".sound-headset"
[*]Add the following lines and save and close the file.
```
#! /bin/sh -f
asoundconf set-default-card Headset
for name in $(ps ux | awk '/artsd/ && !/awk/ {print $2}'); do kill "$name"; done
for name in $(ps ux | awk '/kmix/ && !/awk/ {print $2}'); do kill "$name"; done
kmix
```
(Note that you will need to *show hidden files* in order to see this file in your home folder).

[*]Right-click on your Desktop
[*]Select "Create New" | "Link to Application..."
[*]A "Properties for Program.desktop - KDesktop" dialog will appear

[*]Click the "General" tab
[*]Type "Headset" in the textbox
[*]Click on the KDE gear icon
[*]A "Select Icon - KDesktop" dialog will appear
[*]Select the "System icons:" radio box
[*]Select "Actions" from the dropdown
[*]Select the "voicecall" icon which looks like a headset and mic (or chose a different icon)

[*]Click the "Applications" tab
[*]Type "Use Headset" in the "Comment" textbox
[*]Click the "Browse..." button
[*]An "Open - KDesktop" dialog appears
[*]Press F8 to show hidden files
[*]Select the ".sound-headset" file you created in your home folder ('/home/<userid>/.sound-headset')
[*]Click the "Open" button
[*]Click "OK"

[*]Right-click on the new "Headset" icon on your Desktop
[*]Select "Properties"
[*]A "Properties for Headset.desktop - KDesktop" dialog will appear
[*]Click on the "Permissions" tab
[*]Mark the "Is executable" checkbox
[*]Click "OK"
[/LIST]


**_Setup an Icon for "Speakers" (Using On-board Intel Sound Device)_**

[LIST=1]
[*]In your home folder, create a file called ".sound-intel"
[*]Add the following lines and save and close the file.
```
#! /bin/sh -f
asoundconf set-default-card Intel
for name in $(ps ux | awk '/artsd/ && !/awk/ {print $2}'); do kill "$name"; done
for name in $(ps ux | awk '/kmix/ && !/awk/ {print $2}'); do kill "$name"; done
kmix
```
(Note that you will need to *show hidden files* in order to see this file in your home folder).

[*]Right-click on your Desktop
[*]Select "Create New" | "Link to Application..."
[*]A "Properties for Program.desktop - KDesktop" dialog will appear

[*]Click the "General" tab
[*]Type "Speakers" in the textbox
[*]Click on the KDE gear icon
[*]A "Select Icon - KDesktop" dialog will appear
[*]Select the "System icons:" radio box
[*]Select "Applications" from the dropdown
[*]Select the "kmix" icon which looks like a speaker with sound waves (or chose a different icon)

[*]Click the "Applications" tab
[*]Type "Use Speakers" in the "Comment" textbox
[*]Click the "Browse..." button
[*]An "Open - KDesktop" dialog appears
[*]Press F8 to show hidden files
[*]Select the ".sound-intel" file you created in your home folder ('/home/<userid>/.sound-intel')
[*]Click the "Open" button
[*]Click "OK"

[*]Right-click on the new "Speakers" icon on your Desktop
[*]Select "Properties"
[*]A "Properties for Speakers.desktop - KDesktop" dialog will appear
[*]Click on the "Permissions" tab
[*]Mark the "Is executable" checkbox
[*]Click "OK"
[/LIST]


**_Optional Icon Placement_**

You can drag the icons onto the kicker instead of your desktop.  If you get a warning "This action will overwrite [...] with itself," then move the icon into another folder, like your home folder, before dragging it onto the kicker.


**_Usage_**

[LIST=1]
[*]Attach your sound device (if it is detached, like the USB Headset).
[*]Click on the icon for your sound device.
[*]The KMix icon in the taskbar will disappear and reappear.
[*]If you are running a media player application, you will have to restart it for the sound to be redirected out of the selected sound device.
[/LIST]
[LIST]
[*]All of your available sound devices will be listed in the KMix "Current mixer:" dropdown.
[*]You can open KMix from the taskbar, select the sound device, and adjust its properties such as volume.
[*]Terminal console sound output is redirected to the selected sound device without restarting.
[/LIST][ATTACH]58625[/ATTACH]

---

