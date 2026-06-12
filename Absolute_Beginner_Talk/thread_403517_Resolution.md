---
title: "Resolution"
date: 2007-04-07
forum: Absolute Beginner Talk
---

### Post by Skip2MyPou on 2007-04-07
Hey, I just installed ubuntu and I'm wondering how to change the resolution. I went to System>Preferences>Screen Resolution and it just goes up to 800x600.

---

### Post by mikeyphi on 2007-04-07
> **Skip2MyPou said:**
> Hey, I just installed ubuntu and I'm wondering how to change the resolution. I went to System>Preferences>Screen Resolution and it just goes up to 800x600.

Probably need to install Graphic card driver....good advice here [http://ubuntuguide.org/wiki/Ubuntu_Edgy#Graphics_Card](http://ubuntuguide.org/wiki/Ubuntu_Edgy#Graphics_Card)

---

### Post by heimo on 2007-04-07
This is common problem. Check these for hints:
[https://help.ubuntu.com/community/FixVideoResolutionHowto](https://help.ubuntu.com/community/FixVideoResolutionHowto)
[http://www.ubuntuforums.org/showthread.php?t=83973](http://www.ubuntuforums.org/showthread.php?t=83973)

---

### Post by Skip2MyPou on 2007-04-07
I'm REALLY confused.....can someone give me a simple step by step walkthrough? I have an ATI Radeon 9600XT video card by the way.

---

### Post by mikeyphi on 2007-04-07
> **Skip2MyPou said:**
> I'm REALLY confused.....can someone give me a simple step by step walkthrough? I have an ATI Radeon 9600XT video card by the way.

Try here:- [http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide)

---

### Post by heimo on 2007-04-07
Could you give us the make and model of your monitor?

Open a terminal (Applications->Accessories->Terminal) and run these commands and give us the output (it's case sensitive):

```
grep Driver /etc/X11/xorg.conf 
grep VertRefresh /etc/X11/xorg.conf
grep HorizSync /etc/X11/xorg.conf
grep Modes /etc/X11/xorg.conf
```

---

### Post by Skip2MyPou on 2007-04-07
My monitor is a Viewsonic PerfectFlat A70f

---

### Post by heimo on 2007-04-07
Output for HorizSync line (in a post above) should be close to 30-72 and for VertRefresh 50-150 (or at least 50-90). Output for Modes should include 1280x1024 and 1024x768 if you want to use those modes. Driver should probably be ati (or fglrx). Is it?

Link to your monitor specs:
[http://www.viewsonic.com/support/desktopdisplays/crtmonitors/aseries/a70f/#specs](http://www.viewsonic.com/support/desktopdisplays/crtmonitors/aseries/a70f/#specs)

---

### Post by Antman on 2007-04-07
> **Skip2MyPou said:**
> I'm REALLY confused.....can someone give me a simple step by step walkthrough? I have an ATI Radeon 9600XT video card by the way.

Just use the Envy script: Envy Script(ATI/Nvidia): [http://www.albertomilone.com/nvidia_scripts1.html]("http://www.albertomilone.com/nvidia_scripts1.html")

:guitar:

---

### Post by Skip2MyPou on 2007-04-07
Yea...I am like absolute noob of the noobs so I have no idea what to do...

---

### Post by Antman on 2007-04-07
> **Skip2MyPou said:**
> Yea...I am like absolute noob of the noobs so I have no idea what to do...

1. If you're using Ubuntu 6.10 (edgy) just download this package: [Click]("http://albertomilone.com/ubuntu/nvidia/scripts/envy_0.9.1-0ubuntu4_all.deb")

2. Then go to> System> Administration> Synaptic Package Manager. You will be prompted for your admin password. 

3. After you enter it and Synaptic opens, go to Menu "Settings> Repositories" and select "Universe and Multiverse options". THen click "close"
[IMG]http://www.entermfg.com/pics/synaptic.png[/IMG]

4.  Then hit the "Reload" button in Synaptic. Once it refreshes the package list, close Synaptic.

5. Locate the "envy_0.9.1-0ubuntu4_all.deb" file you downloaded --- right-click it and select "GDebi Package Installer" --- select the Install Package button to install Envy.

Once it's done look under> Applications >Systems Tools> and launch Envy.

From there just pick your Graphics Card and install.... :guitar: 

Ant

---

