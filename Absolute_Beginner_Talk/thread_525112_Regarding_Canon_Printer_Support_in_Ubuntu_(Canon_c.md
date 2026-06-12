---
title: "Regarding Canon Printer Support in Ubuntu (Canon called me)"
date: 2007-08-13
forum: Absolute Beginner Talk
---

### Post by jenson on 2007-08-13
Hi guys/girls/seniors/juniors/etc,

I have a Canon Pixma MP180 multi functional printer and I cant seems to find a compatible driver for Ubuntu, and I've decided to contact the Canon Technical Support. Up to my surprise, they told me that the requests from Linux communities are low thus making them quite reluctant to spend their resources into developing a Linux driver for the printer, in fact they said there is no intend for them to release any Linux driver yet as they hardly receive requests from Linux users to have a Linux printer driver.

They even said that there would be no market value for the driver even though they develop and release it if the demand is low as the users are not that much. Most of the users run Windows and Mac OS.

Any clue on this? Any tip can be given to me?

Thanks.

Regards,
Jenson

---

### Post by ramjet_1953 on 2007-08-14
This thread may help:

[http://openprinting.org/show_printer.cgi?recnum=Canon-Pixma_MP170](http://openprinting.org/show_printer.cgi?recnum=Canon-Pixma_MP170)

It's for the MP170, but worth a try.

You can also try TurboPrint. They claim to support your printer. Unfortunately it is not free, but isn't that expensive.

[http://www.turboprint.de/english.html](http://www.turboprint.de/english.html)

There is a trial download, so you can see if it works OK.

Regards,
Roger :cool:

---

### Post by jenson on 2007-08-14
> **ramjet_1953 said:**
> This thread may help:

[http://openprinting.org/show_printer.cgi?recnum=Canon-Pixma_MP170](http://openprinting.org/show_printer.cgi?recnum=Canon-Pixma_MP170)

It's for the MP170, but worth a try.

You can also try TurboPrint. They claim to support your printer. Unfortunately it is not free, but isn't that expensive.

[http://www.turboprint.de/english.html](http://www.turboprint.de/english.html)

There is a trial download, so you can see if it works OK.

Regards,
Roger :cool:

Hi ramjet,

Yeah I tried installing TurboPrint trial download and it works pretty well with it. But I'm also trying out other possibilities too. I also wish to get the scanner working. I will give gutenprint a try using MP150 or MULTIPASS150 drivers and see whether it work out properly for me, but how can I go about uninstalling TurboPrint driver? I don't know the command.

I'm going to try two other possibilities later.

Thanks.

Regards,
Jenson

---

### Post by Benbow on 2007-08-14
Three months on, I am very happy with Feisty but I am still struggling with my mp170. It seems to me that printers (on the whole) are a big problem in linux generally and my next will be a HP!!

I have tried various generic drivers with no success. I eventually bought turboprint based on the trial and found that with text and spot colours, no problem but with photographs turboprint failed as the settings available are minimal compared with the canon driver settings for xp. I now use xp for photo and better quality printing and Ubuntu for the rest.

I think that canon opt for a "keep your head in the sand and it will go away". Wrong.....the winners will be HP, one of the few who apparently provide linux drivers for many of their machines.

---

### Post by jenson on 2007-08-14
haha, it's working now, just that I can't use canon software but at least can make the printing and scanning working now =)

Thanks guys!

---

### Post by freesitebuilder on 2007-08-21
I asked Canon UK why they don't produce a Linux driver, and here's their reply:
> Please be advised that although there are people out there who use the Linux operating system, it is not a widely used mainstream operating system. Due to this Canon has made the decision not produce drivers for Linux.

However, if you wish to develop drivers to be used with the Linux operating system, or possibly find drivers which have already been developed by third parties, you may be interested in looking in the Canon Digital Imaging Developer Program. Further details can be found on uor website here:
[http://www.didp.canon-europa.com/](http://www.didp.canon-europa.com/)

Yours sincerely,
Canon Support Centre
Should our answer not fully resolve your problem, please feel free to either re-submit a new query by clicking here, or alternatively call our support helpdesk at 08705 143 723 Monday to Friday from 9:00AM to 5:30PM stating the 7 digit reference number in the subject of this email.

---

### Post by OzzyFrank on 2008-03-15
> **jenson said:**
> haha, it's working now, just that I can't use canon software but at least can make the printing and scanning working now =)

Thanks guys!

Posting how you got it happening would help others. I was going to suggest [COLOR="DarkRed"]**Xsane**[/COLOR], which is a pretty good app and worked with the scanner part of my Canon MP800 multifunction out-of-the-box. Anyone who is trying to get scanning happening should install it (it will end up in your Graphics menu). Cheers

---

### Post by bumanie on 2008-03-15
Canon reportedly have said that Hell would have to freeze over before they'd bother writing linux drivers. There is this site in Japan that has some canon drivers for linux. As far as I am aware, it is your best bet. Whoever said their next printer would be HP is on the money. HP have excellent linux support.
Try here [http://cweb.canon.jp/drv-upd/bj/other.html](http://cweb.canon.jp/drv-upd/bj/other.html)
Hope it helps.

---

### Post by jenson on 2008-03-15
sorry oh, I use the default cup package recommended by you guys here and get it working, but it's limited to printing and minimum scanning. All features are quire restricted though.I try not to use paid third party driver. I rather use generic driver or wait for their release, else I would switch to HP on my next purchase since the reply I gotten from Canon also shown that they have no interest in supporting Linux..that's stupid!

---

### Post by OzzyFrank on 2008-03-16
Oh, you're just using the default drivers Ubuntu has? Yeah, minimal printing (fine for text though), but scanning should be as good as in Windows, with programs like Xsane.

Yep, Canon seem proud to be cutting their own throats, hehe. Personally, I can't believe Linux users only make up 1% of PC users... but then again, in market terms, I am a Windows users, since I bought it at one stage or another. The fact I use Ubuntu most of the time doesn't get recorded on any ledger... and I assume there are millions like me. Then there are those who have totally given up on Windows and Mac and purely use Linux... where does that get recorded? I mean, who makes up these figures??

Anyway, it seems so ridiculous that Canon would rather save a few hundred or thousand dollars paying a couple of programmers than make many, many thousands off those who won't buy a printer that won't work fully in Linux. I mean, that just seems stupid beyond belief! Look at much smaller companies that are supporting Linux (in case one wants to defend Canon based on Linux's supposed market share).

I might email Canon and ask if I should be buying HP next time, hehe!

---

### Post by dodderer on 2008-04-22
> **jenson said:**
> haha, it's working now, just that I can't use canon software but at least can make the printing and scanning working now =)

Thanks guys!

can someone expound on what he did? words of one syllable please.

---

### Post by hardyn on 2008-04-23
"Please be advised that although there are people out there who use the Linux operating system, it is not a widely used mainstream operating system. Due to this Canon has made the decision not produce drivers for Linux.

However, if you wish to develop drivers to be used with the Linux operating system, or possibly find drivers which have already been developed by third parties, you may be interested in looking in the Canon Digital Imaging Developer Program. Further details can be found on uor website here:
http://www.didp.canon-europa.com/"

I understand that linux driver demand does not have the same magnitude of windows or osx, but i am seeing the trend of hardware companies pawning the driver development off on the linux community... if this really is something they should be doing to sell hardware.

I have noticed that HP directs linux driver support to openprinting, and it looks like cannon is asking the poster consider developing a linux driver for free for them.

If osx uses cups, and is a posix system, is it really that big a issue port to linux?

---

### Post by roscal on 2008-06-12
I have a Cannon Pixma, which works wonders.
..Only on my wifes comp though..(XP).
Never got it to work properly on my machine.
(Still on Feisty at the moment)
Guess what brand of printer I'm buying next??
(and hence, their ink)
This 'niche' market could number into several million.

---

### Post by freesitebuilder on 2008-06-13
My Pixma IP3000 needed a third-party driver (TurboPrint) under prev releases, but in Hardy (8.04) it's supported directly.

---

### Post by johnlvs2run on 2008-06-13
Thanks much for this thread.  

I was planning to get a Canon printer today, after checking here first to make sure it would work.

So much for that idea.  :)

---

