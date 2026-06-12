---
title: "[SOLVED] Navigate to a Directory in the Terminal"
date: 2008-02-02
forum: Absolute Beginner Talk
---

### Post by Crumpets and Jam on 2008-02-02
I have download the file to install Flash from Adobe's website, [here]("http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash&ogn=EN_US-gntray_dl_getflashplayer"). I am installing it using the instruction on the same page.

[QUOTE=Adobe]1. Click the "Download .tar.gz" link. A dialog box will appear asking you where to save the file.

2. Save the .tar.gz file to your desktop and wait for the file to download completely.

3. Unpackage the file. A directory called install_flash_player_9_linux will be created.

4. In terminal, navigate to this directory and type ./flashplayer-installer to run the installer. Click Enter. The installer will instruct you to shut down your browser(s).

5. Once the installation is complete, the plug-in will be installed in your Mozilla browser. To verify, launch Mozilla and choose Help > About Plug-ins from the browser menu.[/QUOTE]

In step 4, I am instructed the navigate to the directory *install_flash_player_9_linux* which is on my desktop. How do I do this? Thanks everyone.

---

### Post by jan quark on 2008-02-02
try my guide i explain this also

[http://janquark.fatfreehost.com/tutorial3.html](http://janquark.fatfreehost.com/tutorial3.html)

---

### Post by rfurman24 on 2008-02-02
In terminal cd/to/directory/. If it is on your desktop I think you cd /home/user/Desktop where user is your user name then issue the command. There are debs available to install which would be better imo.

---

### Post by ~LoKe on 2008-02-02
```
cd ~/Desktop/install_flash_player_9_linux
```
=)

---

### Post by Crumpets and Jam on 2008-02-02
Thanks for all the help. I did with;

```
cd /home/john/Desktop/install_flash_player_9_linux
```

Thanks again.

---

### Post by jan quark on 2008-02-02
please mark this thread as solved

use thread tools thx

---

