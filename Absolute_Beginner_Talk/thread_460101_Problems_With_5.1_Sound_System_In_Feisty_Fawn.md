---
title: "Problems With 5.1 Sound System In Feisty Fawn"
date: 2007-05-31
forum: Absolute Beginner Talk
---

### Post by wikiguy on 2007-05-31
HEY GUYS PLEASE HELP ME , IVE JUST BOUGHT A 5.1 SOUND SYSTEM BUT I CAN´T HEAR LEFT AND RIGHT CHANNELS , I CAN ONLY HEAR THE CENTER(THE ONE THAT IS PLUGGED  IN THE GREEN JACK) :( CAN ANYONE HELP ME , IVE A AC `97 TYPE SOUND CARD , REALTEK TO BE MORE SPECIFIC,ACTUALLY IM RUNNING AN AMD 64 UBUNTU FEISTY FAWN VERSION.

THANKS FOR YOUR HELP GUYS:p

---

### Post by wikiguy on 2007-07-15
well, ive solved myself,

:-\":-\":-\"

you just need to install gnome alsa-mixer using synaptic

then in command window do a :

asoundconf list

this will display the number of soundcards thatyou have plugged in.In my case is a realtek ac'97 so it displayed   " ICH"

then do a :


asoundconf set-default-card "the name of the card"

in my case is

 asoundconf set-default-card ICH

alright we almost finish:o

then in terminal type this:

GNOME:

gedit ~/.asoundrc

KDE:

kedit ~/.asoundrc


then copy and paste this:




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
                channels 6
                period_time 0
                period_size 1024 # try 2048 against skipping
                buffer_time 0
                buffer_size 5120 # in case of problems reduce this
                                 # in case of skipping, try increasing
        }
     }

# upmixing: 
pcm.ch51dup {
        type route
        slave.pcm dmix6
        slave.channels 6
        ttable.0.0 1
        ttable.1.1 1
        ttable.0.2 1
        ttable.1.3 1
        ttable.0.4 0.5
        ttable.1.4 0.5
        ttable.0.5 0.5
        ttable.1.5 0.5
   }

pcm.duplex {
     type asym
     playback.pcm "ch51dup" # upmix first
#     playback.pcm "dmix6"  # just pass to 6 channel dmix
#     capture.pcm "dsnoop:0" # doesn't work for me
     capture.pcm "snd_card"
}

# change default device:
pcm.!default {
     type plug
     slave.pcm "duplex"
}





AND THATS ALL SAVE AND REBOOT YOUR MACHINE:guitar:

---

