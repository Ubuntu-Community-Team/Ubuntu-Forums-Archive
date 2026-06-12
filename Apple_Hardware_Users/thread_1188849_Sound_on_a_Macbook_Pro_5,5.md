---
title: "Sound on a Macbook Pro 5,5?"
date: 2009-06-16
forum: Apple Hardware Users
---

### Post by NorQue on 2009-06-16
[SIZE="3"][COLOR="Red"]**Update/EDIT #2:**[/COLOR][/SIZE]
According to various reports in this thread **sound now seems to work with newest alsa snapshots**. Haven't tried it myself yet, but thanks to digging work done by bobbytables & barryreid we now have Ubuntu-specific step-by-step instructions on how to install the sound driver [here](http://ubuntuforums.org/showpost.php?p=7627817&postcount=98).



**Update/EDIT:**
Still no sound on the Macbook Pro 5,5. Since I guess I'm just the first one with this problem and other 13" Macbook Pro/5,5 users might follow later I thought I'd update this post with everything I tried unsuccessfuly so far.


[LIST][*] Installed alsa 1.0.20 from shell script ([http://ubuntuforums.org/showthread.php?p=6589810#post6589810](http://ubuntuforums.org/showthread.php?p=6589810#post6589810))
[*] Installed alsa 1.0.19 manually with patch for Macbook Pro 5,1 according to [wiki description]("https://help.ubuntu.com/community/MacBookPro5-1_5-2/Jaunty#Sound")
[*] Installed alsa 1.0.20 manually with instructions to enable [Intel HDA driver]("http://www.alsa-project.org/main/index.php/Matrix:Module-hda-intel")
[*] Added options snd_hda_intel model=mbp3 to /etc/modprobe.d/options
[*] Added options snd_hda_intel model=macbook-pro to /etc/modprobe.d/options
[*] Added options snd_hda_intel model=mbp3 to /etc/modprobe.d/options.conf
[*] Added options snd_hda_intel model=macbook-pro to /etc/modprobe.d/options.conf
[*] Added options snd_hda_intel model=mb5 to /etc/modprobe.d/options (with patched alsa 1.0.19)
[*] Created custom .asoundrc in home according to [dman77's suggestion]("http://ubuntuforums.org/showpost.php?p=7471221&postcount=8")[/LIST]

Actually I've tried a lot more things than that and all of the above in various combinations and an additional reinstall in the meantime, but to no success so far.

I've attached lspci, lsmod and proc/codec output to this post, maybe it helps someone else to find a solution to this problem.



Old Post:
---------------------------
Hello,

got me one of the new 13" Macbook Pros that were released last week and finally got around installing Ubuntu on it, which I used as only OS for two years already on my other PC.

I have some strange error messages related to ACPI on start up and no hibernate/suspend/restart, camera doesn't seem to work either, but that doesn't bother me much. What I really find quite annoying is that I can't get any sound out of it.

The *sudo dmidecode -s system-product-name* output says *MacBookPro5,5*, so apparently there's no support in the [Mactel Wiki Support Matrix](https://wiki.ubuntu.com/MactelSupportTeam/CommunityHelpPages#Mactel%20Wiki%20Support%20Matrix) yet. I managed to get some things to work with instructions from 5,1 Macbook Pro (mainly Keyboard LEDs, right click on touchpad), but I'm a bit reluctant to try the sound patch that's described there, since I don't know if I'm on the same sound hardware.

I tried the [alternate solution](http://ubuntuforums.org/showthread.php?p=6589810#post6589810) the article links to, which seems to install Alsa 1.20, but this doesn't work. Right after the script is executed I seem to have alsa running, aplay -l produces output regarding a built-in nvidia HD soundcard (which I can quote if necessary, but I'm sitting on my other PC right now), but I still don't get any sound.

Anything I can do? Could anyone help? Would be highly appreciated.

P.S.
Also having no Page Up/Page Down/Home/End/Insert/Delete keys is a bit annoying... is it possible to tie them to the FN key somehow?

---

### Post by alexmurray on 2009-06-16
> **NorQue said:**
> 
The *sudo dmidecode -s system-product-name* output says *MacBookPro5,5*, so apparently there's no support in the [Mactel Wiki Support Matrix](https://wiki.ubuntu.com/MactelSupportTeam/CommunityHelpPages#Mactel%20Wiki%20Support%20Matrix) yet. 
Looks like you're the first! You should create a new 5,5 page with any info for others to use in the future

> **NorQue said:**
> 
I managed to get some things to work with instructions from 5,1 Macbook Pro (mainly Keyboard LEDs, right click on touchpad), but I'm a bit reluctant to try the sound patch that's described there, since I don't know if I'm on the same sound hardware.

It can't hurt - try and see :)

> **NorQue said:**
> I tried the [alternate solution](http://ubuntuforums.org/showthread.php?p=6589810#post6589810) the article links to, which seems to install Alsa 1.20, but this doesn't work. Right after the script is executed I seem to have alsa running, alsa -l produces output regarding a built-in nvidia HD soundcard (which I can quote if necessary, but I'm sitting on my other PC right now), but I still don't get any sound and alsa -l doesn't produce output after a restart.
Well 1.0.20 doesn't contain any of the needed driver mods for the MBP5,1 so I am not surprised it doesn't work :)

> **NorQue said:**
> Also having no Page Up/Page Down/Home/End/Insert/Delete keys is a bit annoying... is it possible to tie them to the FN key somehow?
they already are tied to fn on the MBP5,1 as:
```

PageUp ->  Fn+Up
PageDown -> Fn+Down
Home -> Fn+Left
End -> Fn+Right
Insert -> Fn+Enter
Delete -> Fn+Backspace

```

---

### Post by cyberdork33 on 2009-06-16
> **NorQue said:**
> *sudo dmidecode -s system-product-name* output says *MacBookPro5,5*

Interesting... that means there is a 5,3 and 5,4 out there too, and I am guessing they are the 15" and 17" new releases...

Here is the bug on the ACPI thing:
[https://bugs.edge.launchpad.net/mactel-support/+bug/341230](https://bugs.edge.launchpad.net/mactel-support/+bug/341230)

I second trying the patch for the other 5,x models.

---

### Post by NorQue on 2009-06-16
> **alexmurray said:**
> Looks like you're the first! You should create a new 5,5 page with any info for others to use in the futureDon't really know what to write there besides copying the 5,1 article, since I haven't exactly accomplished very much and I'm not really the biggest Linux expert (despite my two year of usage... it's nice that usually everything just works out of the box without a lot of problems and when there are any they are solved easily most of the time ;) ).
> **alexmurray said:**
> It can't hurt - try and see :)> **cyberdork33 said:**
> I second trying the patch for the other 5,x models.Tried the 5,1 patch now, but it doesn't work. :( There anything I can do besides writing my own driver? Any info that's needed? Any output I can post that may help someone who might be interested in helping out? Or to find out if it's even just a layer 8 problem?
> **alexmurray said:**
> they already are tied to fn on the MBP5,1 as:
```

PageUp ->  Fn+Up
PageDown -> Fn+Down
Home -> Fn+Left
End -> Fn+Right
Insert -> Fn+Enter
Delete -> Fn+Backspace

```Thanks a bunch, that helped a lot. :)

---

### Post by alexmurray on 2009-06-16
As far as audio goes if you could post the output of ```
cat /proc/asound/card0/codec#0
``` then I can try have a look for you, although I still don't completely understand all the hda audio stuff - the best person to contact would be Kacper who wrote the patch for the MB[P]5,1 - his email address is on the wiki page which has the patch - and if you email him the contents of /proc/asound/card0/codec#0 and tell him you are trying to get your MBP5,5 working he may be able to write a patch for you if you're lucky ;)

---

### Post by cyberdork33 on 2009-06-16
yea it is purely about adding the capability to alsa I am afraid.

---

### Post by NorQue on 2009-06-17
```
cat /proc/asound/card0/codec#0
```says:```
Codec: Generic 1013 ID 4206
Address: 0
Vendor Id: 0x10134206
Subsystem Id: 0x106b4d00
Revision Id: 0x100301
No Modem Function Group found
Default PCM:
    rates [0x7f0]: 32000 44100 48000 88200 96000 176400 192000
    bits [0x1e]: 16 20 24 32
    formats [0x3]: PCM FLOAT
Default Amp-In caps: N/A
Default Amp-Out caps: N/A
GPIO: io=4, o=0, i=0, unsolicited=0, wake=0
  IO[0]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
  IO[1]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
  IO[2]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
  IO[3]: enable=1, dir=1, wake=0, sticky=0, data=0, unsol=0
Node 0x02 [Audio Output] wcaps 0xd041d: Stereo Amp-Out
  Amp-Out caps: ofs=0x73, nsteps=0x7f, stepsize=0x01, mute=1
  Amp-Out vals:  [0xf3 0xf3]
  Converter: stream=0, channel=0
  PCM:
    rates [0x7f0]: 32000 44100 48000 88200 96000 176400 192000
    bits [0x1e]: 16 20 24 32
    formats [0x3]: PCM FLOAT
  Power: setting=D0, actual=D0
  Delay: 13 samples
Node 0x03 [Audio Output] wcaps 0xd041d: Stereo Amp-Out
  Amp-Out caps: ofs=0x73, nsteps=0x7f, stepsize=0x01, mute=1
  Amp-Out vals:  [0x5c 0x5c]
  Converter: stream=0, channel=0
  PCM:
    rates [0x7f0]: 32000 44100 48000 88200 96000 176400 192000
    bits [0x1e]: 16 20 24 32
    formats [0x3]: PCM FLOAT
  Power: setting=D0, actual=D0
  Delay: 13 samples
Node 0x04 [Audio Output] wcaps 0xd041d: Stereo Amp-Out
  Amp-Out caps: ofs=0x73, nsteps=0x7f, stepsize=0x01, mute=1
  Amp-Out vals:  [0xf3 0xf3]
  Converter: stream=0, channel=0
  PCM:
    rates [0x7f0]: 32000 44100 48000 88200 96000 176400 192000
    bits [0x1e]: 16 20 24 32
    formats [0x3]: PCM FLOAT
  Power: setting=D0, actual=D0
  Delay: 13 samples
Node 0x05 [Audio Input] wcaps 0x18051b: Stereo Amp-In
  Amp-In caps: ofs=0x33, nsteps=0x3f, stepsize=0x03, mute=1
  Amp-In vals:  [0x0c 0x0c] [0x0c 0x0c]
  Converter: stream=0, channel=0
  SDI-Select: 0
  PCM:
    rates [0x1f5]: 8000 16000 32000 44100 48000 88200 96000
    bits [0x1e]: 16 20 24 32
    formats [0x3]: PCM FLOAT
  Power: setting=D0, actual=D0
  Delay: 8 samples
  Connection: 2
     0x0c* 0x12
Node 0x06 [Audio Input] wcaps 0x18051b: Stereo Amp-In
  Amp-In caps: ofs=0x33, nsteps=0x3f, stepsize=0x03, mute=1
  Amp-In vals:  [0x38 0x38] [0x38 0x38]
  Converter: stream=0, channel=0
  SDI-Select: 0
  PCM:
    rates [0x1f5]: 8000 16000 32000 44100 48000 88200 96000
    bits [0x1e]: 16 20 24 32
    formats [0x3]: PCM FLOAT
  Power: setting=D0, actual=D0
  Delay: 8 samples
  Connection: 2
     0x0d* 0x0e
Node 0x07 [Audio Input] wcaps 0x180791: Stereo Digital
  Converter: stream=0, channel=0
  SDI-Select: 0
  Digital: Preemphasis Copyright
  Digital category: 0x0
  PCM:
    rates [0x570]: 32000 44100 48000 96000 192000
    bits [0x1e]: 16 20 24 32
    formats [0x7]: PCM FLOAT AC3
  Unsolicited: tag=00, enabled=0
  Power: setting=D0, actual=D0
  Delay: 8 samples
  Connection: 1
     0x0f
Node 0x08 [Audio Output] wcaps 0x40611: Stereo Digital
  Converter: stream=0, channel=0
  Digital:
  Digital category: 0x0
  PCM:
    rates [0x7f0]: 32000 44100 48000 88200 96000 176400 192000
    bits [0x1e]: 16 20 24 32
    formats [0x7]: PCM FLOAT AC3
  Power: setting=D0, actual=D0
  Delay: 4 samples
Node 0x09 [Pin Complex] wcaps 0x410581: Stereo
  Pincap 0x0000001c: OUT HP Detect
  Pin Default 0x012b4030: [Jack] HP Out at Ext Rear
    Conn = Comb, Color = Green
    DefAssociation = 0x3, Sequence = 0x0
  Pin-ctls: 0x00:
  Unsolicited: tag=00, enabled=0
  Power: setting=D0, actual=D0
  Delay: 1 samples
  Connection: 1
     0x02
Node 0x0a [Pin Complex] wcaps 0x410581: Stereo
  Pincap 0x00000054: OUT Detect Balanced
  Pin Default 0x90100121: [Fixed] Speaker at Int N/A
    Conn = Unknown, Color = Unknown
    DefAssociation = 0x2, Sequence = 0x1
    Misc = NO_PRESENCE
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=00, enabled=0
  Power: setting=D0, actual=D0
  Delay: 1 samples
  Connection: 1
     0x03
Node 0x0b [Pin Complex] wcaps 0x410101: Stereo
  Pincap 0x00000050: OUT Balanced
  Pin Default 0x90100120: [Fixed] Speaker at Int N/A
    Conn = Unknown, Color = Unknown
    DefAssociation = 0x2, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x00:
  Delay: 1 samples
  Connection: 1
     0x04
Node 0x0c [Pin Complex] wcaps 0x41048b: Stereo Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00]
  Pincap 0x00000024: IN Detect
  Pin Default 0x400000f0: [N/A] Line Out at Ext N/A
    Conn = Unknown, Color = Unknown
```Well, I guess asking Kacper for help certainly can't hurt, I'll send him a mail later.

Purely out of curiosity, is there /proc/asound/card0/codec#0 output for a Macbook 5,1 to compare somewhere?

---

### Post by dman777 on 2009-06-17
Is this a completely new sound card on the market? If not, alsa should support this already. I am willing to bet this is a config issue. It is best to disable Alsa in the kernel completely, and install it externally(the latest). Also, make sure when it is installed you have the compile option for your sound card model. Make sure you have alsa tools installed also. In Gentoo when it installs, the script installs alsa and as a module. I don't know how it would install with rpm or apt-get. Do this, stay in root and do a aplay -l. Create a .asoundrc in your user home directory(this means in /root and /home/user_name. It should look like what I posted in the bottom. Use the output from aplay -l to match what the card name and device name in .asoundrc.It it said that the .asoundrc file is not needed. But in some cases I have found it is. If you run out of options, it won't hurt to try this. 

> pcm.!default {
	type hw
	card 0
        device 0
}

ctl.!default {
	type hw           
	card 0
        device 0
}


---

### Post by alexmurray on 2009-06-17
sorry dman777 but you are getting way too ahead of yourself - by the looks of the output the vendor id is not even recognised, and the chipset seems quite different to that of the MBP5,1 so I would doubt this is going to work - besides the OP already tried alsa-driver-1.0.20 from source and it didn't work.

You can find a bunch of versions of the output for the MBP5,1 at the launchpad bug [https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/337314](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/337314)

Just to confirm -can you try using the MBP5,1 patch but make you manually specify to use the mb5 model by adding the following line to /etc/modprobe.d/options

```
options snd_hda_intel model=mb5
```

And then try rebooting... I doubt this will work but you never know

---

### Post by NorQue on 2009-06-17
That .asoundrc didn't work, unfortunately. aplay -l says```
card 0: NVidia [HDA NVidia], device 0: HDA Generic [HDA Generic]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```so a direct cut'n'paste of what you wrote should've worked, shouldn't it? (with card and device both being 0)

After installing alsa 1.0.20 from [this]("http://ubuntuforums.org/showthread.php?p=6589810#post6589810") script again I can now select it in alsaconf as *hda-intel nVidia Corporation MCP79 High Definition Audio (rev b1)*. Unfortunately alsamixer now always quits with *alsamixer: function snd_ctl_open failed for default: Invalid argument*. I also found specific instructions on how to compile alsa for this card on the [alsa homepage]("http://www.alsa-project.org/main/index.php/Matrix:Module-hda-intel"), I'll give this a try next.

[EDIT]
Sorry, alexmurray, you posted while I wrote my own post, didn't see it before hitting save. Does it make sense to try to compile alsa for hda-intel before dabbling with that patch again?

[EDIT #2]
Instructions from alsa didn't work, either. Going to try alexmurrays suggestion now...

[EDIT #3]
So frustrating. I compiled 1.0.19 again, created a file "options" in /etc/modprobe.d/ and added that line, but still no sound. :(

---

### Post by NorQue on 2009-06-18
Bump due to update in first post.

---

### Post by crocowhile on 2009-06-18
I got the same MBP just yesterday. I have been ubuntu users for few years now and I'd rather keep using that. Did you encounter any other problem?

I am quite amazed by how MacOSX is handling the battery life (7 hours is wow) and the suspend/resume routine (you open the lid and it's just ON!); how do these two compare under Ubuntu? Can anyone make a comment?

---

### Post by NorQue on 2009-06-18
> **crocowhile said:**
> I got the same MBP just yesterday. I have been ubuntu users for few years now and I'd rather keep using that. Did you encounter any other problem?

I am quite amazed by how MacOSX is handling the battery life (7 hours is wow) and the suspend/resume routine (you open the lid and it's just ON!); how do these two compare under Ubuntu? Can anyone make a comment?So far I haven't really used it yet, sorry. Suspend, hibernate and restart all don't work for me, so unlike OS X you have to shut it completely off each time you stop using it with Ubuntu. Can't comment on battery yet as I haven't used it without power supply so far.

It surely is one of the best quality pieces of hardware that I've come across so far, though, that's why I bought it right after release, since I've been considering getting the "old" 13" unibody MacBook for quite a while anyways.

---

### Post by crocowhile on 2009-06-19
I have installed 9.04 and of course I have the same problem.

Other things that do not work despite using the mactel ppa are:

*brightness of the screen:*
cannot be regulated in any way: no applet, no keys, no automatic
also pommed doesn't work (version 1.25) as it complaints that the macbook is unknow.

*suspend / resume / restart*
none of them works. Only shutdown does.

*nvidia 180*
makes compiz crash. 173 works

other things seem to work.
If you or anybody else find something new please update.

---

### Post by bcpnikhil on 2009-06-19
> **crocowhile said:**
> I have installed 9.04 and of course I have the same problem.

Other things that do not work despite using the mactel ppa are:

*brightness of the screen:*
cannot be regulated in any way: no applet, no keys, no automatic
also pommed doesn't work (version 1.25) as it complaints that the macbook is unknow.

*suspend / resume / restart*
none of them works. Only shutdown does.

*nvidia 180*
makes compiz crash. 173 works

other things seem to work.
If you or anybody else find something new please update.

Granted I'm using Gentoo with 2.6.30, so my information may not be the most applicable, but nvidia 185.18.14 works really well with compiz for me. Try compiling and installing them.

I'm having issues with sound too, as well as suspend, resume, and restart, so no help there unfortunately.

Install nvclock to control screen brightness.

---

### Post by rebanador on 2009-06-20
+1. I'm having exactly the same problem with sound as you people.

My outputs look exactly like the OP's, and did pretty much the same as him (options, new alsa, etc).

Looking forward to get the sound working!

---

### Post by crocowhile on 2009-06-22
Some update:

nvidia drivers 185.x.x work nicely
the deb package can be find at this ppa
[https://launchpad.net/~thefirstm/+archive/ppa](https://launchpad.net/~thefirstm/+archive/ppa)

nvclock works for changing screen brightness but a better way is to install
nvidia_bl_dkms from the mactel repository
[https://launchpad.net/~mactel-support/+archive/ppa](https://launchpad.net/~mactel-support/+archive/ppa)
adding the line
nvidia_bl 
to the file /etc/modules

This way screen brightness can be controlled through the F keys and also will adjust automatically with the light sensor. If you are not happy with the automatic adjustament you can customize values in gconf-editor apps/gnome-power-manager/ambient

The touchpad works but tapping doesn't work out of the box. You need to configure certain variables using synclient. In my case I changed 
synclient TapButton1=1
synclient TapButton2=2
synclient TapButton3=3
synclient PalmDetect=1
synclient VertEdgeScroll=0

more later

---

### Post by e-dard on 2009-06-25
> **crocowhile said:**
> I have installed 9.04 and of course I have the same problem.

Other things that do not work despite using the mactel ppa are:

*brightness of the screen:*
cannot be regulated in any way: no applet, no keys, no automatic
also pommed doesn't work (version 1.25) as it complaints that the macbook is unknow.

Hi guys,

I have one of the 5,5's.  However, I don't use Ubuntu, I use Arch Linux.

Just to let you know, I emailed the pommed author and sent him some output so he could update pommed for the new 13" Macbook Pro.  You can download the source for the updated version (1.27) from the git repository [here]("http://git.debian.org/?p=pommed/pommed.git;a=snapshot;h=refs/heads/master;sf=tgz").

Hope that helps.

---

### Post by Leftmost Cat on 2009-06-25
OP, have you emailed Kacper regarding this? If so, have you received any reply?

---

### Post by Gyroscope352 on 2009-06-25
Hey guys, there's a lot of talk on this thread about the 5,5 (13" pro), but does anyone know if this also applies to the new 15" (that is, the 5,3)? Because that is what I have and I'm not getting any sound either. I'm going to assume the problems with the 5,5 will carry over to the other new ones as well, unless someone tells me that a solution already exists.

---

### Post by NorQue on 2009-06-26
> **Leftmost Cat said:**
> OP, have you emailed Kacper regarding this? If so, have you received any reply?Sorry, no, didn't do so. With all the other issues I chose to wait till 9.10 to give Ubuntu on 5,5 another try.

I hope I don't sound like an a**, but with all the issues I decided it's not worth it wasting more time on getting everything to work, especially since I won't be of any more help as to "complain" about non-working functions.

---

### Post by alexmurray on 2009-06-26
But if you don't file bugs / make some noise about problems how do you expect them to get fixed unless you are going to fix it yourself. You cant assume others are aware of the problems you've got and they will magically be fixed - unless someone writes a patch for the ALSA driver and it gets included in the 2.6.31 kernel (which Ubuntu 9.10 will ship with) then I can pretty much guarantee this wont work for you in 9.10 either.

---

### Post by Gyroscope352 on 2009-06-27
alexmurray's right, Nor. This is how Linux works. If you didn't want to fix the problem, it would have been helpful to let us know so we could fix the problem.

I'll e-mail Kacper, guys. Just let me mess around fro an hour with this sound to make sure all the available solutions really aren't working, and I'll let him know.

EDIT: alright, I've e-mailed him. Let's hope he's feeling generous.

---

### Post by Gyroscope352 on 2009-06-27
> **e-dard said:**
> Hi guys,

I have one of the 5,5's.  However, I don't use Ubuntu, I use Arch Linux.

Just to let you know, I emailed the pommed author and sent him some output so he could update pommed for the new 13" Macbook Pro.  You can download the source for the updated version (1.27) from the git repository [here]("http://git.debian.org/?p=pommed/pommed.git;a=snapshot;h=refs/heads/master;sf=tgz").

Hope that helps.

I know I'm a total noob, but how do I install this from the source?

---

### Post by bobbytables on 2009-06-27
since this is cleary not-yet-supported hardware i sent a report to alsa-dev:

[http://article.gmane.org/gmane.linux.alsa.devel/64346](http://article.gmane.org/gmane.linux.alsa.devel/64346)

---

### Post by Leftmost Cat on 2009-06-27
Looking into the backlight, I don't believe the linked fix in pommed is going to do anything. (Please correct me if I'm wrong.) I've hacked together a HAL-based fix that should make it work for those who use GNOME and the like. This isn't an ideal solution, and it looks like some extra work is needed in the kernel for a more permanent fix, but here's the stopgap.

First, install the smartdimmer package.

If you aren't using karmic with the latest HAL update, apply the following patch in /usr/lib/hal:
```
Index: hal-0.5.12+git20090626/tools/linux/hal-system-lcd-get-brightness-linux
===================================================================
--- scripts/linux/hal-system-lcd-get-brightness-linux	2008-11-27 19:11:38.000000000 +0100
+++ scripts/linux/hal-system-lcd-get-brightness-linux	2009-06-26 09:55:55.000000000 +0200
@@ -23,6 +23,15 @@
 		exit 1
 	fi
 	exit ${value}
+elif [ "$HAL_PROP_LAPTOP_PANEL_ACCESS_METHOD" = "sony-nvidia" ]; then
+	# smartdimmer -g
+	value=$(( $(smartdimmer -g | awk '{print $3;}') - 15 ))
+	if [ $? -ne 0 ]; then
+		echo "org.freedesktop.Hal.Device.LaptopPanel.NotSupported" >&2
+		echo "smartdimmer -g returned != 0" >&2
+		exit 1
+	fi
+	exit ${value}
 fi
 
 # Check for file existance and that it's readable
Index: hal-0.5.12+git20090626/tools/linux/hal-system-lcd-set-brightness-linux
===================================================================
--- scripts/linux/hal-system-lcd-set-brightness-linux	2008-11-27 19:11:38.000000000 +0100
+++ scripts/linux/hal-system-lcd-set-brightness-linux	2009-06-26 09:55:55.000000000 +0200
@@ -23,6 +23,15 @@
 		exit 1
 	fi
 	exit 0
+elif [ "$HAL_PROP_LAPTOP_PANEL_ACCESS_METHOD" = "sony-nvidia" ]; then
+	# -s  --set <level>	Set brightness level (15-100)
+	smartdimmer -s "$(( $value + 15 ))"
+	if [ $? -ne 0 ]; then
+		echo "org.freedesktop.Hal.Device.LaptopPanel.NotSupported" >&2
+		echo "smartdimmer -s returned != 0" >&2
+		exit 1
+	fi
+	exit 0
 fi
 
 # Check for file existance and that it's writable
```

Create a .fdi file containing the following in /etc/hal/fdi/policy (name does not matter):
```
<?xml version="1.0" encoding="UTF-8"?>

<deviceinfo version="0.2">
  <device>
    <match key="system.kernel.name" string="Linux">
      <match key="system.hardware.vendor" contains="Apple">
        <match key="system.hardware.product" string="MacBookPro5,5">
          <spawn udi="/org/freedesktop/Hal/devices/mbp_backlight"/>
        </match>
      </match>
    </match>
  </device>
  <device>
    <match key="info.udi" string="/org/freedesktop/Hal/devices/mbp_backlight">
      <append key="info.capabilities" type="strlist">laptop_panel</append>
      <merge key="info.category" type="string">laptop_panel</merge>
      <merge key="info.product" type="string">MacBook Pro Backlight Control</merge>
      <merge key="laptop_panel.access_method" type="string">sony-nvidia</merge>
      <merge key="laptop_panel.num_levels" type="int">86</merge>
      <append key="info.interfaces" type="strlist">org.freedesktop.Hal.Device.LaptopPanel</append>
      <append key="org.freedesktop.Hal.Device.LaptopPanel.method_names" type="strlist">SetBrightness</append>
      <append key="org.freedesktop.Hal.Device.LaptopPanel.method_signatures" type="strlist">i</append>
      <append key="org.freedesktop.Hal.Device.LaptopPanel.method_argnames" type="strlist">brightness_value</append>
      <append key="org.freedesktop.Hal.Device.LaptopPanel.method_execpaths" type="strlist">hal-system-lcd-set-brightness</append>

      <append key="org.freedesktop.Hal.Device.LaptopPanel.method_names" type="strlist">GetBrightness</append>
      <append key="org.freedesktop.Hal.Device.LaptopPanel.method_signatures" type="strlist"></append>
      <append key="org.freedesktop.Hal.Device.LaptopPanel.method_argnames" type="strlist"></append>
      <append key="org.freedesktop.Hal.Device.LaptopPanel.method_execpaths" type="strlist">hal-system-lcd-get-brightness</append>
    </match>
  </device>
</deviceinfo>
```

Let me know how this works for you. It's a dirty, dirty hack, but it gives me some control over backlight, including gnome-power-manager's automatic dimming when on battery.

---

### Post by crocowhile on 2009-06-28
LEftmost cat, is it the LCD backlight you are talking about? Cause I found that works ok without major hacks. Just install the nvidia_bl_dkms package from the mactel repository and make sure it loads by calling it from /etc/modules

The ambient feature also will work from gnome this way (you may want to change polling frequency to something lower than 30 seconds and adjust the correction factors to your taste using gconf-editor).

The keyboard backlight, OTOH, that doesn't seem to work with ambient yet.

Thanks for submitting the ALSA bug, btw. Did anybody manage to fix the restart/suspend/resume yet? I have read it may have something to do with rEFIt actually.

---

### Post by bobbytables on 2009-06-28
i'm actually using gentoo and have _no_ problem whatsoever with standby or hibernate.  only reboot is still not working, the other two things worked out of the box.

sources are 2.6.30 vanilla, nvidia in version 180.60 and xorg-server 1.6.1.901-r4

standby times are 5 seconds for wakeup and about 2-3 seconds to go to sleep. hibernate of course takes longer.

---

### Post by e-dard on 2009-06-28
> **Gyroscope352 said:**
> I know I'm a total noob, but how do I install this from the source?

Sorry, I have no idea.  On Arch it is incredibly easy to install a source archive as a package (one of the main advantages of Arch).  You could look in the package and compile it yourself from source and then put the various files in the right places.

> **Leftmost Cat said:**
> Looking into the backlight, I don't believe the linked fix in pommed is going to do anything.

Correct (if you are referring to the LCD backlight).  I have installed nvclock for the moment, in order to control the backlight manually.

> **crocowhile said:**
> 
The keyboard backlight, OTOH, that doesn't seem to work with ambient yet.

Using the previously linked pommed will allow you to control the keyboard backlight using the correct keys.  It *is* ambient sensitive, and will turn on and off at certain light thresholds.

---

### Post by Gyroscope352 on 2009-06-28
> **crocowhile said:**
> LEftmost cat, is it the LCD backlight you are talking about? Cause I found that works ok without major hacks. Just install the nvidia_bl_dkms package from the mactel repository and make sure it loads by calling it from /etc/modules


Thanks for this. This was one of the things I hadn't gotten yet.

> **bobbytables said:**
> 
sources are 2.6.30 vanilla, nvidia in version 180.60 and xorg-server 1.6.1.901-r4


I'm sorry, what? Are these packages or something we need to install? Because I could really use these working too.

And, of course, we're all still waiting on sound which to me is the biggest issue. At least now Kacper and Alsa are aware of the problem, and hopefully we can get a fix soon.

---

### Post by bobbytables on 2009-06-29
> **Gyroscope352 said:**
> Thanks for this. This was one of the things I hadn't gotten yet.

I'm sorry, what? Are these packages or something we need to install? Because I could really use these working too.


those are simply the version names of my currently installed software. 
i have "kernel26" in version 2.6.30 (vanilla-sources is simply the name in gentoo for linus torvalds' kernel, without any extra patches) and my nvidia-drivers are of version 180.60

i believe the xorg-server in ubuntu is of a less-recent version, but i'd probably just wait for it to be updated by apt.

---

### Post by Gyroscope352 on 2009-06-29
> **bobbytables said:**
> those are simply the version names of my currently installed software. 
i have "kernel26" in version 2.6.30 (vanilla-sources is simply the name in gentoo for linus torvalds' kernel, without any extra patches) and my nvidia-drivers are of version 180.60

i believe the xorg-server in ubuntu is of a less-recent version, but i'd probably just wait for it to be updated by apt.

Yeah, I'll just do that. Sounds like more trouble than it's worth at this point for me to figure out what I need to make it work.

---

### Post by FALKER on 2009-06-29
> **Gyroscope352 said:**
> Yeah, I'll just do that. Sounds like more trouble than it's worth at this point for me to figure out what I need to make it work.

You could upgrade to 9.10 alpha, it uses 2.6.30. Although its not always stable.
You could also try [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30/) and [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.31-rc1/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.31-rc1/)

---

### Post by crocowhile on 2009-06-30
> **bobbytables said:**
> i'm actually using gentoo and have _no_ problem whatsoever with standby or hibernate.  only reboot is still not working, the other two things worked out of the box.

sources are 2.6.30 vanilla, nvidia in version 180.60 and xorg-server 1.6.1.901-r4

standby times are 5 seconds for wakeup and about 2-3 seconds to go to sleep. hibernate of course takes longer.

mmmh. I tried the 2.6.30: didn't help.
My nvidia version is 185.18.14 but neither 173.* nor 180.* made any difference. Ubuntu 9.04 ships with Xorg 1.6.0 but I doubt that is involved. I really don't know what it could be. Some people say has to do with bios-emulation in rEFIt but I believe rEFIt  is already starting in legacy mode (if not, I could not find how to force that anyway).

---

### Post by bobbytables on 2009-07-06
hey folks,

so we, .. well takashi iwai, made some major headway 

and digital-out works :) .. however analog still doesn't.

if digital is enough for you, go grab his latest unstable snapshot:

[ftp://ftp.kernel.org/pub/linux/kernel/people/tiwai/snapshot/alsa-driver-unstable-snapshot.tar.gz](ftp://ftp.kernel.org/pub/linux/kernel/people/tiwai/snapshot/alsa-driver-unstable-snapshot.tar.gz)

now when you unmute IEC958, you'll notice that the red light in your line-out starts to glow ;)


i'll get back to you, when there's more to tell.

---

### Post by bobbytables on 2009-07-06
w000000000000000000000t


okay i get sound =) via built-in speakers. .. right now it's by using hda-verb etc... it's kind of a hustle.

just saying: sit tight, there'll be a solution in a bit =)

---

### Post by mrtekkid on 2009-07-07
So I am guessing that the new Unibody Macbook Pro 15" from like Mid 2009 does not have sound supported yet? 

I read this thread and I am a major Ubuntu noob and I definitely do not know a thing about compiling or installing files.... and I have no sound... but I did download that unstable file thing but I do not know what to do with it... 

if there's no sound for my Ubuntu installation for my Mac... I'll uninstall it and go back to Mac only.... atleast that works....

---

### Post by bobbytables on 2009-07-07
> **mrtekkid said:**
> So I am guessing that the new Unibody Macbook Pro 15" from like Mid 2009 does not have sound supported yet?
it would be good to know if it is using the same chip. 
do this in a shell: 
```

sudo lspci  |grep -i Audio

```
and see if it returns:
"Audio device: nVidia Corporation MCP79 High Definition Audio (rev b1)"
if so - you might be good to go, as soon as the drivers will be out (which should be soon). if it's a different string, please post it, and, if you're interested, we can then try to figure out how we'd get that to work.

> **mrtekkid said:**
> 
I read this thread and I am a major Ubuntu noob and I definitely do not know a thing about compiling or installing files.... and I have no sound... but I did download that unstable file thing but I do not know what to do with it... 
it's actually not _that_ complicated..
i don't run Ubuntu, so there might be additional steps to remove the old drivers etc.
however, i bet somebody in this forum will be able to tell you how to get it up and running, once there is a tarball

> **mrtekkid said:**
> if there's no sound for my Ubuntu installation for my Mac... I'll uninstall it and go back to Mac only.... atleast that works....
whatever floats your boat .. if you're note enjoying free software (for it's several reasons), you might be wrong here after all.
it's simply pointless to make such a threat - nothing good comes from this.

---

### Post by bobbytables on 2009-07-07
i got a question actually:

all of those ubuntu users who also have the A1156 - Apple Remote:

when you run "xev" and you start hitting buttons on your remote (while obviously pointing it to the IR-receiver), do you get keystroke-events?

if so, can you do a lsmod | grep -i IR   and paste the content? thanks.

---

### Post by crocowhile on 2009-07-07
> **bobbytables said:**
> i'm actually using gentoo and have _no_ problem whatsoever with standby or hibernate.[...]

standby times are 5 seconds for wakeup and about 2-3 seconds to go to sleep. hibernate of course takes longer.

Are you using compiz by any chance? Looking forward to trying the new alsa modules, btw. Thanks for taking care of this together with the alsa dudes.

---

### Post by bobbytables on 2009-07-07
> **crocowhile said:**
> Are you using compiz by any chance? 

Well not 'compiz',  but yes: my kwin is using compositing. so yeah - alpha-channel and wobbly windows, and exposé and all that jazz. ;)  works perfectly.

> **crocowhile said:**
> Thanks for taking care of this together with the alsa dudes.
you're welcome :)  although thanks should really go to Takashi Iwai - he's the brains.

---

### Post by bobbytables on 2009-07-07
completely forgot to tell you guys:

takashi fixed it as far as this:
[COLOR="SeaGreen"][SIZE="3"]- digital out works ootb[/SIZE]
[SIZE="4"]- built-in speakers work TOO!!!!!!!!!!!! :D :D :D 
- even "surround" seems to be an extra speaker in the mbp and mute-switch and volume control work =)[/SIZE][/COLOR]

the only thing missing is: getting some sound out the analog-jack and also disabling speakers once headphones are plugged in.. so for now: "only" built-ins.  this is ******* awesome though of course :)

[COLOR="Red"][SIZE="4"]
the following is for rather experienced users, who sort of know what i'm talking about.[/SIZE][/COLOR]

please can someone make this more userfriendly?
either make a deb or create a guide that will actually apply to 9.04, simply by copy and pasting.

short version, but: this COULD break some stuff in your system.. i have _no_ idea what precautions to take with ubuntu!

you'll need kernel-sources or headers i think (in gentoo both are installed by default)
---------------------------
get rid of the old alsa-modules..
in my case that's: 
```

cd /lib/modules/`uname -r`/kernel/
rm sound/ -r

```
however your directory could be different.. maybe try to find out where the alsa-stuff is, with:
```

cd /lib/modules/`uname -r`/
find . -name "*hda*"

```

once deleted:

get:
[ftp://ftp.kernel.org/pub/linux/kernel/people/tiwai/snapshot/alsa-driver-unstable-snapshot.tar.gz](ftp://ftp.kernel.org/pub/linux/kernel/people/tiwai/snapshot/alsa-driver-unstable-snapshot.tar.gz)

```

tar xf alsa-driver-unstable-snapshot.tar.gz
cd alsa-driver-unstable
./configure --enable-dynamic-minors  --without-oss --with-cards="hda-intel"  && make && sudo make install

```

.. you could start unloading every module with "snd" from lsmod, with rmmod, like this:
```

# lsmod
snd-hda-intel
snd-hda
....

```

so you'd do: sudo rmmod snd-hda-intel   etc.. but they have dependencies, so you might be better of to simply restart.
if you did it by hand, do: modprobe snd-hda-intel.
after that, alsamixer should show "Cirrus Logic" and as soon as you unmute the channels you'll get sound =)

---

### Post by mrtekkid on 2009-07-08
> **bobbytables said:**
> it would be good to know if it is using the same chip. 
do this in a shell: 
```

sudo lspci  |grep -i Audio

```and see if it returns:
"Audio device: nVidia Corporation MCP79 High Definition Audio (rev b1)"
if so - you might be good to go, as soon as the drivers will be out (which should be soon). if it's a different string, please post it, and, if you're interested, we can then try to figure out how we'd get that to work.


it's actually not _that_ complicated..
i don't run Ubuntu, so there might be additional steps to remove the old drivers etc.
however, i bet somebody in this forum will be able to tell you how to get it up and running, once there is a tarball


whatever floats your boat .. if you're note enjoying free software (for it's several reasons), you might be wrong here after all.
it's simply pointless to make such a threat - nothing good comes from this.

That is the chip that shows up by the way. So basically there is a fix on the way then that is not out yet? IS that what you are telling me?

It wasn't a threat... I am just slightly frustrated... look at it this way... why use an operating system that half works when I can use another one that I am more comfortable with that fully works? 

I am trying to open my mind to the so called wonders that is Ubuntu... took most of the day to partition partition the drive correctly and boot right .... so I am obviously interested in in this OS.... but I'm not to keen on the shell commands...so when people start tossing around commands like it's everyday talk.... that's when I get lost....it's not everyday talk for me.

---

### Post by bobbytables on 2009-07-08
> **mrtekkid said:**
> That is the chip that shows up by the way. So basically there is a fix on the way then that is not out yet? IS that what you are telling me?
as stated in my more recent posts: there is a fix. eventhough it takes some manual labour.
however maybe someone involved in this thread can make a little manual how to do it right on ubuntu.

> **mrtekkid said:**
> 
It wasn't a threat... I am just slightly frustrated...

oh don't get me wrong, i wasn't threatened. i'm just saying it's pointless to state it.
> **mrtekkid said:**
> look at it this way... why use an operating system that half works when I can use another one that I am more comfortable with that fully works? 
that is a question i'm tired of answering, and it really does not belong here anyways.
if you can't answer that for yourself, then maybe you should use OS X.
However, all that glistens is not gold.
yes - it has a high usability and is ever so pretty.
no - you can't just go ahead and change the way a certain .app behaves under certain circumstances,
and unless you get Apple to do it for you, you're pretty much ******.
in a open source world, if you can't change it, maybe some buddy of yours can or already has or someone else you don't even know has a patch for that, or you simply get in contact with the actual developer,

instead of some call-center-dude who will then 
while (i<10) {
     print "tell it to some his supervisor, who will also ";
     i = i +1
     if (i >9)
         error("problem has been forgotten already");
}



> **mrtekkid said:**
> 
I am trying to open my mind to the so called wonders that is Ubuntu... took most of the day to partition partition the drive correctly and boot right .... so I am obviously interested in in this OS.... but I'm not to keen on the shell commands...so when people start tossing around commands like it's everyday talk.... that's when I get lost....it's not everyday talk for me.

i really wouldn't agree to "the wonder that is Ubuntu", not even "the wonder that is linux",
but: the wonder that is the idea of open source.


so anyways: sit tight. there is a solution. just wait for the good folks to bring it to you with a one-button-click.

---

### Post by hvthao on 2009-07-08
I realized that the microphone is also working too. But the recording level seems to be too low, hardly hear from what you recorded.

---

### Post by Tiega on 2009-07-09
Hi,

Thank you for the great job you do to solve the sound problem on MacBook Pro 5,5 and 5,4.

I can't wait to read a new post everyday telling me that something is fix.....

By the way, I tried to do the same installation as bobbytables (post #42), but unfortunately it seems that I haven't got sound on speaker.... doesn't matter, I can wait for the next fix.

And sometimes after (few hours), I opened a java software (medical software in fact) which produce sound when you click on certain button..... and there was sound !!!!!!

At the moment I'm not able to say why there is sound in this java software and not for the whole system....

Tiega

PS : I don't wait for an answer, this was just my return of experience.
PSS : Sorry for my english, I'm french ;)

---

### Post by dolphinbrain on 2009-07-09
> **bobbytables said:**
> i got a question actually:

all of those ubuntu users who also have the A1156 - Apple Remote:

when you run "xev" and you start hitting buttons on your remote (while obviously pointing it to the IR-receiver), do you get keystroke-events?

if so, can you do a lsmod | grep -i IR   and paste the content? thanks.

I also recently got the 15" MBP and was delighted to see that a sound fix is in the making. Thanks a lot. Well done and keep up the good work!

I have the Apple Remote A1156 and lsmod | grep -i IR gives me:
appleir                13440  0 

I installed all the packages from the Mactel PPA.

I am also attaching the xev outputs for the different buttons on the Apple Remote. Briefly,

|<<           yields keycode 166 (keysym 0x1008ff26, XF86Back)
>>|           yields keycode 167 (keysym 0x1008ff27, XF86Forward)
+             yields key 60 on the 1st press and key 2 on the 2nd press
-             yields key 2 on all presses
middle button yields key 2 on all presses
Menu          yields keycode 147 (keysym 0x1008ff65, XF86MenuKB)

---

### Post by hvthao on 2009-07-09
Finally, the microphone works, and i can record my voice. Trying testing skype now!

---

### Post by Gyroscope352 on 2009-07-09
I love how subscriptions stop sending you notices if you forget to visit the actual thread. I had no idea any of this was going on!

However, I think I'll hold off until I can get sound out of my external speakers too, since they are the speakers I will be using 99% of the time. Until then I'll keep following this thread. Thanks so much bobbytales for hooking us up!

---

### Post by mzbz on 2009-07-09
Hello,

thanks for fixing sound so far!

Since there was also some talk about key bindings ... I configured my functions keys as described here [1], but F11 and F12 don't seem to work anymore - when I press F11, the clipboard contents are pasted, when I press F12 the mouse right click is triggered. Anyone else experiencing this?

[1] [https://help.ubuntu.com/community/MacBookPro5-5/Jaunty#Keyboard](https://help.ubuntu.com/community/MacBookPro5-5/Jaunty#Keyboard)

---

### Post by crocowhile on 2009-07-09
> **bobbytables said:**
> i'm actually using gentoo and have _no_ problem whatsoever with standby or hibernate.  only reboot is still not working, the other two things worked out of the box

bobbytales, could you please send me the .config file that you used to configure the kernel before compilation? I tried the 2.6.30 vanilla on ubuntu 9.04 but still no success.
thanks

---

### Post by bobbytables on 2009-07-09
sure thing:

grab it here:
[http://nutz.unfoog.de/mbp_2.6.30.config](http://nutz.unfoog.de/mbp_2.6.30.config)

however: since i like to make my configs small, maybe this one is either not working with ubuntu. also: if you used mactel-patches, i don't know if they work anymore - i still don't have the apple remote working =(

the other stuff should work though.

i've been meaning to complete the config, but alsa is currently more important, and i'm still trying to fix it

oh speaking of alsa: i couldn't enable my microphone :( .. what did you guys do?!?!?!.. or: where did you test it?

---

### Post by bobbytables on 2009-07-09
also:
it's "bobbytables", not "bobbytales", guys ;)

[http://xkcd.com/327/](http://xkcd.com/327/)

---

### Post by crocowhile on 2009-07-09
> **bobbytables said:**
> since i like to make my configs small, maybe this one is either not working with ubuntu. also: if you used mactel-patches, i don't know if they work anymore - i still don't have the apple remote working =(

Thanks a lot. Let's see how it will works, it's compiling right now.
I don't apply mactel patches. There's a cool PPA repository for ubuntu that does everything in DKMS. Also, I believe the patches date back to 2.6.26

What MBP do you have? The 15"? The 13" doesn't have the IR for the 
remote, does it?

> **bobbytables said:**
> 
oh speaking of alsa: i couldn't enable my microphone :( .. what did you guys do?!?!?!.. or: where did you test it?
You can test it using gnome-sound-recorder. It works with the latest alsa snapshot but there is no boosting and it records at a very low volume. It is still unusable for me.

---

### Post by crocowhile on 2009-07-09
Just found how to get the boost working. From the volume mixer select the "Digital" slider in the "recording" tab. That slider actually seems to control the gain of the mic and you can then get nice and loud input. Still didn't manage to get it working with skype but with gnome-sound-recorder works ok.

---

### Post by dolphinbrain on 2009-07-09
> **mzbz said:**
> Hello,

Since there was also some talk about key bindings ... I configured my functions keys as described here [1], but F11 and F12 don't seem to work anymore - when I press F11, the clipboard contents are pasted, when I press F12 the mouse right click is triggered. Anyone else experiencing this?

[1] [https://help.ubuntu.com/community/MacBookPro5-5/Jaunty#Keyboard](https://help.ubuntu.com/community/MacBookPro5-5/Jaunty#Keyboard)

F11 and F12 work for me: the notification area show volume increase and decrease when I hit the keys. But I didn't install bobbytables' sound solution so far, so I can't tell you if it really works.

However, the keyboard section on the installation instruction mentions this [link]("http://www.rickycampbell.com/swap-fn/") for swapping the Fn key, but it only gives a 404 error. Has anyone done it before and could summarize how to swap the Fn key?

Thanks.

---

### Post by mzbz on 2009-07-10
> **dolphinbrain said:**
> F11 and F12 work for me: the notification area show volume increase and decrease when I hit the keys. But I didn't install bobbytables' sound solution so far, so I can't tell you if it really works.

However, the keyboard section on the installation instruction mentions this [link]("http://www.rickycampbell.com/swap-fn/") for swapping the Fn key, but it only gives a 404 error. Has anyone done it before and could summarize how to swap the Fn key?

Thanks.

I followed the instructions mentioned here under "Permanently / With .conf file":
[https://help.ubuntu.com/community/AppleKeyboard#Ubuntu%209.04%20(Jaunty%20Jakalope)]("https://help.ubuntu.com/community/AppleKeyboard#Ubuntu%209.04%20%28Jaunty%20Jakalope%29")

Afterwards, Fn+F11 and Fn+F12 increase and decrease sound as expected, I tested the new ALSA drivers.

However, "normal" F11 and F12 do not work. When I hit the keys in the Gnome key bindings settings, the key strokes are not even detected ...

---

### Post by dolphinbrain on 2009-07-10
> **mzbz said:**
> I followed the instructions mentioned here under "Permanently / With .conf file":
[https://help.ubuntu.com/community/AppleKeyboard#Ubuntu%209.04%20(Jaunty%20Jakalope)]("https://help.ubuntu.com/community/AppleKeyboard#Ubuntu%209.04%20%28Jaunty%20Jakalope%29")

Thanks that helped a lot!

> 
Afterwards, Fn+F11 and Fn+F12 increase and decrease sound as expected, I tested the new ALSA drivers.

However, "normal" F11 and F12 do not work. When I hit the keys in the Gnome key bindings settings, the key strokes are not even detected ...

If I test the keybindings with xev all normal F-Keys are recognized. If your keys are not recognized then the key bindings are probably missing at the level of the X server. You might want to check if you have a .Xmodmap in your home directory. The syntax is basically

```
keycode NUM KEYNAME
```

where NUM is the number obtained from xev, and KEYNAME is a recognizable name for the X server. In your case, those keynames are simply F1 through F12. See also the manpages for Xmodmap and for xrdb to see how to add your local mapping to the existing ones (i.e. xrdb -merge ~/.Xmodmap)

---

### Post by crocowhile on 2009-07-10
> **bobbytables said:**
> sure thing:
grab it here:I compiled the kernel using your gentoo configuration but didn't make a difference: still no suspend/resume. too bad.

---

### Post by mzbz on 2009-07-10
> **dolphinbrain said:**
> ```
keycode NUM KEYNAME
```where NUM is the number obtained from xev, and KEYNAME is a recognizable name for the X server. In your case, those keynames are simply F1 through F12. See also the manpages for Xmodmap and for xrdb to see how to add your local mapping to the existing ones (i.e. xrdb -merge ~/.Xmodmap)

Thanks already, but this is strange.

I opened a gnome terminal and started xev.

When I hit F10, xev says

```

KeyRelease event, serial 33, synthetic NO, window 0x3000001,
    root 0x13f, subw 0x0, time 2293993, (1214,753), root:(1218,799),
    state 0x0, keycode 76 (keysym 0xffc7, F10), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False
```So far, so good.

When I hit F11, xev says

```

FocusOut event, serial 33, synthetic NO, window 0x3000001,
    mode NotifyNormal, detail NotifyNonlinear
```At the same time, the xev window is deactivated, and the clipboard contents are pasted into the terminal window.

When I hit F12, xev says

```

FocusIn event, serial 33, synthetic NO, window 0x3000001,
    mode NotifyUngrab, detail NotifyAncestor
```At the same time, the xev window is deactivated and a mouse right click is performed, i.e. the context menu is opened where the mouse pointer is.

Any idea??

---

### Post by Gyroscope352 on 2009-07-10
> **bobbytables said:**
> also:
it's "bobbytables", not "bobbytales", guys ;)

[http://xkcd.com/327/](http://xkcd.com/327/)

haha. oops.

---

### Post by rebanador on 2009-07-12
Hi everybody,

I installed the unstable alsa driver as showed in post #42, but no luck. I religiously followed the procedure (didn't go rmmod but just restarted). Back in Ubuntu I tried to execute alsamixer but all I get is:

alsamixer: function snd_ctl_open failed for default: No such file or directory

What could be going wrong?

Thanks!

---

### Post by bobbytables on 2009-07-12
> **rebanador said:**
> alsamixer: function snd_ctl_open failed for default: No such file or directory

What could be going wrong?

Thanks!


hard to say. however there are a few things you can check:

```

sudo lsmod | grep snd

```

if that shows a bunch of lines including snd_hda_intel, the driver got loaded.
see if snd_hda_codec_cirrus is there as well.
if so, the installation-procedure went well and it's hard to tell what's wrong. 

but most likely you wont see snd_hda_codec_cirrus.

if there are no snd-modules, try: sudo modprobe snd-hda-intel


well let's see what you can figure out so far =)

---

### Post by crocowhile on 2009-07-12
I think the upgrade of EFI firmware from OSX (now version 1.7) has solved the sleep/resume issue. Now the machine goes to sleep and resumes w/o problems. Restart still doesn't work, though: it hangs saying "restarting system" and nothing happens. Adding ACPI=force to grub menu.list didn't help.

---

### Post by bobbytables on 2009-07-12
that's actually a good pointer. i also have the new firmware. so that seems to be right.

also: yeah reboot still sucks ;)

---

### Post by rebanador on 2009-07-13
> **bobbytables said:**
> hard to say. however there are a few things you can check:

```

sudo lsmod | grep snd

```

if that shows a bunch of lines including snd_hda_intel, the driver got loaded.
see if snd_hda_codec_cirrus is there as well.
if so, the installation-procedure went well and it's hard to tell what's wrong. 

but most likely you wont see snd_hda_codec_cirrus.


Hi,

```

sudo lsmod | grep snd

```

yields:

```

snd_page_alloc          8996  0

```


> 
if there are no snd-modules, try: sudo modprobe snd-hda-intel

well let's see what you can figure out so far =)


```

sudo modprobe snd-hda-intel

```

```

WARNING: All config files need .conf: /etc/modprobe.d/options, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/options, it will be ignored in a future release.
FATAL: Error inserting snd (/lib/modules/2.6.31-2-generic/kernel/sound/acore/snd.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error running install command for snd
WARNING: Error inserting snd_pcm (/lib/modules/2.6.31-2-generic/kernel/sound/acore/snd-pcm.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting snd_hwdep (/lib/modules/2.6.31-2-generic/kernel/sound/acore/snd-hwdep.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting snd_hda_codec (/lib/modules/2.6.31-2-generic/kernel/sound/pci/hda/snd-hda-codec.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting snd_hda_intel (/lib/modules/2.6.31-2-generic/kernel/sound/pci/hda/snd-hda-intel.ko): Unknown symbol in module, or unknown parameter (see dmesg)


```

AFAIR I simply followed instructions, but it smells like I have done  something stupid here.

Thanks for your time =)

---

### Post by crocowhile on 2009-07-13
> **rebanador said:**
> 
AFAIR I simply followed instructions, but it smells like I have done  something stupid here.
I think the problem is simply that you are using the experimental kernel (2.6.31). I think you should stick with 2.6.28 or 30. Does the wifi even work with the .31?

---

### Post by rebanador on 2009-07-14
> **crocowhile said:**
> I think the problem is simply that you are using the experimental kernel (2.6.31). I think you should stick with 2.6.28 or 30. Does the wifi even work with the .31?

Yes, it does.

The patch shouldn't work with 2.6.31? Will try rebooting into .28 or .30.

---

### Post by marcimat on 2009-07-14
> **rebanador said:**
> Yes, it does.

The patch shouldn't work with 2.6.31? Will try rebooting into .28 or .30.

Hi,

(Please apologize my (fr)english)

I had the same modprobe installation errors yesterday on Ubuntu 9.04 (kernel 2.6.28-generic) when apply the [#42]("http://ubuntuforums.org/showpost.php?p=7578127&postcount=42") suggestion. Resolved by replacing my old /etc/.../kernel/sound directory (I have backuped before the "rm sound/ -r" command) and reinstall alsa without remove the files into the sound directory.

I think you can also copy a last kernel sound directory if you dont have backup.

---

### Post by Mazza558 on 2009-07-15
You know this sound fix, what will I have to do when a better version of the alsa drivers comes along?

---

### Post by rebanador on 2009-07-15
I just tried in .31 and same thing happens (aforementioned errors). If this patch works in .28 it doesn't really help because I still don't have wifi with that kernel - so I won't use it.

So I guess I'll wait for some news =)

---

### Post by barryreid on 2009-07-15
Hi guys..

I picked up my new MacBook Pro "15 yesterday, so I am so glad to find this thread.

I have followed what was done in post #42 but when I run the ./configure command I get the following error:

make[2]: Entering directory `/root/alsa-driver-unstable/usb'
copying file alsa-kernel/usb/usbmidi.c
patching file usbmidi.c
Hunk #2 succeeded at 237 (offset 12 lines).
Hunk #3 succeeded at 261 with fuzz 2 (offset 12 lines).
Hunk #4 FAILED at 354.
Hunk #5 succeeded at 1602 (offset 240 lines).
Hunk #6 succeeded at 1968 (offset 262 lines).
1 out of 6 hunks FAILED -- saving rejects to file usbmidi.c.rej
make[2]: *** [usbmidi.c] Error 1
make[2]: Leaving directory `/root/alsa-driver-unstable/usb'
make[1]: *** [dep] Error 1
make[1]: Leaving directory `/root/alsa-driver-unstable'
make: *** [include/sndversions.h] Error 2

Im running kernel 2.6.28-13-generic on ubuntu 9.04 and i have all the headers installed.

Can anyone tell me what i might be doing wrong?

---

### Post by hvthao on 2009-07-15
That's strange. Mine is Macpro 13 without any error.

---

### Post by hvthao on 2009-07-15
You're right! The new driver has errors (15/07). But 3 days ago, it didn't. Sadly, I deleted the old driver file.

---

### Post by barryreid on 2009-07-15
But correct me if im wrong but the patch and the file its trying to patch are both in the file that was provided in post #42.

So I dont see why this is throwing up an error?

---

### Post by hvthao on 2009-07-15
The file is updated everyday! The last successful time is 13 Jul.

---

### Post by barryreid on 2009-07-16
If someone has the file from the 13th could you please attach it to this thread.

---

### Post by hvthao on 2009-07-16
Good news! The driver released today works fine. Just tested.

---

### Post by barryreid on 2009-07-16
Ok I have just installed the drivers and im still getting nothing... Am I missing something here, is there any other configs that I need to tweak or anything. 

So from fresh install of Ubuntu I load the drivers and it should work?

---

### Post by crocowhile on 2009-07-16
> **barryreid said:**
> Ok I have just installed the drivers and im still getting nothing... Am I missing something here, is there any other configs that I need to tweak or anything. 

So from fresh install of Ubuntu I load the drivers and it should work?

yes but you need to unmute the card and adjust the other volumes? does the headphone jack work with the latest snapshot?

---

### Post by barryreid on 2009-07-16
I think i have messed with too much stuff trying to get this to work.. I think i should do a fresh install, as once i install the new drivers i am not getting any installed devices, just getting the pulseaudio and when i try run alsamixer it just throws an error.

---

### Post by crocowhile on 2009-07-16
> **barryreid said:**
> I think i have messed with too much stuff trying to get this to work.. I think i should do a fresh install, as once i install the new drivers i am not getting any installed devices, just getting the pulseaudio and when i try run alsamixer it just throws an error.

a fresh install is not required if you know what you are doing. did you load the modules after compiling?

---

### Post by Gyroscope352 on 2009-07-16
> **crocowhile said:**
> yes but you need to unmute the card and adjust the other volumes? does the headphone jack work with the latest snapshot?

I second this question. All of a sudden, everyone's all ecstatic but I feel like I missed something. Do we have full working sound now, headphone jack and all? And if so, all we have to do is install the latest snapshot of the alsa drivers as described in post #42 by bobbytables?

---

### Post by barryreid on 2009-07-16
Its just the 1 module am i right?

"modprobe snd-hda-intel"

and that is how u load the module?

---

### Post by barryreid on 2009-07-16
This is what i get when i run the command.

root@barry-laptop:~# modprobe snd-hda-intel
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
FATAL: Error inserting snd (/lib/modules/2.6.28-13-generic/kernel/sound/acore/snd.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error running install command for snd
WARNING: Error inserting snd_pcm (/lib/modules/2.6.28-13-generic/kernel/sound/acore/snd-pcm.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting snd_hwdep (/lib/modules/2.6.28-13-generic/kernel/sound/acore/snd-hwdep.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting snd_hda_codec (/lib/modules/2.6.28-13-generic/kernel/sound/pci/hda/snd-hda-codec.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting snd_hda_intel (/lib/modules/2.6.28-13-generic/kernel/sound/pci/hda/snd-hda-intel.ko): Unknown symbol in module, or unknown parameter (see dmesg)

And this is what im getting from dmesg:

[  136.558973] snd: Unknown symbol sound_class
[  136.560573] snd_timer: Unknown symbol snd_info_register
[  136.560820] snd_timer: Unknown symbol snd_info_create_module_entry
[  136.561045] snd_timer: Unknown symbol snd_info_free_entry
[  136.561432] snd_timer: Unknown symbol snd_verbose_printk
[  136.561677] snd_timer: Unknown symbol snd_iprintf
[  136.561959] snd_timer: Unknown symbol snd_ecards_limit
[  136.562268] snd_timer: Unknown symbol snd_unregister_device
[  136.562491] snd_timer: Unknown symbol snd_device_new
[  136.562912] snd_timer: Unknown symbol snd_register_device_for_dev

---

### Post by barryreid on 2009-07-16
What kernel are you using?

---

### Post by crocowhile on 2009-07-16
> **Gyroscope352 said:**
> I second this question. All of a sudden, everyone's all ecstatic but I feel like I missed something. Do we have full working sound now, headphone jack and all?I just tried out today's version. Headphones still don't work. Rest is good.

> **barryreid said:**
> What kernel are you using?who are you talking to, sorry? Anyway, try the following script.


```
#!/usr/bin/env bash
sudo mv /lib/modules/`uname -r`/kernel/sound /lib/modules/`uname -r`/kernel/sound_original
cd ~
wget ftp://ftp.kernel.org/pub/linux/kernel/people/tiwai/snapshot/alsa-driver-unstable-snapshot.tar.gz
tar xf alsa-driver-unstable-snapshot.tar.gz
cd alsa-driver-unstable
sudo ./configure --enable-dynamic-minors  --without-oss --with-cards="hda-intel"
sudo make
sudo make install
echo "now reboot the machine and execute 'sudo modprobe snd-hda-intel'"
```

---

### Post by barryreid on 2009-07-16
haha sorry, well anyone who has got it working, Im using kernel 2.6.28.13

Just read through your script and it is 100% what I did myself, only difference is I ran all the commands as root.

After reboot I try load the module and I get the errors I posted in my previous post.

---

### Post by crocowhile on 2009-07-16
> **barryreid said:**
> After reboot I try load the module and I get the errors I posted in my previous post.Well, then I don't really know what to say. I know you may get some error similar to that when you don't rm -r the sound directory (mv is not enough for whatever reason). if you fear you changed too many things you can always try:

sudo aptitude reinstall linux-headers-2.6.28-13-generic linux-image-2.6.28-13-generic linux-restricted-modules-2.6.28-13-generic

---

### Post by barryreid on 2009-07-16
Ok just to be 100% sure this is what i have done.

I reinstalled ubuntu 9.04
I updated it
I installed build-essential
I created a scrip file with your script
I ran it
It compiled successfully
I rebooted
I tried to load the module

and this is what I got:

barry@barry-laptop:~$ sudo modprobe snd-hda-intel
FATAL: Error inserting snd (/lib/modules/2.6.28-13-generic/kernel/sound/acore/snd.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error running install command for snd
WARNING: Error inserting snd_pcm (/lib/modules/2.6.28-13-generic/kernel/sound/acore/snd-pcm.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting snd_hwdep (/lib/modules/2.6.28-13-generic/kernel/sound/acore/snd-hwdep.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting snd_hda_codec (/lib/modules/2.6.28-13-generic/kernel/sound/pci/hda/snd-hda-codec.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting snd_hda_intel (/lib/modules/2.6.28-13-generic/kernel/sound/pci/hda/snd-hda-intel.ko): Unknown symbol in module, or unknown parameter (see dmesg)
barry@barry-laptop:~$

---

### Post by crocowhile on 2009-07-16
> **barryreid said:**
> Ok just to be 100% sure this is what i have done.
$
Well, if we have the same machine and the same distribution it should really work. I just tried today and it was fine on my mac.

```
gg@ggmac:~$ sudo dmidecode -s system-product-name
MacBookPro5,5
gg@ggmac:~$ uname -a
Linux ggmac 2.6.28-13-generic #45-Ubuntu SMP Tue Jun 30 22:12:12 UTC 2009 x86_64 GNU/Linux
```

are you using 32bit by any chance?

EDIT:
Alright, I tried again. Doesn't work on mine either now :/ must be something wrong with the current snapshot

EDIT2:
wrong again. you must retain original folder "sound" in /lib/modules/`uname -r`/kernel. deleting the original folder is wrong.

---

### Post by barryreid on 2009-07-16
Nope, Im running 32bit and i have the MacBookPro 15'

root@barry-laptop:/home/barry# sudo dmidecode -s system-product-name
MacBookPro5,4
root@barry-laptop:/home/barry# uname -a
Linux barry-laptop 2.6.28-13-generic #45-Ubuntu SMP Tue Jun 30 19:49:51 UTC 2009 i686 GNU/Linux

but from what i have heard 5,4 or 5,5 should not make a dif.

Edit:
Problem seems to be that if u remove the sound folder u are killing all the soundcore stuff, and without the soundcore thats why it throws up all the errors. I cant even load just snd

---

### Post by barryreid on 2009-07-16
Then how come in your script you rm -rf that folder?

---

### Post by crocowhile on 2009-07-16
> **barryreid said:**
> Then how come in your script you rm -rf that folder?

'cause it was a copy and paste of post #42. Now it's fixed. Sorry about that.

So, I did:

```
#delete the entire thing, just to clean up stuff
sudo rm -rf /lib/modules/`uname -r`/kernel

#reinstall the kernel
sudo aptitude reinstall linux-headers-2.6.28-13-generic linux-image-2.6.28-13-generic linux-restricted-modules-2.6.28-13-generic

#launch the script
./update_alsa.sh

#reboot and modprobe. Sound works
```

---

### Post by barryreid on 2009-07-16
OMG its working... Thanx so so so much... been at this for 3 days since I got my mac on tuesday.

Edit:
Its a bit bugy but its working :) and my headphone jack is working.

---

### Post by barryreid on 2009-07-16
Have you by any chance been able to get the restart working. shutdown and all work fine. Just no restart.

---

### Post by Mazza558 on 2009-07-16
I followed the guide a few pages back, but now I get "null output" in the sound controls, and modprobing gives me this:

> james@james-laptop:~$ sudo modprobe snd-hda-intel
[sudo] password for james: 
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
FATAL: Error inserting snd (/lib/modules/2.6.28-11-generic/kernel/sound/acore/snd.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error running install command for snd
WARNING: Error inserting snd_pcm (/lib/modules/2.6.28-11-generic/kernel/sound/acore/snd-pcm.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting snd_hwdep (/lib/modules/2.6.28-11-generic/kernel/sound/acore/snd-hwdep.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting snd_hda_codec (/lib/modules/2.6.28-11-generic/kernel/sound/pci/hda/snd-hda-codec.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting snd_hda_intel (/lib/modules/2.6.28-11-generic/kernel/sound/pci/hda/snd-hda-intel.ko): Unknown symbol in module, or unknown parameter (see dmesg)


HELP!

EDIT: From my understanding, removing those alsa files was actually the wrong thing to do, right? How do I get them back? Reinstalling ALSA?

---

### Post by barryreid on 2009-07-16
Ok here is a step by step guide on how to get it all working.

First thing you need to do is remove anything in your sound folder so we have a clean start, do this by running:

```
sudo rm -rf /lib/modules/`uname -r`/kernel/sound
```

Next thing you need to do is restor your original kernel files, to do this run the following command:

```
sudo aptitude reinstall linux-headers-2.6.28-13-generic linux-image-2.6.28-13-generic linux-restricted-modules-2.6.28-13-generic
```

After that you will be prompted to restart, Restart Now.

Once back in ubuntu run the folowing commands:

```
wget ftp://ftp.kernel.org/pub/linux/kernel/people/tiwai/snapshot/alsa-driver-unstable-snapshot.tar.gz
tar xf alsa-driver-unstable-snapshot.tar.gz
cd alsa-driver-unstable
sudo ./configure --enable-dynamic-minors  --without-oss --with-cards="hda-intel"
sudo make
sudo make install
```

Now reboot. Once your system is back up open up your volume control and unmute all the channels and make sure they are turned up.

---

### Post by rebanador on 2009-07-16
> **barryreid said:**
> Ok here is a step by step guide on how to get it all working.

(...)



Awesome! Followed the guide and got it working with kernel 2.6.31-3-generic.

Alas, still no headphones.

Thanks!

---

### Post by Mazza558 on 2009-07-16
> **barryreid said:**
> Ok here is a step by step guide on how to get it all working.

First thing you need to do is remove anything in your sound folder so we have a clean start, do this by running:

```
sudo rm -rf /lib/modules/`uname -r`/kernel/sound
```

Next thing you need to do is restor your original kernel files, to do this run the following command:

```
sudo aptitude reinstall linux-headers-2.6.28-13-generic linux-image-2.6.28-13-generic linux-restricted-modules-2.6.28-13-generic
```

After that you will be prompted to restart, Restart Now.

Once back in ubuntu run the folowing commands:

```
wget ftp://ftp.kernel.org/pub/linux/kernel/people/tiwai/snapshot/alsa-driver-unstable-snapshot.tar.gz
tar xf alsa-driver-unstable-snapshot.tar.gz
cd alsa-driver-unstable
sudo ./configure --enable-dynamic-minors  --without-oss --with-cards="hda-intel"
sudo make
sudo make install
```

Now reboot. Once your system is back up open up your volume control and unmute all the channels and make sure they are turned up.

I've done all this but have no sound still. I get the Cirrus Logic stuff, but it was never muted in the first place...

edit: got it working! yay! now all we need is the headphone jack to work...

edit2: is there a way to compile alsa with midi support? I need it for audio production. If not, then I'll have to keep my older laptop around solely for that purpose.

---

### Post by barryreid on 2009-07-16
The one that is muted was not in Cirrus, it was just in the Alsa Mixer, If i remember right it was the PCM slider.

---

### Post by barryreid on 2009-07-16
> **rebanador said:**
> Awesome! Followed the guide and got it working with kernel 2.6.31-3-generic.

Alas, still no headphones.

Thanks!

My headphones work, I just have to mute the Front Speaker slider to get it to stop coming through the laptop speakers.

---

### Post by rebanador on 2009-07-17
> **barryreid said:**
> My headphones work, I just have to mute the Front Speaker slider to get it to stop coming through the laptop speakers.

Hmmm not for me. No sound through the headphone/line-out jack whatsoever.

---

### Post by onesnowyplover on 2009-07-17
> **barryreid said:**
> Ok here is a step by step guide on how to get it all working.

...



I've been following this thread for a few days, without luck on my new 15" macbook pro (MacBookPro5,3), until barryreid's post. Thank you very much for posting step-by-step, it turns out I was missing the "sudo aptitude reinstall..." commands.

Like everyone else, my headphone output is quirky. But that's good enough!

Thank you all, and hope to see you around now that I'm registered.
-Mark H

---

### Post by bobbytables on 2009-07-17
according to a few things i've been reading/hearing, the MBP5,4 (15") and the 17" have a different codec on their hda-chip, compared to the 13" 5,5.

**barryreid** or some other mbp5,4-owner, could you please a) do a ```
lsmod | grep -i snd
```   and paste the output?  

and b) even better:
```
cat /proc/asound/card0/codec#0
```

most likely a realtek-chipset will turn up, and has not actually a lot to do with the Takashi-Cirrus patches. 

meaning: the 15"mbp should have working sound with any recent alsa-driver-version.

---

### Post by barryreid on 2009-07-18
barry@barry-laptop:~$ lsmod | grep -i snd
snd_hda_codec_cirrus    20224  1 
snd_hda_intel          36064  3 
snd_hda_codec          88576  2 snd_hda_codec_cirrus,snd_hda_intel
snd_hwdep              14852  1 snd_hda_codec
snd_pcm                82948  2 snd_hda_intel,snd_hda_codec
snd_seq                57648  0 
snd_timer              29192  2 snd_pcm,snd_seq
snd_seq_device         15372  1 snd_seq
snd                    61300  14 snd_hda_codec_cirrus,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_seq,snd_timer,snd_seq_device
soundcore              15200  1 snd
snd_page_alloc         17032  2 snd_hda_intel,snd_pcm





barry@barry-laptop:~$ cat /proc/asound/card
card0/ cards  
barry@barry-laptop:~$ cat /proc/asound/card0/codec#0 
Codec: Cirrus Logic CS4206
Address: 0
Function Id: 0x1
Vendor Id: 0x10134206
Subsystem Id: 0x106b4c00
Revision Id: 0x100301
No Modem Function Group found
Default PCM:
    rates [0x7f0]: 32000 44100 48000 88200 96000 176400 192000
    bits [0x1e]: 16 20 24 32
    formats [0x3]: PCM FLOAT
Default Amp-In caps: N/A
Default Amp-Out caps: N/A
GPIO: io=4, o=0, i=0, unsolicited=0, wake=0
  IO[0]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
  IO[1]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
  IO[2]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
  IO[3]: enable=1, dir=1, wake=0, sticky=0, data=1, unsol=0
Node 0x02 [Audio Output] wcaps 0xd041d: Stereo Amp-Out
  Amp-Out caps: ofs=0x73, nsteps=0x7f, stepsize=0x01, mute=1
  Amp-Out vals:  [0x73 0x73]
  Converter: stream=0, channel=0
  PCM:
    rates [0x7f0]: 32000 44100 48000 88200 96000 176400 192000
    bits [0x1e]: 16 20 24 32
    formats [0x3]: PCM FLOAT
  Power: setting=D0, actual=D0
  Delay: 13 samples
Node 0x03 [Audio Output] wcaps 0xd041d: Stereo Amp-Out
  Amp-Out caps: ofs=0x73, nsteps=0x7f, stepsize=0x01, mute=1
  Amp-Out vals:  [0x80 0x80]
  Converter: stream=0, channel=0
  PCM:
    rates [0x7f0]: 32000 44100 48000 88200 96000 176400 192000
    bits [0x1e]: 16 20 24 32
    formats [0x3]: PCM FLOAT
  Power: setting=D0, actual=D0
  Delay: 13 samples
Node 0x04 [Audio Output] wcaps 0xd041d: Stereo Amp-Out
  Amp-Out caps: ofs=0x73, nsteps=0x7f, stepsize=0x01, mute=1
  Amp-Out vals:  [0x73 0x73]
  Converter: stream=0, channel=0
  PCM:
    rates [0x7f0]: 32000 44100 48000 88200 96000 176400 192000
    bits [0x1e]: 16 20 24 32
    formats [0x3]: PCM FLOAT
  Power: setting=D0, actual=D0
  Delay: 13 samples
Node 0x05 [Audio Input] wcaps 0x18051b: Stereo Amp-In
  Amp-In caps: ofs=0x33, nsteps=0x3f, stepsize=0x03, mute=1
  Amp-In vals:  [0xb3 0xb3] [0xb3 0xb3]
  Converter: stream=0, channel=0
  SDI-Select: 0
  PCM:
    rates [0x1f5]: 8000 16000 32000 44100 48000 88200 96000
    bits [0x1e]: 16 20 24 32
    formats [0x3]: PCM FLOAT
  Power: setting=D0, actual=D0
  Delay: 8 samples
  Connection: 2
     0x0c* 0x12
Node 0x06 [Audio Input] wcaps 0x18051b: Stereo Amp-In
  Amp-In caps: ofs=0x33, nsteps=0x3f, stepsize=0x03, mute=1
  Amp-In vals:  [0x0f 0x0f] [0x0f 0x0f]
  Converter: stream=0, channel=0
  SDI-Select: 0
  PCM:
    rates [0x1f5]: 8000 16000 32000 44100 48000 88200 96000
    bits [0x1e]: 16 20 24 32
    formats [0x3]: PCM FLOAT
  Power: setting=D0, actual=D0
  Delay: 8 samples
  Connection: 2
     0x0d* 0x0e
Node 0x07 [Audio Input] wcaps 0x180791: Stereo Digital
  Converter: stream=0, channel=0
  SDI-Select: 0
  Digital: Preemphasis Copyright
  Digital category: 0x0
  PCM:
    rates [0x570]: 32000 44100 48000 96000 192000
    bits [0x1e]: 16 20 24 32
    formats [0x7]: PCM FLOAT AC3
  Unsolicited: tag=00, enabled=0
  Power: setting=D0, actual=D0
  Delay: 8 samples
  Connection: 1
     0x0f
Node 0x08 [Audio Output] wcaps 0x40611: Stereo Digital
  Converter: stream=0, channel=0
  Digital:
  Digital category: 0x0
  PCM:
    rates [0x7f0]: 32000 44100 48000 88200 96000 176400 192000
    bits [0x1e]: 16 20 24 32
    formats [0x7]: PCM FLOAT AC3
  Power: setting=D0, actual=D0
  Delay: 4 samples
Node 0x09 [Pin Complex] wcaps 0x410581: Stereo
  Pincap 0x0000001c: OUT HP Detect
  Pin Default 0x012b4030: [Jack] Headphone at Ext Rear
    Conn = Comb, Color = Green
    DefAssociation = 0x3, Sequence = 0x0
  Pin-ctls: 0xc0: OUT HP
  Unsolicited: tag=01, enabled=1
  Power: setting=D0, actual=D0
  Delay: 1 samples
  Connection: 1
     0x02
Node 0x0a [Pin Complex] wcaps 0x410581: Stereo
  Pincap 0x00000054: OUT Detect Balanced
  Pin Default 0x90100121: [Fixed] Speaker at Int N/A
    Conn = Unknown, Color = Unknown
    DefAssociation = 0x2, Sequence = 0x1
    Misc = NO_PRESENCE
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=00, enabled=0
  Power: setting=D0, actual=D0
  Delay: 1 samples
  Connection: 1
     0x03
Node 0x0b [Pin Complex] wcaps 0x410101: Stereo
  Pincap 0x00000050: OUT Balanced
  Pin Default 0x90100120: [Fixed] Speaker at Int N/A
    Conn = Unknown, Color = Unknown
    DefAssociation = 0x2, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x40: OUT
  Delay: 1 samples
  Connection: 1
     0x04
Node 0x0c [Pin Complex] wcaps 0x41048b: Stereo Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00]
  Pincap 0x00000024: IN Detect
  Pin Default 0x400000f0: [N/A] Line-Out at Ext N/A
    Conn = Unknown, Color = Unknown
    DefAssociation = 0xf, Sequence = 0x0
  Pin-ctls: 0x00:
  Unsolicited: tag=00, enabled=0
  Power: setting=D0, actual=D0
  Delay: 1 samples
Node 0x0d [Pin Complex] wcaps 0x41048b: Stereo Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00]
  Pincap 0x00001764: IN Detect Balanced
    Vref caps: HIZ 50 GRD 80
  Pin Default 0x90a00110: [Fixed] Mic at Int N/A
    Conn = Unknown, Color = Unknown
    DefAssociation = 0x1, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x24: IN VREF_80
  Unsolicited: tag=00, enabled=0
  Power: setting=D0, actual=D0
  Delay: 1 samples
Node 0x0e [Pin Complex] wcaps 0x41000b: Stereo Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x02, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00]
  Pincap 0x00000020: IN
  Pin Default 0x400000f0: [N/A] Line-Out at Ext N/A
    Conn = Unknown, Color = Unknown
    DefAssociation = 0xf, Sequence = 0x0
  Pin-ctls: 0x00:
  Delay: 1 samples
Node 0x0f [Pin Complex] wcaps 0x410681: Stereo Digital
  Pincap 0x00000024: IN Detect
  Pin Default 0x400000f0: [N/A] Line-Out at Ext N/A
    Conn = Unknown, Color = Unknown
    DefAssociation = 0xf, Sequence = 0x0
  Pin-ctls: 0x00:
  Unsolicited: tag=00, enabled=0
  Power: setting=D0, actual=D0
  Delay: 1 samples
Node 0x10 [Pin Complex] wcaps 0x410301: Stereo Digital
  Pincap 0x00000010: OUT
  Pin Default 0x014be040: [Jack] SPDIF-Out at Ext Rear
    Conn = Comb, Color = White
    DefAssociation = 0x4, Sequence = 0x0
  Pin-ctls: 0x00:
  Delay: 1 samples
  Connection: 1
     0x08
Node 0x11 [Vendor Defined Widget] wcaps 0xf00040: Mono
  Processing caps: benign=0, ncoeff=22
Node 0x12 [Pin Complex] wcaps 0x41000b: Stereo Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x02, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00]
  Pincap 0x00000020: IN
  Pin Default 0x400000f0: [N/A] Line-Out at Ext N/A
    Conn = Unknown, Color = Unknown
    DefAssociation = 0xf, Sequence = 0x0
  Pin-ctls: 0x00:
  Delay: 1 samples
Node 0x13 [Beep Generator Widget] wcaps 0x700000: Mono
Node 0x14 [Audio Output] wcaps 0x40611: Stereo Digital
  Converter: stream=0, channel=0
  Digital:
  Digital category: 0x0
  PCM:
    rates [0x7f0]: 32000 44100 48000 88200 96000 176400 192000
    bits [0x1e]: 16 20 24 32
    formats [0x7]: PCM FLOAT AC3
  Power: setting=D0, actual=D0
  Delay: 4 samples
Node 0x15 [Pin Complex] wcaps 0x410301: Stereo Digital
  Pincap 0x00000010: OUT
  Pin Default 0x400000f0: [N/A] Line-Out at Ext N/A
    Conn = Unknown, Color = Unknown
    DefAssociation = 0xf, Sequence = 0x0
  Pin-ctls: 0x00:
  Delay: 1 samples
  Connection: 1
     0x14
barry@barry-laptop:~$

---

### Post by chintalapati on 2009-07-18
I recently bought my Macbook pro 15 inches (unified body).
By using rEfit, i am able to triple boot with Os X, Ubuntu 9.04 32-bit and XP pro.

My macbook model
sudo dmidecode -s system-product-name
MacBookPro5,3

I got everything working except sound. I tried all the instructions mentioned in ubuntu macbook pro community.

lspci -v 
00:08.0 Audio device: nVidia Corporation MCP79 High Definition Audio (rev b1)
    Subsystem: nVidia Corporation Device cb79
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 22
    Memory at e7480000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel


lsmod | grep snd
snd_hda_intel          34120  3 
snd_hda_codec          83456  1 snd_hda_intel
snd_hwdep              15364  1 snd_hda_codec
snd_pcm_oss            45984  0 
snd_mixer_oss          22912  1 snd_pcm_oss
snd_pcm                82948  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy          10884  0 
snd_seq_oss            36224  0 
snd_seq_midi           14240  0 
snd_rawmidi            29856  1 snd_seq_midi
snd_seq_midi_event     15232  2 snd_seq_oss,snd_seq_midi
snd_seq                57456  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29192  2 snd_pcm,snd_seq
snd_seq_device         15372  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    66724  18 snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15200  1 snd
snd_page_alloc         17032  2 snd_hda_intel,snd_pcm


Can anyone please help to get sound working? 

Thanks in advance.
Please let me know if you need more info.

---

### Post by bobbytables on 2009-07-18
> **chintalapati said:**
> 
I got everything working except sound. I tried all the instructions mentioned in ubuntu macbook pro community.


did you try the instructions you can find in this very thread?

---

### Post by bobbytables on 2009-07-18
> **barryreid said:**
> barry@barry-laptop:~$ lsmod | grep -i snd
snd_hda_codec_cirrus    20224  1 

...

hm okay- this is rather interesting. you might want to join alsa-devel - mailinglist with your information.

or alternatively: could you grab alsa-info.sh (here: [http://www.alsa-project.org/alsa-info.sh](http://www.alsa-project.org/alsa-info.sh)) and run it on your system?
it'll provide you with a link to all kinds of information. also if you want, you can run codecgraph, which will generate a SVG of your soundchip.

i will pass that stuff on to Takashi and the mailinglist then.

thanks

---

### Post by chintalapati on 2009-07-19
> **bobbytables said:**
> did you try the instructions you can find in this very thread?

Actually i had gone through the thread upto page 9.
So i thought no solution yet.
But instructions on page 10 worked - Thanks alot.

---

### Post by rcn30rcn on 2009-07-20
I haven't seen this problem. it works fine in mine.

---

### Post by Mazza558 on 2009-07-20
Can anyone help me with getting MIDI to work? DO I have to enable midi options in ALSA, when compiling?

---

### Post by bobbytables on 2009-07-22
> **Mazza558 said:**
> Can anyone help me with getting MIDI to work? DO I have to enable midi options in ALSA, when compiling?


should be sufficient to do a configure with --with-sequencer.
like so:
```
./configure --enable-dynamic-minors  --without-oss --with-cards="hda-intel" --with-sequencer
```

.

---

### Post by dschoerl on 2009-07-23
Is it the some procedure for the new Mac Pro, Quad-Core?

---

### Post by dschoerl on 2009-07-23
Is it the some procedure for the new Mac Pro, Quad-Core? Thanks!

---

### Post by chintalapati on 2009-07-23
I m having Macbook pro unified body (2.8 GHz, 4GB)
I recently did triple boot (OS X.Ubuntu 9.04, XP pro).

(ubuntu 9.04 32 bit)
After following the instructions on page 10 (in this thread). I got my sound working. 
But my flash player has no sound, it freezes my firefox too.

Does any one know how to fix it?.  Any help highly appreciated.

---

### Post by chintalapati on 2009-07-23
Flash player problem got resolved.
I followed this thread
[http://ubuntuforums.org/showthread.php?t=1146943&page=3](http://ubuntuforums.org/showthread.php?t=1146943&page=3)

---

### Post by Ravernomina on 2009-07-25
I have no sound and i tried the solutions on this thread :(



Mac book Pro 15" (5,4) any assistance please :)

Btw its still showing as nvidia and not as cirrus Logic.... :/


i also attached the alsa utility scripts output.

---

### Post by Ravernomina on 2009-07-25
Bump   Please help :(

---

### Post by bobbytables on 2009-07-25
Hey *,

so i found [this patch]("https://lists.launchpad.net/mactel-support/msg01237.html") (which i altered a little bit) so that the CapsLock-Key becomes the "Print/SysRq"-Key. 

this way you can use the magic-sysrq-keys again.
(Alt-CapsLock-S/U/O to turn of the computer, B won't work due to reboot not working)


apply by going to your sources-dir, and do 
```
patch -p1 < /location/of/the/patch.txt
```


oh btw: [COLOR="Red"]this will currently only work with "USB_DEVICE_ID_APPLE_WELLSPRING3_ANSI", aka the US-Layout.[/COLOR]
if someone needs this applied to another mbp-keyboard layout, please IM me.

---

### Post by Ravernomina on 2009-07-25
please assist

---

### Post by crocowhile on 2009-07-26
> **Ravernomina said:**
> please assist
Dude, follow instruction in message #98 and you'll be fine.

---

### Post by alexmurray on 2009-07-26
Actually I think Ravernomina has a different sound chipset (see their earlier post) than yours so I wouldn't be surprised if it doesn't work.

---

### Post by Gyroscope352 on 2009-07-26
Hey guys, it took me awhile to get around to installing these alsa drivers...just wanted to say thanks! Works like a charm! Headphone jack works, just have to mute the front speaker in volume control if I don't want it coming out of the 'book's speakers. Fantastic! Linux is now usable! lol

---

### Post by Ravernomina on 2009-07-26
i have the same chipset and i tried everything else :l


Nothing is working and its a pain in the butt

---

### Post by Gyroscope352 on 2009-07-27
> **Ravernomina said:**
> its a pain in the butt

Welcome to Linux! It's far more of a pain in the *** than most Linux users would lead you to believe.

Good luck finding a solution. I'd help, but sadly, I'm probably even more of a noob than you.

---

### Post by avilella on 2009-07-30
Hi Gyroscope352,

Is the wiki at the URL below up-to-date to your own investigations?
[https://help.ubuntu.com/community/MacBookPro5-5/Jaunty](https://help.ubuntu.com/community/MacBookPro5-5/Jaunty)

Have you tried the Firewire? Apple Remote Control? Is the touchpad and perfectly keyboard functioning?


> **Gyroscope352 said:**
> Welcome to Linux! It's far more of a pain in the *** than most Linux users would lead you to believe.

Good luck finding a solution. I'd help, but sadly, I'm probably even more of a noob than you.

---

### Post by Gyroscope352 on 2009-07-30
> **avilella said:**
> Hi Gyroscope352,

Is the wiki at the URL below up-to-date to your own investigations?
[https://help.ubuntu.com/community/MacBookPro5-5/Jaunty](https://help.ubuntu.com/community/MacBookPro5-5/Jaunty)

Have you tried the Firewire? Apple Remote Control? Is the touchpad and perfectly keyboard functioning?

Oh hey, there's documentation now! lol. Since I was one of the first (apparently) to try Ubuntu on these machines, I thought about starting the documentation but by the time I thought about it I had already gotten half the stuff working, and hell if I remembered how.

That said, I do not really know the solutions to what did work on my machine, but I can say what still doesn't. I don't know about FireWire or the Apple Remote, but I do know that the touchpad is a pain in the **** as described there. Unlike in OS X, you cannot have two fingers on the touchpad at once, or it will think you want to scroll/right click. In OS X, there's something (magical?) about the touchpad that makes it act like the old touchpads with the button at the bottom - if you have two fingers on the touchpad, but one is at the bottom (where the old button would have been), it will act as if you have the old touchpad (the top finger moving the cursor and the bottom clicking). I'm not sure if this makes sense or not, but if you use the methods described in the documentation, go into Ubuntu and see what I mean. Perhaps I'm the only person that uses their trackpad like this, but I doubt it. In Ubuntu, you have to literally only touch the touchpad with one finger, and then press the pad down with that same finger to click (or pick it up and put your thumb down, you literally cannot have two fingers on the trackpad without it right-clicking or scrolling). It's pretty bad. No clue how to fix it though. That, screen brightness keys, and reboot are probably the biggest problems at the moment.

Question: How do I make the other non-hardware related F keys (such as expose, dashboard, play/rew/ff) function in Ubuntu? I set up Compiz Widgets to mimic the OS X dashboard, but I can't map F4 to show them, I have to map fn+F4 because it says F4 is taken or something.

---

### Post by bobbytables on 2009-07-30
> **Gyroscope352 said:**
> No clue how to fix it though. That, screen brightness keys, and reboot are probably the biggest problems at the moment.

well you can enable TapButton1,2,3  - so you only have to tap to click - that is one help, also: i talked to some people who then told me that synaptics is being worked on, so that the apple-magic should work under linux too in the not-too-distant future.
also: when you use [pommed]("http://git.debian.org/?p=pommed/pommed.git;a=summary"), the brightnesskeys for keyboard work ootb, and when you use the patch from Brian J. Tarricone for the nvidia brightnesscontrol ([here]("http://spuriousinterrupt.org/journal/2009/07/new-laptop-aka-gentoo-on-macbook-pro-55/")) you can also regulate your brightness.


> **Gyroscope352 said:**
> Question: How do I make the other non-hardware related F keys (such as expose, dashboard, play/rew/ff) function in Ubuntu? I set up Compiz Widgets to mimic the OS X dashboard, but I can't map F4 to show them, I have to map fn+F4 because it says F4 is taken or something.

i mapped mine to F18,F19,F20 and such, that way you can simply assign them, like so in your .Xmodmap:
```
keycode 128 = F20
keycode 212 = F19
```
(F20 i believe is the eject-button i'm using for other stuff, F19 should be the exposé)

---

### Post by bobbytables on 2009-07-30
so listen you guys.... 

so i decided that i now use OS X, coz sound doesn't work with the headphones.

i now believe opensource is "a cancer that infects everything it touches"...

ohno wait a minute: 

[SIZE="4"][COLOR="Red"]the headphones DO WORK NOW!!!!!!!!!!!!!!!!!!!!!!!!!!!!
!!!!!!!!!1
!!!1111111111111111111[/COLOR][/SIZE]


!!!


F*** YEAH.


[http://thread.gmane.org/gmane.linux.alsa.devel/65231](http://thread.gmane.org/gmane.linux.alsa.devel/65231)  here's the patch, and according to Takashi, this will find it's way into 2.6.32  .. so for now it's better to manually patch, i suppose.

oh i just got another 2 emails, from the thread, so Takashi says:
> You can use alsa-driver-snapshot (not unstable one)
from now on.  It might take some time until the server is sync'ed.

there you have it, boys =)


a round of applause to Takashi and Stelian and the bunch :)

---

### Post by avilella on 2009-07-30
Any luck with reboot? Has anyone tried anything recently to get it to work?

---

### Post by bobbytables on 2009-07-31
> **bobbytables said:**
> 
[SIZE="4"][COLOR="Red"]the headphones DO WORK NOW!!!!!!!!!!!!!!!!!!!!!!!!!!!!
!!!!!!!!!1
!!!1111111111111111111[/COLOR][/SIZE]



... seriously - no one is gonna comment on that?

---

### Post by mzbz on 2009-07-31
> **bobbytables said:**
> ... seriously - no one is gonna comment on that?

Maybe everyone's busy listening to music from headphones ...

Haven't tried the solution myself, but will do so later. Do you know if it is already included in the snapshot releases that were linked here earlier?

---

### Post by crocowhile on 2009-07-31
I can confirm headphones work on 5,5. Great Work!
Reboot seems to work a bit better with 2.6.28-14 but still not perfect: my system will reboot into linux (the machine does not actually reset: simply the kernel is re-loaded from scratch).

---

### Post by avilella on 2009-07-31
meaning you don't get to choose between OSX / Linux but you are directly directed to a Linux reboot?

---

### Post by crocowhile on 2009-07-31
Yes. Weirdly enough it doesn't even get me to choose which kernel to boot from grub. It would just load the most recent kernel. At least it doesn't hang.

---

### Post by Gyroscope352 on 2009-07-31
> **bobbytables said:**
> ... seriously - no one is gonna comment on that?

I thought it was well said ;-)

---

### Post by bobbytables on 2009-07-31
> **crocowhile said:**
> Yes. Weirdly enough it doesn't even get me to choose which kernel to boot from grub. It would just load the most recent kernel. At least it doesn't hang.

that's not weird, but called "kexec system call" - it's a kernel-feature, that allows you to simply reboot into another kernel, you skip everything else (like bios/efi and also grub)

---

### Post by crocowhile on 2009-07-31
> **bobbytables said:**
> that's not weird, but called "kexec system call" - it's a kernel-feature, that allows you to simply reboot into another kernel, you skip everything else (like bios/efi and also grub)

Alright, I see what they did here, then. With the upgrade to 2.6.28-14 the package called kexec-tools was probably installed and/or activated. If I disable kexec (by editing the file at /etc/default/kexec) then the restart goes through ACPI again and fails. Thanks for pointing this out.

So, install kexec-tools to get restart kind-of-working.

---

### Post by Mazza558 on 2009-08-07
I'm trying this on Karmic and with the 2.6.31.2 kernels instead. I can report that you get no sound at all if you follow the steps at post 98 (reinstalling karmic's kernels instead of the Jaunty ones in that post). This is even after unmuting everything in alsamixer. 

Bah.

---

### Post by Mazza558 on 2009-08-10
Tried it on Jaunty and ALSA refuses to compile. 

Double Bah.

---

### Post by gds on 2009-08-11
> **Mazza558 said:**
> I'm trying this on Karmic and with the 2.6.31.2 kernels instead. I can report that you get no sound at all if you follow the steps at post 98 (reinstalling karmic's kernels instead of the Jaunty ones in that post). This is even after unmuting everything in alsamixer. 

I followed post 98 on my Karmic install (kernel 2.6.31-5-generic-pae) and it worked for me. Both onboard speakers and headphones seem to be working now.

Do you get an error if you try to manually insert the module?

---

### Post by Mazza558 on 2009-08-12
> **gds said:**
> I followed post 98 on my Karmic install (kernel 2.6.31-5-generic-pae) and it worked for me. Both onboard speakers and headphones seem to be working now.

Do you get an error if you try to manually insert the module?

I'm on Jaunty now, with a fresh install. I'm following the instructions on post 98 exactly. When I try and and make the alsa driver, this is what I get:

> ~/alsa-driver-unstable$ make
if [ ! -d include/sound -a ! -L include/sound ]; then \
	  ln -sf ../alsa-kernel/include include/sound ; \
	fi
cp -puvf include/version.h include/sound/version.h
make dep
make[1]: Entering directory `/home/james/alsa-driver-unstable'
if [ ! -d include/sound -a ! -L include/sound ]; then \
	  ln -sf ../alsa-kernel/include include/sound ; \
	fi
cp -puvf include/version.h include/sound/version.h
make[2]: Entering directory `/home/james/alsa-driver-unstable/acore'
copying file alsa-kernel/core/info.c
/home/james/alsa-driver-unstable/utils/patch-alsa: 24: patch: not found
make[2]: *** [info.c] Error 1
make[2]: Leaving directory `/home/james/alsa-driver-unstable/acore'
make[1]: *** [dep] Error 1
make[1]: Leaving directory `/home/james/alsa-driver-unstable'
make: *** [include/sndversions.h] Error 2


**I think the newer alsa-driver tarballs are broken. Could someone kindly upload the tarball that compiled for them?**

---

### Post by gds on 2009-08-12
> **Mazza558 said:**
> I'm on Jaunty now, with a fresh install. I'm following the instructions on post 98 exactly. When I try and and make the alsa driver, this is what I get:


/home/james/alsa-driver-unstable/utils/patch-alsa: 24: patch: not found


Since it's a fresh install, could you be missing some of the build tools? Does 
```
apt-get build-dep alsa-source
```
drag in the necessary tools? I do still have the tarball I built from if you need it.

---

### Post by Mazza558 on 2009-08-12
> **gds said:**
> Since it's a fresh install, could you be missing some of the build tools? Does 
```
apt-get build-dep alsa-source
```
drag in the necessary tools? I do still have the tarball I built from if you need it.

Thanks!

I now have sound, now to test it with LMMS :)

EDIT: I have sound with LMMS but no MIDI support. The keyboard's detected via lsusb. I compiled with the --with-sequencer flag.
EDIT: My keyboard as a MIDI device isn't detected in any music programs which usually support it.

>  lsmod | grep snd
snd_hda_codec_cirrus    20224  1 
snd_hda_intel          36576  3 
snd_hda_codec          89216  2 snd_hda_codec_cirrus,snd_hda_intel
snd_hwdep              14852  1 snd_hda_codec
snd_pcm                83460  2 snd_hda_intel,snd_hda_codec
snd_seq                57648  0 
snd_timer              29192  2 snd_pcm,snd_seq
snd_seq_device         15372  1 snd_seq
snd                    61428  14 snd_hda_codec_cirrus,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_seq,snd_timer,snd_seq_device
soundcore              15200  1 snd
snd_page_alloc         17032  2 snd_hda_intel,snd_pcm


---

### Post by Mazza558 on 2009-08-13
Anyone have any ideas about MIDI support?

---

### Post by Mazza558 on 2009-08-28
After a bit more investigating, it turns out that the midi modules "snd-usb-audio" and "snd-rawmidi" weren't loading, and modprobing them returns "module not found" errors.

I've emailed alsa-users and also the dev who made the alsa patches, asking for help.

---

### Post by Mazza558 on 2009-08-28
I've fixed the problem. The with-card flag during configure is unnecessary and anyone who wants midi support too should remove it.

---

### Post by amd-64 on 2009-08-29
> **Mazza558 said:**
> I've fixed the problem. The with-card flag during configure is unnecessary and anyone who wants midi support too should remove it.

Nice work.

---

### Post by Mazza558 on 2009-08-29
> **amd-64 said:**
> Nice work.

Yup, it's nice to use the MacBook for audio production, as the sound quality is very good indeed.

---

### Post by shivathreya on 2009-08-29
Hi,

I installed and configured pulseaudio and it rocks.

Also Skype 2.1 beta works excellent with PULSE!

Shiva

---

### Post by bobbytables on 2009-08-31
hi everybody

i know most of you guys obviously use ubuntu. 
however i don't and i finally took the time to extract the appleir-code from the 33MB single diff-file that is applied to the vanilla sources on ubuntu.

so whoever it might concern, can find the diff here:
[http://nutz.unfoog.de/mbp/](http://nutz.unfoog.de/mbp/)

(there's also my diff to set Print to CapsLock ... seriously - who needs Caps anyway)

---

### Post by rebanador on 2009-09-05
Hi all,

I am aware this is OT but as you very probably own the same model as I, you might have passed through the same problem.

I kept apt-get updating my Macbook Pro 5,5 with Ubuntu and I ran into a bug: "kinit: No resume image, doing normal boot..." (X server won't start).

This happened about 2 weeks ago, I tried a lot of possible solutions but none of them worked so far. Even booting with different kernels won't solve it. I even tried today booting with the Karmic alpha-5 from a CD image, and I still doesn't work (no error but no X - a startx & won't help either).

Any ideas or pointers?

Thanks!

---

### Post by dennis123123 on 2009-09-05
I think theres a problem with the current xorg/nvidia/drivers:

[https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/414259](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/414259)

I'm reading up on this as I planned to buy a MBP soon!
Any other input from people would be helpful to me too :S

EDIT1: Found more people with similar problems with very recent Xorg and nvidia laptop chips [http://bbs.archlinux.org/viewtopic.php?id=77131&p=1](http://bbs.archlinux.org/viewtopic.php?id=77131&p=1)

---

### Post by rebanador on 2009-09-07
Well I actually solved my problem by reinstalling nvidia-185-kernel-source and related packages.

Thanks!

---

### Post by rebanador on 2009-09-07
Btw, does anybody know when will the patched ALSA (the steps to get sound working mentioned in this thread) get into the Ubuntu flow?

---

### Post by dennis123123 on 2009-09-07
Glad to hear you got it working.

the wiki says around 2.6.32 :(

---

### Post by Mazza558 on 2009-09-08
> **dennis123123 said:**
> Glad to hear you got it working.

the wiki says around 2.6.32 :(

Which basically means the 10.04 release.

---

### Post by matthewmcnew on 2009-09-08
> **shivathreya said:**
> Hi,

I installed and configured pulseaudio and it rocks.

Also Skype 2.1 beta works excellent with PULSE!

Shiva

For me the microphone is incredibly quiet in skype. Even though I have the microphone turned up all the way. Any suggestions?

---

### Post by shivathreya on 2009-09-09
You uncheck "Allow skype to change mixer levels" In sound options. It will work.

Shiva

---

### Post by dennis123123 on 2009-09-10
Did the driver make it into the just-released 2.6.31 kernel? I wouldn't know where to start looking in the changelog!

---

### Post by shivathreya on 2009-09-10
No.

Shiva

---

### Post by dennis123123 on 2009-09-11
> **shivathreya said:**
> No.

Shiva

Disappointing, but ty for the reply

---

### Post by viktara on 2009-09-14
Hi,

I was facing an issue using the instructions earlier in this thread, as per my post here:
[http://ubuntuforums.org/showthread.php?t=1264578](http://ubuntuforums.org/showthread.php?t=1264578)

However I resolved that by installing the correct kernel :)

Now however, I get sound from the headphone socket, but not from the speakers.

Has anyone else faced this problem? I have unmuted all the channels I can.

The only strange thing I can see is that alsamixer does not have a mute control for PCM - where the volume applet does.

In any case I have unmuted and set to full all the channels.

Vik

---

### Post by shivathreya on 2009-09-14
Follow this post bit by bit and it should work.

[http://ubuntuforums.org/showpost.php?p=7627817&postcount=98](http://ubuntuforums.org/showpost.php?p=7627817&postcount=98)

Shiva

---

### Post by viktara on 2009-09-15
> Follow this post bit by bit and it should work.

[http://ubuntuforums.org/showpost.php...7&postcount=98](http://ubuntuforums.org/showpost.php...7&postcount=98)

Yeah - this is exactly what I have done so far.

But for me, it has only given me sound from the headphone socket and not from the main speakers.

Any other ideas about how to debug further?


Thanks


Vik

---

### Post by bobbytables on 2009-09-16
hi there again, guys

uhm - so I still haven't gotten my mic to work.
there must be some patches or whatnot in your distros, in gentoo at least it doesn't seem to be working.

so i was wondering: could somebody who'd like to help, and who has a working microphone, please IM me his jabber-id so i could talk to that person directly and check for a few things?

thanks everyone.

---

### Post by mirish87 on 2009-09-16
Hi Guys
I'm completely new at Linux (running Ubuntu 9.04 kernel 2.6.28.15) and I have a Macbook Pro 13 inch (Macbook Pro 5,5) but i tried what they suggested for the 15inch version but I tried using this driver instead of what they suggested so I skipped the first couple of steps and did the below:
 
I downloaded this ALSA driver and installed it. 
 [ftp://ftp.kernel.org/pub/linux/kernel/people/tiwai/snapshot/alsa-driver-20090916.tar.gz](ftp://ftp.kernel.org/pub/linux/kernel/people/tiwai/snapshot/alsa-driver-20090916.tar.gz)

I just followed the INSTALL guide in there, rebooted then tried to following for sound in this link (with the exception of the driver they recommend)
 [https://help.ubuntu.com/community/MacBookPro5-1_5-2/Jaunty#Sound](https://help.ubuntu.com/community/MacBookPro5-1_5-2/Jaunty#Sound)
```
gksudo gedit /etc/asound.conf
```and then added the following into the .conf file
```
pcm.out {
        type route
        slave.pcm "hw:0,0";
        slave.channels 6
        ttable {
                0.0 1
                1.1 1
                2.2 1
                3.3 1
                4.4 1
                0.5 0.5
                1.5 0.5
        }
}

pcm.!default {
    type pulse
}
```and then last but not least...
```
gksudo gedit /etc/pulse/default.pa
```and find the #load-module module-alsa-sink line and add channels=6 device=out at the end so it looks like this 
```

#load-module module-alsa-sink channels=6 device=out

```and then i rebooted and went into Volume Control and selected my HDA Nvidia (alsa mixer) and enabled everything under preferences and whacked the volume right up and bingo sound from my macbook pro speakers and from my headphones.

---

### Post by crocowhile on 2009-09-16
I know some folks had trouble getting the microphone to work at proper volume (way too low). this is how to get it working (you need to have pulseaudio installed)

1. Open Application -> Sound & Video -> PulseAudio Device Chooser
2. Click on the &#8220;PulseAudio Applet&#8221; on the system tray and open &#8220;Manager&#8221;.
3. Click on the &#8220;Devices&#8221; tab, select &#8220;Monitor of HDA NVidia" in source
4. Click properties and set the volume to about 150%

Profit!

---

### Post by tonycolin on 2009-09-17
Worked first time - many thanks!

---

### Post by Takala on 2009-09-20
> **barryreid said:**
> Ok here is a step by step guide on how to get it all working.

First thing you need to do is remove anything in your sound folder so we have a clean start, do this by running:

```
sudo rm -rf /lib/modules/`uname -r`/kernel/sound
```Next thing you need to do is restor your original kernel files, to do this run the following command:

```
sudo aptitude reinstall linux-headers-2.6.28-13-generic linux-image-2.6.28-13-generic linux-restricted-modules-2.6.28-13-generic
```After that you will be prompted to restart, Restart Now.

Once back in ubuntu run the folowing commands:

```
wget ftp://ftp.kernel.org/pub/linux/kernel/people/tiwai/snapshot/alsa-driver-unstable-snapshot.tar.gz
tar xf alsa-driver-unstable-snapshot.tar.gz
cd alsa-driver-unstable
sudo ./configure --enable-dynamic-minors  --without-oss --with-cards="hda-intel"
sudo make
sudo make install
```Now reboot. Once your system is back up open up your volume control and unmute all the channels and make sure they are turned up.

Hi, this doesn't work for me. I have a new Macbook pro 5,5 and now that I've done this tutorial I still have no sound:

```

:~$ lspci | grep audio
:~$ aplay -l
aplay: device_list:217: no soundcards found...
:~$ lsmod | grep -i snd
snd_page_alloc         18960  0 
:~$ alsamixer
alsamixer: function snd_ctl_open failed for default: No such file or directory

```

---

### Post by viktara on 2009-09-21
Hi,

> **Takala said:**
> Hi, this doesn't work for me. I have a new Macbook pro 5,5 and now that I've done this tutorial I still have no sound:

```

:~$ lspci | grep audio
:~$ aplay -l
aplay: device_list:217: no soundcards found...
:~$ lsmod | grep -i snd
snd_page_alloc         18960  0 
:~$ alsamixer
alsamixer: function snd_ctl_open failed for default: No such file or directory

```

When you restarted did you select the 2.6.28-13 kernel?

I have not been able to make it work at all with 2.6.28-15 - which is the current kernel.

HTH

---

### Post by Takala on 2009-09-21
> **viktara said:**
> Hi,



When you restarted did you select the 2.6.28-13 kernel?

I have not been able to make it work at all with 2.6.28-15 - which is the current kernel.

HTH

Hi, 

thanks for the reply! I went straight from the 2.6.28-11 to 2.6.28-15. So I'm using the current kernel. I take it that it is not possible to get sound fixed with that kernel?

Cheers,
Eelis

---

### Post by viktara on 2009-09-22
I've not been able to get it to work with the latest kernel - and for me, even with the recommended kernel, I only get sound from the headphone socket.

I'm trying the unstable snapshot every so often to see if that helps.

---

### Post by dennis123123 on 2009-09-22
Just an FYI, I'm using Debian sid, with kernel 2.6.30-2 and it works fine with the unstable alsa snapshot.

---

### Post by ringo999 on 2009-09-27
I tried #98 with 2.6.28-15-generic on 64-bit. No luck :-(

---

### Post by ringo999 on 2009-10-05
anyone who got it working with the current kernel?

---

### Post by shivathreya on 2009-10-07
After you follow #98, make sure that the volume sliders are up to maximum.

I found that they were muted and front speaker slider was at its lowest. Once I restored them to max everything was working.

Shiva

---

### Post by ringo999 on 2009-10-07
#98 are instructions for **2.6.28-13** but I'm running **2.6.28-15**. when executing the script i never get to see a front speaker panel... in my volume applet preferences the device selected is *HDA Nvidia(Alsa mixer)* is selected and the only channels are have are *Master, PCM* and *Capture*...

---

### Post by dennis123123 on 2009-10-07
> **ringo999 said:**
> #98 are instructions for **2.6.28-13** but I'm running **2.6.28-15**. when executing the script i never get to see a front speaker panel... in my volume applet preferences the device selected is *HDA Nvidia(Alsa mixer)* is selected and the only channels are have are *Master, PCM* and *Capture*...

Those instructions are valid for any kernel, hence the `uname` entries. You did it wrong.

---

### Post by ringo999 on 2009-10-08
> **dennis123123 said:**
> Those instructions are valid for any kernel, hence the `uname` entries. You did it wrong.

I did exactly as described in #98, only using 2.6.28-15-generic instead.
When i reboot the second time nothing seems to have changed, audio is not mute as well. 

And you got it working on the same machine? So what do you think I did wrong?

:confused:

---

### Post by Takala on 2009-10-12
> **ringo999 said:**
> I did exactly as described in #98, only using 2.6.28-15-generic instead.
When i reboot the second time nothing seems to have changed, audio is not mute as well. 

And you got it working on the same machine? So what do you think I did wrong?

:confused:

Hi,

I got it working just now. I realized that I had made a mistake by using the -13 kernel at the aptitude part of the instructions. Now I used the -15 kernel and it is working.

---

### Post by rebanador on 2009-10-12
After various kernel updates in the Karmic development line I kept on losing sound.

I tried again with #98 but no luck.

I found, however, this bit that perfectly worked for me with kernel 2.6.31-12 without even restarting!

```

apt-get build-dep alsa-source
wget ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.21.tar.bz2
tar jxvf alsa-driver-1.0.21.tar.bz2
cd alsa-driver-1.0.21
./configure
make
make install
alsa force-reload
```

From [http://forum.notebookreview.com/showthread.php?t=418403#sound](http://forum.notebookreview.com/showthread.php?t=418403#sound)

Good luck!

---

### Post by ringo999 on 2009-10-12
Thanks for the input, got inspired to upgrade to Karmic. After executing #98 sound works. Also restart works now. Can't tell yet if the other features work well though. Nice to finally have sound back!

---

### Post by prol on 2009-10-12
hows the battery life on it?

---

### Post by hvthao on 2009-10-13
Same as Jaunty. Around 5 to 6 hours.

---

### Post by hanzomon4 on 2009-10-14
Wow! only get 1 hour.. 30 mins tops

---

### Post by hvthao on 2009-10-14
> **hanzomon4 said:**
> Wow! only get 1 hour.. 30 mins tops

How come? Even if you dont enable laptop-mode, i think it can last 3 hours. Here's my screenshot.

[IMG]http://hvthao.com/hvthao/temp/Screenshot.png[/IMG]

---

### Post by satish_vell on 2009-10-16
> **rebanador said:**
> After various kernel updates in the Karmic development line I kept on losing sound.

I tried again with #98 but no luck.

I found, however, this bit that perfectly worked for me with kernel 2.6.31-12 without even restarting!

```

apt-get build-dep alsa-source
wget ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.21.tar.bz2
tar jxvf alsa-driver-1.0.21.tar.bz2
cd alsa-driver-1.0.21
./configure
make
make install
alsa force-reload
```

From [http://forum.notebookreview.com/showthread.php?t=418403#sound](http://forum.notebookreview.com/showthread.php?t=418403#sound)

Good luck!

Awesome! Works perfectly!
I tried other solutions on this thread but none worked for my MBP5,3
Thanks a lot rebanador

---

### Post by nukedeath on 2009-10-16
> **rebanador said:**
> After various kernel updates in the Karmic development line I kept on losing sound.

I tried again with #98 but no luck.

I found, however, this bit that perfectly worked for me with kernel 2.6.31-12 without even restarting!

```

apt-get build-dep alsa-source
wget ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.21.tar.bz2
tar jxvf alsa-driver-1.0.21.tar.bz2
cd alsa-driver-1.0.21
./configure
make
make install
alsa force-reload
```From [http://forum.notebookreview.com/showthread.php?t=418403#sound](http://forum.notebookreview.com/showthread.php?t=418403#sound)

Good luck!

After running this on 9.10 beta kernel 2.6.31-14 and rebooting, i got sound!. Had to install gnome mixer to unmute speakers.

This is truly magnificent :)

EDIT:
[COLOR=Red]
After todays update i lost sound again :|[/COLOR]

---

### Post by hvthao on 2009-10-17
Maybe you've installed a new kernel. Try to recompile the alsa driver again for the new kernel!

---

### Post by proycon on 2009-10-18
What about microphone? I manage to playback sound, but recording sound is a different matter, it seems to only record very faintly, even with volume on 100%. 

(I'm on a Macbook Pro 5,3 btw)

---

### Post by hvthao on 2009-10-18
Mine is the same. It seems to lack of a mic boost.

---

### Post by prol on 2009-10-18
How did u manage to get 5 hours? Did u tweak it? if so what did u do?

---

### Post by hvthao on 2009-10-18
You can follow this thread [http://ubuntuforums.org/showthread.php?t=1215928](http://ubuntuforums.org/showthread.php?t=1215928),
 or use the laptop-mode-tools.

---

### Post by mjantti on 2009-10-20
After many an hour of struggling, I have restored sound on my Macbook Pro 5,2 running karmic beta running 2.6.31-14-generic on a 64-bit system (which I lost on upgrading from Jaunty to Karmic beta). The following may be helpful. 

```

~# sudo uname -a
Linux kronos 2.6.31-14-generic #48-Ubuntu SMP Fri Oct 16 14:05:01 UTC 2009 x86_64 GNU/Linux

```The key thing I did, apart from following a modification of the instructions found at [https://help.ubuntu.com/community/MacBookPro5-1_5-2/Karmic/#Sound](https://help.ubuntu.com/community/MacBookPro5-1_5-2/Karmic/#Sound)
  (the part about removing pulseaudio)  and [http://ubuntuforums.org/showpost.php?p=7979472&postcount=171"]http://ubuntuforums.org/showpost.php?p=7979472&postcount=171]("http://ubuntuforums.org/)
  was to modify  /etc/modprobe.d/alsa-base.conf by  commenting out the line with snd-hda-intel and adding a new line with a different options, so 

```

~# tail -2 /etc/modprobe.d/alsa-base.conf
# options snd-hda-intel power_save=10 power_save_controller=N
options snd-hda-intel model=mb5

```I experimented with several versions of alsa but 1.0.21 worked, so I ran this scrip (seen in many posts with minor variations, one of the the link above):

```

sudo rm -rf /lib/modules/`uname -r`/kernel/sound
sudo aptitude reinstall linux-headers-`uname -r` linux-image-`uname -r`
sudo wget ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.21.tar.bz2
tar jxf alsa-driver-1.0.21.tar.bz2
cd alsa-driver-1.0.21
sudo ./configure --enable-dynamic-minors --without-oss --with-cards="hda-intel"
sudo make
sudo make install

```After this, I reloaded alsa using

```
alsa force-reload
```unmuted all channels using gnome-alsa-mixer after which I  logged out, logged in. At this point, I had sound, although not using applications that typically rely on pulseaudio. 

Next, I re-installed pulseaudio and, after some experimenting, discovered that in Sound Preferences, I needed to choose under Hardware the profile "Analog Stereo Duplex" to both hear sound. But now it works!

---

### Post by ringo999 on 2009-10-25
Hey, this worked, great, thanks.

About battery life: i applied some of the scripts and activated laptop-mode-tools so now i get 3hrs max.

Another problem: I cant dim the screen brightness anymore, I guess I need nvidia 190 for that. Anybody got it working?

> **mjantti said:**
> After many an hour of struggling, I have restored sound on my Macbook Pro 5,2 running karmic beta running 2.6.31-14-generic on a 64-bit system (which I lost on upgrading from Jaunty to Karmic beta). The following may be helpful. 

```

~# sudo uname -a
Linux kronos 2.6.31-14-generic #48-Ubuntu SMP Fri Oct 16 14:05:01 UTC 2009 x86_64 GNU/Linux

```The key thing I did, apart from following a modification of the instructions found at [https://help.ubuntu.com/community/MacBookPro5-1_5-2/Karmic/#Sound](https://help.ubuntu.com/community/MacBookPro5-1_5-2/Karmic/#Sound)
  (the part about removing pulseaudio)  and [http://ubuntuforums.org/showpost.php?p=7979472&postcount=171"]http://ubuntuforums.org/showpost.php?p=7979472&postcount=171]("http://ubuntuforums.org/)
  was to modify  /etc/modprobe.d/alsa-base.conf by  commenting out the line with snd-hda-intel and adding a new line with a different options, so 

```

~# tail -2 /etc/modprobe.d/alsa-base.conf
# options snd-hda-intel power_save=10 power_save_controller=N
options snd-hda-intel model=mb5

```I experimented with several versions of alsa but 1.0.21 worked, so I ran this scrip (seen in many posts with minor variations, one of the the link above):

```

sudo rm -rf /lib/modules/`uname -r`/kernel/sound
sudo aptitude reinstall linux-headers-`uname -r` linux-image-`uname -r`
sudo wget ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.21.tar.bz2
tar jxf alsa-driver-1.0.21.tar.bz2
cd alsa-driver-1.0.21
sudo ./configure --enable-dynamic-minors --without-oss --with-cards="hda-intel"
sudo make
sudo make install

```After this, I reloaded alsa using

```
alsa force-reload
```unmuted all channels using gnome-alsa-mixer after which I  logged out, logged in. At this point, I had sound, although not using applications that typically rely on pulseaudio. 

Next, I re-installed pulseaudio and, after some experimenting, discovered that in Sound Preferences, I needed to choose under Hardware the profile "Analog Stereo Duplex" to both hear sound. But now it works!

---

### Post by justinlawrence on 2009-10-28
compiling works but only until the kernel is upgraded.

i'm also concerned that compiling might get in the way of the official ubuntu/alsa fix at some later stage or is this not possible?

is there somewhere we can vote on this at launchpad? has anyone reported it there yet?

---

### Post by crocowhile on 2009-10-28
> **justinlawrence said:**
> 

is there somewhere we can vote on this at launchpad? has anyone reported it there yet?

It has already been committed. With 2.6.32 sound  works fine out of the box on my MBP.

---

### Post by faust99 on 2009-11-11
> **justinlawrence said:**
> compiling works but only until the kernel is upgraded.



This happened to me today as I inadvertently upgraded to 2.6.31 kernel and now there is no sound again. 

Would anyone be able to indicate whether it is possible, and how to compile 2.6.32 kernel in Karmic?

Also I tried to repeat the process indicated in this thread (i.e. restore kernel files 2.6.18 ) but for some reason the packages for this kernel could not be found by aptitude. I don't understand this as it worked just yesterday. Is it a matter of getting these packages from the jaunty repos? If so, which ones?

---

### Post by shivathreya on 2009-11-13
Just repeat the step in [http://ubuntuforums.org/showpost.php?p=7627817&postcount=98](http://ubuntuforums.org/showpost.php?p=7627817&postcount=98)

Post 98. It will work.

Shiva

---

### Post by faust99 on 2009-11-13
> **shivathreya said:**
> Just repeat the step in [http://ubuntuforums.org/showpost.php?p=7627817&postcount=98](http://ubuntuforums.org/showpost.php?p=7627817&postcount=98)

Post 98. It will work.

Shiva

Yeah unfortunately it did not work....

---

### Post by bobbytables on 2009-11-22
hey everybody, 

me again.

so like probably all of you, I'm rather annoyed by the synaptics-drivers... i'm not blaming the developers here, it's just a 10 year old piece of software and maybe it's time for a new one.

that's the thing i really miss most from OS X .. it works okay in linux, and actually i'm almost done writing a patch to support 4-finger-click and tap.. (it's finished - only thing remaining is the question what it should actually do.)

anyways: i would like to start a new multitouch-driver. from scratch. i'm looking for ambitious developers, that have C experience.

please contact me..

---

### Post by crocowhile on 2009-11-22
> **bobbytables said:**
> that's the thing i really miss most from OS X .. it works okay in linux, and actually i'm almost done writing a patch to support 4-finger-click and tap.. (it's finished - only thing remaining is the question what it should actually do.)
What do you mean what actually do? Release it :) I am looking forward to trying that.
I have no experience with C (only python) so no help on that. You may want to get in touch with this guy though: [http://touchd.sourceforge.net/](http://touchd.sourceforge.net/)

---

### Post by Cerin on 2009-12-01
I have a Macbook Pro 5.5, and my sound had been working just fine, until a routine "update" a few days ago. Now no sound.

Bootup Manager shows both Alsasound and Pulseaudio services are installed, but only Pulseaudio is enabled/running. Is that correct? If not, how do I remove or disable the one that shouldn't be there?

---

### Post by Cerin on 2009-12-01
> **shivathreya said:**
> Just repeat the step in [http://ubuntuforums.org/showpost.php?p=7627817&postcount=98](http://ubuntuforums.org/showpost.php?p=7627817&postcount=98)

Post 98. It will work.

Shiva

Thanks, that worked for me.

---

### Post by Cerin on 2010-01-03
This works great. The only downside is that you have to rerun this script every time your kernel updates. I put these steps in a script, accessible from my path to make things a bit easier.

Any idea how we can tell if or when the start sound package supports this feature, so we can stop recompiling our own sound module? How would we revert to the default package?

> **barryreid said:**
> Ok here is a step by step guide on how to get it all working.

First thing you need to do is remove anything in your sound folder so we have a clean start, do this by running:

```
sudo rm -rf /lib/modules/`uname -r`/kernel/sound
```

Next thing you need to do is restor your original kernel files, to do this run the following command:

```
sudo aptitude reinstall linux-headers-2.6.28-13-generic linux-image-2.6.28-13-generic linux-restricted-modules-2.6.28-13-generic
```

After that you will be prompted to restart, Restart Now.

Once back in ubuntu run the folowing commands:

```
wget ftp://ftp.kernel.org/pub/linux/kernel/people/tiwai/snapshot/alsa-driver-unstable-snapshot.tar.gz
tar xf alsa-driver-unstable-snapshot.tar.gz
cd alsa-driver-unstable
sudo ./configure --enable-dynamic-minors  --without-oss --with-cards="hda-intel"
sudo make
sudo make install
```

Now reboot. Once your system is back up open up your volume control and unmute all the channels and make sure they are turned up.

---

### Post by dennis123123 on 2010-01-04
It was included in (stable) kernel 2.6.32, released Thu, 3 Dec 2009.

---

### Post by Cerin on 2010-01-04
> **dennis123123 said:**
> It was included in (stable) kernel 2.6.32, released Thu, 3 Dec 2009.

That's good news, but I guess I'll still have to wait for another update, since I'm currently running 2.6.31 and neither the stable nor unstable alsa drivers are working for me. Alsamixer reports "function snd_ctl_open failed for default: No such file or directory". Is there any way to fix that?

How do I remove my custom compiled alsa driver once I start using 2.6.32?

---

### Post by Cerin on 2010-01-06
> **dennis123123 said:**
> It was included in (stable) kernel 2.6.32, released Thu, 3 Dec 2009.

It seems this is not the case, or what they included still does not work for the Macbook hardware. I installed kernel 2.6.32 following [http://www.ramoonus.nl/2009/12/03/linux-kernel-2-6-32-installation-guide-for-ubuntu-linux/](http://www.ramoonus.nl/2009/12/03/linux-kernel-2-6-32-installation-guide-for-ubuntu-linux/) and I still have no sound.

---

### Post by linuxopjemac on 2010-01-06
did you also unmute with alsa-mixer ?

---

### Post by szymi on 2010-01-06
Hi guys, just to let you know: I'm using Ubuntu Karmic on my macbook 5-5 with the following kernel:

```
szymi@ski:~$ uname -r
2.6.31-17-generic
```and I have sound. The kernel I believe is "held" in this package: 

```
linux-image-2.6.31-17-generic-pae
```After installing it, you'll have to edit /boot/grub/grub.cfg, find the following line: 

> set default="0" and adjust it so that grub boots to the right kernel. 

If you decide to downgrade, after booting into you new-old kernel remember to reinstall video drivers if you are using proprietary ones to get them to work. Also, you will have to create and run as root the following script (I found it somewhere around here:[ https://help.ubuntu.com/community/MacBookPro5-5/Karmic]("http://https://help.ubuntu.com/community/MacBookPro5-5/Karmic"), can't remember where exactly) 

```

#!/bin/bash
sudo rm -rf /lib/modules/`uname -r`/kernel/sound
sudo aptitude reinstall linux-headers-`uname -r` linux-image-`uname -r`
rm alsa-driver-snapshot.tar.gz
wget ftp://ftp.kernel.org/pub/linux/kernel/people/tiwai/snapshot/alsa-driver-snapshot.tar.gz
tar xf alsa-driver-snapshot.tar.gz
cd alsa-driver
sudo ./configure --enable-dynamic-minors --without-oss --with-cards="hda-intel"
sudo make
sudo make install
```

The above script will install the right alsa driver for your system, and also it will remind you about unmuting sound. Easiest way to do this is to use gnome-alsamixer.

By the way, just a small hint for some of you: if you have something working and it stops working after an update, try booting into the kernel version you were using before update. Nine times out of ten it will magically get your Linux to work again. Generally, if you are inexperienced, always think twice before upgrading kernel if you don't have a valid reason to do so. 

Good luck.

---
[szymi's blog]("http://blog.szymi.com")

---

### Post by Cerin on 2010-01-06
> **linuxopjemac said:**
> did you also unmute with alsa-mixer ?

Ah, I thought I had. After double checking, I realized my "front speaker" channel was still muted. Unmuting that fixed it. Sorry for the false alarm.

---

### Post by Cerin on 2010-01-11
A couple more oddities I've noticed after upgrading to the 2.6.32 kernel:

1. My camera no longer works. Opening Cheese reports "No camera found!"
2. When I open my lid and Ubuntu comes out of suspension, the login prompt appears briefly, and then Ubuntu goes back into suspension. I have to manually press the power button and wait several minutes to bring it out of suspension.

Does anyone else have these problems?

Chris

---

### Post by dennis123123 on 2010-01-11
nope



well, cant speak for everyone, but I certainly don't!

---

### Post by faust99 on 2010-02-04
One of todays security updates is linux-libc-dev (Linux Kernel headers for development). If I install this is it likely to be an issue for the sound on macbook pro 5,5? Sorry for the noob question but I've gained so much grey hair from this issue and now that I've finally got an installation that works almost flawlessly, the last thing I want to do is screw it up again.

---

### Post by alexmurray on 2010-02-05
I would be very surprised if this affected sound. All security updates should be applied ASAP - would you rather have broken sound or your entire machine compromised?

---

### Post by faust99 on 2010-02-05
> **alexmurray said:**
>  would you rather have broken sound or your entire machine compromised?

Same thing really, since I use my computer for work, which revolves around....sound and music  :guitar:

As far as I understand, the sound problem was/is related to the kernel. 

Last time I installed a kernel update it blew my sound and nothing would get it back except a fresh install. I'd like to avoid that.

---

### Post by norbster on 2010-02-05
I'm very new to Ubuntu, and even more new to Linux at that. As the thread suggests I am also having a problem with my sound. I have literally read through all 22 pages and did what was written there. I still have no sound. :( Is there any help for me?

---

### Post by syntheticz on 2010-10-10
I have a Macbook Pro 5,5 
2.53ghz Intel Core 2 duo
13'3 inch display model 
Nvidia 9400M 256MB DDR3 shared
4GB DDR3 RAM
Ubuntu 10.10 Maverick Meerkat. 

I can confirm that on this model the measures in post no.98 do work, I have full sound support after taking these steps. However, I had to change the kernel numbers to account for the updated kernel in 10.10.

---

### Post by larrinski on 2010-12-10
> **syntheticz said:**
> I have a Macbook Pro 5,5 
2.53ghz Intel Core 2 duo
13'3 inch display model 
Nvidia 9400M 256MB DDR3 shared
4GB DDR3 RAM
Ubuntu 10.10 Maverick Meerkat. 

I can confirm that on this model the measures in post no.98 do work, I have full sound support after taking these steps. However, I had to change the kernel numbers to account for the updated kernel in 10.10.

Sorry to bump an old thread here, but it is very applicable to my problem.
I ran 'sudo rm -rf /lib/modules/`uname -r`/kernel/sound' and then 'sudo aptitude reinstall linux-headers-2.6.35-23-generic linux-image-2.6.35-23-generic linux-restricted-modules-2.6.35-23-generic' thinking that it would update but it says it couldn't find the modules. Now I have NO sound. I used to have headphone sound but have nothing now. I am running PinguyOS on my Macbook Pro 5,5 and it says I am running kernel 2.6.35-23-generic. 
Any assistance to get my sound up and running would be great!

---

### Post by larrinski on 2010-12-29
> **larrinski said:**
> Sorry to bump an old thread here, but it is very applicable to my problem.
I ran 'sudo rm -rf /lib/modules/`uname -r`/kernel/sound' and then 'sudo aptitude reinstall linux-headers-2.6.35-23-generic linux-image-2.6.35-23-generic linux-restricted-modules-2.6.35-23-generic' thinking that it would update but it says it couldn't find the modules. Now I have NO sound. I used to have headphone sound but have nothing now. I am running PinguyOS on my Macbook Pro 5,5 and it says I am running kernel 2.6.35-23-generic. 
Any assistance to get my sound up and running would be great!

Anyone able to help me? I've had no sound for a few weeks now and need some assistance...

---

### Post by larrinski on 2011-01-02
Got my solution to getting sound to work on the PinguyOS forum. 
I ran sudo apt-get update
Then sudo apt-get dist-upgrade. Rebooted and ran alsamixer and unmuted the front speakers...Sound! Woot...
Cheers.

---

### Post by Emranth on 2011-02-11
Apologies if this was discovered earlier and I missed it. I've spent hours and hours playing with alsamixer and countless other solutions on and off over the past year with various distros in various arrangements (single, double and triple boots) and never gotten more than sound from the headphone jack until today. Admittedly I'm ignorant of most things linux (probably because I end up spending the first few days with it fighting with things like this and that's a little discouraging) so don't expect some crazy terminal solution that edits 42 separate configuration files.

The steps that brought sound back into my life:
1. Boot from the Mac OS X install DVD
2. Restart without doing anything
3. Shout something in an exuberant manner, profanity and fist pumping are encouraged when you hear the Ubuntu startup theme

As far as I can tell nothing has changed in alsamixer since the reboot. The reason that I tried this was that prior to this I was running a Mac OS X/Windows 7 dual boot which defaulted to Windows 7. I always found it irritating that if OS X was not muted I would hear its startup theme when booting into Windows, regardless of what the volume was under Windows. OS X seemed to be far too ingrained with the dual boot and even now with only 10.10 installed I still briefly see a grey boot screen reminiscent of OS X. So how much control could OS X have from the grave? Apparently enough to keep the laptop muted.

Maybe someone more knowledgeable than me can figure out what was going on, I'm just happy this debacle is over.

---

### Post by dunsta on 2011-02-19
Hi, sorry to bring up an old problem again.
I am using mbp 5,5
ubuntu 10.10 2.6.35-25-generic

I tried to commands in post # 98, 
but when I tried
```
sudo aptitude reinstall linux-headers-2.6.28-13-generic linux-image-2.6.28-13-generic linux-restricted-modules-2.6.28-13-generic
```I got no packages installed, fair enough I have 35-25, so i substituted in those numbers
```
sudo aptitude reinstall linux-headers-2.6.35-25-generic linux-image-2.6.35-25-generic linux-restricted-modules-2.6.35-25-generic
```but I got a message "couldnt find linux-restricted-modules-2.6.35-25-generic"
but the other 2 did completed, so i ran the rest of the code after reboot
from wget - sudo make install
I have made sure front speakers aren't muted
but still no sound.
what should i do?

---

### Post by Faokryn on 2011-03-03
> **dunsta said:**
> Hi, sorry to bring up an old problem again.
I am using mbp 5,5
ubuntu 10.10 2.6.35-25-generic

I tried to commands in post # 98, 
but when I tried
```
sudo aptitude reinstall linux-headers-2.6.28-13-generic linux-image-2.6.28-13-generic linux-restricted-modules-2.6.28-13-generic
```I got no packages installed, fair enough I have 35-25, so i substituted in those numbers
```
sudo aptitude reinstall linux-headers-2.6.35-25-generic linux-image-2.6.35-25-generic linux-restricted-modules-2.6.35-25-generic
```but I got a message "couldnt find linux-restricted-modules-2.6.35-25-generic"
but the other 2 did completed, so i ran the rest of the code after reboot
from wget - sudo make install
I have made sure front speakers aren't muted
but still no sound.
what should i do?

First off, thank you!  I'm really new to Ubuntu and I was really lost trying to figure out how to fix my sound.  I had already found post #98, but it wouldn't work for me. I stumbled upon your post, and decided to try substituting "35-25" for "28-13".  And it worked!  I still got the same error you did, but at least the other two were installed.  Anyway, after a few more hours of frustrated web browsing, I decided to just go on to the next step in post #98, and after I tweaked my volumes, it worked!  As I said, I'm no authoritative source, but since it worked for me, maybe you should give it a try.

---

### Post by faust99 on 2012-02-23
> **dunsta said:**
> Hi, sorry to bring up an old problem again.
I am using mbp 5,5
ubuntu 10.10 2.6.35-25-generic

I tried to commands in post # 98, 
but when I tried
```
sudo aptitude reinstall linux-headers-2.6.28-13-generic linux-image-2.6.28-13-generic linux-restricted-modules-2.6.28-13-generic
```I got no packages installed, fair enough I have 35-25, so i substituted in those numbers
```
sudo aptitude reinstall linux-headers-2.6.35-25-generic linux-image-2.6.35-25-generic linux-restricted-modules-2.6.35-25-generic
```but I got a message "couldnt find linux-restricted-modules-2.6.35-25-generic"
but the other 2 did completed, so i ran the rest of the code after reboot
from wget - sudo make install
I have made sure front speakers aren't muted
but still no sound.
what should i do?

I don't use a mbp anymore so i'm a bit behind on installations for it, but i did have a 5,5 with 10.4 and i never had to reinstall the kernel to get sound working. I do recall that i took a few fresh installs to get it going though-the mbp gave the impression of being anti-anything that was not mac os. anyway, 10.11 worked out of the box from memory.

you've probably tried this, but it's all i can think of right now: [https://help.ubuntu.com/community/MacBookPro5-5/Maverick]("https://help.ubuntu.com/community/MacBookPro5-5/Maverick")

good luck

---

