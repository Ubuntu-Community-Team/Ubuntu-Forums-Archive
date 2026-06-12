---
title: "Lucent Winmodem help...still"
date: 2006-02-27
forum: Absolute Beginner Talk
---

### Post by HSSsb17 on 2006-02-27
Ok...I've followed steps for countless methods of installing Lucent Winmodem drivers.  I always seem to have trouble with this "modprobe" thing.

I type "sudo modprobe ltserial" and I get:
"FATAL:  Error inserting ltserial (/lib/modules/2.6.12-9-386/extra/ltserial.ko) Invalid Argument"

What does this mean?
How do I go about fixing it?
What is modprobe, anyway?
Is Linux worth all of this?

Help is greatly appreciated.  Thanks.

---

### Post by stanz on 2006-02-28
Hey HSSsb17... 
Is this the info your following?
**[DialupModemHowto]("https://wiki.ubuntu.com/DialupModemHowto?action=fullsearch&value=linkto%3A%22DialupModemHowto%22&context=180"):**
[https://wiki.ubuntu.com/DialupModemHowto?highlight=%28dialupmodemhowto%29]("https://wiki.ubuntu.com/DialupModemHowto?highlight=%28dialupmodemhowto%29")

Have you tried, or does.. 'wvdial' work for ya?
Maybe give more info on what cha got~ in your box.
 =========
I pulled out my M$ modems, and picked up an external serial modem... and i'll
tell ya, Linux~ Ubuntu, Debian... sure is worth it!
Sorry I can't tell ya more.. some xpert will pass by soon tho!

---

### Post by HSSsb17 on 2006-02-28
I have a HP Pavilion Desktop PC, Lucent Winmodem 56k (driver 8.31).  I have two hard drives (1st 40GB for Windows/boot, 2nd 160GB; 130 for Windows storage and 30 for linux (since I dont plan to use it that often)).  I am fairly familiar with windows, and I would like to become acquainted with a linux system, but I'm not having much luck with that.  I did look at that link you gave, but I'm still having problems with anything that uses the "modprobe" command.  Maybe that information helped?

---

### Post by stanz on 2006-03-01
Hey HSSsb17....
Naaa- that info don't help much... what info did you get from the 'ScanModem" tool?
I've done a search {that button under 'sign-in'..} and found some very detailed:  "[Solved Lucent ltmodem]("http://ubuntuforums.org/showthread.php?t=93852&highlight=Lucent+Winmodem")" posts. Very DETAILED to your error messege.
Have you followed the 'steps done' in your other post? What was your results? Spend more time- re-doing, the nessesary steps- described in "[finnish]("http://ubuntuforums.org/showthread.php?t=93852&highlight=Lucent+Winmodem")" post.
*> [I]it's a product of _huge investigation_ starting from linmodems.org, which took me **3 weeks** :smile:. I've read almost a **100 guides** and readme's and none of them helped me fully. I had to find myself that 2.6.12-9-386 kernel is compiled with gcc-3.4, and it's required for proper modules compilation.* --------------------
I must refer you to the other posts, as i can't be a help- with winmodems.
 I avoided all these hassles ~ and bought the external serial modem ~ and it works both Linux & M$ !
---------------------
[FizDev Thread:]("http://ubuntuforums.org/showthread.php?t=112751&highlight=Lucent+Winmodem")
Also, you might want to search in this forum for "Lucent Modem" if you haven't already. You should find what you are looking for.

Note : I've just seen these, might help you out![/I] 
[https://wiki.ubuntu.com/DialupModemH...ht=%28modem%29]("https://wiki.ubuntu.com/DialupModemHowto?highlight=%28modem%29")
[https://wiki.ubuntu.com/DialupModemH...tingUpMod  ems]("https://wiki.ubuntu.com/DialupModemHowto?action=show&redirect=SettingUpModems")
[https://wiki.ubuntu.com/SmartLinkMod...ht=%28modem%29]("https://wiki.ubuntu.com/SmartLinkModemDriverHowTo/FromSource?highlight=%28modem%29")                                                                                                              *                 Last edited by FizDev : 01-05-2006 at 12:05 AM.                                  *

---

### Post by DiscoKiller on 2006-03-01
looking at that bit about the kernel being compiled with gcc3.4 try entering this before you try any installation commands


sudo export CC=/usr/bin/gcc-3.4

then ur p`word, then follow any installation instructions


Good Luck

DK

---

### Post by stanz on 2006-03-01
[U]
[/U]Yeah, HSSsb17~ I was not encouraging you to recompile your kernel !!
Those are just links, to other posts- offering some advise, and also to show-
things take time and research, then more reading & researching.
I'm glad to see DiscoKiller passed by & offered some info!
[ ]("http://ubuntuforums.org/member.php?u=72586")

---

### Post by DiscoKiller on 2006-03-03
hey despite my very limited knowledge i like to trawl the forums to see if i can pass on my wisdom somehow, makes me feel all fuzzy and warm inside \\:D/

anyhoo i only said that coz when i was trying to install the spcaxx drivers for my webcam, if i did it without first inputting that command into my terminal then it wouldn`t work, i now have it as a script to execute on bootup :D  but yeah the same reason was given in the howto i followed, that the kernel was complied using Gcc 3.4 and so they said i had to use that when compiling my drivers. i dont pretend to understand but parrot fashio isnt always bad :cool: 

laters

DK

---

### Post by DiscoKiller on 2006-03-03
[QUOTE=HSSsb17]
Is Linux worth all of this?
[/QUOTE]

well i recently re installed winxp pro on a small partition to see what it was like and i`ve had nothing but trouble, i would never go back to it permanently either. trust me dude if u persevere you will get so much out of ubuntu...

DK

---

### Post by Bentu on 2006-03-04
Here is the modem that I have:
Agere Systems (formerly Lucent) LT Winmodem Lucent/Agere DSP Mars or Apollo chipset
I am using it right now with the 2.6 kernel, it's your basic, dreaded "winmodem," and it works fine. If you're having trouble it's because of your driver, the one below configures everything when installed, avoid suffering through all the convoluted instructions and buying more hardware. Just download, untar, run, enter your isp's settings and surf the web. If the one below doesn't work, this site has many more, just get similar that will do the configuration (if the one below doesn't work for you) and be done with it. Avoid those drivers that don't do the configuration, if at all possible, they're too much hassle.

Link to driver:
[http://linmodems.technion.ac.il/packages/ltmodem/kernel-2.6/ltmodem-8.26b1.tar.gz](http://linmodems.technion.ac.il/packages/ltmodem/kernel-2.6/ltmodem-8.26b1.tar.gz)

---

### Post by stanz on 2006-03-05
Hi All~,
HSSsb17- Howz it working for ya??...?
--------
DiscoKiller, Right On!...I Trolled here, myself too...and have only, so much i can offer- this exchange, helps me remember~ what i *think* i know. :-k
---------------
"**anyhoo, i only said that coz when i was trying to install the spcaxx drivers for my webcam**" - 
---------------
Kewl, I was jus' looking into that too! Tho, i haven't read enough or got into it yet, I'm trying to get mine to work (when i get back into my ubuntubox).
Another day...Another Thread...!
--------------
Hey Bentu..
> your basic, dreaded "winmodem,
Hummm.. That kinda gives me an incentive, to pull my ol' modem's outta storage & try that!?

Thumbs up to ya's.....Later!   :grin:

---

### Post by Bentu on 2006-03-05
Stanz,
  
  Fyi, I just pulled out an antique conextant hcf winmodem out of the junk pile this afternoon, on the web under debian in no time at all. It works just as well under debian as under windows, can't tell any difference, got the driver from the linuxtant website, the free driver version. All I did was activate the modem (using the networking tool), installed wvdial, installed the driver, ran wvdial.conf, ran wvdial as su, boom, on the web. Don't know why the instructions everywhere are so complex. I even installed the new firefox version, all this was done in a flash, bet I didn't spend a half hour on it. Of course, I'm different than most people, I'm too poor and stingy to buy stuff so I won't throw the modems away, I try to make them work!

---

### Post by MrChips on 2006-03-05
I had nothin' but trouble trying to get on with a modem.  The device manager kept putting it in odd places and yadayadayada...I wound up sharing the connection with my Windows comp.

You may want to check with your ISP about info on a Linux config.  My ISP had a section for it but by the time I got to it I was hooked up and had chosen to wait out the arrival of DSL in my area.  

Oh, but someday *prays*

Good Luck! btw...Linux is worth it. ;)

---

### Post by towsonu2003 on 2006-03-05
I lost track: did the op succeeded compiling the driver after exporting gcc 3.4?

---

### Post by HSSsb17 on 2006-03-06
Sorry, I actually gave up on this whole modem thing for a while, but I'm still determined.  I've tried all of the links and everything.  I come up with the same problem every time at anything that uses "modprobe."  It still gives me that "invalid arguement" error.  I think I'll just buy an external modem that would work for both ubuntu and windows.  Does anybody have any suggestions as to what modem would be cheap and efficient, or should I not give up on my winmodem yet?

---

### Post by Endwin on 2006-03-06
Greetings, 

I too had issues with the ltwinmodem thing when I set up a laptop with ubuntu for a friend. As far as I can tell the wiki lies. Despite the restricted modules saying that it has the drivers they are not there. If you bring up Synaptic and look at installed files you will see directories of everything else BUT the lt_modem dir. I don't know if it was removed and someone forgot to update the description of the package or what but as far as the wiki instructions go you can't do it.

My solution:

1. Undo anything the wiki told you to do, the editing of files namely. Better yet may want to consider a fresh install. 

2. Download the .deb package from [http://linmodems.technion.ac.il/pack...el-2.6/Ubuntu/]("http://linmodems.technion.ac.il/pack...el-2.6/Ubuntu/") Note that this only has i386 and 686 versions of the deb package if you need a different version for a kernel you want to install you will have to compile it from source and that is beyond my scope at the moment. This will work for a stock install though.

3. Reboot - Once you have the package installed and have rebooted you should be able to have your modem now. Go to System -> Administration -> Networking and enable the modem and make sure to go to the second tab and have it auto detect your modem which should be /dev/modem. However if it does not detect it then something is probably wrong.

I hope this helps some.

---

### Post by towsonu2003 on 2006-03-06
[QUOTE=Endwin]Greetings, 

I too had issues with the ltwinmodem thing when I set up a laptop with ubuntu for a friend. As far as I can tell the wiki lies. Despite the restricted modules saying that it has the drivers they are not there. If you bring up Synaptic and look at installed files you will see directories of everything else BUT the lt_modem dir. I don't know if it was removed and someone forgot to update the description of the package or what but as far as the wiki instructions go you can't do it.

My solution:

1. Undo anything the wiki told you to do, the editing of files namely. Better yet may want to consider a fresh install. 

2. Download the .deb package from [http://linmodems.technion.ac.il/pack...el-2.6/Ubuntu/]("http://linmodems.technion.ac.il/pack...el-2.6/Ubuntu/") Note that this only has i386 and 686 versions of the deb package if you need a different version for a kernel you want to install you will have to compile it from source and that is beyond my scope at the moment. This will work for a stock install though.

3. Reboot - Once you have the package installed and have rebooted you should be able to have your modem now. Go to System -> Administration -> Networking and enable the modem and make sure to go to the second tab and have it auto detect your modem which should be /dev/modem. However if it does not detect it then something is probably wrong.

I hope this helps some.[/QUOTE]
I think it is also time for you to file a bug report. 

@Ednwin: any chance you can edit the wiki for correct info? thanks.

---

