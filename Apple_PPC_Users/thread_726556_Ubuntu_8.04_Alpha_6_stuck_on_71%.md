---
title: "Ubuntu 8.04 Alpha 6 stuck on 71%"
date: 2008-03-16
forum: Apple PPC Users
---

### Post by Cows on 2008-03-16
I have a iBook 12 " 800 mhz 256 mb ram ppc g3. Everything goes fine until the installer reaches 71% , it doesn't move and stays at "Configuring APT Sources". I waited more then 40 minutes and nothing has happened. Any recommendations ?

[color=green]Solution :[/color] If you have more then 320 MB RAM, Use the GUI Installer. For some reason the Alternative did not work well on my iBook G3 with 256 MB RAM. I upgraded to 640 MB RAM but there still was a problem. After that I tried the GUI install and it worked perfectly.

---

### Post by BladeMelbourne on 2008-03-16
Are you plugged into a wired network?

I'm just guessing... it may be attempting to connect to an apt repo.

---

### Post by Cows on 2008-03-16
I was connected to a wired network but it was stuck so I just disconnected it and now I'm trying to install it with no internet connection. I can enable sources later if it would just install.

---

### Post by frog_pilot on 2008-03-17
I had the same issue. Try a later build. It worked again since 2008/03/12 daily build. Get it here [http://cdimage.ubuntu.com/ports/daily-live/current/]("http://cdimage.ubuntu.com/ports/daily-live/current/")

---

### Post by Cows on 2008-03-17
I downloaded this one yesterday :

hardy-alternate-powerpc.iso          17-Mar-2008 02:38  648M  Alternate install CD for Mac (PowerPC) and IBM-PPC (POWER5) computers (standard download)

[http://cdimage.ubuntu.com/ports/daily/current/](http://cdimage.ubuntu.com/ports/daily/current/)

I only have 256 MB RAM for my iBook so that live CD you gave me wouldn't run. Alternative only. Also I'm kinda mad since my computer needs a new kernel in order for WPA to work ; (.

---

### Post by frog_pilot on 2008-03-17
I wondered about your lack of ram. I would do a minimal install and then install xubuntu-desktop.

But why a new kernel for wpa.
Iconfigured a bcm4317 chip for wpa under feisty mor than a year ago. Some tweaking in wpa_supplicant.conf and a autostart script and it did work. But it was a broadcom-chip in an acer-notebook no airport or airport extreme. And did you look for "wireless" here in the ppc forum section? I remember several threads about wireless issues but not sure, if wpa was a topic there...

---

### Post by Cows on 2008-03-17
It's a new kernel to support WPA for original Airport cards. My card should be using the orinoco_cs drivers and so it requires a new kernel for WPA and WPA2 support.

[http://ubuntuforums.org/showthread.php?t=673771&highlight=wpa+airport](http://ubuntuforums.org/showthread.php?t=673771&highlight=wpa+airport)

That thread leads into the new kernel. I'm most likely just going to get Tiger or Panther.

PS: I don't think RAM is a issue because I installed Debian Etch 4.0r3 net-install and when the installation was complete ( 10x faster then Ubuntu installation ), I was booted onto a GNOME desktop. No problems whatsoever. It was actually extremely fast. About 5x faster then OS X. Only problem is the sound and WPA support.

EDIT: It wasn't March 17, 2008 the one I downloaded it was March 15, 2008. I'm downloading the March 17, 2008 one at the moment. Hopefully they should have fixed the problem. I really don't feel like buying Panther nor Tiger.

EDIT 2 : Something is definitely wrong with the installer. I burned the March 17, 2008 and it still got stuck at 71%. I'm going to install 7.10 since I already know how to fix everything on it. Hopefully when 8.04 comes out, everything will be fine. Also is PPC support coming back to Ubuntu ?

EDIT 3 : Looks like I don't need to recompile a new kernel since it was already developed ( patch ) ; ).

[http://ubuntuforums.org/showthread.php?t=304217&page=9](http://ubuntuforums.org/showthread.php?t=304217&page=9)

---

### Post by Cows on 2008-03-19
I just ordered 512 MB SD-RAM PC133. I will have 640 MB RAM in total which is the maximum for G3s. Hopefully it was a RAM issue and it will fix the installation problem.

---

### Post by frog_pilot on 2008-03-20
Do you remember what the installer was doing when it was on 71%? There are messages about current activities under the progress bar. On my system it failed during configuring apt and syncing with the package-server. But with the daily alternate image from 2008/03/12 it succeded.

If 2008/03/17-image didn't work for you, it is most likely something else in your case...

/edit:
I don't think it was a RAM-issue, if you used the alternate-cd.
Did gutsy-installation also fail?

---

### Post by Cows on 2008-03-20
It was Configuring APT Sources.

Gutsy installation did now fail. It did get stuck at Installing Yaboot Loader. Thing is that I had the Yaboot Loader already because the previous installation of Debian Etch didn't fail. Debian never failed on me. Only Ubuntu, but then again I used the Debian Etch Net-Install. So It didn't have much to install.

If Debian could install with no problem then it "HAS" to be a Hardy Heron installer problem under PPC. 

My RAM should be here tomorrow morning.

---

### Post by slacka-vt on 2008-03-20
why not use the Ubuntu Hardy net-installer then ?
worked great on my G4 TiBook, and i did it wirelessly.
discovered my Airport Card right away.

[Hardy PPC 32bit "Mini.iso" net-installer build 20080310-33]("http://archive.ubuntu.com/ubuntu/dists/hardy/main/installer-powerpc/20070308ubuntu33/images/powerpc/netboot/")

---

### Post by Cows on 2008-03-20
Thanks ;). Does yours support WPA though ?

---

### Post by Cows on 2008-03-20
The Net-Install Stays at "Starting Partitioner 55%" .. I'm going to wait till my 512 RAM gets here tomorrow. That should definitely let me install Ubuntu if it is RAM related issue. I'll let you guys know what happens.

---

### Post by slacka-vt on 2008-03-21
Yes, WPA Personal and WPA2 Personal are both fully supported on Hardy
straight "out-of-the-box".
Hope your RAM upgrade solves your installation issue.
Hardy has been running flawlessly on my TiBook G4 1Ghz with 768MB's of RAM.

Good luck!
~s

---

### Post by Cows on 2008-03-21
Alright Thanks. Hopefully it will install and my Original Airport card will support WPA & WPA 2.

---

### Post by Cows on 2008-03-21
It's really slow the installer, and it crashes. Now I know it was a alpha problem. I'll wait till the BETA gets to PPC.

---

### Post by Cows on 2008-03-21
I downloaded and burned the Ubuntu 8.04 Desktop Installer and it works like a charm. I have had no problems whatsoever and it's currently installing on my iBook G3. So far the only thing I don't like is that my Airport card still doesn't have WPA support out of the box. I have the Original Airport card with Orinoco chipset. I also believe I have no sound.

---

### Post by slacka-vt on 2008-03-21
After it's done installing, you should be able to set the wireless security to WPA.
Also, for some reason you will need to set the sound module to load at boot.
There's a thread here some where. 
Its called the powermac_snd .   .
here's the thread:

[http://ubuntuforums.org/showthread.php?p=3835472]("http://ubuntuforums.org/showthread.php?p=3835472")

You're almost there!
~s

What i did, verbatim is type in the terminal:

sudo nano /etc/modules

and added "snd_powermac"   *no quotes*

to the modules file, this automatically loads the sound driver at boot up.

reboot and you should be rewarded with the "Ubuntu Bongos" upon login.

~s

---

### Post by Cows on 2008-03-21
That's weird because sound works for me. It loads up on boot and everything. I can't set the security to WPA because i'm using the Original Airport card that runs on the Orinoco Chipset. Therefore I need to compile the Linux Kernel 2.6.24 with the appropriate patch.

[http://ubuntuforums.org/showthread.php?t=304217&page=2](http://ubuntuforums.org/showthread.php?t=304217&page=2)

---

### Post by slacka-vt on 2008-03-21
What do you see when you go to
System > Administration > Network
"unlock"
Select Wireless Connection
Press "Properties" button ?

No ability to select wireless encryption ?

~s

---

### Post by Cows on 2008-03-21
Oh SNAP LOL!!! It supports WPA .. how the hell did this happen lol... I was compiling the kernel and my screen turned black and I couldn't wake it up :(. Thanks.

---

### Post by Cows on 2008-03-22
What I'm trying to do now is enable smooth 3d acceleration on my ibook.

EDIT: There is also something wrong with the Virtual Terminals. If I try to bring up a tty1 or more I only see a black screen with a blinking cursor.

---

### Post by slacka-vt on 2008-03-22
That's about where I'm at.
I have a question for you though,
I'm assuming this iBook G3 doesn't have any kind of substantial video card.
Does it even support 3D Acceleration ?
I believe their is a minimal vram requirement and 
I don't believe your machine makes the cut.
Of course I could be wrong.

On another note, there has been numerous threads about compiz and glrx drivers and all that.
Basically, what I have gathered is:

There are no official drivers that support 3D Accelaeration for Nvidia (most common mac notebook) for the PPC architecture.
Just not enough demand.

So we are using a generic one that seems to work *well*.
However, there is some sort of 3D graphics enabled by default on our architecture
and we have no control over.
I.E., when you go to System > Preferences > Appearance 
choose "Visual Effects" tab,
and "None" is selected by default even though there is obviously *some*
3D Acceleration working.
When I choose either "Normal" or "Extra",
My screen flashes like somethings happening
then I get a "Desktop Effects Could not be Enabled" dialog box.

I have read through some threads that had some good info
but not ussualy pertaining to the PPC architecture

~s

---

### Post by Cows on 2008-03-22
Yea same here.

Check out this thread: 

[http://ubuntuforums.org/showthread.php?t=26148&page=4](http://ubuntuforums.org/showthread.php?t=26148&page=4)

be careful that you don't put "AGPMode "4". This will turn your screen black when you restart X . A fix to this is "AGPMode" "2" instead of "4". I'm not going to run 3d acceleration on my mac. I'm probably going to run Fluxbox or IceWM.

---

