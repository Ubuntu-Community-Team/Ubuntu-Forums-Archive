---
title: "iBook G4 from 2005"
date: 2012-07-07
forum: Apple Hardware Users
---

### Post by 2blue on 2012-07-07
I have an old iBook G4 marked "A1134 copyright 2005". It's one of those white ibooks, whith a 1.42GHz processors and only 512 RAM. It still runs fine with osx, but my main goal is to get an all lubuntu laptop setup.  

I keep reading some have managed to install lubuntu and different buntus on old ibooks, but I struggle a bit.

I have burned lubuntu 12.04 for power pc and I get as far as a lubuntu welcome, and "press TAB key for a list of ...", then the lubuntu logo "wait" screen, then it stops after a few error messages (not regognizing wireless drivers I think). The last message line on the screen is "stopping save udev log and update rules". 

Any experience, thoughts or ideas on how to go about this? 

Regards

---

### Post by gwjvan on 2012-07-07
When starting up from the live cd image, at the yaboot prompt where it says "boot: ", try typing:

live b43.blacklist=yes
[COLOR=Gray](Edit: It previously said Linux b43.blacklist=yes, here... I changed it to "live" to reflect it is for a live cd)[/COLOR]

There is a bug in 12.04 (and earlier versions) which sometimes causes kernel panic when trying to load the firmware for the b43 wireless card. You might be having this problem (it affects some people and not others). It should be fixed in 12.10

I got 12.04 to work on my PowerBook by installing from the alternate cd image, then  I manually removed and reinserted the wireless drivers... but, try to see if the above works first. If the above works, and you are able to install 12.04, you will have to type "Linux b43.blacklist=yes" the first time you boot from the hard drive-- then install the wireless firmware and restart to have functioning wireless.

---

### Post by 2blue on 2012-07-07
No, I didn't get any where. I got "Linux:2,/vmlinux: Unable to open file, Invalid device". Not sure what it means, I need to google a bit more.

---

### Post by gwjvan on 2012-07-07
Whoops,

For the live cd type:
live b43.blacklist=yes


then, after you install, when booting the first time type:
Linux b43.blacklist=yes 


I've updated my first post to reflect this

---

### Post by 2blue on 2012-07-07
Oh, the blue desktop appeared. Thanks !! 

I have yet to try it out and I don't dare say much yet. I can't make the wireless work right a way, but it seems promising. 

Thanks again ;- )

---

### Post by gwjvan on 2012-07-07
No problem-

You'll have to install with a wired connection, or without an internet connection. I don't think you'll be able to get the wireless working from a live cd session.

To get the wireless working after installing: You'll have to boot up (from the hard drive) without the wireless drivers again (the second command, above), then install the firmware. If you have a wired internet connection, you type this into a terminal:

sudo apt-get install firmware-b43-installer

Then reboot regularly.

---

### Post by gwjvan on 2012-07-07
Also, I have a PowerBook from 2005 that has a touchpad issue. I had to compile the driver myself. I think the problem also affects iBooks from 2005. If you find that the cursor is sluggish and moves in rectangular formations, here's a post to help with that:

[http://ubuntuforums.org/showthread.php?p=11973897#post11973897](http://ubuntuforums.org/showthread.php?p=11973897#post11973897)


Also, here is a page that has lots of answers to general PowerPC Ubuntu questions  (If you haven't already been to it):

[https://wiki.ubuntu.com/PowerPCFAQ/](https://wiki.ubuntu.com/PowerPCFAQ/)

---

### Post by 2blue on 2012-07-08
I braved an install, it boots and seem to run fine. I have yet to try with wired connection, so I am not fully there yet. There is also and odd issue with shut down, I have to use the power on/off button. 

Tanks again

---

### Post by 2blue on 2012-07-08
I can not make the  "Linux b43.blacklist=yes" stick, I have to give it on each boot. Is there a simple way to edit boot up somewhere?

---

### Post by gwjvan on 2012-07-08
Run the following command in a terminal:[INDENT] sudo gedit /etc/yaboot.conf
(or "sudo leafpad /etc/yaboot.conf" if you don't have gedit)
[/INDENT]Then add[INDENT]    b43.blacklist=yes
[/INDENT]to the list of arguments within the quotation marks on both of the append="..." entries near the end of the file. Depending on what was already there, your append sections should now look something like: append="quiet splash b43.blacklist=yes"

Save the file, then open a terminal and type:[INDENT] sudo ybin -v
[/INDENT]However, once you install the wireless firmware, you will need to set the yaboot.conf back to how it was, before (and run "sudo ybin -v" again)- or else the wireless will keep being disabled.

---

### Post by 2blue on 2012-07-12
Thanks for all the help gwjvan. 

I finally managed to get access to a modem, at a new internet cafe with very a very helpful girl. It turned out her father is all into  linux, at least she had a clue what it was all about. 

After updates the booting issue sorted its` self out and I installed lubuntu restricted packages with out any problem. The sudo command for wireless worked fine too. 

I have now a very quiet, acceptably fast laptop that boots and run all right. There are a few issues however, like Pidgin crashing as soon as you try to write something. I get as far as adding ric account, and it crashes. Any idea how to go about this?

Would it be helpul to keep posting issues in this thread, or should I make a new one for the Pigin issue?

---

### Post by gwjvan on 2012-07-12
I suppose it is up to you. I just installed pidgin to see if it would crash and I was able to join an IRC chat and didn't have that issue. I don't have any other experience with pidgin. You might want to use a different IRC client.

---

### Post by 2blue on 2012-07-12
I´ve used pidgin before and it's usually all fine, and it´s default in lubuntu. I added Chatzilla and it works fine. 

Another issue is sound; there is no sound on the system, neither playing CD (which mplayer seems to play fine other wise), no DVD (which mplayer doesn´t play at all), nor in youtube. The odd thing is there is no alsamixer in terminal, I suppose ppc lubuntu doesn´t use it?

I insalled restricted packages, which I thought would enable DVDs playing, and adobe flash player? I must confess I just accepted and marked off "OK" and pressed "TAB" a couple of times without reading much of the text.

Edit, I checked packages, and alsa-utils are there, but  when I write "alsamixer" in terminal I get "cannot open mixer, no such file or directory".

---

### Post by gwjvan on 2012-07-13
> **2blue said:**
> Another issue is sound; there is no sound on the system, neither playing CD (which mplayer seems to play fine other wise), no DVD (which mplayer doesn´t play at all), nor in youtube. The odd thing is there is no alsamixer in terminal, I suppose ppc lubuntu doesn´t use it?

Try this (from the PPC FAQ):

sudo rm /etc/modprobe.d/blacklist.local.conf

then restart

> I insalled restricted packages, which I thought would enable DVDs playing, and adobe flash player? I must confess I just accepted and marked off "OK" and pressed "TAB" a couple of times without reading much of the text.I haven't actually played DVD's on this computer, but the ppc faq has some info on that:
[https://wiki.ubuntu.com/PowerPCFAQ/#Video_codecs_and_DVD_playback](https://wiki.ubuntu.com/PowerPCFAQ/#Video_codecs_and_DVD_playback)

Looks like you have to install medibuntu from their site.
 
As for flash: There is no flash for PPC. There are some replacements like gnash and lightspark, but I hear they don't perform as well. For youtube videos, I use a firefox extension called FlashVideoReplacer (though sometimes the html5 video plays at the same time, so I set it to default to the standalone player so I can navigate away from the firefox page if I need to)

EDIT: Looks like you already found this and discussed it in another thread


> Edit, I checked packages, and alsa-utils are there, but  when I write "alsamixer" in terminal I get "cannot open mixer, no such file or directory".Looks like someone on another forum who had this problem reinstalled alsa-utils and then alsamixer worked for them.

---

### Post by 2blue on 2012-07-13
Alsa and sound works after the sudo you gave. I spent hours googeling and reading the ppc FAQ page getting now where, and it was all this simple blacklist command! 

And for the DVD, I have been down the rout of medibuntu and restricted extras on regular pcs, and they really should be in the two restricted packages listed in package manager. Still, I will try it out.

---

### Post by gwjvan on 2012-07-13
I just installed the medibuntu package and I can watch DVD's. I tried out a few dvd players. Xine seems to be the winner in my very quick tests.

Totem seems to choke. (It is the default on Ubuntu...)

VLC plays well, but the dvd menus don't work fully naturally

The Xine player (installed by the name xine-ui) plays well, and the menus/etc behave as you'd expect

---

### Post by 2blue on 2012-07-13
Thanks, I seem to have the medibuntu package all ready when trying to install from terminal, latest version and no updates yet. 

Java is not working, not sure why, there are no known issues appart from running a bit slow apparently.

---

### Post by 2blue on 2012-07-13
Update;

Thanks again for all your help. The part about  medibuntu finally sunk in (sorry I was a bit slow there) and the lib install suggested in FAQ made DVDs play fine, both Mplayer and VLC. Lubuntu doesn`t have Totem, and I`m not sure this ibook could handle it either (1.42GHz processor, 512MB RAM, not sure if it`s worth testing?) Totem is nice though. 

It turned out Java needed icedtea6 plugin, and it runs!!

Next issue is making the mplayer gecko setup stream TV. This has woked very nicely for me in 11 versions and regular pc, and it still looks like gnome mplayer and gecko plugin is default setup on 12.04. 

Is anyone familiar with ibook mousepad functions? There a no menu popping up when right clicking, there seem to be no regular right click functions at all.

---

### Post by hovrashko on 2012-07-13
I dont know how you managed to get it set up but apple hardware is always been a junk and will be. I was not able to setup my G4 with 2 GB of ram

---

### Post by 2blue on 2012-07-13
Probalby not the ram then, because I have only 512MB, I haven`t upgraded anything yet. I`m not even very good at this, I just ask for help and people have been very helpful with the issues I post, even though I probably explain stuff very cumbersomly. I just knew lubuntu could run on this G4 iBook, and did my best to handle whatever turned up along the way. It could run lion and some leopard versions, but I really wanted lubuntu. 


You might want to give it another try hovrashko. I have a feeling someone decided a long time ago linux should give the user a bit of frustration and resistance, and we are still under that spell ;- )

---

### Post by 2blue on 2012-07-13
I`m trying to make gnome mplayer work with the gecko setup for [this]("http://www.nrk.no/nett-tv/klipp/857021/") local TV channel. I`m not sure if there are restrictions outside Norway, but does anyone else with 12.04 powerpc build stream this site? It is usually recommended for windows mediaplayer or silverlight, which is configurated in some settings under "innstillinger". 

An alternative might be vlc and mozilla plug in, but I hesitate to install mozilla plugin, in the past it has been major hassle to get back to the mplayer gecko setup once did. 

Edit; initially I though all codecs and libs would be in the two restriced packages found in package manager, but I´m not so sure anymore. Would I need to add something like win32 or anything related in addition to the two restriced packages? It is windows mediaplayer oriented streaming, both live and from archive.

---

### Post by 2blue on 2012-07-16
I`ve reinstalled lubuntu from scratch, did updates and added the two restricted packages, rebooted twice but wireless is not activated? 

The only difference I noticed in the update process, is that update resisted a bit, and update manager did a "parital upgrade" in stead. Then I updated again after reboot, and installed the restricted packages. Any idea why it didn`t activate the wireless?

Edit; apparently the system just needed a few mintues to detect my wireless, suddenly it was there with out any more fuzz.

---

