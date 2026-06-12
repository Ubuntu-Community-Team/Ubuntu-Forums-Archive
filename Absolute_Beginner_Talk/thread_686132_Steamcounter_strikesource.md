---
title: "Steam/counter strike/source"
date: 2008-02-02
forum: Absolute Beginner Talk
---

### Post by Bluestick on 2008-02-02
can somone plz tell me how to install it steam? or a guide on "how-to" ive looked but no luck.
 I do have wine version 0.9.46 installed!

---

### Post by Bluestick on 2008-02-02
oh and BTW my wine is not configured in anyway... maybe i need to do that as well?
running amd athlon 3400++
ATI X850 pro
1.5 gigs of ram
200 gig HD
ubuntu 7.10

---

### Post by Bluestick on 2008-02-02
ok never mind this is never getting installed.. ive read a few tutorials.. none of them make sense! they all for pro.. im a newb..

---

### Post by ajgoyt on 2008-02-03
Hi noticed your post here - Here is from another post a few up from yours- Not actually Source related but Steam related.........

Hope this helps..........


Why don't you try logging out and logging back in, since something seems to be running that we can't get rid of (or even rebooting the whole machine  ). Then run steam from the terminal and see what happens. We just need to get steam fully closed so we can open it again.
I followed this guide when I setup steam + counter-strike - [http://linux.wordpress.com/2007/02/0...source-and-16/](http://linux.wordpress.com/2007/02/0...source-and-16/)
Obviously, all that matters there for you is installing wine + steam, you can deal with the orangle box separately (once you actually get into steam!)

---

### Post by ajgoyt on 2008-02-03
That link is not on the 1st page i had to search here is the actual link see the attach is just a text file - for some reason it will not show the whole link!

Hope this helps...

AJ

---

### Post by Rocket2DMn on 2008-02-03
> **ajgoyt said:**
> Hi noticed your post here - Here is from another post a few up from yours- Not actually Source related but Steam related.........

Hope this helps..........


Why don't you try logging out and logging back in, since something seems to be running that we can't get rid of (or even rebooting the whole machine  ). Then run steam from the terminal and see what happens. We just need to get steam fully closed so we can open it again.
I followed this guide when I setup steam + counter-strike - [http://linux.wordpress.com/2007/02/0...source-and-16/](http://linux.wordpress.com/2007/02/0...source-and-16/)
Obviously, all that matters there for you is installing wine + steam, you can deal with the orangle box separately (once you actually get into steam!)

I posted that a bit ago, but this user's problem is different.  To install steam, you need to download the install file from [http://steampowered.com](http://steampowered.com)
This will give you an msi installation file, so save it to 
/home/*yourusername*/.wine/drive_c/
then open a terminal and run
```
cd ~/.wine/drive_c
wine msiexec /i SteamInstall.msi
```
This will run you through the steam installation.  Note that .wine is a hidden directory in your home folder, so in nautilus you need to hit CTRL+H to see the hidden files and folders.
That link is still a good guide though, and you can skip a lot of stuff since you already have wine (and now steam installed).  You can essentially skip to step 4 after following my directions above, but you need to do "2.3. Downloading Microsoft core fonts" so you can actually see the text in steam!  Here it is for your reference - [http://linux.wordpress.com/2007/02/07/wine-gaming-steam-half-life-half-life-2-counter-strike-source-and-16/](http://linux.wordpress.com/2007/02/07/wine-gaming-steam-half-life-half-life-2-counter-strike-source-and-16/)

---

### Post by chewit on 2008-02-03
Basically

download wine-doors, you have to download the .deb file from here [http://www.wine-doors.org]("http://www.wine-doors.org")


Once installed. You right click of the steam.exe installer, on option should appear at the top, saying "Open with Wine", something like that and it will install Steam.

---

