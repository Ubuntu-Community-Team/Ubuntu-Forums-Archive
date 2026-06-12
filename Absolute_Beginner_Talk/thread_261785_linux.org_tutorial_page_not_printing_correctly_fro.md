---
title: "linux.org tutorial page not printing correctly from Firefox to HP PSC 950"
date: 2006-09-20
forum: Absolute Beginner Talk
---

### Post by patslap on 2006-09-20
Hi

I'm trying to print this page [http://www.linux.org/lessons/beginner/l15/lesson15a.html]("http://www.linux.org/lessons/beginner/l15/lesson15a.html")
but the text runs past the right-hand margin cutting words in half and missing the ends of lines. I can't scan the print-out becasue I'm having scanning problems, too - but that's for another day!

Can anyone help me out? I've tried the CUPS web-based printing frontend, but I couldn't get into the administration sections as it requires a password which I don't have (it didn;t accept my username and root password).
The printer friver I'm using is Hpijs (recommended) - HPLIP 0.9.7 (Suggested).

Thanks in advance.

patslap

---

### Post by Sef on 2006-09-20
Do you have this problem with only this site or other sites?

If it is only this site, then I suspect the problem lies with the site and not with your PSC.

---

### Post by patslap on 2006-09-20
Hmmmm - I'm not sure as the printer refrefuses to print anything now. I've tried cancelling print jobs, then printing again, bu the print job sits in queue. 

It also does this when trying to print a test page. ](*,)

---

### Post by Sef on 2006-09-20
I would uninstall the driver and reinstall this way:

System > Administration > Printing

---

### Post by patslap on 2006-09-20
I removed the printer, then aded it again - now it prints OK again.

but the problem remains with the tutorial on linux.org.

I tried several options in 'page setup' such as ticking  the 'shrink to fit page option' which seems to do nothing, and reducing the scaling to as little as 50%, which does reduce text size, so more text fits on one line, but it stills disappears off the edge of the margin, even though I have the margins set well within printable areas.

I've managed a workaround by printing these pages in Landscape orientation at 75% scaling ( in Page Setup ). This avoids the text being cut, but is not ideal as I would prefer portrait orientation.

---

### Post by mlalkaka on 2006-10-26
Did you try changing the margin settings in Firefox? Go to File > Page Setup... and click on the "Margins & Header/Footer" tab.

---

