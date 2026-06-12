---
title: "installed kubuntu with winxp on 1st partition, now nothing works"
date: 2007-09-21
forum: Absolute Beginner Talk
---

### Post by mendo on 2007-09-21
hello - first let me say hi and thank everyone for reading/helping.  i am absolutely new to ubuntu.

i installed kubuntu to the second partition on my hd - the first partition contains winxp pro.  i had to use the alternate cd - live cd wouldn't boot - it apeared to load, then no video. i tried to follow the hermanzone's alternate cd 7.04 dual boot guide and adapt it to my situation the best i could.  the kubuntu install seemed to be successful - cd ejected, rebooted, got error 'error loading operating system' or something.

i booted from winxp cd into repair console.  i couldn't even look at the directory on c:, it said 'an error occurred during directory enumeration'.  fixmbr didn't produce anything but c: prompt and fixboot produced 'fixboot cannot find the system drive, or the drive specified is not valid'.  i don't know much more to try and i don't know how to do anything with kubuntu - i don't even know any of the linux commands.  

i have perused posts that i could find pertaining to my issue.  it sucks if i have lost my windows os, but i was due for a clean install anyways.  i would like to have winxp and kubuntu on one disk, separate partitions.  i have many hard drives - 3, totalling 8 partitions.  other specs:

amd 64x2 3800+
asus a8v mobo
2gb ram
ati radeon x800 gto
wd 36gb raptor -winxp on 1st part, kubuntu on 2nd
maxtor 200gb sata hd
seagate 320 gb ide hd

i'm sure this post is woefully inadequate, but it should provide a starting point for anyone gracious enough to lend a helping hand.  i can elaborate later.  with the information provided, does anyone have an idea or link that i should try/read?

thanks a ton.

---

### Post by SpiritIsReality on 2007-09-21
howdy
I don't have a sata yet.
It looks like your rig's a real gamer.
until somebody shows up with the answers, you could try to find them here
[http://www.google.ca/search?hl=en&q=site%3Ausers.bigpond.net.au%2Fhermanzone+sata&btnG=Search&meta=](http://www.google.ca/search?hl=en&q=site%3Ausers.bigpond.net.au%2Fhermanzone+sata&btnG=Search&meta=)
once on a page, it helps me to click on the edit, at top of firefox, click on find in this page,
enter sata in box at bottom of window, hit next..next..

[http://www.google.com/custom?cx=002165917076592449621%3Ay8jmiivon3o&q=linux+install+grub+sata+ide&sa=Search&cof=AH%3Aleft%3BCX%3ALinux%2520search%2520Engine%3BDIV%3A%23cccccc%3BFORID%3A1%3BGFNT%3A%23666666%3BL%3Ahttp%3A%2F%2Fwww%2Egoogle%2Ecom%2Fcoop%2Fimages%2Fgoogle_custom_search_sm%2Egif%3BLH%3A55%3BLP%3A1%3B&adkw=AELymgVszXJ1vRg-A8SPrPwst2E-E_06F3tzDkVI41NsX5lBQlis9O3a2JxXLqgCN2jEGd1nfgp-VFjXnT37AghbOgkI6brqb5MUQ9wGjpohUP7yNCf32xSo4QlQcKqRd1uQXrAk2N4nPHgzVzIpmjDkeuGP55FVXrqH5t9Xi-xaFyf9_NaXx596cvMO_kbBz5XeDe__uBIwlbe501wDZOZ9zIX2kecQJA&client=pub-7825705102693166&channel=3833691868](http://www.google.com/custom?cx=002165917076592449621%3Ay8jmiivon3o&q=linux+install+grub+sata+ide&sa=Search&cof=AH%3Aleft%3BCX%3ALinux%2520search%2520Engine%3BDIV%3A%23cccccc%3BFORID%3A1%3BGFNT%3A%23666666%3BL%3Ahttp%3A%2F%2Fwww%2Egoogle%2Ecom%2Fcoop%2Fimages%2Fgoogle_custom_search_sm%2Egif%3BLH%3A55%3BLP%3A1%3B&adkw=AELymgVszXJ1vRg-A8SPrPwst2E-E_06F3tzDkVI41NsX5lBQlis9O3a2JxXLqgCN2jEGd1nfgp-VFjXnT37AghbOgkI6brqb5MUQ9wGjpohUP7yNCf32xSo4QlQcKqRd1uQXrAk2N4nPHgzVzIpmjDkeuGP55FVXrqH5t9Xi-xaFyf9_NaXx596cvMO_kbBz5XeDe__uBIwlbe501wDZOZ9zIX2kecQJA&client=pub-7825705102693166&channel=3833691868)
[http://www.google.com/coop/cse?cx=002165917076592449621%3Ay8jmiivon3o](http://www.google.com/coop/cse?cx=002165917076592449621%3Ay8jmiivon3o)
trails

---

### Post by hyper_ch on 2007-09-21
ah, the mix between sata and ide drives confuses grub sometimes...

Upon booting you can edit the grub entries that will be used to start. I think this is done with the "e" button (have a read on the screen).

then you will have a line something like:

```

hd(X,Y)

```

This actually means use drive number X and partition number Y as "root" (well, it's not quite that but you should get the idea).
So on my computer ide and sata drives together mix that up there. You will have to try different settings for the drive number.

Test them from 0 - 2 and leave the partition number as it is.

---

### Post by SpiritIsReality on 2007-09-21
hyper_ch ...thanks

---

### Post by mendo on 2007-09-22
thanks for the replies.  i have had no success.

hyper_ch - i tapped the 'e' button all through the boot process and had still got the 'error loading operating system' error.  nothing on the screen during boot tells me that i can hit anything to do something special.

fmat - thanks for the links, but those seem to deal with dual booting with windows and ubuntu on separate drives.  i have both os's on 1 drive, diferent partitions.  it is a sata drive though.

let me ask this:  would it create a problem for either os if i put the ubuntu swap on a separate physical drive, on the same partition as the windows page file?  i may have naively thought the two could coexist.

i also tried hitting the e button at a terminal - that didn't work.  i don't know how to do anything at the terminal.

i'm thinking my problem here is with grub.  would anyone agree?  that's the first thing i should see when i boot to choose which os to boot into.  i have seen posts re: editing grub, but i don't know how they got to it.  help?

i'm lost.  any help would be fantastic.  thanks.

---

### Post by SpiritIsReality on 2007-09-22
howdy
ya , when the bios starts, then hands it over to grub, then a screen is supposed to show
you an option of which os you want to highlight(select) and then hit enter to boot. That's 
where hyper_ch was talking about the e key. to edit grub.

if you're rig isn't getting to the grub screen...or it's passing it without showing it to you, 
 there's a file called /boot/grub/menu.lst where there's a line about hiddenmenu.

if you can't boot with the live cd, I'm not sure how we can edit files on your hard drive.
the alternate cd...I will have to check if it's got a recovery boot option and see what it's
like.

sorry you've got these problems, we all seem to get different ones somewhere. Seems our
hardware and software choices lead us down different learning experiences. It's all good.

sata pata(ide) mixed...I wonder if you could unplug your ide(pata) and see what happens then.
(kind of a shot in the dark) It might rule out one problem for us anyway.

swap...usually a swap partition on each drive that linux is accessing is a good idea as far as I
know.[edit](AAAA!!! WRONG!!)
[http://tldp.org/HOWTO/Partition/requirements.html](http://tldp.org/HOWTO/Partition/requirements.html)
 the windows page file is probably a ntfs format, and the swap file is ...well it's some
sort of solaris format...but that souldn't keep the grub page from showing up...and they 
should still boot, you'd think...even if they don't have a page/swap file..

ya your deduction about the grub being your trouble,..I think so too. What does your boot
up look like...what shows on your screen...I'm wondering if it doesn't show you the grub
screen, and tries to boot linux...or if it's not getting to the grub screen...?

well, have a look at this here... 
[http://ubuntuforums.org/showthread.php?t=500020](http://ubuntuforums.org/showthread.php?t=500020)
there's a lot there to help lose that lost whatever. a good map and a compass, the stars or the
sun...where the hell are we anyway..

what we need here is a solution...till somebody shows up with one,...we can seek...and see
what we find...i've heard something like that before...

being lost in the bush, or lost on the comp...it's a lot alike I think...it's not a very nice feeling...
if a guy can try to stay cool, take it one step at a time...survival drills..blah blah...the feeling
doesn't rule the day...but get's put in place....we'll be alright here as long as we don't panic
....HELLLLP!.......ok, I feel better now.

I'll get back to you about that alternate cd rescue thing...
hang in there
trails

---

### Post by Pumalite on 2007-09-22
Get a Knoppix Live CD: [http://www.knoppix.org/](http://www.knoppix.org/) and a rescuecd:
[http://www.sysresccd.org/Download](http://www.sysresccd.org/Download)
And explore your system.

---

### Post by SpiritIsReality on 2007-09-22
Pumalite ...thanks, I saw you recommend that in another thread too! doh!
ok the plan is set.

oh
mendo ...you can definately have multiboot os's on one drive...linux is going to love
being on your raptor, I would think.

---

### Post by mendo on 2007-09-22
thanks for the replies - now, riddle me this:

if i can boot from the alternate cd and get to a terminal via the 'rescue a system' option, do i still need the knoppix cd and the rescue cd?  i can get to a terminal, but i have no idea what to do from there.  i saw in one of the posts linked to earlier where somebody used gpedit to edit the menu.lst, but i don't think i have gpedit on my fresh system.  i would use edit, but this this isn't a windows machine and i literally don't even know how to look at a directory yet.

please and thank you.

-mendo

---

### Post by SpiritIsReality on 2007-09-22
howdy

I'm posting this using the knoppix live cd. 
by right clicking on the partition that linux is installed to, I got a gui
(graphics user interface) window  of the system files in konqueror.

[http://www.knoppix.org/](http://www.knoppix.org/)
click on flag of choice, en/us
click on download
click on http
accept

[ ] KNOPPIX_V5.1.0CD-2006-12-30-EN.iso 30-Dec-2006 23:28 698M
[ ] KNOPPIX_V5.1.0CD-2006-12-30-EN.iso.md5 30-Dec-2006 23:30 69
are the two files you want to save to disk. 
burn the iso
[edit]and we could use gedit ...oops, I mean kate text editor off the cd to edit the /boot/grub/menu.lst file
this knoppix (and the rescuecd) are good  disks to have around. IMHO
what do you think.

---

### Post by SpiritIsReality on 2007-09-22
heck
once you've got the knoppix live cd booted on your rig
we could take a tour to linuxcommand.org and he'll get
us started on the terminal. that's what I did, till he got onto
building a web page with scripts...I bailed...I'll get back to that
sometime.

[http://linuxcommand.org/](http://linuxcommand.org/)

having knoppix running on your rig is darn near kubuntu already,
except once you get kubuntu on your raptor,  that'll be fast.

---

### Post by Pumalite on 2007-09-22
Glad you liked it. What's great is that it mounts all partitions automatically, so you have immediate access to all the files in your system.

---

### Post by SpiritIsReality on 2007-09-22
Pumalite ...  ya,thanks
now, we can use knoppix
to get a grub prompt and do this installing grub natively?
[http://www.gnu.org/software/grub/manual/html_node/Installing-GRUB-natively.html#Installing-GRUB-natively](http://www.gnu.org/software/grub/manual/html_node/Installing-GRUB-natively.html#Installing-GRUB-natively)
and edit the /boot/grub/menu.lst file
remove # in front of hiddenmenu
check root for the linux partition....
...
waiting for knoppix to get up and runnin' at mendo ...
[edit] probably would be good to install grub anyway to drive it into mbr.
hopefully there's going to be a grub on the linux partition, but it probably needs
to be installed to mbr (hd0)

---

### Post by Pumalite on 2007-09-22
You can adapt this thread to Knoppix: [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by SpiritIsReality on 2007-09-22
Pumalite...thanks

---

### Post by Pumalite on 2007-09-22
You are welcome. Good luck.

---

### Post by mendo on 2007-09-22
you guys are the bomb.  i have been finishing up a bathroom remodel before she lets me play computer, but i must also watch my spartans take on the irish before any of that.  i will let you know what kind of success i had later tonight or tomorrow.  thanks a ton, guys.

btw - fmat - your tag line is great - time is a great teacher....  classic.

---

### Post by SpiritIsReality on 2007-09-22
catch you on the trail

---

### Post by mendo on 2007-09-22
oops - i mean pumalite.  i knew i wasn't dreaming that up.

---

### Post by Pumalite on 2007-09-22
Yeahh...Nobody gets out of here alive!

---

### Post by SpiritIsReality on 2007-09-23
what's up
(you can edit out the btw-who part or change it, I'll wipe this out..click on edit, right hand side)
does the knoppix run on your rig, if so, what's up with ubuntu live cd.
if knoppix doesn't run, we can try editing files and installing grub with the
alternate cd. (gulp) haha
I don't know how to fix the windows page file, searched support.microsoft.com a bit
can give you the links, but it's beyond me.
might need to run 
sudo dpkg-reconfigure xserver-xorg

screencast for 7.10 alternate cd
[http://screencasts.ubuntu.com/](http://screencasts.ubuntu.com/)

---

### Post by SpiritIsReality on 2007-09-23
what the hell, this is as good a place to keep track of them as any
for what it's worth...
[http://en.wikipedia.org/wiki/Virtual_memory](http://en.wikipedia.org/wiki/Virtual_memory)

the page file ?
[http://support.microsoft.com/kb/311724](http://support.microsoft.com/kb/311724)
[http://forums.techguy.org/windows-nt-2000-xp/582039-solved-repair-reinstall-reformat.html](http://forums.techguy.org/windows-nt-2000-xp/582039-solved-repair-reinstall-reformat.html)
[http://support.microsoft.com/kb/889654/en-us](http://support.microsoft.com/kb/889654/en-us)
[http://support.microsoft.com/kb/307886](http://support.microsoft.com/kb/307886)
[http://www.extremetech.com/article2/0,1697,1679900,00.asp](http://www.extremetech.com/article2/0,1697,1679900,00.asp)

swap partition
did you install the ia64 or i386
[https://help.ubuntu.com/7.04/installation-guide](https://help.ubuntu.com/7.04/installation-guide)
[http://tldp.org/HOWTO/Partition/requirements.html](http://tldp.org/HOWTO/Partition/requirements.html)
[http://ubuntuforums.org/showthread.php?t=282018](http://ubuntuforums.org/showthread.php?t=282018)
[http://ubuntuforums.org/showthread.php?t=363560](http://ubuntuforums.org/showthread.php?t=363560)

probably want to install grub to mbr (hd0)
/boot/grub/menu.lst ...comment out the hiddenmenu like so #hiddenmenu
/etc/fstab ...comment out the windows ntfs partition so it is not auto mounted ?
when boot, if stalls, press alt-F1 or ctrl-alt-F1 to see what it says on the screen

---

### Post by mendo on 2007-09-23
ok - here's the update:

i got grub running by booting off the knoppix cd, and entering commands i found in another post to get grub straight:

sudo grub
find /boot/grub/stage1

and putting that info into  this command:

root (hd0,1)
setup hd0
quit

that at least ran grub at boot, but then i got 'error 15, file not found' when i tried to run ubuntu, kernel 2.6.20-15-generic or ubuntu, kernel 2.6.20-15-generic (recovery).  the windows xp professional would go to a screen that says 'starting up' and do nothing else - i can work on that later.

so i reinstalled from the alt cd and put the root, swap and shared drive on one physical hd, partitions 2, 3, and 4, respectively - winxp on 1.

the install completed successfully and i rebooted.  i got grub, selected ubuntu, and lost any sort of signal to my monitor.  i assume this is due to the fact that i have an ati radeon x800gto.  i have found threads about installing this card, but my question is:  how can i do anything to install the card if i can't see anything on my monitor?

thanks for all of your help so far.  is there any more out there?

-mendo

---

### Post by mendo on 2007-09-23
woah - i just saw the last post from fmat - i didn't know that was there when i wrote my last reply.  i will digest that info now.  thanks.

---

### Post by Pumalite on 2007-09-23
For error 15:
[http://users.bigpond.net.au/hermanzone/p15.htm#15](http://users.bigpond.net.au/hermanzone/p15.htm#15)

'the install completed successfully and i rebooted. i got grub, selected ubuntu, and lost any sort of signal to my monitor. i assume this is due to the fact that i have an ati radeon x800gto. i have found threads about installing this card, but my question is: how can i do anything to install the card if i can't see anything on my monitor?'

If what you have is a failure of xserver:
Ctrl+Alt+F1 to get command line; at the command line:

sudo dpkg-reconfigure xserver-xorg, accept most defaults, choose 'vesa' as the driver, then: startx

---

### Post by mendo on 2007-09-23
ok - thanks - i don't get error 15 anymore.

where do i hit ctrl+alt+F1?  at grub?  after i select ubuntu from grub, i lose my monitor quickly.

thanks.

---

### Post by SpiritIsReality on 2007-09-23
ya, I'd never mind all that ramble of mine,
just when your rig seems not to be doing anything anymore, try to 
press and hold down the ctrl and alt keys, and press F2 or F3, and you should be able to log in.
type user name and passwd. hit enter
then
```
sudo dpkg-reconfigure xserver-xorg
```
and what Pumalite said. 
when it get's to the screen simple, medium, advanced, choice, it'd be good
to know your monitor's refresh rate from the manual or the manuf. web page.
google.com and enter your monitor's name and model could work.
tip: use the space bar to make a * in the resolutions you want, the arrow keys to scroll up and down,
the tab key to change to ok,...you'll catch on...
sorry about all the links. bad habit, haha!

then, after the dpkg-reconfigure xserver-xorg is done, you could
```
sudo shutdown -r now
``` to restart your rig

---

### Post by mendo on 2007-09-23
ok - i've gone through the xserver reconfiguration about 10 times.  i stuck with defaults except for the vesa driver and putting in the hor. and vert. refresh rates of my monitor.  i get the same result - after i select ubuntu from grub, the monitor loses any signal and i have nothing to look at.

at one point, i put in lspci from a command line and tried to figure out where my graphics card actually is plugged in.  i tried to put in what i found - something like 100.1, but that screwed up the boot, so at least i'm not getting any errors on boot, i'm just not getting any video.

now when i boot and select ubuntu, the screen goes blank and on the receiver for my wireless mouse/keyboard, the light to indicate caps lock is blinking.  that's all i know at this point.

any ideas?

---

### Post by Pumalite on 2007-09-23
Let the xserver 'detect' you monitor and go with the default.

---

### Post by mendo on 2007-09-23
wooo hooo - i got it!!

booted thru grub into recovery and entered this:

sudo apt-get install xorg-driver-fglrx
sudo aticonfig --initial

from this post:
[http://ubuntuforums.org/showthread.php?t=190133&highlight=install+with+ati+radeon+x800gto](http://ubuntuforums.org/showthread.php?t=190133&highlight=install+with+ati+radeon+x800gto)

phasmagon is the bomb!!

there was another line i was supposed to enter:

sudo aticonfig --overlay-type-Xv

but it wouldn't work, so i rebooted and i have a gui!!  sweet!

thanks to everyone for their help.  i'm sure i'll be back with more questions.

thanks!

---

### Post by SpiritIsReality on 2007-09-23
yeeeehaaaa.
good to hear you're in the saddle.

so there was an ati driver trick.. I've heard some of them are tough to get going
glad you figured out the home stretch.

I'm going back to the beginner's book I'm reading.
at vim and emacs ...kind of like a long haul uphill in bull gear, grind,grind...haha!

good roadmap here
[http://ubuntuforums.org/showthread.php?t=232059](http://ubuntuforums.org/showthread.php?t=232059)
sudo dpkg-reconfigure xserver-xorg
[http://users.bigpond.net.au/hermanzone/p7.html](http://users.bigpond.net.au/hermanzone/p7.html)
(I'll quit now)

trails

---

### Post by SpiritIsReality on 2007-09-24
howdy mendo
if you happen to see this, or I happen to bump into you again on the forum someplace.
you got the knoppix live cd to boot and run in gui?
too bad the kubuntu live cd didn't boot to gui (graphics user interface)
just think of all the fun we would have missed out on.
post here if you see this.

I've got 200 beans!? holy smoke! blabber blabber! haha!
trails

---

### Post by mendo on 2007-09-26
yes - the knoppix live cd would boot, the kubuntu live cd wouldn't.

i am continuing to have a problem with the graphics at boot issue.  i've been getting the loss of a video signal after i select ubuntu from grub.  i'll reboot in to recovery mode and enter into a terminal:

sudo apt-get install xorg-driver-fglrx

sudo aticonfig --initial

then i get video.  it's really weird b/c the first entry comes back with 'nothing downloaded, nothing done', so in subsequent attempts from the recovery console, i would only enter the second line of text, but that wouldn't get it done.  i would attempt to boot (startx) and immediately lose video.  i would have to boot again into the recovery mode, enter both lines of text in a terminal and boot - all will work, but i will probably have to do it all over again next time.

any ideas on this one?

thanks.

---

### Post by SpiritIsReality on 2007-09-26
howdy

we could try refining this search a bit (click on search within results at the bottom of the page)
[http://www.google.ca/search?as_q=&hl=en&num=10&btnG=Google+Search&as_epq=ati+radeon+x800&as_oq=&as_eq=&lr=&as_ft=i&as_filetype=&as_qdr=m6&as_occt=any&as_dt=i&as_sitesearch=ubuntuforums.org&as_rights=&safe=images](http://www.google.ca/search?as_q=&hl=en&num=10&btnG=Google+Search&as_epq=ati+radeon+x800&as_oq=&as_eq=&lr=&as_ft=i&as_filetype=&as_qdr=m6&as_occt=any&as_dt=i&as_sitesearch=ubuntuforums.org&as_rights=&safe=images)

and we could try clicking on the search, advanced search, keywords ati radeon x800
or ati radeon ....then click on  find posts from last 6 months.
could add keywords like fglrx ... 
 could narrow it down by
choosing search titles only, or search in tips and tutorials. 
some threads get marked [solved]. they're definately worth looking at. but there could be an
answer in the others too.
for the radeon fglrx
[http://www.google.ca/search?q=+%22ati+radeon+x800%22+fglrx++site:ubuntuforums.org&hl=en&as_qdr=m6&start=0&sa=N](http://www.google.ca/search?q=+%22ati+radeon+x800%22+fglrx++site:ubuntuforums.org&hl=en&as_qdr=m6&start=0&sa=N)
and the aticonfig
[http://www.google.ca/search?hl=en&q=+%22ati+radeon+x800%22+fglrx+aticonfig++site%3Aubuntuforums.org&as_qdr=m6&btnG=Search&meta=](http://www.google.ca/search?hl=en&q=+%22ati+radeon+x800%22+fglrx+aticonfig++site%3Aubuntuforums.org&as_qdr=m6&btnG=Search&meta=)

one day I hope to get to where I know one or two answers without the search stuff
but it sure is fun....did I say fun out loud...don't take it wrong, I like searching for solutions
to the problems on this networklll toooo. the biggest problem with this network here
is usually the guy that's typing this here. haha!

this is for the open source driver
[https://help.ubuntu.com/community/RestrictedDrivers/ATI](https://help.ubuntu.com/community/RestrictedDrivers/ATI)
[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

we could try searching /usr/share/doc for any fglrx files and see what gives.
or try man -k fglrx and see what it says, then man <that>

I'll get back to you with some of the ones I think might help.
edit : hard for me to know, since I don't have the graphics card to try it out.
suggestion : post your question to a forum. either beginner or installation or hardware?
there's a lot of helpful heavy hitters around these parts.
for the heck of it you could
have a look at this thread and see what you think. it's for a x1300
[http://ubuntuforums.org/showthread.php?t=560766](http://ubuntuforums.org/showthread.php?t=560766)
myth tv video card howto
[https://help.ubuntu.com/community/MythTV_Hardware_VideoCards](https://help.ubuntu.com/community/MythTV_Hardware_VideoCards)

trails

---

