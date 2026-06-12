---
title: "Something is wrong with my Brother HL-760"
date: 2005-12-12
forum: Absolute Beginner Talk
---

### Post by carlossaatana on 2005-12-12
I have installed my printer Brother HL-760 into LPT1. I have added it via System -> Admistration ->Printing but it is not in my device manager. What should I do?

---

### Post by qiemem on 2005-12-12
[http://www.linuxprinting.org/show_printer.cgi?recnum=Brother-HL-760]("http://www.linuxprinting.org/show_printer.cgi?recnum=Brother-HL-760")
There ya go! Sounds like it doesn't work perfect, but this should get you by.
For future reference, [http://www.linuxprinting.org/](http://www.linuxprinting.org/) is the place to go for printer info. Also, I found this by going to the [ubuntu wiki documentation]("https://wiki.ubuntu.com/UserDocumentation") and looking for printer info. This is a great reference for getting ubuntu all set up (combined with the [faq]("http://help.ubuntu.com/starterguide/C/faqguide-all.html").)

---

### Post by carlossaatana on 2005-12-12
Now I maybe know what is wrong. In the options of my HL-760 port is set to Paraller Port #1(CANON) allthough my printer is connected to LPT1. There is not LPT1 in that list, how I can add it there?

---

### Post by qiemem on 2005-12-12
Options where? In the properties of the printer or in the setup or what?
If its in the properties, do you mean the Location? That should be blank...

---

### Post by carlossaatana on 2005-12-12
Sorry I got finnish version of Ubuntu and I do not know what are correct english words for these. But I mean that in my device manager there is not LPT1 at all. Should I add it there some way? If yes, please tell me how.

---

### Post by qiemem on 2005-12-12
Oh hey no worries...
Okay, now I see what you're talking about, but I don't think you have to add it (I'm new at this too, so I'm not certain.)
If you go System->Administration->Printing, is it listed there? What happens when you try to print a test page? (Right Click->Properties->Print test page)
Sorry I don't know Finnish :) Also, tell me if I'm being too basic.

---

### Post by carlossaatana on 2005-12-12
LPT1 is not listed there, I really don't know why. When I click "print test page" it sends test page to my printer(apparentely) but my printer does not react at all. I think it is trying to send it through COM1 or COM2 and that is not what I want.

---

### Post by qiemem on 2005-12-12
LPT1 won't be listed there (in the Printers window), the name of the printer itself will. What is listed there?
Did you install the correct drivers for the printer?

---

### Post by Delkster on 2005-12-12
LPT1 is the parallel port.

Unfortunately I can't say off-hand what could be wrong and what you need to do to get it working since I don't know about Brother printers and have never used one.

---

### Post by carlossaatana on 2005-12-13
Oh sorry I thought that paraller port means COM1 or COM2. And yes I have installed Brother HL-760 PPD-file. But still my printer isn't reacting at all when I try to print e.g test page. 

In my printer windows there is HL-760 as it supposed to be. But when I right click this very printer and click option/properties. Appearing dialog I click connection tab. Here is printers port(or something like that, I think I should install Ubuntu in english, would be much easier and better). And there is listed Paraller port #1 and Paraller port#1(CANON) and Paraller port #1(EPSON). Is it important to select correct choice here? If yes, what it will be?

---

### Post by carlossaatana on 2005-12-13
Yeah now my printer is working. Thanks for everybody.

---

### Post by gogamga on 2005-12-27
What did you do to make it work.
I have the same problem with my Lexmark z42

---

