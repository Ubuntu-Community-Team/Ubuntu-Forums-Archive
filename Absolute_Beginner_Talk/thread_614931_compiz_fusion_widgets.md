---
title: "compiz fusion widgets"
date: 2007-11-16
forum: Absolute Beginner Talk
---

### Post by reesy on 2007-11-16
I've enabled widgets but have no idea how to actually get widgets to work in compiz fusion. If any one could help me i would be grateful.

---

### Post by Inxsible on 2007-11-16
you would probably have to download and install widgets. Screenlets is one of them which can use the widget plugin in Compiz Fusion.
gDesklets too i think.

---

### Post by reesy on 2007-11-16
How do i install the screenlet?

---

### Post by FuturePilot on 2007-11-16
Go System>Administration>Software Sources. Click the Third Party Software tab and click add. Then add this line
```
deb http://download.tuxfamily.org/screenlets gutsy screenlets
```
Then click close and Reload the sources when prompted. If you get an error about a missing Key that's OK. The next step will fix that.
Open a terminal and put this in
```
wget http://download.tuxfamily.org/screenlets/hendrikkaju.gpg -O- | sudo apt-key add - && sudo apt-get update
```
Now
```
sudo apt-get install screenlets
```

:)
The Screenlets Manager should show up under System>Preferences

---

### Post by Niniel on 2007-11-16
Neat, I've been asking myself the same question. Thank you. 
Although at this point I'm not sure I even want widgets on my desktop. But who knows, maybe I'll find one that I have to have.

---

### Post by Inxsible on 2007-11-16
I find conky to be a much better option that the resource intensive screenlets (which over time consume more and more memory - at least for me)

---

### Post by FuturePilot on 2007-11-16
> **Inxsible said:**
> I find conky to be a much better option that the resource intensive screenlets (which over time consume more and more memory - at least for me)

Ah yes. I have also fallen in love with Conky. It can display just about everything you would ever want to know about your system. I have also noticed an increase in memory usage with Screenlets.

---

### Post by santiagoward2000 on 2007-11-23
The repositories have changed. Now, it's:
```
deb http://download.tuxfamily.org/screenlets gutsy screenlets
```

and the key:
```
wget http://download.tuxfamily.org/screenlets/hendrikkaju.gpg -O- | sudo apt-key add - && sudo apt-get update
```

FuturePilot, could you edit your first post for others to see it? Thanks!

Still, great how-to! :guitar:

---

### Post by FuturePilot on 2007-11-23
> **santiagoward2000 said:**
> The repositories have changed. Now, it's:
```
deb http://download.tuxfamily.org/screenlets gutsy screenlets
```

and the key:
```
wget http://download.tuxfamily.org/screenlets/hendrikkaju.gpg -O- | sudo apt-key add - && sudo apt-get update
```

FuturePilot, could you edit your first post for others to see it? Thanks!

Still, great how-to! :guitar:

Thanks for the info, I wasn't aware of this ;)
Fixed

---

### Post by santiagoward2000 on 2007-11-23
> **FuturePilot said:**
> Thanks for the info, I wasn't aware of this ;)
Fixed

You're welcome! I'm glad I've helped!

---

### Post by akparker on 2007-11-23
Thank you, FuturePilot.

Your how-to worked flawlessly.

Have you experienced a problem with the calendar screenlet having a large black frame around it?  I can't seem to resize/change it.

Thanks ...

---

### Post by slughappy1 on 2007-11-23
You can go to [http://gnome-look.org/index.php?xcontentmode=165](http://gnome-look.org/index.php?xcontentmode=165) to get screenlets. The easiest way to install screenlets, with the way explained earlier, is to unzip the files and put the folders in the /home/username/.screenlets directory

---

### Post by akparker on 2007-11-23
slughappy ...

Thanks for the link.
I was having trouble finding a good site of Ubuntu screenlets.

I cannot find the .screenlets directory, which is odd considering I've just installed other screenlets via the process outlined on this thread.

Any thoughts would be appreciated.

BTW, the "search" feature on my system does not ... for some reason ... return any results, even when I know for a fact that a given file and/or directory exists ... so I can't search for .screenlets until I work out this issue.

Thanks in advance for any help.  I'm a newbie.

AKP

---

### Post by santiagoward2000 on 2007-11-25
> **akparker said:**
> slughappy ...

Thanks for the link.
I was having trouble finding a good site of Ubuntu screenlets.

I cannot find the .screenlets directory, which is odd considering I've just installed other screenlets via the process outlined on this thread.

Any thoughts would be appreciated.

BTW, the "search" feature on my system does not ... for some reason ... return any results, even when I know for a fact that a given file and/or directory exists ... so I can't search for .screenlets until I work out this issue.

Thanks in advance for any help.  I'm a newbie.

AKP

Hi akparker, sorry for the delay!
The **.screenlets** folder may not be there yet. Just create it yourself and extract the files there. That should do it.
Cheers!

---

### Post by collegedude10 on 2007-11-28
how do i make it so that the screenlets load up on start up? everytime i start my computer i have to open them back up one by on.

---

### Post by santiagoward2000 on 2007-11-28
> **collegedude10 said:**
> how do i make it so that the screenlets load up on start up? everytime i start my computer i have to open them back up one by on.

Hi!
Just open screenlets-manager, select the screenlet you want and then check the **Automatically start on login** box.

---

### Post by moriss on 2008-04-24
The second line doesn't work for me. I get this error message:

"
--08:01:33--  [http://download.tuxfamily.org/screenlets/hendrikkaju.gpg](http://download.tuxfamily.org/screenlets/hendrikkaju.gpg)
           => `-'
Resolving download.tuxfamily.org... 88.191.250.18
Connecting to download.tuxfamily.org|88.191.250.18|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
08:01:33 ERROR 404: Not Found.

gpg: no valid OpenPGP data found.
"


moriss

---

