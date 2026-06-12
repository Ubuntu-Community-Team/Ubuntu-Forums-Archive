---
title: "Help!  LinuxNewbie needs complex multi-boot advice"
date: 2007-03-24
forum: Absolute Beginner Talk
---

### Post by pketch on 2007-03-24
Hi Everyone!

I've been using Ubuntu as my primary OS now for about a month and I really think I'm going to stay with it.  I am extremely technical - I am an IT guy but have always worked and coded in an all-Windows environment and I am still very much a Linux newbie.  I've had a small Linux setup on my computer for years, but really only dabbled with it as I never could get everything working the way I needed it to to use as a primary OS.  All of that has changed now that I've been working with Ubuntu - for the first time I'm really able to do everything (and I mean everything!) I did in Windows on my home PC with Ubuntu...and with XGL & Beryl loaded, frankly I find the desktop experience to be more pleasing than XP or Vista by far.  Unfortunately, I am still a Linux newbie, relatively speaking anyway.  Now that I am comfortable using Ubuntu I want to make some boot/partition changes and try out some new stuff, but it took me a while to get both my Ubuntu 6.10 setup as well as my multi-boot just right and I REALLY don't want to mess up all that work.  I'm really hoping that some more experienced Linux/Ubuntu users out there can give me some advice.  I know it might get a little complicated, and I apologize in advance.. I'm really just seeking some more experienced input into what I'm about to undertake, and if what I'm proposing isn't very feasible, I apologize, but I had to ask.

I also will create ghost images of my hard drives as a back up before I go messing around with them JUST in case I hose something (Which is likely as you will see).

Ok, here goes.. .this is what my current setup is:

Hard drive 0 (250GB):
Partition 0: 50 GB /  Windows XP (NTFS)
Partition 1: 100 GB / Windows Vista (NTFS)
100GB of unpartitioned Space

Hard drive 1 (200GB):
Partition 0: 180GB / No OS installed, NTFS filesystem
Partition 1: 19GB / Ubuntu 6.10 Edgy (EXT3)
Partition 2: 1GB / Ubuntu boot partition (EXT3)


When I power on my PC, GRUB loads up and I get a choice between my Ubuntu 6.10 kernels or my Windows Bootloader.  If I choose the top kernal, Ubuntu loads just fine.  If I choose the Windows bootloader, it drops me into the Vista bootloader where I can choose between Windows XP & Windows Vista.

Alright, that said, THIS is what I want to do WITHOUT blowing up my Ubuntu 6.10 install or my Windows stuff:

1. Install a copy of Ubuntu Ultimate Edition to check it out (Which I gather is just Edgy Eft with a bunch of things pre-loaded and some new themes).  I'm thinking I should install that on the unpartitioned space on my first hard drive.  Remember I still want to be able to boot to my working 6.10 install.

2. After I've checked it out, I want to completely get rid of the Ubuntu Ultimate Edition and install the current Ubuntu 7.04 Feisty Fawn beta in its place so I can check it out and run the short and long beta tests to send the results in to Ubuntu and do a little something for the distro.

3. When I'm done with that, I plan to completely erase the beta install and delete any partitions created during my tests in 1 & 2 leaving that 100GB free again on drive 0.

4. I want to then wait until the final version of Feisty Fawn is released next month and install that to the 100GB unpartitioned space on drive 0.  This will become my main OS.

5. I briefly want to be able to keep using my 6.10 install while I'm getting Feisty fawn just right in case it takes me a few days to get it all working.

6. When Feisty Fawn is finally configured and working exactly like I want it to, I just want to wipe out those two Linux partitions on drive 1 and expand partition 1 on that drive to take that newly freed up space.

So, finally, next month I want my setup to be this:

Hard drive 0 (250GB):
Partition 0: 50 GB / Windows XP (NTFS)
Partition 1: 100 GB / Windows Vista (NTFS)
Partition 2: 99GB / Ubuntu 7.04 Feisty (EXT3)
Partition 3: 1GB / Ubuntu Boot Partition (EXT3)

Hard drive 1 (200GB):
Partition 0: 200GB / No OS installed, NTFS filesystem

After that, I'll be done and will run like this indefinitely.

Is all of this possible or am I just totally crazy here?

Thanks in advance for any advice, and I'm sorry for the length of the post.

Regards,

-Pablo

---

### Post by hansoffate on 2007-03-24
Your idea sounds good and should work.  Just make sure your bootloader knows it.

-Hans

---

### Post by chewearn on 2007-03-24
Only one thing I am not sure regarding your idea: how does the windows bootloader works in Vista?  Is it basically same as XP and can survive a MBR overwritten by grub?
If grub currently already residing in disk 0 MBR, then it should be ok.

---

### Post by freebird54 on 2007-03-24
Certainly sounds possible. **BUT DO NOT LET GRUB ONTO drive 0**

You should certainly have no trouble editing your existing grub menu.lst on drive 1 to look for the 'new' Ubuntu if necessary - so do NOT let any of the new installs put GRUB onto your windows boot drive, or you will have to re-create the Vista boot loader you use for both Windows selections.

I am not sure if it will recognize the pre-existing GRUB on drive 1 - but no probs if it does not - you can easily add in whatever is needed.

I am doing similar things here - and it hasn't been a problem  (Kubuntu and Xubuntu and Feisty have been through the 'have a look' stages without trashing XP or Edgy so far!)

Enjoy - it is kind of fun to multi-multi boot lots of choices - though I find that XP is becoming more and painful every time I look at it (if only because it takes to update AV and firewall, and it wants to scan and all the mail tries to get to Outlook and....

---

### Post by pketch on 2007-03-24
Hey thanks for the quick replies!  From both of your comments, it sounds like this might actually work if I'm careful about it.

From what I can tell the Vista bootloader is indeed a little different than the XP bootloader and it was a bit of a pain to get the triple boot going in the first place (Typical M$ junk), but you are correct - GRUB is already residing on disk 0 so that should be a big plus.  That being the case, I'm not really worried so much about it messing up my Windows OS's.. My guess is GRUB will just pass off control to the Vista boot loader without too much trouble if I can figure out how to get the entries right.  What I'm really worried about is hosing my Edgy install and configuring GRUB correctly.

The thing I'm unsure about is how to go about configuring GRUB to make it play nice with the two linux distros.  I mean, with my current setup I'll boot the Ubuntu Ultimate live DVD which is basically the default Edgy Eft installer and tell it to "Automatically use largest available contiguous free space" on drive 0.  But then what -  where does the GRUB config come in? I wonder if it will detect my existing Ubuntu install and read the GRUB entries that are already in there.  How do I tell GRUB to allow me to boot both the new distro as well as the old and not lose the windows boot loader entry?

Thanks again for the advice!

---

### Post by freebird54 on 2007-03-24
You won't hose your Edgy if you don't allow anything onto its current partitions!  I suggest that you do your partition tables in manual mode - so you KNOW what it is doing through the installs.  Just double-check as you go along.  I suggest that you use the '3 partition' setup for any Linux installs - meaning  1gb swap, 10gb root, and the rest mounted as /home .  It just seems cleaner somehow :)

As for editing grub - I suggest that you lay your hands on a little GUI script called GrubEd - a search in these forums should turn it up.  Makes it all a little less painful!

---

### Post by chewearn on 2007-03-25
> **freebird54 said:**
> As for editing grub - I suggest that you lay your hands on a little GUI script called GrubEd - a search in these forums should turn it up.  Makes it all a little less painful!

Hey, thanks man :popcorn:

 Another thing I know today, that I didn't know yesterday.

[GrubED]("http://www.ubuntuforums.org/showthread.php?t=228104")

---

### Post by pketch on 2007-03-25
Hey thanks for the advice,

This morning I decided to give it a shot and get Ubuntu ultimate loaded.

I did as you suggested and used the manual partitioning method, and when prompted where to put GRUB, I told it to overwrite the GRUB that was already on my hd0.  Well, it installed perfectly and it didn't break my Edgy install at all.

The only thing negative that happened was that it doubled all of my existing entries in GRUB.. that is, I had the new entries for the Ubuntu Ultimate Edition kernels, then TWO windows entries instead of one, and then two entries for everything I had in my existing Edgy installation.  Kinda weird, but I didn't care much because all my operating systems still booted.

Nice tip about the grubED.. I used that little guy to clean up all those dupe entries.  Now everything is running very smoothly... when I'm done checking out ultimate, I'll just boot to my Edgy install and blow away those three partitions I created and then will use the Feisty beta cd in the exact same way and do manual partitioning again since it worked out so well.  Then I'll just repeat for the feisty final.

Thanks for getting my down the right path on this thing.. Can't believe how well it went.

One last question... when I finally decide to get rid of my Edgy install after Feisty final is out, do you think I can just delete the partitions it's loaded on and then remove the GRUB entries for it?  Or do I have to do something else?

Also, have you guys had much luck doing a dist-upgrade instead of a clean install?  I was just thinking that that might be an option for me when Feisty final comes out instead of starting over.

Thanks!

---

### Post by freebird54 on 2007-03-25
Glad to hear that it went OK - though I surprised myself at how easy it was compared to playing with Win / OS/2 dual boots back when....

Your proposed method for dropping Edgy will work fine - but I would certainly try the dist-upgrade first.  I *KNOW* I will have a lot of little tweaks and 'extra' packages on there by then, that will take time to replace.  Actually I expect to run both an upgrade and a fresh install - and decide after using both which one to keep.  If the clean install is measurably better (less junk/faster/better looking) than the upgrade, then I'll rebuild to see how it goes....

It is so nice to have some choices!

---

