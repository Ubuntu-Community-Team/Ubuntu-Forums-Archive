---
title: "Weird Problems after reformating"
date: 2007-10-11
forum: Absolute Beginner Talk
---

### Post by xenosyn on 2007-10-11
Ok so here is the story, I recently reformatted my windows hard drive and had a grub error after words it said Master Boot record error so I used the following tutorial to fix it [http://ubuntuforums.org/showthread.php?t=224351]("http://ubuntuforums.org/showthread.php?t=224351")
after doing that I had the famous black screen which told me in my xserver.conf file that no devices were detected I use to get this before when I was trying to install my flgrx drivers for my ati x1300 radeon graphics card so I thought I could temporally fix it like I use to do by going into the recovery console and changing my default graphics driver back to the safe vesa driver but after that it gave me the same error (no devises found) can anyone help me out?

notes
-I'm using ubuntu fiesty 
-been using linux for about 3 weeks now working with my ati x1300 radeon graphics card
-after reformat of my windows (media center sp2) these error occured
-Ubuntu and windows are on separate hard drives

---

### Post by ryanVickers on 2007-10-11
could you try [super grub]("http://www.mediafire.com/?dv4bdnx3xl8")?

Just download, and burn as an ISO - it can restore/fix grub on the MBR ;)

---

### Post by xenosyn on 2007-10-11
Ok thanks I'll try it out and post the results

---

### Post by xenosyn on 2007-10-11
Well that didn't work it seems that I fixed my grub the problem now is trying to get my xserver running like I said I load ubuntu but after so I get an error saying 
No Devices Detected
Fatal Service Error:
No Screens Found
and its not my graphics card becuase I switched to the vesa driver
which should make it work but the same error occurs

---

### Post by ryanVickers on 2007-10-11
try this:

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by xenosyn on 2007-10-11
ok i did but like i said i already changed my driver to the safe 1 (vesa) after i started x same error occured but vesa is reporting it but at the bottem it says 
XIO: fatal IO error 104 (connection reset by peer) on xserver &#8220;:0.0&#8221; after 0 requests (0 known processed) with 0 events remaining.



know what that is?

---

### Post by ryanVickers on 2007-10-11
I have no idea!  It looks like it's unable to connect, or stay connected, er, running and it thinks your terminating it I think... :|

I
m lost, so let's hope someone else comes along! ;)

bump!

keywords:
X
xorg
XIO: fatal IO error 104 (connection reset by peer) on xserver &#8220;:0.0&#8221; after 0 requests (0 known processed) with 0 events remaining.
X window system falure

---

### Post by xenosyn on 2007-10-12
Ah thanks anyways but I solved it myself I put in a little thinking and 
reconfigured my xserver again and went through it carefully  somewhere after I select my video card it tells me I should specify I forget the exact words but its like a code that specifies hardware I'm guessing looking like this 3:0:0 which was the default and something in my mind told me to change it to 2:0:0 and wala my xserver started after I was done configuring and I used the startx command. I then loaded up envy reinstalled my ati drivers and I am now typing this on my Ubuntu fiesty os with my ati driver back and running ^.^

---

