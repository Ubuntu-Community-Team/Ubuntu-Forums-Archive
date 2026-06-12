---
title: "Viewsat STB zmodem problem"
date: 2007-02-06
forum: Absolute Beginner Talk
---

### Post by Teva on 2007-02-06
Hello,

    I'm new to linux and this is very frustrating for me.  I am wondering how to connect my STB (satellite reveiver) to my computer.  With Windows there was a program that I would just double click and it would work.  Unfortunately, ViewSat Xtreme has no support for linux.  I know my com port & serial cable (straight through db9) work because I've used it in the Windows program (Loader2). I've been doing a lot of searching and someone said to use 'minicom'.  Here is the link ([http://dtv100.com/forums/8200-linux-vs-viewsat.html)](http://dtv100.com/forums/8200-linux-vs-viewsat.html)).  I've set everything up as the instructions say, but still no luck.  I just keep getting a failure message.  Do I need to check any settings in Ubuntu (Dapper) to make sure the port is set up correctly?  Is there a better or easier program (with instructions) that I could use to send/receive files via zmodem to my satellite?  Does anyone know what I'm doing wrong?

Thank you,


Teva

---

### Post by Teva on 2007-02-07
I figured out what the problem was. I didn't have sz installed. I went to Synaptic and installed "lrzsz" from there and when I went to do the file transfer, everything worked perfectly! Sorry to waste your time guys but I *just* started using Linux and it's taking me a little while to get used to the way things are done. But I like it.

Thanks,

Teva

---

