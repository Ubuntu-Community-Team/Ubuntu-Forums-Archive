---
title: "Ubuntu on Lenovo V100"
date: 2006-09-17
forum: Absolute Beginner Talk
---

### Post by boredom_amused on 2006-09-17
Hello, I totally switched to Ubuntu on my desktop computer a month ago and I just bought a Lenovo V100 laptop and I'm planning on running Ubuntu on it too. I've done some research and so far the things that might be kind of rough will be the intergrated fingerprint reader, bluetooth, and sound (i don't have the webcam). From what i've read, the wireless issues have been resolved. 
Is there anything else I should be prepared to deal with before I make this commitment?  I just want to be aware of any hassles I might have. 

thanks a lot!

---

### Post by sktx on 2006-09-17
A laptop's first Ubuntu install is always an adventure.  

I don't know if the wireless issues have been resolved, but it is true that climbing a greased pole with your hands tied together is no longer easier than getting your wireless NIC to cooperate with Ubuntu.  Sound has never really been a problem for me, except for at one time getting the sound to work with Flash in Firefox, or letting multiple programs play audio at the same time...


All that aside, considering that it's a new computer, I'd partition off a good chunk of the HDD and run a dual boot setup, so that if you run into major problems and decide that you really don't want to hassle with them, you can still use the hardware that came with your lappy in the OS that it shipped with.  In all likelihood, though, give it enough time and effort and after awhile you'll have it all sorted out and good to go.   Ubuntu on a laptop is incredibly slick, IMO, and if you spend a little time tweaking GNOME/KDE/XFCE/OpenBox/whatever to look cool, an Ubuntu Laptop can be a helluva showoff piece.  

I know ALL the girlies love *my* 'buntu box. :P

---

### Post by boredom_amused on 2006-09-17
hahahaha, yah i think i'm going to dual boot and see how that goes... The funny thing is that I get the feeling that I'll have fewer problems with getting ubuntu to handle everything vs. the headaches I've had just dealing with updating and deleting and installing and whatever whatever when I first turned on this laptop a few days ago... we'll see what happens.

---

### Post by exor|grey on 2006-09-23
I've got XUbunutu 6.06 running on my V100, runs well with a few issues.

Needed to upgrade to the 686 kernel for SMP on the Core Duo. Sound worked out of the box and  wireless just required the installation of wpa_suplicant for WPA.

I haven't gotten the finger-print reader or bluetooth to function properly. Suspend/Hibernate are spotty and sometimes result in a lockup, especially if unplugging before fully suspended. Battery life is pretty poor at about 3.5 hours, but I understand that even under Windows the battery on this model was short lived. I only booted into Windows once after getting the laptop, and have since purged it from the system (dunno if I can get it back with the recovery partition... oh well).

Many of the function keys are OS based, apparently. Getting the volume buttons to work required maping their key codes to functions and I haven't gotten the CRT/LCD switch to work at all. These are things I don't really care that much about, so its alright for the time being.

Looking forward to hearing about other's experiences with this laptop. Hopefully some tips on power settings to make this battery last a bit longer. Toying around with the laptop_mode to see if that helps any.

---

### Post by boredom_amused on 2006-10-09
well i've got ubuntu running on the laptop and minus the wireless card not being detected and disabling after updating (i've sinced reinstalled and not updated.) everything important is working pretty well. The only bluetooth device i have isn't linux supported, so i have no idea if it works or not. the fingerprint reader doesn't work but I think some brilliant people are figuring it all out so i'm going to wait and see. 
The volume buttons work for me, including the Fn ones. 
Also, of the F Fn keys, F4, F7, and F12 don't work for me. 

I was using windows for a few weeks until i finally installed ubuntu, and i can tell you exor|grey, you're not missing anything. The volume controls would open up the windows volume control panel which was ugly. there's a tonne of useless programs included as well and the general thousand and one typical windows drama that everyone goes through. 

Also, yes, the battery doesn't last very long. (only about 4 hours max with a 6cell.) I've been just doing the standard low screen contrast and disabling the wireless and radio to save power.

---

### Post by jcoonrod on 2006-10-10
I've installed Ubuntu 6.1 beta on my v100 and found that the wireless works great, but that suspend and hibernate both fail to reawaken. 

For those co-habiting with XP, you can delete the IBM_SERVICE partition and install Ubuntu there, but you have to delete the partition from inside Ubuntu from the live disk and then run install.

---

### Post by cmavr8 on 2006-11-08
Another V100 - Ubuntu 6.10 Edgy user here.

I have been running dapper for a few months and have been fighting with different problems.

I fresh installed 6.10 (upgrade from dapper would make things worse) and the card reader now works. The wifi is almost perfect (you can suspend/hibernate and it almost always becomes ok when you resume) and the radio kill button works seamlessly.

My major problem is sound, which works 2/6 reboots... I've tried all sorts of "solutions", designed for N100 laptop but can't make it work permanently...

Do you guys with the ubuntu 6.10 have sound problems?

Camera, fingerprint, bluetooth are things I have not researched on. I think fingerprint can be done, camera can't. 

cu!

---

### Post by pillu on 2006-11-21
I got a Lenovo N100 laptop and installed Ubuntu on it. Can't say that I am enjoying it though. The sound doesn't work at all though Ubuntu detects sound card fine. Wireless is slightly slow - I think its a DNS problem. Haven't looked into fingerprint and other stuff yet. Its going to be a long hard slog....

---

### Post by cmavr8 on 2006-11-21
Hi pillu, welcome to the strive-to-make-your-laptop-work club...

I think there is a dedicated forum for N100 owners.. Search around the forum.

There are also lots of possible solutions out there.. Go for it! Try! Just remember to backup any files you modify..

---

### Post by Plume on 2007-02-27
Hello, users of lenovo V100,

I plan to buy a new laptop and install my first ubuntu on it. The Lenovo V100 is my first choice candidate. As you are using it, could you please give me your opinion on it ? (do you recommend it to a linux absolute beginner ?).

I opened a new post for that topic : [http://www.ubuntuforums.org/showthread.php?t=369423&highlight=lenovo+V100]("http://www.ubuntuforums.org/showthread.php?t=369423&highlight=lenovo+V100")
I did not get any answer yet, I hope someone can help me a bit with my choice.

And by the way, what about writing in the wiki documentation about this laptop ? There seem to be quite some people using it now...

thanks in advance !

---

### Post by cmavr8 on 2007-02-28
Ok, I have replied to the other thread Plume started. 

READERS PLEASE VISIT THE OTHER THREAD...

---

### Post by cmavr8 on 2007-04-10
Running Ubuntu Edgy Eft now.
You can see my problem's description in the picture.

---

### Post by cmavr8 on 2007-04-23
Upgraded to Feisty Fawn 7.04.

Sound even worse now. Skype won't recognise my sound devices. Avidemux won't play audio ("trouble initializing audio device" error when ALSA is selected, no error, no sound when DUMMY selected) and Totem Movie player won't start (crashes on start).

reinstalled audio device but nothing changed...

Rhythmbox plays music normally

---

### Post by chengster on 2008-03-13
I'm running 7.10, and I have no sound whatsoever. The volume controls do work, it shows a volume pop-up, but nothing comes out. I've tried using headphones too but no luck. I'm kinda at a loss as to what to do, I'm now to all of this. Help?
-Ehren

---

### Post by cmavr8 on 2008-03-13
Try the command alsamixer and fiddle with the settings. I think you'll solve it.

---

### Post by chengster on 2008-03-13
No dice. The volume is up in there too.

---

