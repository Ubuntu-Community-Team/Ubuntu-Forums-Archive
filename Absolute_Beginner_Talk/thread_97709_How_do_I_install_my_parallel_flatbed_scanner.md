---
title: "How do I install my parallel flatbed scanner?"
date: 2005-12-01
forum: Absolute Beginner Talk
---

### Post by jockjunior on 2005-12-01
Hello all newbie here and a Grandad so talk slowly :smile: 

how do I install my scanner? Its a mustek 600 ep clone badged Targa. I found the mustek_pp.conf file in /etc/sane.d  but I dont know what to do next. I am a complete Linux virgin.  I have managed to get my camera connected ( it shows up as removeable drive) so I can live with that. So its just my scanner and my Lexmark z601 printer to solve.
Thanks in advance for any help it is much appreciated


Phil  (jockjunior)

---

### Post by teaker1s on 2005-12-01
you need to edit it so it points to firmware -look at the sane webpages for more help
[here]("http://www.sane-project.org/") if when you follow the instructions it won't work create a launcher  and use 'sudo xsane' or 'gksudo xsane' if it's still not detected you will need to edit the .conf file to point it to correct port.


use add applications and advanced 
or if you prefer 'sudo synaptic'
you will then be able to search and install either a lexmark driver or cups printing

good luck and remember we have an excellent comunity and wilki which will try to help

---

### Post by jockjunior on 2005-12-01
Thanks will get back to you
have been thrown off computer while Grandaughter plays frozen bubbles:???:

---

### Post by jockjunior on 2005-12-01
Sorry this is not sinking in. can anyone do me a step by step? with this scanner

sorry for being dumb:( 

jock



bump

---

### Post by jockjunior on 2005-12-02
;bump

---

### Post by deNoobius on 2005-12-02
You should just be able use Synaptic to install Sane and run it from the GUI.  It should just detect the scanner.  The scanner needs to be connected and powered up.

---

### Post by jockjunior on 2005-12-02
[http://www.ubuntuforums.org/newreply.php?do=newreply&noquote=1&p=538439](http://www.ubuntuforums.org/newreply.php?do=newreply&noquote=1&p=538439)
thanks will try again

jock

---

### Post by cbudden on 2005-12-02
My Mustek 1200 did not need any installation as it was automatically detected by Xsane.

---

### Post by jockjunior on 2005-12-02
Hello again,
 thanks for all the replies,

Right I have amended /etc/sane.d/dll.conf  to allow mustek_pp and amended etc/sane.d/mustek_pp.conf to read
mustek scanner 600ep parport1 ccd300  etc
 BUT
 the only way I can access the scanner is to open a terminal and input
    sudo xsane 
 then the scanner if found. If I try to open xsane from the menu it doesnt find the scanner and says no device found.

How do I alter this so I can use it from within Gimp etc and without having to log in at a terminal as root ?

thanks again for all your help

Jock:???:

---

### Post by jockjunior on 2005-12-02
Hello again,
 thanks for all the replies,

Right I have amended /etc/sane.d/dll.conf  to allow mustek_pp and amended etc/sane.d/mustek_pp.conf to read
mustek scanner 600ep parport1 ccd300  etc
 BUT
 the only way I can access the scanner is to open a terminal and input
    sudo xsane 
 then the scanner is found. If I try to open xsane from the menu it doesnt find the scanner and says no device found.

How do I alter this so I can use it from within Gimp etc and without having to log in at a terminal as root ?

thanks again for all your help

Jock:???:

---

### Post by teaker1s on 2005-12-02
create a launcher and use  gksudo xsane the reason its only working from console is a permission issue

---

### Post by jockjunior on 2005-12-02
Hi,
made a launcher . can start xsane and scan but it wont let me access the image in Gimp because it says I dont have the right permissions. How can I alter the permissions ?

thanks

Jock

---

### Post by kleeman on 2005-12-02
Go  to System--> Administration --> Users and Groups
Find your user name and edit properties so that you have access to scanners.

---

### Post by teaker1s on 2005-12-02
not wanting to look ignorant that question I don't know the answer but maybe this will [help]("http://www.xs4all.nl/~ljm/SANE-faq.html#4")

---

### Post by teaker1s on 2005-12-02
I did that for mine no joy

---

### Post by jockjunior on 2005-12-02
Kleeman 
I checked in  groups and users and it already says I have scanner access, but it doesnt let me use it.:( 

jock
teaker1s
I looked at your link to the sane faq it says on there for parallel scanner you need to be root or the application needs to be set uidroot to control the ports. 

thanks all
Jock

---

### Post by teaker1s on 2005-12-02
I'm glad your making progress with it, sorry I don't know more hopefully someone will be able to assist further gksudo gives you root access,as for uidroot I don't know the answer, anyway welcome to the forums:KS

---

### Post by jockjunior on 2005-12-02
teaker1s,
 thanks for all your help. I think I've got it now.

set up launcher, then in XSANE alter permissions to allow rw for everyone in order to save images that I can access

that worked.  

just the printer driver to sort now

thanks again
goodnight:D 
jock

---

### Post by arphe_el on 2005-12-05
i already installed xsane using the synaptic but my hp2400 scanner don't recognize by the xsane.

any advice? thanks and GODspeed!

---

