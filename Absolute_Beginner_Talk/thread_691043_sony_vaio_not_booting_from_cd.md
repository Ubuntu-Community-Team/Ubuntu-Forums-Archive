---
title: "sony vaio not booting from cd?"
date: 2008-02-08
forum: Absolute Beginner Talk
---

### Post by danbrazier on 2008-02-08
ok - firstly, hello. complete linux-newb here. got a new sony vaio cr21. vista is the most annoying invention on this planet (in my opinion, of course! i'm sure bill likes it.) so i'm gonna completly ditch it and install linux, i'll just be using the laptop for fiddling really - just the net and pics and movies, and that's about it.

i have muchos other pc's, and ahve no data to lose from this laptop - so can be as destructive as i need.

however! i can not for the life of me get this laptop to boot from any linux dvd i've made so far (7 in total!)

anybody got any ideas, after trawling round these forums, and extensive googling i'm at a loss - so HELP!

thanks in advance :)

dan.

---

### Post by seventhc on 2008-02-08
Is it set to boot from cd in the bios?
I would make a back up of vista just in case you decide you want it back.
I have a sony vaio and made the disks....I don't use them, but I did make them.Did you burn the disk correctly?
If your in vista and open the cd, do you see one file or lot's of files?

---

### Post by danbrazier on 2008-02-08
hey cd is first in boot priority... so that's not it.

i don't care about restaore dics - it ahs a partition anyway, but i also have a couple of copies of vista i'm not using anywhere else so are fine to go back on if the worst comes to the worst!

i've burnt just iso files, and also just the contents of the iso's and tgried booting from them both, to no avail... unless of couse anybody knows of a shortcut or something which is meant to make this laptop boot from cd?

as far as i'm aware - you tell it that cd is first priority, and if theres somethign bootable in there, it'll boot from it?

---

### Post by seventhc on 2008-02-08
It will boot from the cd, but the cd probably burned just the iso image.
go here [http://isorecorder.alexfeinman.com/isorecorder.htm](http://isorecorder.alexfeinman.com/isorecorder.htm) download and then it will properly burn the cd.
The iso has to be extracted. once installed you should be able to right click on the iso image and you'll be able to tell it to burn with iso recorder..something like that.

---

### Post by jan quark on 2008-02-08
also a good site to start with is

[http://www.psychocats.net/ubuntu/iso](http://www.psychocats.net/ubuntu/iso)

the cd must be burned at loswe speed and checked for error, search for "validate written data" or "check midsum" in the burning application

---

### Post by danbrazier on 2008-02-08
cool - cheers for that guys - will give it a go now! must... get... linux!

---

### Post by MarkX on 2008-02-08
Like the others said, you have to burn a *bootable* disk.I've burnt .isos before that weren't bootable.  Depending on the burning application, there is often an option like "make bootable CD" to click before doing the burn.
Why are you using DVDs btw? Ubuntu fits on a CD.

---

### Post by danbrazier on 2008-02-08
was waiting for somebody to ask! i don't have any cd's ;) and they're my dads dvd's so i don't mind using them all up trying to get this working!

just burnt the ISO at 4x which is the lowest nero would let me do it - i was looking for a "bootable" option in there... can't see one :S

---

### Post by danbrazier on 2008-02-08
go team you guys :D its installing! thanks alot - see you in 30 mins when i'll probably need to pick your brains again!

---

### Post by kerry_s on 2008-02-08
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

here's the ubuntu how to.

oops, i just saw you got it. :)

---

### Post by seventhc on 2008-02-08
Good Luck ;)

---

### Post by danbrazier on 2008-02-08
ok, so it installed, and asked me to reove disk so it could boot - and it's been sitting there for 10 or 15 mins saying that it's:

"* running local boot scripts (/etc/rc.local)      [ok]

is that right? no desktop or anything yet? i'm really not sure on this process!

---

### Post by seventhc on 2008-02-08
I don't think it should take that long....
hmmm..do you get any errors?

---

### Post by danbrazier on 2008-02-08
it doesn't present any errors - after just ragging my xbox for a bit and trying to come back to it fresh-minded - i hig the power button, and it says something about ending the "gnome display manager" and then comes up with the ubuntu "boot" screen, and then powers down. turning it on again takes it to the same place or being stuck with some things saying that loading scripts was ok etc...

could this be linked with me not choosing a resolution in the setup?

---

### Post by danbrazier on 2008-02-08
oooh, progess?

it says about pressing 'esc' to select from a menu - so i did - and theres an option for recovery? clicking that presents lots more info and writing about loading and setting various things (sys clock and activating swap file etc)

then it stops at:

root@danslaptop:~#

now what?!

---

### Post by seventhc on 2008-02-08
I don't remember changing any settings during setup. It picked my resolution on it's own. 
I have to find the command, you might need to reconfigure x.

root@danslaptop:~# You are in recovery mode

Found it, you can run this in recovery mode
```
dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by danbrazier on 2008-02-08
im just reinstalling it - it gave me the option to select all resolutions that i didn't want to use - so i hit the top one, thinking "don't want that", and it selected it!

unfortunatly my 14" screen and x2300 GPU won't support 1900x1200!

---

### Post by danbrazier on 2008-02-08
still no joy... the standard boot (i.e. turn it on and leave it to it's own devices) simply gets it to a point where it says:

*starting anac(h)ronistic cron anacron        [ok]
*starting deferred execution scheduler atd [ok]
*starting periodic command scheduler crond [ok]
*checking battery state...                           [ok]
*running local boot scripts (/etc/rc.local)     [ok]



i have no idea :S

---

### Post by danbrazier on 2008-02-08
when i press escape on boot, to go to the boot manager thing.... i get these choices:

ubuntu 7.10, kernel 2.6.22-14-generic
ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
ubuntu 7.10, memtest86+

---

### Post by seventhc on 2008-02-08
Thats the normal menu, but I'm not sure why your having a problem especially  since you could use the Live CD...:confused:

---

### Post by danbrazier on 2008-02-08
i don't know why either... it just keeps coming up with that running local boot scripts thing, and does nothing! :( getting frustrated now... can't see what else i can physically do?!

is it something to do with setting up more boot scripts or anything? whatever they are!?

---

### Post by seventhc on 2008-02-08
I'm not sure, maybe someone else here will have an idea or something you can do.

---

### Post by danbrazier on 2008-02-08
i've found some posts on here about graphics card drivers... and they all refer to running the restricted files from ubuntu or something?

thing is - reading through that, it seems to need internet access - not having an OS i presumably have no drivers for the net?

---

### Post by Faud on 2008-02-08
What is the video card that you have in your laptop and did you try installing under safe graphics mode ?

---

### Post by danbrazier on 2008-02-08
ati x2300 for GPU - just trying kubuntu - see if thats any different? although at the mo i'm getting the same "error"

---

### Post by TheDilettante on 2008-02-08
Umm, you're not going to be thrilled about this, but you should try burning a CD.  I have a Vaio NR260E, and while it too has a DVD Writer, I have never made a boot DVD successfully boot, only the CD I burnt by selecting the "Burn CD Image" or equivalent.  On the plus side, I have bootable CD's from most Linux distros at this point, all of which work.

Hope this helps.

---

### Post by danbrazier on 2008-02-08
how do you mean? use live cd and you apparently can install it from there?

i have a bootable iso on dvd (well... 3 now, 2 ubuntu and one kubuntu) and they all do the same thing (kubuntu is a little different in process, but same in result!)

dilettante - any chance of you explaining the exact process and programs you used? i really wanna get this working now - seen so many cool things i want... no... need! to be able to do with this!

---

### Post by TheDilettante on 2008-02-13
Sorry about the delay in response...  Look, I have found that for whatever reason a DVD is no good for my Vaio.  Consequently, you need some program that can write a disc image - NOT a data DVD or anything like that.  What program are you using?  Googling "windows iso" turned up [http://isorecorder.alexfeinman.com/isorecorder.htm](http://isorecorder.alexfeinman.com/isorecorder.htm), which may be more useful for you (still on windows, right?)

I'll look in tomorrow, if you're still checking this post.

---

### Post by danbrazier on 2008-02-27
i'd forgotten all about this post! I just stuck with good ol' faithful xp in the end. although i am about to make a new forray in to linux on my desktop now!

---

