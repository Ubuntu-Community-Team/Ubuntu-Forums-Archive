---
title: "surround on Audigy (ca0106) .asoundrc file, (combine settings)"
date: 2007-10-21
forum: Absolute Beginner Talk
---

### Post by studo77 on 2007-10-21
Ok, here goes.

I have my Creative Audige SE card, chip ca0106

Sound is working pretty ok. But i have two sets of .asoundrc i would like to combine.

The first is where i get a mix of stereo to 5.1, and this i done by:
Found on [http://pastebin.ca/464795?srch=upmix]("http://pastebin.ca/464795?srch=upmix")
```
pcm.!dmix {
   type plug
   slave {
       pcm surround51
       channels 6
   }
}
pcm.!default {
   type plug
   slave.pcm "dmix"
   slave.channels 6
   route_policy duplicate
}
```

This upmixes my stereo, and lets 5.1 audio through. But, it does not let me play multiple audiosources.

This next one is found at
[http://ubuntuforums.org/showthread.php?t=285065]("http://ubuntuforums.org/showthread.php?t=285065")

Which i cut down to only analog:
```
# Override the default output used by ALSA.
# If you do not override the default, your default
# device is identical to the (unmixed) analog device
# shown below.  If you prefer mixed and/or digital
# output, uncomment the appropriate four lines below
# (only one slave.pcm line).
### comment out this entire section to use unmixed
pcm.!default {
  type plug
  slave.pcm "dmix-analog"

}

# Alias for analog output on the Audigy (hw:0,0)
# - This is identical to the device named "default"--which
# always exists and refers to hw:0,0 (unless overridden)
# - Therefore, we can specify "hw:0,0", "default", or "analog"
# to access analog output on the Audigy
pcm.analog {
 type plug
 slave.pcm "analog-hw"
}

# Control device (mixer, etc.) for the Audigy card
ctl.analog {
 type hw
 card 0
}

# Alias for (rate-converted) mixed analog output on the
# Audigy (hw:0,0)
#  - This will accept audio input--regardless of rate--and
# convert to the rate required for the dmix plugin
# (in this case 48000Hz)
pcm.mixed-analog {
 type plug
 slave.pcm "dmix-analog"
}

# Control device (mixer, etc.) for the Audigy card
ctl.mixed-analog {
 type hw
 card 0
}




# The following devices are not useful by themselves.  They
# require specific rates, channels, and formats.  Therefore,
# you probably do not want to use them directly.  Instead use
# of of the devices defined above.

# Alias for analog output on the Audigy (hw:0,0)
# Do not use this directly--it requires specific rate,
# channels, and format
pcm.analog-hw {
 type hw
 card 0
 # The default value for device is 0, so no need to specify
}

# Control device (mixer, etc.) for the Audigy card
ctl.analog-hw {
 type hw
 card 0
}


# Direct software mixing plugin for analog output on
# the Audigy (hw:0,0)
# Do not use this directly--it requires specific rate,
# channels, and format. You can edit the rate to use 
# another sampe rate like 9600
pcm.dmix-analog {
 type dmix
 ipc_key 1234
 slave {
   pcm "analog-hw"
   period_time 0
   period_size 1024
   buffer_size 4096
   rate 48000
 }
}

# Control device (mixer, etc.) for the Audigy card
ctl.dmix-analog {
 type hw
 card 0
}

```

This plays multiple audiosources, and lets 5.1 pass through. 

BUT it only plays stereo on front speakers.

I tried putting 
       pcm surround51
       channels 6

and
   slave.channels 6
   route_policy duplicate

Into the multiple working, where i thought they belonged, but then my soundcard gets locked up.
And letting all lines in the .asoundrc also gives troubles.

So how do i combine the two? Where to put in lines from the first, into the second to get a working .asoundrc?
And if i am very lucky, also explanation on why...

If i get the right answer i will post it on other posts on nearly the same issue, but the posts are dead, and long time since. (pops up on query)

---

### Post by studo77 on 2007-10-21
Bonusinfo:
If i use a
```
pcm.ch51dup {
         slave.pcm surround51
         slave.channels 6
         type route
         ttable.0.0 1
         ttable.1.1 1
         ttable.0.2 1
         ttable.1.3 1
         ttable.0.4 0.5
         ttable.1.4 0.5
         ttable.0.5 0.5
         ttable.1.5 0.5
}
```

to distribute the sound, i get sound on all 5.1 speakers, but the sound is very choppy, and not listenable.

---

