---
title: "have searched until i'm cross eyed"
date: 2006-10-23
forum: Absolute Beginner Talk
---

### Post by kratos1963 on 2006-10-23
I thought I would like to expand my knowledge and learn the world of linux.  I taught myself dos back before there was windows, hell even before there was dosshell.  I was writing sophisticated bat and bas files when most of you were in diapers. I grew up with Archie and Veronica.  I hated it when Microsoft came out with windows because it instantly made ever user a know it all.  But it was all good because I understood Dos.  I could play with peoples minds with the bat files I could write. Bat files that would scare the shit out of people.  I once spent a month telling my boss about a bogus april first virus.  I wrote a simple bat file that simulated a hard drive format that launched 4/1.  he freaked out.  it was all in fun and once she got over her panic attack she laughed about it.  My point is that I'm no dumb ***. I can teach my self anything if I have the resources.

My whole online linux experience has dampened my eagerness to learn linux.  Seems like everywhere I turn I see "don't ask read".  I went to #Ubuntu on IRC  and was rediculed about my OS and my hardware. I have tried my best to read and learn as much as I can, and I'm at my wits end.  So I'm just going to ask and if it's been asked before, I don't care.  I'm not trying to be nasty but if i get banned, again  I don't care. If anyone can give me a heads up to the problem I am having I would be forever graatful.

Ok  now for my Q.

I have an aopen 63pro mobo with an intel 667 processor.  Slot one I think,  its the one that stands up on the mobo. and 256 ram.

A 10m hard drive with one partition listed as drive D
A 80m hard drive with mutiple partitions up to L

a generic cdrom drive.

a voodoo3 grapics card  with 16megs ram driving a 19" ic flat panel monitor and a trident svg driving a 17" crt monitor

a advance  something something 4000 sound card

a external scsi cdrom drive

a external usb dvd drive

Drive C: boots win98
Drive E: boots win2k
Drive G: boots winxp

two floppy's and a partiage in a pair tree.

Q:  does any of these pose a problem trying to run Linux?

I have downloaded both Ubuntu and morphixs.  niether will work on my pc  and both will work on work pc.

---

### Post by kratos1963 on 2006-10-23
going to go play texas holdem at pokerstars.com on my dos plat form and wait for a reply.

---

### Post by akniss on 2006-10-23
> **kratos1963 said:**
> 
A 10m hard drive with one partition listed as drive D
A 80m hard drive with mutiple partitions up to L


One question: does this mean 10/80 megabytes?  If those are 10/80 gigabyte HDDs, you will probably be fine...  However, I'm not sure how you're running XP if that is an 80 MB.  Not sure what your "m" means is what I'm getting at...

And if you can boot off of your cdrom, why not just pop in a liveCD to see if everything works?  That will probably be the easiest way to find out if everything works.

---

### Post by kratos1963 on 2006-10-23
sorry  10/80 gig

---

### Post by kratos1963 on 2006-10-23
would be hard to run 3 platforms from a 80 meg drive no?

---

### Post by Sef on 2006-10-23
> would be hard to run 3 platforms from a 80 meg drive no?

Do you mean triple boot? (Have a choice of 3 operating systems to boot into.)

If so, yes you can do that.  Not too hard to do.

---

### Post by kratos1963 on 2006-10-23
98 2000 and xp

believe i said partitsions up to drive "L"

I'm to lazy to go back and look,  like i said I have read until I'm cross eyed.

---

### Post by GameboyHippo on 2006-10-23
The Voodoo 3 3000 might give you problems.  I'm running it on my secondary PC and it's been a nightmare.  My suggestion is to configure it to use vesa "sudo dpkg-reconfigure xserver-xorg" and forget about 3D acceleration on it.

---

### Post by po0f on 2006-10-23
kratos1963,

WRT hardware, the only thing I could see a problem with is your external SCSI cdrom, and possibly your sound card (only since you weren't too sure about the model).  The best way to test your hardware would be to just pop in the live CD, boot it up and cross your fingers.  ;)  On the software side, good luck setting all that up in GRUB!  ;)

I can't apologize on behalf of anyone who has tried to "help" you with ridicule (only they can do that), but I am a little saddened by your experience.  I don't frequent #ubuntu, but have been there occasionally.  Generally the people there are helpful, but there are always bad apples.  I'm sorry that your first experience with our Ubuntu community was a bad one, hopefully we can rectify that in the coming days.  :)



Wow, I am really slow in posting, maybe I should just have given an answer and submitted it, and not typed so much.

---

### Post by kratos1963 on 2006-10-23
have set my primary video card to the trident and Ubuntu still locks during load.

---

### Post by kratos1963 on 2006-10-23
#ubuntu was a joke.  but ever one here seems nice enough.

---

### Post by po0f on 2006-10-23
kratos1963,

Is there anything on the screen that you can maybe post here?

Older hardware also tends to behave badly with ACPI, try passing *acpi=off* to your boot command.  IIRC hit F6 when you get to the boot screen and add it to the parameters passed to the kernel.

---

### Post by kratos1963 on 2006-10-23
k I'm going to pull the voodoo card,and the scsi card and try again.

thanks for the imput.

---

### Post by kratos1963 on 2006-10-23
I added no apic and no lapic to boot command. and the only thing I see wrong is during check files it says squashfh mismatch  or sometihing like that

---

### Post by po0f on 2006-10-23
kratos1963,

Can you verify that you have a clean burn of the iso?  Compare the md5sum from the mirrors with what you get from your downloaded iso.

---

### Post by kratos1963 on 2006-10-23
I took both Ubuntu and Morphix to work and they both work on the pc.  i'm having a hardware problem.

---

### Post by brash on 2006-10-23
Try checking both hard drives and ram for any errors there?

---

