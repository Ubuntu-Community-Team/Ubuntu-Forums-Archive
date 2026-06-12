---
title: "printer setup"
date: 2006-10-27
forum: Absolute Beginner Talk
---

### Post by STREETURCHINE on 2006-10-27
hi all, have been trying to set up my printer no for about 2 weeks and i have had it,
 i have a canon mp110 ,have read just about all the tutorials ,i ron the foo setup wizard(or what ever its called) it recomends a driver i click install it then tells me to open a ppd file.
 whats a ppd file where do i find one that works,i have found files with ppd in them but when i click on them to open nothing happens ,
so if some one out there can give me a step by step tutorial i would be eternally gratefull.  ](*,)  ](*,) 

                 thanks heaps :-D

---

### Post by lazyart on 2006-10-28
Here's a thread for you:

[http://ubuntuforums.org/showthread.php?t=76184](http://ubuntuforums.org/showthread.php?t=76184)

Search the forums for "mp110" and you might find a few more helpful threads. :)

---

### Post by STREETURCHINE on 2006-10-28
as i said i have spent 2 weeks looking at these sites ,i have been to most twice but i am just going round in circles,i have tried the link you posted it dosnt work,but thanks for the effort,
 i must say this has been the biggest problem i have faced and the most frustrating,if i cant fix it soon i will have to go back to windows,because i need the printer for my work. 
   so any body help please](*,)  ](*,)

---

### Post by steven8 on 2006-10-28
I added my printer by going to System>Administrative(?)>Printing

It open a window with an Add Printer icon.  I clicked it, it told me the printer I have connected, I clicked Okay, opted to NOT click the Install Driver, since it already called it by name.  I just went with okay to the end.  It came up with an icon for my printer and said it was ready.

Have you gone the System>Administrative>Printing route?

---

### Post by STREETURCHINE on 2006-10-28
yes i have the printer icon it tells me it is ready,when i fininish my reportand hit print it tells me it is in the cue, the printer tells me it is printing but nothing gets printed.

---

### Post by steven8 on 2006-10-28
It throws no errors?  Paper or otherwise?

---

### Post by STREETURCHINE on 2006-10-28
no errors no paper nothingit is now telling me there are two jobs,which is correct,the screen on the printer says printing,but no paper coming out with my scribbles on them,i figure it is a driver problem but the computer recognises it as soon as it is turned on,i am bamboozled

---

### Post by steven8 on 2006-10-28
This may sound funny, and is a tad archaic, but I have some OLD machines in my basement that I fiddle with.  I was setting up an old HP DeskJet 6P in Win3.1 the other day, to print stuff from Word 2.0.  And it just wouldn't work.  Windows saw the printer and all, and the printer seemed fine, but it just wouldn't print.  I had to go into the printer set-up and tell it that the paper was being fed manually and not by a paper cartridge.

Check your printer set-up (properties) to make sure they are okay.

---

### Post by STREETURCHINE on 2006-10-28
i have checked in settings ,and under connections it has no printer detected,and it keeps swapping to network printer instead of local ,so this could be where the problem is ,but the setup wizard detects the printer and calls it local

 under printer status it says;usb printer is busy retry in 5 seconds but that seems to be stuck

---

### Post by steven8 on 2006-10-28
This will sound lame, but trying turning your printer off and back on.

---

### Post by STREETURCHINE on 2006-10-28
yep done that (about 100 times today)
 managed to get all the fields full ,got it to detect my printer but no joy,
 well been at it for 6 hours today time for a break. 
by the way as i posted earlier steven8 i have a 512 ddrll-533 ram memory stick here if you want it,just leave your address and i will post out
 ps// thanks for your help i have 1 week to get my printer online or i will have to go back to windows ,and that my friend is a bugger.

---

### Post by steven8 on 2006-10-28
Oh yes, I'm sorry.  I forgot that.  Unfortunately, I have no machine that uses ddr2 ram.  Thanks though!

I'm sorry we haven't got your printer running.  Have you tried the canon website to see if they have any info?

I don't want you to have to go back to windows.  I'll do some more searching to see what I can find.  You go get some rest!!

---

### Post by steven8 on 2006-10-28
I found this link in another thread that says it has a driver for your printer:

[http://freshmeat.net/projects/turboprint/?branch_id=14276&release_id=207484]("http://freshmeat.net/projects/turboprint/?branch_id=14276&release_id=207484")

---

### Post by STREETURCHINE on 2006-10-28
no worries on the memory chip ,any one want it its there's,yes i down loaded the drivers from that site ,it is one of those things,i went and bought a lap top with winows on it so i can print out my docs so my desktop is now totally ubuntu and my laptop windows,solved that problem

---

### Post by steven8 on 2006-10-28
I went to the Canon website.  That model is in the archives (like most of my hardware.) and they have drivers for win95 and up and MacOSX, but no linux at all. :-(

Was that a real driver or some virtual thing that we linked to back earlier?

Glad you got the windows laptop to print with, though!!  That's cool.

---

### Post by STREETURCHINE on 2006-10-28
im not sure about the drivers,i have installed just about everyone there is and none work,but one has to eventually ,i have read some posts on here that say they got there mp110 working with linux.
i dont know why the companies dont bring out there printers wiyh drivers for linux it would be so much easier:p

---

### Post by steven8 on 2006-10-28
But not profitable enough. :-(

I saw a thread where, a user shutdown their computer, turned on their printer, then turned on the computer, booted into ubuntu, and it saw the printer and it worked okay!  Have you tried that one yet?

---

### Post by rplantz on 2006-10-28
I had some problems with printers when I first started using Ubuntu. (It was Hoary Hedgehog.)

I have two usb printers, a Samsung laser and Epson inkjet. Here are the steps I did to get them installed:

1. I used System->Administration->Printing to remove my printers.
2. I plugged in both printers and turned them on.
3. Then from System->Administration->Printing I did Printer->Add Printer.

It found my printers. I selected "Use a detected printer:"

4. Click on Forward. It correctly named my printer and gave a recommended driver. DO NOT click on "Install Driver."

5. Click on Forward. Name the printer. I just left the default there, which was my printer's model number.

6. Click on Apply.

That did it for me.

---

### Post by STREETURCHINE on 2006-10-28
> **rplantz said:**
> I had some problems with printers when I first started using Ubuntu. (It was Hoary Hedgehog.)

I have two usb printers, a Samsung laser and Epson inkjet. Here are the steps I did to get them installed:

1. I used System->Administration->Printing to remove my printers.
2. I plugged in both printers and turned them on.
3. Then from System->Administration->Printing I did Printer->Add Printer.

It found my printers. I selected "Use a detected printer:"

4. Click on Forward. It correctly named my printer and gave a recommended driver. DO NOT click on "Install Driver."

5. Click on Forward. Name the printer. I just left the default there, which was my printer's model number.

6. Click on Apply.

That did it for me.

 thanks we have tried that but i tried it again with the same result.
 printing i job...on the printer screen it says printing ,but no paper coming out with my scribble on it

---

### Post by STREETURCHINE on 2006-10-28
> **steven8 said:**
> But not profitable enough. :-(

I saw a thread where, a user shutdown their computer, turned on their printer, then turned on the computer, booted into ubuntu, and it saw the printer and it worked okay!  Have you tried that one yet?

yes i tried that several times it just dont do nuttin but thanks for you effort i havnt given up getting it to work on linux ,now i have the lap top it is not so important ,but i will try all ideas over andover andover  :D

---

### Post by steven8 on 2006-10-29
Oh phooey!  I'll keep looking for new ideas, and you keep us posted  on your progress!

---

### Post by STREETURCHINE on 2006-10-29
thanks mate , may just have to go to turbo print and pay for drivers,although they are quite pricey ,but might be easier than going out and buying printers till i find one that works with linux..:p

---

