---
title: "What was the last command you entered into Terminal?"
date: 2012-05-08
forum: Cafe Games
---

### Post by iMurshaq on 2012-05-08
Quite simple game but I doubt many people will remember!!!


```
sudo apt-get install cairo-dock
```

---

### Post by Enigmapond on 2012-05-08
```
sudo traceroute -n -w 2 -q 2 -m 30 8.8.8.8
```

---

### Post by CompyTheInsane on 2012-05-08
```
sudo poweroff
```

---

### Post by The Cog on 2012-05-08
```
exit
```

---

### Post by ajgreeny on 2012-05-08
```
history
```as I couldn't remember what it was I last entered!  Prior to that it was ```
sudo fc-cache -f -v
``` having just added a lot of unusual fonts that I need for my personal letter-headings and invoices.

---

### Post by PaulW2U on 2012-05-08
```
updates
```

it's an alias for 

```
sudo aptitude update && sudo aptitude -V safe-upgrade && date
```

---

### Post by catlover2 on 2012-08-22
```
yaourt -Syua&&halt
```

---

### Post by synaptix on 2012-08-22
```
gksudo gedit /etc/sysctl.conf
```

---

### Post by miegiel on 2012-08-22
```
mail
```

---

### Post by Petro Dawg on 2012-08-22
```
sudo apt-get upgrade
```

---

### Post by MG&amp;TL on 2012-08-22
```
sudo vim /etc/hostname 

```

Changing my server's hostname.

---

### Post by LiamOS on 2012-08-22
```
../../cloudy/source/cloudy.exe < 0.1.in.in > 0.1.out && gnuplot carbonPlotScript
```

---

### Post by CompyTheInsane on 2012-08-22
```

starttf2 -maxplayers 32 +exec [REDACTED].cfg +map mvm_mannworks +sv_password [REDACTED]

```
It runs a shell script for starting up a Team Fortress 2 server inside a screen session with parameters passed to srcds_run, last run on Saturday.

---

### Post by Mr.Dee on 2012-08-22
lynx [www.google.com]("http://www.google.com")

---

### Post by ubuntu27 on 2012-08-22
> **iMurshaq said:**
> Quite simple game but I doubt many people will remember!!!


```
sudo apt-get install cairo-dock
```

Well, you don't have to remember. Just press "up" key and it will display your last used command. And if you keep pressing "Up", it will shown even more. ^^


Mine is ```
sudo apt-get update && sudo apt-get dist-upgrade
```

---

### Post by malspa on 2012-08-22
> **The Cog said:**
> ```
exit
```

LOL!

Same here -- after running rsync to do my backups this morning.

---

### Post by synaptix on 2012-08-22
```
sudo sh ./amd-driver-installer-12.6-legacy-x86.x86_64.run --buildpkg Ubuntu/precise

```

---

### Post by Lisiano on 2012-08-22
```
iftop -nNpB -i eth0 -f "port 49400"
``` That's from a VPS I have.

---

### Post by catlover2 on 2012-08-22
sudo -s

---

### Post by IWantFroyo on 2012-08-22
gksudo gedit ~/.bashrc

---

### Post by synaptix on 2012-08-22
winecfg

---

### Post by Lisiano on 2012-08-22
```
flexedit
```
Which is a simple alias to this
```
nano ~/.flexget/config.yml
```

---

### Post by blackmail on 2012-08-22
```
sudo aptitude search cairo | grep dock

```

---

### Post by miegiel on 2012-08-22
```
cat /home/common/scripts/iptables-save-c.sky | sudo iptables-restore -c
```
(after saving and editing the rules ofc.)

---

### Post by Moose on 2012-08-22
sudo apt-get install amarok

---

### Post by gandalf3 on 2012-08-22
exit

---

### Post by pqwoerituytrueiwoq on 2012-08-22
```
cd /tmp;d="`date`";ln -s `f="$(ls -l /proc/$(pgrep -f flashplayer)/fd | grep deleted)" && f="${f##*:+([0-9]) }" && f="${f%% -*}" && echo /proc/$(pgrep -f flashplayer)/fd/"$f"` /tmp/"movie-$d";smplayer -fullscreen /tmp/"movie-$d"
```
used to play flash videos in smplayer where i can use vdpau

---

### Post by QIII on 2012-08-22
```

QIII@computer:~$ sudo apt-get winning-lottery-numbers
QIII@computer:~$ lol! like i haven't heard that one before.  loser!  leave me alone.  i have a date with a microwave.

```

---

### Post by Lisiano on 2012-08-23
```
mplayer_ kuulsuse_narrid.mpg
```
Which is a .bashrc function
```
function mplayer_(){
if [ `ffmpeg -i "$1" 2>&1 | grep "h264 (High 10)" -c` = 1 ]; then mplayer -geometry 1680:282 -*** -ontop -stop-xscreensaver -vc ffh264, -vo vdpau -fs "$1" `echo $@ | cut -f2- "-d "`; else mplayer -geometry 1680:282 -*** -ontop -stop-xscreensaver -vc ffh264vdpau, -vo vdpau -fs "$1" `echo $@ | cut -f2- "-d "`; fi
}
```

---

### Post by miegiel on 2012-09-03
```
sudo iftop -p -c iftop.resolve.conf
```

---

### Post by 73ckn797 on 2012-09-03
> **gandalf3 said:**
> exit


This ^

---

### Post by chellrose on 2012-09-08
```
./changebrightness.sh
```
which runs a little script for lowering my monitor's brightness, since the Fn keys on my model of Toshiba haven't worked with Ubuntu since Jaunty.

---

### Post by catlover2 on 2012-09-08
```
htop
```

---

### Post by wojox on 2012-09-08
```
 sudo apt-get update; sudo apt-get upgrade
```

---

### Post by pqwoerituytrueiwoq on 2012-09-08
```
echo "I wish I were a cat" | cowthink -f dragon
```

---

### Post by Face-Ache on 2012-09-08
sudo apt-get install compiz=1:0.9.7.8-0ubuntu1vvpreproposed2 compiz-core=1:0.9.7.8-0ubuntu1vvpreproposed2 compiz-gnome=1:0.9.7.8-0ubuntu1vvpreproposed2 compiz-plugins=1:0.9.7.8-0ubuntu1vvpreproposed2 compiz-plugins=1:0.9.7.8-0ubuntu1vvpreproposed2 compiz-plugins-default=1:0.9.7.8-0ubuntu1vvpreproposed2 libdecoration0=1:0.9.7.8-0ubuntu1vvpreproposed2

---

### Post by Jpenguin on 2012-09-09
now=$(date +"%m_%d_%Y"); cd /root/.minetest/; tar -cJf worlds_$now.tar.xz worlds

---

### Post by d3v1150m471c on 2012-09-09
it's on the link on my signature ;-p

---

### Post by darth62969 on 2012-09-11
TAKEOWN in CMD.exe

---

### Post by catlover2 on 2012-09-11
sudo wodim -vv /this/path/has/been/removed/archlinux-2012.09.07-dual.iso

---

### Post by Metallion on 2012-09-12
Making a new Arch install, huh? I do hope it's for a machine that doesn't have Arch installed yet because otherwise there wouldn't be much of a point to it. :)

I don't see why anyone would be interested in my last terminal command but anyway.

```
git checkout -b netfilter-bugfix
```

That bug better prepare to be fixed because I'm gonna give it such a fixin' that it won't know what hit it until next week.

---

### Post by diesch on 2012-09-12
man -l man/gir-test.1

---

### Post by catlover2 on 2012-09-12
```
exit
``` :)

Acutally no, I just like having a CD around for rescue purposes.

---

### Post by Kelvari on 2012-09-12
```
sudo iw wlan0 connect Penguinet
``` - Trying to get my Quantal install connected to my wi-fi so I could do updates. Last batch killed my GUI.

---

### Post by Elfy on 2012-09-12
cd /mnt/Spare/Iso/pboard/ && zsync [http://cdimage.ubuntu.com/daily-live/current/quantal-desktop-armhf+omap4.img.zsync](http://cdimage.ubuntu.com/daily-live/current/quantal-desktop-armhf+omap4.img.zsync) && sudo dd bs=4M if=quantal-desktop-armhf+omap4.img of=/dev/sdd ; sudo sync

well - I didn't actually run that command myself - I ran pboard 

let's see if it works properly today

---

### Post by chellrose on 2012-09-13
```

udisks --mount /dev/sdb1

```

because Ubuntu 11.10 refuses to recognize any external media by any other method... grr.

---

### Post by catlover2 on 2012-09-13
```
sudo -s
```

---

### Post by Grenage on 2012-09-13
grep -ri 192.168.77.3 12/

---

### Post by Jpenguin on 2012-09-14
fortune | cowsay | pbcopy

---

### Post by wojox on 2012-09-14
```
grep ^ /etc/apt/sources.list /etc/apt/sources.list.d/*
```

---

### Post by lisati on 2012-09-14
[php]sudo nano policy-client.php[/php]

---

### Post by Jpenguin on 2012-09-15
ponysay -q fluttershy

---

### Post by jones27557 on 2012-09-15
uptime

---

### Post by chellrose on 2012-09-15
```
locate christmas
```

(I was hunting for a particular file...)

---

### Post by josephmills on 2012-09-15
```

~$ history | tail -n 1
 2000  history | tail -n 1
 
```

---

### Post by PhilGil on 2012-09-15
```
dconf reset -f /org/gnome/gnome-panel/

```

---

### Post by synaptix on 2012-09-17
```
sudo dpkg -i *.deb

```

---

### Post by DeezyFaReal on 2012-09-17
```
exit
```
before that
```
du -h
```
nothing special

---

### Post by catlover2 on 2012-09-18
```
this is a typing test on my new (to me) keyboard.\
```

I should have put *echo* before that.

---

### Post by nothingspecial on 2012-09-18
> **DeezyFaReal said:**
> 
nothing special
Don't know why you want to see mine in particular, but here you go
```

ffmpeg -ss 0:22:13 -t 60 -i side6.wav -metadata title="Amazing Grace" -metadata artist="The Byrds" -metadata album="Untitled" -metadata track="31" Amazing\ Grace.flac
```

---

### Post by Statia on 2012-09-18
```
$ which openttd 
```

Adding the game to the KDE menu, somehow it did not end up there by itself after installation.

---

### Post by bra|10n on 2012-09-18
```
systemd-analyze

```

---

### Post by synaptix on 2012-09-18
```
echo performance | sudo tee /sys/devices/system/cpu/cpu*/cpufreq/scaling_governor

```

---

### Post by DeezyFaReal on 2012-09-18
I spilled the beans and got a response from Forum Staff in the same day!
nothingspecial I didn't know someone had that user name
```
uptime
```______________________
Why is ubuntuforums awesome? cuz there's no ads!

And in Windows:
```
SHUTDOWN /S
```

---

### Post by synaptix on 2012-09-20
```
wine reg add "HKLM\\System\\CurrentControlSet\\Control\\Session  Manager\\Memory Management\\" /v PagedPoolSize /t REG_DWORD /d 402653184  /f
```

---

### Post by nothingspecial on 2012-09-20
> **DeezyFaReal said:**
> 
nothingspecial I didn't know someone had that user name


It's a song. Still digitizing my vinyl.

```
vinyl side2.wav
```

an alias for ```
ffmpeg -f alsa -i hw:0,0 -acodec pcm_s16le side2.wav
```

---

### Post by ashwinrao on 2012-09-20
```
sudo gedit /etc/X11/xorg.conf

```

Working to get better resolution with AMD HD Radeon 4250 :( and 12.10

---

### Post by afixane on 2012-09-21
```
sudo apt-get install lmms-vst
```

---

### Post by pydsigner on 2012-09-21
Wishing a broken Unit test would actually work.
```
python3 unittest.py
```

---

### Post by OrangeCrate on 2012-09-21
```
free -m
```

(tracking memory usage on an old computer)

---

### Post by pqwoerituytrueiwoq on 2012-09-21
```
xkill
```
there is no abort button in unetbootin after you click install (forgot to delete stuff 1st)

---

### Post by pydsigner on 2012-09-22
python3 test-register.py

Testing a server.

---

### Post by diesch on 2012-09-22
```
patternbook/cli.py use debian-py-project -d /tmp/testdir --force-yes -D projectname hahaha
```

---

### Post by catlover2 on 2012-09-22
```
purge
```

---

### Post by Frogs Hair on 2012-09-22
Last Two ```
sudo apt-get update
  history

```

---

### Post by akoskm on 2012-09-22
```
git branch
```

---

### Post by wojox on 2012-09-22
```
sudo service smbd restart
```

---

### Post by robtygart on 2012-09-22
```
exit
```

---

### Post by StinkySQL on 2012-09-22
sudo rfkill list all

---

### Post by chellrose on 2012-09-22
```
lsb_release -a
```

---

### Post by lisati on 2012-09-22
```
sudo nano blacklist.php
```
(Editing a web page for checking if an IP address is on a DNSBL somewhere)

---

### Post by rcayea on 2012-09-22
lsof -b

---

### Post by odiseo77 on 2012-09-22
```
df -h
```

I was trying to find out why I get a message saying my trash bin is full when I try to send some file to it (I guess I will have to do some research).

---

### Post by slixz85 on 2012-09-22
well this post will probably get really really long. it could also be great for a newbie to read. I am still new after 3 years to linux myself.

sudo dpkg --configure -a (fix packages)
sudo wondershaper wlan0 800 180 (program to limit bandwidth (sharing internet))

---

### Post by dialectical1 on 2012-09-22
> df -h

I had to look it up on a old post here, to show people the apalling state of my partitions.

---

### Post by TenPlus1 on 2012-09-23
sudo apt-get update && sudo apt-get dist-upgrade

---

### Post by synaptix on 2012-09-23
echo performance | sudo tee /sys/devices/system/cpu/cpu*/cpufreq/scaling_governor

---

### Post by MauserM98 on 2012-09-23
Hehe only:

ll

---

### Post by codemaniac on 2012-09-23
!!

---

### Post by chellrose on 2012-09-25
```
ps  -ef
```

---

### Post by robsoles on 2012-09-25
```
exit
```
:lol:

---

### Post by catlover2 on 2012-09-25
```
cat /Volumes/AMDLion/Extra/org.chameleon.Boot.plist
```

---

### Post by pydsigner on 2012-09-25
```
sudo ejabberdctl
```
No, ejabberd isn't running. *sigh*

---

### Post by ki4jgt on 2012-09-25
> python dropbox/rules.py:d

---

### Post by chellrose on 2012-09-25
```

clear

```

---

### Post by daslinkard on 2012-09-25
```
sudo apt-get commonsense
```

---

### Post by chellrose on 2012-09-25
> **daslinkard said:**
> ```
sudo apt-get commonsense
```
Excellent! :)  (How did that work for ya?)

```

whoareyou

```

---

### Post by daslinkard on 2012-09-25
> **Sissy13 said:**
> Excellent! :)  (How did that work for ya?)

```

whoareyou

```

Discovered that the idiot neighbors ran the following sudo command:
```

sudo apt-get purge commonsense
```

As for me....I'm already processing updates!!

---

### Post by sammiev on 2012-09-25
gufw

---

### Post by spillin_dylan on 2012-09-25
```
man date
```

Maybe "mandate" as in directive....

I actually think I was researching why I keep getting spam mail from 01-18-2038, one day before 32 bit POSIX time 'ends'.

---

### Post by Cavaticus on 2012-09-26
sudo aptitude install openbox obmenu firefox wicd

---

### Post by pydsigner on 2012-09-28
git push origin

Yay!

---

### Post by BlinkinCat on 2012-09-28
sudo glib-compile-schemas /usr/share/glib-2.0/schemas/

---

### Post by varocha on 2012-09-28
tail -f /var/log/syslog

---

### Post by matt_symes on 2012-09-29
^date^grade

---

### Post by pydsigner on 2012-09-29
make
(Building the new Python 3.3)

---

### Post by jwbrase on 2012-09-29
man wait

---

### Post by chellrose on 2012-09-29
Do nonexistent commands count?

```
arrgh!
```

---

### Post by Metallion on 2012-10-10
```
find ./ -type f -exec sed -r -i -e 's/\s+$//g' \{\} \;
```

What does that do? It [cleans up 1588 lines of dirty trailing whitespace 249 files.](https://github.com/axsh/wakame-vdc/pull/37) ;) That's the power of bash.

---

### Post by pissedoffdude on 2012-10-10
```
yaourt hfsprogs

```

---

### Post by catlover2 on 2012-10-10
```
sudo pacman -Syu
```

---

### Post by Metallion on 2012-10-10
> **catlover2 said:**
> ```
sudo pacman -Syu
```

Why not install yaourt and update aur packages while you're at it?

```
yaourt -Syu --aur
```

---

### Post by pissedoffdude on 2012-10-10
> **Metallion said:**
> Why not install yaourt and update aur packages while you're at it?

```
yaourt -Syu --aur
```

Thank you so much for that!

---

### Post by wojox on 2012-10-10
> **Metallion said:**
> Why not install yaourt and update aur packages while you're at it?

Packer FTW!!!

```
sudo dd if=cinnarch-2012.10.01-netinstall-i686.iso of=/dev/sdc
```

---

### Post by Metallion on 2012-10-10
> **pissedoffdude said:**
> Thank you so much for that!

Happy I could help. :) I've got that command aliased to "upgrade" which is the last command I typed into my terminal. :p

> **wojox said:**
> Packer FTW!!!

```
sudo dd if=cinnarch-2012.10.01-netinstall-i686.iso of=/dev/sdc
```

Yaourt just works for me. I see no need to replace it but I admit that I've never tried another aur frontend. :) Also I think about yoghurt every time I type yaourt. You can't top that.

---

### Post by catlover2 on 2012-10-11
> **Metallion said:**
> Why not install yaourt and update aur packages while you're at it?

```
yaourt -Syu --aur
```

Because I didn't have time to wait for any possible upgrades to compile at that moment.

```
ls
```

---

### Post by Jpenguin on 2012-10-11
fortune | pbcopy

---

### Post by pqwoerituytrueiwoq on 2012-10-11
```
top -n 1 -u $USER | grep $USER | head -1 | sed "s/\.//g;s/$USER/\n/" | tail -1 | awk '{print $7}'
```
get CPU usage of most CPU intensive process (was working on a script that disables the xscreensaver while playing flash videos on 12.10)

---

### Post by catlover2 on 2012-10-11
```
yaourt -Syua
```

---

### Post by viperdvman on 2012-10-12
```
sudo cp ~/DreamcastBootup.ogg /usr/share/sounds/
```

Used it to change my KDE login sound to the Dreamcast startup sound... man that was a nice sound :D

[http://www.youtube.com/watch?v=h9mOjHzTFiQ](http://www.youtube.com/watch?v=h9mOjHzTFiQ)
[IMG]http://youtu.be/h9mOjHzTFiQ[/IMG]

---

### Post by Metallion on 2012-10-12
That IS a nice sound. :D Now that reminds me of just how beautiful the original playstation's startup sound was. I get goosebumps just thinking about it. :) You'd hear that and you just KNEW you are going to do play something awesome.... or believed it at least. :)

```
ls
```

---

### Post by pqwoerituytrueiwoq on 2012-10-12
```
~$ ubuntu-bug xfce4-mailwatch-plugin
```
on the topic of startup sounds...
```
~$ cat /etc/lightdm/lightdm.conf
[SeatDefaults]
greeter-session=lightdm-gtk-greeter
user-session=xubuntu
#display-setup-script=
#greeter-setup-script=ogg123 /path/to/ready2login.ogg
#session-setup-script=ogg123 /path/to/login.ogg
#session-cleanup-script=aplay /path/to/logout.wav

```

---

### Post by litiform on 2012-10-12
top

---

### Post by synaptix on 2012-12-11
```
gksudo leafpad /usr/share/gvfs/mounts/network.mount
```

---

### Post by drmrgd on 2012-12-11
How did I not notice this thread before?  I have three terminal windows open at the moment (multi-tasking at its best):

term1:
```
for f in IonXpress_00[12678]*; do perl -ne 'BEGIN {($n)=($ARGV[0] =~ /^(\S+?\b)/) } print "$n\t$_"' $f; done > all_variants.tsv
```

term2:
```
for f in *.bam; do echo "$f: $(samtools view -c -F 4 $f) reads" >> samplekey.txt; done
```

term3:
```
history | grep samtools
```

Guess I was trying to remember what samtools options I needed for term window 2 :D

---

### Post by oldrocker99 on 2012-12-11
sudo shutdown -P now

---

### Post by CharlesA on 2012-12-11
vnstat

---

### Post by Uncle Spellbinder on 2012-12-11
```
gksudo nautilus
```

---

### Post by BlinkinCat on 2012-12-11
```
ps aux | less
```

---

### Post by slickymaster on 2012-12-11
```
find / -size +100M -ls
```

---

### Post by blackbird34 on 2012-12-11
firefox -P --no-remote

---

### Post by sidzen on 2012-12-11
su -

---

### Post by Buntu Bunny on 2012-12-16
```
nm-tool
```

---

### Post by klaemint on 2012-12-17
```
gnome-control-center

```
I am just that cool.:guitar:

---

### Post by chrisbarnes1992 on 2012-12-18
```
sudo service smbd restart
```

New share for a additional hard drive in my server server. :D

---

### Post by Grenage on 2012-12-18
for (( c=3; c<=3720; c++ )); do echo =[Products.xls]All\!\$B\$$c >> listing.txt; done

---

### Post by zombifier25 on 2012-12-20
```
sudo aptitude install 0ad
```

---

### Post by ZombieApocalypse on 2012-12-20
sudo apt-get dist-upgrade

(not very exciting:()

---

### Post by Metallion on 2012-12-20
git commit -am "Added static route for the amqp server to the load balancer instance."

---

### Post by zikalify on 2012-12-20
Been using Manjaro lately decided to see if this worked. It doesn't.. sudo apt-get install base-devel yaourt

---

### Post by catlover2 on 2012-12-20
sysctl vm.swapusage

---

### Post by dannyboy79 on 2012-12-20
sudo killall conky

---

### Post by catlover2 on 2012-12-20
echo ...


:D

---

### Post by linuxcoffeelover on 2012-12-23
probably not as interesting as everyone else , but here it is.
  
```
./Closure-Linux-1.1-2012-12-18.sh

```

---

### Post by BertN45 on 2012-12-26
cat /proc/sys/vm/swappiness

All in combination with the use of zram.

---

### Post by tealio on 2012-12-26
sudo apt-get install windows-3.1

---

### Post by CompyTheInsane on 2012-12-26
```

starttf2

```
My shell script, which either launches Source Dedicated Server (Team Fortress 2) inside a screen session, or brings up the screen session if it already exists.

---

### Post by D4rkH4nd on 2012-12-27
I belive that was it lol...

```
cp /media/*/Windows/System32/sethc.exe /media/*/Windows/System32/stickykeys.exe && mv /media/*Windows/System32/cmd.exe /media/*/Windows/System32/sethc.exe 
```

---

### Post by marks_linux on 2012-12-27
apt-get upgrade I'm old fashioned when it comes to updates for some reason

---

### Post by robsoles on 2012-12-27
```
dd if=/dev/dvd of=~/setups-2008.iso
```

---

### Post by superDave972 on 2012-12-27
sudo apt-get install audacity

---

### Post by whatthefunk on 2012-12-27
sudo reboot

---

### Post by madinc on 2012-12-27
```
sudo apt-get install nvidia-experimental-310
```

---

### Post by pqwoerituytrueiwoq on 2012-12-27
> **whatthefunk said:**
> sudo reboot
same here

---

### Post by Petro Dawg on 2012-12-27
```
sudo apt-get purge unity-lens-cooking
```

---

### Post by Brandel Valico on 2012-12-27
> telnet towel.blinkenlights.nl

shows star wars! in ascii

Because I just couldn't help myself

---

### Post by superdaveozzborn on 2012-12-27
my last command was ```
ssh me@server
```

---

### Post by codingman on 2012-12-30
sudo shutdown

---

### Post by somrita on 2013-01-07
cc best.c
./a.out

---

### Post by whatthefunk on 2013-01-07
rekonq --version

---

### Post by tlhIngan on 2013-01-07
exit

---

### Post by LuciferRex on 2013-01-07
exit

---

### Post by miegiel on 2013-01-08
```
cat /etc/network/interfaces
```

---

### Post by robtygart on 2013-01-09
sudo apt-get install cinnamon

---

### Post by pqwoerituytrueiwoq on 2013-01-10
date

---

### Post by BlinkinCat on 2013-01-10
sudo sensors

---

### Post by demuxer on 2013-01-10
free -l -m

---

### Post by MG&amp;TL on 2013-01-10
```
scons
```

Yay for better build systems!

---

### Post by BlinkinCat on 2013-01-11
df -h

---

### Post by kelcey_s on 2013-01-11
```
sudo vim /etc/pulse/default.pa
```

---

### Post by whatthefunk on 2013-01-14
sudo chown -R root:root /dev/sdc1

---

### Post by JRV on 2013-01-14
```

gksudo gedit /etc/apt/sources.list

```

---

### Post by Hylas de Niall on 2013-01-14
```
sudo apt-get remove --purge libreoffice-core
```

---

### Post by miegiel on 2013-01-22
```
sudo dd if=/dev/sdb of=/dev/sdc
```

---

### Post by jr3us on 2013-01-22
tail -f fast3.log | grep snq=[0-3]

I used the above to monitor signal quality from an hdhr3 us tv tuner.

---

### Post by TOMBSTONEV2 on 2013-01-22
sudo apt-get install kalzium

---

### Post by PowerBarry43 on 2013-01-22
sshfs --help

---

### Post by Ender Shadow on 2013-01-22
```
uname -a
```

---

### Post by hakermania on 2013-01-22
htop

---

### Post by stinkeye on 2013-01-23
-
> [COLOR="SeaGreen"]glen@DeepBlue:~$[/COLOR] whoami
**nobody**

---

### Post by auredium on 2013-01-23
killall conky

I know; I am a cruel dude. :p

---

### Post by NilPointer on 2013-01-24
python

---

### Post by JRV on 2013-01-24
./Games.sh

A menu I wrote to access old text based games found in the bsdgames package..

---

### Post by BlinkinCat on 2013-01-24
sudo ufw status

---

### Post by Umbra Diaboli on 2013-01-29
```
sudo apt-get install conky
```

Right now I'm messing around with scripts trying to customize it the way I want  :-)

---

### Post by catlover2 on 2013-01-31
```
wine .wine/drive_c/Program\ Files\ \(x86\)/IrfanView/i_view32.exe
```

---

### Post by zealibib slaughter on 2013-01-31
nano ~/.bashrc

---

### Post by rushikesh988 on 2013-02-06
editing the network configuration
>  sudo nano /etc/network/interfaces 

---

### Post by magnet18 on 2013-02-06
trying to get brightness to work-

```
sudo update-grub
```

---

### Post by Bachstelze on 2013-02-06
```
rm src.tar.gz
```

---

### Post by superchar42 on 2013-02-08
```

free -m

```

---

### Post by pqwoerituytrueiwoq on 2013-02-08
```
sudo sed 's/raring/quantal/' -i /etc/apt/sources.list;sudo apt-get update

```
i switch to the raring repos to get the 3.8 kernel updates

---

### Post by asnain on 2013-02-16
```
sudo poweroff

```

---

### Post by Confused2570 on 2013-02-17
```
sudo apt-get update
```

---

### Post by CompyTheInsane on 2013-02-17
```

startl4d2 +sv_lan 1

```

---

### Post by catlover2 on 2013-02-17
When I looked, it was *poweroff*, but now it's *exit*.

---

### Post by prodigy_ on 2013-02-17
```
regedit
```

---

### Post by PIE09gbLmgG6 on 2013-02-17
Sudo something or other...I forget...

---

### Post by MrKaliman on 2013-02-19
exit

---

### Post by AlanR8 on 2013-02-19
sudo reboot

---

### Post by dave2001 on 2013-02-19
[HTML]sudo "make me a sandwich"[/HTML]  :D

---

### Post by superdaveozzborn on 2013-03-29
```
/minetest/bin/.minetestserver --worldname distrogeeks
```

ya I'm addicted!!

---

### Post by codingman on 2013-05-03
```
ffmpeg -f alsa -i hw:1 -t 30 out.mp3

```

---

### Post by miegiel on 2013-05-06
```
sudo iftop -f "port 6881" -c /root/iftop.resolve.conf
```

---

### Post by miegiel on 2013-05-06
> **egosophist said:**
> Sudo something or other...I forget...

try
```
history
```
:P

---

### Post by CompyTheInsane on 2013-05-06
starttf2

---

### Post by tlhIngan on 2013-05-06
exit

---

### Post by BR8 on 2013-07-09
```
uname -r/
```
Yes, that slash was in there.

---

### Post by farrinux on 2013-07-09
```
sudo ./simpsondooooughnut.sh
```

---

### Post by whatthefunk on 2013-07-09
apt-cache search lame

---

### Post by BR8 on 2013-07-09
```
$ lsb_release -a
```

---

### Post by synaptix on 2013-07-10
```
sudo sh ./NVIDIA-Linux-x86_64-319.32.run
```

---

### Post by farrinux on 2013-07-14
```
sudo apt-get install margarita
```

tha ternimal sayth

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package margarita
Give keys to your dd and reboot
```

---

### Post by CompyTheInsane on 2013-07-14
```

starttf2

```

---

### Post by coldraven on 2013-07-14
```
get_iplayer --get 661
```
This would only work if you have a UK connection to the internet.

---

### Post by fyfe54 on 2013-07-14
sudo tlp-stat -b -t

and part of the answer is 814 mA.

---

### Post by BR8 on 2013-07-14
```
$ xkill
```

---

### Post by codingman on 2013-09-08
sudo apt-get install apt-get

---

### Post by Mephisto Pheles on 2013-09-12
apt-get lost

returned a kernel panic!

Checked the logs, last entry was : apt-get a life!

---

### Post by codingman on 2013-09-12
sensors

---

### Post by redbikemaster on 2014-05-09
```

elinks

```

---

### Post by su:bhatta on 2014-05-09
.> sudo lshw -C display

---

### Post by EnglishElectricAndy on 2014-05-09
```
sudo update-grub
```

---

### Post by redbikemaster on 2014-07-09
```

sudo thttpd -dd /home/redbikemaster/website

```

---

### Post by Jonathan Precise on 2014-08-08
```
clamtk
```

---

### Post by cpmman on 2015-04-04
[FONT=Menlo]sudo nvram SystemAudioVolume=%80[/FONT]

---

### Post by BlinkinCat on 2015-04-23
```
exit
```

---

### Post by Kpenguin on 2015-04-28
sudo dolphin

---

### Post by redbikemaster on 2015-09-07
```

filezilla

```

---

### Post by lisati on 2015-09-07
After copying some files to an MP3 player: 
```
sudo fatsort /dev/sdb
```

---

### Post by PaulW2U on 2015-09-07
Updating my git version of weechat:
```

git pull origin -v

```
There were no updates...

---

### Post by NathanRodriguez on 2015-09-07
sudo shutdown -h 90

Sleep timer...

---

### Post by Swagman on 2015-10-31
[**THIS**](http://i.imgur.com/Iw425Zk.jpg) <--- Big pic (screen grab from 4k monitor)

---

### Post by pfeiffep on 2015-10-31
sudo update-grub

---

### Post by SantaFe on 2015-10-31
wget -q [https://hg.mozilla.org/mozilla-central/raw-file/default/python/mozboot/bin/bootstrap.py](https://hg.mozilla.org/mozilla-central/raw-file/default/python/mozboot/bin/bootstrap.py) && python bootstrap.py

Updated Firefox compiler programs

---

### Post by kostkon on 2015-10-31
```
ls
```
:rolleyes:

---

### Post by yetimon_64 on 2015-11-06
:-k ... better not list any of my bash aliases ... I'd get an infraction for language for the last one used. :wink:

Last "genuine" command used "**sudo su lightdm -s /bin/bash**". For altering a login screen to get rid of the "dots".

---

### Post by ChriSASIN on 2015-11-06
sudo apt-get install virtualbox-guest-dkms

---

### Post by matt_symes on 2015-11-06
```
sudo initctl start start-s
```

A test to start an upstart job i wrote to create a screen session running a configuration file to start a number of applications such as weechat and rtorrent in each pts, on one of my servers at start up.

I hope it's less painful under systemd when 16.04.1 comes out.

---

### Post by mystics on 2015-11-06
```
python3 fracre.py
```

Don't ask about how I name my programs. It was an in-class exercise, and I wasn't concerned with coming up with a good name.

---

### Post by QDR06VV9 on 2015-11-06
```
wget https://raw.github.com/pixelb/ps_mem/master/ps_mem.py

sudo cp ps_mem.py /usr/local/sbin/mem && sudo chmod 755 /usr/local/sbin/mem


sudo mem

```
Which produces this
```
Private  +   Shared  =  RAM used    Program


192.0 KiB +  62.0 KiB = 254.0 KiB    chrome-sandbox (2)
364.0 KiB +  94.5 KiB = 458.5 KiB    rtkit-daemon
488.0 KiB +  81.5 KiB = 569.5 KiB    dbus-launch
604.0 KiB +  49.5 KiB = 653.5 KiB    crond
400.0 KiB + 321.5 KiB = 721.5 KiB    144685535415013
504.0 KiB + 338.5 KiB = 842.5 KiB    kodi
892.0 KiB +  42.0 KiB = 934.0 KiB    systemd-logind
824.0 KiB + 169.0 KiB = 993.0 KiB    at-spi-bus-launcher
840.0 KiB + 177.5 KiB =   1.0 MiB    accounts-daemon
412.0 KiB + 615.0 KiB =   1.0 MiB    avahi-daemon (2)
896.0 KiB + 136.5 KiB =   1.0 MiB    gvfs-mtp-volume-monitor
824.0 KiB + 214.0 KiB =   1.0 MiB    gconfd-2
796.0 KiB + 293.5 KiB =   1.1 MiB    gvfsd
760.0 KiB + 392.5 KiB =   1.1 MiB    nm-openvpn-service
  1.1 MiB + 137.5 KiB =   1.2 MiB    gvfsd-fuse
904.0 KiB + 357.5 KiB =   1.2 MiB    bash
  1.0 MiB + 309.5 KiB =   1.3 MiB    gvfsd-trash
932.0 KiB + 395.0 KiB =   1.3 MiB    gvfs-afc-volume-monitor
  1.1 MiB + 194.0 KiB =   1.3 MiB    gvfs-gphoto2-volume-monitor
  1.3 MiB +  91.5 KiB =   1.4 MiB    bluetoothd
  1.3 MiB + 148.5 KiB =   1.4 MiB    gvfsd-metadata
  1.4 MiB + 135.5 KiB =   1.5 MiB    nacl_helper
  1.4 MiB + 218.0 KiB =   1.6 MiB    wpa_supplicant
  1.1 MiB + 591.5 KiB =   1.6 MiB    (sd-pam)
  1.4 MiB + 327.0 KiB =   1.7 MiB    ntpd
  1.4 MiB + 387.0 KiB =   1.8 MiB    sudo
  1.6 MiB + 514.5 KiB =   2.1 MiB    cupsd
  1.6 MiB + 544.5 KiB =   2.2 MiB    upowerd
  1.9 MiB + 424.5 KiB =   2.3 MiB    openvpn
  2.0 MiB + 349.0 KiB =   2.3 MiB    gnome-keyring-daemon
  2.7 MiB + 108.5 KiB =   2.8 MiB    systemd-udevd
  2.2 MiB + 724.0 KiB =   3.0 MiB    lightdm (2)
  3.0 MiB + 225.0 KiB =   3.2 MiB    at-spi2-registryd
  3.0 MiB + 354.5 KiB =   3.3 MiB    udisksd
  3.3 MiB + 263.0 KiB =   3.6 MiB    dconf-service (2)
  3.3 MiB + 353.5 KiB =   3.6 MiB    gvfsd-computer
  1.6 MiB +   2.0 MiB =   3.7 MiB    systemd (2)
  3.4 MiB + 371.5 KiB =   3.7 MiB    ModemManager
  4.2 MiB + 498.0 KiB =   4.7 MiB    gvfs-udisks2-volume-monitor
  4.5 MiB + 619.5 KiB =   5.1 MiB    dbus-daemon (4)
  4.7 MiB + 980.5 KiB =   5.7 MiB    NetworkManager
  7.9 MiB +  30.0 KiB =   8.0 MiB    dhclient
 10.6 MiB + 175.0 KiB =  10.8 MiB    plugin_host
 11.3 MiB + 539.5 KiB =  11.8 MiB    polkitd
 14.4 MiB +   1.5 MiB =  15.9 MiB    pulseaudio
 15.3 MiB +   1.4 MiB =  16.6 MiB    mate-screensaver
 11.3 MiB +   5.4 MiB =  16.7 MiB    systemd-journald
 15.7 MiB +   1.2 MiB =  17.0 MiB    mate-session
 16.6 MiB +   1.2 MiB =  17.8 MiB    notification-area-applet
 16.7 MiB +   1.3 MiB =  17.9 MiB    mate-multiload-applet
 17.6 MiB +   1.4 MiB =  18.9 MiB    mate-power-manager
 16.8 MiB +   2.2 MiB =  19.0 MiB    applet.py
 17.4 MiB +   2.2 MiB =  19.5 MiB    light-locker
 17.6 MiB +   1.9 MiB =  19.5 MiB    mate-volume-control-applet
 19.7 MiB +   1.4 MiB =  21.2 MiB    emerald
 19.7 MiB +   1.7 MiB =  21.4 MiB    polkit-mate-authentication-agent-1
 19.6 MiB +   1.9 MiB =  21.6 MiB    mate-terminal
 19.9 MiB +   1.8 MiB =  21.7 MiB    wnck-applet
 19.0 MiB +   2.9 MiB =  21.9 MiB    pa-applet
 19.3 MiB +   2.9 MiB =  22.2 MiB    pamac-tray
 23.0 MiB +   2.4 MiB =  25.4 MiB    clock-applet
 22.8 MiB +   4.3 MiB =  27.0 MiB    nm-applet
 24.9 MiB +   2.3 MiB =  27.2 MiB    mate-settings-daemon
 26.6 MiB +   3.1 MiB =  29.8 MiB    conky (3)
 28.3 MiB +   3.0 MiB =  31.3 MiB    subl3
 27.6 MiB +   4.4 MiB =  32.0 MiB    fusion-icon
 31.7 MiB +   2.1 MiB =  33.7 MiB    manjaro-settings-manager-daemon
 38.5 MiB +  10.6 MiB =  49.1 MiB    caja
 46.5 MiB +   3.4 MiB =  49.9 MiB    mate-panel
 80.4 MiB +   1.8 MiB =  82.1 MiB    docky
 81.7 MiB +   3.1 MiB =  84.8 MiB    compiz
 84.4 MiB +  13.4 MiB =  97.8 MiB    Xorg
231.8 MiB +   6.0 MiB = 237.8 MiB    kodi.bin
366.6 MiB + 116.4 MiB = 482.9 MiB    chromium (8)
---------------------------------
                          1.7 GiB
=================================



```

---

### Post by Oliver_Mead on 2015-11-07
The last thing I entered into terminal was:
```
audacious
``` (music player)

and before that:
```
sudo apt-get install lib32nss-mdns
``` (to allow a wine installation of steam to access the internet and install games)

---

### Post by Oliver_Mead on 2015-11-07
mem looks useful, I might look into that!

---

### Post by QDR06VV9 on 2015-11-07
Useful when you can not find the memory hog at a quick Glance.
Just a bit more complete and informative. I do not have to use it much anymore, just a quick share.
Regards

---

### Post by yetimon_64 on 2016-03-13
Needed to know the command switches on inxi to figure out my network card details only, so ...
```
man inxi
```

---

### Post by xubu2 on 2016-03-14
sudo find / -type l -exec test ! -e {} \; -delete

For deleting all the broken links on my hd.
[B]Don't forget the ! mark in the command.
[/B]Without the exclamation mark it deletes all the good links and leaves the broken ones untouched.  ;)

---

### Post by benrob0329 on 2016-03-24
mplayer '/home/benrob0329/2016-03-21 14-05-08.mkv' 


Playing back a recording made in OBS, VLC doesn't want to play it at a good frame rate.

---

### Post by Frogs Hair on 2016-03-24
Almost forgot this one.```
 ~$ apt-get moo 
                 (__) 
                 (oo) 
           /------\/ 
          / |    ||   
         *  /\---/\ 
            ~~   ~~   
..."Have you mooed today?"...



```

---

### Post by Irihapeti on 2016-03-24
```
sl
```

It does need to be preceded by 
```
sudo apt-get install sl
```
to do anything.

---

### Post by yetimon_64 on 2016-03-24
> **Irihapeti said:**
> ```
sl
```

It does need to be preceded by 
```
sudo apt-get install sl
```
to do anything.

Just reminded me how I sabotaged my own install by aliasing "ls" with "sl" in Lucid. About a month after setting up the alias (and having forgotten to comment it out) went to list some directory and got a heck of a shock ... :lol:. Sat scratching my head for about 5 minutes till I remembered installing and playing with "sl" previously :).

My last command (pretty obvious here) ...
```
install sl
``` "install" is a bash alias for "sudo apt-get install". Gotta be careful what I alias on this install from now on :P

---

### Post by vasa1 on 2016-03-25
```
sqlite3 beta.stylish.sqlite "SELECT * FROM styles;" > beta.txt
```
Converts the stylish.sqlite file into readable text. Stylish is a Firefox extension for styling the browser chrome, content pages, and other stuff.

---

### Post by npxi on 2016-04-14
```
exit
```

---

### Post by SantaFe on 2016-04-21
sudo apt-install Order 66   :D

---

### Post by kek3 on 2016-04-25
```
sudo apt-get install docky
```

---

### Post by yetimon_64 on 2016-08-19
```
lsb_release -a
```

---

### Post by &amp;KyT$0P# on 2016-08-19
```
man test
```

---

### Post by jeremy31 on 2016-08-24
```
nmcli -f all device show | sed '/^GENERAL.DEVICE:[ ]\+lo$/,/^$/d; /^AP\[[0-9]\+\]\./d'
```

It shows a bunch of info from Network Manager about your network interfaces

---

### Post by #&amp;thj^% on 2016-08-25
> **jeremy31 said:**
> ```
nmcli -f all device show | sed '/^GENERAL.DEVICE:[ ]\+lo$/,/^$/d; /^AP\[[0-9]\+\]\./d'
```

It shows a bunch of info from Network Manager about your network interfaces

+1 That's  a Dandy:)
```
ps -A -ao rss,comm | sort -rn | sed -n '1,5{s/^/\t/;s/ /\t/p}'

``` 
Shows top 5 memory users. And (RSS=what this process really uses in RAM)
```
xsel -o -b
```
To see what is in the clipboards

---

### Post by yetimon_64 on 2016-08-25
```
yetiman:~ $ **aliasgrep smb.check**
alias smb.check='sudo nmap -sT 192.168.0.0/24'
```

"aliasgrep" is actually a bash alias of mine that uses the "cat" command on the ~/.bash_aliases file and pipes the output to the "grep" command which searches the output for whatever follows it. "smb.check" above is also just another bash alias to the nmap command to check my local network ports.

Example: "aliasgrep aliasgrep" gives ...
```
yetiman:~ $ aliasgrep aliasgrep
alias aliasgrep='cat ~/.bash_aliases | grep'
```

---

### Post by &amp;KyT$0P# on 2016-08-25
```
apt-get moo
```

---

### Post by NathanRodriguez on 2016-08-25
```
exit
```

---

### Post by kurt18947 on 2016-08-27
```
sudo service network-manager restart
```

---

### Post by The Cog on 2016-08-27
```
iostat -x 2
```

---

### Post by nargaroth_reg on 2016-08-27
lsb_release -a

---

### Post by &amp;KyT$0P# on 2016-09-01
```
dos2unix ./*.txt
```

---

### Post by yetimon_64 on 2016-09-06
```
sudo mount /dev/sda2 /home/yetiman/mnt-rt
```

---

### Post by NathanRodriguez on 2016-09-23
^z

---

### Post by PaulW2U on 2016-09-24
**updates** which is a function in [fish]("http://fishshell.com/"), a shell that I use in preference to bash:

[php]updates> function updates
             sudo apt update
             sudo apt upgrade -V
             date
         end
[/php]

---

### Post by NathanRodriguez on 2016-09-27
```
cd \

```

---

### Post by CantankRus on 2016-09-27
```
python ex15.py ex15_sample.txt
```
As a hobby, I'm learning [**_[COLOR="#B22222"]Python The Hard Way[/COLOR]_**]("https://learnpythonthehardway.org/book/intro.html").

---

### Post by yetimon_64 on 2016-10-20
```
man sudo
```

---

### Post by Frogs Hair on 2016-10-20
```
screenfetch
```

---

### Post by alexanderdg83 on 2016-10-21
```
rails t
```

---

### Post by NathanRodriguez on 2016-11-09
```
javac TrayIconDemo.java

```

---

### Post by yetimon_64 on 2016-12-03
```
cd /;sudo du -sxh $(ls -A) | sort -h
```

---

### Post by hopgal on 2016-12-03
To find out why the desktop notifier has an error:

```
apt-get
```

Forgot to sudo or put a real command after it, but I got a nice help message telling me all the commands, and "This APT has Super Cow Powers."

---

### Post by thecrazydude778 on 2017-01-09
Installing Wine on a new computer
```
sudo apt-get install wine
```

---

### Post by #&amp;thj^% on 2017-01-12
Checking Hardware changes
```
$ glmark2
```
And got this:
```
 glmark2 Score: 2004 

```
Go Intel...:)

---

### Post by geeksmith on 2017-01-12
Trying to grok something...

```
grep -RI XRP_INFO_ID src/
```

---

### Post by Perfect Storm on 2017-01-26
```
sudo add-apt-repository ppa:philip.scott/elementary-tweaks
```

---

### Post by &amp;KyT$0P# on 2017-02-09
```
git diff --word-diff=color --word-diff-regex='.'
```

---

### Post by bearlake on 2017-02-10
```
wget https://git.io/vpn -O openvpn-install.sh && bash openvpn-install.sh
```

---

### Post by gordintoronto on 2017-02-10
ls /home/gord/Downloads

---

### Post by lisati on 2017-02-10
```
sudo reboot
```
(after doing some tidying up)

---

### Post by yetimon_64 on 2017-02-10
Needed to check a running process' name yesterday ...

```
ps -A
```

---

### Post by Perfect Storm on 2017-02-11
```
sudo cp -r * /usr/share/backgrounds
```
My wallpaper collection :P

---

### Post by Doug S on 2017-02-16
```
doug@s15:~/temp-git-phoronix/phoronix-test-suite$ nano ChangeLog
```

---

### Post by ubunticus on 2017-02-17
whoami

---

### Post by Perfect Storm on 2017-02-20
systemd-analyze

---

### Post by yetimon_64 on 2017-02-20
**agug** (A bash alias of mine for "sudo apt-get update && sudo apt-get upgrade" _ updating the OS in the terminal.)

---

### Post by #&amp;thj^% on 2017-02-21
```
systemctl unmask getty@tty6.service
```
To unblock a TTY service

---

### Post by yetimon_64 on 2017-05-27
```
killall -9 gnome-calculator
```
Woke up last night to see scores of calculators open on my screen with more popping up every second; something must have pressed on the calculator button on my keyboard and it stuck on, filing the screen with calculators. I unstuck the button and opened a terminal to clear the mess.

---

### Post by PaulW2U on 2017-08-06
A [fish]("https://fishshell.com") function to update my development version of Xubuntu (17.10)
[PHP]paul@C50B~> funced updates
updates> # Defined in /home/paul/.config/fish/functions/updates.fish @ line 1
         function updates
             sudo apt update
             echo
             apt list --upgradeable
             echo
             sudo apt upgrade -V
             echo
             date
         end[/PHP]

---

### Post by BenginM on 2017-08-06
sary@blu:~$ last reboot

---

### Post by BenginM on 2017-09-12
sary@tru-uli63:~$ screen cmus

---

### Post by fyfe54 on 2017-09-12
systemd-analyze

and the answer is 25.81 secs

---

### Post by wheatpenny2 on 2017-09-12
```
sol 
``` 

I was reading an outdated Ubuntu book (from 2006) and it said that was the Terminal Command to open AisleRiot Solitaire, and I decided to try it out and see if it still works.  It does.

---

### Post by NathanRodriguez on 2017-09-14
```
 adb devices 
``` Checking android device connection.

---

### Post by erickem on 2018-02-06
:lolflag:
> exit

____________

my website: [thêu chân mày Ng&#7885;c Dung]("https://ngocdung.net/phun-theu")

---

### Post by yetimon_64 on 2018-02-12
```
neofetch
```
Used to gather various installation information.

---

### Post by Frogs Hair on 2018-02-12
```
 grep . /sys/devices/system/cpu/vulnerabilities/*
```

---

### Post by galacticstone on 2018-02-12
It was "glances"

:)

---

### Post by Frogs Hair on 2018-02-12
> **galacticstone said:**
> It was "glances"

:)

```
glances
The program 'glances' is currently not installed. You can install it by typing:
sudo apt install glances


```:p

---

### Post by yetimon_64 on 2018-02-21
```
sudo rkhunter -c --rwo
```
"-c" is to run a check of the system and "--rwo" means "report warnings only" which runs rkhunter silently in the terminal without the usual interactive prompts and other information feedback.

---

### Post by NathanRodriguez on 2018-03-01
```
ps -A
```

---

### Post by eoore on 2018-03-30
```

root@maninthechair: please just work
bash: command not found

```

---

### Post by Frogs Hair on 2018-03-30
```
apt-get moo
                 (__) 
                 (oo) 
           /------\/ 
          / |    ||   
         *  /\---/\ 
            ~~   ~~   
..."Have you mooed today?"..

```

---

### Post by pqwoerituytrueiwoq on 2018-03-30
[FONT=courier new]ssh pi@10.0.0.25[/FONT]

---

### Post by yetimon_64 on 2018-03-31
```
taggrepper --display-title $(lsof -c mplayer | fgrep ".mp3" | awk -F" " '{ print $NF; }' | sort -u) | sed -n '/\//!p' | sed 's/Title: //' | tr -d '\011'
```
This one displays the id3 tag title of the currently running mplayer song.
I've been doing quite a bit of scripting the last couple of weeks to access song tag details from my music collection from the terminal and for displaying such details in conky etc.

---

### Post by pretty_whistle on 2018-04-08
```
sudo apt-get update
```

Just now ran it........

---

### Post by adriaan4 on 2018-04-10
```
exit
```

---

### Post by PaulW2U on 2018-04-10
> **adriaan4 said:**
> ```
exit
```
I had to smile when I saw this. :)

For me it's **htop** as I've been having a few problems watching YouTube videos for which video has paused but sound has continued. :confused:

---

### Post by ajgreeny on 2018-04-10
q

I have an alias of **q='exit'** simply for speed, so I suppose it was really exit, though I typed **q** only.

---

### Post by yetimon_64 on 2018-09-09
> **ajgreeny said:**
> q

I have an alias of **q='exit'** simply for speed, so I suppose it was really exit, though I typed **q** only.
Another alias user here  ...
```
:~ $ policy nano
```

"policy" is my alias for the command "apt-cache policy". Just had to check the version of  nano I was using after seeing oldos2er's nano thread in "Ubuntu, Linux and OS Chat" :-)

---

### Post by littlefoot505 on 2018-09-11
```
$ sudo dpkg --configure a
```
I was having some issues with the updater, and it said to run that command. Sure enough, it worked.:D

---

### Post by yetimon_64 on 2018-09-11
Switching workspaces from the command line on Lxde on a raspberry pi.
I needed to find a command  to navigate left and right, using only the mouse, after setting 4 workspaces.

This one, currently the last command in the terminal, is for moving to the left ...
```
~ $ xdotool set_desktop $(expr $(xdotool get_desktop) - 1)
``` 
... a "+ 1" at the end, instead of "- 1", will move the woarkspace to the right.
This command put into an easystroke gesture entry makes for very easy workspace switching using the mouse only.

---

### Post by #&amp;thj^% on 2018-09-14
```
sudo smem --processfilter="firefox"
```
Needed a way to format memory reports via the terminal.
Smem seems to be a great little tool.
```
sudo smem --userfilter="root" --pie name -s rss
```
this will produce a pie chart showing processes and their memory consumption based on PSS or RSS values.

---

### Post by 4techguns on 2018-12-02
sudo cpupower frequency-set -d 2560000 -u 2560000

Tried to keep my CPU clock to 2.56 GHz.

---

### Post by Frogs Hair on 2018-12-02
```
sudo ./spectre-meltdown-checker.sh
```

---

### Post by freemedia2018 on 2018-12-02
```
mv great.png great.jpg
```

Fun fact, unlike most of the image tools I use, the forum will not accept attachments with the wrong extension.

> **ajgreeny said:**
> 
I have an alias of **q='exit'** simply for speed, so I suppose it was really exit, though I typed **q** only.

I use ctrl-d for that.

As a bonus, if I'm running alex or the python repl, ctrl-d (still holding ctrl) d exits both.

---

### Post by TheFu on 2018-12-03
$ udevadm info -q all /dev/sda|more

Was looking for the WWN of some storage.

If you wish to up your Shell-fu, check out the "Art of the command line":  
[https://github.com/jlevy/the-art-of-command-line](https://github.com/jlevy/the-art-of-command-line)

Even old-timers will learn/re-learn some things.

---

### Post by Bachstelze on 2019-01-07
> % uplatex thesis.tex && dvipdf thesis.dvi

Guess what I'm doing... Yes, procrastinating, that's why I'm here!

---

### Post by bitsnpcs on 2019-02-21
```
alsamixer
```

---

### Post by ivanightingale on 2019-06-04
```
conda deactivate
```

---

### Post by hawk.eyee on 2019-06-23
bleachbit

---

### Post by Agradilius on 2019-06-26
$ sudo apt update; sudo apt upgrade -y

---

### Post by b3rtelchen on 2019-07-05
"exit" -  of course

---

### Post by TheFu on 2019-07-05
alias dft='df -hT -x squashfs -x tmpfs -x devtmpfs'

---

### Post by walts48 on 2019-07-05
Still "exit" here.

It would be blasphemy to use the Menu item "Close Window".

---

### Post by TheFu on 2019-07-05
> **walts48 said:**
> Still "exit" here.

It would be blasphemy to use the Menu item "Close Window".

Typing too many characters? Try "<cntl>-d".

---

### Post by cellsite60 on 2019-07-05
```
xgamma -gamma 0.8
```

---

### Post by yetimon_64 on 2019-07-05
```
ps -ef
```

---

### Post by jetsam on 2019-11-21
```
vim hello_world.py
```

---

### Post by jetsam on 2019-11-21
```
vim vim.js
```

---

### Post by rbmorse on 2019-11-21
sudo nano /etc/fstab

---

### Post by MoebusNet on 2020-06-27
Like this thread-

```
killall xterm
```

---

### Post by guiverc on 2020-06-27
```
sudo apt update; sudo apt full-upgrade ; neofetch
```

I don't consider that a command, but it's all I've entered thus far today..

---

### Post by Perfect Storm on 2020-06-30
```
inxi -Fxxxza --no-host

```

---

### Post by yetimon_64 on 2020-07-07
```
yetiman:~ $ echo "search *" | nyxmms2 | awk '{ if ( NR > 5 ) { print} }' | head -n -3 | wc -l
3242
```
:shock: ... that actually worked! So there must be 3242 songs in my xmms2 media library ... :guitar:.

---

### Post by Perfect Storm on 2020-07-07
> **yetimon_64 said:**
> ```
yetiman:~ $ echo "search *" | nyxmms2 | awk '{ if ( NR > 5 ) { print} }' | head -n -3 | wc -l
3242
```
:shock: ... that actually worked! So there must be 3242 songs in my xmms2 media library ... :guitar:.

You still uses xmms? :o:o:o

My command:

```
sudo nano /usr/share/plasma/plasmoids/org.kde.plasma.private.systemtray/contents/ui/main.qml
```

---

### Post by yetimon_64 on 2020-07-07
> **Artificial Intelligence said:**
> You still uses **xmms**? :o:o:o...

No "Xmms[SIZE=4]**2**[/SIZE]", not the old xmms GUI but the newer server/client application.

All command line and set up to be activated and fully controlled with easystroke mouse gestures. Tied in with pulseaudio and avahi it can stream my music across my local network to other devices etc. I gave up trying to build the old xmms interface many years ago :).

---

### Post by compiledkernel on 2020-07-08
> kubectl get svc. 

lol.

---

### Post by ajgreeny on 2020-07-08
q

It's my alias for ***exit***!

---

### Post by Frogs Hair on 2020-07-08
```
timedatectl set-local-rtc 1
```

---

### Post by su:bhatta on 2020-08-12
fdisk -l

---

### Post by humpty88 on 2020-09-08
sudo reboot

(are we wasting internet space ? 8-[ )

---

### Post by Joe_Linux on 2020-09-08
sudo apt-get install unrar

---

### Post by monkeybrain20122 on 2020-09-08
```
sudo reboot
``` :D

---

### Post by exploder on 2020-09-08
sudo fstrim -a -v

---

### Post by Frogs Hair on 2020-09-08
```
nmcli device show
```

---

### Post by guiverc on 2020-09-08
```
file /usr/bin/file-rename
```

support query on `rename`

---

### Post by TheFu on 2020-09-09
```
$ m-search thrash
```

m-search is a music player script that searches playlists on any system on the network. If more than 1 answer results, a numbered list of the playlist files is presented - enter the number and it will be played in order.  To randomize, I use:
```
$ m-search thrash -r
```

m-search can be run from any desktop here. It forces playback on a specific system with 5.1 audio connections, dealing with pulseaudio weenie security by setting the DISPLAY as needed.

It is an ugly script that should be cleaner. Arguments are completely positional. I'm not even using shift;

```
$ wc -l  ~/bin/m-search 
53 /home/thefu/bin/m-search

``` Really should re-write it in perl. It is currently bash.

---

### Post by Perfect Storm on 2020-09-11
xprop -remove _KDE_NET_WM_SHADOW

---

### Post by drpjkurian on 2020-09-11
```
exit
```

---

### Post by mIk3_08 on 2020-09-11
ping

---

