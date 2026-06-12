---
title: "Big problem with GDM  - Gnome Desktop Manager"
date: 2005-10-20
forum: Absolute Beginner Talk
---

### Post by loninappleton on 2005-10-20
There has not been real good response on this problem for me which
has gone on for several weeks now.

None of the Ubuntu installers from 4.10 or Agnula Demudi will
get past some problems in Gnone Desktop Manager or whatever
is stopping the screen display.

My setup goes ok until a reboot at which time I here the screen
click like it's changing resolutions and then nothing-- big blank
screen.

I have used some of the live cds and they come up the way they
should.  What is difference on live cd installs from the hard disk versions?


On the Demudi which is for musicians from Agnula, everything on the 
live cd works ok, but the hard disk install fails repeatedly.

The video card is old-- A Diamond Stealth 2000 Pro.  Why can the 
live cd find the proper lower resolution but the hard disk install cannot?


I have been the route of trying to copy /etc/X11 from live cd to 
hard drive but that is too complicated.  After all, the hard disk install
pulls up a blank screen or dumps me out at the command line after
the GDM fails.

This is a stand alone setup.  There is no telecomm connection.

---

### Post by Kyral on 2005-10-20
You are using 4.10 (Warty)?

Try snagging a 5.10 (Breezy) install CD and using that...

---

### Post by loninappleton on 2005-10-20
I  went back to my sent-for copy of Unbuntu after
attempting to use current product.  I have another copy from Ubuntu coming in the mail.

However I have no faith that this will do any good.


I'd like to hear from those who have had a similar
problem with GDM described above and what they _did_
about it, if anything.


What I've been seeing is this sort of Bob and Joe's Linux
given an exotic name:  Ubuntu, Mepis etc etc with no
form of uniformity or ability to install.  


So what is more helpful is to tell me how these glitches
have been fixed.

---

### Post by Kyral on 2005-10-20
Honestly dude, this is the first time I've heard about a problem like one you describe...

---

### Post by loninappleton on 2005-10-21
I downloaded a Breezy 5.10 but haven't fiddled with it.

My big concern is the audio distro Demudi.


My repeated question on this is: if it works in Live CD,
why does it totally screw up on a disk install?


Something is different between the one and the other
and I'm thinking it's that 'click' where something is trying
to change resolutions.  The one that displays is 640x400
if I'm not mistaken.   The automatic Ubuntu installer is not very flexible on this: it shows 3 default items which
can only sensibly be 'clicked through' and ok'ed.

---

### Post by Kyral on 2005-10-21
[quote=loninappleton]The automatic Ubuntu installer is not very flexible on this: it shows 3 default items which
can only sensibly be 'clicked through' and ok'ed.[/quote]

'clicked through and ok'd'?

---

### Post by mushr00m on 2005-10-21
[QUOTE=loninappleton]I downloaded a Breezy 5.10 but haven't fiddled with it.

My big concern is the audio distro Demudi.


My repeated question on this is: if it works in Live CD,
why does it totally screw up on a disk install?


Something is different between the one and the other
and I'm thinking it's that 'click' where something is trying
to change resolutions.  The one that displays is 640x400
if I'm not mistaken.   The automatic Ubuntu installer is not very flexible on this: it shows 3 default items which
can only sensibly be 'clicked through' and ok'ed.[/QUOTE]

I did have that problem with my brothers computer... it was a onboard i845 intel graphics "chipset"](*,) . Using a warty liveCD I could add a line "xsession=i845" (could be wrong on that) and I got a nice 800x600 resolution... but the install does what you discribe everytime. Starts the kernal then I imagine when it comes to starting X I get a hung screen, sometimes cursor sometimes not.  

I haven't had a single install problem on MY computer and ubuntu is my OS of choice.  

I just fresh installed breezy today to give Automatrix a try... it looked fun. It worked just fine, if you had the desire I'm sure the script is freely editable.

---

### Post by loninappleton on 2005-10-21
The setup has a screen where some very high resolutions
appear.  Way down at the bottom, 3 have asterisks at the
lowestones.  I had a dififficult time selecting one so I figured those are the defaults (because the three are 
preselected.)  Even when I tried to slect one, the same thing happens.


I'm trying a different install, this time of Kubuntu.


Will see if the same thing happens....

Yep, attempting to select just 640x400 just clicked through to the next setup process.
,

---

### Post by loninappleton on 2005-10-21
hey MushrOOm,

  Your post came through on email notification but not
here.


  Where do you force the command for i845 chipset?
Just in terminal mode?


  How can I find the location of the info on this old
Diamond Stealth card?


  How can the command work if I just get a blank screen?
I'm not seeing any opportunity to modify what the installer is doing.


  There was an error message that came up on a couple boots but now I'm not getting even that.


  I've inquired at Debain HQ about this as well.  So far
no replies.


  Just now a reboot does the same thing as the install:
'click'/switch to blank screen.  As I was shutting down, the setup screen reappears for a moment then off.

---

