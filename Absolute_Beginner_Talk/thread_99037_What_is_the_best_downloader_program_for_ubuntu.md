---
title: "What is the best downloader program for ubuntu?"
date: 2005-12-04
forum: Absolute Beginner Talk
---

### Post by racermike1967 on 2005-12-04
Hi, I was hoping to find a downloader program like "Free Download Manager".  Does anyone know of a good program?

---

### Post by 23meg on 2005-12-04
I suggest d4x. It's in the repositories.

---

### Post by racermike1967 on 2005-12-04
What does everyone else think?

---

### Post by Chickenmonger on 2005-12-04
I'd suggest wget. It's command-line based, and it's as simple as typing ```
wget http://url.com/file 
```
at the shell prompt.

---

### Post by tokyovigilante on 2005-12-04
wget is definitely the easiest if you're comfortable with a command-line. 

If you use it, add the -c option (i.e. wget -c <URL for file>) as this will get it to pick up where it left off if it is interrupted. Very good for dial-up etc.

---

### Post by xmastree on 2005-12-04
d4x, eh? Never tried that one, so I got it.


I'm trying to make a launched for it on the top panel, but when I try to select the icon (strangely, named nt.png) I can't see it...

Screenshot shows the launcher config window clearly showing the icon, the error message, and the file manager behind that, also showing it. It's 644, like all the other files there, and I can select others. I tried renaming it but that didn't work either.

:confused: :confused: :confused:

Edit: If I save the PNG in my home directory, it works. why not from /usr/share/pixmaps? It's 644, like the others, and I can use any of those if I like.

---

### Post by lothar_m on 2005-12-05
wget is simply the best. 

Fast, clean and very powerfull.

---

### Post by ssam on 2005-12-05
i use wget -c for big files.

there is gwget, which looks like simple front end to wget.

has anyone used it?

---

### Post by psusi on 2005-12-05
I have never understood this whole download manager thing.  

What's wrong with just clicking the link in a web browser and choosing the place to save it?

---

### Post by Gray. on 2005-12-05
Mostly used by dial-up users so that they can resume. I agree with using wget. Fast and simple. Although this gwget sounds interesting. I'm installing now and I'll post feedback.

*EDIT* I just finished playing with it and it's a nice lean, clean inteface. I'd highly recommend it for people not familiar or particularly fond of the command line. To get it:

sudo apt-get install gwget

---

### Post by psusi on 2005-12-05
[QUOTE=Gray.]Mostly used by dial-up users so that they can resume. I agree with using wget. Fast and simple. Although this gwget sounds interesting. I'm installing now and I'll post feedback.[/QUOTE]

Haven't web browsers been able to resume for years now?

---

### Post by bailout on 2005-12-05
There was a thread on this exact question a few days ago, have a search and see if there are any other suggestions there.

I will repeat what I said then, I recomend Opera's inbuilt dl manager. It supports resume and I haven't felt the need to use anything else on win or linux since switching to opera a few years ago.

You also get the best browser available as a bonus ;)

---

### Post by xmastree on 2005-12-05
Someone said that firefox can resume downloads, but I find that once the d/l stops, that's it. Gotta start over. There's a pause/resume button, but once paused you've killed it.

---

### Post by tokyovigilante on 2005-12-05
Yeah Firefox's download resume has never worked for me, on Windows, Mac OS or Linux.

I usually use jigdo to upgrade/build Dapper CD images, and Azureus for most everything else. If you want to use an integrated download manager in Firefox, get the [FlashGot extension]("http://www.flashgot.net") for Firefox, which will integrate into the wget frontends gwget and KGet for Gnome and KDE respectively.

---

### Post by xmastree on 2005-12-05
I prefer to use a separate program anyway. Browsers can crash, and you don't want to keep all your eggs in one basket.
It's not nice losing 99% of a huge download because something in a website makes your browser misbehave.

---

### Post by bored2k on 2005-12-05
wget over here. 90% of the time i download stuff using links, so wget -c does the job greatly. no bloat and it's wicked simple.

bittorrent > wget > *

---

### Post by korami on 2005-12-06
[QUOTE=ssam]i use wget -c for big files.

there is gwget, which looks like simple front end to wget.

has anyone used it?[/QUOTE]

I also use gwget, it's nice, clean and does the job. It also can be integrated into firefox, so that when clicking on a download link, firefox asks me if i want to open the file, download it (via the firefox built-in downloader) or download with gwget.

---

### Post by steve.horsley on 2005-12-06
[QUOTE=bored2k]wget over here. 90% of the time i download stuff using links, so wget -c does the job greatly. no bloat and it's wicked simple.[/QUOTE]

I agree with wget. I often use it in one of the console windows e.g. alt-ctl-f2. That way I can log out the GUI and let the nipper play games while it's downloading.

But why is everyone saying "wget -c"? You don't need this normally. wget will retry after timeouts anyway (patience, grasshopper - it may be some minutes before it retries). You only need "-c" if you have killed the original wget process and are starting a new wget process on a partially downloaded file. 

Steve

---

### Post by janrinok on 2005-12-06
I use aria - but any of the other suggestions will do the trick.  A matter of choice, but at least you have one! Jan

---

### Post by tokyovigilante on 2005-12-06
[QUOTE=steve.horsley]
But why is everyone saying "wget -c"? You don't need this normally. wget will retry after timeouts anyway (patience, grasshopper - it may be some minutes before it retries). **You only need "-c" if you have killed the original wget process and are starting a new wget process on a partially downloaded file. **
Steve[/QUOTE]

Exactly, downloading a Ubuntu ISO for example can take upwards of 24 hours on dial-up, and a lot of people, esp. on laptops etc. won't want their machine on for this length of time.

---

### Post by jwd45244 on 2005-12-06
curl is a very good http and ftp command line tool, also

---

### Post by beelzebub1987 on 2005-12-13
I use to use d4x, but then because of downloading some other programs that it's not compatable with, it won't work. But it doesn't matter because d4x isn't all that great. I use to prefer wget and gwget, but now I've found something new and seems to work a lot faster: aget.
More Info on aget: [http://www.enderunix.org/aget/](http://www.enderunix.org/aget/)
I got it from the repositories. Not sure where exactly though, my sources.list is a bit large.
"sudo apt-get install aget"
and it works just like wget:
"aget [options] URL"

A few other ones that I've found:
"sudo apt-get install debget"
- for .deb files
"sudo apt-get install kget"
- Download Manager for KDE
"sudo apt-get install nget"
- auto-resuming command line NNTP file grabber

---

