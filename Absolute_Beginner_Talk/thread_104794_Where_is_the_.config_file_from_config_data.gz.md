---
title: "Where is the /.config file from config_data.gz ?"
date: 2005-12-16
forum: Absolute Beginner Talk
---

### Post by CaptainMorgan on 2005-12-16
Im trying to set up madwifi and going was good til I reached the make command to compile the kernel... got an error, 

**KernelPath /usr/src/linux not found **

so I tried to relocate the path to /usr/src/linux-source-2.6.12/kernel/ and also tried /usr/src/linux-headers-2.6.12-10/kernel/ and it seems every turn it takes it's looking for the .config file... not a config file with no ( . ) but a file that has the extension .config ... unless Im confusing things...

---

### Post by bscbrit on 2005-12-17
You've probably gathered from the multitude of replies that you haven't received that no-one seems to have seen this problem before.  I confess that I am one that multitude!  All I can suggest is that you try to download it again but I am not optimistic that it will help.  Are you using an ubuntu package or have you downloaded this from somewhere else? i.e. is it an ubuntu kernel package or not?

---

### Post by kaamos on 2005-12-17
You're compiling a kernel?

I suggest looking here: [http://ubuntuforums.org/showthread.php?t=85064](http://ubuntuforums.org/showthread.php?t=85064)

---

### Post by bscbrit on 2005-12-17
Kaamos - they way you asked that question made me think twice - I had to go back and check.  But yes, he says he is compiling a kernel....

---

### Post by kaamos on 2005-12-17
The version he's trying to compile is 2.6.12-10, as available in the repos. Is linux-restricted-modules broken, or why is the kernel compilation necessary?

---

### Post by CaptainMorgan on 2005-12-17
Seems I went down an empty hallway on this one..

Thank you for the replies folks.

I ended up severely ruining my system, so I reinstalled Breezy... after consulting with numerous folks on #ubuntu - irc.freenode.net, they said that most Atheros chips work out of the box. This was not the case in my setup. 

After installing Breezy for the second time, just the like the first time, I went straight to the wireless to get it working as a first priority... in case I mess up anything. There was a nice chap at freenode that probably had pity but he walked with me every step of the way for like an hour and a half. Wish I could buy him a drink. 

In the end, we got it working... he doesn't know why how we got it working... nor did he know why my chip didn't work out of the box even though it's officially supported. 

It's still a tricky process switching between wireless and hardwired ( for big downloads, or deskwork ), it should be easy but every time I **sudo ifconfig eth0 up**, either the wireless will shut down, and I won't be able to get hardwired to work, or niether will work for like 20 minutes... which reminds me that with my current setup, knowing the key and passphrase etc, I still can't connect to a secure network, I can only connect to a non-secure. Ive been told to upgrade to WPA instead of WEP, doing that now so maybe we'll see some changes. 

I learned much about the kernel compiling, cool process - which evidently disrupted my system and apparently the compiling was unneccessary what without many headaches.

cheers

---

