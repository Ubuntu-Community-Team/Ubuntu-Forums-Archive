---
title: "help ubuntu running slow"
date: 2007-11-19
forum: Absolute Beginner Talk
---

### Post by rude_lee on 2007-11-19
after wednesday update my laptop has been going super slow had compiz on things where going like slide shows on pause i turned compiz off and i gained some function back but its still real slow tried installing and reinstalling compiz but its still that way
im running gutsy on a gateway mx6440 with the new 200m ati driver
help

---

### Post by duruttye on 2007-11-19
Did you check in system monitor, maybe you'll see what is slowing down your system, there are many reasons that this can happen.
how is your CPU usage?
In terminal try "top", or ps -ef, see if there is anything that doesn't belong there.
What if you remove completely compiz? Did you try that?
Can't think of anything else.

---

### Post by el escocés on 2007-11-19
as said before in terminal run top

look at which process(es) are constantly using memory or cpu, if you see a process and you are not sure what is running it type pstree in the tmerinal and search for the process, or try grep'in it:

pstree | grep gzip (for example)

let us know what you find out...

---

### Post by shuttleworthwannabe on 2007-11-19
ok, I have also had this experience when I updated the first install with the downloaded apps (compiz was one of them). I could not resolve the issue even after I completely removed compiz; I got so frustratyed I reinstalled Gusty, and now I am not updating even if I get a naging popup showing updates available.

I hope there is a good solution fo rthis,

S

---

### Post by rude_lee on 2007-11-19
it dont show any processes eatin alot of anything so im not sure
i would rather not have to reinstall ubuntu
do u know how to unistall x server that i use for fglx to run compiz how to uninstall this

---

### Post by duruttye on 2007-11-20
[HTML]sudo dpkg-reconfigure xserver-xorg[/HTML]
This will reconfigure your xserver, the reinstallation of compiz you'll have to do separately, from synaptic.

---

### Post by shuttleworthwannabe on 2007-11-20
Update: to speed up my Gutsy, I now did this:

1. Set visual effects to None
2. Removed xserver-xgl using $ sudo apt-get remove xserver-xgl
3. Then did the recommended update/upgrade
4. Note: I did not have to remove compiz from synaptic

So you may not afterall have to do a reinstall. Hope that helps,

S

---

### Post by rude_lee on 2007-11-20
i think i kinda fixed it but the wrong way i took effects off
unistalled ati restricted drivers restart install restricted drivers restart compiz on and it works and runns with less lag then when i installed the newer ati software
thanks alls good people

---

### Post by NIT006.5 on 2007-11-20
Just another thought; I had a similar issue when I tried some of the water effects in compiz-fusion. It didn't actually use up resources or anything like that BUT the GUI became slow i.e. moving a window, resizing a window etc. - all the things handled by compiz-fusion, were painfully slow. After disabling the water effect, it works perfectly though. All other effects run smoothly. Probably a totally different issue but thought I would mention it just in case it helps.

---

