---
title: "live DVD demo and install won't work"
date: 2007-04-08
forum: Absolute Beginner Talk
---

### Post by apple pie maker on 2007-04-08
Summary: I bought a copy of "Moving to Ubuntu Linux" by Marcel Gagne and tried repeatedly to run the demo and install Ubuntu 6.06 LTS from the live DVD that came with the book - with no success.

Details: My machine is an HP desktop, less than a year old, with a 3.06 Gh Celeron processor and 526Mb of RAM. I installed a second hard drive of 300Gb for Linux alone. (Windows XP Service Pack 2 is on the first hard drive of 160 Gb.) Video card is ATI Radeon xPress 200 series.

I first tried to use Linux about 10 months ago using a CD that came with another book, "Red Hat Linux 7.3 for Dummies". It would proceed only in text mode, not in the graphical user interface mode promised in the book, and oddly enough, when it presented a list of places from which to load the OS, the list did not include the CD itself. I suspect that the drive had a defect that made it hide from the OS. Seven months later, after other problems with the drive, HP sent me a new drive - but that does not explain why only text and not gui was available on the CD. (I just now tried to load Red Hat from the CD using a CD player rather than the DVD drive, but it lists a pile of "can't find this or that" messages, including the one about resource region 3 that you'll see below a bit, and it still goes to text mode even when I select graphical at the first screen. I stopped at that point because I have little interest in loading an old version of Red Hat rather than a current version of Ubuntu.)

A few weeks ago I saw the Gagne book at the local library and thought that I had found a fast and easy way to start using Linux/Ubuntu. The DVD in that book was lightly scratched, so I bought a fresh copy to get a pristine DVD - then spent four hours in about 20 futile attempts to run the demo and install the OS from the DVD.

I started the machine with Windows, put the live DVD in the drive tray, restarted the machine, and set the BIOS to boot from the DVD. The Ubuntu boot menu screen appeared and I clicked on "Start or install Ubuntu". From here on, nothing ran as the book said it would.  A black screen appeared with the Ubuntu logo and a progress bar, and slowly these items appeared on the bottom of the screen: "Loading essential drivers...ok...mounting root file system...ok...moving pount points...ok...adding live cd user." After a long pause the screen switched to black with white text and showed these lines:

Uncompressing Linux...ok. Booting the kernel
[4294670.434000] mp-bios bug: 8254 timer not connected to io-apic
[4294670.593000] pci: can't allocate resource region 3 of device 0000:00:00.0

Another long pause and these lines were added:

[4294848.514000] hdc: ide_intr: huh? expected NULL handler on exit
[4294867.740000] buffer i/o error on device hdc logical block 333746

Later these messages appeared:

squashfs error: sb_bread failed reading block 0x75707
squashfs error: unable to read cache block
squashfs error: unable to read directory block

These messages continued to appear every 30-90 seconds for about 10 minutes, with variations in the numbers. I interpreted a screen and a half of error messages as a bad sign and decided to try again, only to find that nothing on the keyboard, nor the mouse, worked, except control-alt-delete, so I pressed those keys to start again. Further attempts to "Start and install" brought similar results, so I tried the next option on the Ubuntu boot menu, "Start Ubuntu in safe graphic mode" - and several tries there got the same results that I got with "Start and install".

Ever resourceful, I decided to try option three on the Ubuntu boot page, "Install in text mode". This route got me noticeably further. The system had me set up a user id and password, and select a time zone, a language and a keyboard layout, and it even partitioned the hard disk. All of this was done in dialogue boxes that appeared over a blue screen of dread that oscillated in a ghostlike fashion, as though the screen passes were starting alternately at pixels one and two. Eventually a box appeared with the label "Installing base system". This box had a progress bar that zoomed to "6%" and froze at "Retrieving locales". Repeated attempts gave the same results.

Next I tried option four on the Ubuntu boot page, "Install in OEM mode". Results were the same as in text mode except that when the machine froze at "6%" as described above, it was "Retrieving libtest-charwidth-perl..." After the usual long pause, it issued a warning:

Debootstrap warning
file:///cdrom/pool/main/libt/libtext-charwidth-perl/libtext/charwidth-perl_0.04-3_i386.deb was corrupt

The warning gave me the option to continue, so I tried it and this message appeared:

Warning: couldn't download pkg libtext

"Continue" was again an option. I chose it and waited. The progress bar stayed at 6% and this message appeared:

Retrieving libncurses5

("Curses"? - my thoughts exactly.)

At this point the machine froze. I decided to return to the boot option screen and try "Check cd for defects'" This option created some text across the top of the screen in a green reminiscent of early DOS: "Loading Linuz..." (Yes, Linux with a "z".) A grey box appeared labeled "Loading Linux kernel". but its progress bar stopped at 9%. After a long pause another box appeared on top of the previous one: "I/O error - error reading boot cd -  reboot". I rebooted; same result.

At some point in my many attempts to use this live DVD I did get some sort of home screen that offered to load five applications (Firefox, Thunderbird, the word processor, GIMP, and another that I don't recall, nor do I remember how I got to that screen.) This screen had lots of general information, three sample screens on the left, and when I clicked on the Ubuntu logo at the top, it took me to an internet page from which I could downloaad a copy of Ubuntu from a mirror (in a mere three hours). The desktop that M. Gagne promised was, however, nowhere to be found.

I spent three hours yesterday looking through posts in Absolute Beginners, but except for some remarks about ATI support, nothing really addressed my issues. The manuals describe how things operate when they operate properly, but understandably don't cover the zillions of errors and glitches that are possible. (If in fact the answer is somewhere and I missed it,I would humbly much appreciate direction to it.)

Yes, I did try the "noapic" trick as described inthe book, without success. I will try the more complicated version recommended by EDURM in the post  dated 6-5-06 - when I have more time.

At this point I suspect that I have a brand-new defective DVD, a BIOS that may be goofed up, a video card that may be uncooperative, and I'm still mystified by that "huh?" error message. I'd still like to give Ubuntu a spin (no pun intended, but we'll chuckle anyway), especially because I paid $25 for the book to get a - hahaha! - quick and easy way to test-drive and install Ubuntu without the potentially time-consuming problems of a download-and-burn. Please accept my thanks in advance for any help and suggestions.

P.S.: One item for the Windowsphobes: Yesterday I spent an hour or so composing and carefully typing this post directly to the forum page. When I clicked the submit button, I found that Windows - all of it, everything, except moving the pointer - had frozen -  even the control-alt-delete combo would not work!. All I could do was to turn the machine off, lose my work, and rewrite it today.

---

### Post by mac.ryan on 2007-04-08
Wow... a piece of literature! :)

First of all welcome onboard in the ubuntu community... (almost onboard, I should say...).

I don't have a definitive answer to your problems, but a bit of search with google and on the forums led me to shortlist the following three possibilities:
[LIST]
[*]A problem with your plugged USB devices (unplug them all and retry)
[*]A problem with your DVD
[*]A problem with your DVD drive[/LIST]Anyhow - unless you really need 6.06 version of ubuntu for some reasons, I would suggest that you burn the Edgy release (latest stable), as a forum staff members in one of the threads I skimmed was explicitly mentioning a "bug" in that version that might be the cause of this behaviour.

Interesting (and LONG) thread that seems related to your problem:
[http://ubuntuforums.org/showthread.php?t=186115](http://ubuntuforums.org/showthread.php?t=186115)

I am sorry you are struggling with ubuntu, but - believe me - once you get along with it, it's worth the effort!! :)

---

### Post by Kohbo on 2007-04-08
Sounds similar to my problem. The problem was a bad burn. Prob got a faulty dvd. Anyway, try d/l the desktop version and burning the image. When you get to the first menu select "Check cd" and if it says 0 checksums were faulty then u should be good to go. I did this and it installed fine.

---

