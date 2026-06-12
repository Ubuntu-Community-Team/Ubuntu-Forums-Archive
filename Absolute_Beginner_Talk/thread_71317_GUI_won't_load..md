---
title: "GUI won't load."
date: 2005-10-03
forum: Absolute Beginner Talk
---

### Post by Knighthammer on 2005-10-03
Hello - I'm very new to both Linux and Ubuntu. A friend of mine said to try out Ubuntu since I wanted to experiment with Linux some - if it goes well, I might even make it my main OS.

Here is the problem I'm having - I just installed the Ubuntu 6.10 iso and the intall went fine (even dual boot with WinXP) but I can't get the GUI to come up, best I get is a text prompt for login info. 
Quick sys specs;
3.6GHz P4
915i chipset
ATI X800XL PCI-e video card
1GB ram
2 hard drives, one for each OS

I'm not sure whats wrong - does Ubuntu or Linux for that mater work well with PCI-e video cards?

Help if you know what I should do next - thanks!

---

### Post by aysiu on 2005-10-03
What happens when you log in and then type ```
startx
``` ?

---

### Post by Knighthammer on 2005-10-03
Says 

```

Fatal server error:
no screens found

XIO: fatal IO error 104 on X server ":0.0" after 0 requests (0 known processed) with 0 events remaining.

```

---

### Post by aysiu on 2005-10-03
Usually, when I get errors, I do a Google search for the error, but [it doesn't look as if your error is very common](http://www.google.com/search?num=100&hl=en&lr=lang_en&safe=off&q=%22XIO%3A+fatal+IO+error+104+on+X+server%22&btnG=Search). I'm not sure what to do. Anyone else?

---

### Post by Qrk on 2005-10-03
type 

sudo dpkg-reconfigure xserver-xorg

into the command prompt. It will ask you a series of questions regarding your monitor (and some other hardware) 
Depending on your monitor (which I'll guess is flat screen, seeing as your system is nicer), you might have "nv" highlighted. Try switching that to something else, like vesa or vga. Go through the rest of the program.

---

### Post by Knighthammer on 2005-10-03
I will try that when I get in front of the system again (its a home, and I'm working) Yes the screen is a flat panel - good guess.

Has anyone else gotten a PCI-e card work in Linux? 

I have another system that I hope to build soon that has onboard graphics so assuming that should work.

---

### Post by Sirius on 2005-10-05
I get the same problem and have 

Problem (X-Server is not starting up with fresh install, xorg.0.log error No Screens Found) I have ubuntu 32 bit disc (and tried the 64 bit disc same prob) with a MSI k8n Neo4 AMD 3200 64 bit x800 Ati card, have a genaric 19 inch CRT

---

### Post by Ampersand on 2005-10-05
Could you check the xorg.0.log for lines starting with (EE)? They should give a few more details of the problem.

---

### Post by Sirius on 2005-10-05
(II) Primary Device is: PCI 05:00:0
(II) ATI:  Candidate "Device" section "ATI Technologies, Inc. Radeon X800 Pro (R423 UI)".
(II) ATI:  Unshared 8514/A not probed.
(II) ATI:  Unshared Mach64 at PIO base 0x02EC not probed.
(WW) ATI:  PCI Mach64 in slot 5:0:0 could not be detected!
(WW) ATI:  PCI Mach64 in slot 5:0:1 will not be enabled
 because it conflicts with another non-video PCI device.
(EE) No devices detected.

Fatal server error:
no screens found

---

### Post by Sirius on 2005-10-05
Stumped ?

---

### Post by Ampersand on 2005-10-05
I've not used PCI-e personally, I was hoping that it would give someone else enough to suggest something.

Only thing I can suggest is to do a dpkg-reconfigure xserver-xorg again, and make sure everything about the graphics card is correct.

---

### Post by rzapeople on 2005-10-05
I get the same problem too. I'm trying to install ubuntu on my Dell Inspiron 1200 notebook and the gui doesnt load. All I get is the command prompt after it has switched itself off with a warning that BIOS not found. I did do the dpkg-reconfigure xserver-xorg and still nothing... Its getting annoying now!!!!

---

### Post by tseliot on 2005-10-05
My nvidia Geforce 6200 TC PCI-E worked properly only with the proprietary drivers.

About your problem: you should either try Ubuntu Hoary 5.04 (the stable version) or wait until Breezy (the stable version) is out (october 13).

---

### Post by rzapeople on 2005-10-05
My problems may be even worse! Cant even get the live cd to load teh gui! I'm stumped now. Didnt know linux could be so difficult to work with...? :confused:

---

### Post by varcsscotty on 2005-10-07
I'm getting the same problem on an older system...no pcie.  the dpkg-reconfigure xserver-xorg doesn't work and I've tried reinstalling several times and reconfiguring. It just down't work:(

---

