---
title: "SkypeMate or kb2kskype"
date: 2007-11-30
forum: Absolute Beginner Talk
---

### Post by anewguy on 2007-11-30
Has anyone had any luck yet with SkypeMate for Linux or with kb2kskype?

I have tried to run SkypeMate for Linux, but it says something about a library missing.

I have tried kb2kskype, and it sort of works.  The problem I have with it is with audio - it's choppy and you end up not being able to understand 75% of it.  I have an OLD P4/500 box with only 256mb of memory running Gutsy - could memory problems cause this, or is it more likely the CPU can't keep up?

Any help in getting this working would be GREATLY appreciated!  I have a subscription to SkypeOut and I need it to call my parents in Arizona and my sisters, all of whom live a LONG way away from me.  I'm on disability, so I can't afford regular long distance phone calls.

BTW - I'm on dsl.

Thanks!:)

---

### Post by wieman01 on 2007-11-30
> I have tried to run SkypeMate for Linux, but it says something about a library missing.
What is the actual error message? Could you post it?

---

### Post by anewguy on 2007-12-01
This same problem has been referenced in the past, and so far I have seen no solution.  Here is the error:


dave@dave-desktop:~/Desktop$ ./SkypeMate
./SkypeMate: error while loading shared libraries: libdbus-1.so.0: cannot open shared object file: No such file or directory
dave@dave-desktop:~/Desktop$


That library is not listed in synaptic, and I tried an apt-get install and it didn't find it either.

Is there any chance someone has the source for this thing so we can try to get it to work in Ubuntu?  It appears it's only for Fedora Core 3.

I also tried another suggestion tonight and removed my installed Skype and downloaded an older version and installed it, because it had been suggested that kb2kskype did not get along with an automatic setting of some sort in Skype.  It installed fine, but when I try to test call it starts the call, which I hear, then it stops the test call saying there is a problem with the audio input.  I can't figure that out, as it is showing the correct devices in Skype.

I also tried install the X11 bus communications package, as it wasn't installed in my Gutsy version of Ubuntu.  Still made no difference.

I really need to find some way to make this work!   Any and all suggestions are appreciated!

Thanks in advance!:)

---

### Post by anewguy on 2007-12-02
bump.

---

### Post by anewguy on 2007-12-02
Well, I went through a bunch of stuff (I could make it sound cool but the truth is I don't exactly know why I needed to do everything to begin with!:) ).  I downloaded the source for kb2kskype and after the above "stuff" I eventually got it to compile and install.  Did the same for the usbb2k-api stuff.

End result:  still the same - the audio is all broken up.  I have printed off the source, since I've recently been exposed to some libusb programming, to see if anything obvious stands out.  that will take a while.

In the mean time, no luck at all with SkypeMate for Linux.

Has anyone ever gotten any of this to run on anything other than Fedora?  In other words, has anyone gotten this to run in Ubuntu?  Which version?  What are your cpu and memory specs?  Any ideas to help me?

I can't believe that we can just be left out in the dark on this, but at the same time if you look at the downloads of the kb2kskype stuff it only numbers a few hundred in total - no wonder the vendor or Skype itself doesn't want to put the time into it.

If anyone has ANY ideas, ANY help at all, PLEASE let me know!

---

### Post by simon_6162 on 2007-12-04
Skypemate doesn't work anymore unless you want to downgrade to skype 1.3.53 and dbus 0.33. (which will probably break gnome !)

Re kb2kskype: have you turned off the auto gain setting in skype 
 Options -> sound devices -> untick allow skype to control my audio settings. 

This app does work in ubuntu, have a look at this thread.
[http://sourceforge.net/forum/forum.php?thread_id=1742913&forum_id=653443](http://sourceforge.net/forum/forum.php?thread_id=1742913&forum_id=653443)

---

### Post by anewguy on 2007-12-05
I already have the alsa stuff set up as mentioned in the link.  I am able to communicate with the box - that's not a problem.  The problem is that the sound is all cut up and not understandable.

I've done some experimenting and can report the following:

If I start up usbb2k_api, then go to another window and do the api_connect thing as mentioned in the readme for testing, but do no start kb2kskype, I can then make a Skype test call and at least understand the audio.  Of course, it isn't as clean and I have no control over the box.

Starting up kb2kskype causes the garbled audio again.

I'm still wondering if my CPU and memory are enough for this to be able to run.  I've tried running the system monitor when it is running, and memory would appear okay, but the cpu is max'd out.  From years of prior experience on a lot bigger box, I know that system monitors eat cpu, and I don't know if that is the case now or if indeed my CPU can't handle the load.

Keeping in mind that kb2kskype is all software, it would appear the telbox, etc., is working - I just can't get valid audio.

---

### Post by simon_6162 on 2007-12-05
If you hover over the pop up window in skype that represents your call you get the call stats and cpu usage. 
I just tried Skype 2.0 today on fedora (don't ask why I was on a ubuntu foum !) I get around 50% jitter to echo123 and the audio issue you take about, if i drop back to 1.4 it works perfect. This is also the case for my on board sound card. 

I went back to 2.0 unplugged my webcam and disabled video restarted and I get no jitter.

Could you try using your onboard sound card in your current setup, but with kb2kskype running and then without, and report and change.
Ten unplug your webcam (if you have one) disable video and restart Skype.
if that doesn't work try Skype 1.4

Simon

---

### Post by simon_6162 on 2007-12-05
I meant send Packet loss at 50% sorry.

---

### Post by anewguy on 2007-12-06
Already on Skype 1.4 (it's the only one I could find available from Skype for Linux).

---

### Post by simon_6162 on 2007-12-10
So what happens when you hover over the pop up window in skype that represents your call you get the call stats and cpu usage.

post the stats for a call to echo123

---

### Post by xtrm_redbull on 2007-12-10
You may want to try [skype 2.0]("http://www.skype.com/download/skype/linux/beta/") but its still beta version. You could also search the forums if you experience problems with skype. Good luck:)

---

### Post by quinnten83 on 2007-12-10
I hear good things about skype 2.0 Beta for linux, 
perhaps you can try with that.
Are those other programs frontends for skype or are they clones?

---

### Post by anewguy on 2007-12-13
Okay, here's the status on this:

My cpu usage shows at 100% with kb2kskype running.  So I do this instead and I can at least use the phone and Skype:

via sudo, start usbb2k_api from a terminal window

in a different terminal window, I connect to the api as it shows in the read me for testing:

api_connect /tmp/usbb2k.sock

when the terminal finishes dumping out the initial stuff about the phone I do this:

press Enter once to get to the SEND> prompt

at the SEND> prompt, enter SWITCH USB/PSTN

This switches the box to usb.  Then I fire up Skype and use it to dial out.  I never load kb2kskype.  The audio on my end is noisy, but everyone says the call is loud and clear.  Have done this several times using my regular cordless phone with the base connected to the USB Telbox.  Hasn't disconnect me yet.

This work around obviously results in a loss of some of the functions with the box, but at least I can call out.

I'm going to mark this as closed for now.  For those interested, a PIII-500 Dell XPS system with only 256 meg of memory just isn't enough to run the entire thing cleanly in Ubuntu.  Heck, I'm kind of surprised I can run Ubuntu Gutsy on it.

---

### Post by anewguy on 2007-12-13
> **quinnten83 said:**
> I hear good things about skype 2.0 Beta for linux, 
perhaps you can try with that.
Are those other programs frontends for skype or are they clones?

I have a USB box between my regular cordless phone and my computer.  By default, the box is set to "PSTN".  I have a phone line hooked into the box, so by default my cordless phone works normally through a normal phone line.  The box allows you to switch to USB, so I can use the same phone to talk via Skype.  The box has driver software that only runs in Windows.  To get all the functionality, you need the 2 programs besides Skype in Linux.  This functionality includes getting a ring while you are on Skype letting you know someone is calling on your regular phone line, placing the Skype call on hold, and then answering the regular phone line call, going back to Skype when done.  The 2 parts to this are usbb2k which is the actual interface in Linux to the box, and kb2kskype, which is the software that provides all the functionality in Linux,  Unfortunately, my box doesn't have enough power to run all that and maintain stable audio.  It's a PIII-500 with only 256 meg of memory.  The processor is so pegged with kb2kskype running that nothing can run smooth, so the audio is all garbled up instead of being clear.  My previous post relates as to how I can at least use the phone for Skype and regular calls but without all the extra functionality the box provides that I would like to use.  Until the day comes that I can afford a different computer, I'm pretty much stuck with what I can do.

Hope that explains things to you a little clearer.  All 3 - usbb2k, kb2kskype, and Skype are needed in Linux for all the functionality I want.  I don't want a "dedicated" Skype phone - I want to be able to use by regular cordless phone for both Skype and regular calls.  The box allows me to do that.

---

### Post by anewguy on 2007-12-14
> **simon_6162 said:**
> So what happens when you hover over the pop up window in skype that represents your call you get the call stats and cpu usage.

post the stats for a call to echo123

Sorry I forgot to tell you about that.  Using Ubuntu 7.10, usbb2k and kb2kskype with Skype 1.4, nothing shows if you hover over the call box when a call is in progress, so I obviously can't give %'s.  Running system monitor shows the cpu pegged.  When I do the steps I just mentioned (ie, not using kb2kskype) the cpu is still pegged but at least the audio works ok.:)

Outside of waiting until some time when I can get a different computer, I'm not sure there is much else I can do for now.

Thanks for the help and suggestions!!:):)

---

### Post by anewguy on 2007-12-16
> **xtrm_redbull said:**
> You may want to try [skype 2.0]("http://www.skype.com/download/skype/linux/beta/") but its still beta version. You could also search the forums if you experience problems with skype. Good luck:)

One problem - Skype 2.0 requires a minimum of a 1 gig processor.  As already noted, I only have a PIII-500.

---

### Post by simon_6162 on 2008-01-09
Do you want to give this version a try, its a bit more CPU friendly. 
[http://kb2kskype.sourceforge.net/downloads/kb2kskype-0.3.6-alpha5.tar.bz2](http://kb2kskype.sourceforge.net/downloads/kb2kskype-0.3.6-alpha5.tar.bz2)

To get stats from skype go to options -> advanced and tick display technical stats. the restart skype.

---

### Post by altariel on 2008-03-30
and new packages downloadable for both (k)ubuntu 6.10 and (k)ubuntu 7.10 :)
[http://sourceforge.net/project/showfiles.php?group_id=186708](http://sourceforge.net/project/showfiles.php?group_id=186708)

---

