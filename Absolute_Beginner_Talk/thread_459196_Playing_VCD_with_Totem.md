---
title: "Playing VCD with Totem"
date: 2007-05-30
forum: Absolute Beginner Talk
---

### Post by pyramid on 2007-05-30
Folks, I am using Fiesty Fawn and already a fan of it. I cannot play VCDs with my Totem-Xine or Gstreamer, installed MPlayer and tried but no success. Getting the following error msg

Totem could not play 'vcd:///media/cdrom0'.
There is no input plugin to handle the location of this movie

Does anyone has a solution for this.

---

### Post by Inxsible on 2007-05-30
do you have all the necessary codecs installed ?

you error looks more like a mounting issue or that the drive isnt being recognized. Could you post your fstab ?

```
gedit /etc/fstab
```

copy and paste the contents here

---

### Post by mahiyar on 2007-05-30
Even for me Totem could not handle VCD play, not in edgy neither in feisty. I'am using mplayer. For mplayer to work you have to go to preferrences>video and select the proper video codec (try all and see what works).

---

### Post by rajeev1204 on 2007-05-30
Feisty cannot play VCD because it is not properly mounted .Its a confirmed bug in feisty . ( I filed it by the way ;) )

Its not the fault of the players but a system thing i guess ( kernel ?)

There is no icon on the desktop which appears when u insert  a vcd .

DVD and data cd mounts fine .

Dapper does not have this issue but yes totem could never play a vcd then or now . Mplayer or gxine worked fine for dapper.

In Feisty Mplayer plays it badly and vlc spits out a lot of errors or sometimes does not play at all . Neither does gxine play it

Another thing u will notice is that u cannot copy files from the vcd to ur hard disk  in feisty .



regards

rajeev

---

