---
title: "No Mic"
date: 2007-01-17
forum: Absolute Beginner Talk
---

### Post by RichPicker on 2007-01-17
Hi, all. My first switch to linux, as of yesterday. I now have everything up and running EXCEPT the microphone. I'm using a Dell laptop, which has a headphone and microphone jack on the left side. None of the linux apps will recoginize the mic., Help please. Thanks. (Hmm. Also. the trackpad doesn't work quite the same.)
Richard

---

### Post by tommytom on 2007-01-17
Have you set the volume level for the mike input it's usually muted double click the speaker icon in the top left corner assuming you are using Gnome (Ubuntu) rather than Kde (Kubuntu) you can unmute there. If you are familiar with the command line then type in the terminal ```
alsamixer
``` and you get pretty much the same. Hope that helps

---

### Post by RichPicker on 2007-01-18
Thanks. Still no mic. When I type 'alsamixer' in the terminal I get a graphic that shows Master (at 29%), PCM (at 93%), Capture (at 100%), and Input So with the word "Mic" above it, but no graphic for the Mic.

In the upper left corner of that terminal screen it says:
Card: HDA Intel
Chip: SigmaTel STAC9200
View: [Playback] Capture All
Item: Master

When I access the controls by double-clicking the sound icon, and select HDA Intel (Alsa Mixer) it has slider controls for the Mic. But when I select SigmaTel STAC9200 (OSS Mixer) there is NO slider for a Mic - only ONE slider for the speaker.

I suspect I need to download something for the SigmaTel STAC9200 from the Synaptic Package Manger, but I'm not sure, and not sure which to download.

---

### Post by mikewhatever on 2007-01-18
After opening alsamixer from the terminal, try hitting Tab button once or twice. You'll see more controls appearing. See the screenshot of my alsamixer. I had to set intmic to capture for the external one to work. Doesn't really make sense, but fact. You can navigate with right/left arrows from one control to another, and to change it from capture to blank hit space.
I also have to mention that I reinstalled sound driver before getting to play with settings, but I am not sure it had to be done. Check out this thread [http://ubuntuforums.org/showthread.php?t=258878&page=2](http://ubuntuforums.org/showthread.php?t=258878&page=2)
to see how. Note that we seem to have slightly different sound cards too.

---

### Post by RichPicker on 2007-01-18
Thank you. I've been into alsamixer via the terminal, and mine looks just like yours. Confusing to me why the mic has no slider. It toggles between mic and line. 

I tested with "sound recorder" and with alsamixer set to "line" I hear a hum; with alsamixer set to "mic" I hear a hiss.

I tried to download and install (This mouse response is terrible.) the latest alsamixer drivers from their website, but as far as I can tell they are sitting in my temp folder. Other than "add/remove" and "synaptic package manager", I have no idea how to install them.

Sorry, but none of this is intuitive. Shouldn't there be a bug fix for the mic problem somewhere? An update? There are numerous people with the same problem. (This mouse response is terrible - makes it nearly unuseable.)

---

### Post by mikewhatever on 2007-01-19
The link in my earlier post describes how to install alsa driver in details. I have also used this one: [http://ubuntuforums.org/showthread.php?t=205449&highlight=comprehensive+sound](http://ubuntuforums.org/showthread.php?t=205449&highlight=comprehensive+sound)
What is your touchpad, or do you use an external mouse?

---

### Post by RichPicker on 2007-01-19
I'll do what I can to install the latest alsamixer driver. But that seems like a gamble at best. I see the instructions, but they make no sense to me. I didn't see in the Ubuntu blurbs that UNIX command-line expertise is required, Yes, I am disappointed, but venting that frustration here won't help the mic, Thans for your help. I'll do what I can. And a bug has been launched.

It's a Touchpad-PS/2 touchpad, and it's working very badly. Rarely is one click enough. Sometimes it takes 6 clicks. And it jumps around in the text.

---

### Post by RichPicker on 2007-01-19
Here's more info on the touchpad. 90% of the time, at least 2 clicks are required, for internet links, the numbers on the calculator, the "Go" button for the search on this page - everything. I've changed the settings on the mouse from the System>Preference>Mouse, but the problem is unchanged. Many times up to 6 clicks are required. This problem did not exist when this machine was running windows xp, so I believe the touchpad itself is healthy.

---

### Post by RichPicker on 2007-01-19
The chipset-driver instructions didn't help. And the instIstructions begin by saying the best f believe the only hope is for ubuntu to identify and fix the bug, or for me to re-install windows. This is very difficult to type, because the cusor moves all over the text. This ubuntu linux is NOT  robust. It is a grave disappointment. Typing is extrememly difficult. I have launched a bug about the mouse - but no response. I made a mistake to trust ubuntu.](*,) :confused: :( :( Ty

---

### Post by mikewhatever on 2007-01-19
I am not familiar with Dell's laptops, cause I have HP pavilion. We should concentrate on one thing at a time, either the mic, or the touchpad, whatever is more pressing. Meaning info on the touchpad, you should post some specs, not the number of clicks. For example, mine is synaptics v6.2.

---

### Post by RichPicker on 2007-01-19
The touchpad is the more important problem.

Dell Inspiron
Pentium M
Touchpad-PS/2

This is all the info I was able to find in the reboot (F2) screen. Let me know where I can get more info if you need it. Rarely does one click work. At least 2 are requred 90% of the time. And when in this type of text block, the cursor jumps. The click problem is the most important. Sometimes it requres 6 clicks to place the text cursor in a text block. While typing this message, the cursor jumped to another line of text four times. I do not have the ability to script complex lines in the terminal.

---

### Post by mikewhatever on 2007-01-19
Done some searching. There seems to be a different fix to your mic.
[http://ubuntuforums.org/showthread.php?t=201887&highlight=dell+inspiron+SigmaTel+STAC9200](http://ubuntuforums.org/showthread.php?t=201887&highlight=dell+inspiron+SigmaTel+STAC9200)

Searching more for touchpad solution, found this [http://ubuntuforums.org/showthread.php?t=333755&highlight=dell+inspiron+touchpad](http://ubuntuforums.org/showthread.php?t=333755&highlight=dell+inspiron+touchpad)

---

### Post by RichPicker on 2007-01-19
Thank you for your help. I'll do what I can. But there are many things I don't understand. For example, how to:

"1. backup your existing /etc/modprobe.d/alsa-base"

I have no idea what this means, Sorry for all the trouble I'm bringing to this forum. I certainly regret installing ubuntu. The true problem seems to be that ubuntu simply doesn't work. They  should test it before they release it. Oh wel...  I'll try my best with all these instructions before I post again.

---

### Post by RichPicker on 2007-01-19
From the mouse fix instructions:
"Turn on your computer and keep pressing "ESC" until you get to the GRUB menu."

I pressed Esc many many times. but nothing happens. 

Regarding the mic fix instructions:
How do I "backup existing /etc/modprobe.d/alsa-base"?

---

### Post by bodhi.zazen on 2007-01-19
> **RichPicker said:**
> From the mouse fix instructions:
"Turn on your computer and keep pressing "ESC" until you get to the GRUB menu."

I pressed Esc many many times. but nothing happens. [/quote]

Not sure about that one ...

> Regarding the mic fix instructions:
How do I "backup existing /etc/modprobe.d/alsa-base"?

Open a terminal Type:

```
sudo cp /etc/modprobe.d/alsa-base /etc/modprobe.d/alsa-base.bak
```

And, don't be afraid to ask questions.

And do not expect to learn a whole new OS in 5 minutes. Give yourself some breathing room :p

---

### Post by mikewhatever on 2007-01-19
Right, I can see you know how to back up, then, to edit the file use this command ```
sudo gedit /etc/modprobe.d/alsa-base
```

Don't forget to save after editing.

About GRUB, that's a boot manager for those of us who dual boot. If you don't, then you don't have it. Have you looked at the CPU load as the test suggested? > Make sure this is your problem:

open: Applications &#8211; System Tools - "System Monitor" (from the menu in GNOME). If you have only KDE (then maybe you're using Kubuntu) you should install System Monitor by using Synaptic (as I've noticed &#8220;KSysguard&#8221; in KDE doesn't detect the problem). Click on &#8220;Resources&#8221;: you will see &#8220;CPU1&#8221;: and the percentage of usage of your processor. If the percentage is high (try this without any programs running), i.e. something like 50% or more then you have this problem.

---

### Post by mikewhatever on 2007-01-19
This is probably redundant, but did you know, that Mouse settings in System->Preferences affect the touchpad. You can try raising acceleration and sensetivity.

---

### Post by RichPicker on 2007-01-19
CPU Usage is averaging 4%

Yes, I have tried changing the mouse settings.

Here's what I have so far in the terminal:

rich@rich-laptop:~$ sudo cp /etc/modprobe.d/alsa-base /etc/modprobe.d/alsa-base.bak
rich@rich-laptop:~$

Okay, Make what edits to which file?

---

### Post by OldTimeTech on 2007-01-19
Which Ubuntu did you load to your laptop, I've heard/told that Edgy 6.10 works better with laptops than 6.06....

---

### Post by mikewhatever on 2007-01-19
What you've done with cp command made a copy of the original file. Now to edit the original file paste this into terminal 
```
sudo gedit /etc/modprobe.d/alsa-base
```

a file will open, so add the line in bold to the end of it and save.

```
1. backup your existing /etc/modprobe.d/alsa-base
2. append the following to the end of the file:

**options snd-hda-intel model=ref**

Reboot, tweak your levels in alsamixer to your liking, record, playback.
```

---

### Post by RichPicker on 2007-01-19
I changed the file from the terminal,.saved it, restarted the machine. Now, by double-clicking the sound icon - under Options I get : mic, front mic, or line

I tried recording again, but the same thing - only hiss.

I'm going to switch to Mandriva. This is too much trouble. I don't expect to learn it in five minutes. I've been here doing this for four days. ubuntu is neither stable NOR free. It has cost me toooo much wasted time trying to get it to run. 

Thanks for you help. Good luck with this piece of crap ubuntu

---

### Post by mikewhatever on 2007-01-19
Sorry it didn't work as well as you had hoped. You should choose what's best for you.

---

### Post by jvc26 on 2007-01-19
Mate just because it didnt work for you there is no need to slag it off in such a crude and generalized manner. Maybe something didnt work, people may well go to help you, but you have to be patient. Things could well be fixed in a few days. I know its really frustrating to have lost a few days trying to get to the bottom of the problem but thats no call for getting offensive.

Good luck with mandriva, I hop it works out for the best for you.
Il

---

### Post by RichPicker on 2007-01-21
The mic and mouse problems exist exactly in Mandriva. It's not an Ubuntu problem, it must be a problem with this Dell laptop and Linux in general.

And this is a poor apology, but after writing manuals for this stuff for 20+ years, I have no patience left. 

I edited this file:
sudo gedit /etc/modprobe.d/alsa-base

with this:
options snd-hda-intel model-ref

And now the mic DOES work. (I must select 'mic' NOT 'front mic'.)

But, Audacity stopped working. When I try to launch it I get this:

"There was an error initializing the audio I/o layer.
You will not be able to play or record audio.
Error: Host error."

Audacity worked before I edited the file.

And when I start/restart with the headphones UNPLUGGED, There is no sound from the headphone jack, only from the laptop's speakers. I must start/restart with the headphones PLUGGED IN to get that jack to work. That, too, is new since I edited the file.

I fear that appending the file kinda' sorta' forced the mic to work, but it created or neglected other problems. Is it possible to find the root problem?

---

### Post by mikewhatever on 2007-01-21
Welcome back. To tell you the truth, I do not know the exact solutions for your sound/mic and touchpad problems. It seems quite obvious, that your sound card and touchpad need 'tweaking', but as much as we all want our problems solved quickly and efficiently, sometimes it is not possible. To help, you can first of all be patient, second, look under System->Administration->Device Manager, find the hardware that's not working, and search or ask for specific help. 
I've only myself installed Ubuntu not that long, and also had problems, which I new not how to solve, nor could get any help with. I thought I'd give it a week, and then if the problems aren't fixed, I'll consider uninstalling. In five days, I was done an learned a lot on the way.

Cheers!:D

---

### Post by RichPicker on 2007-01-24
I was running 6.06 Dapper. I did all the recommendations from this group, and others from a helper at launchpad.net.

It got the mic to work. and the mouse to work 'better' but there were other problems. (Audacity still crashed, etc.) The launchpad.net person suggested I upgrade to 6.10 Edgy.

I did that, and am now running Edgy. The same problems exist. I repeated the previous fixes, but the mic still does not work. The mouse is not as bad as before, but still not right. 

Audacity crashes when I open it. Sometimes Sound Recorder locks up and I have to force quit. When Sound Recorder does work, and I try recording, I hear hiss or hum only.

Dependency problems? Driver problem? I don't know enough about linux or Edgy to proceed unaided.

Your suggestions?

---

### Post by RichPicker on 2007-01-24
Sorry. I keep saying mouse, but I mean touchpad.

---

### Post by RichPicker on 2007-01-24
Also, with Dapper the Totem Movie player never worked, though I downloaded all the necessary plugins, codecs, etc. I use Kaffeine to play the movies. But now with Edgy , neither of them works.

---

### Post by RichPicker on 2007-01-24
I just installed GXINE and it works well. And, the audio adjustments and graphic equalizer work well. So, this means some part of the sound card is working well, but not the mcrophone?

---

### Post by bro on 2007-01-25
Hi. 
My mic is not working. I have my alsa drivers. I have my intel hda soundcard. I have ubuntu 6.10. I did the above with adding the line to /etc/modprobe.d/alsa-base. However. My mic does not work! 
Is it possible at all to get the mic to work with this soundcard? Or ar we just passing possibilities but there's no one whom actually got it working?

---

### Post by mikewhatever on 2007-01-25
Reposting this just to make sure it is noticed [http://ubuntuforums.org/showthread.php?t=205449&highlight=comprehensive+sound](http://ubuntuforums.org/showthread.php?t=205449&highlight=comprehensive+sound)

---

### Post by RichPicker on 2007-01-25
I don't know,. The mic worked when I was running Dapper. But with Dapper, the Audacity still crashed. Since upgrading to Edgy, I have had zero response from the launchpad.net folks. You might have it right, maybe it's not possible. I will pursue it.

---

### Post by RichPicker on 2007-01-25
After receiving a program update this morning, I tried Sound Recorder, and it works. But only by selecting Capture or IEC958. (The IEC 958 switch is new since the update.)

If I try recording with Capture Mux selected, Sound Recorder hangs and I must Force Quit.

If I click the Record button a second time, without closing that window and opening a New window in Sound Recorder, it hangs and I must Force Quit.

Audacity doesn't work. Under Edit > Preferences > Audio I/O the Playback and Recording Devices are both /dev/dsp with no other choices in those tabs.

Well... additionally - minutes ago Sound Recorder worked when selecting IEC958, but no longer. Now it works only when selecting Capture.

I just now tried the Skype Test Call, and the mic worked. Good.

So, it looks like the mic works only by selecting Capture in Sound Recorder, and only with a New window in Sound Recorder, and it works with Skype. But Audacity is still strange.

Oh how funny. I tried Sound Recorder one more time with IEC958 before posting this message, and it worked this time. Sheesh...

---

### Post by RichPicker on 2007-01-25
More information:

Each time I open Audacity, it asks "which language" - a first time start each time.

I recorded a few seconds of voice in Sound Recorder, saved it, and imported it into Audacity. Audacity played it very well. Looks like it's just the mic that Audacity doesn't like.

I'm posting all this to the launchpad.net also. Progress is being made.

---

### Post by RichPicker on 2007-01-25
Playing around with Audacity, under the microphone LR volume slider meters, I selected "Monitor Input". Then tried to Record, and IT WORKED. 

I have recorded in Audacity with and without  "Monitor Input" selected, and it works.

Maybe because today is Thursday? :D   I'll keep my fingers crossed, continue testing and using, and report back here tomorrow.

---

### Post by RichPicker on 2007-01-26
It all seems good and working today. Thanks everyone for the help.,

---

### Post by RichPicker on 2007-01-27
This is nuts.

Everything was working, until today when seemingly out of the blue, all the problems returned.

A) Audacity crashes
B) Sound Recorder hangs and I must Force Quit.
C) Several clicks (taps) on the trackpad are required to select and link or button.

The only 2 things I can think of that changed are:

1) I installed and successfully used the Hydrogen application.

2) When I started the laptop today I got a message that Skype quit unexpectedly when I shut it off last night.

I removed Hydrogen and restarted, but the same problems exist.

I couldn't understand how to remove Skype (it's not in Add/Remove) so, I rebooted from the Edgy CD and COMPLETELY reinstalled Edgy.

I backed up my data on disc, and completely reinstalled.

From a fresh start here: the mic does not work. Sound Recorder and Audacity don't hang or crash, but no recording is possible.

I will not use Skype again until I KNOW if it is the problem.

If anyone has any suggestions, I welcome them.

Is it possible that this Dell laptop will simply NOT WORK with linux? What am I doing wrong?

---

### Post by chronusdark on 2007-01-29
i have a dell xps m1210 and i have the no mic problem and its not that its not recording its that its recording at a volume REALLY REALLY low (ie in audacity the wave barely bumps) but i get a big jump when i unplug/plugin the mic so i know its geting input i just dont think its doing the correct thing with it

as for your synaptic problems mine is working fine so i dont know how to help you there but if i find something as to the mic problem i wil sure let you know

---

### Post by RichPicker on 2007-01-29
My mic is working again, at least for now. For your low volume: Check the 'Capture" settings in the volume control and by typing   alsamixer    in the terminal window. There are settings in those two places for the capture volume (the input volume).

My trackpad is good now also. 

Only problem now is the sound is not in sync with the picture when I play a movie with Gxine or Kaffeine. The sound IS in sync when I use Totem Movie player, but not when I use the other two. I'll check in this forum and elsewhere for any fixes.

---

### Post by RichPicker on 2007-01-29
Everything was working well previously also. But I think Skype would NOT relinquish control of the sound card. I have not re-installed Skype, and I won't until I know it's 'safe'

Maybe off topic, but how does a person Remove a program that they installed without using Add/Remove -- like Skype --  which is installed by downloading it from their web site. I couldn't find how to dump the thing.

---

### Post by RichPicker on 2007-05-10
My mic DID work with Edgy. But an update killed it. I waited and installed Feisty, but the mic does not work, and a fix has not been released yet.

Would it work for me to do a clean install of Edgy and avoid whatever was in the update, but turning off the updater?

---

### Post by aktiwers on 2007-05-10
Is your Mic connected infront of the cabinet? 
Mine is, and only works if I double click on the sound icon in the panel.
Go to Edit => Preferences => Tick "Mic Select" And close that window.
Now go to options, and pick Mic2.

This works for me.. and somehow also when it is connected from behind of the cabinet.
hmm well.. maybe it works for you too.

---

### Post by RichPicker on 2007-05-10
Its a dell laptop. I've done all the alsa and volume control stuff. I need to wait for the fix to arrive in Feisty, but wondered about going back to Edgy. It's been a frustration.

---

### Post by RichPicker on 2007-05-10
The longer I go without Skype the more I realize how much I NEED it.

---

### Post by RichPicker on 2007-05-11
I really feel stupid. I need to apologize to everyone for my inability.
The mic works perfectly now.

Instead of addiing this to the alsa-base file:  ". . . =ref"  (= character)

I added this:  ". . . -ref"  (- character)

How lame. Thank you everyone for your help.

---

