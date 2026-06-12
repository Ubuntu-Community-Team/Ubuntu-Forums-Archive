---
title: "iPod touch users successfully usign Linux?"
date: 2008-01-09
forum: Absolute Beginner Talk
---

### Post by tigerplug on 2008-01-09
Just wondering has anyone here using one with Ubuntu successfully?

---

### Post by frup on 2008-01-09
I can't say the touch works but the newest nano can work.

Search "New Generation Ipod" in the forum and there is a good thread for getting things working. It involves updating the ipod library that rhythmbox, amarok and gtkpod use allowing them to read the and write to the new ipod database system. 

You also need to set an ID on the ipod etc... There may be easier ways of doing this by now, I am not sure, by 8.04 things should work 100% out of the box I guess.

---

### Post by rod40cool on 2008-01-09
> **tigerplug said:**
> Just wondering has anyone here using one with Ubuntu successfully?

I have successfully synced music Mp3 files with my iPod Touch using Amarok. First you have to jailbreak the iPod (on firmware 1.11) - try [http://www.ipodtouchhacks.com/ipod/touch/hacks/jailbreak/](http://www.ipodtouchhacks.com/ipod/touch/hacks/jailbreak/)  It's not exactly easy as there are quite a few manual steps involved.
You also need to get ipod-convenience which enables you to mount and unmount the ipod for Amarok.
```
sudo apt-get install ipod-convenience
```

Good luck.

---

### Post by raginghampster on 2008-01-09
Wait ... so your playing mp3 files on ipod?

---

### Post by Crumpets and Jam on 2008-01-09
> **tigerplug said:**
> Just wondering has anyone here using one with Ubuntu successfully?

Have a look [here]("https://help.ubuntu.com/community/PortableDevices/iPhone").

---

### Post by bobo on 2008-01-09
> **Crumpets and Jam said:**
> Have a look [here]("https://help.ubuntu.com/community/PortableDevices/iPhone").

I tried what you posted a couple days ago and I followed it word for word.  The thing that happens to me is that when I mount my iPod Touch via the wireless network, Amarok will show my iPod great.  But when I unmount and disconnect from the iPod, ALL my music is gone.  I can't even connect to it via iTunes in Windows, have to reset the device.

Any suggestions?

bobo

---

### Post by rs8000 on 2008-01-10
I too had issues with getting the Ipod Touch to work using the instructions on the Ubuntu community page. They are partially correct but I was able to find a better howto (Thanks Fred Emmont) that when followed works perfectly. There are some steps that are duplicate from the ocmmunity page but there are also some importnat components that a re missing from teh community page. Try following these steps, they worked for me including album art syncing.:


Well, there's a lot of partial instructions on the web, but not a consistent set all the way through, so here's my attempt - hopefully there's enough information here to find everything you need here. Also, this is going to involve resetting your iPod to factory settings, so you'll lose everything currently on it. These instructions should also work on an iPhone - of course, these instructions are for information only, do it at your own risk. Also, sorry, you need a Windows/OSX machine to do the initial setup, and, you need a wireless LAN where you want to sync (with internet connection for setup) - on the plus side, you'll have wireless sync, which even Windows and OSX users don't have :)



   1. Download the 1.1.1 and 1.1.2 firmware images for your iPod Touch/iPhone

   2. Open iTunes, go to your iPod's tab, and shift-click (option-click) "Restore", and select the 1.1.1 firmware image you downloaded earlier

   3. Go to JailBreakMe.com in Safari on the iPod, and click the install link at the bottom

   4. You now have an "Installer" application - run it, then click "Install" at the bottom; click "Tweaks (1.1.1)", then "OktoPrep", and click yes when it asks you if you want to install it

   5. Open iTunes, go to your iPod's tab, and shift-click "Update" (*NOT* "Restore"), and select the 1.1.2 firmware

   6. Download and run the touchfree jailbreak 1.1.2 software - tick "Enable SSH Server", change the password, and press the magic button

   7. Wait a long time for it to finish, and for your iPod to reboot a few times

   8. Click "Install", then "System", and "BSD Subsystem", and say yes when it asks if you're sure

   9. ssh to [email]root@your.ipod.ip.addr[/email]ess, and edit /etc/sshd_config (nano, vi, vim are available), enabling rsa public key authentication

  10. Make a passwordless rsa ssh key

  11. ssh-copy-id it to your [email]root@your.ipod.ip.addr[/email]ess

  12. restart sshd on it (from the "SSH" icon in the iPod's launcher)

  13. Install fuse, sshfs-fuse, and a recent build of libgpod onto the linux machine you want to sync it with

  14. sudo mkdir /mnt/ipod; sudo chmod 755 /mnt/ipod

  15. Mount the iPod's media area with "sshfs [email]root@your.ipod.ip.addr[/email]ess:/var/root/Media /mnt/ipod"

  16. cd to /mnt/ipod

  17. ln -s iTunes_Control iPod_Control

  18. cd iPod_Control/Device

  19. sudo lsusb -v -d 05ac: | grep iSerial | awk '{print $3}' | cut -b1-16  | xargs printf "FirewireGuid: 0x%sn" > SysInfo

  20. Leave /mnt/ipod

  21. fusermount -u /mnt/ipod

  22. Open Amarok, and open the page for configuring media devices (Settings->Configure->Media Devices)

  23. Add a new iPod device, at /mnt/ipod (or /media/ipod, depending on your distribution)

  24. Click the two cog wheels by your iPod in Amarok's list of Media Devices

  25. In the "Pre-connect command" box, type "sshfs -o workaround=rename [email]root@ipod.ip.addres.here[/email]:/var/root/Media /mnt/ipod" ("workaround=rename" fixes issues with album art).

  26. In the "Post-connect command" box, type "fusermount -u /mnt/ipod"

  27. Use Amarok's "Devices" pane to sync music to and from it - remember that you have to exit and restart the Music app on the iPod after syncing (open it, and hold down the home button until it disappears)



If you're a user of a 64-bit distribution, you'll need a small patch for libgpod.

---

### Post by bobo on 2008-01-12
Thanks rs8000!!  Those instructions are great.  I'm having an issue with steps 9-11.  I tried to vi sshd_config file but it comes up as a blank file.  I'm also unclear on how to make a passwordless rsa ssh key nor do I understand how to ssh-copy-id.  Any help that you can provide would be great.

Thanks again.

bobo

---

### Post by Cam1223 on 2008-01-13
Im going to go through these steps in a few but u said 64bit users need a patch for libgpod, do u think u could link me somewhere to the patch or somewhere where it talks about that. i have libgpod2 and libgpod-common i want to know if that will work.

---

### Post by Cam1223 on 2008-01-13
also anyone know why i keep hitting this "E: Couldn't find package ipod-convenience"
am i missing a repo source or something??

---

### Post by bobo on 2008-01-13
cam1223:

Try this repo...

deb [http://ppa.launchpad.net/ipod-touch/ubuntu](http://ppa.launchpad.net/ipod-touch/ubuntu) gutsy main

---

### Post by Cam1223 on 2008-01-13
ran into a bigger problem when i put in sshfs to mount the ipod it just keeps spitting back read: Connection reset by peer i had mounted it before i dont know whats wrong now

---

### Post by Cam1223 on 2008-01-13
ok srry about that the problem was the known_hosts list was wrong on the root and i was changing mine (the user)

i can transfer songs to the ipod but the database wont sync. the music app still says no content. what im i missing?????

---

### Post by rs8000 on 2008-01-14
After transferring music to your touch you need to restart the Music App on the touch so your music will display. Do this by holding down the button on the front of the Touch while you are in your Music App. After 3-4 seconds you will get booted to the Touch home screen. Go back into the Music App and your music should be there.

---

### Post by ntetreau on 2008-01-15
> **rs8000 said:**
> After transferring music to your touch you need to restart the Music App on the touch so your music will display. Do this by holding down the button on the front of the Touch while you are in your Music App. After 3-4 seconds you will get booted to the Touch home screen. Go back into the Music App and your music should be there.

Technically, ipod-umount should take care of resetting the Music app for you.

---

### Post by rs8000 on 2008-01-16
> **ntetreau said:**
> Technically, ipod-umount should take care of resetting the Music app for you.

Practically, at least for me, ipod-(u)mount doesn't work at all for a Touch. That's why the directions I posted earlier don't even use it.

---

### Post by jazztt on 2008-01-16
There are several tools available in Linux that you can use to sync an iPod. Just do a google search for "ipod sync linux" or something similar. I use Linux heavily at home, but almost exclusively as back-end machines to support PVR functions and general-purpose server functions. Consequently, I cannot tell you if any of the available software works well or not.

Whichever iPod sync'ing tool you try in Linux, be aware that you cannot use it to play protected files.

Good luck

---

