---
title: "[SOLVED] Trouble Running Live CD"
date: 2007-10-27
forum: Absolute Beginner Talk
---

### Post by Ocarina654 on 2007-10-27
Hello.
Until yesterday Windows has always worked just well enough that, although I have been interested in Linux, I've never felt the need to switch.
That recently changed.  My computer crashed, and when Windows came back There was so much wrong with it I can't fix it (can't paste, can't drag and drop, can't edit the registry, can't enable/disable services, Windows doesn't recognize my sound card, etc, ad infinity).  It seems that the solution to every problem I have seems to be kept from working from another problem.  The solution to that problem is blocked by another problem, and this terrible chain continues for what seems to be forever.  Even System Restore wouldn't run, so I am literally stuck with no way to address the issue.
So finally, I have come to the conclusion that its time to shake off the chains of oppression and join the ranks of Linux users.
I've always been fond of the Ubuntu philosophy, and I even have some 7.04 CDs, so the choice of which Distro was obvious.

However, I'm having trouble trying to get Ubuntu to do anything.
I plan on running Ubuntu live from the CD in order to backup important/personal files, then wipe the drive and start over from Linux.

Except I can't do that.  I have my BIOS boot from the CD and I get the Ubuntu, and choose "Start or Install Ubuntu".  It seems to be working fine for a few seconds but then it just seems to stop.

I get to the screen with "BusyBox v1.1.3".  There is a blank line after this header, then the lines appear and nothing happens
"/bin/sh: can't access tty; job control turned off" and
"(initramfs) [     42.543308] ata3.00: failed to set xfermode (err_mask=0x4)"

This problem also occours when I try to "Check Disc for Errors".  I would hope that the disc doesn't have errors, because I got the disc from Ubuntu/Cannonical through the mail to pass out (so far I have a few people interested, but, like me, all of them aren't tired of Windows quite enough to make the jump).

For reference, the PC in question has 3.5ghz dual core, 4 GB RAM, and normally runs under Windows XP Pro SP2.  If more in-dept technical/hardware details are required, I'd be happy to look them up.  I'm just not shure what'd help or not, and I'm trying to use that computer as little as possible.

---

### Post by Pumalite on 2007-10-27
See if you can boot a Knoppix Live CD to save your data: [http://www.knopper.net/knoppix/index-en.html](http://www.knopper.net/knoppix/index-en.html)
Later you can install Ubuntu with the Alternate CD.
Posting your specs would help.

---

### Post by DezSP on 2007-10-27
I got a problem very similar to this with the 6.10 LiveCD, turns out the kernel was too old and didn't support my hardware properly. 7.04 fixed that, so the first thing I'd suggest is using a newer version of Ubuntu, or another LiveCD with a later kernel.

When you say your computer crashed, what exactly happened to it? It might well be related, as that third line definitely looks like a HDD issue to me. Quite what it's trying to tell us I have no idea though. Try booting with the hard drive unplugged, and see if it still happens.

---

### Post by Ocarina654 on 2007-10-27
I was trying to burn a CD when the computer froze entirely.  Trying to close the program, Ctrl+Alt+Del didn't do anything, nothing was responding.  I turned the computer off manually, and when I turned it back on everything was busted.
Come to think of it, HDD problems seems likely.  If the crash/shutdown caused physical HDD errors, would there be any way to repair that short of replacing the drive?

About Knoppix: I have an old Knoppix 3.3 CD, but it too has problems starting up.  Perhaps it is as DezSP says, and there is a problem with the Kernel supporting my hardware.

I haven't tried unplugging the HDD yet (its hard to get to in my PC, HP builds tightly packed machines, apparently), but will try that soon.  I will also try downloading both a newer version of Knoppix and Ubuntu 7.10 and see if Kernel updates will help on the Linux front of this issue.

Thanks for the help.

Also, I don't really know what hardware information would be necessary, but here's my DxDiag information.
[http://download.yousendit.com/3C073ABB77121C17](http://download.yousendit.com/3C073ABB77121C17)
If there's any other hardware information that would help, let me know more specifically and I'll see what I can do about obtaining it.

---

### Post by DezSP on 2007-10-27
You could try running CHKDSK.exe on it, use a XP disc if you can't get it to run from the actual OS. CD burning means plenty of read/write activity on the HDD, and if it crashes in the middle it can cause all sorts of problems.

But as I've already said, it's not entirely clear what exactly the problem is with booting into Linux on your machine, so try some diagnostics and we'll get to the bottom of this. :)

---

### Post by Crafty Kisses on 2007-10-27
> **Pumalite said:**
> See if you can boot a Knoppix Live CD to save your data: [http://www.knopper.net/knoppix/index-en.html](http://www.knopper.net/knoppix/index-en.html)
Later you can install Ubuntu with the Alternate CD.
Posting your specs would help.

I always liked the Knoppix LiveCD.

---

### Post by Ocarina654 on 2007-10-28
Well, older Knoppix disc didn't work, but newer one did.

I'm guessing this just was a Kernel/hardware support issue.

However, since I haven't tried Ubuntu yet, I don't know that I'd call my problem totally solved.  However, the majority of the issue has been taken care of, so I'm going to mark this solved.

On a completely unrelated note, this version of IceWeasel that came with Knoppix either has a German dictionary, or none at all.  It's marking all my words as mis-spelled...  Haha, I'll figure it out.

---

