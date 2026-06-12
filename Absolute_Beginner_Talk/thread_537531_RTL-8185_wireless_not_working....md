---
title: "RTL-8185 wireless not working..."
date: 2007-08-29
forum: Absolute Beginner Talk
---

### Post by Tssabackus on 2007-08-29
RTL-8185 wireless card hooked up to an antenna which should receive the signal from the wireless modem...thats my setup.

I searched, and found 3 or 4 threads, but they all lead to other threads, and its way over my head...

I had a friend install ndiswrapper, but is not sure how to use it. THere were also other stuff...does anyone have a nice idiot proof guide for new users of linux?

---

### Post by kevdog on 2007-08-29
ndiswrapper + win98 rtl driver should work best for you!

---

### Post by tyggna1 on 2007-08-29
> **Tssabackus said:**
> does anyone have a nice idiot proof guide for new users of linux?

Documentation is your best bet--posted on "support-documentation" at the top of the page.

As for ndiswrapper:  

first thing:  Download the win98 drivers for your card like kevdog said.  Unzip/untar it and put it on a file you can find.  If it's a .exe, try running it in wine or in a windows environment--just remember where it puts the file.

Then, the easiest way I found is to go to add/remove programs, and search for "ndis"
the first one one that list will say windows wireless drivers.  Check it and install, then run it as soon as it is installed.  If it's already installed--I'd remove it, as it sometimes won't show up in any menus--and then reinstall.  When it comes up, click "install driver" with the plus sign next to it, and navigate to the .ini or .sys file that contains your wireless driver information.

---

### Post by Tssabackus on 2007-08-31
[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=1&PFid=1&Level=6&Conn=5&DownTypeID=3&GetDown=false&Downloads=true#RTL8185L](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=1&PFid=1&Level=6&Conn=5&DownTypeID=3&GetDown=false&Downloads=true#RTL8185L)

I have downloaded the linux driver but I have no idea what to do. THere are lots of files, but I can't make sense of anything... My friend says to install I need some build essential program, but I don't have internet unless I can borrow a long ethernet cord again...

Would using Wine with the windows driver work better? I would still need the cord...but if its better then I would rather do that.

---

### Post by Tssabackus on 2007-09-03
I still need help someone

---

### Post by enderwig on 2007-09-03
I uncommented the line thats says
blacklist r818x
in /etc/modprobe.d/blacklist and then restarted, and it all worked fine

---

