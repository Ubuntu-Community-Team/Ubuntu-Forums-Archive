---
title: "Need Dual Boot Advice (another of my computers goes Ubuntu)"
date: 2006-05-06
forum: Absolute Beginner Talk
---

### Post by mybootorg on 2006-05-06
After falling in love with Ubuntu on my laptop, I think I'm ready to make the same move on my home PC.  With one caveat.  The home PC, of course, has all my games on it. World of Warcraft etc.  And though I know that many of them will undoubtedly run just fine on WINE or Cedega, I'm not ready to take the plunge yet.  I don't want to not play World of Warcraft :) But I don't want to end up installing XP again either.

What I've decided to do is run out to the computer store this morning and pickup a new hard drive and install Ubuntu (Dapper) on that, while leaving my XP install pristined.

Once complete, what's the best way to set things up to boot to this Ubuntu / Windows XP on seperate drives option?

PS: Pointing me to a tutorial is fine. I just didn't have much luck this morning finding a tutorial that fit my "one OS per drive, dual boot" scenario.

Thanks in advance,

Craig

---

### Post by Sef on 2006-05-06
This is an excellent tutorial on dual booting.

[http://users.bigpond.net.au/hermanzone/]("http://users.bigpond.net.au/hermanzone/")

---

### Post by confused57 on 2006-05-06
That's how I have my system set up:  Ubuntu master,  Windows slave & I used these 2 threads to set it up,  it's pretty easy, pay particular to the advice by "lha":

[http://www.ubuntuforums.org/showthread.php?t=124989&highlight=Jumper+settings](http://www.ubuntuforums.org/showthread.php?t=124989&highlight=Jumper+settings)

[http://ubuntuforums.org/showthread.php?p=677880#post677880](http://ubuntuforums.org/showthread.php?p=677880#post677880)

The instructions are pretty self explanatory,  at least I know I can disconnect one drive or the other if I have problems.

I had forgotten all about this thread, but glad it worked out for you.  Thought I'd just answer here rather than bumping the thread back,  I try to give back when I can, especially if it's something I've personally encountered; I've received invaluable assistance from others and I'm just beginning to be able to return the favor(s).  That's what makes this such a great forum and community.

---

### Post by mybootorg on 2006-05-08
[QUOTE=confused57]That's how I have my system set up:  Ubuntu master,  Windows slave & I used these 2 threads to set it up,  it's pretty easy, pay particular to the advice by "lha":

[http://www.ubuntuforums.org/showthread.php?t=124989&highlight=Jumper+settings](http://www.ubuntuforums.org/showthread.php?t=124989&highlight=Jumper+settings)

[http://ubuntuforums.org/showthread.php?p=677880#post677880](http://ubuntuforums.org/showthread.php?p=677880#post677880)

The instructions are pretty self explanatory,  at least I know I can disconnect one drive or the other if I have problems.[/QUOTE]

Folks,

Thank you both for the advice on dual booting. I eneded up going with "lha's" advice because it was nice, clean and simple.

[quote=lha]You're easiest off if you make Windows drive slave and Ubuntu drive master. Then open terminal (Applications->Accessories->Terminal) and type
```
cd /boot/grub
sudo cp menu.lst menu.lst_backup
sudo gedit menu.lst
```[/quote]

Thanks again!  This forum has really been a blessing as I've learned Ubuntu.  Once I gain my own little collection of knowledge, I will be sure to stick around and help others.

---

