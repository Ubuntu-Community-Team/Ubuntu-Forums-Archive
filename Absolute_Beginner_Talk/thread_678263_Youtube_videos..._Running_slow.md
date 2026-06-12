---
title: "Youtube videos... Running slow ?"
date: 2008-01-25
forum: Absolute Beginner Talk
---

### Post by Bluestick on 2008-01-25
Hey guys i noticed my you tube videos are running extremely slow and if i FULL SCREEN them.. its frame by frame making it impossible to watch....
  It was running good when i had "win vista" 
anybody have any idea why?

---

### Post by Bluestick on 2008-01-25
Could this be because my "Restricted Drivers" are not Enabled ?

---

### Post by kplaxmaster on 2008-01-25
Are you using Adobe Flash (non-free) or Gnash to view flash?

Also, what computer architecture are you using?  I am assuming you are using Firefox as well?  Please provide more information.

I ask about the architecture because the 64-bit flash-plugin from Ubuntu's repository doesn't work yet.  It has been fixed already, but didn't make it to the current repository's.  So if you *do* have an x64 version of Ubuntu, then you won't be able to install the flash-plugin via apt-get but rather must compile it yourself or wait for 8.04 release.  See [http://ubuntuforums.org/showthread.php?t=636397](http://ubuntuforums.org/showthread.php?t=636397) if this is the case.

Hope this helps, and if your not x64 please provide more details.  I am also assuming your internet connection is the same as it was when Vista was running the flash movies just fine?

---

### Post by Bluestick on 2008-01-25
Ok im running... Ubuntu 7.10 32bit  AMD 3400++ 200gig HD 1.5 gig of ram ATI X850 PRO and Comcast is my connection. and firefox
  And i think im just running Adobe Flash!

---

### Post by Bluestick on 2008-01-25
anyone having this problem on the 32 bit 7.10.. running youtube videos really slow, with a similar system as mine i posted above?

---

### Post by kplaxmaster on 2008-01-25
There shouldn't be any issue with 7.10 32-bit.  Firefox is one of the leading web-browsers in terms of plugins such as flash (adobe even creates linux firefox plugins).

Is your video card correctly setup under Ubuntu??

---

### Post by JonUK76 on 2008-01-25
Adobe Flash Player would not install for me automatically through package manager. It would appear to, but would always fail due to the file being corrupt.

I had to download the tar.gz file from the Adobe website to get it work.

And yep, video performance for me was very poor with the default drivers for an Nvidia 7600GT. The restricted driver made a big difference.

---

### Post by Bluestick on 2008-01-25
> **kplaxmaster said:**
> There shouldn't be any issue with 7.10 32-bit.  Firefox is one of the leading web-browsers in terms of plugins such as flash (adobe even creates linux firefox plugins).

Is your video card correctly setup under Ubuntu??
My video card sux with ubuntu no drivers are out there for it... so no its not installed corectly.. i dont have my restricted driver enabled... if i do that it messes everything up..
  Maybe i should go out and purchase a new "video card' something like 7900 gt stock OC my bro has that one on vista it does wonders!!!!

---

### Post by TheForkOfJustice on 2008-01-26
I'm getting choppy playback on YouTube and on SWF files on my hard drive.

It's not a vid card problem as far as I can tell since the last version of Flash worked flawlessly.  I'm guessing it is a problem with Flash itself.

Anyone else got a theory?

---

### Post by NapsterX on 2008-01-26
i use to have that problem on my laptop but then i just went to adobe's website and re downloaded the packages i needed and it fixed all my problem

---

### Post by sports fan Matt on 2008-01-26
Id second that theory and as we know, Adobe with Linux doesnt fix overnight, which is a shame.  Best bet id say is to hope for a fix in the next release

---

### Post by daviduff on 2008-02-15
I Have the same problem. Really slow youtube video or pages.  Do you really think Restricted drivers could help me? (if i could get them to work!)

---

### Post by thetechguyz on 2008-02-24
SAME HERE!
I had a problem with Youtube videos and I tried uninstalling and reinstalling adobe from the package manager. Still the same result if not worst. I got the original from the adobe website in the form of a tar.gz, extracted it and ran the install file. After installation it ran perfectly fine. But I mean... You can wait for the next release like what the guy up there said... Or you can read and fix the problem in few seconds. lol... And I am a beginner Linux user... Well, I was until I tested every top ten distro from distrowatch.com LOL... I love how much linux has evolved over the years... it makes me happy!

---

### Post by vertozia on 2008-03-24
yeahhh, they do run superslow, im going to try opera and see how flash works with opera on linux...redtube is also slow :)

---

### Post by Tekovro on 2008-05-07
I had the same problem. when i first installed ubuntu and upon opening firefox and a webpage with a flash video you get a few options as to which flash player you want to install for the video.. i made the mistake of picking one of the others rather than adobe-nonfree.. i installed it later but it didn't help so i went to synaptic package manager and typed in flash and uninstalled all the flash plugins installed and then reinstall adobe-nonfree flash.. Now youtube is running smooth as butter.

hope it works for you too.

---

