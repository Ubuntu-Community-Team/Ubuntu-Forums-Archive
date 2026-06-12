---
title: "Why does cursor move erratically &amp; erase data? (LM13)"
date: 2013-04-06
forum: Apple Hardware Users
---

### Post by este.el.paz on 2013-04-06
[http://forums.linuxmint.com/viewtopic.php?f=47&t=129344](http://forums.linuxmint.com/viewtopic.php?f=47&t=129344)

Folks:

I've had this thread posted on the LM forum for several weeks with little offered for solutions, let alone comment on the problem.  I searched google and see that there are many similar complaints, I have "disable touchpad while typing" checked . . . .  I'm posting this question here based upon a recent check of the sources.list in LM 13 . . . most of which is ubuntu-based--perhaps there might be some experience into this problem from this forum?  I do have two installs of PPC Xubuntu/Lu 12.04 on two of my PPC units and haven't had this level of problem, whereas the LM13 MATE 64 install on my MBPro seems to find this problem, particularly in FF, but tested in Midori, and a number of DEs . . . across the board the problem will occur, where typing along peacefully and suddenly cursor jumps to back in the text box, erasing data in between . . . yesterday I noticed that when I hit the shift key to capitalize a letter . . . the problem happened, just the first time I noticed that aspect.  

Anyway, thanks for any insights . . . .
> et al:

Moving this post over to a new topic, I searched the forum  here, as well as google, and saw reference to mouse/cursor moving  erratically, or losing control of mouse, and there was a bug report from  Sept '12, that I couldn't find buried in the list of bug reports with a  similar issue as mine, but no solutions found.  The problem is that the  mouse/cursor will suddenly jump back in an email, usually in a browser,  and the typing will just start there; and more annoyingly, sometimes  the text between where it was and where it ends up, will be erased.  It  might be in this post, after almost getting to the end, suddenly it will  all be erased.  I couldn't find any insights into this problem, so I'm  posting here.  Actually there was a post from someone in LM14 with the  jumping cursor problem, the answer given by someone was to update the  xserver-xorg-core file . . . I checked mine in synaptic and it's as new  as it can be for LM13.  Perhaps someone can offer some insights?  The  code above is showing the errors that came when I tried to install  Chromium . . . in both Synaptic and Terminal.

e.e.p.

---

### Post by este.el.paz on 2013-04-20
Alrighty . . . so far so good . . . let me rephrase the question, it seems like the wisdom from the LM forum is mostly pointing at the touchpad as the problem.  I've got "disable touchpad while typing" checked as "on" and now in XFCE DE I've got the touchpad turned "off" to see if that solves the problem . . . .  I'd prefer to be able to use my touchpad as needed, rather than having to turn it on or off in the Terminal or in Settings each time I want to use it.  

But from what I've actually experienced it is something to do with the keyboard, either hitting the shift key or some other key that seems to elicit the data erasure problem . . . rather than accidental swiping of touchpad.  The new question is, is it generally a problem in Xubuntu 12.04 64 bit system that the touchpad needs to be completely disabled in order to type?  I saw a vague reference in a LM thread about "turning off touchpad" as taking care of "jumping cursor" problem, but my searches for "erratic cursor" erasing data brings zero search results.  I'm wondering if I switch to Xubun 12.04 if there is any similar problems with typing in a laptop where somehow the proximity to the touchpad causes erratic cursor movement that erases lines previously typed as it continues to do in LM13.

Thanks,

e.e.p.

---

### Post by matt_symes on 2013-04-20
Hi

Is the mousepad not scyncing correctly and so jumping about ?

What do your logs say ? Look in /var/log/syslog and older versions of the same.

```
egrep "sync|mouse|lost" /var/log/syslog{,.1}
```

Inspect them visually as well. Pick the times in the logs where you knew  the device was playing up.

Also check /var/log/dmesg as well.

What driver are you using for the mousepad ?

```
xinput --list
```

```
lsmod
```

Not sure what it is but it will us a start. If it's a bug in the software then there may not be much you can do if there are no workarounds or quirks you can employ.

It may be a case of using an external mouse and maybe even keyboard.

How confident are you that this is not a hardware issue ? What tests have you performed to see if it is not hardware ?

Have you physically opened the PC to check for dust, dirt, dry joints ? What other operating systems have you ran on there *recently* that worked with no problems ?

**EDIT:**

And also when you reply, please don't create walls of text. Use spacing and paragraphs. Use many of them.

It will make it much easier to read. I know many people who would not bother to read a wall of text as it's such hard going.

Please don't think that was anything but helpful advice as that was the spirit it was meant in.

Kind regards

---

### Post by este.el.paz on 2013-04-20
@matt_symes:

Thanks for the reply, hopefully I'm providing a reasonable amount of text.  First thing, in OSX partition I do not have this problem, it's exclusive to LM13 MATE and the various DEs I have installed in LM; so I don't think it's hardware--it's a '09 MBPro.  I do use a plug in mouse when the problem happens, which is intermittent, but when it happens will be paroxysmal--meaning it will continue to occur once it starts.  Yes, I think it's a bug, but I've been wrong many times in my life.  In terms of logs, I really don't know enough to know if what I'm seeing has any meaning.  But I did "leafpad" the dmesg and I pasted a few lines from it, i don't know if you want me to try to compress the whole thing and attach it as .tar.gz, obviously it would be a wall of text?  Right now the touchpad is turned off in XFCE DE, so I didn't know if "HEST is not enabled" has anything to do with that.  Again, I ran the mouse|lost command a few ways, it seemed to return to the prompt or the ">" . . . .  lsmod is pasted in . . . .

```
var/log/dmesg:

77] GHES: HEST is not enabled!

93] mousedev: PS/2 mouse device common for all mice

8] input: Apple Inc. Apple Internal Keyboard / Trackpad as /devices/pci0000:00/0000:00:04.0/usb3/3-6/3-6:1.0/input/input8
[   23.184658] apple 0003:05AC:0236.0003: input,hidraw2: USB HID v1.11 Keyboard [Apple Inc. Apple Internal Keyboard / Trackpad] on usb-0000:00:04.0-6/input0

```

```
sudo egrep "sync|mouse|lost /var/log/syslog{,.1}
>
```

```
xinput --list&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; Logitech USB Optical Mouse              	id=12	[slave  pointer  (2)]
&#9116;   &#8627; bcm5974                                 	id=10	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Power Button                            	id=7	[slave  keyboard (3)]
    &#8627; Sleep Button                            	id=8	[slave  keyboard (3)]
    &#8627; Apple Inc. Apple Internal Keyboard / Trackpad	id=9	[slave  keyboard (3)]
    &#8627; Built-in iSight                         	id=11	[slave  keyboard (3)]



```

```
lsmodModule                  Size  Used by
michael_mic            12612  4 
arc4                   12529  2 
vesafb                 13844  1 
parport_pc             32866  0 
snd_hda_codec_cirrus    28098  1 
bnep                   18281  2 
rfcomm                 47604  0 
ppdev                  17113  0 
binfmt_misc            17540  1 
nvidia              11308613  32 
snd_hda_intel          33719  4 
snd_hda_codec         127706  2 snd_hda_codec_cirrus,snd_hda_intel
snd_hwdep              17764  1 snd_hda_codec
lib80211_crypt_tkip    17390  0 
snd_pcm                97275  2 snd_hda_intel,snd_hda_codec
wl                   3074895  0 
snd_seq_midi           13324  0 
snd_rawmidi            30748  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61929  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29990  2 snd_pcm,snd_seq
hid_apple              13375  0 
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
btusb                  18332  1 
usbhid                 47238  0 
bluetooth             180153  13 bnep,rfcomm,btusb
snd                    79041  17 snd_hda_codec_cirrus,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
hid                    99636  2 hid_apple,usbhid
cfg80211              205774  1 wl
joydev                 17693  0 
uvcvideo               72627  0 
videodev               98259  1 uvcvideo
v4l2_compat_ioctl32    17128  1 videodev
bcm5974                17399  0 
mac_hid                13253  0 
soundcore              15091  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
applesmc               19554  0 
lib80211               14381  2 lib80211_crypt_tkip,wl
shpchp                 37201  0 
input_polldev          13896  1 applesmc
i2c_nforce2            13058  0 
apple_gmux             12751  0 
video                  19651  1 apple_gmux
apple_bl               13673  0 
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
usb_storage            49243  0 
firewire_ohci          41000  0 
firewire_core          63600  1 firewire_ohci
crc_itu_t              12707  1 firewire_core
forcedeth              63460  0 
```

---

### Post by matt_symes on 2013-04-20
Hi

> sudo egrep "sync|mouse|lost**"** /var/log/syslog{,.1}

That was missing a quote.Not to worry about that now.

 Are you receiving my replies by email ? If so then please double check the actual post before following the commands.

Lets gets the logs.

```
sudo apt-get install pastebinit
```

```
cat /var/log/syslog | pastebinit
```

Post back the URL displayed underneath that command.

```
cat /var/log/dmesg | pastebinit
```

Same again with that one.

Well check those first and move back if required to see if there's anything of interest in them.

To cut down my search, can you tell me the last time it happened ?

EDIT:

Can you also post the output of

```
xinput --list-props "Apple Inc. Apple Internal Keyboard / Trackpad"
```

Kind regards

---

### Post by este.el.paz on 2013-04-20
@matt:

Sorry about that missing quote, I was in the forum, but I ran the command a number of times, must have missed it; I'm at work and have to . . . work as well as play. [Edit: I just ran [COLOR=#000000]*sudo egrep "sync|mouse|lost*[/COLOR]**" ****/var/log/syslog{,.1}** again and it just returned the prompt as I mentioned before]

Anyway, thanks for the code on installing pastebinit . . . much appreciated.  A new variation of the problem happened yesterday, where suddenly the whole email was highlighted, and then a few minutes later I was posting in a forum and the "code" html symbol was pasted without me clicking on "code" . . . .  The exact time I can't say, was in Chrome or FF and typing an email reply . . . might have been 10 AM or lunch time . . . would not have been after 3 PM . . . I think later on like 6PM is when I turned the touchpad off, and haven't done enough typing since then to see if it changes the situation or not.

[Edit, yes, I saw that the first pastebinit was empty, perhaps there is some limit on the file size on the wifi at work?  If the second one is also empty I'll try it again at home.]
[http://pastebin.com/mRjXcL6R](http://pastebin.com/mRjXcL6R)

[http://pastebin.com/fiY9WJEE](http://pastebin.com/fiY9WJEE)

xinput --list-props "Apple Inc. Apple Internal Keyboard / Trackpad"
Device 'Apple Inc. Apple Internal Keyboard / Trackpad':
    Device Enabled (143):    1
    Coordinate Transformation Matrix (145):    1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
    Device Product ID (259):    1452, 566
    Device Node (260):    "/dev/input/event8"

---

### Post by matt_symes on 2013-04-20
Hi

You missed the edit to my last post as well. Please take a look. 

Always double check the post. It's common practice to edit an existing post than for create a new post for every idea one may have. It's also for editing typos.

Kind regards

---

### Post by matt_symes on 2013-04-20
Hi

This pastebin is empty.

[http://pastebin.com/rD7SrQf9](http://pastebin.com/rD7SrQf9)

Can you run this paste again

```
cat /var/log/syslog | pastebinit
```

and repost the link.

I'll take a look for you tomorrow as it's now 1.20am here.

Hopefully the logs will show us something or we'll be able to make progress with the information we have gained so far.

Kind regards

---

### Post by este.el.paz on 2013-04-21
@matt:

I guess it's Sunday all over the planet, hopefully you saw that I changed the first pastebinit link . . . perhaps there's nothing instructive there.  I was thinking yesterday that it must have been late when you were writing, and I do appreciate the fact that you replied with some help, but probably better to get more sleep to keep the show going in the long run.  Anyway, it's interesting what's happening, if you go back to the one email where you can see the bold text in the command that I copied pasted from the Terminal . . . I didn't select that text to be bold . . . and then I couldn't un-bold it either . . . so I'm considering that to be part of this same problem . . . . ??

And, earlier I was thinking that it was a FF problem because it always seemed to happen there, but then it happened in Midori as well, and then Chrome . . . .  However, last night I was replying to an email in my other computer, iBook, running Xubuntu 12.04 PPC and reviving from suspend into FF . . . typing an email, and suddenly a new tab opened and the text started typing in the location bar as the cursor had jumped there . . . this was plugged in keyboard and mouse . . . so that was the first time this kind of problem had happened in Xubuntu . . . and starting me to think that it's not just an LM problem . . . .  Don't know now.

Anyway, was thinking that since I've gotten zero direct help on my issue from LM forum that it might be time to switch the MBPro over to Xubuntu 64 . . . it might change something or it might not, but at least here someone tried to give me some direction into the problem . . . that much I appreciate . . . .  Thanks very much.  We'll see if I can find the time . . . it is all in the same family of OSs . . . .

e.e.p.

---

### Post by este.el.paz on 2013-04-24
> **matt_symes said:**
> Hi

What do your logs say ? Look in /var/log/syslog and older versions of the same.

Inspect them visually as well. Pick the times in the logs where you knew  the device was playing up.

Also check /var/log/dmesg as well.

Not sure what it is but it will us a start. If it's a bug in the software then there may not be much you can do if there are no workarounds or quirks you can employ.

s

@matt_s:

So, I've posted the requested items, and in the interim I was playing around with disabling the touchpad . . . and I'd have to say that the problem didn't happen during that time, but then I didn't do a lot of typing either.  So, now I've changed back to MATE with "disable while typing" . . . and as yet no problem.  I upgraded the system this morning and I did see that a new "xserver-xorg-core" was installed, and that was a possible solution offered in another thread about cursor problems.

However, today at 1:25PM I tried to launch newly installed GParted app and on the authenitification sign in I typed 3 letters and then I couldn't type any more, and nothing else was launch-able either . . . the whole screen was frozen . . . had to shut the computer down.  On re-launch I was able to open GParted and just as a test I swiped the touchpad to see if it would freeze the screen, but . . . no.  I checked the var/log/syslog  and nothing was listed at 1:25 . . . it went from 1:20PM and then jumped to 1:27PM after I re-launched.  So, is this a "new" problem or just part of the old?  I can't tell from my limited knowledge whether what is listed is relevant to a problem or not.

[http://pastebin.com/7dFBUtA2](http://pastebin.com/7dFBUtA2)

Don't know if that will show anything or not . . . .

e.e.p.

---

### Post by matt_symes on 2013-04-24
Hi

> **este.el.paz said:**
> 
However, today at 1:25PM I tried to launch newly installed GParted app and on the authenitification sign in I typed 3 letters and then I couldn't type any more, and nothing else was launch-able either . . . the whole screen was frozen . . . had to shut the computer down.

Does your keyboard have a caps lock light ? 

If it does, next time the machine freezes, is the light flashing ?

It it is then the kernel has crashed. 

If it's not flashing then press the caps lock key. 

Does it toggle the caps lock light on and off ? 

It not the you have had a kernel crash. 

If it does toggle on/off then that would suggest X has crashed.

> On re-launch I was able to open GParted and just as a test I swiped the touchpad to see if it would freeze the screen, but . . . no.  I checked the var/log/syslog  and nothing was listed at 1:25 . . . it went from 1:20PM and then jumped to 1:27PM after I re-launched.  So, is this a "new" problem or just part of the old?  I can't tell from my limited knowledge whether what is listed is relevant to a problem or not.
[http://pastebin.com/7dFBUtA2](http://pastebin.com/7dFBUtA2)

Don't know if that will show anything or not . . . .

e.e.p.

It's really hard to make any kind of diagnosis because there is nothing in the logs and when i click on that pastebin link above i'm getting 

> Unknown Paste ID!

so i can't even check for myself :( 

It sounds like it may be a different issue but we're working blind.

The only thing i can think of at the moment is to look in the directory /var/crash.

Can you post the output of

```
ls -lh /var/crash
```

That is a small L in -lh.

Kind regards

---

### Post by este.el.paz on 2013-04-24
> **matt_symes said:**
> Hi



Does your keyboard have a caps lock light ? 

If it does, next time the machine freezes, is the light flashing ?

It's really hard to make any kind of diagnosis because there is nothing in the logs and when i click on that pastebin link above i'm getting 
so i can't even check for myself :( 

It sounds like it may be a different issue but we're working blind.

The only thing i can think of at the moment is to look in the directory /var/crash.

Can you post the output of

```
ls -lh /var/crash
```

That is a small L in -lh.

Kind regards

@matt:

Thanks for the reply . . . I don't know what's going on with the pastebinit . . . I think the internet here at work is not too fast.  Thanks for the insight into caps lock, I didn't notice anything.  I ran the code on the crash and got:
```
ls -lh /var/crash
total 216K
-rw------- 1 root whoopsie 216K May 18  2012 mintmenu-keybinder.0.crash
```

Which seems a bit odd, lost track of time, but didn't think I had even had the LM system installed then?  But, nothing from today . . . .

e.e.p.

[Edit:]  Right after I posted the above info I was typing an email, several sentences went fine, then, beginning a new sentence with the capital S . . . and the next letter and subsequent words were up in the first sentence . . . .  So, the problem is contining even after update to xserver-xorg-core earlier today . . . .  And, I checked the syslog again, and nothing shows at that time 5:58PM . . . only 8 mins. earlier was "wpa_supplicant[871]: WPA: Group rekeying completed with e0:91:f5:0a:47:c1 [GTK=TKIP]"  which also was there 30 mins before that, as well as at the top of the hour was a "cron" . . . .  Nothing that seemed to indicate anything happening . . . it's just like a system "graffitti" . . . .  

I'm pretty sure that my fingers didn't touch the touchpad, even though in MATE and in FF this problem is more frequent . . . I'm still looking at the shift key typing a capital letter as what sets off the problem . . . but it hasn't happened in these sentences.  Is it after two spaces between the period and the new sentence?  I just tried that as well . . . haven't figured out how to reproduce the problem at will.

---

### Post by matt_symes on 2013-04-24
Hi

It's really odd that nothing is being logged during the crash.

What's your disk space like ? Can you post the output of

```
df -h
```

Kind regards

---

### Post by este.el.paz on 2013-04-24
df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda3        21G  5.9G   14G  31% /
udev            1.8G  4.0K  1.8G   1% /dev
tmpfs           736M  1.1M  735M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            1.8G   88K  1.8G   1% /run/shm

---

### Post by matt_symes on 2013-04-24
Hi

I have to say that with no information to go on at all, i'm totally at a loss at the moment.

I have not been able to view any of the logs that may hold some clues. 
No crash dumps to give clues. 
Space on the drive for syslog to write to.

I'm really not sure what to suggest as everything i may suggest would just be a total stab in the dark. I'm not sure you'll be able to get this fixed via a forum with no information to go on.

*shrugs*

Kind regards

---

### Post by este.el.paz on 2013-04-24
> **matt_symes said:**
> Hi

I have to say that with no information to go on at all, i'm totally at a loss at the moment.

 I'm not sure you'll be able to get this fixed via a forum with no information to go on.

*shrugs*

Kind regards

Matt:

Well, thanks for trying as much as you did, much appreciated . . . I'll keep tracking the problem until it maybe becomes more reproducible . . . or, get tired of it.

e.e.p.

---

### Post by matt_symes on 2013-04-24
Hi

If you can get any information in the logs when something fails then post it here.

I'm subscribed to this thread. I just need something to go on before i can even attempt to try to help.

Kind regards

---

### Post by este.el.paz on 2013-04-25
@Matt:

I was trying to post a further update in the LM "bug report" site . . . which doesn't seem to elicit any response, but I was typing anyway and the problem happened . . . so I'm pasting what I was typing so you can see it . . . sorta . . . .  My previous post there lists as being "21 days ago" and the initial post probably 2 weeks before that . . . with no reply offered there as of this moment, hence my sniping about it.

> Yes, I'm getting a sense of great speed and alacrity in the LM community when it comes to offering insight into problem[server]s.  I've tried removing Cinnamon, I've upgraded the system several times since my first post here, and even looking for an answer on the forum, saw a mention in LM14 that the x[] . . . .  OK, that was the problem, as I started typing the "s" in "xserver" the cursor jumped back to in back of "problem" and began typing there.  It's very irritating . . . but intermittent . . . .

e.e.p. 


So, you can see where I put the brackets after the "x" . . . that is where I was busily typing my rant . . . and the next letter the cursor jumped to behind "problem" and I had typed "server" before I noticed it.  Haven't had time to check the syslog to see if anything happened at around 6:38 PM my time on 4/25 . . . .  The connection might be a bit better here at this location so if I see something interesting around that time I might try to pastebinit . . . again.  So, just to be clear, this isn't a mouse problem, it's a cursor problem, if there is such a distinction . . . logged in to MATE and typing in FF, which is where the problem happens the most . . . FF that is.

e.e.p.
[Edited moments later:  Problem happened at 6:38PM, so you can see in syslog that it jumps from 6:20 to 6:50 . . . and looks like something happening with internet connection?  But I was/am under the impression I'm connected all the time . . . doesn't seem to be anything instructive in the syslog for this problem??

> Apr 25 18:20:06 MacBookPro NetworkManager[843]: <info> (eth1): supplicant interface state: 4-way handshake -> completed
Apr 25 18:50:17 MacBookPro wpa_supplicant[871]: CTRL-EVENT-DISCONNECTED bssid=58:97:1e:23:54:70 reason=0
Apr 25 18:50:17 -MacBookPro kernel: [44206.656644] cfg80211: All devices are disconnected, going to restore regulatory settings
Apr 25 18:50:17 -MacBookPro kernel: [44206.656658] cfg80211: Restoring regulatory settings
Apr 25 18:50:17 -MacBookPro kernel: [44206.656668] cfg80211: Calling CRDA to update world regulatory domain
Apr 25 18:50:17 -MacBookPro NetworkManager[843]: <info> (eth1): supplicant interface state: completed -> disconnected
Apr 25 18:50:17 -MacBookPro kernel: [44206.671955] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
Apr 25 18:50:17 MacBookPro kernel: [44206.671967] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)

---

### Post by este.el.paz on 2013-04-27
@Matt:

Just to let you know, to prevent you from wasting further time on thinking about this problem . . . I spent last evening zeroing out LM13 and using the somewhat unclear Alternate installer to install Xu 12.04 64bit into the partition where LM13 was living.  So, I'll continue testing to see if the problem is alleviated or if it works its way back into the system . . . .  So far I've just added GParted and LXDE . . . and the wireless drivers, fairly smooth except for the "GRUB installer" part, where the default choice is not auto-loaded . . . and I didn't write down the sda that was marked as "bios_grub" . . . had to go through the whole process again . . . .  I was using "Guided, use largest free space" . . . but in second install had to go back and mark the Home partition as "root" . . . manually . . . .  Seems like this has been around from the Debian installer for quite awhile??  Might have been easier just using the LiveDVD installer?  but I had just done that in PPC a few weeks back and there was something about not being able to use "manual install" on the LiveDVD, but the guided install went well for that one--thought I'd try it with the Alternate and do manual . . . but, I'm lazy.  : - )

Thanks for your efforts to help, you tried where the LM forum just never even got a balloon off the ground on the problem . . . sorry to have to say that, but . . . .  So, now I've got all my units, living and semi-comatose, running Xu 12.04 with LXDE added, two in PPC, and one Intel . . . good to go util the next LTS comes out.

e.e.p.

---

### Post by matt_symes on 2013-04-27
Hi

Take a read of this thread as the threads it links to.

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/240738](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/240738)

> [LEFT][COLOR=#333333][FONT=Ubuntu Mono]Due to recent diversity of touchpad hardware this bug gains publicity. I found that Macbooks, newer Samsung laptops and Asus EeePCs are among the affected systems[/FONT][/COLOR][/LEFT]

Maybe it's not totally fixed. There may be workarounds you can try though.

You're using syndeamon ?

Kind regards

---

### Post by este.el.paz on 2013-04-27
Matt:

That seems to describe the issue . . . a bit pressed for time right now, but I'll try to read thru the bug report tomorrow.  I'm hoping that the problem was "erased" by switching the OS.  I don't know if I'm using syndaemon or not; and I'm not quite sure if the suggested test on the link is something easy to do, or not--I would have to spend some more time with it.  So, thanks for finding that, some of the posters on LM forum were suggesting this is a touchpad issue, or touchpad interefering with mouse . . . and suggesting to turn off the touchpad altogether to test, I did try it but didn't do enough typing to see if it would show up--but still wouldn't consider manually turninig off the TP to be a viable or practical solution.  I still saw the problem happening thru the laptop keyboard, not touching the TP.  In Debian on my iBook if I inadvertently hit the TP while typing it would "freeze the screen" . . . I guess, "crash X" ???? whatever that is . . . and I would have to restart the computer to regain control.  This is another problem, X isn't crashing, etc . . . but as the one poster mentions, very irritating to lose whole sentences, etc.

Thanks again,

e.e.p.

---

