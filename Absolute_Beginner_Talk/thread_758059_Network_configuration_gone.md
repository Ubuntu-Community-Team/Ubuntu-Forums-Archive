---
title: "Network configuration gone"
date: 2008-04-17
forum: Absolute Beginner Talk
---

### Post by Troca on 2008-04-17
Ok its all i have done is installed Kiba-dockl by following instructions on this forum. And after i restarted my computor my network icon next to the clock in the system tray in top right corner was gone so i added it manualy next to my name. i then try to acces the configuration option and i get this Error msg after i typed in my password see screen shoot.

[http://www.mediahump.com/image/83256/](http://www.mediahump.com/image/83256/)

So if anyone could shine some light of what have happend i would be very thankful


oh and iam running Ubuntu 8 beta

---

### Post by quirks on 2008-04-17
Hi Troca,

this is weird. Apparently not only your network configuration is gone, but your network card is not even detected. I don't know how to fix this, but I will try to help you anyway (as no one else has tried to so far). A good starting point is to examine the output of **dmesg**. I gives you valuable information about the hardware in your operating system and tells you, if something went wrong during boot. You can also check other logs (go to System -> Administration -> System Log).

quirks

---

### Post by quirks on 2008-04-17
I just have got another idea: maybe it is not your network card, but only NetworkManager (the icon in the tray), which is fooling around. Can you connect to the internet or other PCs on the network. If so, your network configuration is fine and it should only be a matter of reconfiguring NetworkManager.

quirks

---

### Post by Troca on 2008-04-17
yeah i had some notes i wrote down in my book. the first thing i did when this happens was to type 

sudo ifconfig eth0 192.168.1.1 up

this helped me to get my networkcard to startagain. iam actualy writeing this post from the computor iam having problems with.

I also upped 2 more screenshoots as u can c i can playaround with the network settings but as soon as i hit config i get that error msg 

[http://www.mediahump.com/image/83257/](http://www.mediahump.com/image/83257/)

[http://www.mediahump.com/image/83258/](http://www.mediahump.com/image/83258/)

i prob f@@ked up my uninstall of Kiba aswell sens it still starts when i startup ubuntu. Anyway iam gona reinstall everything clean in 7 days when the finalversion of Ubuntu8 is getting relesed.

Oh and thanks for helping me quirks. Iam so new to Ubuntu/Linux and i feal so lost sometimes Luckely this forum is a gr8 sourc for finding answers and askign questions :)

---

### Post by quirks on 2008-04-17
It looks like NetworkManager forgot to manage your network device (for whatever reason). As far as I know it must be set to auto in /etc/network/interfaces. But if you are going to do a fresh install in a week anyway, it is probably not worth the effort spending hours on trying to fix that problem. But I don't want you to do a complete reinstall, just because NetworkManager doesn't work properly anymore. I'm sure there is a way to fix that. I have never seen a Linux system shredded so much, that it couldn't be fix anymore.

By the way, you don't have to use NetworkManager necessarily. If you do not change between networks frequently (i.e., you are not using a laptop), you can disable it and configure everything under System -> Administration -> Networking. This is what I do for my desktop PC, where I have to use static IPs, because my router is kind of a bad DHCP server. *sigh* And even if you switch between networks, you can apply appropriate settings when needed in the network configuration. NetworkManager is helpful, when you want your laptop to automatically switch to a (more reliable) wired connection available, and use a wireless connection otherwise.

quirks

---

### Post by Troca on 2008-04-17
thank you very much. And iam not reinstalling becus of this only. btw the System -> Administration -> Networking is the setting i use to have at the top right corner of my screen right next to the speaker volume and the clock so thats the one i was looking for i gues :) just need to figure how to get it backup there. 

main reason for reinstall is because i have used ubuntu for about 1 week now, only used Ubuntu 7 for 1 day but it worked better in the aspects of that i didn't have to re share all my SMB shares every time i restarted my comp and the static ip is working perfect in ubuntu7 in Ubuntu 8 i have to ifconfig it every time i reboot for it to work did a post about that ([http://ubuntuforums.org/showthread.php?t=755726](http://ubuntuforums.org/showthread.php?t=755726)) and ppl replyed its a bug in version8. and i think the Smb thing is a bug aswell at least i assume so. Hopefully all this will be fixed in the Final version :) 


thats the main reasons for my reinstall.

---

### Post by quirks on 2008-04-17
Just in case you do not know: you do not have to reinstall a new system every time a new release comes out. You can upgrade to a newer version using the Update Manager (go to System -> Administration -> Update Manager). Whenever a new version is available, a button appears near the top of the window, telling you that you can download it now. When you click the button, the program downloads all software packages and installs them. It takes about two hours (for me), and after that you have the most recent Ubuntu with all the software you had already installed on the older version.

quirks

---

### Post by Troca on 2008-04-18
Oh i thought i had to reinstall it when the finalversion was relesed

---

### Post by Troca on 2008-04-18
Oh i thought i had to reinstall it when the finalversion was relesed. If i could only figureout how to get the icon back on the samelocation :P

---

