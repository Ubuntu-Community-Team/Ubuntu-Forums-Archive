---
title: "Can you use an Windoze printer driver under wine?"
date: 2007-05-18
forum: Absolute Beginner Talk
---

### Post by ianb72 on 2007-05-18
I have an old Lexmark X85 Printer/Scanner/copier that was given to me, but there are no linux/Ubuntu drivers for it, I have tried the How to at [How To: Lexmark Printers]("http://ubuntuforums.org/showthread.php?t=49714")

But it doesn't work.

Is there anyway I can use a Windoze driver under Wine to use this printer?

Cheers
Ian

---

### Post by Terl on 2007-05-18
Unfortunately it looks like your printer may not work under Linux.  Check this page at LinuxPrinting.org:  [Lexmark Printers]("http://openprinting.org/printer_list.cgi?make=Lexmark").  You will see that the x85 is listed in the paperweight side.  Sorry. :(

Linux Printing is a good site and has a great deal of information.  I'd recomment, if you later decide to get a printer that will work under Linux, that you check this site first for recommendations.  The HP brand is generally a good choice but check the site first to make sure.

My printer does not work under linux either...one reason I kept my pc as a dual boot.

---

### Post by esoterica on 2007-05-18
Lucky for you the price of new printers has come down so low anymore that they are practically giving them away. My local Walmart was selling the All In One Type printers this week for like $30.00, the box said it worked with Windows, Mac and Linux. You've probably already wasted more than $30 worth of your own time just trying to get an old printer working.

If your determined though, I was reading in the community documentation pages the other day an interesting option to making Windows drivers work in Linux, never tried it yet myself, but it was interesting none the less, just wish I could find the link for you now. There is a Linux utility they were talking about that lets you extract the .sys file out of Windows driver software and build it to run your hardware in Linux.

I wish I could find that documentation page for you, but I can't remember now what it was I was looking for when I accidentally ran across it, it certainly looked promising, it explained how to extract the .sys file from the .exe or .zip file for the windows driver then some way to recompile it to work in Linux.

Here's something somewhat similar that may help you, but it's not what I was looking for, sure wish I could find it again. If you search hard enough you'll find it, the only word I can remember that you can use for a search string though is "extracting .sys".

[http://www.linuxquestions.org/linux/answers/Networking/NdisWrapper_The_Ultimate_Guide/](http://www.linuxquestions.org/linux/answers/Networking/NdisWrapper_The_Ultimate_Guide/)

---

### Post by Terl on 2007-05-18
That link is for ndiswrapper which is for the wireless connection.  

esoterica is right about printer prices.  It is worth a look if you are in the market for one.  Like I mentioned, double check the linux printing site to make sure it works.

---

### Post by esoterica on 2007-05-18
> 
That link is for ndiswrapper which is for the wireless connection. 


I realized that, but if you read the information on that page it also tells you how to extract the files you need from windows .exe files. Which if combined with the other information I was looking for and still can't find is needed in order to make the windows drivers work in Linux. The instructions I'm trying to find only explained how to do this if you were already in Liinux, I figured before I lost that page that told you how to do it from in Windows as some people may need to know how to do I'd better paste the link in here. There is more information on that page though than just what applies to Wireless and Ndiswrapper specificly when you read further down it.

---

