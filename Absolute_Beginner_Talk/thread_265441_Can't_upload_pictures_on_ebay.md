---
title: "Can't upload pictures on ebay"
date: 2006-09-26
forum: Absolute Beginner Talk
---

### Post by newbie8 on 2006-09-26
Hi to all. I am a pure Ubuntu user (only Ubuntu dvd is installed in my computer and windows erased).

As I was in ebay and I wanted to sell something, I noticed that I could not find the option/function to upload pictures to ebay.

The only function that was available was to transfer pictures to a picture-hosting site and attach the http address which is more troublesome to do.

I didn't think it was a Firefox problem since I was able to do it using Windows XP and Firefox in the past.

Is there a quick-fix to this? Is this normal?

thank you.

---

### Post by nudnik on 2006-09-26
> **newbie8 said:**
> Hi to all. I am a pure Ubuntu user (only Ubuntu dvd is installed in my computer and windows erased).

As I was in ebay and I wanted to sell something, I noticed that I could not find the option/function to upload pictures to ebay.

The only function that was available was to transfer pictures to a picture-hosting site and attach the http address which is more troublesome to do.

I didn't think it was a Firefox problem since I was able to do it using Windows XP and Firefox in the past.

Is there a quick-fix to this? Is this normal?

thank you.

Visit this page: [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

And make sure you have all the needed software installed.
You might need the package called "mjpegtools" to begin with

---

### Post by dmizer on 2006-09-26
oddly enough, i was just reading about this very issue in a very very old thread from 2004.  it seems ebay has chosen to turn it's back on the insignificant linux community.

here's a recent thread at the ebay forums:
[http://forums.ebay.com/db2/thread.jspa?threadID=2000208185&tstart=120&mod=1158035628795](http://forums.ebay.com/db2/thread.jspa?threadID=2000208185&tstart=120&mod=1158035628795)

---

### Post by nudnik on 2006-09-26
I recently uploaded pictures to ebay without incident, so it is possible with a properly configured penguin.

---

### Post by newbie8 on 2006-09-26
Besides pictures, I can't seem to edit texts wysiwig. It is all in html code which I am not familiar with.

What is the fastest way to solve the problem of:

1. Not being able to upload pictures to Ebay

2. Not being able to edit "descriptions" in listings the normal wysiwig way (instead of pure html).

I was going to erase Ubuntu entirely and switch back to Windows XP since I cannot live without Ebay.

Cheers!

---

### Post by newbie8 on 2006-09-26
Even if I use Ebay's "sell similar" functions to sell the exact same thing, the pictures disappear which is a major bummer if someone sells dozens of the similar item.

I checked-out the link that was given but could not find a definite answer to the problem.

Please note that everything was okay with the Firefox-XP combination.

I am using the Drake on DVD by the way.

Please help...I can't live without Ebay and I don't like to part with Ubuntu. It is almost perfect except for the ebay thing.

---

### Post by dmizer on 2006-09-26
have patience.  it might take a little bit of doing, but if someone else has made it work so can you.

i'm not too sure where to tell you to start because i don't use ebay, but if you're patient, i'm sure nudnik can offer you a workable solution.

but it looks like your first step is going to be to install mjpegtools.

---

### Post by nudnik on 2006-09-26
I was hoping mjpegtools had something to do with still jpeg format, but after checking the description once again (been a while) it appears relevant only to video. 

At any rate, I have all multimedia codecs installed, the proprietary nvidia driver and am using a standard up to date version of firefox, so I am unsure what allows me to succeed when you have not. 

](*,)

Below, to the best of my memory, are the  modifications I've made to Ubuntu, many of which have no relevance I am sure.

win32 codecs
all gstreamer 10 packages
lame
sox
ffmpeg
alsamixergui
alien
k3b
bittornado
i686 smp kernel, latest version+headers
gxine
mjpegtools
libxine extra codecs
libxine main
real player
flash
java, latest runtime
gcc
libc6-dev
nvidia driver compiled from source

---

### Post by juhizz on 2006-09-26
I think the problem is Java. I have the same problem, but it´s weird, sometimes it works and sometimes doesn´t:-k . Try with different browser, it may work.

---

### Post by newbie8 on 2006-09-26
Did some research and this is what I found [http://forums.ebay.com/db2/thread.jspa?threadID=1000326575&tstart=0&mod=1157868815024](http://forums.ebay.com/db2/thread.jspa?threadID=1000326575&tstart=0&mod=1157868815024)

and more [http://www.d-a-l.com/help/showthread.php?t=46765](http://www.d-a-l.com/help/showthread.php?t=46765)

I think it is a common problem but there does not seem to be a solution.

Will be trying to browse with Opera. If that does not work, then its Linux most likely.

Hoping for a quick solution. There are more like me out there who love Linux but are sellers on Ebay too.

Cheers!

---

### Post by newbie8 on 2006-09-26
Still does not work with Opera. Once I find a solution, will let everyone else know. 

Please help...

---

### Post by newbie8 on 2006-09-26
I have also installed Java and it still does not work.

Is it because of this...Ebay only talks about Mac & Windows and does not talk about Linux.

[http://pages.ebay.com/help/newtoebay/browser-recommendations.html](http://pages.ebay.com/help/newtoebay/browser-recommendations.html)

---

### Post by dmizer on 2006-09-26
do you have flash installed and configured/working correctly?

btw, i find it humerous and ironic that they offer support options for msntv users but not linux users.

which java did you install?

edit:
actually, i just bopped over there myself to check things out.  i have java installed too, but it's the default linux install.  you'll need a more recent java.

---

### Post by newbie8 on 2006-09-27
Hello again.

I installed the 2 groups of Java/Jre that were available on my Ubuntu dvd (synaptic) repositories. 

I also went to the java.com site for verification but nothing happens. It just gives me a semi-blank page. I think the jre on the dvd is 1.4

The ebay problem seems to be either java or activeX related.

I tried to download the latest java on the java site but after the long wait, errors just appear.

Is there are simple way to upgrade Java?

I've got to get this going before the weekend listing schedule.

Thanks!

---

### Post by newbie8 on 2006-09-27
Still no solutions to the 
1. can't upload pictures to ebay directly
2. can't edit descriptions on ebay the normal way.

But....

I found an alternative which is Auctiva.com which allows me to upload pictures.

Strange....

---

### Post by nudnik on 2006-09-28
sudo apt-get install sun-java5-jre

The above will install a more recent version of Java, the one I am using.

---

### Post by ishimaru_kaito on 2006-10-10
If you're using ebay.co.uk, I found I could upload pictures using the old listing system, which they's still got.  It's the only way I've discovered of doing it.  I don't know how long they're going to keep it on there though, but the day they take it off, they'd better have a decent solution for linux users!!

See the attached pic for the listing option (in purple):D

---

### Post by newbie8 on 2006-10-18
[http://business.newsforge.com/article.pl?sid=06/10/17/2050230&from=rss](http://business.newsforge.com/article.pl?sid=06/10/17/2050230&from=rss)

This is what I was talking about re Linux not working for Ebay.

It just seems that I experienced it ahead of the rest.

---

