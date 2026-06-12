---
title: "wanting to try ubuntu, running into a snag"
date: 2007-07-19
forum: Absolute Beginner Talk
---

### Post by noremacyug on 2007-07-19
when i go to install ubuntu onto my scsi striped array i get an error as though it's not accessing the disk. i figure this is due to lack of drivers for the adaptec 2100s pci card  on the install disk, just my guess. i was able to switch the boot order to my second single ide drive and installed ubuntu on that, however after removing the disc and rebooting, it through an error during the boot process. error 18 i believe it was.  how would i go about dual booting off my striped array or if i have to, leave windows on the array and put ubuntu on the single ide drive?

i'm new to linux so please be gentle.  looking to learn and possibly convert someday once i'm comfortable with it.  if any more info is needed, let me know.

thanks
guy

---

### Post by noremacyug on 2007-07-19
anyone?  i'm still in need of direction.

---

### Post by noremacyug on 2007-07-20
ok, without my changing anything it magically let me go to livecd of ubuntu.  from which i suppose i could have went on and installed. but i wanted to see if it would work again or if it would give me the error again.  guess what, i got the error.  i've gotten it to go to livecd a couple times and the other times were errors.  it's a shot in the dark as to whether or not it works.

here' a lovely pic of said error.

---

### Post by noremacyug on 2007-07-20
for the love of all thats good!!! No one knows anything that can help?!?!?!?!

---

### Post by asmoore82 on 2007-07-20
:confused: have you tried using the single drive yet?

---

### Post by armandh on 2007-07-20
ubuntu is the first linux I have tried that works well
I have a few work bench junkers and it is on these i have tried knopix, linspire, ubuntu, etc.
I would NOT advise anyone to try it on mission critical hardware [at first] or at all without a working immage.

while the live cd workes with 128M mem the install requires 256 to partition while there is no swap file [while you are partitioning]
resolved with an old small hard drive for the swap file while the main HDD is setup

---

### Post by graigsmith on 2007-07-20
went to this site to see what scsi cards ARE supported in the kernel.
[http://www.linuxhq.com/ldp/howto/Hardware-HOWTO/raid.html](http://www.linuxhq.com/ldp/howto/Hardware-HOWTO/raid.html)

and it looks like the only raid cards supported are mylex raid cards.  and i looked at some prices, they are VERY expensive raid cards.  

adaptect offers linux drivers. for red hat and suse.  mabey you could get those to work, i have no idea how to do that though.

[http://www.adaptec.com/en-US/downloads/rh/rhl_6?productId=ASR-2100S&dn=Adaptec+SCSI+RAID+2100S](http://www.adaptec.com/en-US/downloads/rh/rhl_6?productId=ASR-2100S&dn=Adaptec+SCSI+RAID+2100S)

---

### Post by trak87 on 2007-07-20
> **noremacyug said:**
> anyone?  i'm still in need of direction.

Don't use RAID.

---

### Post by alienexplorers on 2007-07-20
If you are running windows then run that on the striped array.  Load and run Ubuntu from the single drive.  It should recognize the Windows and Ubuntu and setup the grub loader for you.

---

### Post by tcoffeep on 2007-07-20
Have you tried searching for what the error code might mean (depending on the program you're using)?

---

### Post by noremacyug on 2007-07-20
finally, i appreciate the responses guys/gals.

i did originally create an 8gb partition on the single drive which i installed ubuntu on.  after the instalation process i got a grub error i think it was.  i want to say error 18.  after that i just decided to put them both on the raid array but have had no luck so far.

as far as partitioning goes, i'm giving the main system files ~7gb of space and ~1gb of space for the swap.

i've been trying to get the livecd to work however, it won't even load to that so long as i have the raid card set to higher priority than the ide controller.  i keep getting the error that is in the picture above.  what exactly does the livecd need to boot up, do i need to have a free partition set aside just to run the livecd? surely not. 

 if i can't install on the raid array like i really want to then i suppose i'll repartition the single ide drive again and see what happens with it.

i'm pretty sure i mentioned it above, but just to restate it, i did accidently get into the livecd whilest the raid card was set to higher priority than the ide controller once and only once.  i changed nothing on my system it just went on in.  i rebotted to see if it would let me do it again, but no go.

again i appreciate the responses.

---

### Post by Majorix on 2007-07-20
I have seen this error somewhere else in these forums. That was in the absolute beginners forum too. You might want to look up if they got a working solution.

Furthermore, I would suggest reporting this as a bug over at launchpad.

Good luck.

---

