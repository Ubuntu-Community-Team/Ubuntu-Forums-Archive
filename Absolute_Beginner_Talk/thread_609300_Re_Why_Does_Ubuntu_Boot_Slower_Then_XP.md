---
title: "Re: Why Does Ubuntu Boot Slower Then XP?"
date: 2007-11-10
forum: Absolute Beginner Talk
---

### Post by boriquajake on 2007-11-10
I installed Ubuntu about a week ago on my 18 month-old Presario laptop and it takes for freaking ever to boot. Within a few seconds some text comes up that gives me the option of pressing some button to get into some menu but after a few seconds that goes away and then the screen goes black. I mean it goes that weird kind of LCD screen black where the backlight is on but the pixels are are all black, more like the screen is showing me a picture of Bill Gates' soul than like the screen is off. Anyway, it stays in that condition for like five solid minutes before the username screen comes up. What do you guys think? Is this something I can fix?

---

### Post by LaRoza on 2007-11-10
That option to press a key (ESC), is for the boot menu. If you are not dual booting, it is hidden by default, you can unhide it by commenting out the hidden menu option in /boot/grub/menu.lst.

I have also seen that black screen problem (on a desktop computer, Compaq Presario, about 1 year old, forget the exact model).

It doesn't happen all the time though, does it do the same for you?

---

### Post by boriquajake on 2007-11-10
For me it does happen every time. While the black screen is up there is no response to any keys as far as I can tell. I have pressed any button I could think of, heh heh.

---

### Post by Paul820 on 2007-11-10
Go to post #5 in this link and try that [http://ubuntuforums.org/showthread.php?t=608207]("http://ubuntuforums.org/showthread.php?t=608207")

---

### Post by LaRoza on 2007-11-10
But it does boot eventually? I never waited that long with the desktop, so I don't know if it does boot. I just restart it.

I don't know any fixes, and don't know why it does this. On another Compaq Presario (the one I am using now), this problem does exist at all. Maybe there is a hardware issue with the older Presarios.

As for the LCD black screen, the backlight is the source of all light, and it takes energy (electricity) for the polarized liquid crystals to align. The default (no energy required) is black. Actually, it is not any colour. There are three layers of polarized films, and that prevents any light from passing through. The one in the middle changes to let light through.

---

### Post by boriquajake on 2007-11-10
> **Paul820 said:**
> Go to post #5 in this link and try that [http://ubuntuforums.org/showthread.php?t=608207]("http://ubuntuforums.org/showthread.php?t=608207")

Well, I went to that thread and followed the first part of the instructions, i.e. I opened up the terminal and entered sudo gedit /boot/grub/menu.lst 

That got me into whatever that is but the next instruction in the post is to "make a backup". What does that have to do with my problem? Is it just good policy to make a backup before jerking around with the menu.lst thing or does that somehow solve my problem? I know, I know, I am a total noob.

---

### Post by Paul820 on 2007-11-10
You are reading post #4, go to post #5. Post four was for someone else who wanted to mess with the menu.lst. Yes, messing with system files ( anything not in your home folder ) can wreck your system if you don't know what you are doing so it's wise to make a backup first. Anyway, post #5 is what you want, the startupmanager one.

---

### Post by boriquajake on 2007-11-10
OK, that makes more sense. What is "synaptic" and where do I find it?

---

### Post by Paul820 on 2007-11-10
System->Administration->Synaptic Package Manager

---

### Post by boriquajake on 2007-11-10
> **Paul820 said:**
> You are reading post #4, go to post #5. Post four was for someone else who wanted to mess with the menu.lst. Yes, messing with system files ( anything not in your home folder ) can wreck your system if you don't know what you are doing so it's wise to make a backup first. Anyway, post #5 is what you want, the startupmanager one.


Something tells me you are steering me down the right path because another one of my issues is that fonts look really weird in gmail and certain other sites and you are pointing me to something to do with screen resolution. Maybe both issues are related?

---

### Post by Sef on 2007-11-10
> Something tells me you are steering me down the right path because another one of my issues is that fonts look really weird in gmail and certain other sites and you are pointing me to something to do with screen resolution. Maybe both issues are related?

Yes,  I would suspect a problem with the graphics card.   It could take so long to boot up because it looking for the driver, and bad driver can affect your fonts.   Could also be the card itself.

---

### Post by boriquajake on 2007-11-10
> **Paul820 said:**
> System->Administration->Synaptic Package Manager

OK I found the synaptic package manager and I entered startupmanager into the search field, but it does not seem to find anything. I really do not mean to be so obtuse, seriously. What am I missing?

---

### Post by Kingsley on 2007-11-10
Open up the command line and type this:
```
sudo apt-get install startupmanager
```

---

### Post by Paul820 on 2007-11-10
Are you using gutsy? It is in there on gutsy. If you are on feisty there is a deb file on getdeb.net under system tools.

---

### Post by boriquajake on 2007-11-10
Kingsley, I pasted what you said into the old terminal and after entering my root password I got this: >  sudo apt-get install startupmanager
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package startupmanager


Does that seem odd?

---

### Post by Sef on 2007-11-10
Applications > Accessories > Terminal

then type in this command:

```
sudo apt-get update
```

then type in this command:

```
sudo apt-get install startupmanager
```

You should always do an update before downloading any software.   This will give you the latest versions in the repositories.

---

### Post by boriquajake on 2007-11-10
> **Paul820 said:**
> Are you using gutsy? It is in there on gutsy. If you are on feisty there is a deb file on getdeb.net under system tools.

I think I am running 7.10. That is a fairly recent iteration of gutsy, isn't it? Hell, now I am really confused. ;-)

---

### Post by Sef on 2007-11-10
> I think I am running 7.10. That is a fairly recent iteration of gutsy, isn't it? Hell, now I am really confused. 

That is correct.  Gutsy Gibbon, 7.10, is the latest version of Ubuntu.

---

### Post by boriquajake on 2007-11-10
> **Sef said:**
> Applications > Accessories > Terminal

then type in this command:

```
sudo apt-get update
```

then type in this command:

```
sudo apt-get install startupmanager
```

You should always do an update before downloading any software.   This will give you the latest versions in the repositories.

Thank you for the tip about updates. I actually wrote down the code on a post-it for in the future. Anyway, after getting the update I again entered sudo apt-get install startupmanager and I once again got the couldn't find package message.

>  sudo apt-get install startupmanager
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package startupmanager


---

### Post by Paul820 on 2007-11-10
Yes, 7.10 is the latest, did you do what Sef said above? It's strange you are not getting it show up in synaptic. Can you post the contents of you sources.list file?
From the terminal
> **sudo gedit /etc/apt/sources.list**
Copy and paste the contents here.

---

### Post by boriquajake on 2007-11-10
Dangit, it is good of you people to take the time to help me deal with this. Anyway, here is the what came up on the source list:

> deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

# Line commented out by installer because it failed to verify:
#deb [http://pr.archive.ubuntu.com/ubuntu/](http://pr.archive.ubuntu.com/ubuntu/) gutsy main restricted
# Line commented out by installer because it failed to verify:
#deb-src [http://pr.archive.ubuntu.com/ubuntu/](http://pr.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
#deb [http://pr.archive.ubuntu.com/ubuntu/](http://pr.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
# Line commented out by installer because it failed to verify:
#deb-src [http://pr.archive.ubuntu.com/ubuntu/](http://pr.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# Line commented out by installer because it failed to verify:
#deb [http://pr.archive.ubuntu.com/ubuntu/](http://pr.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
#deb-src [http://pr.archive.ubuntu.com/ubuntu/](http://pr.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
#deb [http://pr.archive.ubuntu.com/ubuntu/](http://pr.archive.ubuntu.com/ubuntu/) gutsy-updates universe
# Line commented out by installer because it failed to verify:
#deb-src [http://pr.archive.ubuntu.com/ubuntu/](http://pr.archive.ubuntu.com/ubuntu/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# Line commented out by installer because it failed to verify:
#deb [http://pr.archive.ubuntu.com/ubuntu/](http://pr.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
#deb-src [http://pr.archive.ubuntu.com/ubuntu/](http://pr.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
#deb [http://pr.archive.ubuntu.com/ubuntu/](http://pr.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse
# Line commented out by installer because it failed to verify:
#deb-src [http://pr.archive.ubuntu.com/ubuntu/](http://pr.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://pr.archive.ubuntu.com/ubuntu/](http://pr.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
# deb-src [http://pr.archive.ubuntu.com/ubuntu/](http://pr.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

# Line commented out by installer because it failed to verify:
#deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
# Line commented out by installer because it failed to verify:
#deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
# Line commented out by installer because it failed to verify:
#deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
# Line commented out by installer because it failed to verify:
#deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
# Line commented out by installer because it failed to verify:
#deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
# Line commented out by installer because it failed to verify:
#deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse

That is a long pasting. I hope that is what you wanted me to do.

---

### Post by Paul820 on 2007-11-10
Yes, and there is your problem my friend, all your sources are commented out like load of others have been. On the lines that begin with** # deb** and **# deb-src**, take off the **#** from the beginning of those lines. Only those lines though and no others. And also the very top line where it says Cd rom, put a # at the beginning of that line as you don't need to install from cd. When you have done that run
> sudo apt get update
and then
> sudo apt-get install startupmanager

---

### Post by &lt;&lt;joe&gt;&gt; on 2007-11-10
anyone know why everyones source list are commented out?
welll not everyone just alot .... bug?

---

### Post by Paul820 on 2007-11-10
It's usually when gutsy is installing when you have no internet connection. It tries to get the updates online in the install process and with there being no connection it comments them out for some reason. It should just leave them, feisty never did it so it must be something new for gutsy.

---

### Post by &lt;&lt;joe&gt;&gt; on 2007-11-10
interesting thanks

---

### Post by Paul820 on 2007-11-10
If you look above the url lines there is this
> # Line commented out by installer because it failed to verify:
So the installer commented them out. This can cause so many headaches for new people who don't have a clue what a source.list file is and why they can't find the packages that everyone else says are there. They should put it back to how it was before.

---

### Post by boriquajake on 2007-11-10
> **Paul820 said:**
> It's usually when gutsy is installing when you have no internet connection. It tries to get the updates online in the install process and with there being no connection it comments them out for some reason. It should just leave them, feisty never did it so it must be something new for gutsy.

I am confused, my internet connection is working fine. I mean, I am posting this stuff from the computer with the problem.

Also, Paul820, I did the update command an hour or so ago and I still did not have the startupmanager. Do you think it will work now for some reason?

Another thing, Paul, when you say that I should remove the # from the lines that begin # space deb (# deb) or the ones where they are close together (#deb) or does it not matter?

---

### Post by Paul820 on 2007-11-10
It doesn't matter, if it starts with **#deb** or **# deb**, take away the #

---

### Post by boriquajake on 2007-11-10
> **Paul820 said:**
> Yes, and there is your problem my friend, all your sources are commented out like load of others have been. On the lines that begin with** # deb** and **# deb-src**, take off the **#** from the beginning of those lines. Only those lines though and no others. And also the very top line where it says Cd rom, put a # at the beginning of that line as you don't need to install from cd. When you have done that run

and then

I ran the update again and got the same result:

> sudo apt-get update
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/main Translation-en_US
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/restricted Translation-en_US
Get:1 [http://pr.archive.ubuntu.com](http://pr.archive.ubuntu.com) gutsy-backports Release.gpg [191B]          
Ign [http://pr.archive.ubuntu.com](http://pr.archive.ubuntu.com) gutsy-backports/main Translation-en_US
Get:2 [http://archive.canonical.com](http://archive.canonical.com) gutsy Release.gpg [191B]
Ign [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Translation-en_US
Ign [http://pr.archive.ubuntu.com](http://pr.archive.ubuntu.com) gutsy-backports/restricted Translation-en_US
Ign [http://pr.archive.ubuntu.com](http://pr.archive.ubuntu.com) gutsy-backports/universe Translation-en_US
Ign [http://pr.archive.ubuntu.com](http://pr.archive.ubuntu.com) gutsy-backports/multiverse Translation-en_US
Get:3 [http://pr.archive.ubuntu.com](http://pr.archive.ubuntu.com) gutsy-backports Release [37.0kB]
Get:4 [http://archive.canonical.com](http://archive.canonical.com) gutsy Release [6998B]
Ign [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Packages 
Ign [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Sources
Get:5 [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Packages [676B]
Get:6 [http://pr.archive.ubuntu.com](http://pr.archive.ubuntu.com) gutsy-backports/main Packages [3648B]
Get:7 [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Sources [355B]     
Get:8 [http://pr.archive.ubuntu.com](http://pr.archive.ubuntu.com) gutsy-backports/restricted Packages [14B]
Get:9 [http://pr.archive.ubuntu.com](http://pr.archive.ubuntu.com) gutsy-backports/universe Packages [2463B]
Get:10 [http://pr.archive.ubuntu.com](http://pr.archive.ubuntu.com) gutsy-backports/multiverse Packages [14B]
Get:11 [http://pr.archive.ubuntu.com](http://pr.archive.ubuntu.com) gutsy-backports/main Sources [1792B]
Get:12 [http://pr.archive.ubuntu.com](http://pr.archive.ubuntu.com) gutsy-backports/restricted Sources [14B]
Get:13 [http://pr.archive.ubuntu.com](http://pr.archive.ubuntu.com) gutsy-backports/universe Sources [2253B]
Get:14 [http://pr.archive.ubuntu.com](http://pr.archive.ubuntu.com) gutsy-backports/multiverse Sources [14B]
Fetched 55.7kB in 2s (25.3kB/s)
Reading package lists... Done


and then I tried to get the install manager:

>  sudo apt-get install startupmanager 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package startupmanager


Help

---

### Post by dummyhead3 on 2007-11-10
Are you sure that you actually installed ubuntu? take the Live CD out of the drive to make sure

---

### Post by Paul820 on 2007-11-10
You source file should be exactly the same as this, i see that from the output you never commented out reading from the cd rom, anyway, this is how your sources.list file should look:
```
#deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

# Line commented out by installer because it failed to verify:
deb http://pr.archive.ubuntu.com/ubuntu/ gutsy main restricted
# Line commented out by installer because it failed to verify:
deb-src http://pr.archive.ubuntu.com/ubuntu/ gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
deb http://pr.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted
# Line commented out by installer because it failed to verify:
deb-src http://pr.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# Line commented out by installer because it failed to verify:
deb http://pr.archive.ubuntu.com/ubuntu/ gutsy universe
# Line commented out by installer because it failed to verify:
deb-src http://pr.archive.ubuntu.com/ubuntu/ gutsy universe
# Line commented out by installer because it failed to verify:
deb http://pr.archive.ubuntu.com/ubuntu/ gutsy-updates universe
# Line commented out by installer because it failed to verify:
deb-src http://pr.archive.ubuntu.com/ubuntu/ gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# Line commented out by installer because it failed to verify:
deb http://pr.archive.ubuntu.com/ubuntu/ gutsy multiverse
# Line commented out by installer because it failed to verify:
deb-src http://pr.archive.ubuntu.com/ubuntu/ gutsy multiverse
# Line commented out by installer because it failed to verify:
deb http://pr.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse
# Line commented out by installer because it failed to verify:
deb-src http://pr.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://pr.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
deb-src http://pr.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://archive.canonical.com/ubuntu gutsy partner
deb-src http://archive.canonical.com/ubuntu gutsy partner

# Line commented out by installer because it failed to verify:
deb http://security.ubuntu.com/ubuntu gutsy-security main restricted
# Line commented out by installer because it failed to verify:
deb-src http://security.ubuntu.com/ubuntu gutsy-security main restricted
# Line commented out by installer because it failed to verify:
deb http://security.ubuntu.com/ubuntu gutsy-security universe
# Line commented out by installer because it failed to verify:
deb-src http://security.ubuntu.com/ubuntu gutsy-security universe
# Line commented out by installer because it failed to verify:
deb http://security.ubuntu.com/ubuntu gutsy-security multiverse
# Line commented out by installer because it failed to verify:
deb-src http://security.ubuntu.com/ubuntu gutsy-security multiverse
```

---

### Post by boriquajake on 2007-11-10
> **dummyhead3 said:**
> Are you sure that you actually installed ubuntu? take the Live CD out of the drive to make sure

Dude, not a bad guess. From what Paul said the system was a little bit confused about that, but when I went and removed the #s from the source list where he told me to the update actually worked. When I then tried to get the startupmanager that worked too. Now, my question is, where do I go from here to resolve the slow booting problem?

---

### Post by Paul820 on 2007-11-10
Do you have the startupmanager in System->Administration->Startup-Manager ?

---

### Post by boriquajake on 2007-11-10
OK, I found the startupmanager and I made the requisite change to the screen resolution. I am going to reboot and see how long it takes. Wish me luck.

---

### Post by boriquajake on 2007-11-10
Holy cow, that solved the problem. I don't know how to thank you all. Now if only I could get the fonts in gmail to look somewhat legible, but that is a job for a different thread. I will go search for the answer to that one.

Thanks again.

---

### Post by Paul820 on 2007-11-10
Yay, i love a happy ending :cry: :lolflag: It would have been a lot quicker if gutsy never commented out all your sources. Anyway, glad you got it sorted out. :)

---

### Post by Tyke91 on 2007-11-10
please mark this thread as solved so that future people can get help from it :)

---

### Post by Bosphorus on 2007-11-10
Thanks, Paul. This tip did the trick! Fixing the startup resolution worked.

---

