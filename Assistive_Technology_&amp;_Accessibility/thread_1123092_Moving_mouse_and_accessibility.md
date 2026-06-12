---
title: "Moving mouse and accessibility"
date: 2009-04-11
forum: Assistive Technology &amp; Accessibility
---

### Post by kilhian on 2009-04-11
Hello all

I'm daily using this [software]("http://nipg.inf.elte.hu/headmouse/headmouse.html")  in order to manage my computer (moving the mouse with my head moves, I became disable due to a  [desease]("http://en.wikipedia.org/wiki/Amyotrophic_lateral_sclerosis")).
I can't no more use ubuntu, because there is no tools available to move mouse pointer.
this [software]("http://nipg.inf.elte.hu/headmouse/headmouse.html") is the best open-source for windows.
sources are [here]("http://sourceforge.net/projects/erutarian")
is it posssible for a team to port it ?
but I'm not a dev :(
Thank you for your time and your atttention

kilhian

---

### Post by cmauri on 2009-04-14
kilhian,

Please try Enable Viacam ([http://viacam.org](http://viacam.org)). It's available for Windows and Linux. Please tell if you need additional features (perhaps already found in the software you are talking about). I'll consider implementing it.

Regards,

César

> **kilhian said:**
> Hello all

I'm daily using this [software]("http://nipg.inf.elte.hu/headmouse/headmouse.html")  in order to manage my computer (moving the mouse with my head moves, I became disable due to a  [desease]("http://en.wikipedia.org/wiki/Amyotrophic_lateral_sclerosis")).
I can't no more use ubuntu, because there is no tools available to move mouse pointer.
this [software]("http://nipg.inf.elte.hu/headmouse/headmouse.html") is the best open-source for windows.
sources are [here]("http://sourceforge.net/projects/erutarian")
is it posssible for a team to port it ?
but I'm not a dev :(
Thank you for your time and your atttention

kilhian

---

### Post by kilhian on 2009-04-17
Thanks, I will try it :)

---

### Post by cmauri on 2009-04-22
Hi kilhian,

I've added a new version (1.0) of Enable Viacam. I've fixed several bugs and also introduced .deb packages. See Changelog for details.

Regards,

César

---

### Post by kilhian on 2009-04-22
Doesn't work on Ibex :(
i've downloded the deb file
launch it
then it asks me to install libavcodec0d dependency wich one is unavailable from apt-get :(/

---

### Post by cmauri on 2009-04-23
Until now the .deb package has been tested on debian etch. Ports to Ubuntu are also planned. Meanwhile you can try compiling the (debianized) sources. 

Regards,

César

---

### Post by kilhian on 2009-04-23
Here is error message while make
> icons/user.xpm:284: attention : deprecated conversion from string constant to &#8216;char*&#8217;
wconfiguration.cpp: In member function &#8216;void WConfiguration::CreateControls()&#8217;:
wconfiguration.cpp:247: erreur: invalid use of incomplete type &#8216;struct wxImageList&#8217;
/usr/include/wx-2.8/wx/generic/listctrl.h:16: erreur: forward declaration of &#8216;struct wxImageList&#8217;
wconfiguration.cpp:250: erreur: invalid use of incomplete type &#8216;struct wxImageList&#8217;
/usr/include/wx-2.8/wx/generic/listctrl.h:16: erreur: forward declaration of &#8216;struct wxImageList&#8217;
wconfiguration.cpp:252: erreur: invalid use of incomplete type &#8216;struct wxImageList&#8217;
/usr/include/wx-2.8/wx/generic/listctrl.h:16: erreur: forward declaration of &#8216;struct wxImageList&#8217;
make[2]: *** [eviacam-wconfiguration.o] Erreur 1
make[2]: quittant le répertoire « /home/hadopix/eviacam-1.0/src »
make[1]: *** [all-recursive] Erreur 1
make[1]: quittant le répertoire « /home/hadopix/eviacam-1.0 »
make: *** [all] Erreur 2


:(

---

### Post by cmauri on 2009-04-27
Last week I've received a mail from a developer who is working on the Ubuntu port. Meanwhile you can try this:

Add the following line:

#include <wx/imaglist.h>

in the wconfiguration.cpp file before the line

#include "wx/wxprec.h"

Then recompile it again.

Let me know if it worked.

Regards,

César

---

### Post by kilhian on 2009-06-06
> /usr/bin/ld: cannot find -lXtst
collect2: ld returned 1 exit status
make[2]: *** [eviacam] Erreur 1
make[2]: quittant le répertoire « /home/hadopix/eviacam-1.0/src »
make[1]: *** [all-recursive] Erreur 1
make[1]: quittant le répertoire « /home/hadopix/eviacam-1.0 »
make: *** [all] Erreur 2

so bad

---

### Post by cmauri on 2009-06-08
kilhian,

Try with the latest eViacam version (currently 1.0.1) and ensure that libXtst is installed (for Debian you should install the libxtst6 and libxtst-dev packages), then check that under /usr/lib there you have:

./libXtst.so.6.1.0
./libXtst.so.6
./libXtst.a
./libXtst.so

Let me know if it worked.

Also you can check [this]("http://www.vivaolinux.com.br/artigo/Acessibilidade-Movimentos-do-mouse-com-a-face-(eViacam)") guide on compiling.

Cesar

---

### Post by kilhian on 2009-06-08
hi,
compilation is now ok
The webcam is not recognized althought it works on cheese, camstream...
creative webcam notebook 
Prod id: 0x401f
thanks

---

### Post by pcgaldo on 2010-06-16
eViacam is working for me in Ubuntu 10.04 LTS, installing this packages:

libhighgui1_1.0.0-6.2ubuntu1_i386.deb
libcv1_1.0.0-6.2ubuntu1_i386.deb
libcvaux1_1.0.0-6.2ubuntu1_i386.deb
eviacam_1.2.1_i386_ubuntu_karmic.deb

This software is not in the Ubuntu repositories. That is why I have proposed their inclusion in the repositories, through Ubuntu Brainstorm:

[[IMG]http://brainstorm.ubuntu.com/idea/25114/image/1/[/IMG]](http://brainstorm.ubuntu.com/idea/25114/)

---

### Post by cmauri on 2010-06-18
This is good news! I hope to see eviacam included in the main distribution. 

Regarding the webcam compatibility, there is good news too. We are working on a new camera layer that will improve compatibility with many cameras.

---

### Post by jettaknight86 on 2010-08-17
Have you tried using MouseTrap? It's in the repos. It might work in the meantime.

---

