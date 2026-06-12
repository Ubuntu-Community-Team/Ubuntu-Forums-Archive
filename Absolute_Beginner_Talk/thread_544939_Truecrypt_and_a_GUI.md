---
title: "Truecrypt and a GUI"
date: 2007-09-06
forum: Absolute Beginner Talk
---

### Post by Orbital75 on 2007-09-06
Hey guys.... I love Truecrypt and keep all my finances encrypted with it
on windows. I don't really understand to much about TrueCrypt on the command
 line so I was curious if there was a nice and stable GUI for it.

Thanks

( EDIT )  Just read something about a GUI for TrueCrypt called forcefield.
Where can I get this and is it stable?

---

### Post by wheredidrealitygo on 2007-09-06
There is a GUI for it called Forcefield (available in synaptic for download, as well as truecrypt). You should in theory be able to copy that truecrypt directory from the windows machine, over onto the ubuntu machine, and mount it with forcefield.

Any specific information about command line usage can be brought up in a terminal with the command "man truecrypt".

---

### Post by Orbital75 on 2007-09-06
Hummm....... I serched in the Synaptic Package Manager but nothing
comes up.  This is what I am typing in  **Forcefield**

---

### Post by wheredidrealitygo on 2007-09-06
Which version of Ubuntu are you using, and which repositories are you downloading from?

If you don't have all repositories enabled it might not show up in synaptic.

---

### Post by Orbital75 on 2007-09-06
I'm running 7.04  Feisty and I have all the repositories enable.  
( Main, Universe, Restricted, and Multiverse )

---

### Post by wheredidrealitygo on 2007-09-07
If you already have Automatix installed, you can do it through Automatix, under the utilities heading on the left-panel.

Automatix is a GUI for automated installing of applications.

NOTE: Automatix has recently gotten a lot of negative attention as being bad for some systems, you may want to do some research on it before installing, if you decide to do that.

I have it installed I just realized, which is why it shows up in my synaptic. Automatix is installed on my system and I find it works for me, but there are varying opinions on it and the risks involved. I find them negligible.

If you wish to the install of forcefield manually you can follow a walkthrough I found online here:

[http://ubuntu-unleashed.blogspot.com/2007/09/encrypt-your-files-with-truecrypt.html]("http://ubuntu-unleashed.blogspot.com/2007/09/encrypt-your-files-with-truecrypt.html")

or you could do it through [Automatix]("http://www.getautomatix.com") at your own risk.

---

### Post by Orbital75 on 2007-09-07
Thanks for the links....  I may hold off on Automatix but will more than likely try to
install Forcefield some how.

---

### Post by wheredidrealitygo on 2007-09-07
Good luck with either :)

---

### Post by mdebusk on 2007-09-07
> **Orbital75 said:**
> Thanks for the links....  I may hold off on Automatix but will more than likely try to install Forcefield some how.

I have Forcefield installed, but I rarely use it. The command line method is very simple once you've done it once or twice.

The URL to which "wheredidrealitygo" referred provides simple installation instructions and includes a reference to a download site, but I wouldn't call it a tutorial. Fortunately, Forcefield is simple.

---

### Post by hyper_ch on 2007-09-07
From the German Ubuntu Wiki ([http://wiki.ubuntuusers.de/TrueCrypt](http://wiki.ubuntuusers.de/TrueCrypt)) they link to a forcefield .deb [http://bockcay.de/stuff/programs/forcefield/forcefield_0.91-1_i386.deb](http://bockcay.de/stuff/programs/forcefield/forcefield_0.91-1_i386.deb) which is supposed to work in fiesty and edgy - however I haven't tried it and I don't know if that link is ok.

---

### Post by Orbital75 on 2007-09-07
Well, I opened up a command line and typed this

wget [http://bockcay.de/stuff/programs/forcefield/forcefield_current_all.deb](http://bockcay.de/stuff/programs/forcefield/forcefield_current_all.deb)

It showed a progress bar and said it completed.

I have no idea what to do next.
I don't ever have a clue if it installed or where it is on my machine.


Could someone help.  :confused:

[IMG]http://img158.imageshack.us/img158/4582/00screenshotvf1.jpg[/IMG]

---

### Post by hyper_ch on 2007-09-07
I guess it's in your home directory ;) open a terminal an do this:

```

mv ~/forcefield_current_all.deb ~/Desktop/

```

That should move it to the desktop where you can double-click it.

---

### Post by Orbital75 on 2007-09-07
Thank you for your help.  It was sitting in my Home Directory as you suggested.
I guess I over looked it as I was scrolling through my files ( time for some spring cleaning ).

Anyways, I installed it with the deb package manager and it seems to work fine.
It even installed a icon (Red Star) in my Accessories menu. 

I'm going to have to create a Truecrypt Group and add myself to it so I don't have to enter
in my SU password for every operation though. Could be a security risk. 

Thanks for the tip.....

---

