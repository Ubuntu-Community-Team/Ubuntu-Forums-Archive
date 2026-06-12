---
title: "(Macbook) Sound almost on par with OS X, need help with Headphones"
date: 2009-07-20
forum: Apple Hardware Users
---

### Post by ian_hawdon on 2009-07-20
Ever since I put any GNU/Linux on this macbook (2,1) the sound hasn't been as good on speakers as OS X or Windows, the problem it turned out was that the bass speaker was actually the right rear speaker, so anything on the left was just tinny, whilest the right channel had a fuller sound.

I decided to take action, to make things easier, I removed pulseaudio:

```
sudo apt-get remove pulseaudio
```

and edited my .asoundconf to the following:

```
# ALSA library configuration file

# Include settings that are under the control of asoundconf(1).
# (To disable these settings, comment out this line.)
</home/ian/.asoundrc.asoundconf>

pcm.!default plug:monobass
ctl.!default {
  type hw
  card ICH7
}

pcm.snd_card {
     type hw
     card 0 # change to your cards number or name
}


# 6 channel dmix:
pcm.dmix6 {
     type dmix
        ipc_key 1024
        ipc_key_add_uid false # let multiple users share
        ipc_perm 0660 # IPC permissions (octal, default 0600)
        slave {
                pcm snd_card # see below
                rate 48000
                channels 4 
                period_time 0
                period_size 1024 # try 2048 against skipping
                buffer_time 0
                buffer_size 5120 # in case of problems reduce this
                                 # in case of skipping, try increasing
        }
     }

pcm.monobass {
       type route;
       slave.pcm dmix6 
  slave.channels 4 
  ttable.0.0 1
  ttable.1.1 1
  ttable.0.3 1 # copy front left to rear right
  ttable.1.3 1 # copy front right to rear right
  ttable.4.3 1 # copy center to rear right

  ttable.2.0 1
  ttable.3.1 1
  ttable.4.0 1
  ttable.4.1 1
  ttable.6.0 1
  ttable.7.1 1

}


```

As you can see, the left, centre (yeah, I spelt it with US English in the config) and right channels are all sent to the right rear speaker, and now sound is great on speakers!

The down side is, now the headphones are producing nothing in the left, and the mono mix in the right (basically doing what the rear speakers are doing)

Anyone have any ideas how to make the headphone channel map to the front left and right mixes?

cheers

---

### Post by ian_hawdon on 2009-07-22
bump

---

### Post by ian_hawdon on 2009-07-23
shameless bump!

---

### Post by ian_hawdon on 2009-07-25
bump

---

### Post by ian_hawdon on 2009-07-27
bump

---

### Post by ian_hawdon on 2009-07-28
bumping again

---

### Post by ian_hawdon on 2009-08-02
bump

---

### Post by ian_hawdon on 2009-08-07
bump

---

### Post by Bearded-flower on 2009-08-08
WOW, bump

---

### Post by ian_hawdon on 2009-10-11
a bumpdate, still having problems getting Stereo sound on the headphone jack, but at least things are more balanced on the speakers with this new asound:

```
# ALSA library configuration file

pcm.!default plug:monobass
ctl.!default {
  type hw
  card ICH7
}

pcm.snd_card {
     type hw
     card 0 # change to your cards number or name
}


# 6 channel dmix:
pcm.dmix6 {
     type dmix
        ipc_key 1024
        ipc_key_add_uid false # let multiple users share
        ipc_perm 0660 # IPC permissions (octal, default 0600)
        slave {
                pcm snd_card # see below
                rate 48000
                channels 4 
                period_time 0
                period_size 1024 # try 2048 against skipping
                buffer_time 0
                buffer_size 5120 # in case of problems reduce this
                                 # in case of skipping, try increasing
        }
     }

pcm.monobass {
       type route;
       slave.pcm dmix6 
  slave.channels 4 
  ttable.0.0 1
  ttable.1.1 1
#  ttable.0.2 0.5 # copy front left to rear left for mono headphone output (rather than just the right speaker)
#  ttable.1.2 0.5 # copy front right to rear left for mono headphone output (rather than just the right speaker)
  ttable.0.3 0.5 # copy front left to rear right
  ttable.1.3 0.5 # copy front right to rear right
#  ttable.4.3 1 # copy center to rear right <-- NEVER ENABLE THIS EVER, IT JUST SOUNDS AWFUL!!!!

  ttable.2.0 1
  ttable.3.1 1
  ttable.4.0 1
  ttable.4.1 1
  ttable.6.0 1
  ttable.7.1 1

hint {
show on
description "INTEL-HDA-bass"
}

}

```

This works on KDE4 too, uncomment the two referring to headphones to get both speakers working on the headphone jack, the sound is sadly true mono, this is why I'm here!

---

