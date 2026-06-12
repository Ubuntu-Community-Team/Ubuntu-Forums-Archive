---
title: "rolling ubuntu back"
date: 2007-10-19
forum: Absolute Beginner Talk
---

### Post by nikef on 2007-10-19
Hi
can ubuntu to taken back a couple days ,like u can in windows 

thanks

---

### Post by hyper_ch on 2007-10-19
If you don't have previous backups you can't.

But what do you want to roll back to?

---

### Post by nikef on 2007-10-19
thanks
i upgraded to gutsy lastnight,

gutsy will not load, i get error i go into grub and choose o/s listed there,it looks like ubuntu ,with some gutsy stuff added 

and thats what i am using at the moment,some1 told me its a grub bug,but i do not have dvd re-writer to copy super grub.i do not understand  :confused:

so i thought ubuntu could be rolled back ,so i got no gusty on there

---

### Post by skymera on 2007-10-19
yeah that is a good point, system restore is very important. incase of serious mishaps.

but as said, it dosent exist here, so back ups only :(

---

### Post by nikef on 2007-10-19
thanks,have no back ups at all :confused:

looks like i will have re-install ubuntu then

---

### Post by skymera on 2007-10-19
thats what i do all the time,
my stuff is kept on windows, so i copy back over.
or on external.

---

### Post by hyper_ch on 2007-10-19
I make a backup every 6h to my 4th harddisk ;) and once a day to my server...

---

### Post by jj97blazer on 2007-10-19
so theres no system restore at all?  i have alot of important stuff as far as bookmarks and what not.  if i cant restore it how can i find everything to copy it as far as bookmarks and pics and stuff goes?

---

### Post by bobpur on 2007-10-20
> **jj97blazer said:**
> so theres no system restore at all?  i have alot of important stuff as far as bookmarks and what not.  if i cant restore it how can i find everything to copy it as far as bookmarks and pics and stuff goes?


I have re-installed enough to try to keep all of my stuff organized to the Home folder and/or Desktop folder. That way, if you bork your system, you can snatch it out of there with out hunting all over to find it. Providing, of course, it is not borked to the point it will not boot. Before that happens, you should've BACKED UP everything to another (External) drive. Yeah, it was a hard lesson for me to learn too:) 
Remember! Hindsight is 20/20 :( :(

---

### Post by jj97blazer on 2007-10-20
well that just sucks i guess.

---

### Post by crimesaucer on 2007-10-20
> **jj97blazer said:**
> so theres no system restore at all?  i have alot of important stuff as far as bookmarks and what not.  if i cant restore it how can i find everything to copy it as far as bookmarks and pics and stuff goes?

Do you mean Firefox bookmarks?

---

### Post by jj97blazer on 2007-10-20
> **crimesaucer said:**
> Do you mean Firefox bookmarks?

yeah.

---

### Post by ofb on 2007-10-20
> **jj97blazer said:**
> well that just sucks i guess.

Well hang on there.

What you're saying is you've got a borked install and no backups, right?

Yes, there is no 'system restore' to roll back to. But your drive isn't fried, so you can still retrieve your data even if you can't fix your install. (Which perhaps you can, but let's clear up the Worst Case Senario first.)

All your personal data and config files are under /home/user_name, where 'user_name' is whatever you log in with.

So you can still do something like boot with a LiveCD and then copy that /home/user_name directory to CDR, or one of your other partitions or drives.

In other words - do a backup after it's "too late".

Some of your config files might be messed up - hard to say what a borked install had played with - but your data will be just fine.

Making sense? So what have you got there for LiveCDs, and other partitions or drives? Was this a dual boot machine?

---

### Post by jj97blazer on 2007-10-20
im runnin a livecd now.  no partitions.  not a dual boot.  its a dell laptop.  can i reinstall on a new partition and go into the old partition and retreive the information i need?

---

### Post by crimesaucer on 2007-10-20
> **ofb said:**
> Well hang on there.

What you're saying is you've got a borked install and no backups, right?

Yes, there is no 'system restore' to roll back to. But your drive isn't fried, so you can still retrieve your data even if you can't fix your install. (Which perhaps you can, but let's clear up the Worst Case Senario first.)

All your personal data and config files are under /home/user_name, where 'user_name' is whatever you log in with.

So you can still do something like boot with a LiveCD and then copy that /home/user_name directory to CDR, or one of your other partitions or drives.

In other words - do a backup after it's "too late".



That sounds like the best way, then you can at least save your data and bookmarks, which is in your .mozilla/firefox/profile_numbers.default/bookmarks.bak


Then you can import that file into your next install, but you probably know that. (if you don't know how to import in, click: Bookmarks-->--Organize Bookmarks ... then click... File-->--Import File ... and just import the bookmarks.bak file)

---

### Post by ofb on 2007-10-20
> **jj97blazer said:**
> im runnin a livecd now.  no partitions.  not a dual boot.  its a dell laptop.  can i reinstall on a new partition and go into the old partition and retreive the information i need?

Um... yeah, in theory, but I'm not going to recommend partitioning. If something goes wrong during that, then you are definitely out of luck. (You shouldn't be feeling lucky right now. ;))

It'd be much better to get a copy of your stuff off that drive. You got no CDR writer then? How about another machine to transfer the files to over the network? 

Or even FTP them to some account you have? You could at least do that with critical items. Like if you were really desperate you could do things like zip up your bookmark files and mail them to your Gmail account, but I'm hoping we don't have to get that silly.

---

### Post by jj97blazer on 2007-10-20
cool deal.  ill try it and hope it works.  thanks for the help guys.

---

### Post by jj97blazer on 2007-10-20
i have a cdr on this machine but i runnin the livecd with it.  i have a network i just have to get on it and fiddle with it.  yeah i was thinkin about just emailing them to my self.  this is the second time its crashed.  but at least this time my hard drive still works.  i just put it in.  both times it crashed unbuntu lasted about a month and a half and then boom, dead.  is there a more stable OS?  i like linux based stuff.  i tried the new fedora but i couldnt ever get it to go wireless so i said screw it and installed unbuntu again.  thanks again for all yalls help.

---

### Post by ofb on 2007-10-20
> **jj97blazer said:**
>  both times it crashed unbuntu lasted about a month and a half and then boom, dead.  is there a more stable OS?

I would never say that Ubuntu doesn't crash, but "boom, dead"? Sounds like you got some flakey hardware troubles going on.

As far as stable goes, yeah Ubuntu is good. I'd say there's no point shopping around.

For flakey hardware... geeze it could be so many things. A while back we had terrible trouble with bad capacitors throughout the industry. There was a bad batch of electrolyte that polluted most everything. Sometimes the caps would just blow (nice 'pop' sound, a little smoke, a bad smell) and sometimes they would only swell. Those are the worst, because it's not a complete failure, and what happens is you get random crashes. Those were a total [I can't say that here] to trouble-shoot.

EDIT: by the way, if you can get a copy of a distro like Puppy Linux, then it will load into memory and free up your drive for burning.

---

### Post by jj97blazer on 2007-10-20
it didnt really go boom.  i was just using it as a good descriptive word.

---

### Post by cotcot on 2007-10-20
> **nikef said:**
> thanks
i upgraded to gutsy lastnight,

gutsy will not load, i get error i go into grub and choose o/s listed there,it looks like ubuntu ,with some gutsy stuff added 

and thats what i am using at the moment,some1 told me its a grub bug,but i do not have dvd re-writer to copy super grub.i do not understand  :confused:

so i thought ubuntu could be rolled back ,so i got no gusty on there

It would improve the chances on help if you supply some more info. You get a error on grub. Which error ?

Do you have a CD reader and  liveCD avaible ?

---

### Post by FrozenFlame22 on 2007-10-20
> **ofb said:**
> 
For flakey hardware... geeze it could be so many things. A while back we had terrible trouble with bad capacitors throughout the industry. There was a bad batch of electrolyte that polluted most everything. Sometimes the caps would just blow (nice 'pop' sound, a little smoke, a bad smell) and sometimes they would only swell. Those are the worst, because it's not a complete failure, and what happens is you get random crashes. Those were a total [I can't say that here] to trouble-shoot.

My last computer was doing just fine for over five years before it died to capacitor failure. Just happened to be at the same time I was installing Ubuntu for the first time. ](*,)

---

### Post by argie on 2007-10-20
If you want to backup all your stuff, all you have to do is backup your home folder. All your personal settings are saved there under dot folders like .mozilla, .gnome and stuff like that.

---

### Post by hyper_ch on 2007-10-20
System restore is an unnecessary feature that makes you think you are safe...

However if you do have system restores and no backups and if then your harddisk fails (and one did so for me once) then all your data is gone...

MAKE BACKUPS on a regular base on a different harddisk, preferably onto a different computer, preferably onto a different remote computer!

Linux makes that quite easy.

---

### Post by ofb on 2007-10-20
> **hyper_ch said:**
> Linux makes that quite easy.

[http://www.psychocats.net/ubuntu/backup](http://www.psychocats.net/ubuntu/backup)
[http://ubuntuforums.org/showthread.php?t=35087](http://ubuntuforums.org/showthread.php?t=35087)

Anyone have a link for a more GUI- oriented method for Ubuntu's more GUI-oriented intended users?

A small trouble with Ubuntu is online advice is written by people who started well before the beginner, so they tell how to do things in the way they know -- which misses any GUI improvements that were recently introduced. Have we got anything like that for backups yet?

"Only wimps use tape backup: _real_ men just upload their important stuff on ftp, and let the rest of the world mirror it ;) " -Linus Torvalds

And yes, I've relied on the two-drive method for years. Then I lost two drives at once. Having an off-site copy is a good idea.


EDIT: looks like GUI backup is in the works
[https://wiki.ubuntu.com/UbuntuHomeBackup](https://wiki.ubuntu.com/UbuntuHomeBackup)

---

