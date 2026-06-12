---
title: "Upgrade Problems Please Help Me!"
date: 2006-10-30
forum: Absolute Beginner Talk
---

### Post by mcglnx on 2006-10-30
Hi,

I've upgrade to 6.10 last week and found out a couple of issues that are really annoying! Ubuntu is not ready for human beings - I was innocently thing so, I was wrong.

For the Record I got a new Dell Inspiron 6400 with an ATI Radeon X1400 card. I already fixed the DRI issue first before with 6.6.

Here is a quick list of the issues I got:
[LIST]
[*]The CD booted up,... then stopped in the middle of the boot process. I rebooted disabling the splash (not human friendly) to find out a "BUG - SOFT lokup detected on CPU#0" message. I fixed this removing the ipw3945 modules list.
[*] Then started to upgrade and had an issue with the kernel - my /boot partition of 50M was too small - the installation continued blindly letting my computer in an un-stable state! 
[*] I was able to upgrade using the CD procedure instead of installing from scratch, then I had to fix (again) the same issue.\
[*] Finaly I got everything working but still have the 'DRI initialization failed' issue. I tried to un-install the fglrx then re-install the ATI driver - but still have the same issue.
[*] BTW: It took me some time to realize the default sh is dash instead of bash - makes me trouble to run the ATI driver installation.
[*] BTW: I cannot access any console any more (Atl-F1,...)
[*] BTW: I cannot watch DVD any more.
[*] small one: F-Spot screen saver is not configured by default - the displaying nasty error message. Would be greate to let him search for images by example about "Human beings" or region of the installed computer?
[/LIST]

All in all I liked the idea of Ubuntu- I'm just a bit disapointed because I don't want to spend much time configuring my computer any more. I was considering buying a Mac but finally decided for Ubunut - I was wrong.

As I told I don't have much time to 'play' with computer at home. But may be if I can help,....just let me know!

Cheers,
M.

---

### Post by Lord Illidan on 2006-10-30
Nah, it is ready for human beings, wake up and realise you are not one of them...hehe

Ok seriously... can u reword your titles in future. "Upgrade Problem" is better than all this Ubuntu is NOT ready for bla bla bla...ok

About upgrades etc, it recommended to do a fresh install.

---

### Post by happy-and-lost on 2006-10-30
You may have to wait a while for your graphics problems (i.e. DVD playing etc.) to be sorted, the ATi driver doesn't work on Edgy... yet.

---

### Post by lazyart on 2006-10-30
> **mcglnx said:**
> 
All in all I liked the idea of Ubuntu- I'm just a bit disapointed because I don't want to spend much time configuring my computer any more.

Like any OS installation, one must configure.  Otherwise you SHOULD be buying something where it's all done for you-- like a Mac.

Was 6.06 not working?  Was the upgrade necessary?  Is returning to 6.06 not an option?

---

### Post by John.Michael.Kane on 2006-10-30
mcglnx your thread title has been cleaned up. 

Also mcglnx if you want help edit you post or start a thread in proper section of the forum stating what the issues are.  

In regards to edgy have a read [http://ubuntuforums.org/showthread.php?t=286209](http://ubuntuforums.org/showthread.php?t=286209)

---

### Post by mcglnx on 2006-10-31
Thanks - for your suggestion.
At least the title of the thread woke you up compared to my previous (kind) posts. Do not take it personnaly though! :)

Ok - I read some thread saying that 6.10 was not considered as 'stable'. What confused me is the very nice and promissing announcement that have been posted for 6.10. I thought it was a green light! next time I see something new on the Ubuntu Home page I'll be more cautious. My fault.

BTW: I found this link regarding ATI: [http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide). I'll try tonight!

Thanks again for your answers and advices!

M.

---

### Post by mcglnx on 2006-11-04
Current status:
 ATI update fixed the issue! yes!

However, 
- I can only run beryl with DRI disabled, which prevents me to run applications like fgl_glxgears
- With DRI I got around 400FPS, without DRI (Xgl and beryl) I got 1200FPS!
- Under Xgl, the control panel of Xine does not displays or is scrambled.
- My TTY consols are not usable: the screen is a big chaos!

- I was not able to use the Ricoh Card Reader.
- The Wireless network worked with 6.6LTS but not with 6.10. I installed the intel driver using ndiswrapper, but no success. Interface does not want to show using 'ifup wlan0'

Thx

---

