---
title: "installing canon i560 on ubuntu6.0 edgy eft"
date: 2007-05-24
forum: Absolute Beginner Talk
---

### Post by ibidnah on 2007-05-24
ubuntu 6.0 edgy eft printer install wizard has three screens. Ist time thru some months ago installing i560 canon, i went to linus printing.org, I think and somehow found a CUPSYS command that allowed i560 to start working. then print head went bad on canon i560, so I took it off line,replaced print head, and tried to install. Forgot where in linux printing site the download was that will allow the printer to work so....

 trouble is: screen #2 calls for finding yer printer on down list for canon and i560 isn't on there, third screen calls for ppd file and thru a number of calls for help, phillipe answered and said type in driver" Canon-i560-bj8pa06n.upp.ppd." I added ppd when caveat screen said put ppd on the end or it won't take. so all this led to a phantom print command running a complete cycle( you can hear it and feel the cycle starting and ending inthe printer). for job queue printing but no output at all. so i called canon rep and he told me how to independently test printer by holding down right restart button on printer. so the printer works ok test page came out.

Under System and Services, i checked and scrolled down and found two printer system cues, one for CUPS and one for Hiypic or something and made sure CUPS was checked.when i alternated back and forth between these two starter print command interfaces, the printer icon came into view in the top of screen and when i clicked off on Hiypic whatever, the print cue icon went away.

When i went to ubuntu wiki printing print site, an administrator mentioned that canon i560 was a no brainer installation and that you used a S630 driver. later in another communication post someone installed an i550 using an I-8200 driver and that worked. 

anyway I am held up in getting things going by the lack of an entry for canon i560 on the drop down menu for printer ident. on page two of Ub's 6.0 Edgy eft. and can;t find the CUPSYS auto download driver in linux printing. org. i used before to make canon i560 work?

thanks,

fred

---

### Post by dstew on 2007-05-24
Use the driver named bj8pa06n.upp. It should be in the foomatic package, which is obtained by Synaptic Package Manager. Install the printer as a CUPS local printer, and you should be able to select this driver for the i560. See the [foomatic page for this printer]("http://openprinting.org/show_printer.cgi?recnum=Canon-i560").

How is your printer connected? Is it on a USB port, or on a parallel port? Make sure you pick the correct port on the drop-down menu on the first page. DO NOT pick the "hp" type of port.

---

