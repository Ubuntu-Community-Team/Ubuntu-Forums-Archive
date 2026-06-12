---
title: "How do i copy DVD,S"
date: 2007-02-24
forum: Absolute Beginner Talk
---

### Post by skiddly on 2007-02-24
[SIZE="5"][/SIZE]Is there a programme anything like Nero or Clone DVD to use on ubuntu i can play my dvd.s and playback is good and the sound but i need a prog to copy for back ups:guitar: rock on linux

---

### Post by overdrank on 2007-02-24
> **skiddly said:**
> [SIZE="5"][/SIZE]Is there a programme anything like Nero or Clone DVD to use on ubuntu i can play my dvd.s and playback is good and the sound but i need a prog to copy for back ups:guitar: rock on linux

This thread might be of some help [http://www.ubuntuforums.org/showthread.php?t=23440](http://www.ubuntuforums.org/showthread.php?t=23440)

---

### Post by John.Michael.Kane on 2007-02-24
take your pick. all should be in the repo's..
dvd::rip
acidrip
k9copy
Thoggen

---

### Post by ramjet_1953 on 2007-02-25
K9 copy works a charm for me, especially if you want to compress a DVD9 onto a DVD5.

For straight 1:1 copying, K3b does a good job.

Regards,
Roger :cool:

---

### Post by RudolfMDLT on 2007-02-25
Kaffeine or VLC are very good players.

For ripping I use K9Copy, it works beautifully. I rip to ISO.

Linux allows the mounting of ISO's in folders. so I just use this command to mount the ISO image in a folder and play the selected dvd as it where a DVD.

mkdir /Folder
chmod 777 /Folder
mount -o loop -t iso9660 /Source /Folder

Or, after you ripped the ISO, K9Copy can write it back to a new DVD. 

K3b can write and recode the ISO's onto xvid files.

Goodluck and Enjoy!

Cheers,

Rudolf

---

### Post by Chemist on 2007-02-25
I've used K9 for a long time now and found it works brilliantly

---

### Post by skiddly on 2007-02-25
H i again i cannot find k9 copy in add remove,have looked at k3b dont think it does what i want , i need to be able to copy from 1 dvd straight to a new dvd disc like i can with nero recode, or clone dvd i mean copying movies, and things like pink floyd in concert dvd etc etc:confused:

---

### Post by morganGDFP on 2007-02-25
> H i again i cannot find k9 copy in add remove,have looked at k3b dont think it does what i want , i need to be able to copy from 1 dvd straight to a new dvd disc like i can with nero recode, or clone dvd i mean copying movies, and things like pink floyd in concert dvd etc etc

I just installed it from synaptic so it is there.
You probably need to add the extra repositories..
[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_add_extra_repositories](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_add_extra_repositories)

Good luck

---

### Post by skiddly on 2007-02-25
[SIZE="5"][/SIZE][COLOR="DarkOrchid"][/COLOR]Found it i thought it would be in the add/remove prog section im learning something new all the time  many thanks for help skiddly

---

### Post by skiddly on 2007-02-26
Found and installed k9 but tried to copy a couple of movies and it spit them back out do i need something like any dvd as well and if so what is the ubuntu equivalent

---

### Post by 3rdalbum on 2007-02-26
Do you have libdvdcss? You need that library in order to read and copy commercial DVDs.

[https://help.ubuntu.com/community/RestrictedFormats]("https://help.ubuntu.com/community/RestrictedFormats")

---

### Post by skiddly on 2007-02-28
[COLOR="RoyalBlue"][SIZE="5"][/SIZE][/COLOR]Finally got k9 to regocnise disc and it gave me the title etc clicked on copy using k3 k9 copied files k3 burned em and lo and behold will it play no chance its probably me thick as bulls lugs but all i want is to copy a shopbought cd its so easy on bill gates overpriced windows but i cant for the life of me figure it out here yet ](*,) #-o :cry: :cry:

---

### Post by skiddly on 2007-02-28
sorry i meant dvd not cd

---

### Post by skiddly on 2007-02-28
Well finally managed to copy a cd with k3 but no joy ay all with a dvd any help in easy steps will be appreciated is there any extra stuff i need to d/l i want to copy a bought dvd my copy is getting scratched its only the bairns Barney dvd but if it knacks up life will be hell help me copy it before it gets that far please skiddly

---

### Post by morganGDFP on 2007-02-28
hmm..I can't understand why it doesn't work for you..I only installed K9copy and had no problems whatsoever...
Just to verify this I am copying a DVD right now..
Here is what I did:
I had an .iso image already laying on my hard drive so I opened that (file -> open).
That should work if you insert a DVD in the drive aswell, by following these steps:
1. insert source DVD in drive
2. select input device DVDRAM /dev/hda (in my case)
3. file -> open 

now in the "Title" section of k9copy (on the left side) my movie pops up. 
(I tried to put a nice picture here but did not succeed...:) I only managed to get it as an attachment.) 
But as you can see from the picture the DVD movie will be broken down into different Titlesets. 
In my case there is only one since I have already stripped it off all menus and extras. 
You will probably have a bunch of other Titlesets and various menu settings.

I always strip all that **** off and keep only the movie.

What you want to do now is to find the biggest Title (most likely Title 1) and open that. 
Next select what language you want and which subtitles.
and of course the video file...

After you have done that you click Actions -> copy or just click on the "DVD" button.

Now k9copy should start "Authoring" and after that is completed it will ask you to insert an empty DVD in the drive and subsequently burn the movie onto the disc.

This is how I did it and it worked flawlessly for me.

AS I said before though this will give you ONLY the main movie on a DVD without menus, or extras. This way you can squeeze it in on a dvd5 and still keep a decent quality.

Hope this works and if not post what went wrong and hopefully someone who is smarter than me sorts it out for you.

Cheers
Morgan

---

### Post by skiddly on 2007-03-01
could i rip dvd to iso and then burn converting back to dvd if so how

---

### Post by morganGDFP on 2007-03-01
> **skiddly said:**
> could i rip dvd to iso and then burn converting back to dvd if so how

yes you can. just select ISO image as output device instead of DVD...

Did it work to copy that movie by the way?

---

### Post by airtonix on 2007-03-01
also try out devede for turning xvid,divx,mpeg to dvd

---

