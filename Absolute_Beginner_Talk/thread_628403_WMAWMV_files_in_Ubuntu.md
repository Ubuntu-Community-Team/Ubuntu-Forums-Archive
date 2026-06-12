---
title: "WMA\WMV files in Ubuntu"
date: 2007-12-01
forum: Absolute Beginner Talk
---

### Post by subs on 2007-12-01
I am having lot of trouble running WMA or WMV files in rhythmbox / mplayer / totem....

whatever tutorials i could find on the net.... were for dapper or edgy.....

can some one give me the exact procedure to install the necessary codecs to run these files on gutsy(7.10)

---

### Post by subs on 2007-12-01
bump

---

### Post by tommcd on 2007-12-01
Install ubuntu-restricted-extras using apt-get or synaptic. First make sure you have the universe and multiverse sources added to your sources.list
[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)
Install the libdvd* stuff and the w32 codecs from medibuntu:
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

You can easily find this stuff in the forums by searching. Post back if you need more help.

---

### Post by ikt on 2008-01-04
> **tommcd said:**
> Install ubuntu-restricted-extras using apt-get or synaptic. First make sure you have the universe and multiverse sources added to your sources.list
[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)
Install the libdvd* stuff and the w32 codecs from medibuntu:
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

You can easily find this stuff in the forums by searching. Post back if you need more help.

If these don't work, Install VLC media player and Audacious and gxine and something magical happens.. and then your WMV video with WMA audio will play in gxine.

Should probably report as a bug or something :s

---

