---
title: "How do I Get Ubuntu on A &quot;Special&quot; Computer"
date: 2008-02-09
forum: Absolute Beginner Talk
---

### Post by gulliccj on 2008-02-09
I own a very specical laptop. by special, i mean it has no CD drive, no place for a CD drive, no floppy drive (also no plac for one), and an encripted BIOS. Normally, i would have wiped the BIOS, but i cannot find the watch-like battery. (there is also no OS) Is there any way else to reset a bios besides taking out the battery. PLEASE HELP ME! :confused:

---

### Post by LaRoza on 2008-02-09
Help you do what?

How did you get this laptop? 

Also, give the model name and hardware it has.

Why do you want to reset the BIOS?

---

### Post by dansco on 2008-02-09
if there is no cmos battery the BIOS is probably  on an eprom 
no idea about how to change it but here some info

[http://en.wikipedia.org/wiki/EPROM](http://en.wikipedia.org/wiki/EPROM)

---

### Post by ve9gj on 2008-02-09
If you are trying to install Ubuntu on a note book with no cdr or floppy and a totally empty hard disk (no OS) you will have to boot from a USB device or a network (PXE boot).  A network boot requires a boot server to be on the same local network.  A typical example is at [http://wiki.koeln.ccc.de/index.php/Ubuntu_PXE_Install](http://wiki.koeln.ccc.de/index.php/Ubuntu_PXE_Install)

Knoppix actually makes this very easy.  Boot a  knoppix cd on any old PC and activate the knoppix boot server.  Now boot the "cd less" pc and get it to boot from the network and it will boot knoppix also.  You then have acces to the hard drive.  

Ask for details if you want to try this route.

Glenn

---

### Post by gulliccj on 2008-02-10
First Of all, this is a Dell Latitude C400. 
I got it from my Dad's Work (locheed Martin) after they moved. it has a 40 GB hard drive and 512 Mb of RAM. I would also love to boot from a network or a USB drive, but the BIOS is password protected and i cannot find the battery. Should i take it to a pro?  

NOTE: the BIOS says it is vertion A12. Don't know what that means.

---

### Post by gulliccj on 2008-02-10
Oh, wiping the BIOS would be a nice start for help.

---

### Post by gulliccj on 2008-02-10
I want to restart the BIOS so i can boot from a USB device. The config is locked by a password, so i can't change any boot options.

---

### Post by kryth on 2008-02-10
Dig around here or call Dell support. 

[http://support.dell.com/support/edocs/systems/latc610/en/index.htm](http://support.dell.com/support/edocs/systems/latc610/en/index.htm)

---

### Post by topsites on 2008-02-10
Why not just ask the guy who owned it before?

Because I'm not so sure I like the sounds of this...

---

### Post by kryth on 2008-02-10
was the H/D formated? If it wasn't sometimes Dells have a hidden restore partition. Try holding down or hitting down one of the F* keys ie. f3 or f4.  If i boot my dell and hold f3 it will restore my h/d to factory new.

---

### Post by hyper_ch on 2008-02-10
[https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)

---

### Post by amingv on 2008-02-10
Also you can take out the hard-drive and install it on any other compatible laptop.

Do you even have the service tag number or anything?

---

### Post by Jerry N on 2008-02-10
> **gulliccj said:**
>  Is there any way else to reset a bios besides taking out the battery. PLEASE HELP ME! :confused:

On a motherboard for a desktop computer there is a usually jumper change that will allow you to clear the BIOS settings.  Possibly on your laptop there is a reset button somewhere, like in the battery chamber.  Maybe the manufacturer can provide a users manual or a setup manual.  Note:  I have seen what looks like some confusion on this forum about clearing the BIOS settings and think it needs to be pointed out that using the battery or the jumper to clear the BIOS RAM is in no way the equivalent of "flashing" or upgrading the BIOS.

Jerry

---

### Post by gulliccj on 2008-02-10
I have removed the BIOS battery, but how long does it have to stay out, and what else do i have to do?
:confused::confused::confused:

---

### Post by gulliccj on 2008-02-10
i have removed the BIOS battery, now what?

---

### Post by moshuptrail on 2008-02-10
I doubt removing the battery will restore the BIOS to factory defaults.  If it were that easy, then why have a password in the first place?  Your laptop was designed to be highly secure if it fell into the "wrong" hands.  Contents of the HD are probably encrypted if they have not been wiped.  I think your best bet would be to find a similar laptop and swap the HD into that, install Ubuntu, and then back to your laptop.  Failing that would it be possible to take it back to the authority at Lockheed who released it in the first place?  Someone had to authorize taking it out of service and turning to civilian duty.

---

### Post by s3a on 2008-02-10
Buy a 2.5 inch hd usb 2.0 enclosure go to a desktop, install ubuntu, then put the hd back that's what I did on my brocken optical drive laptop. ;) VERY EASY! (The hardest part is disassembling the laptop...if you consider that hard)

---

### Post by gulliccj on 2008-02-10
i do nat own or have access to a laptop with a compatible HDD slot. How else can i get an OS on it?

---

### Post by Ptero-4 on 2008-02-10
Actually, any PC (as long as it's a PC and not a M$C) will do. Just stick your "laptop" HD in a 2.5" enclosure, install ubuntu and then put the disk back. Ubuntu is (AFAICT) quite good at redetecting hardware changes and shouldn't bother you with problems due to the different HW (except perhaps X11, but a quick edit of your xorg.conf sets it right).

---

### Post by moshuptrail on 2008-02-10
s3d has an excellent idea.  buy a little USB HD.  But that depends on the laptop being able to boot from a USB drive.  I'm not sure what he meant about taking apart the laptop.
But, wait 24 hours and check the BIOS.  Maybe it'll let you in!  Worth a try.

I think what he's saying is that most any 2.5" hd will work.
You could even pick up a laptop with a good hd on eBay for low$ if the screen was broken or something like that.

---

### Post by moshuptrail on 2008-02-10
Check this out...
[http://cgi.ebay.com/Dell-Inspiron-1000-for-Parts-or-Repair_W0QQitemZ140205603357QQihZ004QQcategoryZ140080QQssPageNameZWDVWQQrdZ1QQcmdZViewItem](http://cgi.ebay.com/Dell-Inspiron-1000-for-Parts-or-Repair_W0QQitemZ140205603357QQihZ004QQcategoryZ140080QQssPageNameZWDVWQQrdZ1QQcmdZViewItem)

---

### Post by dstew on 2008-02-10
There is also netboot, if the BIOS is PXE-enabled. See [http://ubuntuforums.org/showthread.php?t=690483](http://ubuntuforums.org/showthread.php?t=690483)

---

### Post by the_sorrow on 2008-02-10
Dude I think you should go with the enclusere idea, because it's safer and faster, and you will not have problems when transfering back to your laptop.

---

### Post by gulliccj on 2008-02-10
will this HDD fit into a standard computer? [CLICK HERE FOR PIC]("http://www.bvrradio.110mb/images/hdd.jpg"). I really don't really want to take my computer apart. a better picture will be here soon

---

### Post by gulliccj on 2008-02-10
sorry the link did not work. Here it is: [CLICK HERE]("http://www.bvrradio.110mb.com/images/hdd.jpg")

---

### Post by paintba||er on 2008-02-10
It still doesn't work...

---

### Post by gulliccj on 2008-02-10
okay, now that the links don't work, here's the PIC:

[IMG]http://bvrradio.110mb.com/images/hdd.jpg[/IMG]

---

### Post by gulliccj on 2008-02-10
i am really angry. [HERE IS A NEW LINK TO A PRO'S SITE]("http://www.adapturl.com/uploads1/products/img2/182281_1157063975.jpg")

---

### Post by gulliccj on 2008-02-10
[IMG]http://www.adapturl.com/uploads1/products/img2/182281_1157063975.jpg[/IMG]

---

### Post by Jon Monreal on 2008-02-10
> **gulliccj said:**
> i am really angry. [HERE IS A NEW LINK TO A PRO'S SITE]("http://www.adapturl.com/uploads1/products/img2/182281_1157063975.jpg")
Stay calm.

That is a 2.5" Hard Drive, meaning that it will not fit in a desktop computer.

What the other posters have been suggesting is that you buy a 2.5" Hard Drive Enclosure with USB support and you use the desktop computer to install Ubuntu on that Hard Drive, and then you put the Hard Drive back into the laptop.

Hope this helps.

---

### Post by gulliccj on 2008-02-11
where can i buy this 2.5" Adapter. Does Anyone Know?????

---

### Post by whazooo on 2008-02-11
Sorry Wrong thread

---

### Post by dstew on 2008-02-12
> where can i buy this 2.5" Adapter. Does Anyone Know?????[Here]("http://shopping.yahoo.com/p:Ultra%20Products%20Ultra%20USB%202.0%202.5-inch%20Hard%20Disk%20Drive%20Enclosure:1991997307") is an example.

---

### Post by dansco on 2008-02-16
Here  is another option

[http://www.maplin.co.uk/Module.aspx?ModuleNo=37602&doy=16m2&C=SO&U=strat15](http://www.maplin.co.uk/Module.aspx?ModuleNo=37602&doy=16m2&C=SO&U=strat15)

---

### Post by seventhc on 2008-02-16
Removing the battery will reset it to factory defaults. I have used this method before on a friends computer.
The thing is, it can take up to an hour before it defaults back. I suggest removing the battery and just let it sit for at least an hour just to be safe. Then the password should be gone.

---

### Post by gulliccj on 2008-02-25
WHOOPEEEEEEEEEEEEEEEEEEEEEE! AFTER 6 MONTHS OF TOILS, TEARS, SCREAMING, BANGING OADS, CALLS TO EVRYONE....I FINALLY HAVE AN OPERATING SYSTEM ON MY LAPTOP!!!!!!!!!!!!!!!! GUESS WHAT IT IS... IT IS UBUNTU 7.10: GUTSY GIBBON. I WANT TO THANK EVERYONE HERE FOR THEIR HELP. YOU WERE ALL AWSOME!

:KS:KS:popcorn::guitar::):):):)

---

### Post by JoshuaRL on 2008-02-25
> **gulliccj said:**
> WHOOPEEEEEEEEEEEEEEEEEEEEEE! AFTER 6 MONTHS OF TOILS, TEARS, SCREAMING, BANGING OADS, CALLS TO EVRYONE....I FINALLY HAVE AN OPERATING SYSTEM ON MY LAPTOP!!!!!!!!!!!!!!!! GUESS WHAT IT IS... IT IS UBUNTU 7.10: GUTSY GIBBON. I WANT TO THANK EVERYONE HERE FOR THEIR HELP. YOU WERE ALL AWSOME!

:KS:KS:popcorn::guitar::):):):)

+1 for Ubuntu and FOSS!

---

### Post by stalkingwolf on 2008-03-03
> **gulliccj said:**
> WHOOPEEEEEEEEEEEEEEEEEEEEEE! AFTER 6 MONTHS OF TOILS, TEARS, SCREAMING, BANGING OADS, CALLS TO EVRYONE....I FINALLY HAVE AN OPERATING SYSTEM ON MY LAPTOP!!!!!!!!!!!!!!!! GUESS WHAT IT IS... IT IS UBUNTU 7.10: GUTSY GIBBON. I WANT TO THANK EVERYONE HERE FOR THEIR HELP. YOU WERE ALL AWSOME!

:KS:KS:popcorn::guitar::):):):)

Perhaps you could post the steps you took to get your install for others?

---

