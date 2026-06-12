---
title: "Ubuntu freezes after installing"
date: 2007-05-16
forum: Absolute Beginner Talk
---

### Post by linuksman on 2007-05-16
I'm having problems installing ubuntu.  I can load the live-cd fine and then install from the icon on the desktop.  The installation process seems to go well.  Then when I boot it takes several minutes to load.  It says overrange on my lcd a few times, and then finally goes to the orange background and animated cursor.  The computer seemingly freezes here.  I tried moving the mouse around, and it's position is updated on screen slowly, about once every one and a half seconds.  Although it looks like it could be loading, nothing happens..

Using Ubuntu from the live-cd works completely fine.  Attempting to install from the alternate-install ISO hangs during install.  

My system specs are:
Athlon 3500+
ECS nforce4-A939 ([http://www.ecs.com.tw/ECSWebSite/Products/ProductsDetail.aspx?DetailID=493&DetailName=Feature&MenuID=47&LanID=9](http://www.ecs.com.tw/ECSWebSite/Products/ProductsDetail.aspx?DetailID=493&DetailName=Feature&MenuID=47&LanID=9))
ATI X800 Pro 256mB pcie
Mushkin value memory 1 GB 3-3-3-8 200Mhz
Maxtor 200GB IDE
Logitech Keyboard, G5 mouse
Nvidia Nforce networking controller
Airlink 101 XR usb network adapter
Realtek ALC655 Audio
Sceptre 22" X22WG-gamer (1680x1050)

Please help me,

---

### Post by Big_Croc7 on 2007-05-16
Which version of Ubuntu are you using (eg. Feisty, v7?)

Once it's had time to load after the orange screen appears (e.g. give it a minute to settle) press ctrl-alt-f1; if this brings up a text login screen, it might be a problem with X (this is the system that handles grahpics).  Ctrl-alt-f7 should bring you back to the graphical screen.  This won't help fix it, but it might help to diagnose the problem.

---

### Post by linuksman on 2007-05-16
ok I will try that.  

I think there must be some problem because it takes so long to get to the orange screen, and afterwards it just stays there, I don't notice anything 'settling'.

---

### Post by linuksman on 2007-05-16
what I meant was that the orange background appears and so does the animated cursor.  The animation of the cursor is very slow.  The cursor remains animated as if the computer is still trying to process something, but the mouse can move (the position of the cursor is updated slowly as I said before).  It remains like this indefinitely (I've waited for 30 min, 45 min, 10 min, etc.--no difference).  

Anyways I'm still going to do what you said when I get back to my computer../

---

### Post by linuksman on 2007-05-17
I tried hitting the ctrl shortcuts and I was able to get to the command prompt-type screen.  It is slow (significantly slower than when in recovery mode) as if it  is being encumbered by the slow gui.  The gui itself takes extremely long (I waited for like 40-50 min) and it actually let me log in.  After that the cursor switches eventually to the regular mouse icon, but nothing else happens and it stalls here (waited 1.5hrs+).  It's like as if the CPU was being used 100% constantly in windows xp, making everything else slow.

---

### Post by Big_Croc7 on 2007-05-17
It sounds like it's probably an issue with your graphics card drivers - I'm afraid I don't know anything about ATI cards, except that quite a lot of people have had problems getting them to work properly.  It's odd that the live cd works fine in that case though.

Sorry, just to clarify:
> It is slow (significantly slower than when in recovery mode) 
Do you mean, that the console you get using ctrl-alt-f1 is slower than using text-only boot mode from Grub's boot selection screen?

One other thing that might be causing issues, is the kernel.  The kernel version is the number you see on the selection at boot (e.g. 2.6.17.5819).  There are different kernels that are optimised for 64-bit processors, and sometimes using the generic i386 version can be more stable; however, I think graphics driver problems are more likely.

A thread on similar issues to yours, but caused by kernel issues, is here:
[http://ubuntuforums.org/showthread.php?t=421415](http://ubuntuforums.org/showthread.php?t=421415) though it dosen't really find a solution for your problem :-(

---

### Post by Jimmyd on 2007-05-17
Dont know if this will help you, I had all kinds of freezing, black screen problems last night trying to install ubuntu, finally reintalled and used the second option, safe graphics mode. Since then, it installed great, works great, no problems.

---

### Post by linuksman on 2007-05-17
Big_Croc7:  Yeah I was thinking it could be a gfx driver issue as well.  I followed the instructions for ATI x**** cardds according to the stickied thread in this forum to no avail.  Ya, I also found it odd that the live cd works fine with no problems, also the recovery mode seems to work fine.

Yes, it is how you said, the console I get by hitting ctrl+alt+f1 after booting normally into the gui mode appears significantly slower.  It takes longer to give me prompts and very long to execute commands.  Actually it seemed to have finally hung when I tried to do a 'sudo apt-get update' because nothing appeared after that..I eventually shut it down afterwards because it wasn't moving for 1+hrs.  

I only use the i386 version..I have not used the 64bit version due to issues like the one you described and others..

I will look into the thread..thanks

Jimmyd: What do you mean 'safe-graphics' mode?  I tried installing using the alternate install CD but that froze midway, and I don't remember seeing any 'safe-graphics' mode while installing from the GUI Live-CD..

---

### Post by linuksman on 2007-05-17
Jimmyd: Thanks, I found the safe graphics mode but installing via that mode halted midway.  It gave me some info! - 

[http://img412.imageshack.us/my.php?image=1sterrorscreenlinuxsaferl7.jpg](http://img412.imageshack.us/my.php?image=1sterrorscreenlinuxsaferl7.jpg)

[http://img255.imageshack.us/my.php?image=2nderrorscreenlinuxsaferf1.png](http://img255.imageshack.us/my.php?image=2nderrorscreenlinuxsaferf1.png)

---

### Post by Big_Croc7 on 2007-05-18
Have you tried sudo dpkg-reconfigure xserver-xorg ?  If not, try that, from recovery mode.  Let me know how that goes; I'm afraid I'm busy over the weekend, so probably won't be able to reply until Monday.  Good luck!

---

### Post by linuksman on 2007-05-22
Big_Croc7: That may have been the trick, but I didn't have to use it.  I had deleted the partitions a few days prior in an effort to install from the alternate installer, but since that didn't work I was going to install using the regular live-cd graphical gui in order to try what you said but then the OS loaded okay and everything was working fine.  

Well that was strange... but I guess now the problem is resolved

Thanks for the help everyone

---

