---
title: "please advise, did i just kill my install?"
date: 2008-02-04
forum: Absolute Beginner Talk
---

### Post by strider123 on 2008-02-04
I am a total linux newbie and would appreciate any insight which you guys might provide. I installed 7.10 about a week ago and in my excitement, i began to install a bunch of apps via the terminal, as instructed by walkthroughs. In retrospect, I think i could have potentially done something REALLY bad. Judging by the commands I've inputted, is there anyway to tell  how badly i screwed up? Would i need to completely reinstall linux and change all of my online passwords? PLEASE bare with me and ANY info at all would be greatly appreciated.

Here is a list of the commands I have entered into the terminal:
 /usr/share/doc/libdvdread3/install-css.sh
apt-get autoremove
sudo apt-get remove wine
sudo apt-get remove wine_0.9.54~winehq0~ubuntu~7.10-1_i386_packages
gksudo synaptic
 /home/login/.wine #make uninstall
dpkg --remove clamav*
sudo tar xfprot-1.22.tar.gz
sudo tar xzvf xfprot-1.22.tar.gz
sudo dpkg -i fp-linux-ws.deb
sudo apt-get install firestarter
sudo dpkg -i avg75lms-r51-a1240.i386.deb
sudo -i avg75lms-r51-a1240.i386.deb
sudo deb -qip –scripts avg75lms-r51-a1240.i386.deb
wget [http://free.grisoft.com/softw/70free/setup/avg71flm-r30-a0791.i386.rpm](http://free.grisoft.com/softw/70free/setup/avg71flm-r30-a0791.i386.rpm)
sudo rpm -qip –scripts avg75lms-r51-a1240.i386.deb
sudo gedit /usr/share/applications/avg.desktop
apt-get install chkrootkit.
 wget -c [http://downloads.rootkit.nl/rkhunter-1.3.0-.tar.gz](http://downloads.rootkit.nl/rkhunter-1.3.0-.tar.gz)
 sudo dpkg -i avg75fld-r51-a1243.i386.bed
wget [http://free.grisoft.com/filedir/inst/avg75fld-r51-a1243.i386.deb](http://free.grisoft.com/filedir/inst/avg75fld-r51-a1243.i386.deb)
sudo dpkg -i rkhunter-1.3.0.tar.gz
wget [http://downloads.sourceforge.net/rkhunter/rkhunter-1.3.0.tar.gz?modtime=1190502076&big_mirror=0](http://downloads.sourceforge.net/rkhunter/rkhunter-1.3.0.tar.gz?modtime=1190502076&big_mirror=0)
sudo ./install-desktop-entries.sh install
 cd /usr/lib/avast4workstation/share/avast/desktop
sudo dpkg -i avast4workstation_1.0.8-2_i386.deb
wget [http://files.avast.com/files/linux/avast4workstation_1.0.8-2_i386.deb](http://files.avast.com/files/linux/avast4workstation_1.0.8-2_i386.deb)
 sudo dpkg -i avg75lms-r51-a1240.i386.deb
 sudo dpkg -i avast4workstation_1.0.8-2_i386.deb
/home/login/desktop/rkhunter-1.3.0/installer.sh
apt-cache search clamav
sudo apt-get install avg
 sudo apt-get install rkhunter
 "cd/c:/home/login/Desktop/rkhunter-1.3.0
 "cd/c:/home/login/Desktop/rkhunter-1.3.0.tar.gz"
sudo apt-get install denyhosts
sudo apt-get install rkhunter
ps ax | grep [c]lamd
 wget [http://download.bitdefender.com/unices/old/linux/free/bitdefender-console/en/BitDefender-Console-Antivirus-7.1-3.linux-gcc3x.i586.debps](http://download.bitdefender.com/unices/old/linux/free/bitdefender-console/en/BitDefender-Console-Antivirus-7.1-3.linux-gcc3x.i586.debps) ax | grep [c]lamd
sudo apt-get install gnome-vfs-obexftp
sudo mv -i essential-20071007/* /usr/lib/win32/n
tar jxfv essential-20071007.tar.bz2
wget [http://www3.mplayerhq.hu/MPlayer/releases/codecs/essential-20071007.tar.bz2](http://www3.mplayerhq.hu/MPlayer/releases/codecs/essential-20071007.tar.bz2)
sudo apt-get install netspeed
sudo aptitude install mozilla-acroread
 sudo aptitude install acroread acroread-plugins acroread-escript
wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add - && sudo apt-get update
 echo "deb [http://packages.medibuntu.org/gutsy](http://packages.medibuntu.org/gutsy) free non-free" | sudo tee -a /etc/apt/sources.list
 echo "deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) gutsy free non-free" | sudo tee -a /etc/apt/sources.list
sudo /usr/share/doc/libdvdread3/install-css.sh

here are commands i entered into the terminal as root:
wget [http://free.grisoft.com/fildir/inst/avg75fld_r51-a1243.i386.deb](http://free.grisoft.com/fildir/inst/avg75fld_r51-a1243.i386.deb)
sudo visudo
sudo bash install.sh $usr
sudo chgrp truecrypt/usr/bin/truecrypt

I'm also having some other problems:
1. when i'm running clamav, i'm only allowed to update in root. is that normal? same goes for rkhunter and xfprot
2. My resolution changes on me randomly when I turn on my desktop i have a nvidia 7300go video card. 

I an well aware that i'm probably trying on your patience and that some of the commands are non sensical if not comical. Once more, I'd like to thank you guys in advance for any help that you guys can provide and i'm going to read A LOT more before doing anything else. THANKS

---

### Post by oedha on 2008-02-04
sorry...i just want to ask.....
what os your purposed to install clamav and(or) avg....since we dont really need those

---

### Post by xpod on 2008-02-04
> I'm also having some other problems:
1. when i'm running clamav, i'm only allowed to update in root. is that normal? same goes for rkhunter and xfprot
2. My resolution changes on me randomly when I turn on my desktop i have a nvidia 7300go video card.

I an well aware that i'm probably trying on your patience and that some of the commands are non sensical if not comical. Once more, I'd like to thank you guys in advance for any help that you guys can provide and i'm going to read A LOT more before doing anything else. THANKS

Not sure about the dead install but there is`nt anything that cant be revived...somehow.so,dont panic ok.
For installing programs i suggest you stick to your package managers to start out
But.......[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

Question one is absolutely right......you must enter your admin(sudo) password to carry out any admin type tasks.
It`s a feature......not a bug:wink:

As far as question 2 goes have you installed the restricted drivers.....via the Restricted Drivers Manager in your menus???
IF you have then you can change your resolution via the preferences menu using "Screens & Graphics".....EDIT:...Sorry, I meant "Screen Resolution" in your preferences menu for the Res.

Failing that you can manually add the correct resolution to your xorg.conf but lets see where your at first.

---

### Post by xpod on 2008-02-04
> sorry...i just want to ask.....
what os your purposed to install clamav and(or) avg....since we dont really need those
__________________

Installed Clam AV on day 2.....never re-installed it on day 3 though and have never used any AV for over 18 months now.
OF course though if the OP shares files & stuff with his Windows using buddies then it`s probably not a bad idea having AV around.
Like many though i refuse to take responsibility for other peoples PC security so do not use any AV in any way,shape or form.
Have run rkhunter and the like occasionally but it never finds anything.

With 5 kids and even more PC`s i think our security has been well and truely tested.:)
Common sense and a little education is all thats required but if people using Ubuntu/Linux still allow themselves to be roped into some type of Social Engineering Exploit then they can but put it  down to experience....and at least learn from it.

---

### Post by hyper_ch on 2008-02-04
> **xpod said:**
> OF course though if the OP shares files & stuff with his Windows using buddies then it`s probably not a bad idea having AV around.
They should be able to protect themselves...

---

### Post by xpod on 2008-02-04
> They should be able to protect themselves...

Quite right,hence my....
> Like many though i refuse to take responsibility for other peoples PC security so do not use any AV in any way,shape or form.

:)

---

