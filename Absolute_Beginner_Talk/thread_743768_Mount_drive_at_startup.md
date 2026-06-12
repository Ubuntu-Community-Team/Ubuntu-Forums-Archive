---
title: "Mount drive at startup"
date: 2008-04-02
forum: Absolute Beginner Talk
---

### Post by tqprvn on 2008-04-02
Small annoyance which hopefully will have an easy fix.

I have 3 partitions on my laptop (Win, Ubuntu system partitions, plus a third shared partition where I keep my data).

I would like that data partition to mount on Ubuntu (7.10) startup rather than having to mount it manually/enter password etc.

Is that complicated for a n00b like me?

- M

---

### Post by Xiong Chiamiov on 2008-04-02
You'll need to add an entry in your fstab, located at /etc/fstab.  There's a brief overview of the file [here]("https://help.ubuntu.com/community/Fstab?highlight=%28fstab%29").  What command are you using to mount it, and I can help you with what you need to add to the fstab.

---

### Post by joshrobinson on 2008-04-02
> **tqprvn said:**
> Small annoyance which hopefully will have an easy fix.

I have 3 partitions on my laptop (Win, Ubuntu system partitions, plus a third shared partition where I keep my data).

I would like that data partition to mount on Ubuntu (7.10) startup rather than having to mount it manually/enter password etc.

Is that complicated for a n00b like me?

- M

it shouldnt be too complicated

could you please post what the drives are you want to mount, and what filesystem type they are?

ex

/dev/sda  and its fat32 etc.

---

### Post by tqprvn on 2008-04-02
allow me to demonstrate just how newbie I am...

What's an fstab?

To mount it now, I go to places, computer, double click on it.  It asks for a password and mounts.

---

### Post by tqprvn on 2008-04-02
> **joshrobinson said:**
> it shouldnt be too complicated

could you please post what the drives are you want to mount, and what filesystem type they are?

ex

/dev/sda  and its fat32 etc.

uh...ok, I will look in Properties :)

NTFS 3.1
mountpoint /media/DRIVEN (driven being the name of the drive)

What is /dev/sda?  Where do I find out?

---

### Post by Xiong Chiamiov on 2008-04-02
Your fstab is, well, a text file that tells the OS which drives/partitions to mount, and where.  There's a little more to it, but that's the meat of it.  Do you know if it's ext3, fat32, or something else?

Please list the results of both
```

ls /dev/hd*

```
and
```

ls /dev/sd*

```

---

### Post by joshrobinson on 2008-04-02
EDIT: Xiong Chiamov seems to be on top of things
no point in both of us posting to confuse things 
ill let you take care of this one :-D

---

### Post by tqprvn on 2008-04-02
> **Xiong Chiamiov said:**
> Your fstab is, well, a text file that tells the OS which drives/partitions to mount, and where.  There's a little more to it, but that's the meat of it.  Do you know if it's ext3, fat32, or something else?

Please list the results of both
```

ls /dev/hd*

```
and
```

ls /dev/sd*

```

I keep getting 'no such file or directory'

---

### Post by Xiong Chiamiov on 2008-04-02
> **joshrobinson said:**
> EDIT: Xiong Chiamov seems to be on top of things
no point in both of us posting to confuse things 
ill let you take care of this one :-D

I messed around with my fstab enough to understand the fundamentals pretty well, but I certainly am confused by tqprvn's last post.

> **tqprvn said:**
> I keep getting 'no such file or directory'

For both of them?  If so, try just ls /dev.

---

### Post by tqprvn on 2008-04-02
> **joshrobinson said:**
> EDIT: Xiong Chiamov seems to be on top of things
no point in both of us posting to confuse things 
ill let you take care of this one :-D
when in doubt, screen grab.

[[IMG]http://img86.imageshack.us/img86/7633/screenshotsystemmonitoryk6.png[/IMG]](http://imageshack.us)

---

### Post by tqprvn on 2008-04-03
> **Xiong Chiamiov said:**
> For both of them?  If so, try just ls /dev.
lotsa stuff:

matt@matt:~$ ls /dev
adsp       ptyc9  ptyr6  ptyw3  random      tty59  ttye4  ttysd  ttyxa
agpgart    ptyca  ptyr7  ptyw4  rtc         tty6   ttye5  ttyse  ttyxb
audio      ptycb  ptyr8  ptyw5  scd0        tty60  ttye6  ttysf  ttyxc
bus        ptycc  ptyr9  ptyw6  sda         tty61  ttye7  ttyt0  ttyxd
cdrom      ptycd  ptyra  ptyw7  sda1        tty62  ttye8  ttyt1  ttyxe
cdrw       ptyce  ptyrb  ptyw8  sda2        tty63  ttye9  ttyt2  ttyxf
console    ptycf  ptyrc  ptyw9  sda3        tty7   ttyea  ttyt3  ttyy0
core       ptyd0  ptyrd  ptywa  sda5        tty8   ttyeb  ttyt4  ttyy1
disk       ptyd1  ptyre  ptywb  sda6        tty9   ttyec  ttyt5  ttyy2
dri        ptyd2  ptyrf  ptywc  sequencer   ttya0  ttyed  ttyt6  ttyy3
dsp        ptyd3  ptys0  ptywd  sequencer2  ttya1  ttyee  ttyt7  ttyy4
dvd        ptyd4  ptys1  ptywe  sg0         ttya2  ttyef  ttyt8  ttyy5
dvdrw      ptyd5  ptys2  ptywf  sg1         ttya3  ttyp0  ttyt9  ttyy6
fd         ptyd6  ptys3  ptyx0  shm         ttya4  ttyp1  ttyta  ttyy7
full       ptyd7  ptys4  ptyx1  snapshot    ttya5  ttyp2  ttytb  ttyy8
fuse       ptyd8  ptys5  ptyx2  snd         ttya6  ttyp3  ttytc  ttyy9
hpet       ptyd9  ptys6  ptyx3  sndstat     ttya7  ttyp4  ttytd  ttyya
initctl    ptyda  ptys7  ptyx4  sr0         ttya8  ttyp5  ttyte  ttyyb
input      ptydb  ptys8  ptyx5  stderr      ttya9  ttyp6  ttytf  ttyyc
kmem       ptydc  ptys9  ptyx6  stdin       ttyaa  ttyp7  ttyu0  ttyyd
kmsg       ptydd  ptysa  ptyx7  stdout      ttyab  ttyp8  ttyu1  ttyye
log        ptyde  ptysb  ptyx8  tty         ttyac  ttyp9  ttyu2  ttyyf
loop0      ptydf  ptysc  ptyx9  tty0        ttyad  ttypa  ttyu3  ttyz0
MAKEDEV    ptye0  ptysd  ptyxa  tty1        ttyae  ttypb  ttyu4  ttyz1
mem        ptye1  ptyse  ptyxb  tty10       ttyaf  ttypc  ttyu5  ttyz2
mixer      ptye2  ptysf  ptyxc  tty11       ttyb0  ttypd  ttyu6  ttyz3
net        ptye3  ptyt0  ptyxd  tty12       ttyb1  ttype  ttyu7  ttyz4
null       ptye4  ptyt1  ptyxe  tty13       ttyb2  ttypf  ttyu8  ttyz5
nvidia0    ptye5  ptyt2  ptyxf  tty14       ttyb3  ttyq0  ttyu9  ttyz6
nvidiactl  ptye6  ptyt3  ptyy0  tty15       ttyb4  ttyq1  ttyua  ttyz7
oldmem     ptye7  ptyt4  ptyy1  tty16       ttyb5  ttyq2  ttyub  ttyz8
port       ptye8  ptyt5  ptyy2  tty17       ttyb6  ttyq3  ttyuc  ttyz9
ppp        ptye9  ptyt6  ptyy3  tty18       ttyb7  ttyq4  ttyud  ttyza
psaux      ptyea  ptyt7  ptyy4  tty19       ttyb8  ttyq5  ttyue  ttyzb
ptmx       ptyeb  ptyt8  ptyy5  tty2        ttyb9  ttyq6  ttyuf  ttyzc
pts        ptyec  ptyt9  ptyy6  tty20       ttyba  ttyq7  ttyv0  ttyzd
ptya0      ptyed  ptyta  ptyy7  tty21       ttybb  ttyq8  ttyv1  ttyze
ptya1      ptyee  ptytb  ptyy8  tty22       ttybc  ttyq9  ttyv2  ttyzf
ptya2      ptyef  ptytc  ptyy9  tty23       ttybd  ttyqa  ttyv3  urandom
ptya3      ptyp0  ptytd  ptyya  tty24       ttybe  ttyqb  ttyv4  usb1
ptya4      ptyp1  ptyte  ptyyb  tty25       ttybf  ttyqc  ttyv5  usb2
ptya5      ptyp2  ptytf  ptyyc  tty26       ttyc0  ttyqd  ttyv6  usb3
ptya6      ptyp3  ptyu0  ptyyd  tty27       ttyc1  ttyqe  ttyv7  usb4
ptya7      ptyp4  ptyu1  ptyye  tty28       ttyc2  ttyqf  ttyv8  usb5
ptya8      ptyp5  ptyu2  ptyyf  tty29       ttyc3  ttyr0  ttyv9  usbdev1.1_ep00
ptya9      ptyp6  ptyu3  ptyz0  tty3        ttyc4  ttyr1  ttyva  usbdev1.1_ep81
ptyaa      ptyp7  ptyu4  ptyz1  tty30       ttyc5  ttyr2  ttyvb  usbdev2.1_ep00
ptyab      ptyp8  ptyu5  ptyz2  tty31       ttyc6  ttyr3  ttyvc  usbdev2.1_ep81
ptyac      ptyp9  ptyu6  ptyz3  tty32       ttyc7  ttyr4  ttyvd  usbdev3.1_ep00
ptyad      ptypa  ptyu7  ptyz4  tty33       ttyc8  ttyr5  ttyve  usbdev3.1_ep81
ptyae      ptypb  ptyu8  ptyz5  tty34       ttyc9  ttyr6  ttyvf  usbdev4.1_ep00
ptyaf      ptypc  ptyu9  ptyz6  tty35       ttyca  ttyr7  ttyw0  usbdev4.1_ep81
ptyb0      ptypd  ptyua  ptyz7  tty36       ttycb  ttyr8  ttyw1  usbdev5.1_ep00
ptyb1      ptype  ptyub  ptyz8  tty37       ttycc  ttyr9  ttyw2  usbdev5.1_ep81
ptyb2      ptypf  ptyuc  ptyz9  tty38       ttycd  ttyra  ttyw3  vcs
ptyb3      ptyq0  ptyud  ptyza  tty39       ttyce  ttyrb  ttyw4  vcs1
ptyb4      ptyq1  ptyue  ptyzb  tty4        ttycf  ttyrc  ttyw5  vcs2
ptyb5      ptyq2  ptyuf  ptyzc  tty40       ttyd0  ttyrd  ttyw6  vcs3
ptyb6      ptyq3  ptyv0  ptyzd  tty41       ttyd1  ttyre  ttyw7  vcs4
ptyb7      ptyq4  ptyv1  ptyze  tty42       ttyd2  ttyrf  ttyw8  vcs5
ptyb8      ptyq5  ptyv2  ptyzf  tty43       ttyd3  ttys0  ttyw9  vcs6
ptyb9      ptyq6  ptyv3  ram0   tty44       ttyd4  ttyS0  ttywa  vcs7
ptyba      ptyq7  ptyv4  ram1   tty45       ttyd5  ttys1  ttywb  vcs8
ptybb      ptyq8  ptyv5  ram10  tty46       ttyd6  ttyS1  ttywc  vcsa
ptybc      ptyq9  ptyv6  ram11  tty47       ttyd7  ttys2  ttywd  vcsa1
ptybd      ptyqa  ptyv7  ram12  tty48       ttyd8  ttyS2  ttywe  vcsa2
ptybe      ptyqb  ptyv8  ram13  tty49       ttyd9  ttys3  ttywf  vcsa3
ptybf      ptyqc  ptyv9  ram14  tty5        ttyda  ttyS3  ttyx0  vcsa4
ptyc0      ptyqd  ptyva  ram15  tty50       ttydb  ttys4  ttyx1  vcsa5
ptyc1      ptyqe  ptyvb  ram2   tty51       ttydc  ttys5  ttyx2  vcsa6
ptyc2      ptyqf  ptyvc  ram3   tty52       ttydd  ttys6  ttyx3  vcsa7
ptyc3      ptyr0  ptyvd  ram4   tty53       ttyde  ttys7  ttyx4  vcsa8
ptyc4      ptyr1  ptyve  ram5   tty54       ttydf  ttys8  ttyx5  watchdog
ptyc5      ptyr2  ptyvf  ram6   tty55       ttye0  ttys9  ttyx6  xconsole
ptyc6      ptyr3  ptyw0  ram7   tty56       ttye1  ttysa  ttyx7  zero
ptyc7      ptyr4  ptyw1  ram8   tty57       ttye2  ttysb  ttyx8
ptyc8      ptyr5  ptyw2  ram9   tty58       ttye3  ttysc  ttyx9
matt@matt:~$

---

### Post by joshrobinson on 2008-04-03
> **tqprvn said:**
> when in doubt, screen grab.

[[IMG]http://img86.imageshack.us/img86/7633/screenshotsystemmonitoryk6.png[/IMG]](http://imageshack.us)

you lied about being a noob :)

---

### Post by tqprvn on 2008-04-03
> **joshrobinson said:**
> you lied about being a noob :)
no, I really didnt.  All I know how to do is take screenshots.  Anything in there vaguely resembling intelligence was done by the IT co that set up our office.

---

### Post by Xiong Chiamiov on 2008-04-03
Ah yes, that helps quite a bit.  I'm assuming that it's the DRIVEN one we're talking about (I think you mentioned it earlier)?

First, you'll need to open the fstab:
```
sudo gedit /etc/fstab
```

Then, at the bottom, add the line
```

/dev/sda5   /media/DRIVEN   fuseblk   defaults    0   1

```

---

### Post by tqprvn on 2008-04-03
*gulp*

now something has really gone awry!

Opened fstab

Pasted in that line.

Saved, closed.

Restarted machine, expecting to see 'driven' on my desktop.

Not there.

Go into places-computer to open it manually as I always do....and now it is not there either!

Looked in System Monitor - not there now.

Help!

---

### Post by joshrobinson on 2008-04-03
whats this command output

```
sudo mount -a
```

---

### Post by kaginken on 2008-04-03
WAIT!!  Hope you haven't started...

Before editing your fstab file, be sure to BACK IT UP!  :)

This is an easy

```
cp fstab fstab_backup_04022008
```

fstab is a very picky file.  if you so much as leave an extra white space in it, it can cause your machine to not boot.  If you have a backup of your last working copy, it's very easy to restore by simply booting into rescue mode and 

```
mv fstab_backup_04022008 fstab
```

reboot, and you're back up and running.

Hope this helps!

rock on  :guitar:

---

### Post by tqprvn on 2008-04-03
> **joshrobinson said:**
> whats this command output

```
sudo mount -a
```
mount: mount point /media/DRIVEN does not exist

---

### Post by Xiong Chiamiov on 2008-04-03
Very good point, and something I missed completely.

Do what Josh said, and also save the copy you have now as something else, remove the line I told you to add, save as plain old fstab, and reboot to see if we're back to where we started.

---

### Post by Xiong Chiamiov on 2008-04-03
> **tqprvn said:**
> mount: mount point /media/DRIVEN does not exist

Does the folder /media/DRIVEN exist?  It should, in order for you to have mounted there before, but...

---

### Post by joshrobinson on 2008-04-03
```
sudo mkdir /media/DRIVEN
```
then
```
sudo mount -a
```

should work

sometimes when ubuntu auto mounts something for you, it removes the directory when you unmount it

---

### Post by tqprvn on 2008-04-03
> **Xiong Chiamiov said:**
> remove the line I told you to add, save as plain old fstab, and reboot to see if we're back to where we started.
ok did that, and we are back to start point.

I may just file this under "too hard for me" and ask the IT guy to do it next time he is in the office.

Thanks anyway guys.

---

### Post by joshrobinson on 2008-04-03
in gedit with fstab open, go to save as, and put in fstab.bkup
then add the line back in that you had,
and do what i posted above, and you got it, it should work

---

### Post by Xiong Chiamiov on 2008-04-03
> **joshrobinson said:**
> in gedit with fstab open, go to save as, and put in fstab.bkup
then add the line back in that you had,
and do what i posted above, and you got it, it should work

Yes, what Josh posted most certainly should work.  I just lost my cool a little when I was reminded that we didn't have you backup the file (something you should always do when working with important stuff like this) and wanted to make sure that you had a working copy you could revert to if need be.

---

