---
title: "failed at first hurdle"
date: 2007-02-04
forum: Absolute Beginner Talk
---

### Post by heatrag on 2007-02-04
To give you an idea of what you are up against in my booting from the ubunto disc it took me two days to get into the BIOIS because of not realising that there's another delete key other than the one above the return.
So far then I can get to the options, Install, memory test, start from first hd etc. but after I try to install it hangs. It lists a number of items as being 'ok' then goes to a blank screen with 'Uncompressing Linux... Ok, booting the kernel' across the top in white text. My system runs XP fine its 1200 mgz with 128 of RAM

While I've typed this I ran it again and for the first time i'm getting an error message repeated numbers followed by... 
'Buffer I/O error on device hdc, logical block 254574'

What next? 

I'm so keen to get this up and running.
Thanks Richard

---

### Post by shareMenaPeace on 2007-02-04
I got same error and waiting like 2 mins didnt kept ubuntu from booting.

When you burn the iso image make sure to burn on 4x speed and verify the data.

---

### Post by shareMenaPeace on 2007-02-04
And you might want to install xubuntu as min requirement for ubuntu is 256 ram. 


[http://xubuntu.com](http://xubuntu.com)

---

### Post by heatrag on 2007-02-04
I didn't burn the cd it was mailed.

---

### Post by heatrag on 2007-02-04
I thought that but it does say on the disc (FI then F2 keys) 128mg RAM to use this ubunto live system.
I'm gonna try xubunto though, thanks a load for the advice.
r.

---

### Post by heatrag on 2007-02-04
Ahh.. the pennys dropped,
128 to run and 256 to install. I usually get there it just takes time.

---

### Post by riven0 on 2007-02-04
> **heatrag said:**
> 

While I've typed this I ran it again and for the first time i'm getting an error message repeated numbers followed by... 
'Buffer I/O error on device hdc, logical block 254574'



You can do the xubuntu cd, or else, just do a regular server install and download your desktop of choice later. However, the logical block error always means a corrupted cd. I've had it happen to me before.

---

### Post by heatrag on 2007-02-06
Thanks.
Server instal?
What I have done is downloaded on my other computer (Mac) xubuntu-6.06.1 -desktopi386.iso and burnt it (X4) to disc. I loaded it in my PC, changed first boot to CDROM in the BIOS but it starts windows. The ubuntu disc opened with the same settings to a menu why won't xubuntu?  
There is a sbm.bin on the disc that it says copy onto a floppy and start from that by passing the BIOS but it's 144mb and there only seems to be 138mb useable on a 3.5in floppy even though it says 144 on the case. (first time I've ever used one)
Am I going to have to give up?

---

### Post by Happy_Man on 2007-02-06
Are you sure you buned it as an .iso? I'm not sure how it works on the Mac (I'm a Windows convert), but look around on these forums for instructions. Usually if you burned the CD slow enough and it still won't boot, that's the problem.

---

### Post by xpod on 2007-02-06
You could try an alternate cd for installing and on those specs you might just find things a bit easier going than a live cd.
You wont be able to try any live session like you can from the live cd but it can sure save a lot of install headaches.

Just a thought if all else is failing.:) 
I`m off to bed so good luck and dont be put off by any hurdles you might initially come across.It`s all good learning along the way......as long as your willing to learn that is:) 

Sorry, but some give up without ever really trying and THAT is a pity.

---

### Post by heatrag on 2007-02-07
Yep alternate cd sounded just the job. I've downloaded it 682.9 MB however when I go to burn it  it tells me there is not enough free space (new cd's capacity 670, available 660.7.) the same thing happened when I downloaded ubuntu that's why I've got a mailed copy. Is it a problem with my burner? Mabe there's files on there that are surplus I can delete

No chance of me giving up yet, it's becoming obsesive, this isn't going to beat me.

---

### Post by riven0 on 2007-02-07
> **heatrag said:**
> Yep alternate cd sounded just the job. I've downloaded it 682.9 MB however when I go to burn it  it tells me there is not enough free space (new cd's capacity 670, available 660.7.) the same thing happened when I downloaded ubuntu that's why I've got a mailed copy. Is it a problem with my burner? Mabe there's files on there that are surplus I can delete

No chance of me giving up yet, it's becoming obsesive, this isn't going to beat me.

Oh! I forgot to add there is one last thing you can do in case you can't partition: boot back up to XP, go to the Run dialog and run: **chkdsk /f**

You may have to reboot to complete the check disk. There is the possibility that your hd is locked by the windows bootloader, which will prevent partitioning. chkdsk /f should unlock it.

---

### Post by heatrag on 2007-02-07
i'm booted up and can't find out how to get to run dialog, sherching help didn't help either.
Thanks for your trouble.

---

### Post by riven0 on 2007-02-07
> **heatrag said:**
> i'm booted up and can't find out how to get to run dialog, sherching help didn't help either.
Thanks for your trouble.

The run menu should be listed in the Start menu. If not, try opening up Task Manager, (CTRL + ALT + Del), go to **File** and choose **Run**.

---

### Post by heatrag on 2007-02-07
yep done and I'm afraid it couldnt find it. I'm running windows ME by the way.

---

### Post by steve.horsley on 2007-02-07
> **heatrag said:**
> Yep alternate cd sounded just the job. I've downloaded it 682.9 MB however when I go to burn it  it tells me there is not enough free space (new cd's capacity 670, available 660.7.) the same thing happened when I downloaded ubuntu that's why I've got a mailed copy. Is it a problem with my burner? Mabe there's files on there that are surplus I can delete

No chance of me giving up yet, it's becoming obsesive, this isn't going to beat me.

I think you are burning it wrong. You need to burn the .iso file **as an image**. Most burning programs have a special menu option or special behaviour specifically for .iso **image** files. If you burn it properly, you will end up with a bootable CD with lots of files and directories on it, very like the desktop installer CD you already have.

The "alternate" installer is the one you want. It  installs a full system (the server installer doesn't install a GUI), but does it in text mode to it doesn't need so much RAM.

---

### Post by heatrag on 2007-02-07
I've now burnt it as per [https://help.ubuntu.com/community/BurningIsoHowto#head-c870784c85d881b96b985bb6f47720add24f13d0](https://help.ubuntu.com/community/BurningIsoHowto#head-c870784c85d881b96b985bb6f47720add24f13d0)
Your right I was burning it incorrectly, the same way i usually burn, drag and drop without using the disc burning utility.
Us Mac users are so lazy we never have to think about anything other than using them for what it's ment for, computing! I've not had a hobby computer befor.
I dead chuffed now and can't wait, its installing this very moment. 6% and waiting, oh 18% now.
Thanks for all the help, r.

---

