---
title: "Replacement for Freedownloadmanager"
date: 2008-03-30
forum: Absolute Beginner Talk
---

### Post by Name141 on 2008-03-30
Does anyone know a good replacement for Freedownload manager?  I MUST have a DL manager with a scheduler starting things at 2 AM my time, and stopping any undownloaded , or pausing, files at 5 AM.  As I am on a sat connection with a.. "Fair Access Policy".

I also would like the ability for integration inside of FireFox.  Such as, with FDM, you "Download with FDM".

---

### Post by y-lee on 2008-03-30
Google found a bunch but I don't use them and am not sure any meet your needs, esp the scheduling thing. Anyway see for a few comparrsions of some of them [download manager comparisons]("http://en.wikipedia.org/wiki/Comparison_of_download_managers"). Also i don't think [gwget]("http://www.gnome.org/projects/gwget/index.html") is listed there so check it out also.

Btw [wget]("http://en.wikipedia.org/wiki/Wget") is the standard command line tool for downloading. That is what i use if I'm not using firefox or the downthemall firefox extension i have installed :)

---

### Post by Name141 on 2008-03-30
I suppose I "could" use wget.   However, following that, I "could" shoot myself in the foot.
But both are something I don't want to do lol.

I think however, I have found the solution for my problem, with wxDownload. It claims I can use FlashGot inside of FireFox, which I will use when I make the switch to Ubuntu anyway.

---

### Post by y-lee on 2008-03-30
> I suppose I "could" use wget. However, following that, I "could" shoot myself in the foot.
But both are something I don't want to do lol.


:lolflag: i was just throwing wget out there for your information, I know many people stay away from command line tools if they can. I however use it in windows even... it has a windows port ya know :)

Anyway glad ya found something ya think might be a solution to your problem,

good luck.

---

### Post by Name141 on 2008-03-30
actually I haven't, it wont keep the cookie of rapidshare links.

---

### Post by y-lee on 2008-03-30
> actually I haven't, it wont keep the cookie of rapidshare links.

Hmm have you looked thru all the options preferences or whatever of the program to see if any relate to cookies? I've never used the program so I dunno :confused:

---

### Post by Name141 on 2008-03-30
Getleft looks promising also.

However, I don't see a way to integrate getleft and firefox.  I am thinking I need something like the FDM's plugin , where it "knows" what to copy to get the file to download ?  I couldn't even get FlashGot to work for Getleft.

---

### Post by Name141 on 2008-03-30
Downloadthemall! doesn't have a scheduler, hm..  I am wondering if wget is the best bet for rapidshare options , due to it needs the premium cookie?  I know there is something along the lines of..

wget -bc -load-cookies file -i filestodownloadhere 

?

---

### Post by y-lee on 2008-03-30
Try it it should accept cookies.

---

### Post by Name141 on 2008-03-30
I tried it , and it doesn't seem to want to work.  I copied cookies, and the referer also.  I still got the HTML instead of file (login page)

---

### Post by Name141 on 2008-03-30
I found this in another part of the forum..
"If you are looking to download from sites like rapidshare, megaupload, etc... use Kget.

1. Install KGet

2. Install Konqueror.

3. Install the FlashGot Firefox extension.

4. Log into your rapidshare premium account or other account in Konqueror. (KGet shares cookies with Konqueror.)

5. Configure FlashGot to use KGet as download manager.

6. Right click on the list of rapidshare or other links in Firefox and got to 'FlashGot Selection'.



Works like a charm."

I am assuming gwget would work fine for it ?

---

### Post by Name141 on 2008-03-30
I got it, using instructions from [http://www.g-loaded.eu/2007/09/15/use-wget-or-curl-to-download-from-rapidshare-premium/](http://www.g-loaded.eu/2007/09/15/use-wget-or-curl-to-download-from-rapidshare-premium/)

it seems it needed ..

.rapidshare.com TRUE    /       FALSE (SomeNumbersHere) TheCookieDataHere

to work properly.

---

