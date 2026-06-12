---
title: "ati xgl,windows not moving"
date: 2006-08-24
forum: Absolute Beginner Talk
---

### Post by deadspeak on 2006-08-24
i managed to get xgl installed, and working the other day, but since had to do a reinstall followed the same instuctions [http://www.tectonic.co.za/view.php?id=916]("http://www.tectonic.co.za/view.php?id=916") but for some reason my windows no longer have the orange bar with the min, max, and close buttons, and as a consequence i can't drag the windows around.

hope you can come to my aid again
thanks
Paul

---

### Post by charles.g.moore on 2006-08-24
When I first got mine working the buttons were missing also

I had to right click the app in the panel and tell it to max/min and then the buttons appeared

---

### Post by deadspeak on 2006-08-24
nope it's having none of it. it's weird because the windows seem to be stuck to the ltop of the screen

---

### Post by PriceChild on 2006-08-24
Yeah... it seems like your xompiz has had trouble loading... any chance of posting what happens in terminal when you do the startup script?

ALso, i REALLY reccomend using the how-tos here instead: [http://ubuntuforums.org/showthread.php?t=148351](http://ubuntuforums.org/showthread.php?t=148351)

Finally, Please remember that xgl/compiz is not beginners stuff :P Its not reccomended for anyone not comfortable with rescuing from the command line.

---

### Post by Greycloak on 2006-08-24
I haven't been able to get Xgl/compiz working on my ATI either.  You can get your window decoration back by entering the following:

```
metacity --replace
```

---

### Post by deadspeak on 2006-08-24
check this out [http://www.compiz.net/viewtopic.php?id=389]("http://www.compiz.net/viewtopic.php?id=389")
just finished setting up taken about 30mins and it's awsome, i've only got a radeon 9550 and it's holding up pretty well

---

### Post by greatmetal on 2006-08-25
Okay I have a radeon 9550 and direct rendering says no how do I turn it on?

---

### Post by deadspeak on 2006-08-25
have you got your drivers all up to date etc [http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide#Installing_the_driver]("http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide#Installing_the_driver")

---

### Post by greatmetal on 2006-08-25
yep it still says Mesa and not ATI

---

### Post by srusso on 2006-08-25
I have the same issue ATi 9700Pro, my top bar "was" gone... thanx for the temp fix. Everything is moving chopy. I followed [http://www.compiz.net/viewtopic.php?id=389](http://www.compiz.net/viewtopic.php?id=389) to the tie and install worked just as planned, restarted and missing bar and chopyness](*,) ](*,) ](*,)

---

### Post by greatmetal on 2006-08-25
well thanks for your help xgl isnt really worth it mabey

---

### Post by llamakc on 2006-08-25
The above link works for me also. However it doesn't reapply the theme I have chosen with the cgwd Themer from an earlier session.

My /usr/bin/startcompiz script is in my sessions as the first thing and looks like:

#!/bin/sh 
killall gnome-window-decorator 
wait

gnome-window-decorator & 
compiz --replace gconf &

and is 755.

I've also noticed that the compiz icon isn't in the notification tray as it was with aiglx. 

How can I get xgl/compiz/cgwd to use my theme after I login without having to rerun startcompiz, and then cgwd --replace from the command line?

Has anybody else seen this behavior?

---

### Post by Crosbie on 2006-08-25
Try replacing gnome-window-decorator in that script with cgwd.

Cgwd is the latest window-decorator manager with Compiz.  Lots of older instructions don't take this into account.

I seem to remember having this problem till I checked in at the [Compiz forums]("http://www.compiz.net/") - which is your best source of info about Compiz stuff.

---

### Post by llamakc on 2006-08-25
Thanks, Crosbie. I'll give that a go. Makes sense.

---

