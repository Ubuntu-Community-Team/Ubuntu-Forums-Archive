---
title: "2 Roadblocks to Ubuntu"
date: 2008-01-09
forum: Absolute Beginner Talk
---

### Post by Bascote on 2008-01-09
Hey guys I recently installed Ubuntu on my home desktop and, although I have a ton of questions I'd like to ask (since trying to figure things out myself aren't getting too far..) I'll start with a couple questions I hope will be simple for many experienced users.

I love ubuntu and I really want to get it installed on my laptop but there are a few problems..

*using the Gutsy Gibbon*

1. At work I connect to a 128 bit encrypted network. Running ubuntu on my laptop from a cd I find that no matter what I do I just cannot get it to connect?

2. At school I connect to a network that uses leap authentication (currently I use intel pro/set to configure it by applying my username and password and some other little details which get the connection going), is there a way to configure this on Ubuntu?

3. My job gives us an ipass account to connect wirelessly from hotspots, we only have an installation for windows, is there an easy way to do this from Ubuntu or do I have to contact ipass people for support with this?

AND THE MOST IMPORTANT QUESTION WHICH WILL DETERMINE WHETHER I GO BLIND OR NOT =)

4. On my desktop computer I usually have a native resolution of 1024 x 768, now once I installed linux I found this beautiful resolution that was automatically set at 1280 x 1024, since its so nice and the only resolution that looks normal on my comptuer I want to keep it but it wont go higher than 50Hz refresh rate and I my eyes are squinting more than normal. Any way to fix this?

THANKS IN ADVANCE!

---

### Post by gupta_sumesh63 on 2008-01-10
To get your resolution do the following:
Open a terminal(Applications->Accessories->terminal).
Then open the file /etc/usplash.conf
code:
> $ gksudo gedit  /etc/usplash.conf
(gap between gedit and /)

There change your resolution to 1024x768
Save the file.
Next time you boot you'll see the new resolution.
That solves your point no 4.
There will be someone who'll  take care your other points.
Alternatively you can download startupmanager.
There you can change your resolution.
cheers.

---

### Post by Bascote on 2008-01-10
Thanks ill try that right away! I just wanted to add number 5 now..

5. Where is the 'best' place to start learning terminal basics and build from there!?

---

### Post by Bascote on 2008-01-10
Tried the configuration it seems its only for the splash screen when starting up.

The only way the screen looks normal is 1280 x 1024 but if I change it to 1024 x 768 it looks like i can see all the pixels.. =(

---

### Post by tgalati4 on 2008-01-10
Answer to 5:  Search for forums for what you want to do from the command line add "bash" to your list of search terms.  You will find lots of scripts and hints.  The best way to learn is to just start using it.  Search the forums for Linux tutorials and you will find lots of links to cheat sheets, cools scripts, bash programming guides, etc.

For example, to find out what is connected to your pci bus:

>lspci -vv

To find out what is connected to your usb:

>lsusb

To find out what kernel modules are currently loaded:

>lsmod

Only about a thousand more commands to learn . . .

For your video resolution, you need to edit your xorg.conf file.  This will only last during your current session, as the Live CD doesn't save settings.  You will have to install it to start customizing.

---

### Post by gupta_sumesh63 on 2008-01-10
O.k.
> System -> Preferences -> screen resolution.
Change your resolution there and try.
For basic commands try this link
> [https://help.ubuntu.com/7.10/basic-commands/C/](https://help.ubuntu.com/7.10/basic-commands/C/)

---

### Post by Bascote on 2008-01-10
Thanks again everyone but the thing is Im not booting from a cd, I have tried changing the resolution from system preferences -> screen resolution but it looks bad. 

I love the way this looks but it wont go higher than 50Hz refresh rate because I guess my screen cant handle more at this resolution. I just thought there was something wrong because the 102 x 768 doesnt look normal.

As for learning commands I'll keep working on it and find out more =) thanks

---

### Post by gupta_sumesh63 on 2008-01-11
Dont loose heart. Try this. Open menu.lst file.
Code:
> $ gksudo gedit /boot/grub/menu.lst

There check for the following line:
> kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=14a23fbc-0268-4838-ad76-89c6f805dd58 ro quiet splash vga=791

You will see that you do not have the entry of vga=791 in your file.
Make that entry. Save the file. Ensure that you have changed your resolution in system->preferences->screen resolution to 1024x768.
Reboot.
Please tell if you see any difference.

---

### Post by Bascote on 2008-01-11
Thanks, I solved that problem yesterday, I just had to go to system -> administrator -> screens and graphics and set my monitor type, I guess its been off this whole time, then using my video card settings (not ubuntu's resolution settings) i was able to set it to 85Hz. =)

1 problem down!

---

### Post by Martin Witte on 2008-01-11
> **Bascote said:**
> Thanks ill try that right away! I just wanted to add number 5 now..

5. Where is the 'best' place to start learning terminal basics and build from there!?

maybe this [https://help.ubuntu.com/community/UsingTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal) does it for you?

---

### Post by Linuxratty on 2008-01-11
> **Bascote said:**
> Thanks, I solved that problem yesterday, I just had to go to system -> administrator -> screens and graphics and set my monitor type, I guess its been off this whole time, then using my video card settings (not ubuntu's resolution settings) i was able to set it to 85Hz. =)

1 problem down!

Excellent.
You also know you can change font size under Firefox...Yes?
Edit.preferences> Content>default font> advnced.
Just so you know. .

---

### Post by Bascote on 2008-01-11
Im sure that'll help, ive been starting to catch on... slowly.

---

### Post by macogw on 2008-01-11
Intel Pro?  Is it an ipw3945 (lsusb will tell you)?  If so, you should be able to do both WPA-LEAP and WEP-128 (and any other WEP or WPA you come across) using Network Manager, which is located in the upper-right part of your screen.  It shows 2 computers when disconnected or connected with a wire and the signal strength for wireless connections.  ipw2200 probably works too, but I don't have personal experience with it.

---

### Post by Bascote on 2008-01-12
I believe its 2200 but I think I need to check with the system administrator for a passkey because I only have the normal key which is a whole bunch of jumbled letters and numbers.

Still I have the problem of LEAP authentication at school.

---

