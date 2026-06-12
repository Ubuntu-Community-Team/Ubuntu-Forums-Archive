---
title: "printer driver for a Canon MP710"
date: 2007-08-15
forum: Absolute Beginner Talk
---

### Post by crazydiver on 2007-08-15
Hello eveyone,
   I am trying to get my printer to run with my computer but unfortunately my computer won't detect the printer. Can anybody help me here?

Best,
crazydiver

---

### Post by linuxwizard on 2007-08-15
I don't see your printer listed link below. Normally when a printer is not listed it is not supported and won't work. Look over the list and see if you can see it. If it was listed it would show recommended driver you need to install  I also did a quick search for your printer in the forum and seen no other posts on it.

[http://www.openprinting.org/printer_list.cgi?make=Canon](http://www.openprinting.org/printer_list.cgi?make=Canon)

---

### Post by Benbow on 2007-08-15
Do you mean MP170? If so it is not supported. Turboprint will print text and spot co;ours for a price but is hopeless at photos as it doesn't have the support for the printer with linux that canon gives xp.
I keep xp specifically for photographs and will change to HP printers when my canon is past it's sell by date.
Bonne chance

---

### Post by st33med on 2007-08-15
Canon is a headache for Linux. They specifically stated that they will not support Linux.

---

### Post by crazydiver on 2007-08-18
Thanks guys... damn... that's bummer!!!

---

### Post by crazydiver on 2007-08-18
I wonder if the model number is wrong. This printer is from Japan that was bought in Japan and sometimes, I notice that American Canon printers vs. Japanese Canon printers although they are the same, have different model numbers...

---

### Post by Benbow on 2007-08-18
"Canon is a headache for Linux. They specifically stated that they will not support Linux."

I know, and that is why after years of using canon printers, I no longer support them.

My choice, no company rules what I choose to do!
__________________

---

### Post by aikishugyo on 2008-02-06
I'm happy to state that despite the abysmal state of affairs with respect to Canon, when I received an MP710 as a gift, I took my problems to the gutenprint mailing list, an absolutely invaluable resource, and Sascha Sommer, the Canon inkjet printer driver developer/hacker managed to get the printer to work for me. This is about a year ago, so for a while the support was only in CVS, but after making sure both 300x300 dpi and 600x600 dpi support was working fine, the support is in the latest stable distributions too. The MP740 is the same except that it adds fax capability. I can also print CDs BTW.

Now I am working on getting SANE support for the included scanner, so I will at least be able to use (as will everybody else) the full capabilities under linux.

I also managed to garner support for the Epson PM-670C (Japanese model). I bought a PIXMA iP4500 two weeks ago as well but have not yet tried it. Sadly the Canon support is currently limited to 600x600 dpi and no edgeless printing, so I can only suggest to people to rather buy the epson G920 or G930 (can use the G920 driver) if they want really high quality printing under linux.

Best regards, Gernot

---

### Post by tad1073 on 2008-02-07
I found this "gutenprint-5.0.1-1lsb3.1.i486.rpm" but I can't remember where I got it from but it has alot of Canon printer drivers. i can't seem to get my network printer to print from ubuntu though so it is kind of useless now.

---

