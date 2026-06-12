---
title: "DVD Playback in 6.06"
date: 2006-07-30
forum: Absolute Beginner Talk
---

### Post by houseisland on 2006-07-30
I am relatively new to Linux -- I have used/toyed Red Hat and Suse severs and desktops, as well a number of other distros.  

I have lots of professional experience with Novell and MS.

I am setting up a PC with my 16-year-old daughter for her use, and we are using Ubuntu 6.06 (very nice desktop by the way).

For the most part all hurdles have been overcome.  We have found Windows-analogous applications that meet her needs and have installed and configured them.

The one major pain so far is DVD playback.  Neither Totem nor MPlayer work.  Totem generates error messages saying that the correct plugins are missing and ***most helpfully*** does not mention what the needed plugins are.  MPlayer seems not open the disk as whole.  And when one browses the the VOB files and asks the app to open them, it generates read errors.  :confused: 

The DVD drive is new and works perfectly in Windows.  The DVD media is good condition and works in Windows.

Any suggestions?

Thanks.

---

### Post by Perfect Storm on 2006-07-30
You might want to check this: [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)
(under Installing libdvdcss2)

By the way try out VLC it's great for multi-media (my personal opinion).

---

### Post by Frank Golden on 2006-07-30
> **houseisland said:**
> I am relatively new to Linux -- I have used/toyed Red Hat and Suse severs and desktops, as well a number of other distros.  

I have lots of professional experience with Novell and MS.

I am setting up a PC with my 16-year-old daughter for her use, and we are using Ubuntu 6.06 (very nice desktop by the way).

For the most part all hurdles have been overcome.  We have found Windows-analogous applications that meet her needs and have installed and configured them.

The one major pain so far is DVD playback.  Neither Totem nor MPlayer work.  Totem generates error messages saying that the correct plugins are missing and ***most helpfully*** does not mention what the needed plugins are.  MPlayer seems not open the disk as whole.  And when one browses the the VOB files and asks the app to open them, it generates read errors.  :confused: 

The DVD drive is new and works perfectly in Windows.  The DVD media is good condition and works in Windows.

Any suggestions?

Thanks.Make sure you have a DVD Region set for your new drive.
The drive that came with my notebook did not have a DVD region selected.
It worked in XP but not in Ubuntu even with all the restricted drivers
installed that Artificial inteligence refers you to here. Set it in XP
or do a search in Synaptic in ubuntu for regionset and install.
Set to you region (see this article for more info)

[http://www.hometheaterinfo.com/dvd3.htm](http://www.hometheaterinfo.com/dvd3.htm)

and enjoy. Apparently DVD drives are made for and assumed to be used 
with windows and as such are set to DVD region 0. This allows them
to be used with a wide range of M$ windows boxes which have
the needed commercial codecs installed. That is why no problems in XP.
Ubuntu don't play that way. You must choose a region. Remember, be careful
you only have 5 choices. You only need to choose a region once but if you
go to foreign country or use a DVD from a foreign country you must choose
the appropriate region. After the fifth one your choice is permanent.
BTW once you get set up try XINE as a player. You can get from Applications>
Add/Remove>Sound & Video. Make sure both Show unsupported applications a
Show commercial applications are checked. After install go to System>Preferences>Removable Drives and Media Preferences>multimedia tab. Under Video DVD Discs make sure Play Video DVD disks when inserted box is checked
and change the command to "xine dvd://" without the quotes. This will
cause DVD movies to autoplay in XINE. Don't know the exact command
for another player.

EDIT: Nevermind about the DVD region stuff the Ubuntu tutorial Artificial inteligence references covers it. I had the same problem you did early with
Ubuntu but I didn't read the whole tutorial, just the stuff about plugins
etc. I finally scrolled to bottom of page and Voila!
It had not occured to me that my drive was set to Region 0.

---

### Post by IrishGangsta on 2006-07-30
*Deleted*
[size=1]**This is not a dating portal* * -- Artificial Intelligence[/size]

---

### Post by Skia_42 on 2006-07-30
Try your luck with Gxine, I've found it to solve all off my problems. And when you are trying to play dvds, don't make the same mistakes I did. Do not start off trying to play copied dvds, it may not work and you'll end up going crazy.

---

### Post by cantormath on 2006-07-30
> **houseisland said:**
> I am relatively new to Linux -- I have used/toyed Red Hat and Suse severs and desktops, as well a number of other distros.  

I have lots of professional experience with Novell and MS.

I am setting up a PC with my 16-year-old daughter for her use, and we are using Ubuntu 6.06 (very nice desktop by the way).

For the most part all hurdles have been overcome.  We have found Windows-analogous applications that meet her needs and have installed and configured them.

The one major pain so far is DVD playback.  Neither Totem nor MPlayer work.  Totem generates error messages saying that the correct plugins are missing and ***most helpfully*** does not mention what the needed plugins are.  MPlayer seems not open the disk as whole.  And when one browses the the VOB files and asks the app to open them, it generates read errors.  :confused: 

The DVD drive is new and works perfectly in Windows.  The DVD media is good condition and works in Windows.

Any suggestions?
Thanks.


The easiest way I have found to getting all of the media set up is with automatix.
you install automatix.
run it.
and click on what you want to work or install.
It installs all of the codecs for video, the video players or whatever else you want to click on....here is the instructions

[http://ubuntuforums.org/showthread.php?t=190025](http://ubuntuforums.org/showthread.php?t=190025)

---

### Post by Blur-king on 2006-07-30
Have you look at the Mplayer setup . Start your and In the preferences tab of the mplayer , go to misc and check that yoour dvd drive is correctly stated it should be something like /dev/dvd. Had similar problem with my cdrom which was corrected once I put in the correct path.

---

### Post by houseisland on 2006-07-30
Thanks all.

:D 

Problems resolved.

Very nice tone to the forums here.  :cool:

---

### Post by Frank Golden on 2006-08-01
> **houseisland said:**
> Thanks all.

:D 

Problems resolved.

Very nice tone to the forums here.  :cool:
Mind sharing what fixed it?O:)

---

### Post by houseisland on 2006-08-02
> **Frank Golden said:**
> Mind sharing what fixed it?O:)

Sure.  No problem:

> **Artificial Intelligence said:**
> You might want to check this: [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)
 (under Installing libdvdcss2).

Following the advice in the link above got Totem, the default player, working.  

I havent had time to play with MPlayer again but I am reasonably certain that it will work now.  

Nor have I had time to look at VLC, the player which Artificial Intelligence recommended..

---

### Post by Frank Golden on 2006-08-02
> **houseisland said:**
> Sure.  No problem:



Following the advice in the link above got Totem, the default player, working.  

I havent had time to play with MPlayer again but I am reasonably certain that it will work now.  

Nor have I had time to look at VLC, the player which Artificial Intelligence recommended..

Glad it worked out. You didn't need to set a Region? I absolutely could not play commercial DVD movies until I chose a DVD Region. Was very frustrating. If I had read through the entire article about restricted codecs I could have spared my self some grief. Live and learn. 
Totem
produces jerky motion and poor picture quality on my machine.
That's why I use XINE. I have MPlayer, it works OK but I prefer
XINE for the better control it gives me. Whatever works for you
though.

---

