---
title: "How do I boot to my Ubuntu disc?"
date: 2005-11-27
forum: Absolute Beginner Talk
---

### Post by startailpro on 2005-11-27
I have been trying to convert linux for a long time, just this week i borrowed suse linux 9.0 professional from a friend. I had to keep reloading linux everytime i change the screen size and colour. So i decided to search the web that used the wine technology and a came i across **ubuntu**. Seeing how i kept my windows i loaded it up and started to download 64-bit version of ubuntu. Finally i can use this technology i have in my pc. I was worried that it said amd64. I downloaded the file over night and burnt it onto a cd using nero. I then rebooted my machine with the disc in my DVD-ROM and it just went straight to windows. So i looked round this forum and found something about the BIOS so i went onto it and there was nothing wrong with the settings. It had cd first.

So how do i load :KS  **ubuntu**?

---

### Post by ssam on 2005-11-27
did you burn the cd correctly? have a look at the instructions here [https://wiki.ubuntu.com/BurningIsoHowto](https://wiki.ubuntu.com/BurningIsoHowto)

i assume from what you said that you have an intel 64bit cpu. don't worry about it being called amd64, i am pretty sure thats just what the kernel hackers call all 64bit x86 cpus.

---

### Post by sarah_b on 2005-11-27
Most likely your iso CD you burned is bad. Try burning it again on the slowest write speed that you can. If that doesn't work redownload the iso again, or even from a different download site.................see if any of these will help you

sarah

---

### Post by startailpro on 2005-11-27
I have burnt onto a cd at the lowest setting i have x4(6,000kb), this did not work. I also have a programme similar to ISO recorder its called ISO blaster. Do i have to open the iso cause burnning it seems to do nothing. Anything else.

---

### Post by teaker1s on 2005-11-27
edit bios settings to boot priority cd rom and dvd rom drives first then your harddisk  turn off search for other boot devices if you have that option

---

### Post by sarah_b on 2005-11-27
deleted

---

### Post by Kvark on 2005-11-27
Can you boot other CDs like a Windows or Suse install CD with that computer?
Can other computers boot that Ubuntu CD?

If it's the CD that doesn't work then check the md5 sum of the iso file to see if your download got corrupted or not.

In Ubuntu and I assume Suse too you check the sum by typing "md5sum /path/file.iso" in a terminal, then compare the random letters that command gives you to the ones on the download site. If they match then your download Iis ok. In Windows I think you need to get a special program to check md5 sums.

---

### Post by startailpro on 2005-11-27
At the moment i am using windiws cause i got fed up with suse linux. It hated my graphic card and made the sreen colours horrible. But suse linux cd will run and so does thw windows. I also did the BIOS to make it to the cd first but made no difference. :confused:

---

### Post by ssam on 2005-11-27
you could try downloading it again.

make sure you get the appopriate version, x86 for most people.

you may want to download with bittorrent. as it does error checking.

or you could get someone to send you an ubuntu cd, the is shipit.ubuntu.com, or maybe a kind person here, or you can buy cds at LinuxCD.org

update:
have a look at [http://www.ubuntuforums.org/showthread.php?t=90650](http://www.ubuntuforums.org/showthread.php?t=90650) and [https://wiki.ubuntu.com/forum/GiveAway](https://wiki.ubuntu.com/forum/GiveAway)

---

### Post by startailpro on 2005-11-27
Its all sorted now. I used something called dvd encryter my friend gave it to me and said that will solve ur problem and she was right.The pc will now reconize the cd and load it. I hope ubuntu is worth it.

---

### Post by startailpro on 2005-11-27
:???:  I have a saying that seems to work with everything i do. You fix one problem there's another. Sounds like windows. Did i say that. Anyways i have loaded ubuntu onto my pc but how to geton to the desktop and there was failure with the x server. I have login in to this sreen that u have to type into a code like shell if u know what that is.

---

### Post by ssam on 2005-11-27
ok good start.

is this with the live or install cd?

sometimes running

```
sudo dpkg-reconfigure xserver-xorg
sudo /etc/init.d/gdm start
```
helps.

see if you can find anything useful in [http://www.ubuntuforums.org/showthread.php?t=79827](http://www.ubuntuforums.org/showthread.php?t=79827)

---

### Post by startailpro on 2005-11-27
installed cd.

---

### Post by startailpro on 2005-11-28
:???: Thought accord. Does **Ubuntu Linux** support ati graphic cards. Cause Suse linux would not allow me to set it to 1024 x 764. I had to use 800 x 600 to make it run but it had something wrong with the colours. When i did set it to 1024 x 764 it just would not load to the desktop. Even when i put the code in it wouldn't. Just sayed display failed. 

When i used that code ssam gave me sudo /etc/init.d/gdm start it just said failed.

---

### Post by startailpro on 2005-11-28
Had a play around with the code:
sudo dpkg-reconfigure xserver-xorg 
and it did reconise my ati after all so thats good. But i do still get the xserver error. 
When i tried starting
sudo /etc/init.d/gdm start
itdid one thing
Starting Gnome Manger...   [failed]

:mad:

---

### Post by ssam on 2005-11-28
ok. what graphics card do you have? maybe it is newer than the current driver supports.

you might want to try reposting with a title like "x wont start on ati what_ever_model_it_is" and mention the things you have tried so far. a decriptive title often helps people help you.

---

### Post by startailpro on 2005-11-28
It is an ati radon x700. And it keeps on saying there is something wrong with the xserver. I have reconfiguered it but i still seemed to have the same problem.
When i was reconfiguing it errors appeared on the screen.
Everyting else is ok.

update:
It did reconize the ati drive.

---

### Post by startailpro on 2005-11-28
Right i got off my ass and looked at this error i just need help with making sense of this error.
(--)probed, (**)from config file, (==) default settings, (++) from command line, (!!) notice, (II) informational, (WW) warning, (EE) error, (NI) not implemented, (??) unknow.

(==) Log file:"/var/log/xorg.O.log", Time:Mon Nov 28 18:13:02 2005
(==) Using config file:"/etc/x11/xorg.conf"
Skipping
"/user/x11r6/lib/modules/extensions/libGLcore.a:m_debug_clip.o" No
symbols found
Skipping
"/user/x11r6/lib/modules/extensions/libGLcore.a:m_debug_norm.o" No
Symbo9ls found
Skipping
"/user/x11r6/lib/modules/extensions/libGLcore.a:m_debug_xform.o" No
symbols found
(EE) No devices detected

Fatel server error:
no screens found


:confused: what does this mean?

---

