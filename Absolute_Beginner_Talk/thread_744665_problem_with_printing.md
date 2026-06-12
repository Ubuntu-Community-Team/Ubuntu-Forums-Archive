---
title: "problem with printing"
date: 2008-04-03
forum: Absolute Beginner Talk
---

### Post by wpshooter on 2008-04-03
Can I get someone to test this to see if they get the same print problem that I do.

I am using Gutsy with Firefox and printing to a HP Laserjet 2100 printer.

Please go to the Virginia Department of Taxation site given below and then try to print the VDOT individual tax form #760 to either a file or to a physical printer and tell me if the output that you get is missing characters.  

For instance, when I output this tax form, the header "**Your First Name**" outputs as **"Your   rst Name**".  And there are many other examples of this missing character problem on this form and other forms the VDOT site.

[http://www.tax.virginia.gov/taxforms/Individual/Income%20Tax/2007/760.pdf](http://www.tax.virginia.gov/taxforms/Individual/Income%20Tax/2007/760.pdf)

I am wondering if this is a problem with Linux, with Adobe Acrobat or something with the VDOT site.  I have tried both Acrobat Reader versions 7 and also versions 8 for Linux and I get the same results.

I can print forms from the IRS site with no such problems.

Thanks.

---

### Post by cmnorton on 2008-04-04
I believe you have hit the jackpot of a problem, I cannot print the form to a an HP LJ 1320. I tried downloading the form; printing it; but it queues to my printer as stopped. 

I tried saving the Acrobat locally and printing that, and still no luck.

I was able to print the page in Ubuntu forums containing your post.

Here is a link, though this may just be because the viewer is Acrobat. I am using Evince.

[http://www.linuxquestions.org/questions/linux-general-1/can-anyone-print-this-pdf-with-acrobat-reader-272931/](http://www.linuxquestions.org/questions/linux-general-1/can-anyone-print-this-pdf-with-acrobat-reader-272931/)

I am able to print this from Windows, which the link above discusses.

---

### Post by wpshooter on 2008-04-04
This is one of those things that just puts me off from recommending/advising my friends, acquaintances, business associations to consider switching to Linux.

Something as simple as being able to properly print a Virginia Individual income tax return form from the VDOT website and you can not do it without having to contact and get 2, 3, or 4 entities involved to see why it won't work.  And even then, trying to get some companies like Adobe to understand what you are talking about and getting someone with enough intelligence from that company to contact you, so you can make them understand the problem, just makes trying to use Linux just too much of a challenge at times.

And it is not as if this is a problem that has just now been discovered because when I look at various postings on the web, they lead me to believe that this type of problem has been ongoing of quite a long while.

And, please do not give me that line that this is not Ubuntu/Linuxs' fault.  

Because if I try to tell that to someone that I might be interested in getting to use Linux, that someone is going to be impressed at about ZERO with that argument.  Because they already now that this type of thing is NOT a problem if you use M/S windows.

Thanks.

---

### Post by cmnorton on 2008-04-04
You make a good point, but I am not so sure this is about Linux as it is a lot of sites do not think about the kind of browsers that are visiting them. In other words, people just assume a Windows client is visiting their site. 

I suggest posting a bug against Ubuntu. In my case, I'd be inclined to post a bug against Evince, because if it can read the PDF, it should be able to print it. Evince is what I used to get the Virginia tax document.

Edit 2:
---------
I also want to add an example in the other direction, at least for open source. Our school system is now turning to Firefox instead of IE on the school system's Windows lab systems. The town is turning to Firefox, because IE works poorly with alt-n's World Client, a Windows mail server and web front end. 

This clearly does not excuse Ubuntu/Linux/Evince/CUPS from failing to print the State of Virginia tax document. But, as you stated, how easy has it been for you to contact Adobe? At least we have Ubuntu Launchpad. 

Edit 1:
------------------------
In the words of the late Curly Howard, "I seen my duty, and I done it"

[https://bugs.launchpad.net/ubuntu/+bug/212017](https://bugs.launchpad.net/ubuntu/+bug/212017)

---

### Post by wpshooter on 2008-04-04
Thanks for your efforts.  I added my 2 cents worth to your bug report.

I have a call in to Adobe to see if they might possibly give me a call back about this.  If they don't, I am going to try to get them and the VDOT together next week and see if some of their "experts" can hash out this problem.

Thanks.

---

### Post by brian_p on 2008-04-04
> **wpshooter said:**
> Please go to the Virginia Department of Taxation site given below and then try to print the VDOT individual tax form #760 to either a file or to a physical printer and tell me if the output that you get is missing characters.  

For instance, when I output this tax form, the header "**Your First Name**" outputs as **"Your   rst Name**".  And there are many other examples of this missing character problem on this form and other forms the VDOT site.


Prints to file fine for for me.

Don't you small tax forms in Virginia. Only two pages!

---

### Post by wpshooter on 2008-04-05
> **brian_p said:**
> Prints to file fine for for me.

Don't you small tax forms in Virginia. Only two pages!

Can you tell us about your setup ?

What version of Ubuntu are you using ?

What PDF viewer are you using ?  In particular, are you using Adobe Acrobat Reader ?

What physical printer are you using and how is it connected to your computer ?

Thanks.

---

### Post by brian_p on 2008-04-05
> **wpshooter said:**
> Can you tell us about your setup ?

What version of Ubuntu are you using ?

It's Debian stable.

> What PDF viewer are you using ?  In particular, are you using Adobe Acrobat Reader ?

xpdf.

> What physical printer are you using and how is it connected to your computer ?

HP LaserJet 6L. Parallel port.

---

