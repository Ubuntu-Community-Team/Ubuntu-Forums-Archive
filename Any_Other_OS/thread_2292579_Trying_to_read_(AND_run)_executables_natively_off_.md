---
title: "Trying to read (AND run) executables natively off my flash drive under real DOS"
date: 2015-08-29
forum: Any Other OS
---

### Post by syntaxerror74 on 2015-08-29
For this old PC here next to me, there is a well-programmed beta bios which I'd like to give a whirl.
Note: **PC *cannot* boot via USB flash drive**. This is not supported.
I'm using Hiren's boot CD as a substitute.

- Put all necessary files on my flash drive
- Booted into Hiren's boot CD and selected DOS Tools option

To get USB to work under DOS, you will require TWO things: an ASPI manager and an USB driver. The latter **cannot** work without the former.
Alright, so I chose USBASPI1.SYS (the Panasonic one), which detected the drive and provided me a LUN (*Not *a driver letter yet!). Not until DI1000DD.SYS is loaded afterwards, you will have a drive letter at your disposition.

Most of the .SYS drivers provided on that CD will NOT work with EMM386 (memory manager) being active, so I turned this off. Plus, most are even allergic to HIMEM.SYS, suddenly pretending there is no flash drive connected. Surely, because it's just such great fun ripping out the drive and jamming it in again all the time...Arghhhh...

With lots of more tricks (skipped here), I managed to get 540K free even in low memory.

Still, I get the following:

```
S:> mem           (internal DOS command!!)

Program too big to fit in memory

Cannot load COMMAND, System halted
```

Mind you, I didn't even *run* the AWD flash tool yet because I wanted to test if *anything* will work! And obviously nothing would.
Can anyone else confirm these strange issues?

---

### Post by ajgreeny on 2015-08-29
I can't follow what you are trying to do (run Linux executables, or are they dos executables?) from a USB flash drive on a machine running an OS; but what OS?

If they are Linux executables on the flash drive that is formatted to fat32, as most are, you will not be able to do that.  For a file to be executable in Linux is has to have the correct Linux file-permissions and fat32 knows nothing about those.

Copy the file or files you have to the Linux HDD and try again and you may be lucky, though it will depend on exactly what you're trying to do.

---

### Post by CharlesA on 2015-08-29
Question - what program are you trying to run and why does it need to be run natively?

I would suggest running Dosbox instead. Way less hassle.
[http://www.dosbox.com/download.php?main=1](http://www.dosbox.com/download.php?main=1)

---

### Post by syntaxerror74 on 2015-08-29
> **CharlesA said:**
> why does it need to be run natively?
> **ajgreeny said:**
> I can't follow what you are trying to do (run Linux executables, or are they dos executables?) from a USB flash drive on a machine running an OS; but what OS?

[I]Initial problem #1: The floppy days are long gone. /me doesn't own a floppy no more.
Initial problem #2: This machine's BIOS does not support booting off a USB flash drive, so you have to think of other ways.
[/I]
Sorry for being a little confusing in my OP (It was late). I want to run the AWD bios flash tool *natively* off my flash drive (I do NOT trust WINE here), which needs real DOS, and won't run when Windows is running as well either. (Hence "Mini XP" from Hiren's CD won't do the trick here)

---

### Post by CharlesA on 2015-08-29
Freedos: [http://www.freedos.org/](http://www.freedos.org/)

Good luck.

---

### Post by Lars Noodén on 2015-08-29
One possible way is to boot FreeDOS from Grub and run it from that:

[http://ubuntuforums.org/showthread.php?t=2040710](http://ubuntuforums.org/showthread.php?t=2040710)

YMMV

---

### Post by syntaxerror74 on 2015-08-30
Thanks a lot Lars - this looks sooo promising! And congrats for having been able to "piece together" something like this just from scratch! 
Lars, by taking your post as a basis I found the right keywords to search for (my searches were fruitless before), and now look at that:

[https://wiki.archlinux.org/index.php/Flashing_BIOS_from_Linux](https://wiki.archlinux.org/index.php/Flashing_BIOS_from_Linux)

If there was a Nobel Prize for wikis, I know who the winner should be. Just what I needed ... anyway, read on...

[EDIT ] [B]Almost there! However, the wiki turned out to be WRONG here!!
[/B]As we haven't mounted / (the root drive) yet at this stage, you MUST OMIT the **/boot** from either line! (using GRUB2)

WIKI suggests:
```
menuentry "Flash BIOS" {
 linux16 /boot/memdisk
 initrd16 /boot/somedisk.img
 }
```

As this will take you back right into error hell, here are the **corrected lines** as follows:

```
menuentry "Flash BIOS" {
 linux16 /memdisk
 initrd16 /somedisk.img
 }
```

SUCCESS! 
There is your long-awaited **A:>** prompt - welcome to FreeDOS!

However, I am afraid I'll have to look for GENUINE MS-DOS instead! (using same technique as before)
My AWD flash tool joyfully felt like spitting out a flood of **Illegal opcode 03EE ...**+<lots of hex dump garbage>, likely to be caused by bad support of the internal AWD routines by FreeDOS.
I hope you are also aware that I would no longer be able to write here if this had happened *while* reflashing!!
PHEWWW. Well, I mean ... that was close. Really. :shock:

---

### Post by CharlesA on 2015-08-30
Next stupid question - why are you even bothering to try to update the BIOS in the first place?

---

### Post by syntaxerror74 on 2015-08-30
Haha, love the great amount of truth in your introductory sentence ("stupid question" :P) Couldn't have worded it better myself...really (hrr hrr)

But all sarcasm aside...yes there *is* a good reason to do so, as AMD-only boards are known to often have poor support for CPUs that followed some months later after the mainboard was first introduced on the market... For instance, a very old board may properly support the Athlon XP 2100+, but show lots of weird behavior once the CPU gets replaced by a 2500+. With a little luck, a BIOS update may (or may not) fix this. And yes, I *am* planning to get this ol' lady revamped a little by givin' her some more power underneath her old hood...

P.S. @all I'm really wondering why I have to explain this to anybody in this sub-forum...

---

### Post by CharlesA on 2015-08-30
Depends on the board and what the new BIOS actually does. If it isn't broke, don't fix it is a rule of thumb when dealing with BIOS updates.

It would probably help if you mentioned the model of the system board you are trying to run this flash utility on.

---

### Post by QIII on 2015-08-30
You may be having to answer questions because others need information in order to formulate a good answer.

Although you are quite aware of the details, others are not so good at reading minds or divining conditions that hold at a location and time remote from them.  Nobody is clairvoyant here.

---

### Post by syntaxerror74 on 2015-08-30
> **CharlesA said:**
> It would probably help if you mentioned the model of the system board you are trying to run this flash utility on. And receive great laughter in return, yeah?! :P Way too many freaks lurking around here who'd replace their hardware EVERY freakin' year. They'd normally be notorious for snickering about our old-time machines...   
Well, it's a Socket 462 one, if you insist to know so badly. But as the flash utility got shipped together WITH the .BIN file, there's a good chance it's a suitable one. ;) However, I concede it might have some compatibility issue anyhow. Besides, I don't think that either the chipset (e. g. NForce 2) or the actual model would have anything to do with my problem... Might take me another couple days until I can be bothered to cram my .bin and flash utility onto a *genuine* MS-DOS floppy image. However, I do see best chances that things will work out, since executables which work *flawlessly* on MS-DOS need not necessarily work equally on FreeDOS as well (e. g. lacking one unusual opcode --> KABOOM)

---

### Post by syntaxerror74 on 2015-09-21
[SIZE=4]SUCCESS!!![/SIZE]

Yay, I finally DID IT!

With great help of a great guy that saved my life many times even by the end of the 1990s...
[https://www.wimsbios.com/awardflasher.jsp](https://www.wimsbios.com/awardflasher.jsp)

THAT was the reason it did not work. The AWDFLASH tool (note: supplied by the mainboard manufacturer himself!) was **too recent** to work with a DOS image booted off grub. Presumably it used some strange opcode quirk that was not only worked around in an earlier version but also caused a major lack of backwards compatibility in the recent one.

Downloaded AWDFLASH v7.21 off Wim's great site and it worked as expected! Cleared CMOS and made all settings from scratch again.
(I booted into DR-DOS, not MSDOS yet, as I couldn't be arsed to find time to piece together such disk yet)
**At any rate, I owe you guys one for the great GRUB approach.** THANKS!
As a Linux person, I'm really wondering whether I should ever boot from a floppy image again using a USB pendrive, considering how comfortable this is if you know how to configure GRUB the correct way. You might even be tempted to make that a separate submenu in GRUB (similar to Ubuntu's *Advanced Options*), letting you boot into a couple different DOS flavors using a different image every time.

---

### Post by sudodus on 2015-09-21
> You might even be tempted to make that a separate submenu in GRUB (similar to Ubuntu's Advanced Options), letting you boot into a couple different DOS flavors using a different image every time. 

Yes, many of us do :-)

You can use **40_custom**.

***Plop*** is also a good alternative. It works from CD as well as from floppy and can help you chainload (and boot from USB, when it does not work directly).

See this link [Howto help USB boot drives](http://ubuntuforums.org/showthread.php?t=2196858)

---

### Post by syntaxerror74 on 2015-09-22
> **sudodus said:**
> 
You can use **40_custom**.
Surprise! :P 
I WAS already using 40_custom for the successful approach described above in all detail.

---

