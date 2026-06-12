---
title: "nvidia drivers impossible to install in asus X53SJ"
date: 2011-09-27
forum: Asus Ubuntu Support (CLOSED)
---

### Post by Mikkå on 2011-09-27
Just curiosity: I have rather new asus X53SJ laptop, whit Ubuntu 10.04. 2.6.32-33-generic . PC´s specs: 15.6" HD (1366x768), Intel® Core™ i3 2310M 2.1 GHz, 4 GB (1x4) DDR3-1333, maks. 8 GB, 500 GB SATA 5400 rpm, NVIDIA GT 520M 1 GB. 
I have been trying for four days to install nvidia drivers to get better resolution (current: 1024x768) and not succeed. And now I have started to believe that it´s impossible to install those drivers in such way they will work in to this computer, because I have tried install them in every possible way.

I think this computer comes with two graphic cards nvidia and intel HD. And the ubuntu cant figure which card it will use, the fu***ng nuoveau is messing things even more and starting the x server everytime in low resolution. Every time i boot, pop up window messages "ERROR Devices not found"  and I messages to my girlfriend in the living room "**** this ****!"

Im just curious, do i have any soul mates who had been wrestling whit the same issue??

---

### Post by realzippy on 2011-09-27
> **Mikkå said:**
> 
Im just curious, do i have any soul mates who had been wrestling whit the same issue??
Guess a few thousands if you have an Optimus laptop.

Run

```
lspci | grep VGA
```

If you see your 2 graphic devices,you have Optimus.
The low resolution is because the kernel you are using is too old
for the I3 graphics.This can be fixed by a newer kernel.
Also your nvidia card can be used,with a special software.
..problem might be that it is impossible to to stop the nvidia card when not used on many optimus laptops,so it sucks battery power all the time.

---

### Post by Mikkå on 2011-09-27
I knew that there is two graphic cards; nivida and the integrated intel. But i didint have a clue that the problem is that.
 
Oh man, I have just paid 600€ for useles computer, though I want to use Ubuntu whit 3D desktop, etc.. nice.

---

### Post by realzippy on 2011-09-27
You can use 3D desktop with your machine !
You just had to install a few things....
...can help you,no problem.

---

### Post by Mikkå on 2011-09-27
[LEFT]I will appreciate if u will! What I need to install?
[/LEFT]

---

### Post by realzippy on 2011-09-28
Run those commands:

```
sudo apt-get purge nvidia-current
sudo add-apt-repository ppa:glasen/intel-driver 
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install linux-image-generic-lts-backport-natty linux-headers-generic-lts-backport-natty 
```

...if it had worked,you should get your 1366x768 after reboot.
Then we can go on with your nvidia-card.

---

### Post by Mikkå on 2011-09-28
Yep, it worked, i got the 1366x768 reso after reboot, and now i have 3D desktop.  :D thx!!

What about that nvidia?

---

### Post by realzippy on 2011-09-28
> **Mikkå said:**
> 
What about that nvidia?

```
sudo apt-get purge nvidia-current
sudo add-apt-repository ppa:bumblebee/stable
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update
sudo apt-get upgrade
```
Reboot!

```
sudo apt-get install bumblebee
sudo usermod -a -G bumblebee yourusername

```
replace yourusername in last command !
Reboot.
then run
```
glxspheres

```
(basic benchmark running on default Intel graphics)

also run
```
optirun glxspheres

```
(now on Nvidia)
...should be pretty faster.

Works?

---

### Post by Mikkå on 2011-09-28
After running sudo glxspheres:

Polygons in scene: 62464
ERROR (584): Could not obtain RGB visual with requested properties

I could run the optirun, and get the psycedelic test screen. Meanwhile i lost my beloved 3D desktop and about 1/4 of my screen is totally black. :D

---

### Post by Mikkå on 2011-09-28
What are commands for manually stopping bumblebee? Couldnt find any on the web.

---

### Post by realzippy on 2011-09-29
Have you run any other commands between post #6 and post #8 ?
If not,it seems that installing bumblebee/x-swat ppa ( #8 )
"destroyed" your running "intel" 3D graphics,so I guess
the xswat packages are the reason.
Try to get back:
```
sudo apt-get purge bumblebee
sudo apt-get install ppa-purge
sudo ppa-purge ppa:ubuntu-x-swat/x-updates
sudo apt-get update
```

reboot.
Have the 3D desktop back ?

---

### Post by Mikkå on 2011-09-29
It didnt went too good. :D I was able to remove bumblebee via purge command, put that command didnt do anything good after that.

Tehdään asetuksia: nvidia-current (195.36.15-0ubuntu2) ...
update-initramfs: deferring update (trigger activated)
Removing old nvidia-current-195.36.15 DKMS files...

------------------------------
Deleting module version: 195.36.15
completely from the DKMS tree.
------------------------------


Done.
Loading new nvidia-current-195.36.15 DKMS files...
Building only for 2.6.38-10-generic
Building for architecture i686
Building initial module for 2.6.38-10-generic

Error! Bad return status for module build on kernel: 2.6.38-10-generic (i686)
Consult the make.log in the build directory
/var/lib/dkms/nvidia-current/195.36.15/build/ for more information.
dpkg: virhe käsiteltäessä nvidia-current (--configure):
 aliprosessi installed post-installation script palautti virhetilakoodin 10
Suoritetaan kohteen python-gmenu liipaisimia...
Rebuilding /usr/share/applications/desktop.fi_FI.utf8.cache...
Suoritetaan kohteen initramfs-tools liipaisimia...
update-initramfs: Generating /boot/initrd.img-2.6.38-10-generic
W: Possible missing firmware /lib/firmware/rtl_nic/rtl8168d-2.fw for module r8169
W: Possible missing firmware /lib/firmware/rtl_nic/rtl8168d-1.fw for module r8169
Suoritetaan kohteen python-support liipaisimia...
Käsittelyssä tapahtui liian monta virhettä:
 nvidia-current
E: Sub-process /usr/bin/dpkg returned an error code (1)


After typing "sudo apt-get install ppa-purge"

...
Done.
Loading new nvidia-current-195.36.15 DKMS files...
Building only for 2.6.38-10-generic
Building for architecture i686
Building initial module for 2.6.38-10-generic

Error! Bad return status for module build on kernel: 2.6.38-10-generic (i686)
Consult the make.log in the build directory
/var/lib/dkms/nvidia-current/195.36.15/build/ for more information.
dpkg: virhe käsiteltäessä nvidia-current (--configure):
 aliprosessi installed post-installation script palautti virhetilakoodin 10
Suoritetaan kohteen python-gmenu liipaisimia...
Rebuilding /usr/share/applications/desktop.fi_FI.utf8.cache...
Suoritetaan kohteen initramfs-tools liipaisimia...
update-initramfs: Generating /boot/initrd.img-2.6.38-10-generic
W: Possible missing firmware /lib/firmware/rtl_nic/rtl8168d-2.fw for module r8169
W: Possible missing firmware /lib/firmware/rtl_nic/rtl8168d-1.fw for module r8169
Suoritetaan kohteen python-support liipaisimia...
Käsittelyssä tapahtui liian monta virhettä:
 nvidia-current
E: Sub-process /usr/bin/dpkg returned an error code (1)


Dunno where u are from, there are finnish commends so it maybe difficult u to get any sense of those error messages. And i think i dont need to mention that 3D desktop doesnt work. :D  Put at least i did get full screen working by removing all 3D apps.

---

### Post by realzippy on 2011-09-29
Mikkå,
if you don't have data to loose,I think the fastest way to solve that
is a fresh install.
Then run again
```
sudo add-apt-repository ppa:glasen/intel-driver 
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install linux-image-generic-lts-backport-natty linux-headers-generic-lts-backport-natty
```
and post.Wait with that bumblebee....

If a fresh install is something you want to avoid for some reason,then,well,
I had to think things over to find a solution for you...

---

### Post by Mikkå on 2011-09-29
Got 3D pack by removing nvidia driver and re-installing the intell driver and uptaiding the whole system. Used those commands u posted earlier.

---

### Post by Mikkå on 2011-09-29
I didnt install new linux image, put should i? System seems to bee stable and running with out any errors. Do u have better codes for this time for the bumblebee?? :P

---

### Post by realzippy on 2011-09-29
Glad you made it,so no fresh install.
As mentioned earlier,I guess the xswat ppa messed up your graphics..
so just installl bumblebee,without xswat:
```

sudo add-apt-repository ppa:bumblebee/stable
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install bumblebee
sudo usermod -a -G bumblebee yourusername
```
mind replacing yourusername

---

### Post by Mikkå on 2011-09-29
After Install command i receive the same error message that i posted earlier.. So,, not working.

---

### Post by realzippy on 2011-09-29
> **Mikkå said:**
> After Install command i receive the same error message that i posted earlier.. So,, not working.

Can you post command and error ?

Is your 3D desktop gone again ?

---

### Post by Mikkå on 2011-09-29
mikko@mikko-laptop:~$ sudo apt-get upgrade
Luetaan pakettiluetteloita... Valmis
Muodostetaan riippuvuussuhteiden puu       
Luetaan tilatiedot... Valmis        
Nämä paketit on jätetty odottamaan:
  linux-generic linux-headers-generic linux-headers-generic-lts-backport-natty linux-image-generic linux-image-generic-lts-backport-natty
0 päivitetty, 0 uutta asennusta, 0 poistettavaa ja 5 päivittämätöntä.
2 ei asennettu kokonaan tai poistettiin.
Toiminnon jälkeen käytetään 0 t lisää levytilaa.
Haluatko jatkaa [K/e]? k
Tehdään asetuksia: nvidia-current (195.36.24-0ubuntu1~10.04) ...
update-initramfs: deferring update (trigger activated)
Removing old nvidia-current-195.36.24 DKMS files...

------------------------------
Deleting module version: 195.36.24
completely from the DKMS tree.
------------------------------
Done.
Loading new nvidia-current-195.36.24 DKMS files...
First Installation: checking all kernels...
Building only for 2.6.38-10-generic
Building for architecture i686
Building initial module for 2.6.38-10-generic

Error! Bad return status for module build on kernel: 2.6.38-10-generic (i686)
Consult the make.log in the build directory
/var/lib/dkms/nvidia-current/195.36.24/build/ for more information.
dpkg: virhe käsiteltäessä nvidia-current (--configure):
 aliprosessi installed post-installation script palautti virhetilakoodin 10
dpkg: riippuvuusongelmat estävät paketin bumblebee asetusten asettamisen:
 bumblebee riippuu paketista nvidia-current; kuitenkin:
  Paketille nvidia-current ei ole tehty vielä asetuksia.
dpkg: virhe käsiteltäessä bumblebee (--configure):
 riippuvuusongelmia - jätetään asetukset säätämättä
No apport report written because the error message indicates it's a follow-up error from a previous failure.
                                                                                                            Suoritetaan kohteen python-gmenu liipaisimia...
Rebuilding /usr/share/applications/desktop.fi_FI.utf8.cache...
Suoritetaan kohteen initramfs-tools liipaisimia...
update-initramfs: Generating /boot/initrd.img-2.6.38-10-generic
W: Possible missing firmware /lib/firmware/rtl_nic/rtl8168d-2.fw for module r8169
W: Possible missing firmware /lib/firmware/rtl_nic/rtl8168d-1.fw for module r8169
Suoritetaan kohteen python-support liipaisimia...
Käsittelyssä tapahtui liian monta virhettä:
 nvidia-current
 bumblebee
E: Sub-process /usr/bin/dpkg returned an error code (1)
mikko@mikko-laptop:~$ 


3D is running great at the moment.

---

### Post by realzippy on 2011-09-29
What I can see (tried to online-translate finnish-german,funny nonsense )that for some reason bumblebee tries to install 
nvidia-current-[COLOR="Red"]195.36.15[/COLOR]...is this correct translated?
It should be 270.something ...but only "nvidia-current"!
Have no idea why bumblebee does this in the moment.
Is it possible that you tried to install nvidia-drivers (195?)manually formerly?
Can you change your system language to english temporarily and repeat?

---

### Post by Mikkå on 2011-09-29
Its correct translated,bumblebee tries to install nvidia-current-195.36.15. I tried to change the language but wasnt able to get it all translatet. I will return to that later this week, got too much lectures and not much time, my language settings are now pretty much messed up. Its all "finglish" :D
And yes, i did tried to isntall nvidia manually at the time i wasnt aware of that this computer had this optimus system in it. 
Here is what i get running sudo apt-get install bumblebee. Dunno do u get any out of that, though it has some lines in Finis also. I will post fully english version later.

mikko@mikko-laptop:~$ sudo apt-get install bumblebee
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  dkms nvidia-current nvidia-settings virtualgl
The following NEW packages will be installed
  bumblebee dkms nvidia-current nvidia-settings virtualgl
0 upgraded, 5 newly installed, 0 to remove and 5 not upgraded.
Need to get 0B/25.5MB of archives.
After this operation, 77.8MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Valitaan aikaisemmin valitsematon paketti virtualgl.
(Luetaan tietokantaa... 215626 tiedostoa ja hakemistoa tällä hetkellä asennettuna.)
Puretaan pakettia virtualgl (.../virtualgl_2.2.90-1~lucidppa4_i386.deb)...
Valitaan aikaisemmin valitsematon paketti dkms.
Puretaan pakettia dkms (.../dkms_2.1.1.2-2ubuntu1_all.deb)...
Valitaan aikaisemmin valitsematon paketti nvidia-current.
Puretaan pakettia nvidia-current (.../nvidia-current_195.36.24-0ubuntu1~10.04_i386.deb)...
Valitaan aikaisemmin valitsematon paketti bumblebee.
Puretaan pakettia bumblebee (.../bumblebee_2.4.1-1~lucidppa1_i386.deb)...
Valitaan aikaisemmin valitsematon paketti nvidia-settings.
Puretaan pakettia nvidia-settings (.../nvidia-settings_195.36.08-0ubuntu2_i386.deb)...
Suoritetaan kohteen man-db liipaisimia...
Suoritetaan kohteen ureadahead liipaisimia...
ureadahead will be reprofiled on next reboot
Tehdään asetuksia: virtualgl (2.2.90-1~lucidppa4) ...

Tehdään asetuksia: dkms (2.1.1.2-2ubuntu1) ...

Tehdään asetuksia: nvidia-current (195.36.24-0ubuntu1~10.04) ...
update-alternatives: using /usr/lib/nvidia-current/ld.so.conf to provide /etc/ld.so.conf.d/GL.conf (gl_conf) in auto mode.
update-alternatives: varoitus: skip creation of /usr/lib32/vdpau/libvdpau_nvidia.so.1 because associated file /usr/lib32/nvidia-current/vdpau/libvdpau_nvidia.so.1 (of link group gl_conf) doesn't exist.
update-alternatives: varoitus: skip creation of /usr/lib32/libvdpau_nvidia.so because associated file /usr/lib32/nvidia-current/vdpau/libvdpau_nvidia.so (of link group gl_conf) doesn't exist.
update-initramfs: deferring update (trigger activated)
Loading new nvidia-current-195.36.24 DKMS files...
First Installation: checking all kernels...
Building only for 2.6.38-10-generic
Building for architecture i686
Building initial module for 2.6.38-10-generic

Error! Bad return status for module build on kernel: 2.6.38-10-generic (i686)
Consult the make.log in the build directory
/var/lib/dkms/nvidia-current/195.36.24/build/ for more information.
dpkg: virhe käsiteltäessä nvidia-current (--configure):
 aliprosessi installed post-installation script palautti virhetilakoodin 10
dpkg: riippuvuusongelmat estävät paketin bumblebee asetusten asettamisen:
 bumblebee riippuu paketista nvidia-current; kuitenkin:
  Paketille nvidia-current ei ole tehty vielä asetuksia.
dpkg: virhe käsiteltäessä bumblebee (--configure):
 riippuvuusongelmia - jätetään asetukset säätämättä
Tehdään asetuksia: nvidia-settings (195.36.08-0ubuntu2) ...
No apport report written because the error message indicates it's a follow-up error from a previous failure.
                                                                                                            Suoritetaan kohteen libc-bin liipaisimia...
ldconfig deferred processing now taking place
Suoritetaan kohteen python-gmenu liipaisimia...
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
Suoritetaan kohteen initramfs-tools liipaisimia...
update-initramfs: Generating /boot/initrd.img-2.6.38-10-generic
W: Possible missing firmware /lib/firmware/rtl_nic/rtl8168d-2.fw for module r8169
W: Possible missing firmware /lib/firmware/rtl_nic/rtl8168d-1.fw for module r8169
Suoritetaan kohteen python-support liipaisimia...
Käsittelyssä tapahtui liian monta virhettä:
 nvidia-current
 bumblebee
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

