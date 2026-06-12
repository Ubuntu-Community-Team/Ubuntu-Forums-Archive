---
title: "Stock Portfolio - Software?"
date: 2005-07-09
forum: Absolute Beginner Talk
---

### Post by garnertr on 2005-07-09
Greetings,

I'm looking for software to use for stock purchase, charting, technical analysis, etc., and I'd like it to provide a ticker  bar (if possible).

Does anyone know of anything?

-----

Side note; if I'm looking for software, and I have no clue as to what I'm looking for, where would be a good place that I can go to browse software titles and descriptions?

---

### Post by dimeotane on 2006-10-07
I've been wanting the same thing, some kind of stock portfolio tracking software that runs nicely under ubuntu.  I hate using the online ones which are so slow, cluttered, and full of advertising.  

I searched under synaptic but the selection of finance software there is quite limited. So I spent the better part of the day looking for a windows portfolio tracking program that could run under wine.  What a waste of time. 

I think I found just what I wanted.  Check out [http://www.grism.org/](http://www.grism.org/)

There's a few dependencies you'll need to install, like ruby, gtk and others but it's worth it.  It works nice and looks good in ubuntu.

---

### Post by Marsolin on 2006-10-08
I haven't run across many [Investing]("http://linuxappfinder.com/businessandfinance/investing") programs yet, but the three I have found are [Market Analysis System]("http://linuxappfinder.com/package/eiffel-mas"), [LinuxTrade]("http://linuxappfinder.com/package/linuxtrade"), and [Qtstalker]("http://linuxappfinder.com/package/qtstalker"). I can't make any personal recommendations because I haven't used any of them.

I'll have to add Grism to the list.

---

### Post by errolsiegel on 2007-01-14
Grism looks like just what I need.

How did you install it?  Is there a package for Ubuntu?

---

### Post by Marsolin on 2007-01-14
I haven't found a deb package for it.  You can find installation instructions [here]("http://www.grism.org/install.html") though.

---

### Post by errolsiegel on 2007-01-14
Thanks -- the instructions on the grism web site worked fine.  It appears that they recommend different versions of ruby-gtk2 and ruby-libglade2 than what is installed on Edgy, but so far I haven't seen any problems.

---

### Post by jagannath on 2007-03-09
> **errolsiegel said:**
> Thanks -- the instructions on the grism web site worked fine.  It appears that they recommend different versions of ruby-gtk2 and ruby-libglade2 than what is installed on Edgy, but so far I haven't seen any problems.

Well, I tried to install like you did. But didn't work for me. I get a 'permission denied' message when I ' ruby setup.rb' !?

Am I missing something here? I am runnng Dapper.

Thanks for any help.

J

---

### Post by Marsolin on 2007-03-09
> **jagannath said:**
> Well, I tried to install like you did. But didn't work for me. I get a 'permission denied' message when I ' ruby setup.rb' !?

Am I missing something here? I am runnng Dapper.

Thanks for any help.

J

You might need to run it using sudo.

---

### Post by dimeotane on 2007-03-10
You'll need version .81 to get the charting to work, posted march 7th 2007.  Yahoo changed their data format and the charting stopped working. 

Has anyone managed to upgrade from .8 to .81?

I run the setup but then grism still says it's version .8

I've messaged Nick, the creator to see what his advice is.

---

### Post by jagannath on 2007-03-11
> **Marsolin said:**
> You might need to run it using sudo.

You're  right.  Thanks.

Wish Grism could get quotes from other stock exchanges too. Like Quick Quotes gets. Unfortunately that's Win software

---

### Post by noMScraig on 2007-05-22
I had to use sudo also and then installation worked great...for newbies like me the exact line is

sudo ruby setup.rb

Additionally I had to go out and reinstall the dependent packages.

Thanks!

---

### Post by PaulHuffman on 2007-09-24
I got the dependencies installed and grism installed with ruby setup.rb.  But I can't figure out how to run it.  bin/grism just tells me "command not found"

---

### Post by boo-koo2 on 2007-12-24
Paul,

why did you not just use the .deb package?

---

### Post by PaulHuffman on 2007-12-28
I got some help from the author of grism.  You need to upgrade ruby-gnome2 (to v0.16.0) with the instructions on this page:

[http://ruby-gnome2.sourceforge.jp/hiki.cgi?Install+Guide+for+Ubuntu](http://ruby-gnome2.sourceforge.jp/hiki.cgi?Install+Guide+for+Ubuntu)

Then just type grism in a terminal.

But another easy way to get away form Microsoft Money Central is to transfer the portfolios to finance.google.com.

---

### Post by mrthundercleese4 on 2008-01-30
anybody know if any of these work like ameritrade's real time ticker where you get a real time stream of the market and can see every buy and sell taking place?

---

### Post by ekravche on 2008-02-11
> **mrthundercleese4 said:**
> anybody know if any of these work like ameritrade's real time ticker where you get a real time stream of the market and can see every buy and sell taking place?

I think that that grism, and qtstalker work based on the data provided by yahoo, so you'll be dealing with daily quotes.

---

### Post by Thelasko on 2008-04-02
I'm a fan of QtStalker.  It's not the easiest to use but it's very powerful.  Excellent for technical analysis.  It defaults to using data from Yahoo but if you have another source you can use it too (with some work).

---

