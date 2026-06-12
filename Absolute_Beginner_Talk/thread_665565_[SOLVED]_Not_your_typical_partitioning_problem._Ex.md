---
title: "[SOLVED] Not your typical partitioning problem. Expert help needed."
date: 2008-01-12
forum: Absolute Beginner Talk
---

### Post by Pogeymanz on 2008-01-12
I'll try my best to keep this as breif as possible.

Summary: 
I did heavy repartitioning, including moving my "/" partition and resizing my "/home" partition and now my Ubuntu has lots of problems booting.

More in depth:
My partition table used to look like this:
Primary    /dev/sda1     WindowsXP                 16gigs
Extended
--Logical    /dev/sda6     /home                          6gigs
--Logical    /dev/sda5     /                                 5.5gigs
--Logical    /dev/sda7     swap                          800MB
--Logical    /dev/sda8     other Linux OS /        5.5gigs
Primary    /dev/sda2      HP Recovery                 8gigs

So I made recovery CD's from Windows so that I could delete the recovery partition and add that space to my /home partition which gets pretty full between using two OS's.

Using Gparted LiveCD, this is what I did:
1. Delete /dev/sda2.
2. Grow Extended partition to consume new space.
3. delete /dev/sda8 (didn't want Mandriva anymore either)
4. Move swap so that there was still 6gigs of unused space at the end of my extended partition
5. Moved and Grew /dev/sda5 "/" so that it is now 6.5gigs with about 4 gigs in front of it.
6. grew /dev/sda6 "/home" to 10gigs.
7. left the 6gigs unallocated at the end of the extended partition.

Now my table looks like this:
Primary    /dev/sda1     WindowsXP                 16gigs
Extended
--Logical    /dev/sda6     /home                          10gigs
--Logical    /dev/sda5     /                                 6.5gigs
--Logical    /dev/sda7     swap                          800MB
--unallocated space                                          6.5gigs

Exactly how I wanted it! Hooray.

I restart and Grub loads as normally, with all the same options it had before (even though some don't exist anymore)

I select Ubuntu and get some error about fsck.ext3 and it aborts with "status 9", or something like that. And it goes to a text-prompt, which I leave by using ctrl-alt-delete.

Then it goes to the Ubuntu log-in screen, which looks like it always does. So I type my name and password and hit enter. It gives me a warning that the home directory is designated as /home/rob and it can't find it, so nothing will work right. It asks me if I want to try logging in anyway and I choose 'yes'. It leaves the login screen for a second and then tells me my session lasted less than 10 seconds and I should try to login using a failsafe option. I choose failsafe gnome. Same thing happens. failsafe terminal works, however.

Since I'm such a novice, I didn't really know what to try in the terminal, so I just used nano to open the error log that said the status 9 stuff, which worked. Then I logged out. 

Windows boots fine, I'm using it to type this now.

My thoughts:
I realize that I physically moved the information for the OS on the harddrive. It must be able to load GRUB and not find the information for "/". I think this is what is causing the /home error also. I don't think there is a problem with the /home partition.

I also realize that I could just use my brute force and reinstall Ubuntu using the same /home partition, so I'd have all my settings, but I don't want to spend hours re-downloading programs (I'm looking at you Eclipse). Also, what would I learn doing that?:) 

So, it seems that I need a way to tell Ubuntu that it has relocated. 

As always, the help is always greatly appreciated. Let's make this a learning experience!

-Rob

---

### Post by fiddledd on 2008-01-12
Unfortunealtly I'm nowhere near an expert., however I had a very similar problem recently. I moved and resized some partitions and had errors sinilar to you. I solved it by moving the partitions back to the original order. But afterwards I figured out what I think was happening. I think that the device names and order had changed so for example sda10 had become sda9. Like I said I fixed it, but there has to be an easier way.

---

### Post by fiddledd on 2008-01-12
Sorry if that doesn't make sense I tried to type it faster as I keep posting too late :)

---

### Post by Pogeymanz on 2008-01-12
I'm going to check what my partitions are called useing GpartedLivecd and then I'll open /boot/grub/menu.lst to see if they match.

However, I don't expect that's the problem because I didn't reorder the partitions; I merely resized them, so all the Ubuntu stuff should have the same names.

I'm wondering if there is just a way to have GRUB reconfigure itself; to "redetect" the OS's.

---

### Post by eapache on 2008-01-12
It seems to be an fstab problem. / seems to be working fine, but /home isn't. Boot into recovery mode with grub, then type```
sudo nano /etc/fstab
```find the line that is set as /home and replace the UUID (big long hex string) with /dev/sda6. Make sure it is the right line, because if you set / as /home, bad things happen :P

Save and quit (ctrl-o, ctrl-x) then reboot with```
sudo shutdown -r now
```Hopefully this works.

EDIT: Don't touch grub!!! It seems you can boot both Ubuntu and Windows fine, so don't mess with it.

---

### Post by The Cog on 2008-01-12
Also try the command **mount** just to see if a partition has been mounted on /home. This will distinguish between possible problems:
1 - No partition is being mounted on /home
2 - the home partition has corrupted and the rob directory is gone
3 - the wrong partition is being mounted on /home (and doesn't have a rob directory).

---

### Post by Pogeymanz on 2008-01-12
I tried what eapache said and replaced the Hex-strings with /dev/sda's for both the "/" and the "/home"  in fstab. No help. 

My partitions are numbered the same as before I partitioned.

I just don't think that the /home partition is the root of the problem (pun intended). The first error I get is just booting Ubuntu. The fsck gets an error because it can't find UUID-eaoidfoahdflakjdf. But it does say that /dev/sda6 is clean with blah number of files/clusters. It says it died with status 9. But then Ubuntu loads anyway, and I have the aforementioned problems with the home stuff.

Man, what can be going on?

I'll try the mount check when I get home later. I'm about to go to dinner now. Thank you all.

---

### Post by The Cog on 2008-01-13
It may also be worth running hte command **blkid** to see if the UUIDs are correct. I might be inclined to edit fstab and start using device names instead anyway.

---

### Post by Pogeymanz on 2008-01-13
I did it! I did it! Woot!

All I did was go in to my /home partition, using a LiveCD and delete .cache.

My theory is that the fstab was the only problem, but when I changed it, nothing appeared to change because something bad must have been saved in my .cache.

---

