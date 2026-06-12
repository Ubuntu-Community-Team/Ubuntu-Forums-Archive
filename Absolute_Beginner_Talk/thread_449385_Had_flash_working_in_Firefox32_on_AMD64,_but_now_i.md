---
title: "Had flash working in Firefox32 on AMD64, but now it's not?"
date: 2007-05-20
forum: Absolute Beginner Talk
---

### Post by blazini on 2007-05-20
I managed to get flash working on my 64bit machine with this tutorial [http://ubuntuforums.org/showthread.php?t=341727]("http://ubuntuforums.org/showthread.php?t=341727")
But I couldn't get realplayer going right. I installed Swiftfox32 with Automatix because it had a plugin pack that I thought would help the realplayer situation. Now my flash and realplayer don't work right. I uninstalled Swiftfox through Automatix and Firefox through Synaptic. After reinstalling Firefox nothing has changed but following the totorial doesn't get flash back up. I'm not worried about realplayer, I just want flash working again. Is there a way to wipe the browsers clean and get Firefox32 (or Swiftfox)and flash working again?

---

### Post by x64Jimbo on 2007-05-20
Uninstalling the packages does nothing to remove the plugins which are stored in your user's application data. You will probably need to delete the .mozilla/firefox directory in your home directory, then follow the instructions again.

---

### Post by blazini on 2007-05-20
Wow, I did what you said and deleted the .mozilla/firefox directory. As a first attempt just to make things easier I tried installing swiftfox and the plugins, and it worked imediately! I can tell this forum is gonna be alotta help, and it only took like 8 minutes for a reply. Thanks!

---

### Post by Kilz on 2007-05-20
> **blazini said:**
> Wow, I did what you said and deleted the .mozilla/firefox directory. As a first attempt just to make things easier I tried installing swiftfox and the plugins, and it worked imediately! I can tell this forum is gonna be alotta help, and it only took like 8 minutes for a reply. Thanks!

If you still have the firefox32 installed it should work also. The problem is you installed nspluginwrapper. This will make flash stop working on all 32bit browsers. When you deleted the ./mozilla folder you deleted the /mozilla/plugin folder that held the nspluginwrapper files.
let me also suggest posting 64bit problems[ in the 64bit section of the forum]("http://ubuntuforums.org/forumdisplay.php?f=134"), there are some common problems we 64bit users know a lot about that those that dont run it dont know about.

---

### Post by blazini on 2007-05-20
I thought newspluginwrapper is what got flash working in Firefox 32? I'm just happy flash is working again. The content that generally gets handled by realplayer is being intercepted by the Mplayer plugin still, and that's causing a minor problem. I'm not gonna worry about it tho, as I'd rather have flash

---

