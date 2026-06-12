---
title: "[SOLVED] Sorry guys, gonna have to add to the list of sound card issues"
date: 2008-01-16
forum: Absolute Beginner Talk
---

### Post by TwinkieFGR on 2008-01-16
I searched for a topic that would help me, but I was unsucessful.

I have a forte media sound card that I can not get to work. Already tried alsa mixer.

I managed to track my issues down to this page-
[http://www.alsa-project.org/main/index.php/Matrix:Module-fm801](http://www.alsa-project.org/main/index.php/Matrix:Module-fm801)

Near the top of this page is this command line
       cd /usr/src
       mkdir alsa
       cd alsa
       cp /downloads/alsa-* .

first 3 commands work fine, but when I get to the fourth command it tells me -
cp: cannot stat `/downloads/alsa-*': No such file or directory

I have no clue what I am doing wrong. and I am using Gutsy 7.10


Please help me?

---

### Post by balaknair on 2008-01-16
Is the folder downloads in your home folder? try 
cp ~/downloads/alsa-*

PS: it's also case sensitive, folder names and file names should match

---

### Post by TwinkieFGR on 2008-01-16
They weren't there, so I tried to manually create them and run the command again, but I got the same error.

---

### Post by balaknair on 2008-01-16
You have to download the the alsa files first from these links
[ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.15.tar.bz2](ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.15.tar.bz2)
[ftp://ftp.alsa-project.org/pub/lib/alsa-lib-1.0.15.tar.bz2](ftp://ftp.alsa-project.org/pub/lib/alsa-lib-1.0.15.tar.bz2)
[ftp://ftp.alsa-project.org/pub/utils/alsa-utils-1.0.15.tar.bz2](ftp://ftp.alsa-project.org/pub/utils/alsa-utils-1.0.15.tar.bz2)

Save them to a folder named downloads in you home directory

In order to compile from source you will need the ncurses library and kernel headers
Install them with the following command in a terminal
sudo aptitude install build-essential libncurses-dev gettext linux-headers-`uname -r`

Copy paste the whole line including the little **-r`**- it's part of the command
then in a terminal type
cd /usr/src/alsa
sudo cp ~/downloads/alsa* .
sudo tar xjf alsa-driver*.bz2
sudo tar xjf alsa-lib*.tar.bz2
sudo tar xjf alsa-utils*.tar.bz2
cd alsa-driver*
./configure --with-cards=fm801 --with-sequencer=yes ; make ; make install
cd ../alsa-lib*
./configure --with-cards=fm801 --with-sequencer=yes ; make ; make install
cd ../alsa-utils*
./configure --with-cards=fm801 --with-sequencer=yes ; make ; make install

modprobe snd-fm801 ; modprobe snd-pcm-oss ; modprobe snd-mixer-oss ; modprobe snd-seq-oss

alsamixer

now you're back to the alsa-project guide, continue from here [http://www.alsa-project.org/main/index.php/Matrix:Module-fm801#Setting_up_modprobe_and_kmod_support](http://www.alsa-project.org/main/index.php/Matrix:Module-fm801#Setting_up_modprobe_and_kmod_support)

---

### Post by TwinkieFGR on 2008-01-16
Ignore this for now, I think I just realized my mistake.

---

### Post by balaknair on 2008-01-16
OK
I hope you get things working now

If you do get things working, please mark the thread as solved
Allthe best

---

### Post by TwinkieFGR on 2008-01-16
Nope, I accidently unzipped the files, but it won't work even with the zipped files. The first part worked fine, installed the files from my disc, but then this happened-

censored-desktop:/usr/src/alsa$ sudo tar xjf alsa-driver*.bz2
tar: alsa-driver*.bz2: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
censored-desktop:/usr/src/alsa$ sudo tar xjf alsa-lib*.tar.bz2
tar: alsa-lib*.tar.bz2: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
censored-desktop:/usr/src/alsa$ sudo tar xjf alsa-utils*.tar.bz2
tar: alsa-utils*.tar.bz2: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors

Any suggestions?

---

### Post by balaknair on 2008-01-16
Sorry for the delay in replying, had to go to work
I'm not sure where you slipped up, but I think you might have mistyped the copy files command

sudo cp ~/downloads/alsa* .

the little . at the end is needed too.
I just replicated the copyand extraction process step by step on my PC, and it's working(the only difference is my downloads folder is Downloads(upper case D) so I type 
sudo cp ~/Downloads/alsa* .

---

### Post by balaknair on 2008-01-16
It seems to be the copy process that's causing you grief
You can use the graphical method to over come that

Press the Alt+F2 keys--> this opens a run dialog--> type gksudo nautilus--> it'll ask for your password--> enter your password--> it'll open a nautilus file browser window with root privileges--> navigate to your home folder>downloads folder--> copy the alsa  tar.bz2 files and without closing the window navigate to the /usr/src/alsa folder and paste the files there, and you can unzip them there. close the window.
Then return to the terminal
cd /usr/src/alsa/alsa-driver*
./configure --with-cards=fm801 --with-sequencer=yes ; make ; make install
cd ../alsa-lib*
./configure --with-cards=fm801 --with-sequencer=yes ; make ; make install
cd ../alsa-utils*
./configure --with-cards=fm801 --with-sequencer=yes ; make ; make install

modprobe snd-fm801 ; modprobe snd-pcm-oss ; modprobe snd-mixer-oss ; modprobe snd-seq-oss

alsamixer

---

### Post by TwinkieFGR on 2008-01-17
Well, I didn't have a chance to play with it yesterday, but I just booted into Ubuntu.

And I heard the boot theme. 
Checked an episode of reaper, and I could hear it fine.
I'm not quite sure what happened, but I seem to have sound now.

Thank you very much Balaknair, you were very helpful.

---

### Post by balaknair on 2008-01-17
That's nice to hear. maybe something you tried during all this provided the one missing piece you needed.
:D

Have fun

---

