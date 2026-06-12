---
title: "Dual booting - Help needed resizing partition + wireless broadband"
date: 2007-05-20
forum: Absolute Beginner Talk
---

### Post by srt5 on 2007-05-20
I have been using Ubuntu for some time and I am helping a friend make the switch from Windows XP to Ubuntu, he seems very interested in giving  Ubuntu Studio a try (since he enjoys his music and multimedia). However I have advised him to dual boot in-case he finds that Ubuntu is not for him.

My question is can anyone advise me on how to resize the windows XP partition on his computer to make space for Ubuntu (or indeed is this even possible)? This probably makes me seem ignorant but I didn't have to worry about this myself since I just dived straight in!

He has wanadoo broadband on his current machine, it comes with a weird-looking wireless adapter (which wasn't detected when I demonstrated Feisty's Live disk), can anyone tell me if ndiswrapper and the driver from the CD will be sufficient to get this device working?

Thanks :)

---

### Post by ajmorris on 2007-05-20
> **srt5 said:**
> I have been using Ubuntu for some time and I am helping a friend make the switch from Windows XP to Ubuntu, he seems very interested in giving  Ubuntu Studio a try (since he enjoys his music and multimedia). However I have advised him to dual boot in-case he finds that Ubuntu is not for him.

My question is can anyone advise me on how to resize the windows XP partition on his computer to make space for Ubuntu (or indeed is this even possible)? This probably makes me seem ignorant but I didn't have to worry about this myself since I just dived straight in!

He has wanadoo broadband on his current machine, it comes with a weird-looking wireless adapter (which wasn't detected when I demonstrated Feisty's Live disk), can anyone tell me if ndiswrapper and the driver from the CD will be sufficient to get this device working?

Thanks :)

To resize the NTFS partition in feisty's live disk, go to Start Menu >> System Tools >> Gnome Partition Editor.

Then once in there, right click on the NTFS partition and drag it down to the size required.

I hope this works for you, because when i did it on a friends laptop, feisty's Gnome Partition Editor issued wrong parameters for the 'NTFS resize' option, so i had to go into the terminal and manually resize the NTFS partition through 'ntfsresize.'

So 1) i hope this is not a bug in the live cd but just a weird error.
and 2) that if this is a bug, that you are able to use the CLI (terminal) :)

GOOD LUCK, if you do need help with the ntfsresize commands, don't hesitate to ask.

Also, if the resize fails, click details in the dialog box where the error happened, and get the details of the ntfs resize, it will tell you what parameters it used to try to resize the partition.

---

### Post by overdrank on 2007-05-20
> **srt5 said:**
> I have been using Ubuntu for some time and I am helping a friend make the switch from Windows XP to Ubuntu, he seems very interested in giving  Ubuntu Studio a try (since he enjoys his music and multimedia). However I have advised him to dual boot in-case he finds that Ubuntu is not for him.

My question is can anyone advise me on how to resize the windows XP partition on his computer to make space for Ubuntu (or indeed is this even possible)? This probably makes me seem ignorant but I didn't have to worry about this myself since I just dived straight in!

He has wanadoo broadband on his current machine, it comes with a weird-looking wireless adapter (which wasn't detected when I demonstrated Feisty's Live disk), can anyone tell me if ndiswrapper and the driver from the CD will be sufficient to get this device working?

Thanks :)

Hi you can find partitioning here
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)
And then broadband issue is different and not looking good at this link
[http://ubuntuforums.org/search.php?searchid=20557823](http://ubuntuforums.org/search.php?searchid=20557823)
Good luck and hope this helps!:popcorn:

---

### Post by srt5 on 2007-05-20
Thanks for the quick responses :) Some great advice there! I am hopefully taking another look at his system later today so I will print off some of this info. I'm sure I'll end up posting back here with some more queries though! Doesn't look good with the broadband, do you think that a different wireless adaptor to the one provided out of the box would be able to connect to the wanadoo router? (sorry I can't be any more specific as I do not know the model off hand).

Thanks again

---

### Post by srt5 on 2007-05-22
Okay, I've taken a closer look at my friend's system, Ubuntu is now installed alongside windows XP. The next step is to try and get his internet working...

His broadband provider is Wanadoo (although I think Orange may have taken over the company), he uses an Inventel UR054g (Revision 01) USB adapter in order to connect to his 'Livebox'.

This works fine for him under XP. However under Ubuntu it doesn't even show up under System > Administration > Network. Also, when I typed ```
lsusb
``` in the terminal, the terminal just hung there and seemed to freeze - does anyone know of an explanation for this?

I think I have found the drivers for this device. I think they are called PRISMA02.inf + .sys. Can anyone who has set up their broadband using this device tell me how they did it? Any help would be much appreciated. Will the ndiswrapper approach even work? And will I need to blacklist any modules?

Thanks :)

---

### Post by srt5 on 2007-05-22
Any suggestions?

---

### Post by zatarregaza on 2007-05-25
> **ajmorris said:**
> To resize the NTFS partition in feisty's live disk, go to Start Menu >> System Tools >> Gnome Partition Editor.

Then once in there, right click on the NTFS partition and drag it down to the size required.

I hope this works for you, because when i did it on a friends laptop, feisty's Gnome Partition Editor issued wrong parameters for the 'NTFS resize' option, so i had to go into the terminal and manually resize the NTFS partition through 'ntfsresize.'

So 1) i hope this is not a bug in the live cd but just a weird error.
and 2) that if this is a bug, that you are able to use the CLI (terminal) :)

GOOD LUCK, if you do need help with the ntfsresize commands, don't hesitate to ask.

Also, if the resize fails, click details in the dialog box where the error happened, and get the details of the ntfs resize, it will tell you what parameters it used to try to resize the partition.

It looks like I might need to try the ntfresize from the CLI too. I keep trying to resize my Vista partition and I get some error saying that filesystem is not recognized. I wouldn't think it has anything to do with the fact I'm running Vista on that partition, does it?
How exactly did you enter this command? What parameters? etc.

Thanks,
Joseph

---

### Post by dada12 on 2007-05-28
Hey, 

You should try PartitionMagic, download it from a torrent or buy it, whichever you prefer. 

1) Install on XP
2) Run Partition Magic, it'll allow you to non-destructively change the size of your Windows partition to make room for a Linux one.  I've used PM for close to 8 years and have never experienced a partitioning problem,

3) Install Ubuntu from the  CD, or DVD (if installing Ubuntu Studio)

Have fun!

---

### Post by dan171717 on 2007-05-29
> **zatarregaza said:**
> It looks like I might need to try the ntfresize from the CLI too. I keep trying to resize my Vista partition and I get some error saying that filesystem is not recognized. I wouldn't think it has anything to do with the fact I'm running Vista on that partition, does it?
How exactly did you enter this command? What parameters? etc.

Thanks,
Joseph


you cant resize vista in gparted at the mo the devs are working ona fix.

also i have a livebox and i cant use the wireless too. any ideas.

(i am using a belkin laptop card with ralilink rt2500 chipset

---

