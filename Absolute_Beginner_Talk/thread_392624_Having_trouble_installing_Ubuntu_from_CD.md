---
title: "Having trouble installing Ubuntu from CD"
date: 2007-03-24
forum: Absolute Beginner Talk
---

### Post by Cold-Gin on 2007-03-24
Hi. I received a Ubuntu CD in the mail. When I install from the CD, I get the opening screen where I select "Start or Install Ubuntu", but then the following occurs:

I get a "Loading Linux Kernel" window, then I see a blank screen that says "Uncompressing Linux... OK", then I was getting a bunch of brown lines and I heard a repeated clicking every few seconds, as if some process were caught in a loop.

Now, when I restart my machine, I still get the opening Ubuntu window, I choose "Start or Install Ubuntu", again, I get the black screen that says "Uncompressing Linux... OK", but then nothing at all happens. The CD is not being read; everything just freezes with no further progress.

I found a link that shows what the installation screens are supposed to look like, at it seems that I never get to the Ubuntu installation screen with the progress bar that begins with "Loading drivers..."

I am installing Ubuntu, on a "throw away" machine, but now I can't seem to move forward with the installation at all. Can anybody make a suggestion at this point?

Thanks so much.

---

### Post by luke411 on 2007-03-24
maybe you should try downloading the cd from Ubuntu.com and see if you just got a bad disk.

---

### Post by koshari on 2007-03-24
you could try using graphic safe mode, 

alternatively the alternative install disk may be an option however you will need another disc which doesnt fix your current dillema,

there are also a few switches you can try that may help, 

just for the record are you able to the get the first menu screen?

---

### Post by Cold-Gin on 2007-03-24
Hi. Thanks for replying... Yes, I do get the opening menu. I chose the check disk option, and that seemed to be fine. I did try in graphics safe mode, but that option also froze...

You said there were some switches I could try... What would they be?

Thanks again.

---

### Post by Feenix3k on 2007-03-25
My nvida motherboard has this problem also. When I loaded Suse I had to add the no apic option. In Ubuntu you add this to the boot line after you push F6. But so far, no matter if i put apic=off or noapic it still loads just before goint to the brown screen befor the Ubuntu box shows. I have gotten as far as getting the start up sound then it all dies. I know my problem with this motherboard is a bios thing.

---

### Post by linuxjerk on 2007-03-25
I found that ubuntu is very picky about what cdrom it will install from. I don't know why.
Out of 3 different cd rom drives I only found one that would install it properly.
Also out of 4 hard drives only 3 would install. The fourth would hang every time.
I guess I should mention that all the drives above would install windows every time
with no failures.
This is with the 6.10 edgy live cd. My live cd checked out ok also. Most of the time I could get the live cd to work
but then it would hang during the install to hard disk.
Something is a bit unstable here.
Seems to be pretty picky about sysem boards and drives.

---

