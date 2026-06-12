---
title: "How to add music to your iPhone/iPad in Ubuntu (WORKAROUND) - all iOS devices!"
date: 2014-01-12
forum: Apple Hardware Users
---

### Post by mrivchenko on 2014-01-12
Yes, folks. It's possible (and it works 100%), but it will require some work... 
As of now, there is no way of syncing your iOS devices with Linux/Ubuntu using traditional means. iOS 7 introduces another problem - the endless "Trust this Computer" loop. 
Here is how you can overcome all of that that. Works flawlessly for me.


Step 1: Jailbreak your iDevice 
Step 2: Install the following apps using Cydia: PwnTunes and OpenSSH (NOTE: make sure these are compatible with your iOS version. iOS 7 has a separate PwnTunes app).
Step 3: Go to PwnTunes settings and enable "Needs Sync" (you might have to fiddle around with other settings and reboot the device before everything works properly)
Step 4: Install FileZilla in Ubuntu. Login to your device (Host: your device's Wifi IP, user: root, password: alpine, port: 22)
Step 4: Navigate to "/private/var/mobile/Media/My Music" and drag the mp3 files from your computer to that folder.
Step 5: Launch the Music app. If everything works properly, your files should be imported and become visible in the music app.

PS essentially this method gives you a complete access to the iPhone/iPad's filesystem, including all hidden folders and files. 

Good luck!

[COLOR="#FF0000"]Staff edit : be aware this will break the device waranty[/COLOR]

---

