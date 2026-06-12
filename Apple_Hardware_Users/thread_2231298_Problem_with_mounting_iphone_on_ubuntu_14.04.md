---
title: "Problem with mounting iphone on ubuntu 14.04"
date: 2014-06-24
forum: Apple Hardware Users
---

### Post by steve_wales on 2014-06-24
Hi, please help!
I'm new to ubuntu (and indeed to Linux in general), and having problems with mounting and syncing to my phone.  I've tried all the main music players associated with the distro. Was able to mount for a while, but unable to sync music to the phone.  But now can't even do that; keep getting the trust issue on the phone and the following error "Unhandled lockdown error (20)". What am I doing wrong?  Please help, all I want to do is use my phone with a great OS

---

### Post by murrayatuptown on 2014-10-12
Same for me.

I never got my bleeping iPhone to work with anything but iTunes under Windows XP.

I just installed Ubuntu Studio and am checking items off a list as I find solutions  in Linux I need to completely eliminate any need to boot into Windows.

I don't really need to use the iPhone as a music player, but have some apps on it. I've not gotten app management on the phone to work well over the phone wireless service. It seemed like I could only (in Windows XP) connect the phone to iTunes software on the PC, then go to the App Store. There didn't seem to be an iTunes app to install on the phone itself, and I only seemed to be able to manage the iPhone through iTunes on the PC...and didn't find a iTunes app for the phone which seemed really weird...but Apple and iEverything make little sense to me.

Thank you.

Murray

---

### Post by Rob Sayer on 2014-10-12
Apple doesn't play well with others.  What model iPhone?  A lot of them don't seem to work with anything except iTunes.

---

### Post by GrouchyGaijin on 2014-10-12
I've been using Ubuntu for a while and I have never been able to sync music to the phone.
What does work for me is an app called EZMP3 Player.
**Description     from the iTunes store website:**
[I]EZMP3 Player is a music player which can play MP3 and M4A (Apple's Lossless Music 
File Format) files.  
You can directly input your music files and there is no need of iTunes sync. [/I]

Basically this is an alternative to the built in player on the phone, as such you can access the EZMP3 directory from the Document's directory on the phone.
I've always just dragged and dropped MP3s onto my phone and that works well for me.

With regard to the Unhandled lockdown error (20) - I've had this or similar lock down errors and usually the problem is that the phone is "closed" for lack of a better word.  Swiping my finger on the phone and entering my passcode then trying again to mount the phone usually works.  Sometimes I am forced to logout or even reboot before the computer will mount and open the phone.

When it does mount and open in the file manager you should get two windows.
1. For the basic (I won't say root) level of the phone.
2. The Documents directory on the phone.

I think that EZMP3 also supports transferring files via wifi, but I have not tried that.

The bottom line is that Apple makes it as difficult as possible for non-commercial OS users to connect their computers to an iPhone.

---

### Post by sp40140 on 2014-10-13
I suggest you don't put your effort into making your iDevices work on Ubuntu. Many.. Many have tried (including me).. But very few have been able to make it work. Even if you make it work, there is huge potential to currupt the lib on your device. 
You are better off with having a spare windows / mac machine. Or run windows in virtual env.
idevice + Ubuntu (linux) is crapshoot with very loong odds.

---

### Post by murrayatuptown on 2014-10-15
For me, current phone is an iPhone 4 (non-S).

My main goal is to keep the apps going - more important than the music player I can replace with a generic mp3 player. 

I have a bunch of tech apps on the phone like FFT, spectrum analysis, and so on.

I never wanted an iPhone anyway but inherited my daughter's hand-me-down one and do try to embrace it (even if I feel the need to bathe afterward).

I briefly considered my next phone might be a Android-based one if I can find same apps. According to some test site in Finland, audio performance (hardware, drivers, combination of same) is highly variable on  phones, even within the same brand because they are not consistent in design. Two models may have totally different audio hardware (DSP, ASIC or whatever), or same devices but different drivers. Disturbing.

I assume an Android phone can manage it's (Android store?) apps through Linux, but only know what I've learned in about a week of Ubuntu-tude.

With about 2 minutes of token effort at  Wine configuration, I discovered some educational DVD software I have that comes with integrated Windows, MAC and Linux 'player' utilities actually runs the Windows Player (.exe) in Ubuntu. The only reason I know it's happening through Wine is it asked for some input the first time it opened.

Maybe I should tell myself to not even think about trying iTunes through Wine. I suppose that's impossible because I'd have to install it and I have purged Windows.

I think I've gotten over that, but feel free to tell me "NO, don't waste another minute!"

Idea: Use my wife's Windows 7 laptop for the infrequent iTunes App Store visit I have to make. I know I have to, or should, create and point to my own folder, but I'll have to find out how uptight they are about more than one user logging into the Store from a specific PC. I already know they are weird about authorizing and device association with accounts.

Apologies for the off-color remark, but in contrast to all the Asian countries electronic gear is built in, I'd guess DPRK is the inspiration for  Apple software's user repression.

If I could get by with 2 cans & a string, I'd choose that over the iPhone. My iPhone experience has been incompatible with stress management and my language has grown more impolite.

Thank you Linux.

Hej, Grouchy Gaijin, arrigato to you too. 

I see two folders with a freebie (rebates = retail price) Android tablet that DOES connect, but I can't get past the lockout indignity with the iPhone.

---

### Post by d4m1r on 2014-10-16
I have an iPhone 4 and it works perfectly with my Ubuntu 12.04 LTS partition....

I don't however use it to sync anything. I can simply view the files on it and copy, paste, delete from within Ubuntu directly. It mounts automatically and without issue everytime however so it is very much possible. I mainly use it to download/delete pictures from my iPhone to my desktop PC. Google something along the lines of "idevicelib ubuntu" or similar...You might need to manually remove some libraries from your Ubuntu installation that come installed by default, and manually install some otherwise to get your iPhone recognized....

I wouldn't bother trying to get anything to sync with your iPhone under Ubuntu however. I heard Rythmbox could do it but I don't see the point of that....If you have any kind of Windows installation, iTunes under Windows works beautifully for syncing stuff to iDevices and Ubuntu has no equivalent as of yet, unfortunately.

---

### Post by Ric_Helm on 2014-10-27
I noticed that someone above mentioned Spectrum analysis, and FFT tool on their I phone. Try looking into the DSO302 on eBay, Alibaba, Amazon. It is a simple Quad Scope in a iPhone case. being open source, there are other apps that contributors have created to install on the same internal drive.  It works with Linux and windows.
Mac drops invisible files into the USB drive of the DSO302 and messes it up.

It is not a full-blown Electronics Test Equipment..however the functions are much more precise than Any iPhone app that is available for the iPhone, or even for an Android. phone, tablet or other.

Go to the seeedstudio site, and look into the independent programmers created apps for this device.. (and yes that is 3 e's in seeed)

---

### Post by d4m1r on 2015-01-25
For anyone still having issues mounting their iOS 7 iDevice to Ubuntu, check out [THIS]("http://itsfoss.com/mount-iphone-ipad-ios-7-ubuntu-13-10/") article.

Worked for me when I upgrade my iPhone 4 from iOS 5 to iOS 7. Using 12.04 x64 myself.

---

### Post by GrouchyGaijin on 2015-01-25
@d4m1r

Does this bring up two directories, one called iPhone and one called Documents on the iPhone?

I can connect my iPhone 5 running ios 8 without much problem except the Documents directory does not mount.
This makes my above suggestion for adding music unusable.

This is what happens when I plug my phone into my computer: (See screen shot at the link below.)
[https://mrkr.io/6p7njEPyfc](https://mrkr.io/6p7njEPyfc)

---

### Post by rhdinah on 2015-03-17
Just putting my two cents in this thread ...

As others have mentioned, everytime I plug in my iPhone 5 to charge I receive this dialog from 14.04

Unable to mount iPhone
Unhandled Lockdown error (-3)

Considering the popularity of the Apple iPhone and the number of Ubuntu users that use both Ubuntu and the Apple iPhone ... AND the amount of time these devices have been out ... IMHO this dialog should NOT be raised.

* To charge an iPhone you should not have to dismiss a dialog. I don't have to do that on my Mac and I should not have to do this on my Ubuntu system.
* I should not have to open/unlock my iPhone to prevent this dialog, if in fact this makes a difference. I don't have to do that on my Mac and I should not have to do this on my Ubuntu system.

I am not speaking of mounted directories ... I'm just using the USB port to charge my phone. This seems like *very* simple stuff and this should be fixed.

Thank you!

---

### Post by GrouchyGaijin on 2015-03-17
@rhdinah

To whom are you writing?  I do not think Apple will see your post here ;)

---

### Post by shantiq on 2016-02-11
well reading around trying to "see" an iphone 4 on 14.04 this worked excellently once i rebooted

one line at a time:


```
sudo apt-add-repository ppa:ingo/ios7support
sudo apt-get update && sudo apt-get upgrade
sudo mkdir /var/lib/lockdown   <<   this one was not needed for me it said the directory was already there
sudo chmod 777 /var/lib/lockdown
```

---

