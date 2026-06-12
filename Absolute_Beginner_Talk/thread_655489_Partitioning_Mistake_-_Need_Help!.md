---
title: "Partitioning Mistake - Need Help!"
date: 2008-01-01
forum: Absolute Beginner Talk
---

### Post by Sunships on 2008-01-01
Hi, during an attempt to edit partitions during Ubuntu 7.10 installation I accidentally set the whole hard drive as "linux-swap". The hard drive already had Windows Vista running with files that I would like to keep - now on boot it says "missing operating system" and goes no further. How can I reverse this? I have tried using a Windows install disc to try and repair, but this did not work. Using the Ubuntu liveCD doesnt help either - while it still sees the hard drive set as "inux-swap", I cannot access it in the file manager to get the information off. 

Any ideas on how to restore Vista, or alternatively at least recover the files before I re-install? Thanks for your help!

---

### Post by Sunships on 2008-01-01
Bump

---

### Post by blithen on 2008-01-01
Get into the live cd and re-install ubuntu on the linux-swap partition it will change the filing system to EXT3 and there you go.

---

### Post by jamaisvu on 2008-01-01
> **Sunships said:**
> Any ideas on how to restore Vista, or alternatively at least recover the files before I re-install? Thanks for your help!

[FONT=Franklin Gothic Medium]You could try using dd (look it up, and be very careful with the syntax) to copy an exact image of whatever's left on that drive to another drive, but quite frankly, it's probably utterly hosed.

If your data are really important, you could try sending your drive off to a data recovery service. Otherwise, remember the following two things:

1) Always back up your data!
2) Always punch people who advise you to back up your data in the head!
[/FONT]

---

### Post by Sunships on 2008-01-01
> **blithen said:**
> Get into the live cd and re-install ubuntu on the linux-swap partition it will change the filing system to EXT3 and there you go.

Hi, won't installing Ubuntu re-format everything? The linux-swap partition is currently the whole hard drive :(

---

### Post by ryanVickers on 2008-01-01
I agree with those 2 points ;)

But yeah... Unfortunately, if it's been formatted, I would say it's all gone.  Sometimes you can recover data if you [COLOR=Red]stop all writing to the drive immediately[/COLOR]!, but its not likely...

If it does work however, you'll have the best luck with archives and images because the file structure is very dense (or something like that... :p)

---

### Post by Sunships on 2008-01-01
> **ryanVickers said:**
> I agree with those 2 points ;)

But yeah... Unfortunately, if it's been formatted, I would say it's all gone.  Sometimes you can recover data if you [COLOR=Red]stop all writing to the drive immediately[/COLOR]!, but its not likely...

If it does work however, you'll have the best luck with archives and images because the file structure is very dense (or something like that... :p)

Hi, I didn't actually start the installation - so far all that happened was the re-assignment of the hard drive to "linux-swap".

Thanks for the comments so far - I am downloading an ISO for a bootable CD which contains TestDisk, and will try that if there isn't a simpler solution.

---

### Post by ryanVickers on 2008-01-03
you are saving the ISO where? ;)

---

