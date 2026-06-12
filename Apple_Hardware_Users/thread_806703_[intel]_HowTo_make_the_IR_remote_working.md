---
title: "[intel] HowTo make the IR remote working"
date: 2008-05-25
forum: Apple Hardware Users
---

### Post by buschi on 2008-05-25
Hello everybody!

Here are my experiences with the IR remote and a MacBook2,1. With Hardy, the IR didn't work at all although it said so on the MacBookPro HowTo page (it's not mentioned on the MacBook page, though). There may be severe errors in here, it's just what works for me:

```
sudo aptitude install lirc lirc-x
```

lirc is the package that "translates" the IR signal to some code like "PLAY", it comes with the program "irexec" which can execute other programs if some button is pressed. lirc-x provides the program "irxevent" which will make a "Page_Down" out of a button event.

During the install, i selected "macmini" as driver on the first screen that asked me and "none" on the second which was asking for the driver to send IR signals to other devices or something.

after reboot, ```
ps ax | grep "ir"
``` showed that lircd was running: ```
..... /usr/sbin/lircd --driver=macmini
```. however, the program ```
irw
``` which should show directly the events, was silent. therefore, i created a config file for lircd as it obviously didn't understand my remote using ```
irrecord
```. It is attached. I saved it in the directory ```
/usr/share/lirc/remotes/apple/
``` and adjusted the file ```
/etc/lircd.conf
```.

After reboot, ```
irw
``` showed the codes which i assigned to the buttons in the attached file (like PLAY, MENU, ...). the next thing is to associate these button press events with some action like Page_Up or starting a program or changing the volume. i didn't go much into that as i am interested only in this Page_Up thing in the moment. These associations are given in the ```
~/.lircrc
``` file. You can find a very sophisticated one in the MacBookPro HowTo; again, I attach mine.

if you call irxevent in the .lircrc, as i do, you have to have irxevent running: ```
irxevent -d
```. you can add this to the things to be started with the session, if you don't want to do it directly before using the remote.

that's it -- ir remote is working :)
hope that can help someone, i got most of it from [http://cweiske.de/tagebuch/Getting Apple Remote, Macbook and LIRC work together.htm]("http://cweiske.de/tagebuch/Getting Apple Remote, Macbook and LIRC work together.htm").

good luck,
sebastian.

---

### Post by cyberdork33 on 2008-05-28
Looks good.

---

### Post by stueng on 2008-05-29
Ok, I managed to get my remote working on iMac by adjusting the vendor device id in appleir.c from 0x8240 to 0x8242 and building the source (ubuntu-modules) and then modprobing appleir

After doing this the remote just worked, without requiring lirc

This was ok for changing volume (in any program) and skipping track in totem, xmms and rythmbox however it didnt work for VLC, mplayer and other applications

To try add further capability I installed lirc and used a lircrc that somebody else had created - now I have VLC and mplayer etc working

The problem I have now is that I am limited by the 6 buttons on the remote control. I would like to get MythTV setup which at least needs up/down left/righ volumeup/down next/prev enter menu escape and perhaps a few more - thats at least like 12 buttons

I have tried a few variations of the lircrc file which should allow the menu button to act as a mode switch so that the volumeup/down turn into up/down after the menu button is pressed and pressing the menu button again will switch mode back to normal

with this configuration however I find the system does all kinds of stuff when I press buttons on the remote, for example if I press the menu button in mplayer totem suddenly opens, in MythTV nothing at all happens

I am wondering if lirc is somehow conflicting with appleir and when I press a button on the remote perhaps two actions or more are taking place - I am not sure if I need appleir to use lirc? and I am not sure how to remove the built in ability to change volume/skip track that comes with Ubuntu before I had lirc

In addition to this I was wondering if I could use a different remote control (one with more buttons) with the apple built in IR receiver

Stu

---

### Post by cyberdork33 on 2008-05-29
> **stueng said:**
> In addition to this I was wondering if I could use a different remote control (one with more buttons) with the apple built in IR receiverI thought that was your intent in your other thread. The easiest way to find out is to try it...

---

### Post by stueng on 2008-05-29
Yes, that was my intent as outline in my other thread I was just re-itterating here - I tried point a few remotes at my IR receiver but I didnt see anything from irexec... although I am sceptical that irexec is the right place to look as other sites I have visisted (lirc sites) explain that to use irrecord I should be monitoring /dev/usb/something but I dont have a /dev/usb

I also to cat /dev/input/event4 but only saw output when I used the mac remote - nothing when I tried pointing other various remotes at it

I think I am going to have to buy a learning remote

---

### Post by zmjjmz on 2008-05-30
I'm not sure if this was accidental or if I misread the OP, but where's that config file for lircd?

---

### Post by cyberdork33 on 2008-05-31
> **zmjjmz said:**
> I'm not sure if this was accidental or if I misread the OP, but where's that config file for lircd?
Looks like he meant to attach it, but forgot. It is posted on the site he linked to though...

/etc/lircd.conf
```
begin remote

  name  lircd.conf.macbook
  bits            8
  eps            30
  aeps          100

  one             0     0
  zero            0     0
  pre_data_bits   24
  pre_data       0x87EEFD
  gap          211994
  toggle_bit_mask 0x87EEFD01

      begin codes
          Repeat                   0x01
          Menu                     0x03
          Play                     0x05
          Prev                     0x09
          Next                     0x06
          Up                       0x0A
          Down                     0x0C
      end codes

end remote
```

---

### Post by buschi on 2008-05-31
> **cyberdork33 said:**
> Looks like he meant to attach it, but forgot. ...


sorry for that... didn't realize that it didn't accept my files -- seems like they have to have a special ending. just remove the ".txt" part when saving!

best,
sebastian.

---

### Post by pravinbravi on 2008-07-13
First of all a big thank you to Ubuntu and the great ubuntu community. I have been able to install (on my new Santa Rosa apple MBP) and use linux exclusively only very recently. This has been my long cherished goal ever since my teens, and this has been only possible due to Ubuntu community.

Regarding the Apple IR A1156, there is a bug in the kernel - not a bug exactly - but the hardware codes in the kernel module are incorrect. There is a great howto somewhere in the ubuntu forums.

basically it involves changing the following in appleir.ko module file:

```
sudo ghex2 /lib/modules/`uname -r`/ubuntu/mactel/appleir.ko
```

[INDENT]if ghex2 is not installed do: ```
sudo apt-get install ghex2
```[/INDENT]

go to edit menu and click on replace, on the left pane (i.e. Hex side) do the following-

[INDENT]AC 05 40 82

eplace with

AC 05 **42** 82[/INDENT]

(look at the bold faced '42')

You will have to do the above every time the kernel is upgraded. So bad!

refer: [http://ubuntuforums.org/showthread.php?t=607797&page=3](http://ubuntuforums.org/showthread.php?t=607797&page=3)

And also make sure that your /etc/modules has this

```
sudo gedit /etc/modules
```

and put the following in it

```
# Apple modules need to be loaded in this order for the IR receiver to work
appleir
usbhid
applesmc
```

Before, I tried all other things but couldn't get the remote to work. But after I changed the codes in the kernel module, voila the remote works. But it still refuses to work with Elisa. This has nothing to do with the Apple hardware tho as Elisa lacks support for apple remotes, it supports only streamzap remotes - thats what Elisa says so.

Think its time this is taken care in the next kernel, other wise every time the kernel is upgraded the bytes have to be changed to get the remote to work.

Enjoy!

--
Pravin

---

### Post by cyberdork33 on 2008-07-15
> **pravinbravi said:**
> Think its time this is taken care in the next kernel, other wise every time the kernel is upgraded the bytes have to be changed to get the remote to work.
Well, someone will need to create a patch to support both IDs and submit it to the kernel source for it to get included in the kernel.

---

### Post by mandelcat on 2008-12-24
This post helped me.  I forgot to have irxevent -d running.  Thanks for the post, guys.

---

### Post by jis on 2009-04-09
I wonder if anybody else has suffered lircd taking lot of CPU power and not working after resume from suspend to RAM?

---

### Post by NoBugs! on 2009-06-20
Is it possible to use a normal tv-remote with this?
I thought any remote was supposed to work if configured first with irrecord, but it always gives the error:
```
irrecord -  application for recording IR-codes for usage with lirc

Copyright (C) 1998,1999 Christoph Bartelmus(lirc@bartelmus.de)

irrecord: could not get file information for /dev/lirc
irrecord: default_init(): No such file or directory
irrecord: could not init hardware (lircd running ? --> close it, check permissions)

```

---

