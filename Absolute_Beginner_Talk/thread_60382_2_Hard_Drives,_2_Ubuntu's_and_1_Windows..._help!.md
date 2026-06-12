---
title: "2 Hard Drives, 2 Ubuntu's and 1 Windows... help!"
date: 2005-08-27
forum: Absolute Beginner Talk
---

### Post by noob_Lance on 2005-08-27
Hey, 

I have an issue! big issue. 

Ok so i have 2 80 gig HDs, one had Windows XP and Ubuntu, the other is jsut Ubuntu. Except i have a problem with my first HD... the GRUB Loader is giving me error 17 so i have to unhook it if i want to get on my computer. How can i get it to load up from my second hard drive first and not touch my first one... yet leave it so i can actually mount it and grab all my files ???

Oh also.... i cant get JRE to install... and not bein able to download music is KILLIN me lol someone help me

and yes i have done
sudo apt-get update
and still it cant find it =@

Thanks
~Lance

---

### Post by edwina on 2005-08-27
I don't have a solution, I'm afraid, but I have a feeling that XP has to be on the first partition of your first hard-drive. Have you got it set up so that your Ubuntu-only drive is your first IDE drive? Just a thought - you're probably far better at this than me!

There is another, recent, thread on JRE. Search for "Java Runtime". I think there is a temporary problem somewhere.

---

### Post by xequence on 2005-08-27
Yes, I think so too... Windows thinks it is the only OS around and therefore (Atleast I think...) wont work with any other ones. Grub fools it into thinking it is the only one. You should install windows first then ubuntu. I dont have any experience with more then one drive though...

---

### Post by noob_Lance on 2005-08-27
didnt work... switched the master and slave settings... and it didnt work... gave me an error that i couldnt... :|

---

### Post by edwina on 2005-08-27
You can't just swap master and slave, as I understand it. XP actually needs to be on the first IDE channel (or virtual IDE if you're using SATA drives).

Can you give us some more information? Was GRUB working before, booting XP and Ubuntu, but now it is broken? Are you saying that you can unhook the first drive, with XP and Ubuntu, then boot purely from the second? Could it be that the Master Boot Record (MBR) is on your XP drive, or is it on the Ubuntu-only drive?

The more information and history you can give us, the better.

---

### Post by noob_Lance on 2005-08-27
hey, yea i can just unhook my first HD and boot right off the second. And yes Grub was working before... except i f'ed windows up and it didnt actually boot :p but it is still there. and yes now grub dosnt work. 

It was 2 days ago i installed this copy of Ubuntu and i dont remember if i had the other HD in or not... would that info help at all?

---

### Post by edwina on 2005-08-28
Hmmmm. If you can boot from the non-XP drive, that implies (to me, as a bit of a noob) that the MBR is on that other drive. This would prevent XP being accessible.

What I don't understand is what has suddenly gone wrong with GRUB. You were booting up previously with both hard-drives plugged in (albeit with no access to XP) and had access to both drives? Did XP ever work with this set-up?

You might try the following, in case your GRUB or MBR are stuffed up in some way :-

1) Check your BIOS settings with both drives plugged in. Ensure that the XP drive is on IDE 0 or IDE1, ahead of the Ubuntu-only drive. If it isn't, do some unplugging and make it so that it is.

2) Boot into the Ubuntu-only drive (by unplugging the other one, if necessary), find your menu.lst file and post the contents here. menu.lst is in /boot/grub/

3) Use a LiveCD to boot with your second drive plugged in. Find the menu.lst file on the second drive and post the contents here as well. Also find the boot.ini file on your XP partition (at the very top of the file structure, in what would be C:/) and post the contents of that here too.

Somewhere in those three files should be the info that we need to try and resolve this one. If not, I'm out of ideas I'm afraid.

---

### Post by noob_Lance on 2005-08-28
nvm... i went into the BIOS and changed the boot sequence to boot the second HD first

---

