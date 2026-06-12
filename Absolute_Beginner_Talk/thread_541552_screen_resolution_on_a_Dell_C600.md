---
title: "screen resolution on a Dell C600"
date: 2007-09-02
forum: Absolute Beginner Talk
---

### Post by Rev_neil on 2007-09-02
Hi All,
         im really new here and i Love it but i have a small prob.i put 7.04 in  my old p3 dell c600 and its Brilliant apart from the fact that the max screen resolution i can get is 800x600 which sucks as every window that opens is huge and i have to keep deleting the bottom panel to click "ok" on anything that needs it.
Please dont say "oh just dpkg-configure x-server-xorg" or something like that  as after a day of trying every setting known to man in x-server i had to reinstall and start over. 

But apart from that, i dunno why i never heard of Linux before as it Rocks. i mainly use lappy for poker and as you can't resize the Tables, its a bit of a drama as the table is bigger than the screen, but  can still play so its not that bad..

Be Excellent to Each Other
Thanks..........
neil

---

### Post by overdrank on 2007-09-02
> **Rev_neil said:**
> Hi All,
         im really new here and i Love it but i have a small prob.i put 7.04 in  my old p3 dell c600 and its Brilliant apart from the fact that the max screen resolution i can get is 800x600 which sucks as every window that opens is huge and i have to keep deleting the bottom panel to click "ok" on anything that needs it.
Please dont say "oh just dpkg-configure x-server-xorg" or something like that  as after a day of trying every setting known to man in x-server i had to reinstall and start over. 

But apart from that, i dunno why i never heard of Linux before as it Rocks. i mainly use lappy for poker and as you can't resize the Tables, its a bit of a drama as the table is bigger than the screen, but  can still play so its not that bad..

Be Excellent to Each Other
Thanks..........
neil

Hi and ok I wont instruct you to reconfigure your xorg but you may have to edit it :)
This link may help
[http://ubuntuforums.org/showthread.php?t=83973&highlight=resolution](http://ubuntuforums.org/showthread.php?t=83973&highlight=resolution)
Good luck!

---

### Post by Papa-san on 2007-09-02
Hi,

I also am running Ubuntu on a Dell Lattitude C-600. The problem you are running into is the same one that ended up driving me back to Dapper.  I had many people give me some great suggestions, and I might be able to link to those threads if you would like. What I ran int after manually editing my xserver, xorg.conf, etc was that I got the resolution I was looking for (1024x768), however I ended up getting an irresoluable issue in exchange. I would get hard system lock ups randomly, frequently, and in a manner that was unable to be tracked down by the suggestions of dozens of folks. 

I don't know if anyone has ever managed to track it down, as I ended up going with Dapper, and have trult been tickled pink ever since. I'm not sure even what is so different in 7.06, but in the two months I fought with it, I never really saw anything that set it apart from Dapper. (I actually had much more severe problems getting my wireless to work. Wireless stunk for 5.10 and 7.06. 6.10 was seamless.How did that go for you? Or do you not have wireless?) let me know if you want to try editing xorg.conf and stuff...

EDIT: After reading the previous post, please let me know how much success you have with that. It seems eerily similar to what I did, though.

Here is a thread that evidently is successful on a C-600 specifically: [http://ubuntuforums.org/showthread.php?t=411489](http://ubuntuforums.org/showthread.php?t=411489)

---

### Post by Rev_neil on 2007-09-03
hi guys
              ill have a look and give it a go later when i have a bit of time,, Yea no probs the wireless got picked up during install ? as just works and i have no real other probs (apart from the update manager just hanging). but im new and havn't really played around much. all i know is that as im not a gamer, this is Brilliant and does everything ive needed so far..

thanks again and ill get back to ya's  with the results :)



neil

---

### Post by alienexplorers on 2007-09-03
adding a modeline to your xorg.conf monitor section may help get other modes working.  See the following example:
> Section "Monitor"
    Identifier     "Monitor0"
    HorizSync       28.0 - 70.0
    VertRefresh     43.0 - 120.0
    ModeLine       "1280x1024_65.00" 119.4 1280 1368 1504 1728 1024 1025 1028 1063 -hsync +vsync
    Option         "DPMS"
EndSection

Modelines can be generated using either of these two sites:
> [http://www.sh.nu/nvidia/gtf.php](http://www.sh.nu/nvidia/gtf.php)

[http://www.bohne-lang.de/spec/linux/modeline/](http://www.bohne-lang.de/spec/linux/modeline/)

---

### Post by Rev_neil on 2007-09-03
!#%$ yea,,,,,,,,,,,,,,

                       Here is a thread that evidently is successful on a C-600 specifically: [http://ubuntuforums.org/showthread.php?t=411489](http://ubuntuforums.org/showthread.php?t=411489)

 thanks  Papa-san...  it worked,  did as he said, copy/pasted into where said, rebooted . Checked my options the 1024x728  was there..  yay and now all good  

Thank you guys soo much, this is reallly Amazing how cool  & helpfull people are..



Be Excellent to each other :) 

neil

---

