---
title: "HANNS-G JW199D... how to change res up??? help..."
date: 2006-11-04
forum: Absolute Beginner Talk
---

### Post by nuke199999 on 2006-11-04
alright... THIS is getting rediculous, my cellphone at this point has easier to read text then this monitor...

 just got this monitor, before that it was on anouther comp, not mine...

it says this:

**Display Size&#65306;**
 19" Wide Color Active Matrix TFT
 Quick Start Guide   
**Brightness&#65306;**
 300 cd/m2  (Typical)     Driver  
**Contrast&#65306;**
 700:1 (Typical)     
**Pixel Pitch&#65306;**
 0.283(H) x 0.238(V) mm  Adobe Reader 7.0    
**Resolution(H x V)&#65306;**
 WXGA+ 1440 x 900   
**Response Time Tr/Tf ms&#65306;**
 5 ms (Typical)   
**View Angle LR,UD&#65306;**
 H/V 150°/135°  
**Display Color&#65306;**    
 16.2M Colors   
Color&#65306; 9300K, 6500K, User Mode   
Input Terminal
     
**Input 1&#65306;**
 VGA Analog x1, PC Audio x1, DVI 


now, i did not get any software with it, nothing...

im running this on a completely stock compac sr1135cl (or what ever)

now, im guessing the reason this picture quality is terrible is the highest res i can move the slider to now is 1280X1024.

how in the heck do i change this to 1440x900.

hanns has a driver file on their website which i then downloaded to my desktop, i have no knowledge on how to install teh driver to make this thing function (if thats the problem, lack of driver) 


so, what do i do...

please help me out guys...

also, can someone explain how to get my font on every pageo n this computer to a normal size? on the help page it is like size 32... on here most text cept for buttons is too big and all i can see are tops of letters, ontop of this, colored buttons artn showing up, the colori n them like on myspace buttons which should be blue, do not show up and i only see text...

fixes???

thanks alot...


-Grady


what else should i change to make this monitor perform like it should????

---

### Post by nuke199999 on 2006-11-04
also, pages that should be black, are not!!! WTH?? if i install the driver will that fix all these problems that are making my experiance with this monitor worse then the 7the level of hell?

---

### Post by nuke199999 on 2006-11-04
alright, well, i tried doing a search for "best possible driver" i chose the downloaded driver file "jw199d" that i downloaded off hanns-g's website.

it said the "plug and play" driver was the best driver for this monitor, which is bull because obviously this isn't...

is there a way i can manually choose this file as a driver? what do i need to do here...

---

### Post by towsonu2003 on 2006-11-04
Could you please post the output of ```
lspci
``` ```
lspci -vv
``` and ```
cat /etc/X11/xorg.conf
``` Even attach the /var/log/Xorg.0.log **as a file** as well :) (pls don't copy paste that one, it's long)

To input the commands, hit alt+**f2** and type gnome-terminal (if you're using Ubuntu) or konsole (if you're using Kubuntu). then type in the command, press enter, and copy paste the output here... 

Also, please link the web page of this product. There is a chance someone has the same product, or know the refresh rates etc... 

as per your font / size problems, can you attach a screenshot of the problem? If you're using Ubuntu, the screenshot tool is under Applications > Accessories > Take Screenshot. I'm not sure about Kubuntu...

Oh, and, also let us know the link to the driver you downloaded...

---

### Post by nuke199999 on 2006-11-04
unfortunately im a complete moron and dont even know what ubuntu or kubuntu is, i got my driver installed, which did nothing visibly, i'm still on the search to get my computer screens res to 1440x900.... what the hell....

i'll try to attempt to do what your telling me to.... like i said dunno what that stuff is, all i know is im running a compaq with a 19'' monitor thats giving me hell right now....](*,)

---

### Post by towsonu2003 on 2006-11-04
> **nuke199999 said:**
> unfortunately i dont know what ubuntu or kubuntu is

Ubuntu is this one: [http://www.ubuntu.com/](http://www.ubuntu.com/)
Kubuntu is this one: [http://www.kubuntu.org/](http://www.kubuntu.org/)

Depends where you downloaded your linux distro...

No worries :) just type gnome-terminal first. If it doesn't bring a window you can type into, try konsole. 
> 
i'll try to attempt to do what your telling me to.... 
that's nice -I may go to sleep soon, I'll check back later if I do so
> like i said dunno what that stuff is, all i know is im running a compaq with a 19'' monitor thats giving me hell right now....](*,)

lol :) Most of us experienced that stage. I still experience that "oh my god what is going on" feeling from time to time :KS  You'll get used to it :mrgreen:

**Correction: my mistake, it's alt+f2, not alt+f3**

---

### Post by nuke199999 on 2006-11-04
[IMG]http://i42.photobucket.com/albums/e320/nuclearhell/untitled.jpg[/IMG]


theres my text problem.... also... heres hanns-g's website....

[http://www.hannsg.com/us/](http://www.hannsg.com/us/)


monitor

[http://usservice.hannsg.net/](http://usservice.hannsg.net/)

---

### Post by towsonu2003 on 2006-11-04
uhm, ok, looks like you're using Windows, not Ubuntu :) And I have no idea how to solve Windows display problems... 

As for the font problem, I don't know about it either... You could try to use another browser available at [http://www.mozilla.com/](http://www.mozilla.com/) (its name is Firefox).

---

### Post by anjin on 2008-03-17
ADMIN: can we get this post removed?  I have a Hanns-G monitor and am running Ubuntu, so finding this thread was a total bummer.  But it's in the top 5 search results.  Which makes it annoying.

---

### Post by ponderworks on 2008-04-18
Agree with Anjin!!  We need to remove this post.

In the meantime, I just got a Hanns-G 19" running Ubuntu Gutsy.  It worked well!  I did discover that the adjustments on the monitor itself made a big difference.

et

---

### Post by tmetzcc325 on 2008-05-20
ponderworks,

I am also using this monitor on a Dell Dimension 2400 running Ubuntu Hardy.  Have you noticed anything weird involving any sort of window looking like it is ghosting off to the right of the screen?  I really can't describe it, but it makes it look like the windows slid in from the right side of the screen, sort of like how lines are drawn behind things that are supposed to be moving fast in cartoons.  I know that is a terrible description, but I really have no other words for it.

I have been using the monitor since Ubuntu 7.04, and each version of the distro has the same problem.  Unfortunately, I haven't been able to test it with other computers/OSes, so I have no reference as to what it might look like otherwise, but I was just curious to see if you'd experiences something similar.

Tom

---

### Post by sugardeath on 2008-06-27
Are you using VGA or DVI?  I've been using the same monitor since 7.04 and have had no problems.  Upgraded to 7.10 and 8.04 and everything has been perfect.  Windows is fine, too.  Well, nearly perfect, for some reason I can't output any other 16:10 resolutions like 1280x800, but that's not that big of a deal.  Overall, this monitor has been very crisp and has required absolutely no setup at all.  In fact, most of the monitor set up options are disabled because I am using a DVI connection and it auto detects everything.  If you can, try that out.  I have hooked a second computer up to the VGA port and, after running the monitor's auto adjust, got it to display at 1440x900 just as crisp as the computer with DVI.

---

### Post by tmetzcc325 on 2008-07-18
Unfortunately I am stuck using the VGA for now (no DVI, and don't feel like buying a video card just yet when I am going to be building a new box in the near future [hopefully]).

I ended up testing it with a laptop (using VGA) running XP, and it looked okay.  It is weird, though, because it seems to fluctuate in how intense the ghosting effect is...lately it hasn't been too terrible (either that, or I am beginning my progression into blindness at a very young age...)

Thanks for the reply, though.

---

