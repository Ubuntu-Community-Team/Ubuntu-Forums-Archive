---
title: "Windows wont boot"
date: 2006-11-22
forum: Absolute Beginner Talk
---

### Post by RideP2 on 2006-11-22
Ok, so I have two hd's. My primary, a 40 gig, with Windows XP on it, and a 300 gig slave, with Ubuntu installed. 

Now my GRUB Bootloader is on hda and I can boot Ubuntu no problem. But the problem is when I go to load windows, it does not give me an error but after the screen were you see the logo and the blue bar moving below it, and it goes to the screen with the blue background and little Windows Xp logo (Normally you would only see this screen a few seconds before your account thing pops up and asks for the pass) and just stays there. 

What could be causing this?

---

### Post by stupidkid on 2006-11-22
Most likely it's not Ubuntu's fault. The things Linux messes up the most are MBR and boot sector (most distros can't write NTFS by default). And since Windows boots, it might be Window's problem.

---

### Post by RideP2 on 2006-11-22
I'm not blaming Ubuntu or nothing, but is there a way to fix this? I want to go play WoW :P

---

### Post by bilange on 2006-11-22
Are you talking about [this screen]("http://www.updatexp.com/images/chkdskbluelge.jpg")?

Boot with a WindowsXP CD and try the Recovery/repair tool ("press R" thingie), but I don't know if this will reset the MBR, though. If you dont want to risk not seeing your Ubuntu installation, don't do this (or wait so someone else can comment and say if doing the Repair process will reset the MBR or not)

---

### Post by RideP2 on 2006-11-22
K, well I reinstalled Ubuntu and that dident do nothing (Dident loose nothing it was a fresh install anyways) And its not that screen.. Like you know when it first boots up there that blue thing under the logo going back and forth, then theres another screen right before you pick the accout you want, like basicly it jams right before giving me what account i want.

---

### Post by krotaz on 2006-11-23
I got the same problem of yours.

It took 1 hour to see the WELCOME screen (I wasn't able to look at the desktop). I think that the problem is that Windows always wants to be the only one installed on the HD and obviously its boot.ini too.

What I did is re install the hole thing, but I installed linux on the sata disk first, then install windows on the Pata disk and finally configure the grub to see my linux partition.

Another friend thinks that windows has some problems with those SATA motherboards that bring the driver on a floppy (who on earth stills have a floppy??) and something may be causing windows to fail.

Bye

---

### Post by hypnotic_frog on 2006-11-23
well if problem can't be solved always can reinstall OS! ;)

---

### Post by bilange on 2006-11-23
> **RideP2 said:**
> Like you know when it first boots up there that blue thing under the logo going back and forth, then theres another screen right before you pick the accout you want, like basicly it jams right before giving me what account i want.

Oh, this screen... well in this case, if you can't even boot Windows XP (and get to the desktop) in [safe mode]("http://www.pcstats.com/articleview.cfm?articleID=1643"), chances are that you *may* have to reinstall XP, in the worst case scenario. 

Now that I know which screen you mean, are you actually logging in with the [NT Stytle login]("http://www.ryerson.ca/acs/usersguide/graphics/Windows%20Pictures/windowsxplogin.png"), or the fancy  [user-friendly XP style]("http://www.winsupersite.com/images/showcase/winxp_login.jpg")?

If you happen to usually login with the NT Style, when the bootup seem to hang, there should be something written near the bottom of the window, like "Preparing network connections" or something else-- whats written here? This may help troubleshoot the login problem. Type "*whatever text when it hangs* +hang" or something like that in google, and if you're lucky maybe you'll find others with the same issue.

If you happen to login with the XP eyecandy interface, maybe you should consider going to safe mode to swith the login type to the NT one, as it will at least give you an indication of where it did hang. If you're at ease at going into the registry, [follow this guide]("http://www.winguides.com/registry/display.php/972/") to change you login type.

---

### Post by steve.horsley on 2006-11-23
Have you completely turned the PC off and on again? I am wondering if Ubuntu left the network card in a state that Windows doesn't like, or something easy like that.

Just a hopeful guess.

---

### Post by RideP2 on 2006-11-23
I'm using the "Fancy" loggin screen. I'll probly just reinstall windows. If it wasent for WoW I'd forget about linux.

---

### Post by kiyometane on 2006-11-23
Put your windows cd and go to recovery console.
Type in the command "fixboot" or "fixboot c"
fixboot will not delete your MBR
Click yes and reboot.

If it does not work, you will have to delete MBR and create a new one with 
"fixmbr". 
But you will have to restore you ubuntu boot loader. Someone can help you in doing so, no need to fresh install of ubuntu.

---

### Post by steevk on 2006-11-23
You'd forget about Linux? Is that a typo?

If WoW is the only thing you use Windows for, I'd really suggest WINE...it runs really well on my computer...have you tried doing that yet?

---

### Post by RideP2 on 2006-11-23
My bad steevk, I meant to say windows. As for wine I dont have much experience with it and I dident think it could connect to the internet.. Cause I wanted to run Ares and it never connected. I'll try to do the fixboot or fixboot c command tomorrow.. It's getting late and I don't realy feel like playing around with that.

---

### Post by kiyometane on 2006-11-23
> **steevk said:**
> You'd forget about Linux? Is that a typo?

If WoW is the only thing you use Windows for, I'd really suggest WINE...it runs really well on my computer...have you tried doing that yet?

his problem was to access windows

---

### Post by RideP2 on 2006-11-23
If I could atleast accest the files I'd be ok, but I cant even get to the drive with Ubuntu gives me an error. 
"error: device /dev/hdb1 is not removable

 error: could not execute pmount"

---

### Post by RideP2 on 2006-11-24
Does anyone know what could be causing this?

---

### Post by steevk on 2006-11-24
> **RideP2 said:**
> My bad steevk, I meant to say windows.

Don't worry about it, I was just making sure that I was getting my facts straight :) 

I don't know much about your error, but check out [this]("https://help.ubuntu.com/community/WorldofWarcraft") wiki entry. It's worked correctly for me every time, and I actually get slightly better performance under WINE than in Windows...

---

### Post by RideP2 on 2006-11-24
Wow, quick reply, I'll go check that out.

---

### Post by RideP2 on 2006-11-24
When they say copy all the files into a folder, is that one folder then everything in there, or a folder then like sub-folder for each disk?

---

### Post by steevk on 2006-11-24
Just one big folder.

---

