---
title: "music library on a second HD (is forgotten by amaroK)"
date: 2006-08-29
forum: Absolute Beginner Talk
---

### Post by happyisland on 2006-08-29
If someone could help me with what I hope is a pretty simple problem I would be much obliged. I have a pretty large library of mp3s, oggs, etc and want to use amaroK as a library and player. I have amaroK installed and it works great - I'm listening to it right now. 
Ok, here's the problem:
All of my music is on a different (SATA) HD from the boot HD. Every time I reboot my PC the amaroK library is empty again and I have to make it rescan which takes ages. This same thing happened with the Listen music player. Does it maybe have something to do with the way I have the backup SATA drive mounted or something? I am brand-new to the linux game and could easily have messed up on installing the second HD.
Thanks for the help in advance. I recently switched to Ubuntu from XP, and this is the ONLY thing that is not running perfectly.
-HI

---

### Post by happyisland on 2006-08-29
I forgot to put that I'm using amaroK 1.3.9.

---

### Post by orb9220 on 2006-08-29
Try 1.4.2 and see if it solves your problem. I think you need to unistall 1.3.9 first but not sure. Using it now runs great and alot more features.
open terminal and copy and paste one line at a time.

wget [http://people.ubuntu.com/~jriddell/kubuntu-packages-jriddell-key.gpg](http://people.ubuntu.com/~jriddell/kubuntu-packages-jriddell-key.gpg)

sudo -s

apt-key add kubuntu-packages-jriddell-key.gpg

echo "deb [http://kubuntu.org/packages/amarok-latest](http://kubuntu.org/packages/amarok-latest) dapper main" >> /etc/apt/sources.list

apt-get update

apt-get install amarok amarok-engines 

Hope this helps.

---

### Post by atomkarinca on 2006-08-29
it can be a mount problem too. is the drive fat or ntfs? then you should update your /etc/fstab according to that.

---

### Post by happyisland on 2006-08-30
I just installed the newest amaroK - thanks for the great how-to, orb9220! Thing is, though it's way better I still have the same library issue. I guess it has to do with the way I have my second HD set up? 
I will try to figure out how to edit my fstab today and see if that works. The drive, btw, is ext3.

---

### Post by happyisland on 2006-08-30
atomkarinca, or anyone else, could you please help me figure out how to configure the fstab file to make my second HD work correctly? The drive is formatted ext3 and is /dev/sda . I just want to be able to have the drive be trackable by amaroK so I don't have to rescan the library every time I turn on the computer...
THANKS!
PS: btw, I looked all over to try to figure out what to do, but the manuals I could find were all too technical for me and I couldn't find a how-to on these boards.

---

### Post by happyisland on 2006-08-30
Ok, I figured out the fstab thing and now IT WORKS!
I am soooooo happy...
Thanks for the help,
HI

---

### Post by dannyboy79 on 2006-09-01
Ok Happyisland, I am really happy for you that you figured it out but one of the main reasons that we have forums is so that people with similar problems can view and read previous threads to figure out their own problems. When a person posts a problem and then later responds to everyone and says, "Nevermind, I figured it out" and doesn't explain what he/she did that isn't really gonna help Linux catch on!!! Can you please post how you got this to work as I am sure I am not the only one with this problem and it will benefit others. I am sorry for being kind of snippy with this but I do see this way to often and myself being a linux newbie as well as you, I am sure you can understand my frustration when you get to a forum read thru super many posts and then at the end you see a post like yours that doesn't contain an answer. So please, please post how you resolved this. Thank you very much and please don't take this the wrong way.

---

### Post by HdK on 2006-09-01
I get this when I try to  put command in $ wget [http://people.ubuntu.com/~jriddell/k...iddell-key.gpg](http://people.ubuntu.com/~jriddell/k...iddell-key.gpg)
--18:58:14--  [http://people.ubuntu.com/~jriddell/k...iddell-key.gpg](http://people.ubuntu.com/~jriddell/k...iddell-key.gpg)
           => `k...iddell-key.gpg'
Resolving people.ubuntu.com... 82.211.81.132
Connecting to people.ubuntu.com|82.211.81.132|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
18:58:14 ERROR 404: Not Found.

---

### Post by orb9220 on 2006-09-01
Well you can skip the key step not neccessary for install.

---

### Post by happyisland on 2006-09-02
you betcha dannyboy. here's what I did:

In terminal I typed:
gksudo gedit /etc/fstab 
(this opens the fstab file in the text editor. fstab is the list of drives to be mounted when the computer starts up).

I then added a line at the bottom to represent the HD I wanted to add. This probably varies depending on how you've installed/formated your new drive, but in my case the new line was: 
/dev/sda1	/media/scsidisk ext3	defaults	0	0

Column 1 is the path where the drive is (with the "1" at the end pointing to  partition 1 - since this is a backup drive it's formated with only one partition (ie no swap, etc). You can find out what your HD is called by clicking System>Administration>Discs and then clicking on the HD in question.
Column 2 is the path where I want the drive to mount. You need to make sure that the folder you've specified (in my case one called "scsidisk" in the media folder) exists.
Column 3 is the filesystem that I used to format the drive. In my case "ext3"
Column 4 this is the Options field where you can specify how you want the drive to be treated on boot. An example is that you can mount it as read-only. I left this as "defaults" since I wanted to have the drive behave pretty normally.
Column 5 putting a zero here means that the drive will be ignored by the program "dump". If you want to use dump substitute a "1" for the zero.
Column 6 putting a zero here means the drive will not be checked by fsck, which is the linux file system consistency check program. 

MAJOR CAVEAT:
I am a total linux noob, with just a few weeks under my belt. The above steps worked for me, but I would recommend verifying this stuff from another source. I mostly figured it out from looking at this page:
[http://wiki.linuxquestions.org/wiki/Fstab](http://wiki.linuxquestions.org/wiki/Fstab)

---

