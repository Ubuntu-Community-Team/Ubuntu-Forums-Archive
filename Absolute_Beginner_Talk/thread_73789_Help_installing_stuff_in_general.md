---
title: "Help installing stuff in general"
date: 2005-10-10
forum: Absolute Beginner Talk
---

### Post by Canuck on 2005-10-10
Hello,

I am "very" new to Linux, my brain has been corroded by Microsoft for a very long time!  Two questions:

1.  If I have downloaded software to install and saved it to my desktop how do I navigate in the Terminal environment in order to install that package (i.e. Skype).

2.  How do I install software from a cd, i.e. MatLab.

Thank you very much, I figure once I get this sorted I should be good from there (for now!).

Canuck

---

### Post by Heli0s on 2005-10-10
If you open a Terminal you're in your home directorie, to get to the desktop type: "cd Desktop" (With the capital D) or "cd /home/[username]/Desktop"

To get to a cd you can type " cd /cdrom " then you have to find a readme or install text file witch tells you how to install the software.

---

### Post by Canuck on 2005-10-10
Heli0s

Cool, thanks for that.  I wasn't sure on how to move around in terminal.  Your help is much appreciated!

Canuck

---

### Post by heimo on 2005-10-10
[quote=Heli0s]
"cd /home/[username]/Desktop"
[/quote] Tip of the day. :) You can substitute /home/[username] with ~ (tilde sign), for example "cd ~/Desktop". You can always get to your home directory with just plain "cd", and to go back to previous directory, use "cd -". Examples:
```

cd (goes to your home directory)
cd Desktop (now you're in ~/Desktop)
cd /tmp (goes to /tmp)
cd - (goes back to ~/Desktop)
cd - (and back to /tmp)
cd .. (now you're in / )

```

---

### Post by Canuck on 2005-10-19
Hello again!

Thanks for the help but I have another question now...  I have posted this question in a couple of threads to try and find an easy (ish) solution and it goes as follows:

I am having a problem installing Matlab. I have been following the Wiki guide on how to install it ([https://wiki.ubuntu.com/MATLAB]("https://wiki.ubuntu.com/MATLAB")) and I get the following error when trying to make an image in the temp file.


command used: [COLOR="Blue"]sudo cp -R /media/cdrom1 /tmp/matlab[/COLOR]

Error Received: [COLOR="Red"]cp: reading `/media/cdrom1/win32/help/base/install/pc/mhelp.dat': Input/output error[/COLOR]


Anyone have any suggestions on how to remedy the situation. By the way I am trying to install the student version R14 SP1 and am running Breezy.

The CD seems to be fine as it installs and runs fine in Windows...

Canuck

---

### Post by tom007 on 2005-10-19
Hey,

not sure if it's really a help in this issue, (i'm also a beginner, but think in 'linux' you have a chance to be a beginner from the first to your last investigation), but you can also try to open two windows on your desktop with the files youre looking for and then catch them with your mouse like in 'Windows' with 'drag & drop'.

Bye
Thomas Rump

---

### Post by Canuck on 2005-10-20
Tomm,

Well we newbies should stick together, sometimes the easiest answer is the best! ;)  The old drag n drop worked like a charm, when it got to the unreadable file I hit skip and the rest went in like clockwork.  I continued with the rest of the install and voila matlab was installed (sort of I had to change a few things due to access rights etc... because Matlab and Linux don't quite agree...).  Thanks for the help.

Canuck

---

