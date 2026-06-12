---
title: "Ubuntu Crashing ~ Urgent"
date: 2007-05-31
forum: Absolute Beginner Talk
---

### Post by sibot on 2007-05-31
Hey all,
My ubuntu seems to be crashing too often for comfort. I don't have a clue why, the system just seems to freeze up during normal running. Anyone has any idea why? please post back! desp need of help! Even as i was writting this post, my ubuntu crashed, im carrying on by restoring the session! SOS
thanks

---

### Post by kevinlyfellow on 2007-05-31
Its very tough to say... Can you give any more information, is it when a particular application is open or just always?  Have you made any changes to your system recently?

I had recently helped a person who had an issue with crashing when firefox was up, he cleared the private data and everything starting working ok.

You may have some bad drivers installed (closed source usually).  Could that be an issue?

Edit: Oh and could you describe what happens when it freezes?  When it freezes, will X restart (ctrl-alt-backspace)?

---

### Post by sibot on 2007-05-31
hey thanks for replying.. Well im back on xp for now, its impossible to work on ubuntu as of now. It crashes within 2mins of boot. The system just freezes, mouse doesnt move, nothing happen, total freeze out! Nothing works, not even the ctrl-alt-backspace. I just installed nvidia drivers, thats about it, nothing else apart from that, and some random applications ofcourse.

---

### Post by Sparkster185 on 2007-05-31
> 
I just installed nvidia drivers, thats about it, nothing else apart from that, and some random applications ofcourse.


The nVidia drivers are probably the culprit.  Try reverting back to the "nv" driver, and then running Envy to correctly install/configure your nvidia driver.

---

### Post by sibot on 2007-05-31
Hmmm, i'd be able to do that if my linux would boot, I guess ill have to format.

---

### Post by kevinlyfellow on 2007-05-31
> **sibot said:**
> hey thanks for replying.. Well im back on xp for now, its impossible to work on ubuntu as of now. It crashes within 2mins of boot. The system just freezes, mouse doesnt move, nothing happen, total freeze out! Nothing works, not even the ctrl-alt-backspace. I just installed nvidia drivers, thats about it, nothing else apart from that, and some random applications ofcourse.

Interesting.  Since when has this been happening?  Has it been since you installed the nvidia drivers or before?  I'm wondering if your nvidia drivers that you installed are clashing with the drivers in the restricted drivers manager.

---

### Post by sibot on 2007-05-31
i downloaded the drivers from the restricted drivers manager only. I guess it started happening soon after, first time it happened when i was switching workspaces, n since then it happens every now and then. when i goto the application menu, when im selecting a window.

---

### Post by heldal on 2007-05-31
> **sibot said:**
> i downloaded the drivers from the restricted drivers manager only. I guess it started happening soon after, first time it happened when i was switching workspaces, n since then it happens every now and then. when i goto the application menu, when im selecting a window.

For people to be able to provide valuable advise you should provide:

1. A description of your hardware: Computer model, or even better details like: pcessor, videocard, network-interface, mainboard etc. Output from commands like  "lspci", "lsusb" (and possibly even "hal-device" for all the gory details) can be of great help.

2. Log-output (if any) from around the time of the crash (files in /var/log).

---

### Post by sibot on 2007-06-01
Hey,
Well the specs of my comp are :-

Processor - Pentium 4 - 3Ghz HT
RAM - 1024 MB (DDR)
GPU - Nvidia 6200 PCI-E (256 MB - 128 (dedicated) 128 (shared)
Soundcard - Creative Audigy Soundblaster 5.1
HDD - 250 GB
Mobo - Intel DGGC101

I'll surely try out them commands once i log back onto ubuntu, I'm supposed to write them in the terminal right?
thanks

---

### Post by Crafty Kisses on 2007-06-01
> **sibot said:**
> Hey,
Well the specs of my comp are :-

Processor - Pentium 4 - 3Ghz HT
RAM - 1024 MB (DDR)
GPU - Nvidia 6200 PCI-E (256 MB - 128 (dedicated) 128 (shared)
Soundcard - Creative Audigy Soundblaster 5.1
HDD - 250 GB
Mobo - Intel DGGC101

I'll surely try out them commands once i log back onto ubuntu, I'm supposed to write them in the terminal right?
thanks

I have the exact same problem man, I've had to reinstall Ubuntu like 12 times, but that's besides the point, I've only had problems with the Nvidia 6 series for some reason. It's weird.

---

### Post by sibot on 2007-06-01
I don't know man, it gets kinda bugging....got my whole mood off..anyway ill try reinstalling it again tonight, did you find any way out though?

---

### Post by sibot on 2007-06-01
Anyone who could offer any help, would be of great assistance.

---

### Post by kevinlyfellow on 2007-06-01
At some point, you may just say that Ubuntu isn't the right distro for you computer.  Codename said he reinstalled 12 times... sounds like thing just are not working.  Have you guys tried Linux Mint (based on Ubuntu, but popular since it is much more lax about closed drivers/software)?  Well there are tons out there that are friendly that you could try if your computer and ubuntu refuse to get along.

---

### Post by sibot on 2007-06-01
Hmmm the whole idea of "ditching" ubuntu makes me kinda sad, had been looking forward to it since a long long time now. Maybe i'll just change my GPU, in the coming days, but i need to put my finger onto something and know exactly whats wrong before doing that.

---

### Post by kevinlyfellow on 2007-06-02
> **sibot said:**
> Hmmm the whole idea of "ditching" ubuntu makes me kinda sad, had been looking forward to it since a long long time now. Maybe i'll just change my GPU, in the coming days, but i need to put my finger onto something and know exactly whats wrong before doing that.

Sorry, its no big deal to me (I've been around the block if you know what I mean ;)).  I fully support you if want to keep digging into it.  These days, a lot of people ditch linux as a whole using Ubuntu as the only example of the OS and I didn't want you guys to run away :-)

But, guess what I just discovered?  A script that will detect and install the NVidia cards.  I found this post on your card [http://ubuntuforums.org/showthread.php?t=390470](http://ubuntuforums.org/showthread.php?t=390470) and it leads here: [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

It should work installing your card by hand, but I'd like to know if the crashing is for sure due to the card.  Best of luck.

---

### Post by sibot on 2007-06-02
Nah, won't be ditching linux just cause it crashes, i'll keep digging into it until i find out whats wrong. Anyway, thanks alot for looking the info up, but i dont think its a problem of the GPU, i reinstalled linux and havent installed the drivers from restricted driver manager, but am still facing the crash problems...Although i checked out the log and found that everytime my computer crashes theres a log entry in the syslog -

Jun 2 14:30:30 sibot gconfd (digvijoy-5273): Resolved address "xml:readwrite:/home/digvijoy/.gconf" to a writable configuration source at position 0
Jun 2 14:30:31 sibot NetworkManager: <information>^IUpdating allowed wireless network lists.
Jun 2 14:30:31 sibot NetworkManager: <WARNING>^I nm_dbus_get_networks_cb (): error received: org.freedesktop.NetworkManagerInfo.NoNetworks - There are no wireless networks stored..

I dont even have a wireless card, can i disable this somehow?

---

### Post by kevinlyfellow on 2007-06-02
Open up your sessions and unchecking network manager and logout/login.  This will disable network manager from when you login.  Maybe this will help

---

### Post by kevinlyfellow on 2007-06-02
ANother idea, although its a bit of a long shot.  Have you tried (or had enough time after logging in) to make a new user and trying that account out?

---

### Post by sibot on 2007-06-02
I'll try out the network bit, Im updating my ubuntu, maybe that'll help

---

### Post by benner on 2007-06-04
if you search the forums you will see a million posts about this one and no solutions.  i have been waiting for an answer since the release candidate of feisty.  funny i never had the problem with the beta.  i have:

ati x550 
amd 4200+
an nvidia chipset on the motherboard (forget which)
1 ide 80gig and 1 sata 250gig
1gig ram

and it crashes totally randomly as you described.

it seems to happen with every card every os version...  no pattern seems to have emerged that i have seen.

---

### Post by sibot on 2007-06-06
its sad, someone should take over the issue, ubuntu might be losing ALOT of people like this.

---

