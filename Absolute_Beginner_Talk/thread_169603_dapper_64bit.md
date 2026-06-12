---
title: "dapper 64bit"
date: 2006-05-02
forum: Absolute Beginner Talk
---

### Post by joshrobinson on 2006-05-02
im going to be getting a 64bit amd laptop this weekend.. so im gona download the 64bit dapper.. can i still install i386 packages on it and they run fine? say i find a program i want that doesnt have a 64bit version, the i386 will run fine?

---

### Post by Jason_25 on 2006-05-02
Well you can force install the package but it's not recommended.  If it's only available in a deb I'll extract the deb's contents and install manually.  Even so, it might not run initially or at all, depending on what libraries it needs.

---

### Post by joshrobinson on 2006-05-03
[QUOTE=Jason_25]Well you can force install the package but it's not recommended.  If it's only available in a deb I'll extract the deb's contents and install manually.  Even so, it might not run initially or at all, depending on what libraries it needs.[/QUOTE]

so im better off running the 32bit version of ubuntu?
maybe ill just give the 64bit a shot and if everything doesnt work out switch back to 32bit

do most programs have 64 bit versions also?

---

### Post by Jason_25 on 2006-05-03
I personally think you would be better off with 64 bit if you know what your doing.  Stuff that I know that absolutely doesn't work is wmv9 and flash.  Pretty much everything ubuntu ships with by default has a 64-bit equivalent, or at least runs in 64.

---

### Post by joshrobinson on 2006-05-03
[QUOTE=Jason_25]I personally think you would be better off with 64 bit if you know what your doing.  Stuff that I know that absolutely doesn't work is wmv9 and flash.  Pretty much everything ubuntu ships with by default has a 64-bit equivalent, or at least runs in 64.[/QUOTE]

wmv9 is no problem.. but no flash? thats gona suck :-( half the webpages out there use it nowadays

---

### Post by Jason_25 on 2006-05-03
I don't/wouldn't use flash even if were an option.  I don't appreciate flash pop-ups and flash ads hogging my cpu.  The quality from most flash-based video web sites are appaling so why bother.  If you absolutely need to watch flash videos from sites like youtube there are ways to download the videos individually to view.  Many of these .flv files work on dapper 64 actually.  Even if they don't you can convert them to an acceptable format with ffmpeg.

Edit:Yes you can do that with a chroot.  I have never tried it because I hate flash.  [This]("https://wiki.ubuntu.com/FirefoxAMD64FlashJava?highlight=%28flash%29%7C%28amd%29")
is one way to do it.  There are other ways like a chroot.

---

### Post by joshrobinson on 2006-05-03
you think i can run the 32bit version of firefox just for flash?

i guess your right about flash, most of it is adverts and lil movies on pages.. i guess i can live with it until someone makes a 64bit flash.. i heard adobe is working on one

---

### Post by shapht on 2006-05-03
In your opiniion do you feel the speed advantage of 64 bit out weighs the hassle of running 32 bit apps? It would seem that the whole distro optimized for K8 would be far more nimble than a 1386, but I won't get to test this until I buy my new box.

---

### Post by sophtpaw on 2006-05-03
[QUOTE=Jason_25]I don't/wouldn't use flash even if were an option.  I don't appreciate flash pop-ups and flash ads hogging my cpu.  The quality from most flash-based video web sites are appaling so why bother.  I hate flash.  [This]("https://wiki.ubuntu.com/FirefoxAMD64FlashJava?highlight=%28flash%29%7C%28amd%29")
is one way to do it.  There are other ways like a chroot.[/QUOTE]

[COLOR="Red"][SIZE="6"]I love Flash! It Rocks! It's Fun. And with modern systems what are all the high spec systems for? Plenty of resource to run it - common[/SIZE][/COLOR]

---

### Post by sotua on 2006-06-09
[QUOTE=Jason_25]I personally think you would be better off with 64 bit if you know what your doing.  Stuff that I know that absolutely doesn't work is wmv9 and flash.  Pretty much everything ubuntu ships with by default has a 64-bit equivalent, or at least runs in 64.[/QUOTE]

Never could make gtkpod run in breezy amd64 (chroot or no chroot). Now runs like a dream on dapper i386.

---

### Post by Jason_25 on 2006-06-09
[QUOTE=sotua]Never could make gtkpod run in breezy amd64 (chroot or no chroot). Now runs like a dream on dapper i386.[/QUOTE]
I couldn't speak for breezy since I've hardly used it.

---

