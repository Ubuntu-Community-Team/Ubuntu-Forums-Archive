---
title: "I can't take any more Ubuntu Gutsy Gibbon"
date: 2007-10-28
forum: Absolute Beginner Talk
---

### Post by El Cabrón on 2007-10-28
OK folks.... I've had enough. I like Ubuntu, a whole lot, but spending every waking moment trying to get things working is getting old. Today I bought a 500GB Maxtor drive and it took 2 hours to get it working. 2 hours! Why? I will say it worked at first but it was very odd. Here's what happened. 

Using KDE, I opened the drive from the mount point with Dolphin. I saw all the autorun.ini and other folders that came loaded on the drive but I didn't want to delete them. Instead, I made a new folder on the drive called "Maxtor Stuff" and tried to copy everything in that folder. No way! Every time I dragged something to the folder "Maxtor Stuff" it kept warning me that I was about to "copy the files over themselves". Believe me, I was not missing the folder or making any error in the process. It just wouldn't let me do it. I had to open "Maxtor Stuff" in the current Dolphin window and then open the 500GB Maxtor drive in another Dolphin process. Once I had two Dolphin programs up I was able to drag folders from one Dolphin window to the other. That worked. Is this a bug? I looked everywhere but couldn't find one.

Then, While backing up my stuff to my new drive I learned that NONE of my music files would copy over. Why? They copied to my HDD from my USB stick? It turns out that these music files are titled in Spanish, with Spanish Characters (words). The fact that my USB Stick is FAT32 didn't make a difference but when I tried to copy them to my 500GB NTFS partition that's when I realized NTFS-g3 or Dolphin can't handle Spanish characters in file names. So either I format the drive to Fat32 or rename 4 gigs of mp3's. That's just plain wrong! They're back on the stick now!

It's not done here. In an effort to get my NVIDIA GeForce 420 working I tried to select a different driver. That didn't work so I went back to NVDIA Generic and rebooted. Hey! Now my external drives won't load? All I get is "You don't have permission" errors. So, I unplug them and plug them in again and they still wont mount. I go into the KDE drive manager and it tells me I have an orphaned "something or rather" So, I disconnect all the drives and restart. Once it's up I plug the drives in and nothing happens. Now I restart again, drives connected, and they come up this time. Why is that?

I like my drives and having the ability to move them from home to the office is great! I like KDE too but I don't like the USB icon on the Desktop for my external hard drive so I tried to change it. (Guess where this is going) Yep, I "Right Clicky" on the Desktop USB Icon for my 500GB drive and see an icon there but it's a folder icon. Hmmm? I change it to a mounted drive icon but to no avail. It's still a USB icon on the desktop. Well, I go back to the properties and select the wrench icon to edit the "file types"and in there I see the USB icon. Ah HA! So I change it to a mounted HDD icon and blam! Now everything I plug into my firewire and USB shows up as a mounted HDD icon. But thats not what I wanted. My Firewire drive is permanent and I wanted it to be "anatomically" represented by an HDD icon. I didn't want ALL of my external devices to have the same icon. I have found no cure for this other than to go back to the USB icon, which I have and it looks stupid.

Since my upgrade to Gutsy I've had Firefox randomly close, system freezing randomly and loss of external devices on a daily basis. I still can't get my NVIDIA 420 working and I really need Google Maps. But it's not just drives and quirks here and there. It's a bunch of little things that are way too time consuming to resolve. Feisty didn't give me grief like this.

Lastly, Just so you know... The Adept Updater has a type-o of sorts. I think it is an OMEN.

The Adept Updater came up and read, **"A new distribution is available. Click next if you wish to upgrade now"** Unfortunately, the only options to click are "Version Upgrade" or "Quit". Where's the **"Next"** button?

It's that "press any key" thing. 

Do I go back to Feisty?

---

### Post by Crafty Kisses on 2007-10-28
Right now, I'm staying with Feisty, not because Gutsy is a bad OS or anything. I just want all the Gutsy problems to get worked out, If I were you I'd stick with Gutsy and wait a couple of weeks untill all the updates come out for it, be patient man. :)

---

### Post by barkej on 2007-10-28
While Gutsy is a final release it is still young. From the sounds of it you would be better off with Feisty if matters are pressing however most of the bugs should not be an issue within a few weeks.

---

### Post by Crafty Kisses on 2007-10-28
> **barkej said:**
> While Gutsy is a final release it is still young. From the sounds of it you would be better off with Feisty till some of the kinks get fixed in Gutsy.

Which that will be fairly soon. :KS

---

### Post by El Cabrón on 2007-10-28
OK, I could access my drive last night but this morning I'm right back to the "Permission Denied" message. I have full access privelleges! 

That's pretty much it for me. I'm going back to Feisty, disgruntled.

---

### Post by sayuki288 on 2007-10-28
maybe your drive doesn't just like you :lolflag:

---

### Post by kellemes on 2007-10-28
> **El Cabrón said:**
> OK, I could access my drive last night but this morning I'm right back to the "Permission Denied" message. I have full access privelleges! 

That's pretty much it for me. I'm going back to Feisty, disgruntled.

How have you setup fstab?

---

### Post by limac on 2007-10-28
Be patient for the new updates . Same thing happened to me with patience. And then I learned that patience in being a successfull linux user is very very neccessary.

I am also a gutsy user and I reported a couple of bugs and hopefully they are worked out. And I personally LOVE gutsy. Trust me, I have used pclinuxos and u have to do a lot more work on it to get that working perfectly.

---

### Post by floke on 2007-10-28
My thoughts on this are here

[http://ubuntuforums.org/showthread.php?t=594210](http://ubuntuforums.org/showthread.php?t=594210)

Unfortunately, ubuntuforums won't let you discuss it.

---

### Post by vincentvee on 2007-11-11
it's been two weeks and i still have problems with it....went back to feisty....waiting for the next LTS then i might go gutsy

> **Codename said:**
> Right now, I'm staying with Feisty, not because Gutsy is a bad OS or anything. I just want all the Gutsy problems to get worked out, If I were you I'd stick with Gutsy and wait a couple of weeks untill all the updates come out for it, be patient man. :)

---

### Post by joker on 2007-11-24
I had the same issue with the filenames, it is a limitation of NTFS-3G and has been around forever,  However the fix is fairly simple and you will only have to do it once.

Install Kid3 (or your mp3 tagger of choice in linux) then use the "rename file from ID3 tag" option to rename your files (assuming they have good tags) and you are all done.  As long as all your umlouts, tildas, and accent marks are in your tags they will be preserved in the filename but converted to UTF-8 format readable and transferable by (and between) both windows and linux.

---

