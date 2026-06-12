---
title: "Computer won't power off"
date: 2008-02-19
forum: Absolute Beginner Talk
---

### Post by toekneevee on 2008-02-19
When I shutdown using quit, Ubuntu goes through the process, gets to the Ubuntu screen, the orange status bar clears, but the machine doesn't turn off. I have to turn the machine off by holding the power button for several seconds. If I shutdown from a terminal with the command sudo shutdown now, the screen shows the following just before it hangs...

*Starting anac(h)ronistic cron anacron [OK]
*Starting deferred execution scheduler atd [OK]
*Starting periodic command scheduler crond [OK]
*Checking battery state... [OK]
*Running local boot scripts (/etc/rc.local) [OK]
init: rc1 main process 6178 killed by TERM signal
root@tony-desktop:~#

Any help will be most appreciated. Thanks.

---

### Post by randy78 on 2008-02-19
> **toekneevee said:**
> When I shutdown using quit, Ubuntu goes through the process, gets to the Ubuntu screen, the orange status bar clears, but the machine doesn't turn off. I have to turn the machine off by holding the power button for several seconds. If I shutdown from a terminal with the command sudo shutdown now, the screen shows the following just before it hangs...

*Starting anac(h)ronistic cron anacron [OK]
*Starting deferred execution scheduler atd [OK]
*Starting periodic command scheduler crond [OK]
*Checking battery state... [OK]
*Running local boot scripts (/etc/rc.local) [OK]
init: rc1 main process 6178 killed by TERM signal
root@tony-desktop:~#

Any help will be most appreciated. Thanks.

I'm not sure what is causing that, but for now you can type in a terminal (or at that command prompt)
sudo poweroff

---

### Post by DiscoKiller on 2008-02-19
i know this sounds stupid but check your keyboard and mouse are plugged in correctly.

---

### Post by philinux on 2008-02-19
Clik the link below for known gutsy bugs. Hanging shutdown is one that affects some hardware.

---

### Post by eggdeng on 2008-02-19
You could try
```
sudo gedit /etc/modules
```
add the line
```
apm power_off=1
```
Save  the file. Changes will not have any effect  until after you reboot.

---

### Post by ellalan on 2008-02-26
I am having similar problem as the OP, I have to switch off at the mains to power off.
I tried to enter "sudo gedit /etc/init.d/halt" command but when I was prompted for password I am unable to enter my login password. Could some one tell me what I am doing wrong here. I am two days old Ubuntu user,so you have to treat me lightly. Any help would be appreciated.

---

### Post by RJ Hythloday on 2008-02-26
I"m having this problem w/ a new edubuntu build. I think it happened when I installed xdm, but I no longer have the option to shut down only hibernate, restart etc.

---

### Post by angry_johnnie on 2008-02-26
I have the same problem on my desktop pc (not on the laptop), but only with ubuntu and ubuntu-based distributions.   I tried all the acpi/apm and so on stuff, but it didn't work.  Now, the strange thing is that it doesn't happen with red hat based distros.  I installed PCLinuxOS (which I've never liked) and it turns it off without any problems.  Anybody out there know what might be causing this?  I really want ubuntu on my desktop.

Sorry for posting a question instead of an answer, but maybe somebody will figure it out.


As for the original thread, well, this is what i found (though it didn't work for me):

(i'll just cut and paste)

 1.   added "noapic nolapic" to the end of the kernel line in 'boot/grub/menu.lst' 
 
or

2.  apm power_off=1 to your /etc/modules
     and  the add acpi=off apm=power_off to your /boot/menu.lst 


or

3.  add acpi=force to your boot parameters

You might want to give those a try.

---

### Post by ellalan on 2008-02-26
Hi All,
I have solved my shutdown problem.
I added  "acpi=force" at the end of the line--kernel /boot/vmlinuz-2.6.22-14-generic root.......
.....ro quiet splash, and it worked now I don't need to power off at the mains. I am really enjoing Ubuntu.:)

---

### Post by NM-Ted on 2008-02-27
Ok, I'm clueless. Can you send me more detailed instructions on adding the ACPI=force, please....
I'm definately a nube, but i really am liking ubuntu.  My machine warns me about needing the "ACPI=FORCE", and will not power off on shutdown.
Thanks,

---

### Post by angry_johnnie on 2008-02-28
> **ellalan said:**
> Hi All,
I have solved my shutdown problem.
I added  "acpi=force" at the end of the line--kernel /boot/vmlinuz-2.6.22-14-generic root.......
.....ro quiet splash, and it worked now I don't need to power off at the mains. I am really enjoing Ubuntu.:)

Well, thanks!  After having tried all the *=yes stuff without any succes, I did what you suggested, and it worked!  Now I'm a very happy, full fledged, ubuntu user, both at home and on my laptop!

---

### Post by ellalan on 2008-02-28
Hi NM-Ted
Go to Applications>Accessories>Terminal,  then click on terminal
Type: sudo gedit /boot/grub/menu.list
It will prompt for password
You type your login password, but you won't see any astrics or any thing do not worry then wait 
then you look for this line
kernel  /boot/vmlinuz-2.6.22-14- generic root ................ ro quiet splash
after the word splash leave a space and type: acpi-force
then close down.
When you restart the PC it will be ok.
BTW when you type you have to leave spaces and do it slowly so that you won't make any typing mistakes.
good luck.

---

### Post by ellalan on 2008-02-28
Sorry Ted
Correction to the above,  please type  lst ( lower cast L) and no i
I mistyped as list but it is actually  lst

---

### Post by todomartinez on 2008-06-08
I know this is an older post that I am replying.  But, I had tried UBUNTU a few years ago on my Toshiba laptop and I found it a bit hard to use.  Simple things like adding plug-ins to mozilla and other stuff seemed way over my head and I've been using computers since DOS.  So, I dumped it and used XP Professional.  I tried the latest release on my kids desktop and it worked great.  So, I decided to install it on my Toshiba laptop and it worked great.  The wireless worked right away, aMSN worked great, it was quick, I had access to my NTFS files, then I tried shutting down.  Nope.  The computer would just hang forever.  I added the acpi-force and everying is fine.  I may not go back to windows after this.

---

