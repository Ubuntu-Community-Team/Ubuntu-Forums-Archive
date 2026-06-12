---
title: "Lost sound - please help..."
date: 2008-03-26
forum: Absolute Beginner Talk
---

### Post by Jay Car on 2008-03-26
Hello,

My computer came with Ubuntu 7.10 pre-installed.  I've had it for a little over 2 months now and it has worked beautifully, sound and all. It's my work machine and I really like it.  

Yesterday it lost its sound. Because I am still moving, converting and organizing files from my old hard drives, and learning how to do my work using new programs, I haven't had much time to actually learn about the computer itself, so I'm still pretty clueless about the hardware and system. I spent last evening gathering up as much of the hardware info that I could find because I was not sure what I might need to post here in order to get help. 

From what I've read on some forum posts by others with the same sound card, it doesn't look very hopeful that (at my skill level) I can get it working again.  But, I'm very willing to give it a good effort, if someone's willing to coach me through it.  

I do not know what made the sound stop working.  The last change that I know of was an update that I okayed to download yesterday morning.  (I don't suppose there's any way to just set the system back to where it was before the sound stopped working? -  Just kidding :)

It was actually later in the day when I noticed there was no sound though, so the update may have had nothing to do with it.  I thought it was only that the volume was turned down or muted, but when I tried to open the volume control, I got this error: "No volume control GStreamer plugins and/or devices found."  I did a restart to see if that would help, but it didn't.  I don't even get the drums at start up now or any other system sounds.  

This is my sound card: 
Onboard Realtek ALC883, 8 Channels
(described in hardware list as: nVidia Corp MCP61 High Definition Audio)

Any help would be very, very appreciated.
Thanks, JC

---

### Post by Jay Car on 2008-03-27
Well now I'm worried that my computer's "lost sound" problem isn't solvable, and no one has the heart to tell me...

Should I post more information about my system? 
I wish I were better at asking questions...
But maybe all I need is some patience, I know there are others with more pressing problems that need help first.

So I'll check back tomorrow.
JC

.

---

### Post by JAPrufrock on 2008-03-27
Try[ this link.]("http://ubuntuforums.org/showthread.php?t=205449")

---

### Post by spiderbatdad on 2008-03-27
No volume control Gstreamer plugins or devices found...is not a good message.
But should be fixable. Could you post the results of these commands:
```
uname -r
asoundconf list
```

---

### Post by Samurai Penguin on 2008-03-27
just passing thru ...

---

### Post by Jay Car on 2008-03-27
To spiderbatdad,

Here is the result for:

uname -r
2.6.22-14-server

There was no result returned for "asoundconf list"

...................................
To JAPrufrock
Thank you for the link to the "Sound Problem Solutions Guide". I had followed that link late last night (found it in another forum post) and did try following the steps outlined there.

Here are the results from two of the commands from that guide: (I've only posted the "Audio device" result here, rather than the entire system hardware list, but I can post all of it if needed)

aplay -l
aplay: device_list:204: no soundcards found...

lspci -v
00:05.0 Audio device: nVidia Corporation MCP61 High Definition Audio (rev a2)

        Subsystem: Giga-byte Technology Unknown device a002

        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 10

        Memory at ee000000 (32-bit, non-prefetchable) [size=16K]

        Capabilities: <access denied>

When I reached the part in that guide that instructs using the command "sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils" I ran into a problem. After pasting that command into the terminal it asked for my password but it would not allow a password to actually be typed in. 

So I went back to the guide to read further...when I reached the part in the guide outlining ALSA driver Compilation (and reading the ALSA Project pages) I felt it was a bit beyond my skills and decided to go ahead and post here...because I probably need supervision on this one.

And thank you both for helping, it's very appreciated!

JC

---

### Post by JAPrufrock on 2008-03-27
Try executing this in terminal/bash:
> discover sound

also, I found this. Don't know if it will help:

I've been trying to get this sound card working for a while now under feisty. I finally have and decided to share how my solution.
The first thing is the card is not actually what it appears to be from lspci. From lspci I get:
"Audio device: nVidia Corporation MCP61 High Definition Audio (rev a2)"
Looking at my motherboard book (motherboard is NF61S) shows that the card is actually a RealTek ALC861. To make this card work, add the following to /etc/modprobe.d/alsa-base
options snd-hda-intel model=3stack

I got this from a bug report. I don't have the URL anymore. Anyway, hope that helps some people get their sound working. Just remember to look closer at what your card actually is and don't waste time on the generic bus name given from lspci.

---

### Post by markjensen on 2008-03-27
You said that sound worked at one time?   And now it doesn't?

If you boot your Ubuntu CD into a LiveCD session, do you get sound again?

---

### Post by Jay Car on 2008-03-27
To JAPrufrock,

When I typed the "discover sound" command into the terminal (without any quotes), it gave no return at all.  You are correct that my sound card is actually a ReakTek ALC861, built into the motherboard. I followed the instructions and pasted "/etc/modprobe.d/alsa-base
options snd-hda-intel model=3stack" into the terminal, but there was no result from it.

Although this particular computer is new and I'm still getting used to it, I've installed Ubuntu or Mandriva on other computers (my friends have been kind enough to let me experiment on their ailing Windows machines :) ), however, I haven't had to use the terminal much at all.  So I'm wondering if, when I get no results from pasting commands into the terminal (and hit "Enter"), could it be because I am not doing it correctly, or leaving something out? 
...................

To MarkJensen

Yes, the sound has worked beautifully on this machine since I've had it (about two months now).  I will try a Live CD and see if the sound works.  Great idea! (why didn't I think of that?)
Will let you know what happens.

Thank you (to both of you!)
JC

---

### Post by zanjabeel5 on 2008-03-27
Hi

this command should give your alsa version:

> cat /proc/asound/version

In the past I had to manually install newer versions of the driver, until ubuntu itself moved to using newer versions. I would recommend trying to install new drivers too.
(maybe you pre installed system had them and update overwritten them)

installing the driver is a matter of copy/paste some commands 
I followed this guide:

[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

---

### Post by JAPrufrock on 2008-03-27
> When I typed the "discover sound" command into the terminal (without any quotes), it gave no return at all. You are correct that my sound card is actually a ReakTek ALC861, built into the motherboard. I followed the instructions and pasted "/etc/modprobe.d/alsa-base
options snd-hda-intel model=3stack" into the terminal, but there was no result from it.

It's not a terminal command. You have to modify the file alsa-base, using a text editor like gedit.  Try this:
open the file alsa-base with this command at the terminal
> sudo gedit /etc/modprobe.d/alsa-base
Now make a backup file by saving the file as alsa-base.bak, or some name you like.
Now scrole down close to the bottom of the file and you'll see lines beginning with the word "options".
Add the following line at the end, or anywhere you want among the option lines:
> options snd-hda-intel model=3stack
Now save the file as alsa-base (File/Save As/ alsa-base).
_Hopefully_, your sound card will now work.

---

### Post by Jay Car on 2008-03-28
To MarkJensen,

I apologise for being so slow, it was a busy work day and then had a family emergency this evening.  However, I just now booted up using the Live CD and the system sounds played, and I played a music file.  When I clicked on the music file, after the player opened, I was given the option to look for needed codecs.  I let it do the search and it brought up gstreamers extra plugins, and I let them be installed, after which the music file (MP3) played just fine.  

When I restarted the computer without the Live CD, the sound no longer worked.  However, it seems hopeful that it DID work for the Live CD.  Maybe it's fixable? :)
...............................

To zanjabeel5, I pasted the "cat /proc/asound/version" command you suggested, and it returned "No such file or directory".

What should I try next?
(Thank you for helping!)
JC

---

### Post by Jay Car on 2008-03-28
To JAPrufrock

I missed seeing your post earlier (I think I'm just tired) Thank you for the explanations, I copied all of it and will follow the directions. I'll report back with the results.
Thanks again, JC

---

### Post by Jay Car on 2008-03-28
Hi JAPrufrock, 

This is what I pasted into the terminal: sudo gedit /etc/modprobe.d/alsa-base

This is what returned: 
[sudo] password for jay:

I then typed my password, but the cursor did not move, it simply would not let me type anything at all. So I just hit "Enter" to see what would happen, and this is what it returned:

Sorry, try again.
[sudo] password for jay:
And once again it would not accept anything I typed. 

Is this some sort of protection to keep users from inadvertently doing damage to system files?  Is there a way to get past this? 

Thanks for all your help,
JC

---

### Post by markjensen on 2008-03-28
When you type in a password on the commandline, normally it doesn't echo anything back.

There may be a way to change that, but the default is certainly no echo.

---

### Post by Jay Car on 2008-03-28
> "When you type in a password on the commandline, normally it doesn't echo anything back. There may be a way to change that, but the default is certainly no echo."


To markjensen, I think what threw me was that the cursor didn't move at all, so I assumed it wasn't working...which made me keep trying, which obviously ruined the password. 

After reading your post I just typed the password **once** and hit Enter. Of course it worked fine that time. Thank you for helping me to figure that out.


> Quote:
sudo gedit /etc/modprobe.d/alsa-base
Now make a backup file by saving the file as alsa-base.bak, or some name you like.
Now scrole down close to the bottom of the file and you'll see lines beginning with the word "options".
Add the following line at the end, or anywhere you want among the option lines:
> Quote:
options snd-hda-intel model=3stack
Now save the file as alsa-base (File/Save As/ alsa-base).
Hopefully, your sound card will now work.

To JAPrufrock,

I was able to follow the steps you outlined. I created a backup, then added the"options snd-hda-intel model=3stack" line to the options list and saved it as alsa-base. I even double checked to make sure the file did save with that line in it.  I then tried to play a sound file.  The sound file didn't play, a message opened saying "Unable to activate plugin media player keys."  Trying to access the volume control gave me the "No volume control GStreamer plugins and/or devices found" message again.  

I then restarted the computer, but still no sound after starting up.  

The **GOOD** side of this is that I learned a little bit about using the terminal, which was great.   

I've been wracking my brain to think back on what I might have done to skunk the sound. It doesn't make sense that it would just stop working for no reason.  

Since the sound plays fine when booting the system using a Live CD, then it can't be a hardware problem, right? 

Question: Is there any way to get a history of any changes I've made to settings (or installing codecs, plugins or software since I got the computer? 

Or is possible to just remove the sound driver and reinstall it? 

Thanks for all the patience and help (and especially for not laughing at me about the password thing. :) )

JC

---

### Post by markjensen on 2008-03-28
I've never had sound problems like this, but it is almost surely a config issue.

I suppose you could fire up synaptic and do a complete removal of alsa, which will also remove config files.  Then re-add it (and it would re-create a default config).   That might work, but I have never done such a thing before...

As for the password thing, that happens more frequently than you might think.  Don't sweat it. ;)

---

### Post by JAPrufrock on 2008-03-28
Yeah, seems like a config problem, which may have occurred after an update, since the live CD works.  The good thing is that the kernel contains the alsa driver for your card, so you don't have to install a driver.  As already suggested, you could try to uninstall and then reinstall alsa.  Or, maybe you could copy the alsa-base file from your live CD bootup to your hard drive.  First, if you want, you can check and see if the file, alsa-base, on your live CD is the same as the one on your hard drive.  They are both located at /etc/modprobe.d/.  Check and compare both, line for line.  If they're exactly the same, the alsa-base file is not the problem (alsa-base is the primary config file).  If the 2 files are different, you could copy the alsa-base file from the live CD to your hard drive.  You would have to boot up your live CD and copy the alsa-base file to a memory stick.  Then copy the file from your memory stick to your hard drive, overwriting /etc/modprobe.d/alsa-base.  Or change the line/lines manually using gedit, like you did before. You will still have your original alsa-base file as alsa-base.bak, so you won't lose it.  Hopefully one of the two methods above will solve the problem (re-install alsa or change the alsa-base file). 

One quick question:  I presume that you get absolutely no sound when you boot up normally, not even the Ubuntu theme.

Also, don't forget to check alsamixer again, to make sure that the sound is turned on.

---

### Post by Jay Car on 2008-03-28
Hi,

I think I'll try the suggestion of comparing the alsa-base file from the live CD to the one on my system, first, and go from there.  I'll do it after work today so I won't have so many distractions.  The things you've both suggested make sense to me, and I'll bet we're on the right track.  I'll let you know how it goes. 

(JAPrufrock, you're correct that the system sounds are also not working.)

Thanks so much for the help!
JC

---

### Post by Jay Car on 2008-03-29
Hi All,

Just checking back to report that the two alsa-base files (one from my installed system and the one from the Live Ubuntu CD) were identical in every way. I had a friend sit down and compare both of them too, just to make sure I hadn't missed something. They match, so it's likely not the problem, right?

I've made sure all my files and folders are moved out of harm's way, and I am going to try the next step, which will be a complete removal of the alsa files, and replace them fresh. 

If that doesn't work I'm prepared to just reinstall the system in the morning. I didn't originally install the system on this computer, but I've installed a few other Ubuntu and Mandriva systems and it generally doesn't take very long, and might be faster than trying to figure this sound problem out. I feel like I am taking up too much of your time here.

**Question:**  I found a website that outlines a script that restores system settings after an OS reinstall. Here is the link:
[http://www.linux.com/feature/62438](http://www.linux.com/feature/62438)

I would like to try using the information there (once I get things working again), but thought I'd ask you first if it looks safe.  I'm not experienced enough to be a good judge, But the idea of being able to put my settings back seems like a time-saver to me...though I certainly don't expect to be reinstalling my system all that often in the future, it never hurts to have a plan, just in case. Right?  

I'll check back and let you know if removing and replacing the alsa files brings back my sound.  

Thanks for the help and guidance,
JC

---

### Post by Jay Car on 2008-03-29
> I suppose you could fire up synaptic and do a complete removal of alsa, which will also remove config files. Then re-add it (and it would re-create a default config). That might work, but I have never done such a thing before...

Well, I've had quite the adventurous morning. I did try removing alsa using the package manager. I only removed "alsa" related options that didn't have the Ubuntu logo next to them.  I figured those with the logo would have been part of the original installation, and since my sound worked previously, I assumed they weren't the problem. Plus, I didn't want to do too much at once so I'd have a better idea of what worked (if anything it did).

Because gstreamer was mentioned in the errors when I tried to access the volume controls, I uninstalled those files too.  I periodically tried to play sound, and did restarts after each change to see if the sound worked, but no luck. 

I finally uninstalled even the alsa files with the Ubuntu logo next to them.  Then started over and reinstalled everything, and once again did a little at a time, starting with the files that had Ubuntu logos.  

Anyway, in the end I never was able to get the sound back. So I just went ahead and reinstalled Ubuntu.  It didn't take very long to do, and everything is back to normal now, sound and all. I am VERY happy for that, though I wish I could have figured out what caused the problem to begin with (so I wouldn't repeat it). 

The only part I haven't quite figured out yet is how to get my old Firefox profile and prefs back. I tried just copying and pasting the old folders into the new FF folder, but only got a message that I didn't own that folder and had no permission to write to it. So, I'm off to visit The Great Google to see how to do that. 

Other than that, all's well again.
I thank you for your help, and for being so patient. This is such a nice forum and all of you that help here deserve applause and appreciation. 
JC

---

### Post by JAPrufrock on 2008-03-29
Oh well, hopefully reinstalling alsa will work.  I'm not so sure if the OS reinstall script you linked to is all that advantageous.  If you've altered your xorg.config file or sources.list you can just copy them to a memory stick and then recopy them to their proper directories after the  re-install. Actually,  I think it might be easier to just reconfigure your hardware, if necessary, after the install.  And of course you should back up your files before you re-install.

Whoops, you posted again before I answered.

---

### Post by Jay Car on 2008-03-29
> I'm not so sure if the OS reinstall script you linked to is all that advantageous. If you've altered your xorg.config file or sources.list you can just copy them to a memory stick and then recopy them to their proper directories after the re-install. Actually, I think it might be easier to just reconfigure your hardware, if necessary, after the install. And of course you should back up your files before you re-install.


I think I'm just tired, it's been a very long day...but I'm feeling very frustrated this evening. I've read through so many posts about how to get previous Firefox profiles and prefs put into a new installation of Firefox, but they all seem to be about moving profiles from XP to Ubuntu, or other situations that are different from mine.  

I'm pretty consistent about backing things up, but it seems pointless if I can't get the files back where they belong...it's taken me longer today to manually redo all my Firefox settings and plugins and begin collecting my old bookmarks, than it did to reinstall the entire Ubuntu system.

I truly do understand why it's important **not** to make critical system files easily available to the user.  However, I'm feeling frustrated at finding it so hard to do something as simple as replace my old preferences in Firefox. 

Is there a way to add a password option to the right-click menu, so when I need to replace a simple profile I can type my password and get quick, but temporary, access?  

I thought using the terminal was fun and enjoyed learning more about it, but I don't know what to type in there to give myself privileges to just one particular folder.

And I just re-read all of this and realize it sounds a bit grumpy.  I don't mean it that way, honestly, I'm just tired and frustrated tonight.  I'll get it figured out tomorrow, I'm sure.  It's probably something very simple (like when I couldn't figure out the password earlier).

Anyway, take care, and many thanks for working through the sound problem with me. 
JC

---

### Post by spiderbatdad on 2008-03-29
if you want to graphically drag and drop or copy/paste system files use ```
gksu nautilus
```
This will open the nautilus file browser with root access.

If you want to edit basic system config file use```
gksu gedit /file/name
```

---

### Post by Jay Car on 2008-03-29
spiderbatdad, you are my hero!  It WORKED like a charm!!!! 

My Firefox is back! 
Thank you SO much!

My computer is playing music, my Firefox is back, and my dog is chewing on my toes...
What more could a person ask for?
:)

---

