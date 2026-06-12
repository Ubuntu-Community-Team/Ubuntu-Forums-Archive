---
title: "gusty wifi connection"
date: 2007-11-13
forum: Absolute Beginner Talk
---

### Post by gatoruss on 2007-11-13
HI - I installed gusty on an extra machine I have.

When I power up, Network Manager finds my SSED and asks for a key.  I provide key and I get logged onto internet.  I then have connectivity for about 15 to 45 minutes, then lose connectivity.  Thereafter, NM tries to connect to the SSED but is unsuccessful.  Only optio at that point is to re-boot and then the pattern repeats itself.

Any ideas?

---

### Post by eldepeche on 2007-11-13
I have similar problems sometimes. Have you tried using Network Manager to change the connection to Wired or off, then change back? This should re-initialise the wifi connection.

---

### Post by gatoruss on 2007-11-13
No, I have not tried that...I am not certain, but my recollection id that the "wired" optiuon is grayed-out.  But I will have to wait until it happens again to be sure.

Thanks.

---

### Post by jw5801 on 2007-11-13
What network card do you have and what driver are you using to run it? It's probably the kernel module that's crashing, so if you remove it and reinsert it then things should be ok again (I've had to do this, although rarely). I'd be more curious to see why it was crashing after such a small amount of time. Is there anything specific you do that causes it to die? Try running "dmesg" just after it happens and see if anything there sheds light, at the very least it should tell you what module is controlling your wireless card. If you're unsure what to make of the output from that command, post it here in code tags and we'll take a look.

---

### Post by gatoruss on 2007-11-13
I have a linksys card...I believe that the drived is rt61 or rt2500 (when I am home tonite I will look again and post).

The last time I ran it (this moring for an hour or so) it seemed to be fine.  Next time it crashes i will run "dmesg" and post.

**Sometimes** (*but not always*) the wifi crash is accompanied by the mouse and the keyboard locking up.  I have a kvm switch to allow 2 PCs (windows xp and ubuntu) to share monitor, keyboard and mouse.  That I imagine could be causing the mouse and keyboard problem, with the simultaneous wifi problem a coincidence....

FWIW - I hope I can solve this wifi issue...I had been playing around with ubuntu a few months ago...got wifi to work with Edgy Eft (6.10), then accidently upgraded to Feisty Fawn (7.04)...and was never able to get wifi to work...gave up in frustration...now thought I'd give it another go with Gusty....I was so pysched at first that NM immediately connected to my wifi card without any configuration other then entering the passkey!

---

### Post by jw5801 on 2007-11-13
Ok, cool. It could be a buggy native driver causing the issues. Were you using ndiswrapper in Edgy?

---

### Post by gatoruss on 2007-11-13
> 
Were you using ndiswrapper in Edgy?
No, I was not using ndiswrapper with Edgy.  I configured my wifi by following this thread...[http://ubuntuforums.org/showthread.php?t=318539](http://ubuntuforums.org/showthread.php?t=318539)

> 
What network card do you have and what driver are you using to run it?
I entered lspci in my terminal and the wifi line read:

> 
01:0a.0 Network controller: RaLink RT2561/RT61 802.11g PCI
> 
It's probably the kernel module that's crashing, so if you remove it and reinsert it then things should be ok again (I've had to do this, although rarely).
How do I do this?

Also,  Each time I boot the pc, I need to re-enter mu pass-key.  Is there a way to make NM do this automatically?

Thanks!

---

### Post by jw5801 on 2007-11-14
> **gatoruss said:**
> No, I was not using ndiswrapper with Edgy.  I configured my wifi by following this thread...[http://ubuntuforums.org/showthread.php?t=318539](http://ubuntuforums.org/showthread.php?t=318539)

I entered lspci in my terminal and the wifi line read:

How do I do this?

Also,  Each time I boot the pc, I need to re-enter mu pass-key.  Is there a way to make NM do this automatically?

Thanks!

Well for the password thing, do you have to enter the key itself? Or just your password into the keyring manager? If it's just the keyring manager, then in gutsy there should be an little check-box that says "do not ask next time." If it doesn't appear take a look through the last few pages of [this](http://ubuntuforums.org/showthread.php?t=187874) thread, there is some discussion on the matter.

That other thread references:
> 6. RTxxx (Ralink) drivers do not support this approach. Either install "ndiswrapper" replacing Serialmonkey's driver or visit this site.So if you're attempting to use WPA level encryptions then you might be struggling. We can set up ndiswrapper if you continue to have problems however, [this](http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list_o-z/) page has the information we need about your card (do a find on rt2561 and you'll see it).

To remove a module from the kernel run ```
sudo rmmod *module-name*
```and to add one, run:```
sudo modprobe *module-name*
```You'll need to know what the module is called though.

---

### Post by ushills on 2007-11-14
Have a look at my site [here ]("http://www.ushills.co.uk/ubuntu/RT61.html")I had similar problems with the RT61 card and managed to resolve it.

---

