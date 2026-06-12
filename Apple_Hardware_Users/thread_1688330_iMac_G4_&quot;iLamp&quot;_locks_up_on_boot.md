---
title: "iMac G4 &quot;iLamp&quot; locks up on boot"
date: 2011-02-15
forum: Apple Hardware Users
---

### Post by henkim21 on 2011-02-15
Hi guys!

First time forum post.  I've dabbled with linux in the past but im getting my feet wet again.

I've got a friend's iMac G4, 700Mhz i believe, aka iLamp.  I couldn't install using the desktop version b/c of size restraints.  So I finally got the alternate version installed.

Now, at boot up, I get an option to choose b/w Linux and the CD.  If I wait a while, it continues to load from yaboot.  It will then continue again.  But before anything else happens, it will lock up.  All I see is a black screen.  Pressing the caps lock key will not toggle the LED light.

Now, when I get to the yaboot prompt, I can interrupt it and try to boot the partition with different parameters.  By the advice of other forum posts, I've tried typing "Linux 1", but the same thing happens (i dont get a command prompt, just a black screen).  I've also tried to boot from the alternate CD again and do a rescue and a rescue-powerpc.  No go.

I've also tried booting into a Live CD (i think it was 10.04 desktop version).  That booted into a black screen as well.  

The only thing I can think of is trying previous versions of ubuntu.

Can a good Samaritan help me troubleshoot this system? Anybody have some advice for me? Thanks in advance!

---

### Post by linuxopjemac on 2011-02-15
I would go for MintPPC!

---

### Post by henkim21 on 2011-02-15
Thanks for the reply!

I'm doing this install for a friend.  i dont know his opinion on Mint PPC and I think he specifically wants ubuntu on it.  I dont know the advantages of Mint PPC over ubuntu either.  Any reasons why Mint PPC can be an advantage over ubuntu on an iLamp?



Any other suggestions with getting past this black screen?

---

### Post by linuxopjemac on 2011-02-15
faster, less bugs

---

### Post by henkim21 on 2011-02-15
I talked to my friend.  Ubuntu is the preferred distro at this point.  He did mention that he would be fine with whatever version of ubuntu.  Any older version suggestions would be welcome. :p

getting through to actually booting past the black screen is my top priority though.  

Any ideas? Thanks!

I also would like to add that when i tried booting to the live 10.04 cd, I get a frozen orange screen instead. o.O

---

### Post by linuxopjemac on 2011-02-15
take the alternate installation CD, without GUI. You can add an xorg.conf file later.
[http://cdimage.ubuntu.com/ports/releases/lucid/release/ubuntu-10.04-alternate-powerpc.iso](http://cdimage.ubuntu.com/ports/releases/lucid/release/ubuntu-10.04-alternate-powerpc.iso)
[http://cdimage.ubuntu.com/ports/releases/lucid/release/](http://cdimage.ubuntu.com/ports/releases/lucid/release/)

---

### Post by henkim21 on 2011-02-15
Yup, the actual installation is done.  Right now, 10.10 is installed through the 10.10 alternate installation.  

should i try 10.04? once i install, how do i add the xorg.conf? i havent been able to access a command prompt yet. that was what i was trying to achieve when i used the "Linux 1" command in yaboot.

---

### Post by linuxopjemac on 2011-02-15
weird, you can't boot in a terminal with Linux 1 ? How about ssh-ing into that box ? Is ssh installed ?

---

### Post by linuxopjemac on 2011-02-15
and how about CTRL-Alt-F1 or so, to get into a tty ?
In Linux mint, I need to use fn-Ctrl-Alt-F1...

---

### Post by henkim21 on 2011-02-15
yeah, yaboot says:

boot:

Then I try to type in Linux 1.  It just boots into the black screen.




I have no idea how to ssh in.  Not sure if its installed, because i never got into ubuntu itself.

I did try ctrl-alt-f1 before. didnt work.  I dont think i have a fn key on my keyboard.

im going crazy here :[[[[[[

---

### Post by linuxopjemac on 2011-02-15
the fn key sits left of my CTRL key on my Dutch MacBook 2,1 keyboard...

---

### Post by henkim21 on 2011-02-15
thank very much for helping through this. 

but i think my keyboard doesnt have a fn key b/c its not a portable? its the imac so its a wired keyboard.  

heres a picture of my keyboard. [IMG]http://vectronicsappleworld.com/collection/articlepics/g4imac/snap26.jpg[/IMG]

---

### Post by linuxopjemac on 2011-02-15
can't you connect a keyboard which has these keys ?

---

### Post by henkim21 on 2011-02-15
I might be able to find one when i get home.  in the mean time, any other suggestions?

---

### Post by henkim21 on 2011-02-15
i hooked up a keyboard with Fn key. Didnt work.  I tried 10.04 alternate install. now it freezes on an orange screen. :-|

---

### Post by henkim21 on 2011-02-15
I kept trying alternate installs down.  9.10 worked.  the boot logo was 16 bit in color but booted up fine.  Doing a distro upgrade now.  Thanks.

Update: the iLamp seems to want to not show properly on a any ubuntu 10.xx and up.

---

### Post by linuxopjemac on 2011-02-16
is that really what you want ? Karmic Koala, will not be updated for a very long time anymore, if at all.

You might want to install Karmic Koala, add a working xorg.conf file from here:
[http://mac.linux.be/content/xorgconf-ilamp-g4-1-ghz](http://mac.linux.be/content/xorgconf-ilamp-g4-1-ghz)
and dist-upgrade to 10.10...

---

