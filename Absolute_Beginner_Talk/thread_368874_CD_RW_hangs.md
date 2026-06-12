---
title: "CD RW hangs"
date: 2007-02-23
forum: Absolute Beginner Talk
---

### Post by zuesko on 2007-02-23
Hi Nwbe,
I wanted to install fresh Dapper on my Linux box, when my DVD drive died, which installed Dapper no problem(when working).
So I had a CD RW lying around and thought that would do the trick. It came out of my Xp box and was burning CD's and reading them, in fact it did everything but make the coffee.

Now back to my Dapper box:
P3 Ram 256 HDD 40GB CD RW Benq 40x12x48

As I said before the DVD, I could load Dapper no problem.
Now the error messages:
It gets the fist install screen, so I  start in safe graphic blah....Nivida video card
Next load kernel and then I wait....wait....wait.....finally,
Uncompressing Linux... Ok, booting the kernel.
Loading essential drivers    Ok
Mouting root file system     Ok
Moving mount points         Ok
Adding live CD user        
wait....wait.....wait.......
Uncompressing Linux... Ok, booting the kernel.
[17179704.296000] hdc: timeout waiting for DMA
[17179781.296000] hdc: cdrom_read_intr: data underrun (4 blocks)
[17179781.440000] Buffer I/O error on device hdc, logical block 27761
[17179824.296000] hdc: timeout waiting for DMA
[17179884.296000] hdc: cdrom_read_intr: data underrun (4 blocks)
[17179886.296000] Buffer I/O error on device hdc, logical block 
[17179886.296000] hdc: timeout waiting for DMA
[17179888.296000] hdc: cdrom_read_intr: data underrun (4 blocks)
[17179888.296000] Buffer I/O error on device hdc, logical block 

This error sequence repeats for 10min aprox and then the screen goes black and that is it.
Any thoughts would be greatly appreciated:confused:

---

### Post by tgalati4 on 2007-02-23
I'm sorry my friend.  Bad news.  Your motherboard suffered a heart attack.

It could be a cable.  Find another one or swap them.  Could be problems with the ide channel.  How do you know if the DVD is bad?  Try it in another machine.  Of couse DVD failures are quite common.  Do a search on your brand and read in amazement.

Could be a jumper problem on the CD.  Try "Slave" instead of "Cable Select"

Go into the BIOS and verify that IDE channels 1 and 2 are active and set to Auto detect.  Watch the BIOS bootup screen for IDE detection messages.  All of your disks should show up.

Could be a power supply problem.  When disks spin up they draw a lot of current and your PS could be dropping out.

If it is an older CD, it could be problems with reading burned CD's.  Many older CD readers are picky about media.  Burn your precious Ubuntu ISO's with ultra-slow, music-quality, archival burn speeds.

It's probably the last case since it died during the read of the compressed image.  Try to perform a CD check.  If it passes the md5 check then you know that the CD can at least read the entire drive.

I had an old CD drive that could read the inner music tracks OK, but it would always fail in the outer tracks.  The bearing had worn and the disk was wobbly.

Keep the faith.  We need you in the fight.

---

### Post by zuesko on 2007-02-24
Thanks tgalati4,

I got to thinking what you said and I recalled the CD RW now in my Linux Box worked on the XP box. So I swapped the old CD R from the XP and visversa.
Guess what? It all works!!

Cheers:)

---

