---
title: "No headphone sound; iMac 21.5&quot;, 12,1; patch_cirrus.c; imac27_122"
date: 2012-06-21
forum: Apple Hardware Users
---

### Post by benzodiaz on 2012-06-21
Hi,

The title says most of the issue, but the critical issue is that I don't know why I can't find patch_cirrus.c.  I was trying to solve the problem with Lunarts and friends, but what worked for them didn't work for me; i.e., adding the line:
options snd-hda-intel model=imac27_122,
to /etc/modprobe.p/alsa-base.conf, then, restarting the computer.

Does Lubuntu not have the file patch_cirrus.c?
How does it build the list of alsa options?

Please let me know if you need additional information.

Thanks,
-J

---

### Post by gordintoronto on 2012-06-21
It took me 30 seconds to find this patch by using Google:
[http://tomoyo.sourceforge.jp/cgi-bin/lxr/source/sound/pci/hda/patch_cirrus.c](http://tomoyo.sourceforge.jp/cgi-bin/lxr/source/sound/pci/hda/patch_cirrus.c)

It never hurts to mention what operating system you are using. Apparently Lubuntu, but what version?

---

### Post by benzodiaz on 2012-06-22
I'm using Lubuntu 12.04, Mac 64 bit.

Re: Ubuntu 12.04 on imac 2011, no headphone sound,

that issue was solved.  However, the solution doesn't work for my system and the only difference is that I am using Lubuntu, while Lunarts is using Ubuntu.  The solution was as follows:

> There is no need to apply the patch above, because it is already there on your ubuntu, my procedure:

1 - By logic recognized which the lines in green mean the extra fix lines of the patch

2 - using gksudo nautilus, then nautilus search feature, located the patch_cirrus.c and entered there with full write privileges(due to gksudo)

3 - using gedit search feature discovered which one of the patch green lines was already there.

After some additional thinking I noticed which one of the patch lines is close to other lines whose content are exactly used on /etc/modprobe.d/alsa-base.conf to solve such kind of problems. The alsa list of supported models for the cirrus codec is not updated yet to include that(not sure if it will); no matter if you get the list from your own ubuntu or from the internet. There was no way to know this model existed without benzodiaz help.

So, open your terminal and:

1 - sudo gedit /etc/modprobe.d/alsa-base.conf

2 - add to end of the file "options snd-hda-intel model=imac27_122"(only the stuff inside the quotes), save and reboot.

This worked for me, the only fix from several and several others I tried. What a pleasant surprise, the fix was already there since this year january, it was only hidden.

PS: Thanks a lot for the tip benzodias

Re: the fact that the file patch_cirrus.c has already been applied in the 3.2.0-25-generic kernel for Ubuntu, says that we can add the mac27_122 option and we have a solution.

My filesystem doesn't contain the file patch_cirrus.c, which seems to build the alsa driver database in some way...

Let me know what you think.

---

### Post by gordintoronto on 2012-06-22
Ubuntu does not include kernel source code, so there is no reason you would have that C program on your system.

If I were you, I would Google other things to try in "model=imac...." unless you are sure your imac is a "27_122" I would certainly try the simple case: model=imac

To further identify your hardware, open Terminal and run this command:
sudo lshw -html > Desktop/config.htm

This should place a file on your desktop; double-click on it to open it in your browser. Search for "Audio device" and "product" might give you something new to plug into Google.

---

### Post by benzodiaz on 2012-06-27
I have a solution that works good enough for me.  This is what I did:

1. In a terminal, paste the line in the quotations, "sudo wget -O run.py http://www.alsa-project.org/hda-analyzer.py"

2. Then paste this, "sudo python run.py", and it will open what's called HDA Analyzer.

3. Click codec-0 on the left hand side, under Nodes. Where it says GPIO, uncheck out-dir, enable, and data for the row [1], and check them for row [2].  If you had your headphones on when you checked data [2], you should get output.

4. At the bottom, click Exp., save as, and save it in your home directory.

5. Open gedit and type, "gksu python /path/to/previously/saved/file" and save it in your home directory.  Go to the gedit file you just made, right click and go to properties, click the permissions tab, and check make this file executable.

7. Whenever your headphones don't work and they should, open a terminal, Ctrl+Alt+t, and type the name of the gedit file you created. This reloads the settings you made in hda analyzer.

Thanks for everybody's help!
Cheers,
benzo

---

### Post by renws on 2012-06-27
That worked for me, thanks a lot.

I'm wondering how you found the solution.


> **benzodiaz said:**
> I have a solution that works good enough for me.  This is what I did:

1. In a terminal, paste the line in the quotations, "sudo wget -O run.py http://www.alsa-project.org/hda-analyzer.py"

2. Then paste this, "sudo python run.py", and it will open what's called HDA Analyzer.

3. Click codec-0 on the left hand side, under Nodes. Where it says GPIO, uncheck out-dir, enable, and data for the row [1], and check them for row [2].  If you had your headphones on when you checked data [2], you should get output.

4. At the bottom, click Exp., save as, and save it in your home directory.

5. Open gedit and type, "gksu python /path/to/previously/saved/file" and save it in your home directory.  Go to the gedit file you just made, right click and go to properties, click the permissions tab, and check make this file executable.

7. Whenever your headphones don't work and they should, open a terminal, Ctrl+Alt+t, and type the name of the gedit file you created. This reloads the settings you made in hda analyzer.

Thanks for everybody's help!
Cheers,
benzo

---

### Post by Lunarts on 2012-06-28
Glad you had found a solution, I have been busy with some things and when I came back to check your issue, it was already solved.

patch_cirrus.c included in ubuntu did exactly what you had done but in a simpler way(just changing model at alsa-conf was needed). The issue was wrong mapping of where the headphone jack was as said at the page you first presented me before, which solved my problem.

I too had tried HDAnalyser before, thought forgot to mention. It is the tool for the job if everything else fails and you know how to use it.

I got two patch_cirrus.c, one under /usr/src/alsa-hda-0.201206181122~precise1 and other under /var/lib/dkms/alsa-hda/0.201206181122~precise1/build. Maybe by locating these two alsa-hda folders at lubuntu(if any) and inserting a ubuntu patch_cirrus.c copy at each(and using model 27_122) would also had solved your problem, but I´m not sure.

PS1: Patch_cirrus.c do exist in ubuntu(at lubuntu it seems it doesn´t), it was commited long ago.
PS2: The apple model 27_122 does not exist, it is a patch which solves the issues for a 27 imac, thought it also solves it for 21,5 imac as the patch creators mentioned.

---

### Post by oqwolq on 2012-11-19
Hi all,

this thread solved the problem for me a few months ago. Now after updating ubuntu last week I get an error message. Pending updates had accumulated for maybe two months up to that day, so I can't say which one precisely caused the error. (...which is why updates tend to accumulate in the first place)

> ~$ sudo python run.py
Using temporary directory: /dev/shm/hda-analyzer
You may remove this directory when finished or if you like to
download the most recent copy of hda-analyzer tool.
Downloading file hda_analyzer.py
Downloading file hda_guilib.py
Downloading file hda_codec.py
Downloading file hda_proc.py
Downloading file hda_graph.py
Downloading file hda_mixer.py
Downloaded all files, executing hda_analyzer.py
Traceback (most recent call last):
  File "/dev/shm/hda-analyzer/hda_analyzer.py", line 546, in <module>
    sys.exit(main(sys.argv))
  File "/dev/shm/hda-analyzer/hda_analyzer.py", line 523, in main
    if read_nodes(sys.argv[1:]) == 0:
  File "/dev/shm/hda-analyzer/hda_analyzer.py", line 89, in read_nodes
    read_nodes2(c.card, i)
  File "/dev/shm/hda-analyzer/hda_analyzer.py", line 60, in read_nodes2
    c = HDACodec(card, codec)
  File "/run/shm/hda-analyzer/hda_codec.py", line 1036, in __init__
    self.parse_proc()
  File "/run/shm/hda-analyzer/hda_codec.py", line 1135, in parse_proc
    self.proc_codec = HDACodecProc(self.card, self.device, file)
  File "/run/shm/hda-analyzer/hda_proc.py", line 478, in __init__
    self.parse(proc_file)
  File "/run/shm/hda-analyzer/hda_proc.py", line 672, in parse
    node.add_digital(line[11:]) 
  File "/run/shm/hda-analyzer/hda_proc.py", line 295, in add_digital
    self.wrongfile('unknown dig1 bit %s' % repr(b))
  File "/run/shm/hda-analyzer/hda_proc.py", line 143, in wrongfile
    raise ValueError, "wrong proc file format (%s)" % msg
ValueError: wrong proc file format (unknown dig1 bit 'Non-Copyright')

Any help would be appreciated.

---

### Post by benzodiaz on 2012-11-26
Hmm. I get the same error.  Seems like now we have a problem with HDA Analyzer?

Anyone have a suggestion?

---

### Post by oqwolq on 2012-12-07
Now in short - who has ubuntu 12.04 running on an iMac won't be able to connect headphones or any sound system.1:icon_frown:

---

### Post by Comsol4 on 2013-01-29
Troller here hoping to be able to help.

I have
27" iMac 2011 model
Ubuntu 12.04 x64
When i used the HDAAnalyzer the headphones/external analog speakers did begin working, but the tinny annoying internal speakers were still blaring.  I found the following settings in HDAAnalyzer to work for me:


Out-Dir [2] [3] checked
enable  [2] checked
unsol   (none)
sticky  (none)
wake    (none)
data    [2] [3] checked

Here is a screen shot:
[IMG]https://lh4.googleusercontent.com/-SGFnrRROS54/UQf_BRyHqjI/AAAAAAAAB_0/mjTuY1gzXrY/s802/HDAANalyzer.png[/IMG]


Thanks everyone!

---

### Post by benzodiaz on 2013-02-07
So, for some reason, I got hdaAnalyzer to run.

The above fix should work if you can get hdaanalyzer to run.

Just follow the steps and reply if you can't get it.

Thanks for the pic Comsol4.  With sound playing, you should be able to play with out-dir, enable, and data to turn the sound off for the speakers and on for the headphone jack.

This time around I Exported (by clicking the Exp button) the state, copied the text into a blank file, named it speakers.py.  Then clicked the boxes to get the headphones on and speakers off, exported that to a file I called headphones.py.  Then I made 2 bash scripts, speakers.sh and headphones.sh, and placed them in my home folder with speakers.py and headphones.py.  This is all that`s in the speakers.sh file:

#!/bin/bash
speakers.py &

Do the same for headphones.sh, make them executable, then when you want to listen to the headphones, open a terminal and type headphones.sh, then hit enter. Done. Same for speakers.sh.

Cheers,

benzo

---

### Post by vincebs on 2014-01-17
Has anyone got this working on an iMac 14,1?

When I try to run hda-analyzer, it fails to load with an error: "ValueError: wrong proc file format (unknown dig1 bit 'KAE')"

Then I tried adding "options snd-hda-intel model=imac27_122" to alsa-base.conf. That doesn't work either.

Here's my alsa-base.conf:
```
# autoloader aliases
install sound-slot-0 /sbin/modprobe snd-card-0
install sound-slot-1 /sbin/modprobe snd-card-1
install sound-slot-2 /sbin/modprobe snd-card-2
install sound-slot-3 /sbin/modprobe snd-card-3
install sound-slot-4 /sbin/modprobe snd-card-4
install sound-slot-5 /sbin/modprobe snd-card-5
install sound-slot-6 /sbin/modprobe snd-card-6
install sound-slot-7 /sbin/modprobe snd-card-7

# Cause optional modules to be loaded above generic modules
install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-ioctl32 ; /sbin/modprobe --quiet --use-blacklist snd-seq ; }
#
# Workaround at bug #499695 (reverted in Ubuntu see LP #319505)
install snd-pcm /sbin/modprobe --ignore-install snd-pcm $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; /sbin/modprobe --quiet --use-blacklist snd-seq-oss ; : ; }
#
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; : ; }
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist saa7134-alsa ; : ; }
# Prevent abnormal drivers from grabbing index 0
options bt87x index=-2
options cx88_alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-caiaq index=-2
options snd-usb-ua101 index=-2
options snd-usb-us122l index=-2
options snd-usb-usx2y index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
# Keep snd-pcsp from being loaded as first soundcard
options snd-pcsp index=-2
# Keep snd-usb-audio from beeing loaded as first soundcard
options snd-usb-audio index=-2
options snd-hda-intel model=imac27_122

```

Any ideas?

---

