---
title: "help me~! im a nobe with linux"
date: 2007-05-09
forum: Absolute Beginner Talk
---

### Post by kambeng02 on 2007-05-09
hi guys
i just knew about all the linux 2 days ago, i have download the image four ubuntu n tried to run it without installed it into my laptop, im using compaq presario v3000 notebook with 512 mb n windows vista home basic edition, im scared that if i install it into my laptop, i can't change back to microsoft, n lost all my data, when i run ubuntu with life cd, i cant use my wireless connection, what am i supposed to do to connect to the net via ubuntu? let see my network name is "abc" n my pass is "123",wat should i write? which type of security should i choose? secondly, i got a problem when playing the music, i cant hear anything from the speaker, please help me, i really want my notebook to look like the one in youtube
best regard
-ame-

---

### Post by Happy_Man on 2007-05-09
Well, for wireless, whiat kind of wireless card do you have? And speakers, which sound card do you have? In Ubuntu, knowing what hardware you've got is important.

---

### Post by KIAaze on 2007-05-09
First of all, no, if installed correctly (which is not very hard), there will be no data loss. :)
Just follow the howto [here]("http://www.google.com/url?sa=t&ct=res&cd=1&url=http%3A%2F%2Fwww.psychocats.net%2Fubuntu%2Finstalling&ei=WbZBRveUK5WE-QK5i9jvDg&usg=AFrqEzeCeAyVlR_HcQTZuCYaPcsgAY77mA&sig2=ur7856tevhv_T_Yi0Qe7QQ").

Now for your problems.
1)wireless not working
2)no sound
3)You want to install Beryl or compiz

1) I recommend you go see at this site:
[http://starbase-12.blogspot.com/2006/09/compaq-presario-v3000-with-ubuntu-606.html]("http://starbase-12.blogspot.com/2006/09/compaq-presario-v3000-with-ubuntu-606.html")
**It's a user who has exactly the same laptop as you, a presario v3000.** ;)

2)Try running the command ```
alsaconf
```.
It's something that solved one of my sound problems once.

3)You should first install your system before attacking that part.
And Compiz (one of the 3D desktops) comes by default with Feisty, so that shouldn't be too much of a problem hopefully. :)

---

### Post by Sef on 2007-05-09
Read [Psychocat's installing]("http://www.psychocats.net/ubuntu/installing") to dual boot from the Desktop (Live) CD.

---

### Post by starcraft.man on 2007-05-09
> **kambeng02 said:**
> hi guys
i just knew about all the linux 2 days ago, i have download the image four ubuntu n tried to run it without installed it into my laptop, im using compaq presario v3000 notebook with 512 mb n windows vista home basic edition, im scared that if i install it into my laptop, i can't change back to microsoft, n lost all my data, when i run ubuntu with life cd, i cant use my wireless connection, what am i supposed to do to connect to the net via ubuntu? let see my network name is "abc" n my pass is "123",wat should i write? which type of security should i choose? secondly, i got a problem when playing the music, i cant hear anything from the speaker, please help me, i really want my notebook to look like the one in youtube
best regard
-ame-

Just a side note since your questions already been answered... 

Just my opinion buy ya got kinda shafted with home basic, thats a REALLY crappy version of Vista, not to mention it lacks aero and most of the other features Vista is sold on (its practically more stripped down than the old XP home)... if your computer can't handle Aero I'd advise ya to call up MS or your manufacturer and downgrade to XP Pro, the "security benefits" of Vista are well worthless if your PC does nothing...

Just my opinion, have a nice experience with Ubuntu and if ya got anymore questions don't be shy :)

Edit: Hey Sef, why does it seem you always squeeze in a super fast post right before I get mine in? Are you forum stalking me? :p

---

### Post by KIAaze on 2007-05-09
[B]Oops, I didn't see he had Vista and not XP!

/!\/!\/!\ In that case, things get a little bit more complicated from what I've heard... /!\/!\/!\[/B]

Try this tutorial for example:
[http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first]("http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first")

I haven't read it completely and don't know how good it is, but you can always google for "dual boot vista and ubuntu" to find something else.

---

### Post by slibuntu on 2007-05-09
Actually, the sound problem could be a codec issue? See the RestrictedFormats wiki page for more details

---

### Post by starcraft.man on 2007-05-09
> **KIAaze said:**
> [B]Oops, I didn't see he had Vista and not XP!

/!\/!\/!\ In that case, things get a little bit more complicated from what I've heard... /!\/!\/!\[/B]

Try this tutorial for example:
[http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first]("http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first")

I haven't read it completely and don't know how good it is, but you can always google for "dual boot vista and ubuntu" to find something else.

Or you can downgrade to XP... up to you, I don't see much of a reason for MS to have even made basic, except for parents who want to make their children cry from its crappyness.

---

### Post by kambeng02 on 2007-05-09
> **Happy_Man said:**
> Well, for wireless, whiat kind of wireless card do you have? And speakers, which sound card do you have? In Ubuntu, knowing what hardware you've got is important.

for wireless is broadcom 802.11b/G WLAN, n for sound card is Conexant High Definition Audio, thanx for ur kindness, really appreciate if u can settle it

---

### Post by seshomaru samma on 2007-05-09
for wireless try[ this]("https://help.ubuntu.com/community/WifiDocs/WPAHowTo")

---

### Post by kambeng02 on 2007-05-10
guys, i still cant settle my problem, please help me, this is what i get after i use lpsci

00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)
**00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)**
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) Serial ATA Storage Controller AHCI (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
**05:00.0 Network controller: Broadcom Corporation Dell Wireless 1390 WLAN Mini-PCI Card (rev 01)**
08:08.0 Ethernet controller: Intel Corporation PRO/100 VE Network Connection (rev 02)
08:09.0 FireWire (IEEE 1394): Ricoh Co Ltd Unknown device 0832
08:09.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
08:09.2 System peripheral: Ricoh Co Ltd Unknown device 0843 (rev 01)
08:09.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
08:09.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)

there are 2 problems, my wireless n my sound system, what should i do? plzz help me

---

### Post by KIAaze on 2007-05-10
Have you tried the link I gave earlier?:
[http://starbase-12.blogspot.com/2006/09/compaq-presario-v3000-with-ubuntu-606.html]("http://starbase-12.blogspot.com/2006/09/compaq-presario-v3000-with-ubuntu-606.html")

I know it's about Ubuntu 6.06 on a Compaq Presario V3000, and not Ubuntu 7.04, but there shouldn't be too many differences.

> download the **ubuntu amd64 generic** cd and instal.
update the system
install the nvidia drivers and restart X

wireless is a problem and took me a while to figure out but its simple really. **_i had a lot of problems because i was using 32 bit driver instead of the 64 bit required_**.

    * .install all the development packages ( linux-kernel-devel & linx headers )
    * download the latest ndiswrapper source and extract it.
    * go into the extracted directory and do
          o make & sudo make install

    * . get the wireless drivers from Compaq's website as the ones on the windows partition are 32 bit ones and linux needs the compaq 64-bit versions to work. Get cabextract and get it to extract the compaq drivers exe file using the command
          o cabextract sp33008.exe

    * . there will be a bcmwl5.inf and a bcmwl5.sys file in the current foder. run the command
          o sudo ndiswrapper -i bcmwl5.inf

    * this will install the drivers and doing
          o ndiswrapper -l shows
                + Installed drivers:
                + bcmwl5 driver installed, hardware present

    * Now run
          o sudo ndiswrapper -m

    * Reboot the laptop.

    * Upon startup run
          o sudo modprobe ndiswrapper

    * the wireless modles are now working. run iwconfig and there should be a wlan0 with wireless extensions. yu can now connect to a network using
          o sudo iwconfig wlan0 essid name-of-essid
          o dhclient wlan0


Sound gave a little trouble. Apparently there a bug in ALSA ( pre 1.0.13 versions ) which cause trouble with the headphone jack. The 1.0.13 version fixes this problem though and can be downloaded from here. Compile and install it and it creats a "sound" script in the /etc/modprobe.d folder. Open this file and add :
options snd-hda-intel index=0 disable_msi=1

Failure to add this results in the sound playing for half a second and getting stuck in an infinite loop. Well now the headphone jack works, its just wierd that the laptop speakers and headphone jack dont have the same control but different controls. Also the laptop speakers dont shut off when one plugs in a headphone, since their volumes are independent.

Now for the 64-bit issue. A lot of problems arise out of using a 64-bit kernel which basically highlight how behind the world still is in 64-bit computing.

For starters i had a bad time trying to find a video player as the 32-bit codecs for wmv, mov and others dont work here with any midea player ( Xine, Mplayer, Vlc, etc ). The sollution was this : I installed that cool software called Automatix. I dont remember how I got it but just google it I guess ( If you try it and get it working please send me a msg and I will edit this post ). In Automatix there is an option for a 32-bit Mplayer and its codecs, install it and your video should work.

Then I also was unable to view flash media on firefox. The solution, install a 32-bit version of Swiftfox and flash as well. This can also be done through Automatix.

And I think it's easier to do all this after installing Ubuntu on your system, since I have no idea about the limitations on system configuration and program installation when running from a live-CD.

---

### Post by kambeng02 on 2007-05-12
hye, plz help me, im really stupid with linux, i dont understand with what u mean for this statement

* .install all the development packages ( linux-kernel-devel & linx headers )
* download the latest ndiswrapper source and extract it.
* go into the extracted directory and do
o make & sudo make install

help me, can uu give me any site for me as an amatuer for linux? how to use it, what the code, and anything else, thanx for your help

---

### Post by KIAaze on 2007-05-14
> * .install all the development packages ( linux-kernel-devel & linx headers )
-Go into System->Administration->Synaptic Package manager
-Click on search and type "linux-kernel".
-You'll find something called "linux-kernel-devel". Select it.
-Click on search and type "linux-headers".
-There will be several packages listed. I don't know exactly which one you will need however.
Just select the one that seems to be the latest and most appropriate.
I would suggest everything that ends with "generic" or "386". Eventually, you could also select all of them if there are no compatibility problems.
-Click on "Apply" and confirm the appearing message box.

> * download the latest ndiswrapper source and extract it.
-Go to [http://sourceforge.net/project/showfiles.php?group_id=93482]("http://sourceforge.net/project/showfiles.php?group_id=93482") and download the latest release.
Currently it's "ndiswrapper-1.43.tar.gz".
If you want or if that one doesn't work, you could download the testing version "ndiswrapper-1.44rc1.tar.gz".

> * go into the extracted directory and do make & sudo make install
-Well, now that you have downloaded the tar.gz file, just go to where you downloaded it and extract it.
To extract it, you can either just right-click on the file and select "extract here" (or "extract to") or you can do it by command-line by doing:
```
tar -xzvf ndiswrapper-1.43.tar.gz
```

-Now that it's extracted, open a terminal (applications->accessories->Terminal)
-go into the extracted folder:
```
cd ~/Desktop/ndiswrapper-1.43
``` (assuming you extracted it on your Desktop)

-Now type ```
ls
```.
This should list the contents of the folder in which you are. There should be a file called "Makefile".
If not, you did something wrong. Go back and make sure that you are in the correct folder after the "cd" command (cd=change directory).

-If the Makefile is listed, then you can start:
Type:
```
make
```
If there are error messages, please post them here.
Type:
```
sudo make install
```
If there are error messages, please post them here.

Most of the time, the error messages are about missing packages.
Go into synaptic package manager like before, search for the packages and install them.

---

