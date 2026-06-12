---
title: "Internet Download manager"
date: 2007-08-15
forum: Absolute Beginner Talk
---

### Post by mokkai on 2007-08-15
any internet download manager for ubuntu 
( like as IDM for windows)
is there anything  ?.....

---

### Post by 1/0 on 2007-08-15
There are plenty of them! Just have a look in Synaptic. 

Freeloader, d4x, jigdo, kget, gwget, aso.

---

### Post by bapoumba on 2007-08-15
Thread moved to "Absolute Beginner Talk" support forum.

---

### Post by Amazona aestiva on 2007-08-15
Hi I advise Kget.;)

---

### Post by eborigene on 2007-08-31
Any idea about Internet Download managers supporting streaming audio and video that integrate well with Xubuntu, please?
Thanks!:(

---

### Post by alienexplorers on 2007-09-01
If you are running firefox you can try a really nice download manager that is also an add-on called DownThemAll.  It can be found at:
> [https://addons.mozilla.org/en-US/firefox/addon/201](https://addons.mozilla.org/en-US/firefox/addon/201)

---

### Post by wtever on 2007-09-21
anything with decent GUI , with resume and schedule capabilities , that has a smart download logic accelerator that features intelligent dynamic file segmentation and safe multipart downloading technology to accelerate your downloads ? ( which is some of other features IDM has + new feature of ability to intercept flv videos like those used in youtube and others )

EDIT : Kget seems fine i might give it a try 

EDIT2 : hmm Kget not so good  No multipart downloading and don't even know the size of large files in advance (increment total size as u go with % stuck at 99% ) !  its only advantage is support of resume capability and the GUI any thing better ?

---

### Post by rogerdean on 2007-10-28
sorry, never found a good answer for this. i miss IDM too - very fast and capable multi-threaded accelerator. did try downthemall but it's nowhere near as quick. really hurts to boot windows in order to download a linux distro quickly!

---

### Post by erginemr on 2007-10-28
There is already a default backend (console) download manager available under Ubuntu: wget. And there are several frontents to wget; gwget and kget for instance. However, I would recommend gtm (gnome transfer manager) which is also a graphical wget frontend and downloads files very fast. (and no, it is not multi-threaded, either)

On the Firefox side, I have also tried DownThemAll for a while, but apparently it often misses the correct addresses of streaming content such as video files in flash. In this department, there is another Firefox extension "DownloadHelper", which does a better job in catching those files off the web.

---

### Post by rogerdean on 2007-10-28
yeah, wget is fine as a download manager, but is not multi-threaded. that's the key thing we're missing. downthemall is multi-threaded so i'm giving it another try...

---

### Post by erginemr on 2007-10-29
Apparently, your prayers have been answered. I have found a program (wxDownloadFast) that uses multi-threading:
[http://dfast.sourceforge.net/](http://dfast.sourceforge.net/)

Also the getdeb.net site has a copy:
[http://www.getdeb.net/app.php?name=wxdownload%20fast](http://www.getdeb.net/app.php?name=wxdownload%20fast)

I have downloaded the program and it seems it does what it says in the multi-threading department. And it is "fast". And apparently you can also specify extra web sources for the same file to increase the downloading speed.

---

### Post by erginemr on 2007-10-29
P.S. It also supports scheduling. :)

---

### Post by rogerdean on 2007-10-29
many thanks! there seems to be a fiesty package but not a gutsy though, and i'm gettiing crashes trying to download ubuntu! will keep trying...

---

### Post by jagannath on 2007-10-29
> **rogerdean said:**
> many thanks! there seems to be a fiesty package but not a gutsy though, and i'm gettiing crashes trying to download ubuntu! will keep trying...


I'm trying the same thing too!! In my case the download window ( the GUI window) just flashes on the screen and vanishes !!:confused:

--
J

---

### Post by so7777777os on 2007-10-29
I think there're no good answer....but many fellow  use wget ....maybe its a good choice....decide yourself.....
maybe  i have some mistakes..pardon me...

---

### Post by erginemr on 2007-10-29
> **jagannath said:**
> I'm trying the same thing too!! In my case the download window ( the GUI window) just flashes on the screen and vanishes !!:confused:

--
J

Sorry to hear that. I am using Gutsy, have downloaded the Edgy package from their web site and mine works fine:
[http://dfast.sourceforge.net/download.html](http://dfast.sourceforge.net/download.html)

Maybe if you issue "wxdfast" from a console, you may have an idea on what the problem is by checking out the messages.

---

### Post by rogerdean on 2007-10-29
Bingo! the edgy package from their own site works in gutsy, but the getdeb fiesty package does not...
Thank you!

EDIT: and it's faster than downthemall
link to package working for me in gutsy 
[http://prdownloads.sourceforge.net/dfast/wxdfast_0.6.0-1_ubuntu_i386.deb?download](http://prdownloads.sourceforge.net/dfast/wxdfast_0.6.0-1_ubuntu_i386.deb?download)

---

### Post by erginemr on 2007-10-30
Glad to hear that rogerdean. I was using gtm before, but am planning to ditch it and start using wxDownload Fast.

---

### Post by PuppetMaster2070 on 2007-12-21
[COLOR="Blue"]For wxdfast i found the answer and I hope it works

from the terminal run the program with this command:[/COLOR]

[COLOR="Red"]wxdfast --notray[/COLOR]

[COLOR="Blue"]and if it worked just fine

edit the run file from: Applications/Internet/Wxdfast

and then type the mentioned command...

and Keep me updated[/COLOR]

---

### Post by hyper_ch on 2007-12-21
d4x is multi-threading, isn't it?

---

### Post by rogerdean on 2007-12-24
seems the package from getdeb still crashes for me, even with the notray option. am having more luck with the one linked to above...

---

### Post by kpkeerthi on 2007-12-24
> **hyper_ch said:**
> d4x is multi-threading, isn't it?

Yes. It is. Of all the download managers, I find this to be the best. 
> Multithreaded (split downloads)
> Scheduling capabilities
> Bandwidth throttling (1-click low/medium/high buttons, as well as in kbps)
> Integrates with firefox (via Flashgot)
> Has nice skinable themes. 
> Stable

---

### Post by hyper_ch on 2007-12-24
I also like D4X very much.

---

### Post by karlo on 2008-02-20
I recommend Downloader4X, it's similar to FlashGet ... splits the files too and includes a scheduler. Also, I love IDM too, specially with downloading many YouTube videos...:confused:I wonder if it works correctly with WINE.

---

