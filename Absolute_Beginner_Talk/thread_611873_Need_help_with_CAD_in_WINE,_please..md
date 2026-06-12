---
title: "Need help with CAD in WINE, please."
date: 2007-11-13
forum: Absolute Beginner Talk
---

### Post by L Campbell on 2007-11-13
I recently installed the latest version of WINE and am hoping to get my IntelliCAD4 ([http://www.cadopia.com/](http://www.cadopia.com/)) to run on it.

What I am not sure about is HOW to do that.  Hopefully the screenshots I (think) I have attached will show the files available on the IntelliCAD  CD.

Should I drag these into a folder on WINE, or what?

Your help will be appreciated.

---

### Post by overdrank on 2007-11-13
> **eldoonftw said:**
> 

run this to debug wine then post output please.

Do not run that command!!!!!!!!!!!!
Thanks to the mods   whew!!!!!!!!!!

---

### Post by L Campbell on 2007-11-13
> **overdrank said:**
> Do not run that command!!!!!!!!!!!!
Thanks to the mods   whew!!!!!!!!!!

OK, so I just 'thought' I was confused.

Now I'm REALLY confused.

I did not understand what you meant at all but thanks, anyway, for trying.   :-)

---

### Post by overdrank on 2007-11-13
> **L Campbell said:**
> OK, so I just 'thought' I was confused.

Now I'm REALLY confused.

I did not understand what you meant at all but thanks, anyway, for trying.   :-)

Sorry for my post I cannot help you with your issue, I was responding to a prior post that has been removed. The command the user gave you would have removed your valuable data from your system.  
[http://ubuntuforums.org/showthread.php?t=611908](http://ubuntuforums.org/showthread.php?t=611908)

---

### Post by L Campbell on 2007-11-13
> **overdrank said:**
> Sorry for my post I cannot help you with your issue, I was responding to a prior post that has been removed. The command the user gave you would have removed your valuable data from your system.  
[http://ubuntuforums.org/showthread.php?t=611908](http://ubuntuforums.org/showthread.php?t=611908)

OK, no problem, thanks anyway.

---

### Post by atomkarinca on 2007-11-13
just double-click the setup.exe or right-click the setup.exe and select open with "wine windows emulator". this should start the setup.

---

### Post by Christmas on 2007-11-13
You can also use a native CAD application, like QCAD. Just install it:
```
sudo apt-get install qcad
```

---

### Post by L Campbell on 2007-11-13
> **atomkarinca said:**
> just double-click the setup.exe or right-click the setup.exe and select open with "wine windows emulator". this should start the setup.

GREAT.  Thanks.

For whatever reason I had not seen this option,  "wine windows emulator".

It now appears that I have CAD files in WINE and I now have to address a license update with Cadopia, as they have sent me a .dat file which, as yet, I have been unable to drop into the appropriate folder.

Hopefully I'll be percolating soon.

Thanks again.

---

### Post by atomkarinca on 2007-11-13
> **Christmas said:**
> You can also use a native CAD application, like QCAD. Just install it:
```
sudo apt-get install qcad
```

actually CAD software is where people get picky. because of their work or getting used to a certain layout or whatever the reason. i have tried a few CAD programs via wine (ideCAD, Sap2000 and AutoCAD) and i have never had trouble. they just installed like in windoze, without a glitch.

---

### Post by atomkarinca on 2007-11-13
> **L Campbell said:**
> It now appears that I have CAD files in WINE and I now have to address a license update with Cadopia, as they have sent me a .dat file which, as yet, I have been unable to drop into the appropriate folder.

wine folder is generally under your home folder. navigate into your home directory and hit ctrl+h, you will see the .wine folder. in that folder there is your drive_c. good luck.

[wine application database]("http://appdb.winehq.org/") is a great source for installing software through wine. you can find howto's on that page. just use the custom search tool on the left pane.

---

### Post by L Campbell on 2007-11-13
> **Christmas said:**
> You can also use a native CAD application, like QCAD. Just install it:
```
sudo apt-get install qcad
```

Thanks but doesn't one have to purchase this system?

The reason I ask is that I had to pay for my IntelliCAD and I'd rather not pay for another system at this point.

Kind regards.

---

### Post by L Campbell on 2007-11-13
> **atomkarinca said:**
> wine folder is generally under your home folder. navigate into your home directory and hit ctrl+h, you will see the .wine folder. in that folder there is your drive_c. good luck.

[wine application database]("http://appdb.winehq.org/") is a great source for installing software through wine. you can find howto's on that page. just use the custom search tool on the left pane.

THANK YOU.

I am as excited as a dog with 2 tails.

Using this route I was able to replace an out of date ' .dat ' file with a current one and it appears the IntelliCAD is working properly.  I haven't tried out all of it's features yet but what I have tried was perfect.

This CAD program is my LAST link to MS and I can already fee the shackles shaking loose.

THANKS AGAIN.

---

### Post by girijesh on 2007-11-13
you may also use A9CAD a free CAD alternative available on [http://a9tech.com/](http://a9tech.com/)

---

### Post by atomkarinca on 2007-11-14
> **L Campbell said:**
> THANK YOU.

I am as excited as a dog with 2 tails.

Using this route I was able to replace an out of date ' .dat ' file with a current one and it appears the IntelliCAD is working properly. I haven't tried out all of it's features yet but what I have tried was perfect.

This CAD program is my LAST link to MS and I can already fee the shackles shaking loose.

THANKS AGAIN.

glad to hear you get it working.

> **L Campbell said:**
> Thanks but doesn't one have to purchase this system?

The reason I ask is that I had to pay for my IntelliCAD and I'd rather not pay for another system at this point.

Kind regards.

qcad is a free and open-source CAD software. you can install it via synaptic.

---

### Post by igel on 2007-11-14
qcad is not a cad anyway, but intellicad has native linux versions from some vendors.Intellicad is a standart codebase that different vendors brand and compile.

---

### Post by atomkarinca on 2007-11-14
> **igel said:**
> qcad is not a cad anyway, but intellicad has native linux versions from some vendors.Intellicad is a standart codebase that different vendors brand and compile.

i've never actually used qcad but as far as i remember it IS a CAD software. however, as i mentioned before, most of the CAD softwares have native linux clients or work perfectly through wine. according to L Campbell, intellicad does, too. as he's already paid for it and got it working he doesn't need a free one but it's always good to keep in mind that we have many alternatives and it's just a few clicks away.

---

### Post by cavacuz on 2007-11-16
> **atomkarinca said:**
> actually CAD software is where people get picky. because of their work or getting used to a certain layout or whatever the reason. i have tried a few CAD programs via wine (ideCAD, Sap2000 and AutoCAD) and i have never had trouble. they just installed like in windoze, without a glitch.

hi atomkarinca!
you say that you work with autocad via wine, can you help me do it?

thanks anyway.

---

### Post by atomkarinca on 2007-11-17
if you have autocad 2000 then just start the setup.exe and you're done. it just works after the install. unfortunately for the other versions the situation is not so good. you can check out other people's workthroughs [here]("http://appdb.winehq.org/objectManager.php?sClass=application&iId=86").

---

