---
title: "xine extra plugins cannot be installed on my computer, any alternatives?"
date: 2007-11-21
forum: Absolute Beginner Talk
---

### Post by renis-pinkles on 2007-11-21
I really want to get amarok working, however, it needs the MP3 support, which it says it installs, but isn't. I have been looking for a solution everywhere but not many people know what to do. I think that this may help, getting this plugins, but is has the following error message:
"Xine extra plugins cannot be installed on your computer type (amd64)"
i hope it isn't suggesting that i am running an amd 64 processor, because i am most certainly not.

any alternatives, or solutions?

---

### Post by jordanmthomas on 2007-11-21
Very interesting problem.  :)
first thinsg first, what does 
```
uname -a
``` show (to make SURE you're not running 64-bit even though I believe you)
and ```
cat /etc/apt/sources.list
``` to make sure you haven't put in a 64-bit repository or something.

I'm not sure if I'll be able to help but this may be a good start.

---

### Post by renis-pinkles on 2007-11-21
okay, well i am feeling a little bit silly now. i dont know if you can tell, but im not great with computers, especially ubuntu. To start with, the response to your first command was as follows:
Linux VaughanLinux-desktop 2.6.22-14-generic #1 SMP Sun Oct 14 21:45:15 GMT 2007 x86_64 GNU/Linux


i have a feeling that this DOES mean i am running 64 bit...

what does this mean, in terms of fixing the problem?

(By the way, i really appreciate your response! :) )

---

### Post by jordanmthomas on 2007-11-21
Yes, you ARE running the 64-bit kernel.
I don't know anything you need to do special, but according to ubuntu's package search, the package amarok-xine is available for amd64.
```
sudo apt-get install amarok-xine
```

This link suggest adding the medibuntu repository and installing packages from there:
[http://ubuntuforums.org/showthread.php?t=368607](http://ubuntuforums.org/showthread.php?t=368607)

---

### Post by renis-pinkles on 2007-11-21
okay, thank you for all your help, patience, and quick replies :)

---

### Post by zaphod9975 on 2008-02-09
I have same problem, but I am using the 32-bit version. Amarok is installed fine, but I can't play ANYTHING from the internet. In the apt-get program installer, the xine extra plugins option is grey-ed out (the only thing not available, and the only one I want!). I have un-commented all the additional sources in the sources file, makes no difference. Surely I am not the only person to use Ubuntu and play internet music on Amarok, so why is this not working????:mad:

---

### Post by zvacet on 2008-02-09
To be sure that you have all repos open go to the system<admin>software sources>chek all boxes under ubuntu softwae and updates tab.Reload.In terminal type


```
sudo apt-get install ubuntu-restricted-extras
```

For KDE

```
sudo apt-get install kubuntu-restricted-extras
```

and for Xubuntu

```
sudo apt-get install ubuntu-restricted-extras
```

So you will install one wich match your dektop.

In terminal

```
gsudo gedit /etc/apt/sources.list
```

add this line
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) gutsy free non-free

Save and close the file.

```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add -
sudo apt-get update
```

Go to the synaptic and in search box tipe w32(64 if you use 64 bit version)codecs and when you find them mark for install and install.

---

### Post by santiagoward2000 on 2008-02-09
Hi!
I had the same problem using **Add/Remove...** I couldn't install them, and I'm on a i386. What I did to get mp3 support was installing **libxine1-ffmpeg**.
I hope this helps!
Cheers!

---

### Post by endymon on 2008-02-15
> **santiagoward2000 said:**
> Hi!
I had the same problem using **Add/Remove...** I couldn't install them, and I'm on a i386. What I did to get mp3 support was installing **libxine1-ffmpeg**.
I hope this helps!
Cheers!

My Amarok is now playing MP3's on AMD64 version because of this solution...

THANKS!

---

