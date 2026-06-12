---
title: "HDIO_SET_DMA failed: Operation not permitted"
date: 2005-08-22
forum: Absolute Beginner Talk
---

### Post by ROUBOS on 2005-08-22
hi people,
I'm trying to setup xine to watch DVDs and I've been told to enable DMA.

Been trying to that and I get "Operation not permitted"
I also entered the code at the end of my hdparm.conf file and rebooted with no success. can someone help me?

this is my hdparm.conf file:
#/dev/discs/disc0/disc {
# mult_sect_io = 16
# write_cache = off
# spindown_time = 240
#}

#/dev/discs/disc1/disc {
# mult_sect_io = 32
# spindown_time = 36
# write_cache = off
#}

#/dev/cdroms/cdrom0 {
# dma = on
# interrupt_unmask = on
# io32_support = 0
#}

#/dev/hda {
# mult_sect_io = 16
# write_cache = off
# dma = on
#}

#command_line {
# hdparm -q -m16 -q -W0 -q -d1 /dev/hda
#}

/dev/cdrom {
dma = on
}

---

### Post by heimo on 2005-08-22
Have you seen this?
[https://wiki.ubuntu.com/DMA](https://wiki.ubuntu.com/DMA)

---

### Post by ROUBOS on 2005-08-22
I read it, and I checked the CDROM drive, it's set to master.
So I don't know what else might be the problem...

---

### Post by heimo on 2005-08-22
See the Troubleshooting section and /etc/modules file.

---

### Post by ROUBOS on 2005-08-22
Keep getting "operation not permited"

When it says "amd74xx" do I replace the "xx" with a number?
and do I also need to put in the Via chipset one?

AMD64 3500+ is what I have

---

### Post by tseliot on 2005-08-22
[QUOTE=heimo]See the Troubleshooting section and /etc/modules file.[/QUOTE]

Or/and if you can't solve the problem (though I hope you do) you can compile a new kernel with DMA enabled by default. It's all explained in my HOWTO if you wish. It's for newbies and it's easy.

[http://www.ubuntuforums.org/showthread.php?t=56835](http://www.ubuntuforums.org/showthread.php?t=56835)

---

### Post by heimo on 2005-08-22
What motherboard do you have? Link to manufacturers specs sheet would be great. The line you add reflects the chipset on your motherboard.

---

### Post by ROUBOS on 2005-08-22
I added the AMD74xx and the via...
and it works. :)

Should I enter some values to "xx" though?

AMD64 3500+ socket 939
and mobo is the ASUS A8V Deluxe

chipset
via k8t800Pro
via vt8237

---

### Post by heimo on 2005-08-22
[QUOTE=ROUBOS]
Should I enter some values to "xx" though?
[/QUOTE]

No xx is part of the modules name. And I believe you can remove AMD74xx

---

### Post by ROUBOS on 2005-08-22
OOPS, I just restarted and DMA is not enabled.. .do I have to enable it everytime?

---

### Post by heimo on 2005-08-22
[QUOTE=tseliot]Or/and if you can't solve the problem (though I hope you do) you can compile a new kernel with DMA enabled by default. It's all explained in my HOWTO if you wish. It's for newbies and it's easy.

[http://www.ubuntuforums.org/showthread.php?t=56835]("http://www.ubuntuforums.org/showthread.php?t=56835")[/QUOTE]

Hi tseliot! :D I had to use this opportunity to take off my hat to you, seen your excellent Howtos. Great work.

---

### Post by heimo on 2005-08-22
[QUOTE=ROUBOS]OOPS, I just restarted and DMA is not enabled.. .do I have to enable it everytime?[/QUOTE]

No. Hopefully I didn't instruct you to remove wrong module. Anyway, to automate enabling DMA, you edit /etc/hdparm.conf. That should do it during boot. Could you run:

 ```
ls -l /dev/cdrom
``` 
If you see hda, enable that section of hdparm.conf too (take off # signs from the beginning of lines on that section). EDIT: Or which ever is your DVD device.

---

### Post by ROUBOS on 2005-08-22
ls -l /dev/cdrom
gives me :

lrwxrwxrwx  1 root root 3 2005-08-22 19:22 /dev/cdrom -> hda


and here is my hdram.conf file:

#/dev/discs/disc0/disc {
#	mult_sect_io = 16
#	write_cache = off
#	spindown_time = 240
#}

#/dev/discs/disc1/disc {
#	mult_sect_io = 32
#	spindown_time = 36
#	write_cache = off
#}

/dev/cdroms/cdrom0 {
	dma = on		   
	interrupt_unmask = on
	io32_support = 0
}

/dev/hda {
	mult_sect_io = 16
	write_cache = off
	dma = on
}

command_line {
       hdparm -q -m16 -q -W0 -q -d1 /dev/hda
}

/dev/hda {
	dma = on
}

/dev/cdrom {
	dma = on
}


But it does not work... need to run sudo hdparm -d1 /dev/hda to set it everytime :-?

---

### Post by tseliot on 2005-08-23
[QUOTE=heimo]Hi tseliot! :D I had to use this opportunity to take off my hat to you, seen your excellent Howtos. Great work.[/QUOTE]
Thanks, I really appreciate your kindness.

---

### Post by heimo on 2005-08-23
[QUOTE=ROUBOS]
/dev/hda {
    mult_sect_io = 16
    write_cache = off
    dma = on
}
[/QUOTE]

Try commenting out (put # signs on beginning of other rows) everything else in hdparm.conf except the first /dev/hda section.

After boot, run *dmesg | less *and search for any errors, anything related to DMA and hdparm.

---

### Post by ROUBOS on 2005-08-23
HI, thanks... that seems like it works... fixed it...

thanks alot for your help guys..

(I thought I tried that before)... hmmm

I'm happy anyway  :razz:

---

### Post by heimo on 2005-08-23
Wow, great. :cool:

---

