---
title: "Upgrading XP to Vista - GRUB help."
date: 2007-08-07
forum: Absolute Beginner Talk
---

### Post by Rovdjur on 2007-08-07
Right now I have a dual boot of Windows XP Pro and Kubuntu. My video card is not recognized in XP as well as it should be, and there are better drivers in Vista for it, so I plan on popping in my Vista CD and choosing the upgrade option.

When I do this will I lose my GRUB boot menu? If so, what would be the easiest way to getting it back so I can default boot into Kubuntu? And also, would the boot options be the same for XP in the GRUB configuration, or will I have to change some stuff (other than the name, obviously).

Thanks :D

---

### Post by LaRoza on 2007-08-07
You will have to restore grub, actually, I have no idea how what the upgrade will do to your harddisk.

I would back up any data you have, and be prepared to fix and reinstall Ubuntu, just in case.

After you "upgrade", you will have to restore grub. Search the forum for that, it is around somewhere.

If you don't have more than 1 GB of RAM, DON'T upgrade to Vista, it won't work. (Experience here)

---

### Post by oilchangeguy on 2007-08-07
> **Rovdjur said:**
> Right now I have a dual boot of Windows XP Pro and Kubuntu. My video card is not recognized in XP as well as it should be, and there are better drivers in Vista for it, so I plan on popping in my Vista CD and choosing the upgrade option.

When I do this will I lose my GRUB boot menu? If so, what would be the easiest way to getting it back so I can default boot into Kubuntu? And also, would the boot options be the same for XP in the GRUB configuration, or will I have to change some stuff (other than the name, obviously).

Thanks :D

do you have the driver cd that came with the video card? have you been to card mfg. website for drivers? if you're using a legal copy of xp have you been to microsoft's website, and downloaded upates (select custom, not critical, to see all updates), there may be a video card update available.

---

### Post by Rovdjur on 2007-08-07
> **LaRoza said:**
> You will have to restore grub, actually, I have no idea how what the upgrade will do to your harddisk.

I would back up any data you have, and be prepared to fix and reinstall Ubuntu, just in case.

After you "upgrade", you will have to restore grub. Search the forum for that, it is around somewhere.

If you don't have more than 1 GB of RAM, DON'T upgrade to Vista, it won't work. (Experience here)

Well my laptop sufices for Vista's prerequisites, so I'll be fine. I am already backing up my Kubuntu partition right now and hopefully nothing bad will happen. I just wanted to check on here before I did anything.

---

### Post by oilchangeguy on 2007-08-07
> **Rovdjur said:**
> Well my laptop sufices for Vista's prerequisites, so I'll be fine. I am already backing up my Kubuntu partition right now and hopefully nothing bad will happen. I just wanted to check on here before I did anything.

did you read post #3?

---

### Post by lisati on 2007-08-07
My experience of re-installing Windows (for me it was by way of a destructive system restore because of to much junk) is that Grub had to be re-installed. Good luck!

---

### Post by ayenack on 2007-08-07
If you haven't got an U/X/Kubuntu live CD you'll need to download [SuperGrubDisk]("http://supergrub.forjamari.linex.org/?section=download") and use that to re-install your grub. If you have a Live CD do [this]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_restore_GRUB_menu_after_Windows_installation").

---

### Post by Rovdjur on 2007-08-07
> **oilchangeguy said:**
> do you have the driver cd that came with the video card? have you been to card mfg. website for drivers? if you're using a legal copy of xp have you been to microsoft's website, and downloaded upates (select custom, not critical, to see all updates), there may be a video card update available.

Haha, I am actually in an odd position. The video card in my laptop is, in fact, ***not*** supported by ATI. They manufacture the card and leave it up to the computer company to write the drivers. All of my versions of Windows are 100% purchased and legal. I have already spent countless hours on the phone with both ATI and Lenovo. My laptop came with Vista preinstalled, but I never liked Vista, so I ordered a Windows XP Pro restore CD set from Lenovo. It comes with all the drivers preinstalled for my exact model number. It installs drivers for the video card, but they are not 100% correct. [[COLOR="Blue"]It says my video card is 512MB Hypermemory when it is in fact 256MB dedicated memory[/COLOR]]("http://pics.krasch.org/albums/userpics/ati.jpg"). Therefore, the performance is terrible.

In Vista, the drivers work flawlessly, but the XP drivers are horrible. I even called Lenovo asking if there were newer drivers out for my card, and they guy gave me a link for driver version 8.29 saying it was the latest they had, but I had version 8.33, so I had a newer version than he thought existed.

In short, they messed up the drivers for the XP and I need Vista in order to get the true performance :(

---

### Post by Rovdjur on 2007-08-07
> **lisati said:**
> My experience of re-installing Windows (for me it was by way of a destructive system restore because of to much junk) is that Grub had to be re-installed. Good luck!

Bleh, I figured I'd have to, haha. Thanks :D

---

### Post by Rovdjur on 2007-08-07
> **ayenack said:**
> If you haven't got an U/X/Kubuntu live CD you'll need to download [SuperGrubDisk]("http://supergrub.forjamari.linex.org/?section=download") and use that to re-install your grub. If you have a Live CD do [this]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_restore_GRUB_menu_after_Windows_installation").

Awesome! As soon as the data is done backing up, I shall give it a shot :)

---

### Post by Rovdjur on 2007-08-07
> **oilchangeguy said:**
> did you read post #3?

Gotta give me time to type my response!

Look at Post #8 :)

---

### Post by oilchangeguy on 2007-08-07
> **Rovdjur said:**
> Gotta give me time to type my response!

Look at Post #8 :)

uh, i did. and you responded. so don't understand the need for this post.

---

### Post by cobrn1 on 2007-08-07
Are you sure that you want to upgrade install vista? I've heard that it can lead to many bugs and headaches. You might be better advised to back up you data and wipe the XP partition, and then clean install vista (but it depends on what licence of vista you have - god I'm glad to use ubuntu! you never realise how great the licencing terms are until you look at microsoft's!)

Anyway, you'll want to download super GRUB disc so that after the installation of vista you can but GRUB back onto the MBR.

Best of luck.

---

### Post by Rovdjur on 2007-08-07
> **cobrn1 said:**
> Are you sure that you want to upgrade install vista? I've heard that it can lead to many bugs and headaches. You might be better advised to back up you data and wipe the XP partition, and then clean install vista (but it depends on what licence of vista you have - god I'm glad to use ubuntu! you never realise how great the licencing terms are until you look at microsoft's!)

Anyway, you'll want to download super GRUB disc so that after the installation of vista you can but GRUB back onto the MBR.

Best of luck.

Well the beautiful thing is that I have NO data whatsoever on my Windows partition. I only installed it for gaming, which it can not handle. So I figured a quick upgrade would work.

However, it probably would be better to do a clean install. I'll give it a shot, and see if the Vista installer can recognize my windows partition and do an install on it. I hope it doesn't give me some stupid error :(

---

### Post by ayenack on 2007-08-07
Why not try the upgrade first then if that seems buggy to you wipe your disk and do a clean install. To me this would seem a better way to go at first.

---

### Post by oilchangeguy on 2007-08-07
> **ayenack said:**
> Why not try the upgrade first then if that seems buggy to you wipe your disk and a clean install. To me this would seem a better way to go a first.

if you've followed along, the user states the computer came pre-loaded with vista. so i'm sure they mean, do a factory restore. not upgrade, from xp to vista.

---

### Post by Rovdjur on 2007-08-07
> **oilchangeguy said:**
> if you've followed along, the user states the computer came pre-loaded with vista. so i'm sure they mean, do a factory restore. not upgrade, from xp to vista.

Well actually I do mean upgrade from XP to Vista.

I have an actual store-bought (my father purchased it for his machine) Vista CD which I plan on popping in and trying out. We'll see what happens.

---

### Post by ayenack on 2007-08-07
If you read his first post you will see that he states that he will upgrade with his Vista CD. Take a look it's on the first line I think. You could be right that he has a restore DVD but that is not what he stated.

---

### Post by oilchangeguy on 2007-08-07
> **Rovdjur said:**
> Well actually I do mean upgrade from XP to Vista.

I have an actual store-bought (my father purchased it for his machine) Vista CD which I plan on popping in and trying out. We'll see what happens.

in view of the driver problems you're having, the restore would probably be a better choice. the vista only cd may not contain the same drivers the restore will.

---

### Post by Rovdjur on 2007-08-07
> **oilchangeguy said:**
> in view of the driver problems you're having, the restore would probably be a better choice. the vista only cd may not contain the same drivers the restore will.

But the Restore would definitely get rid of my Kubuntu partition which I have worked so hard to get to work properly. Lenovo has a program that you can download and it will automatically download and install all the necessary drivers for your laptop model (I have done that several times before. This laptop has been through a lot), So the Vista should work flawlessly, other than the fact that it is running Vista :-P

---

### Post by cobrn1 on 2007-08-07
> **ayenack said:**
> Why not try the upgrade first then if that seems buggy to you wipe your disk and do a clean install. To me this would seem a better way to go at first.

This sounds like it makes sense, but I would strongly recommend just doing a clean instal, particularly as you have no data to back up...

ayenack, I don't know what you windows experienc is like, but incase you don't know, upgrading isn't as easy with windows as it is with linux - infact, it's just asking for trouble in windows, and issues could crop up later.

I recommend doing the clean install of vista, just save your self the hassle of installing twice...

---

