---
title: "[SOLVED] Cannot run Ubuntu Feisty 64 with Ati x700, blackscreen results"
date: 2007-09-20
forum: Absolute Beginner Talk
---

### Post by Ramza001 on 2007-09-20
Please forgive my ignorance, this is my first attempt to use any kind of Linux OS.

My system is a Emachine T6212 Amd 64bit 3200 and i am using a Ati x700 pcie video card.

"the x700 works in windows on my system"

First off I could not use the live 64bit Feisty cd to install Linux because i kept getting a blackscreen and my monitor went off, so I used the alternate version installation cd instead and I successfully installed Linux.

Then when i tried to enter the installed system, I still got a blackscreen and the monitor went off.

So i figured it had something to do with my video, so i took out my video card and the system worked using my integrated x200 video.

I looked up on google if I could disable my integrated video but from what i have read the bios I am using will not allow it.

I tried a number of things the last few days with the help of google and I have found no solution so that I can still use my x700 video card with linux.

If I cannot get this fixed I will have to wait on using this wonderful OS which i have been wanting to use for a long time.

---

### Post by mali2297 on 2007-09-20
Have you tried the advice in the sticky?
[http://ubuntuforums.org/showthread.php?t=414194](http://ubuntuforums.org/showthread.php?t=414194)

---

### Post by Ramza001 on 2007-09-20
Yes it was one of the first things i did and it did not fixed the problem sadly.

---

### Post by mali2297 on 2007-09-20
Well, I've got ATI Radeon Mobility X700 card working on my machine. Although I have a 64bit processor, I use the 32bit Ubuntu. It might be easier to get that working. 

Alternatively, you could check the x86_64 forum here.

---

### Post by Ramza001 on 2007-09-20
Did you try the 64bit version? Did it give you problems?

---

### Post by overdrank on 2007-09-20
> **Ramza001 said:**
> Yes it was one of the first things i did and it did not fixed the problem sadly.

Hi you could try and reconfigure your xorg. When you recieve the black screen use the keys all at the same time ctrl, alt, F1 and this will bring you to the command prompt. Login with user name and password and then use this command ```
sudo dpkg-reconfigure xserver-xorg
```
Answer the questions and choose vesa as the driver. If you dont know the answer to the questions then leave as the default answer given. Hope this helps. Good luck!

---

### Post by mali2297 on 2007-09-20
> **Ramza001 said:**
> Did you try the 64bit version? Did it give you problems?

It was a long time ago, in the days of Breezy Badger (~2005). I can't remember the problems I had but it might have been similar to yours. As soon as I realized that I could run the 32bit version of Ubuntu, I installed that one instead. It will give you less problems, although I hear that the  64bit version has been improved.

---

### Post by Ramza001 on 2007-09-20
> **overdrank said:**
> Hi you could try and reconfigure your xorg. When you recieve the black screen use the keys all at the same time ctrl, alt, F1 and this will bring you to the command prompt. Login with user name and password and then use this command ```
sudo dpkg-reconfigure xserver-xorg
```
Answer the questions and choose vesa as the driver. If you dont know the answer to the questions then leave as the default answer given. Hope this helps. Good luck!

Thank you for the response, I will try this and report back the results as soon as i can.

---

### Post by Ramza001 on 2007-09-20
> **mali2297 said:**
> It was a long time ago, in the days of Breezy Badger (~2005). I can't remember the problems I had but it might have been similar to yours. As soon as I realized that I could run the 32bit version of Ubuntu, I installed that one instead. It will give you less problems, although I hear that the  64bit version has been improved.

Well i was wanting to use the full the full potential of my computer but if worse comes to worse i might try installing the 32bit version like you did.

By the way wikipedia said that a new version of Ubuntu will be released in October if i remember correctly, is this true?

---

### Post by mali2297 on 2007-09-20
> **Ramza001 said:**
> Well i was wanting to use the full the full potential of my computer but if worse comes to worse i might try installing the 32bit version like you did.

By the way wikipedia said that a new version of Ubuntu will be released in October if i remember correctly, is this true?

Yes, Ubuntu 7.10 (Gutsy Gibbon) will be out next month.

---

### Post by Ramza001 on 2007-09-20
> **overdrank said:**
> Hi you could try and reconfigure your xorg. When you recieve the black screen use the keys all at the same time ctrl, alt, F1 and this will bring you to the command prompt. Login with user name and password and then use this command ```
sudo dpkg-reconfigure xserver-xorg
```
Answer the questions and choose vesa as the driver. If you dont know the answer to the questions then leave as the default answer given. Hope this helps. Good luck!

Ok i tried to press ctrl-alt and f1 during the black screen and nothing happened so i rebooted and went into recovery mode.

Next i typed sudo dpkg-reconfigure xserver-xorg in recovery mode, It opened and detected my x700 but asked nothing about any drivers.

Im still getting the blackscreen.

---

### Post by Ramza001 on 2007-09-20
> **mali2297 said:**
> Yes, Ubuntu 7.10 (Gutsy Gibbon) will be out next month.

Think the new ubuntu will have this problem fixed?

---

### Post by glupee on 2007-09-20
why don't you try the alternate desktop cd.
It's a text based install, but it's not any harder than the regular one.
[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)
this way you don't have to wait and get some practice in before gutsy :D

---

### Post by Ramza001 on 2007-09-20
> **glupee said:**
> why don't you try the alternate desktop cd.
It's a text based install, but it's not any harder than the regular one.
[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)
this way you don't have to wait and get some practice in before gutsy :D

I did install by alternate cd when the live cd didnt work, Is there something else I should configure while installing?

---

### Post by mali2297 on 2007-09-20
> **Ramza001 said:**
> Next i typed sudo dpkg-reconfigure xserver-xorg in recovery mode, It opened and detected my x700 but asked nothing about any drivers.


Strange, try it again.

If it still doesn't let you choose driver, you can manually edit the file. Type
```

nano /etc/X11/xorg.conf

```

And try to find a line similar to
> 
        Driver       "ati"

It might say something else than "ati". Anyhow change it to "vesa". Then save (Ctrl+o), quit (Ctrl+x) and reboot (type reboot  and press enter).

---

### Post by Ramza001 on 2007-09-20
> **mali2297 said:**
> Strange, try it again.

If it still doesn't let you choose driver, you can manually edit the file. Type
```

nano /etc/X11/xorg.conf

```

And try to find a line similar to

It might say something else than "ati". Anyhow change it to "vesa". Then save (Ctrl+o), quit (Ctrl+x) and reboot (type reboot  and press enter).

Ive tried it twice, I have tried nano /etc/X11/xorg.conf but it only detected my x200 integrated video.

Ill try it again  and post the results.

---

### Post by overdrank on 2007-09-20
Hi I understand that you checked your bios to disable the onboard graphics but that sure sounds like its the problem. Ubuntu is only detecting the x200 then it must be in the bios. You may check and see if there is a options for the video like onboard first or pic first. Good luck! :popcorn:

---

### Post by Ramza001 on 2007-09-20
> **mali2297 said:**
> Strange, try it again.

If it still doesn't let you choose driver, you can manually edit the file. Type
```

nano /etc/X11/xorg.conf

```

And try to find a line similar to

It might say something else than "ati". Anyhow change it to "vesa". Then save (Ctrl+o), quit (Ctrl+x) and reboot (type reboot  and press enter).


Ok it detects the x700 now, I changed the driver to vesa and rebooted and I still have a blackscreen.

We are making progress right? hahaha

---

### Post by mali2297 on 2007-09-20
Read the last post in this thread:
[http://ubuntuforums.org/showthread.php?t=525725](http://ubuntuforums.org/showthread.php?t=525725)
Try that.

---

### Post by Ramza001 on 2007-09-20
> **mali2297 said:**
> Read the last post in this thread:
[http://ubuntuforums.org/showthread.php?t=525725](http://ubuntuforums.org/showthread.php?t=525725)
Try that.

I just tried it, I went into /boot/grub/menu.lst and deleted "quietsplash" ,rebooted and got blackscreen again.

---

### Post by Ramza001 on 2007-09-20
mobad in the 64bit section of the forum finally found a solution.

[http://ubuntuforums.org/showthread.php?p=3400339#post3400339](http://ubuntuforums.org/showthread.php?p=3400339#post3400339)

""" Originally Posted by mobad  View Post
Heh you have the same video card I have... and the same problem I had.

Should be an easy fix.

Step 1: Ctrl + Alt + F2 and you should get something that asks for you user name.
Step 2: Type in your username and password.
Step 3: Type "sudo nano /etc/X11/xorg.conf" (without quotes) You will need to type your password.
Step 4: Look through the file and find a line like " Driver "ati" "
Step 5: Change the "ati" to "radeon"
Step 6: Hit Ctrl + X then "Y" then enter.
Step 7: Type "sudo /etc/init.d/gdm restart" (without quotes) You may need to type your password.

That should do it! If not post back."""



Thank you to all that helped me, Hopefully this thread will help others in the future.

---

### Post by ReconIsense on 2007-12-28
where exactly do u start the aforementioned process? at GRUB? in the terminal? and also do you need the cd inserted while doing so?

i have a slimlar problem. on grub at best my screen is corrupted at worst it's completly black.
so I boot with the cd inserted and have to re install ubuntu to even get my comp operating. All this while connected to an external monitor (which will still display the corruption when it shows up).
i tried booting with
" nosplash noapic nolapic"

which gave me limited success, yet my screen will eventually get glitchy and freeze, and i'm back to square 1.

btw i'm running Fiesty Fawn 7.04 on a AMD Turion 64 Moblie, ATI X700 Moblie, acer Ferrari 4005wlmi notebook with windows xp sp2 on a separate partition.

---

