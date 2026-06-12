---
title: "re-installing"
date: 2006-06-30
forum: Absolute Beginner Talk
---

### Post by tospig on 2006-06-30
I've searched and read and searched some more but can't find a simple answer:

how do you re-install Dapper?

(and so it doesn't format the hdd).

ta

---

### Post by _simon_ on 2006-06-30
if you don't format you'll end up with a lot of crap on it... unless you mean you have a /home partition and don't want that formatting...

anyway... if you use the dapper desktop cd you can install with or without formatting if you choose to do the partitions manually there is a "re-format" checkbox.

---

### Post by tospig on 2006-06-30
can it be done through the terminal?

I just want to overwrite the current installation, as when I upgraded I didn't upgrade all the files I edited under Breezy, but now they don't seem to be working properly, so I want to try a re-install. (much like you can under windows)

---

### Post by user1397 on 2006-06-30
[quote=tospig]can it be done through the terminal?

I just want to overwrite the current installation, as when I upgraded I didn't upgrade all the files I edited under Breezy, but now they don't seem to be working properly, so I want to try a re-install. (much like you can under windows)[/quote]what do you mean you didn't upgrade all the files you edited?  do you mean system files, like the ones that are in / ?  how were they not upgraded when you upgraded to dapper, they should've!

---

### Post by tospig on 2006-06-30
I had edited them under breezy, and when installing Dapper it asked if i wanted to overwrite these changes or not - i chose not.

(the files are in /etc/gdm)

---

### Post by taurus on 2006-06-30
If you plan to reinstall Dapper, why not format the harddrive so you have a clean system!!!  That would save you a lot of gray hair later instead of just install on top of the old version...  But if you have a seperate /home, then don't format it during the installing process; just mount it on /home.

---

### Post by tospig on 2006-06-30
because I was hoping a reinstall would be the same as it is under windows, where you can just fix broken OS issues without formatting....and therefore not lose any data.

---

### Post by Jagot on 2006-06-30
[QUOTE=tospig]because I was hoping a reinstall would be the same as it is under windows, where you can just fix broken OS issues without formatting....and therefore not lose any data.[/QUOTE]

That isn't reinstalling - thats a system restore.

---

### Post by user1397 on 2006-06-30
so lets clear some things up: do you have a separate /home partition or not?


if you do, reinstalling is practically painless, but you still have to back-up.

if you don't, then you have to backup all your personal files and cerase your entire drive!  (might as well create a seperate /home partition whiule you're at it :p)

---

### Post by tospig on 2006-06-30
> That isn't reinstalling - thats a system restore.

you say potato...


i don't have a seperate /home partition (well, not that I know of - i'm still a newbie and don't know what I'm doing)

If I have to (or rather, should) back-up either way then I may as well just do the quickest and easist thing? I don't have much data on here anyway, I just wanted to quickly fix/reinstall/system restore Dapper.

would starting from scratch and format everything be the best/easiest option? (if so then that gives me another problem - I'm having trouble burning a dapper iso disc.....)

---

### Post by user1397 on 2006-06-30
[quote=tospig]you say potato...


i don't have a seperate /home partition (well, not that I know of - i'm still a newbie and don't know what I'm doing)

If I have to (or rather, should) back-up either way then I may as well just do the quickest and easist thing? I don't have much data on here anyway, I just wanted to quickly fix/reinstall/system restore Dapper.

would starting from scratch and format everything be the best/easiest option? (if so then that gives me another problem - I'm having trouble burning a dapper iso disc.....)[/quote]okay so you have come to this conclusion:  you're going to backup the little data you have, and completely reinstall dapper?

If so, follow the guide in my signature called "downloading and installing ubuntu"

Also, I can help you partition your hard drive correctly with appropriate sizes, if you want to.  How large is your hard drive?

---

### Post by tospig on 2006-06-30
it's only 40Gb 
(this is my spare system I'm using to "learn" linux, and so I don't have much on here - but knowing how to partition might be a good thing)

---

### Post by user1397 on 2006-06-30
[quote=tospig]it's only 40Gb 
(this is my spare system I'm using to "learn" linux, and so I don't have much on here - but knowing how to partition might be a good thing)[/quote]wait, how much ram do you got?

---

### Post by tospig on 2006-06-30
erm, 768mb, pc2100

---

### Post by user1397 on 2006-06-30
okay this is how i would set up your partitions:

10 Gb ext3 for /
25.5 Gb ext3 for /home
512MB for swap space

just follow this guide on how to install it: [SIZE=1][downloading and installing ubuntu]("http://www.psychocats.net/ubuntu/iso.html")[/SIZE]

---

### Post by catlett on 2006-06-30
You should at least make 3 partitions but you could do more if you wanted to get technical. [http://www.linuxplanet.com/linuxplanet/tutorials/3174/1/](http://www.linuxplanet.com/linuxplanet/tutorials/3174/1/)
The 3 main ones you shouold make are swap, root and home.

Make swap twice your ram ,i.e. 256mb ram = 512nb swap.

Make /  root 5gb ( / is the label for root). I never had my root above 3.5gb but some people have posted saying tmp will need more space if you burn dvds. I do not know the exact procedure for buring dvds so you might want to make root 8gb to be safe.

Make home the rest. Home is like My Documents in windows. It will hold all your personal data.

I use gparted live to make my partitions ahead of time [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

Good luck.
[COLOR="Red"]
EDIT[/COLOR] I went to post a reply and then got distracted. I missed the last couple and didn't see that erik already stated everything. Just disregard.

---

### Post by tospig on 2006-06-30
ok, thanks.

however, your guide (erik) on downloading and installing ubuntu - the burning an iso bit is for windows, and i'm using linux.

I've downloaded "ubuntu-6.06-i386.iso", tried right-clicking on it and "write to disc", a pop-up box appears where I can't change any of the options so i just select "write to disc".

another pop-up appears, asking to chose a name for the disc image, and it also asks to save it in a folder. This is the bit i'm confused about - why do i want to save it in a folder?

---

### Post by catlett on 2006-06-30
Use gnomebaker. If you don't have it installed do this ```
sudo apt-get install gnomebaker
``` It will be listed at the top under Applications<Sound & Video
Just launch it from the menu and it has a menu at the top that will say "Burn CD Image"
Just select that and then browse to the dapper iso.

---

### Post by tospig on 2006-06-30
"couldn't find package gnomebaker"

---

### Post by catlett on 2006-06-30
Do you know how to add extra repositories? If not follow this how to. [http://www.psychocats.net/ubuntu/sources.php](http://www.psychocats.net/ubuntu/sources.php) Then run the command again. 

There are repositories that are not enabled when you first install because some of the stuff is not free in some parts of the world. Anyways gnomebaker must be in one of the extra repositories. I have them enabled and I have it.

---

### Post by tospig on 2006-07-01
I followed how to add extra repositories, but after that I still get "couldn't find package gnomebaker"

---

