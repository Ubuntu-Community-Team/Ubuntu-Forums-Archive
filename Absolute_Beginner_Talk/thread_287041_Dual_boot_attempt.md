---
title: "Dual boot attempt"
date: 2006-10-28
forum: Absolute Beginner Talk
---

### Post by Cairna on 2006-10-28
Hi, I'm a windows xp user interested in installing linux, specifically Ubuntu, I downloaded the cd version but I need to make a partition, I'm currently using Symantec Partition Magic.

I have about 30gigs free to make the partition, but I'm not sure how to go about doing it.

Any help? :twisted:

---

### Post by HareBall on 2006-10-28
> **Cairna said:**
> Hi, I'm a windows xp user interested in installing linux, specifically Ubuntu, I downloaded the cd version but I need to make a partition, I'm currently using Symantec Partition Magic.

I have about 30gigs free to make the partition, but I'm not sure how to go about doing it.

Any help? :twisted:
I used the partitioner on the install disk. Gpart, I think. Worked flawlessly. Even knew what I needed as far as how many partitions. Did the swap file, grub and everything.

---

### Post by Xphome on 2006-10-28
if you have 30gb unused then you do a 29gb partition for / and 256-1gb for /swap or 25gb / , 4gb /home , 256-1gb /swap.

i have a 190gb hdd so i have it like this:
80gb /
512mb /swap
111gb unused(for NTFS when im installing XP again(dualboot))

EDIT:i used the partition program on the Live CD.(installation)

---

### Post by fasoulas on 2006-10-28
I had the same quastion when i entered this forum and someone helped me

So go here 

[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

---

### Post by gentlemanmasher on 2006-10-28
I thought using the Gpart on the disk was very easy when I did my install.

---

### Post by Cairna on 2006-10-28
Then my problem seems to be that that does not show up when the burnt CD is in the disk drive. It goes straight to the compaq screen, then to the windows screen giving me the option of Windows Recovery or WIndows XP Home Edition.
:-|



-Edit, my problem seems to be the BIOS settings now that I looked at your link, where do I go to change that?

---

### Post by JayTee on 2006-10-28
> **fasoulas said:**
> I had the same quastion when i entered this forum and someone helped me

So go here 

[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

Definitely check this link out for dual-boot how to. It has tons of really CLEAN, CLEARLY written how-to's on all types of installation and configuration issues for Ubuntu. It's done by one of the forum staff here and they know their stuff.

---

### Post by Cairna on 2006-10-28
I tried the F8, F1,F2, ESC and Del keys during the bootup. Couldn't do anything with it.

Perhaps it's different with my compaq...

---

### Post by confused57 on 2006-10-28
> **Cairna said:**
> I tried the F8, F1,F2, ESC and Del keys during the bootup. Couldn't do anything with it.

Perhaps it's different with my compaq...
I'm not familiar with Compaq, but you could probably use google & find the correct key(s), e.g. compaq(model #) bios

---

### Post by Cairna on 2006-10-28
I have an external harddrive of 10 gigs, is there a way I can use that? The cd I believe doesn't work well.

---

### Post by gn2 on 2006-10-28
Maybe try F10 or F12 to get to the BIOS,

Did you burn the Ubuntu download as an ISO image using a CD-R, CD-RW sometimes doesn't work.....

---

### Post by daou on 2006-10-28
Here is a quick howto on installing Ubuntu to an external USB hdd:

[http://www.ubuntuswitch.com/2006/08/01/installing-ubuntu-on-an-external-usb-hard-drive/]("http://www.ubuntuswitch.com/2006/08/01/installing-ubuntu-on-an-external-usb-hard-drive/")

---

### Post by angus-higgins on 2006-10-28
> **Cairna said:**
> I have an external harddrive of 10 gigs, is there a way I can use that? The cd I believe doesn't work well.

If you have an external hard drive that is USB, and your BIOS features a boot from USB feature, you should be able to do it; although I don't know whether the disk would detect the hard drive as a hard drive. :-k 

Angus Higgins

---

### Post by Bartender on 2006-10-28
I googled 'Compaq BIOS keys' - here's the first [link]("http://www.techadvice.com/tech/B/BIOS_Enter.htm") I came to.  You have to set your BIOS to boot from the optical device.  You should see some main subjects across the top of the bIOS screen - look for "Boot", enter that, look for Boot Device or Boot Order, set to CD or DVD device or however it identifies you optical drive.  Right now it's set to boot from the hard drive.  Save the change.  Make sure you saved it by going right back into BIOS - it's easy to think you made a change when you didn't.  Now the PC will look to the optical drive first and will recognize the Ubuntu CD.  Assuming that's been burned correctly.
Until you've accomplished that there's no point in asking about external drives or what have you.

---

### Post by Cairna on 2006-10-28
The boot order doesn't work, I ended up disabling the hard disk setup.

Seems the problem is the cd not working properly, I suspect the download didn't go down very well.


Thanks for the help, guys!

---

### Post by Cairna on 2006-10-28
It seems like now my only problem is that everytime I download 6.10 ubuntu for PC, it's always missing a file. 6.06 download won't even start through any of the server location :/ ( in the UK and US at least )

---

### Post by phunkizm on 2006-10-28
> **Cairna said:**
> Then my problem seems to be that that does not show up when the burnt CD is in the disk drive. It goes straight to the compaq screen, then to the windows screen giving me the option of Windows Recovery or WIndows XP Home Edition.
:-|



-Edit, my problem seems to be the BIOS settings now that I looked at your link, where do I go to change that?

edit(I don't know if this is the same problem, but the initial post seemed very similar to a problem I once had, so I'm going to post this for any of those who may come across this thread with this problem.)

When I was trying to set up a dual-booted system I found that Compaq has a small "recovery" partition right before the partition that holds Windows.  This partition detects that the partition table has been changed and forces the user to run a recovery, eliminating any changes that have been made.

My way of dealing with this:
Wipe it all out and do a clean install _without_ Compaq's provided software!  (But keep in mind that this will void your customer service warrantee).
And, of course, if you have any important data under Windows you should back it up onto a dvd or cd first.  The downside to this is that in order to have Windows again you're going to have to buy a fresh copy (the Windows that Compaq will give you will just install the recovery partition back).

---

