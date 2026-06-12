---
title: "how to...with k3b ???"
date: 2006-07-24
forum: Absolute Beginner Talk
---

### Post by MaximB on 2006-07-24
1.I want to copy **dvd's** and I can't find that option in k3b
2.when I tried to copy **cd **- it did good on the first half (converting to iso image) but then it said it couldn't eject my cd for some reason, and then it stoped with an error.

---

### Post by aysiu on 2006-07-24
So you don't see this option in your K3B?

---

### Post by MaximB on 2006-07-24
mmm...I just looked at the welcome screen and it wasn't there...thanks
by the way - why ? (the second part of my question).

---

### Post by aysiu on 2006-07-24
No idea on the second question.

---

### Post by MaximB on 2006-07-24
maybe you can tell me how the copy cd/dvd works
do I have to swich between the cd's in order to make a copy or it does it wothout swiching ? (I have 1 dvd and 1 cd recorders)

---

### Post by aysiu on 2006-07-24
I have a DVD-ROM drive and a CD-RW drive, and it looks as if K3B's default copy setup is to copy from the DVD-ROM drive to the CD-RW drive, so I would assume you put the source CD in one drive and the blank CD in the other.

---

### Post by OU812 on 2006-07-24
Hmm. First, k3b can only copy nonencrypted dvds. And I think you need to have libdvdread installed. Unless I'm mistaken, linux can't copy dvd to dvd or cd to cd (unless this has changed recently). So basically, for cds, you can rip the disc as wav files and then burn the wav files. I haven't tried to make an iso. I also haven't tried to copy dvds.

john

---

### Post by aysiu on 2006-07-24
> **OU812 said:**
> Unless I'm mistaken, linux can't copy dvd to dvd or cd to cd (unless this has changed recently). So basically, for cds, you can rip the disc as wav files and then burn the wav files. I haven't tried to make an iso. As you can see from my last screenshot, K3B is built to copy from CD to CD. Now, I haven't actually tried that function, but I have copied to ISO, and it works just fine, so you definitely don't have to rip the disc and then burn the .wav files. At the very least, you can rip to ISO and then burn the ISO afterwards. But I don't see why K3B would give you the appearance of a certain functionality (copying from CD to CD) without that actually working.

Where are you getting your information from?

---

### Post by OU812 on 2006-07-24
I first encountered this "problem" when using zenwalk linux. Please let me clarify - linux can't copy on the fly, so even if you have two drives, you still have to "extract" the files from the source to the hard drive and then burn them to the destination. By using 2 drives, you're only saving yourself the trouble of swapping discs.

@maxddark - are both of your drives showing up in your fstab?

john

---

### Post by aysiu on 2006-07-24
> **OU812 said:**
> linux can't copy on the fly, so even if you have two drives, you still have to "extract" the files from the source to the hard drive and then burn them to the destination. By using 2 drives, you're only saving yourself the trouble of swapping discs. Does it matter to the end-user? If I put in a source disc and a blank disc and say "copy this from here to here," I'm not sure if it matters to me whether it first gets copied to the hard drive and then the disc or to the disc directly, as long as I have a working copy at the end of it.

---

### Post by OU812 on 2006-07-24
Perhaps - I think that when rip directly to mp3, you are doing this digitally. If you first rip to wav and then convert to mp3, you have in effect made an analog recording. Copying a full disc is the same principle - by making an image or ripping as wav files, you are making an analog recording because it goes through your sound card. (I may be wrong).

john

---

### Post by aysiu on 2006-07-24
An ISO image goes through your sound card? What?

---

### Post by OU812 on 2006-07-24
> (I may be wrong)

Whatever. I give up. I thought I was helping.

Peace Out.

P.S. An .iso is made from files on the hard disk. So again you are doing a two-step process by copying files onto the hard drive instead of doing just one step as in on-the-fly.

---

### Post by indytim on 2006-07-24
I just checked my version of K3B and yes, there is a DVD copy.  If you launch K3B and right click on the screen, you will see a variety of functions you can add at the launch screen.  You can also do the same from the K3B menu.  As mentioned before, the DVD copy function should work on data dvd's.  If you're trying to copy a video DVD, will have to do a bit more in the backup process than a mere dvd copy.

IndyTim

---

### Post by thx84 on 2006-10-11
> **aysiu said:**
> Does it matter to the end-user? If I put in a source disc and a blank disc and say "copy this from here to here," I'm not sure if it matters to me whether it first gets copied to the hard drive and then the disc or to the disc directly, as long as I have a working copy at the end of it.

well it does if you have a laptop... i'm still looking for an app that could copy on the fly with only one drive available

---

### Post by aysiu on 2006-10-11
> **thx84 said:**
> well it does if you have a laptop... i'm still looking for an app that could copy on the fly with only one drive available
I wasn't talking about laptops.

I was replying to this remark: > linux can't copy on the fly, **so even if you have two drives,** you still have to "extract" the files from the source to the hard drive and then burn them to the destination. By using 2 drives, you're only saving yourself the trouble of swapping discs. [Emphasis added]

---

### Post by Marc A on 2006-10-17
as far as i know, using K3B for four years now, it can copy on the fly. "On th fly" meaning from one drive to another without creating an image on the hard-disk but using a buffer.

Now if you only have one drive "on the fly" is not possible.

to copy a cd you just open tools and choose copy cd or clic on the picture of two disks. It will open a dialog box with many choice and ten copy an image on your disk, eject the source-disk and burn on the trajet-disk. You need enough place on you hard-drive to store an image during the process.

Good luck,     Marc A

---

