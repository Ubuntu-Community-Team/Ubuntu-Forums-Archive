---
title: "G5 install help"
date: 2009-04-16
forum: Apple Hardware Users
---

### Post by Zabadda on 2009-04-16
I have a G5 which im trying to test by installing linux on but im not sure what im doing as i've never used a MAC before.

It doesnt seem to be picking up the regular ubuntu 8.10 live cd so im not sure if this is even possible to do so. do i need a mac specific version? 

any help would be great, thanks

---

### Post by tiresia on 2009-04-16
[http://ubuntuforums.org/showthread.php?t=964904](http://ubuntuforums.org/showthread.php?t=964904)

---

### Post by Zabadda on 2009-04-16
thanks i tried a few of the options in that post but im not getting anywhere, all i get is the screen with the flashing mac folder in the centre

---

### Post by tiresia on 2009-04-16
OK, most probably you did not download the right installer cd for ppc, or you burned the cd wrong. Read the sticky thread for ppc for download, and burn the cd using the apple disk utility (if you still have macosx). If you are not experienced you can choose the livecd Ubuntu Hardy (8.04). There is no ubuntu intrepid livecd for ppc

Do you want to dualboot ubuntu with macosx?

Be aware, that the PowerMac G5 is a 64-bit machine. At the first (yaboot) prompt hit the TAB-key to choose an appropriate 64-bit option (anyway better 'nosplash' to see how it's booting)

---

### Post by Zabadda on 2009-04-16
i have no access to another mac or macos i have a G5 with no software and a blank HDD. Im looking to sell it on and as im not aware of the legal side about MAC OS etc i just wanted to install lnux on there to test everything works ok

---

### Post by tiresia on 2009-04-16
Are you sure, that you downloaded a cd for PowerPC? How did you burn it?

---

### Post by Zabadda on 2009-04-16
great! ok i didnt have the right version :) ok but now i got the install to work but now i get to a black screen where it asks for my login and pass which is fine now it just sits at the ubuntu command line im not sure what to type to get it to boot further

---

### Post by tiresia on 2009-04-16
> **Zabadda said:**
> great! ok i didnt have the right version :) ok but now i got the install to work but now i get to a black screen where it asks for my login and pass which is fine now it just sits at the ubuntu command line im not sure what to type to get it to boot further
If I understand well, you installed Ubuntu, but X isn't working? Did you use the LiveCD or the alternate CD to install Ubuntu?

---

### Post by Zabadda on 2009-04-16
i used the top one here [http://cdimage.ubuntu.com/ports/releases/8.10/release/](http://cdimage.ubuntu.com/ports/releases/8.10/release/)

---

### Post by tiresia on 2009-04-16
You used the Server Install CD, therefore you don't have any X (grafical interface).
Now either you reinstall Ubuntu using the alternate install cd, or you install the desktop on the installed Server Ubuntu. For this last option, do in the comman line (after logging in as normal user)
```
sudo apt-get install gnome-desktop-environment
```
You need to be connected to internet. Be patient, it will take a while

---

### Post by Zabadda on 2009-04-16
ok ill try those tomorrow :) cheers ill let u know how i get on

---

### Post by stream303 on 2009-04-16
> **Zabadda said:**
> i have no access to another mac or macos i have a G5 with no software and a blank HDD. Im looking to sell it on and as im not aware of the legal side about MAC OS etc i just wanted to install lnux on there to test everything works ok

If you don't plan on holding onto that machine, and just want to test basic functionality, you can download and run FINNIX-PPC, which is a sysadmin/rescue CD.

[http://www.finnix.org/](http://www.finnix.org/)

At the second-stage boot prompt, hit TAB and be sure to choose the 64bit option.  From there you will end up at the commandline and play around.

OR, you can keep the machine, and dedicate it solely to Ubuntu (or any other Linux distro that supports it like Debian etc)

What you are encountering is the wonderful wacky world of apple quirks that can be overcome, but if you aren't interested in keeping it, just run finnix as a quick test.

---

### Post by Zabadda on 2009-04-17
cheers for that ive got the finnix cd to boot to the command line but i really need a graphical display as i dont know what to do with the command line really lol

ill keep it tho for when i learn what im doing, it's just i work for a company that repairs and recycles old laptops and base units and we get a few macs here and there.

since ive been here ive converted a few people to Ubuntu for use at work and for testing all the hardware its perfect, thats why i need one for macs too :)

---

### Post by Zabadda on 2009-04-17
> **tiresia said:**
> You used the Server Install CD, therefore you don't have any X (grafical interface).
Now either you reinstall Ubuntu using the alternate install cd, or you install the desktop on the installed Server Ubuntu. For this last option, do in the comman line (after logging in as normal user)
```
sudo apt-get install gnome-desktop-environment
```
You need to be connected to internet. Be patient, it will take a while

ok i tried this but it was unable to find the package enviroment

---

### Post by Zabadda on 2009-04-17
i also downloaded the alternative version and i still have no x server installed, did i miss something on the install?

---

### Post by Zabadda on 2009-04-17
ok i tried "sudo apt-get install ubuntu-desktop" and that seems to be downloading it now, so ill see what happens after its done

---

### Post by Zabadda on 2009-04-17
DONE! its all installed and working :) does anyone have a link to an ISO that has the desktop already included as it took an hour to download.

---

### Post by tiresia on 2009-04-17
Sorry, for the mistake about the package name.
But, I don't understand why you don't get the desktop installed with the alternate Installer CD. Here are two links (http and torrent)
[http://cdimage.ubuntu.com/ports/releases/hardy/release/](http://cdimage.ubuntu.com/ports/releases/hardy/release/)
[http://cdimage.ubuntu.com/ports/releases/intrepid/release/](http://cdimage.ubuntu.com/ports/releases/intrepid/release/)
[http://torrent.ubuntu.com:6969/](http://torrent.ubuntu.com:6969/)

There is an Ubuntu Hardy LiveCD (it works very good, but installing it on some PowerMac G5 can gives problems with the bootloader [http://ubuntuforums.org/showthread.php?t=994882](http://ubuntuforums.org/showthread.php?t=994882)) 
The alternate Intrepid Installer has a bug (no cd-rom detected [http://ubuntuforums.org/showthread.php?t=964904](http://ubuntuforums.org/showthread.php?t=964904))

---

### Post by Zabadda on 2009-04-17
:) thats ok you've been a great help, id still be stuck otherwise. ill try those links thanks

---

