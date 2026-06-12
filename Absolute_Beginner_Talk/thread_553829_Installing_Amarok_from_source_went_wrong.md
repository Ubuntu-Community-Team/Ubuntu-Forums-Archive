---
title: "Installing Amarok from source went wrong"
date: 2007-09-18
forum: Absolute Beginner Talk
---

### Post by k1001001 on 2007-09-18
Hi all. I was running Amarok 1.4.3, and I wanted to upgrade to 1.4.7, however Synaptic wouldn't let me do so (ie I typed 'sudo apt-get install amarok' but no update results came up). I went to the Amarok website and had to download the source code instead. No worries, though, since they had the instructions printed on the [website]("http://amarok.kde.org/wiki/Download:Source"). After following these instructions (and after sitting through an extremely long 'make' process), Amarok finally installed.

However, when I typed 'amarok' in the terminal, the old 1.4.3 version started up. I tried starting Amarok from the Applications menu as well, and I had the same result. In order to fix this, I uninstalled the old Amarok via 'sudo apt-get remove amarok,' which removed the old version. When I went back to the new version's directory and typed 'amarok' again though, Terminal came back with 'amarok: command not found.' So I tried to install Amarok again through Synaptic, however Synaptic only gives me version 1.4.3. :confused:

Is there any way I can install version 1.4.7?

---

### Post by Bachstelze on 2007-09-18
If you're using Feisty, Amarok 1.4.7 is available in the Backports.

---

### Post by k1001001 on 2007-09-18
I'm still running Dapper, which I imagine is the source of my problem.

I just tried to install a .deb package of Amarok 1.4.7 as well, however I'm stuck in dependency hell. It's telling me I don't have packages that are already installed. I figured as much.

---

### Post by Lord Illidan on 2007-09-18
After you typed make in the Amarok src folder, did you type : > sudo make install ?

Also, you should have removed amarok with sudo apt-get remove amarok before you installed amarok from source, not afterwards. Try it again. I don't think you'll have to repeat the make process.

---

### Post by k1001001 on 2007-09-18
'sudo make install' did the job! I forgot to type it in after watching the 'make' process go on for about 20 minutes last night. Thanks for your help!

---

### Post by Bachstelze on 2007-09-18
You shouldn't have done that. I suggest you do

```

sudo make uninstall
sudo apt-get checkinstall
sudo checkinstall
```

it will build a DEB package of your compiled Amarok and install it, which will mean much less trouble because it will make Apt aware of the new version.

---

