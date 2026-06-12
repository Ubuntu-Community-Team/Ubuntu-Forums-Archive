---
title: "Old iMac - Ubuntu capable ?"
date: 2014-12-27
forum: Apple Hardware Users
---

### Post by michael-piziak on 2014-12-27
I have a very old iMac that I'm sure has the PPC/motorolla chip in it.  If it's possible, what version of Ubuntu (or a lite version) might work on it?
It's one of the first generation iMacs that is the size of a small old style television.
I'm just going to put it in the basement and only use it to web browse with.

p.s. I would like to use a usb flash drive to pull this off - if it's possible.

---

### Post by mörgæs on 2014-12-27
Does this help?
[http://ubuntuforums.org/showthread.php?t=361236&page=86&p=12707046&viewfull=1#post12707046](http://ubuntuforums.org/showthread.php?t=361236&page=86&p=12707046&viewfull=1#post12707046)

---

### Post by michael-piziak on 2014-12-27
Thanks.  Looks like I'll need to burn a CD to pull this off - which I'll buy next time I'm out.
In the mean time, anyone that can give me tips on burning the CD for this project would be greatly appreciated.

---

### Post by ajgreeny on 2014-12-27
Burn the image file (.iso file) as an image, don't just copy it to the DVD,; note a DVD, which you may need as Xubuntu will not fit on a CD; not sure if Lubuntu does now or not.

I see that the linked post already suggests you try Lubuntu or Xubuntu, which was to be my first recommendation to you, but for the burning, just make sure you burn at the slowest speed available to you on whatever hardware or software you use, and before you attempt to install from the DVD use the "Check install media" or similar wording, assuming it's available on a Mac boot system.

---

### Post by michael-piziak on 2014-12-27
ok thanks for the tips.
I suppose "Brasero Disc Burner" should be fine to use, eh?

---

### Post by ajgreeny on 2014-12-27
Of all the CD/DVD burners in Linux that I have used brasero is the one that has given me most bad burns, but having said that, it is still a very small number of times, so it should be OK.

I use a few KDE apps in my Xubuntu setup, such as **digikam** and **kmymoney** which bring in a lot of kde libs so I also often also add **k3b** to my systems, which is probably the best burner available for Linux in my opinion.  I also like xfburn which is the default in Xubuntu/XFCE and so far has never let me down.

---

### Post by michael-piziak on 2014-12-27
I just burned a disk with Brasero.  I burned the Lubuntu 12.04 PPC iso.  That should be a lite OS shouldn't it ?

---

### Post by michael-piziak on 2014-12-27
ok, I booted the burned disk on the old iMac.  Looks like it was a good burn.
I booted the powerpc option of lubuntu

I finally got to this point -> lubuntu@lubuntu:~s
It wants me to type something there.  Any help would be appreciated.

p.s. Where I have the iMac now, it's only hooked up to power.  If I can get lubuntu on it, I'll move it to an ethernet connection in the basement.

update:  I am able to now report that this old imac is a 350mhz G3 processoer with 640 megs of ram and around 110 gig HD.  If there is an even lighter version of Ubuntu to put on this aged system, please do tell and I'll burn another disk.  Perhpas Lubuntu 10.04 lts would be better - if I can find the download for it.

---

### Post by mörgæs on 2014-12-27
10.04 is out of support so that is a no-go.

All installations should be done with wired internet access, especially using the minimal ISO.

At the prompt you have the option of typing one of these:

```
1) sudo apt-get install lubuntu-desktop
2) sudo apt-get install lubuntu-desktop --no-install-recommends
3) sudo apt-get install lubuntu-core
```

ordered from heaviest to lightest. On your hardware they could take a while.

Many people hunt for an extreme-light operative system in order to gain some speed. It's a waste of time, one should be hunting extreme-light applications in stead. 

More info in the link in my signature.

---

### Post by michael-piziak on 2014-12-27
> **mörgæs said:**
> 10.04 is out of support so that is a no-go.

All installations should be done with wired internet access, especially using the minimal ISO.

At the prompt you have the option of typing one of these:

```
1) sudo apt-get install lubuntu-desktop
2) sudo apt-get install lubuntu-desktop --no-install-recommends
3) sudo apt-get install lubuntu-core
```

ordered from heaviest to lightest. On your hardware they could take a while.

Many people hunt for an extreme-light operative system in order to gain some speed. It's a waste of time, one should be hunting extreme-light applications in stead. 

More info in the link in my signature.

ok, I chose #3 and typed in sudo apt-get install lubuntu-core

it then proceeded to do the following on screen:
Reading package lists ... done
building dependency tree
Reading state information ... done
ubuntu-core is already the newest version
__ upgrade, 0 newly installed, 0 to remove and 0 not upgraded   [the blank before upgrade was off screen but I assume it was 0 too].

Then it went back to the prompt.

I don't think anything was installed, as this happened in about a minute.

---

### Post by mörgæs on 2014-12-27
What does **startx** yield? 

By the way, you will get more response if you remove the 'solved' flag.

---

### Post by michael-piziak on 2014-12-27
I got a lot of server errors.  For example, could not connect to server.

Please note, this iMac isn't connected to the internet yet.  Must it be to do this install ?

---

### Post by mörgæs on 2014-12-27
Please see post #9 which you quoted yourself in post #10.

---

### Post by michael-piziak on 2014-12-27
Umh, sorry.

I'm still stuck at this point if someone can assist.

---

### Post by este.el.paz on 2014-12-30
@michael:

There are a number of threads in the forum about "G3/G4 iMac"  and or "Testers wanted for 12.04 PPC" . . . that you should read through.  Also the "PowerPCFAQ" and "Known issues" wiki's are available . . . .

[https://wiki.ubuntu.com/PowerPCFAQ](https://wiki.ubuntu.com/PowerPCFAQ)

[https://wiki.ubuntu.com/PowerPCKnownIssues](https://wiki.ubuntu.com/PowerPCKnownIssues)

You ***should*** be able to get a 12.04 version running without too much problem on a G3, but first try out the LiveDVD and see if you can boot and run the system that way . . . .  It seems like you are trying the alt installer . . . which is "minimal" . . . but requires more time downloading the system . . . .  I did have this "computer is not connected" error on a number of installs on my G4 iMac that might have been some bug related problem . . . .  But, you have a lot of reading to do to have more insight into where your problem might be occurring . . . .  Try out various flavors and see which one works best on your computer, it could be Lubuntu, or it could be Xubuntu, but 12.04 should be OK.

e.e.p.

---

### Post by michael-piziak on 2014-12-30
This is basically a slow ongoing project for me.  Right now the iMac is sitting in the basement on a table awaiting me to find a way to hook it up to power.  It does have the ethernet cord to it, so that is good.

Do you think I should try the regular Ubuntu 12.04 PPC version first ?

---

### Post by este.el.paz on 2014-12-30
> **michael-piziak said:**
> This is basically a slow ongoing project for me.  Right now the iMac is sitting in the basement on a table awaiting me to find a way to hook it up to power.  It does have the ethernet cord to it, so that is good.

Do you think I should try the regular Ubuntu 12.04 PPC version first ?

@michael:

That could be a source of your problem . . . if the computer is not hooked to power . . . it's probably not going to work . . . no matter which system you choose . . . ????  : - ))

On the "regular" Ubuntu, that actually tends to be more resource hungry I believe . . . so depending on how your install is going with the minimal installer, try adding "lxde" or "xfce" desktop environments on top of the "core" . . . .  Or, try the "live" iso(s) of Lubuntu or Xubuntu 12.04 PPC . . . burn them to CD or DVD and try booting them while holding the "c" key and see if it will boot without adding any boot parameters . . . you might need some boot params on the second Yaboot window prompt . . . some of them you can see if you hit the "tab" key . . . .  I don't have a G3 so I don't know the exact details . . . any threads by "rsavage" or "str8bs" should give accurate info about PPC issues, a few others will show up in those threads.  But, the "live" version iso will let you run the system w/o installing to see which one works best . . . .

e.e.p

.

---

### Post by michael-piziak on 2014-12-30
LOL, I had it hooked to power upstairs the other day when I [COLOR=#000000]burned the Lubuntu 12.04 PPC iso.   I don't know if that was a "live ISO" though, but it did take up nearly an entire CD.

I will look for a live ISO, or perhaps you could link me to one, and I'll burn another disk.

Thanks for your continued help![/COLOR]

---

### Post by este.el.paz on 2014-12-30
Linux is a DIY system . . . seek and ye shall find . . . but you should see something like "live desktop" in the file name . . . .  Possibly the Lu PPC live version might fit on a CD . . . if you try to boot it you should get something like "the default option is 'live'" . . . so you would type "live" . . . and it should eventually get you to a desktop GUI . . . it takes some time.  If there is no "live" or live desktop" in the file name, it's just the installer, either "alt" or "minimal" and you have to install it before you can test it out.

e.e.p.

---

### Post by michael-piziak on 2014-12-30
Thanks.

I have 4 CD's burned, one of them should work.  Three are distros of Ubuntu and one is a Mint disk.

---

### Post by este.el.paz on 2014-12-30
> **michael-piziak said:**
> Thanks.

I have 4 CD's burned, one of them should work.  Three are distros of Ubuntu and one is a Mint disk.

OK . . . right, if they are "ppc" they will work, either for install or live . . . on the "mint" . . . is that "mintppc" or "linux mint"?  If it's LM, that does not support PPC . . . .

e.e.p.

---

### Post by michael-piziak on 2014-12-30
Yep, the mint iso is a PPC distro.

I'm installing lubuntu on it now - seems that it's going to take - I'll update you soon if it's working.

---

### Post by michael-piziak on 2014-12-30
ok, after a lengthy install, it restarted and asked for my name and password.  I entered those, then it told me so many updates were available and etc....

Now it's sitting there with the prompt wanting me to enter some command - ?

p.s. I tried "xstart" with no luck.

---

### Post by este.el.paz on 2014-12-30
> **michael-piziak said:**
> ok, after a lengthy install, it restarted and asked for my name and password.  I entered those, then it told me so many updates were available and etc....

Now it's sitting there with the prompt wanting me to enter some command - ?

p.s. I tried "xstart" with no luck.

m-p:  Are you in a TTY window or logged into GUI desktop?  Is this "software updater"??  Or Terminal prompt?  I would say if it's in the GUI then you enter your admin password and hit the "return" key . . . see what happens.

e.

PS:  It would be "startx" . . . but that is only if you are in the TTY "console" and the GUI isn't loading.

---

### Post by michael-piziak on 2014-12-30
I'm definitely not logged into a GUI desktop.  It is simply a terminal prompt (that appeared after I entered my username and password for it).  I tried entering password again but no go - same prompt is there.

---

### Post by este.el.paz on 2014-12-30
> **michael-piziak said:**
> I'm definitely not logged into a GUI desktop.  It is simply a terminal prompt (that appeared after I entered my username and password for it).  I tried entering password again but no go - same prompt is there.

OK, well this is where it's going to get more technical, and possibly exceed my capability to remotely figure out what is going on.  Depending on what type of install you did, and the selections you made or didn't make in the installer could vary wildly.  I've been "talking" to 3 people here this morning . . . do you have a good internet connection yet?

Anyway, if you are in a Terminal, first try to "reboot" . . . type "sudo reboot" (no quotes) and let the system shut down and boot itself and see if you get a Yaboot window opening with options for linux, osx, or cdrom.  You should leave OSX on the computer.  

Later on, back in a Terminal window you can try "sudo apt-get update" . . . and it will ask for yr password, and should run through a list of "sources" . . . followed by the prompt again, then try "sudo apt-get upgrade" and it should show a list of upgrades and ask yes/no to install . . . if it shows some as "held back" that is usually the kernel upgrade(s) . . . you can get those later with "sudo apt-get dist-upgrade" after again running the "update" . . . .

But, really, the first thing is to try to get to the GUI, try to shut the computer down, and then reboot while either holding "option" key, let OSX boot loader window open and see if the "penguin" shows up . . . or, could be if you reboot the Yaboot window will open and show options for linux, osx, or cdrom . . . type "l" for linux . . . see if the GUI loads . . . then try the update/upgrade stuff.

---

### Post by michael-piziak on 2014-12-30
Thanks for all your suggestions, I will try them on my latest attempt.  Already I've installed xubuntu, kubuntu, lubuntu, and even mint (powerpc) and everything goes well until it's finished and I reboot.

I'm tempted to try the oldest Ubuntu for PPC I can locate.

This system is quickly becoming a brick.  I'll mess with it for another week, but when garbage day comes it is gone if it is not running an OS by then (garbage runs on Tuesday morning - are you listening little iMac ?)

p.s. I got rid of os X with the installs a long time ago.

---

### Post by este.el.paz on 2014-12-30
> **michael-piziak said:**
> Thanks for all your suggestions, I will try them on my latest attempt.  Already I've installed xubuntu, kubuntu, lubuntu, and even mint (powerpc) and everything goes well until it's finished and I reboot.

OK, reading back through the thread it does look like you were making a choice between being plugged in to power OR plugged in to internet--whereas the installer requests both plugged in to power AND best is an ethernet connection, because wifi usually is not working with the broadcom wifi card.  And then the question is whether the "installs" have actually happened, and if so, what happens after you reboot??  Actually best of all is "shut down" and do a hard reboot.

>  I'm tempted to try the oldest Ubuntu for PPC I can locate.
p.s. I got rid of os X with the installs a long time ago.

OK, like "Morgaes" said, the "older" OSs are "not supported" . . . you ***should**** be able to get 12.04 installed without too much effort, but that doesn't necessarily mean "effortless" . . . many systems need an "xorg.conf" file for your specific computer . . . .  Also, the general wisdom is to keep OSX going on an Apple . . . and do a dualboot set up using Yaboot.

e.e.p.

---

### Post by michael-piziak on 2014-12-30
This morning, in the basement, I connected the little iMac to power and ethernet (internet) before I tried all these installs.  I've shutdown many times and did many hardboots.

The project is on hold now until tomorrow morning - smiles !

p.s. I know older versions of Ubuntu aren't supported - but the iso files of them are out there, and if I can get one of them to work and use a web browser, I'll roll with it.

---

### Post by michael-piziak on 2014-12-31
As an experiment, I installed Ubuntu 5.01.  It actually worked.  However, it is so ancient that you can't do much with it - for example the web browser can't even do facebook.

I'm going to try a few more, more recent, installs and see what I get.  I know I couldn't get the 12.04 to work.  I'm going to try 9.01 and 10.04 now.  I think the Ram (128 megs) is what is holding me back.

---

### Post by michael-piziak on 2014-12-31
ok, I installed xubuntu 12.04 lts for powerpc (32 bit).  I thought I installed 12.04 - anyways it is acting like 14.04 was installed when you see my screen shot below.

When it reboots, it asks for my login and password and then awaits a prompt.

I have attached a photographed screen shot of how far I get.  Any assistance would be appreciated.

---

