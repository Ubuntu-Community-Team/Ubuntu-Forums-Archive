---
title: "rmvb playing with no video ,only audio"
date: 2007-07-13
forum: Absolute Beginner Talk
---

### Post by romihim on 2007-07-13
this is strange but is actually happening . 
when i run a rmvb file in mplayer it warns me in starting that no codec is installed for this particular format. i click yes to detect format  library . it points me out to some gstreamer library which is already installed(so then why that warning!!!!!!)
But to much of my surprise mplayer then plays that rmvb file ,but without video. only audio . 
same is the case with vlc player
in addition to gstreamer library's i have also installed w32codecs(all) but rmvb file is not playing.
i have figured out ,it is only supporting audio for real media .
i don't want to install 10 different media players for 10 diff. formats ,so not installing real player yet .
help me to correct it 

and one more thing ,that rmvb(video) file is not corrupt ,its working fine in xp.

---

### Post by digital_sabotage on 2007-07-13
open mplayer ...right click and select 'preferences' ...go to the 'video' tab ...try different video drivers ...i'm using 'gl'

...hope this helps ...good luck:-)

---

### Post by romihim on 2007-07-13
Problem is sorted out 
i was using totem mplayer(the one which comes by default in ubuntu), so it was its problem 
now i have mplayer . Its workin fine 
thanks digital_sabotage i actually had to select driver to make mplayer workin

---

### Post by kenchuamy@gmail.com on 2008-05-14
hi, everyone 
i face this problem for 2 days with i downloaded the new ubuntu 8.04, but finally i found solution in my daily....before.

Just go to terminal copy and paste this code
wget -c [http://packages.medibuntu.org/pool/non-free/w/w32codecs/w32codecs_20071007-0medibuntu2_i386.deb](http://packages.medibuntu.org/pool/non-free/w/w32codecs/w32codecs_20071007-0medibuntu2_i386.deb)
sudo dpkg -i w32codecs_20071007-0medibuntu2_i386.deb

i'm newbie, i try all solution in 2 days( refer to forum ), finally i can watch my rmvb movie. 

if anyone have any problem please refer to the website below.

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

thanks everyone for helping me....

100% ubuntu user

regard,

ken

---

### Post by rushtoshankar on 2008-05-22
Thank you verymuch ! it is working !

---

### Post by aparigraha on 2008-06-24
Or if you are on a AMD64 system:

```
wget -c http://packages.medibuntu.org/pool/non-free/w/w64codecs/w64codecs_20071007-0medibuntu1_amd64.deb
sudo dpkg -i w64codecs_20071007-0medibuntu1_amd64.deb
```

Works excellent with Mplayer.

---

