---
title: "k3b equivalent for gnome???"
date: 2006-06-01
forum: Absolute Beginner Talk
---

### Post by user1397 on 2006-06-01
is there a k3b-type application for gnome with as many features as k3b?  i'm mainly interested in the burning iso images option, the md5 checking option, and the verifying data option.  i'm pretty sure gnomebaker doesn't have these options, so please don't suggest it. (unless it does have these options and i just dont know about them!!!)

---

### Post by _simon_ on 2006-06-01
k3b can be run under gnome :)

---

### Post by 5-HT on 2006-06-01
I'm not aware of any for GNOME that are (currently) as fully-featured as k3b.
I'm not sure if you are aware of this, but Gnomebaker can burn disk images.

As to verifying the burn, Dapper's Gnomebaker (0.5.1) does not have that option.
However, I've found it quicker to just verify the md5 digests on the CD myself instead of relying on k3b's verify option. 

What works for me is to create a file on the disk containing the message digests of the contents of the entire disk (apart from the file itself).
The benefit of doing it this way is that you can then check data integrity at a later date (burned disks will go bad in time).
I would highly recommend that you consider doing something similar.

---

### Post by ComplexNumber on 2006-06-01
[quote=erik1397]is there a k3b-type application for gnome with as many features as k3b?  i'm mainly interested in the burning iso images option, the md5 checking option, and the verifying data option.  i'm pretty sure gnomebaker doesn't have these options, so please don't suggest it. (unless it does have these options and i just dont know about them!!!)[/quote] graveman ([click]("http://graveman.tuxfamily.org/")). there's also nero (a gtk application). 

these are some of the things that graveman will do:
 Graphical tool to burn dvd and cdi, made with gtk. You can: 
>  * Burn audio cd from wav, ogg or mp3.
 * Duplicate cd audio, cd data and dvd data.
 * Create iso images from data cd and dvd.
 * Burn cd and dvd data from iso image.
 * Format cd and dvd rewritable.
 * Burn data cd and dvd with files and directories that you choose.
 * Use drag and drop with nautilus or integrated file dialog.


---

### Post by PingunZ on 2006-06-01
Bonfire all the way

[http://perso.wanadoo.fr/bonfire/](http://perso.wanadoo.fr/bonfire/)

you can install it by adding this repo
```
deb http://ketsugi.com/ubuntu dapper main
```

Grtz PingunZ

---

### Post by user1397 on 2006-06-01
[quote=_simon_]k3b can be run under gnome :)[/quote]Yes, I know this.  Iim just tired of all those extra dependencies that k3b brings along with it, and theres quite a lot of them too.

---

### Post by user1397 on 2006-06-01
I like gnomebaker, so I guess i'll use 5-HT's option of just checking the md5 sums by myself.  When I open the md5sum.txt file in my iso disc, there's like a million md5sums.  how do i know which one I should be checking?

---

### Post by ComplexNumber on 2006-06-01
**erik1397**
have you looked into graveman yet? or have you decided that its not necessary?

---

### Post by user1397 on 2006-06-01
[quote=ComplexNumber]**erik1397**
have you looked into graveman yet? or have you decided that its not necessary?[/quote]ComplexNumber, I have decided that it is unnecessary, because i'm mainly interested in burning iso disc images (ubuntu, of course :D)  and i like veryfying that the disc is safe to use and not corrupted.  For example, if i use k3b, i would let it process the md5sum test first, then i would check the option to verify data, and lastly, i would actually do the "check for defects" option in the 6.06 desktop cd!!! (yes im a bit nuts, but when it comes to corrupt iso's, you don't want it to take half of your hard drive with you!)

---

### Post by 5-HT on 2006-06-01
[quote=erik1397]I like gnomebaker, so I guess i'll use 5-HT's option of just checking the md5 sums by myself.  When I open the md5sum.txt file in my iso disc, there's like a million md5sums.  how do i know which one I should be checking?[/quote] 
For recursively checking directory trees, md5deep comes in really, really, really handy.

It's in Dapper's repos and is also an easy compile.

Once you have md5deep, the following commands may be of help to you:

** i) **To create a file with the md5sums:

```
 md5deep -rl {directory} > {name_of_file_to_create} 
``` The 'l' option in there is very important as it will make md5deep use relative paths for the digests. 
As you will be burning this file, you will need relative paths. If you use abosolute paths, you will not be able to verify the disk (well depending on the directory structure).

e.g., /home/foo/bar/somefile will probably not exist on the disc.

The 'r' option is to recusively generate digests for the directory tree


** ii)** To add more directories and files to the file:
```
 md5deep -rl {directory} >> {name_of_md5sum_file} 
``` 

** iii)** To verify all the files whose digests are included in the md5sum file:
```
md5deep -x {md5sum_file} -rw {directory_where_the_files_are_located}
``` 
This command will check the mentioned directory recursively and only output the name(s) and path(s) of files that do NOT match.

------------------
There are many more options that md5deep supports. A quick read of the md5deep manual page covers them. 

Another thing to note (which is relevant to your question) is that you can include multiple lists to use and multiple directories to check (remember that md5deep can be used recursively as well).


As to your question, the answer depends on what you are trying to check.
If there are multiple lists of md5sums, one thing to try would be to add all those lists to the 'verify' command I've noted earlier in the post.

Does this help? If not, post again with any questions and I'll see what I can do.

NOTE: do not actually include { & } in the commands above, they are in there for illustrative purposes.

---------------

Edit: After reading your post again, it looks like you are trying to verify the files in an iso...why don't you just check the digest of the iso itself? That would make things much easier. This post was geared more towards generating a list(s) of md5 digests to verify the integrity of your own optical backups.

HTH

---

### Post by user1397 on 2006-06-02
[quote=5-HT]After reading your post again, it looks like you are trying to verify the files in an iso...why don't you just check the digest of the iso itself? That would make things much easier. This post was geared more towards generating a list(s) of md5 digests to verify the integrity of your own optical backups.[/quote] How would I do that?  and is there a simple gui for md5 sum checking? (like the md5summer program for windows?)

Thanks again for all your help everyone.

---

### Post by AndyCooll on 2006-06-02
The nearest equivalent to K3B in GNOME is Gnomebaker.

:cool:

---

### Post by 5-HT on 2006-06-02
[quote=erik1397]How would I do that?  and is there a simple gui for md5 sum checking? (like the md5summer program for windows?)
[/quote] 
I don't know of any GUI one, but I haven't looked.

If you want to check the iso on a *nix box, easiest thing would be to do the following from the directory that contains the iso:
```
 md5sum name_of_iso 
``` 
This command will give you the md5 digest of the iso, and you can then compare it with the one that should be available from where you downloaded the iso.

HTH

---

### Post by user1397 on 2006-06-02
[quote=5-HT]I don't know of any GUI one, but I haven't looked.

If you want to check the iso on a *nix box, easiest thing would be to do the following from the directory that contains the iso:
```
 md5sum name_of_iso 
``` 
This command will give you the md5 digest of the iso, and you can then compare it with the one that should be available from where you downloaded the iso.

HTH[/quote] Thanks! That's exactly what i was looking for! Simple and quick and easy!!  I don't even think i need gnomebaker, the nautilus cd/dvd creator is good enough for me now!!!

---

### Post by BobSongs on 2006-06-02
If K3B doesn't quite act like it should that's because it needs to be setup properly before hand. Give this command a try```
gksudo k3bsetup
```Things should go well after that. :-)
K3B just acted in a jerky way until I ran that code in a Terminal. After that? No problems.

---

### Post by MetalMusicAddict on 2006-06-02
[QUOTE=PingunZ]Bonfire all the way

[http://perso.wanadoo.fr/bonfire/](http://perso.wanadoo.fr/bonfire/)

you can install it by adding this repo
```
deb http://ketsugi.com/ubuntu dapper main
```

Grtz PingunZ[/QUOTE]
Im with you on this one. ;)

---

### Post by user1397 on 2006-06-02
[quote=BobSongs]If K3B doesn't quite act like it should that's because it needs to be setup properly before hand. Give this command a try```
gksudo k3bsetup
```Things should go well after that. :-)
K3B just acted in a jerky way until I ran that code in a Terminal. After that? No problems.[/quote] it's okay, i've decided that the nautilus cd/dvd creator suits my needs.  (all I do is burn ubuntu iso's and video iso's)

---

### Post by joshrobinson on 2006-06-02
[QUOTE=PingunZ]Bonfire all the way

[http://perso.wanadoo.fr/bonfire/](http://perso.wanadoo.fr/bonfire/)

you can install it by adding this repo
```
deb http://ketsugi.com/ubuntu dapper main
```

Grtz PingunZ[/QUOTE]

no amd64 packages on that repo :-(

---

### Post by steveneddy on 2006-06-02
[QUOTE=_simon_]k3b can be run under gnome :)[/QUOTE]

Dude, K3b can be used under Gnome. I use K3b while running Gnome all the time.

---

### Post by user1397 on 2006-06-03
[quote=steveneddy]Dude, K3b can be used under Gnome. I use K3b while running Gnome all the time.[/quote] I don't get your point; that's exactly what simon said...

---

### Post by Dr. Nick on 2006-06-03
Bonfire is good, but no verify option. I think that is one of the next things to be implemented though.

---

