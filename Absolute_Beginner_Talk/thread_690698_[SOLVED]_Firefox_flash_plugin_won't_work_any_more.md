---
title: "[SOLVED] Firefox flash plugin won't work any more???"
date: 2008-02-07
forum: Absolute Beginner Talk
---

### Post by G. Cotgreave on 2008-02-07
2 nights the update manager showed 1 availiable update witch was the adobe flash player or something, since then firefox won't show any flash contents from any page myspace, youtube google video and so on. is there any way to restore my system 2 days ago? or any other possible way to restore my flash plug in for mozilla?

---

### Post by jan quark on 2008-02-07
i do not know if it is possible to restore the old plugin
but this worked for me

```

sudo apt-get remove --purge flashplugin-nonfree -y && sudo apt-get install flashplugin-nonfree -y
```

---

### Post by Paul820 on 2008-02-07
See this: [http://ubuntuforums.org/showthread.php?t=689637&highlight=flash]("http://ubuntuforums.org/showthread.php?t=689637&highlight=flash")

---

### Post by Crumpets and Jam on 2008-02-07
> **G. Cotgreave said:**
> 2 nights the update manager showed 1 availiable update witch was the adobe flash player or something, since then firefox won't show any flash contents from any page myspace, youtube google video and so on. is there any way to restore my system 2 days ago? or any other possible way to restore my flash plug in for mozilla?

Try uninstalling flash. Open the Terminal and paste:

```
sudo apt-get remove flashplugin-nonfree
```

Download and Save this file [from]("http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz") Adobe's site and follow these instructions.

   1.  Click the "Download .tar.gz" link. A dialog box will appear asking you where to save the file.
   2. Save the .tar.gz file to your desktop and wait for the file to download completely.
   3. Unpackage the file. A directory called install_flash_player_9_linux will be created.
   4. In terminal, navigate to this directory and type ./flashplayer-installer to run the installer. Click Enter. The installer will instruct you to shut down your browser(s).
   5. Once the installation is complete, the plug-in will be installed in your Mozilla browser. To verify, launch Mozilla and choose Help > About Plug-ins from the browser menu.

---

### Post by G. Cotgreave on 2008-02-07
Thanks Crumpets and Jam the tutorial you wrote for me worked perfect!!!! my mozilla flash is now up and working!!!

---

### Post by Crumpets and Jam on 2008-02-07
> **G. Cotgreave said:**
> Thanks Crumpets and Jam the tutorial you wrote for me worked perfect!!!! my mozilla flash is now up and working!!!

Glad it worked for you too.

---

### Post by G. Cotgreave on 2008-02-07
i just saw that googlevideo is not playing on full screen but i will figure it out :):) Thnx Again

---

