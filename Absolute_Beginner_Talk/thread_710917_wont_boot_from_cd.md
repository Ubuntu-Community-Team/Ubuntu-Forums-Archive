---
title: "wont boot from cd"
date: 2008-02-29
forum: Absolute Beginner Talk
---

### Post by Fanin on 2008-02-29
I'm am trying to get my Ubuntu laptop to boot from a CD, but it just says "loading GRUB" or something :confused:

the BIOS settings is set to boot from CD first but it makes no difference.. is there some other way of setting the boot order or something i should know about?

---

### Post by jan quark on 2008-02-29
if you are using the Live CD and encounter this problem

give the[ alternate CD]("http://releases.ubuntu.com/gutsy/") a try.

It's more stable and causes less trouble.

---

### Post by Fanin on 2008-02-29
i guess i forgot to mention that i am trying to install windoze on it :(
the CD drive sounds like its working but my computer just skips it and moves on to starting up Ubuntu

---

### Post by kesman on 2008-02-29
seems like your windows cd isn't working if it doesn't boot.

---

### Post by Fanin on 2008-02-29
CD works fine
i tried it on an other computer and it worked perfectly.. but i want to keep Ubuntu on that computer :)

---

### Post by jan quark on 2008-02-29
if you somehow manage to boot from the Windows CD (still thinking) you will have to restore the Grub Loader because windows will overwrite it and you won't be able to boot into linux anymore.

see here for further reading:
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows?action=show&redirect=RestoreGrub](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows?action=show&redirect=RestoreGrub)

---

### Post by kesman on 2008-02-29
Maybe insert the cd while the pc is running and then boot. If you insert the disk while the computer's booting up, it may not load the disk in time to boot from it.

---

### Post by Fanin on 2008-02-29
> **kesman said:**
> Maybe insert the cd while the pc is running and then boot. If you insert the disk while the computer's booting up, it may not load the disk in time to boot from it.

done that (many times actually) and it wont work :confused:

---

### Post by kesman on 2008-02-29
Are you sure booting from cd is the first choice in bios? Have you tried with any other bootable cd?

---

### Post by Fanin on 2008-02-29
> **kesman said:**
> Are you sure booting from cd is the first choice in bios? Have you tried with any other bootable cd?

i am 100% positive that CD is first in boot order (I've checked, double checked and triple checked)
and yes i have tried booting with a DOS boot CD and it worked fine

---

### Post by kesman on 2008-02-29
This is turning out pretty funny if ubuntu won't let you boot with your windows cd anymore =D
No seriously, it cannot have anything to do with ubuntu or grub since the bootable cd's are loaded way before grub starts.

By the way, you need to press ENTER to get windows cd to boot from cd. Try hitting enter repeatedly during the boot-up.

---

### Post by Fanin on 2008-02-29
> **kesman said:**
> This is turning out pretty funny if ubuntu won't let you boot with your windows cd anymore =D
No seriously, it cannot have anything to do with ubuntu or grub since the bootable cd's are loaded way before grub starts.

By the way, you need to press ENTER to get windows cd to boot from cd. Try hitting enter repeatedly during the boot-up.

i tried hitting enter when booting up, but nothing happened :(
i also tried starting windows setup from cd with Wine, but it didn't work either :confused:
I'm totally out of ideas

---

### Post by kesman on 2008-02-29
Then try again, with ESC key this time. How fast does your laptop screen go on after you boot? Can you see all the bios messages right after you hit the power button?

---

### Post by Fanin on 2008-02-29
> **kesman said:**
> Then try again, with ESC key this time. How fast does your laptop screen go on after you boot? Can you see all the bios messages right after you hit the power button?

hmm.. when i hit escape i can see the bios messages and if i hit escape again i can choose what to boot from, so of course i choose cd-rom.. it loads for a while and then decides to start ubuntu anyways :confused:
what the heck?

---

### Post by kesman on 2008-02-29
Maybe there's some little scratch in the windows cd and a bit too scratch-sensitive cd-rom drive in your laptop that causes this. Can you try with another windows install cd? Also try cleaning the cd abit with some soft cloth and blow into your cd-drive carefully.

---

### Post by Fanin on 2008-02-29
> **kesman said:**
> Maybe there's some little scratch in the windows cd and a bit too scratch-sensitive cd-rom drive in your laptop that causes this. Can you try with another windows install cd? Also try cleaning the cd abit with some soft cloth and blow into your cd-drive carefully.

i have also done that.. nothing works
do you think it would be a good idea to format the drive and then try?

---

### Post by kesman on 2008-02-29
I don't think it would make any difference, but if you don't want to have ubuntu on the disk anymore, then go ahead.

---

### Post by Fanin on 2008-02-29
> **kesman said:**
> I don't think it would make any difference, but if you don't want to have ubuntu on the disk anymore, then go ahead.

I'd rather have Ubuntu than nothing.. oh well, nothing much else to do :(

---

### Post by Fanin on 2008-02-29
oh well.. i have decided to give it a shot and try to wipe my HD
how do i do that :confused:

---

### Post by kesman on 2008-02-29
Boot with ubuntu liveCD and use the partition manager to delete all partitions from the hd.

---

### Post by Fanin on 2008-03-23
could someone please give me a small tut on exactly how to do that or point me in the direction of one?
i tried looking around but i don't think i should touch anything unless i know what I'm doing

---

### Post by Fanin on 2008-03-24
bump :)

---

### Post by Fanin on 2008-03-29
bump

---

### Post by ad_267 on 2008-03-29
Edit: Sorry, I didn't realise this was the third page of posts and hadn't read the previous posts so this will be pretty useless

You need to change the settings in your BIOS. Exactly how you do this is dependent on your computer.

Usually you press the delete of F2 key or something else when the computer is first starting up. There should be a message like "Press the delete key to enter setup"

Once in you need to navigate around and find something like "boot device priority", that lets you change the order of devices that will be used to boot from. You need to put your cd drive before your hard drive in this list. After this your computer should automatically boot from the CD.

I found this, along with many other hits, by googling for "How to boot from CD" which may be helpful: [http://techpaul.wordpress.com/2007/08/03/how-to-boot-from-a-cd/](http://techpaul.wordpress.com/2007/08/03/how-to-boot-from-a-cd/)

---

### Post by Fanin on 2008-03-29
> **ad_267 said:**
> Edit: Sorry, I didn't realise this was the third page of posts and hadn't read the previous posts so this will be pretty useless

You need to change the settings in your BIOS. Exactly how you do this is dependent on your computer.

Usually you press the delete of F2 key or something else when the computer is first starting up. There should be a message like "Press the delete key to enter setup"

Once in you need to navigate around and find something like "boot device priority", that lets you change the order of devices that will be used to boot from. You need to put your cd drive before your hard drive in this list. After this your computer should automatically boot from the CD.

I found this, along with many other hits, by googling for "How to boot from CD" which may be helpful: [http://techpaul.wordpress.com/2007/08/03/how-to-boot-from-a-cd/](http://techpaul.wordpress.com/2007/08/03/how-to-boot-from-a-cd/)

i know that and "boot from CD" is already priority number 1, but the only CD that boots is the Ubuntu liveCD.. it wont allow me to boot anything else

---

### Post by rkd on 2008-03-29
Okay, from what you have said:

You can boot the Ubuntu Live CD.
You can't boot the Windows install CD.
You can boot the Windows install CD on another computer.

That tells me that either the Windows install CD is a little flaky, the CD drive is a little flaky, or both.

Something you could try is to make a copy of the Windows install CD on another computer.  Perhaps the copy will work.  Or if you have a different Windows install CD, that might work.

If you try this, be sure the way you make the copy gives a true duplicate.  If you are unsure of how to do that copy, ask how (and mention what software you have available to use for the copy).

---

### Post by ugm6hr on 2008-03-29
Where did you get the Windows CD?

Is it an OEM version that came with a computer (if so - which one)?

Or did you buy it separately (fresh from Microsoft)?

Have you ever had Windows on the computer?

Another option might be to use Windows in a VM (in Ubuntu) - if that works.

Wiping the HD will not do anything in this situation, since it is clear your computer does recognise bootable CDs properly.

---

### Post by Fanin on 2008-04-13
let's get one thing straight.. i would never pay for windoze.. ever
is that a big problem?
i get it with torrents :)

---

### Post by ugm6hr on 2008-04-13
> **Fanin said:**
> let's get one thing straight.. i would never pay for windoze.. ever
is that a big problem?
i get it with torrents :)

Yes.

Thread closed due to request for instructions on how to install illegal copy of software.

---

