---
title: "Call me Dumb....!"
date: 2005-08-20
forum: Absolute Beginner Talk
---

### Post by Jack-UK on 2005-08-20
Hey guys - Im new Ubuntu and i came across it via a friend who recommended it to me. 

So far I have downloaded and burnt the ISO as an image onto a CD.... The only thing is that for some reason (my computer is 2 months old) and it wont boot from CD and ive changed the boot prioty in the BIOS. I have found that when i reinstall xp i have to use my boot disks. So i was wondering if Ubuntu had something similar that i could put in floppy as it reads that first..

Cheers Guys
Jack

---

### Post by heimo on 2005-08-20
Welcome on Ubuntuforums!

Looks like this could do it:
[http://www.ubuntuforums.org/showpost.php?p=39265&postcount=2]("http://www.ubuntuforums.org/showpost.php?p=39265&postcount=2")

---

### Post by Jack-UK on 2005-08-20
Whats the link to download - I cant seem to actually find the download link.

Jack

---

### Post by Gary Powers on 2005-08-20
Forgive the obvious question Jack, but you did check the md5sum on the download?  That can prevent a boot of the .iso disk.

Gary

---

### Post by Jack-UK on 2005-08-20
lol again call me dumb im not a complete computer wiz so i dont know what i need to do.... I can install xp and stuff and know how operate them.... so if i could be cheeky and ask for a step guide or something?

Jack

---

### Post by Muhammad on 2005-08-20
I have to Ubuntu Hoary Install CD's, onle one of them is capable of booting, and I dunno what the hell is wrong with the other one...

Did you extract the files in the iso image before burning the it on the CD?

---

### Post by Jack-UK on 2005-08-20
i burnt the ISO as an image directly onto a CD so i dont think i extracted

---

### Post by kvidell on 2005-08-20
[QUOTE=Jack-UK]i burnt the ISO as an image directly onto a CD so i dont think i extracted[/QUOTE]
 Was this with  Nero?
I'm not sure but I think sometimes you have to tick the "Bootable" flag before you burn the ISO.

You burnt it correctly if you didn't extract, btw.

---

### Post by Jack-UK on 2005-08-20
I used nero yes

---

### Post by az on 2005-08-20
[QUOTE=heimo]Welcome on Ubuntuforums!

Looks like this could do it:
[http://www.ubuntuforums.org/showpost.php?p=39265&postcount=2]("http://www.ubuntuforums.org/showpost.php?p=39265&postcount=2")[/QUOTE]


Smart Boot Manager is on the install cd.  It is in the install directory.

cd /cdrom/install

sudo dd if=sbm.bin of=/dev/fd0

(I cannot remember if that is the exact filename....)

---

### Post by xmastree on 2005-08-21
[QUOTE=kvidell]Was this with  Nero?
I'm not sure but I think sometimes you have to tick the "Bootable" flag before you burn the ISO.
[/QUOTE]No, that's not the way with Nero.

If you're doing it correctly there isn't an option so select bootable.

What you do is create a new CD from 'disk image or saved project' from Nero's menu. Then when it asks you for the file, select the ISO you downloaded.

Others have fallen into this trap, and ended up with a bootable disc containing one file, the ISO. It boots into some weird version of DOS which is built in to Nero, and they think that because it's different it must be linux...

Once the CD has been made, it should be possible to see files and directories on it. Use explorer to browse to the CD, if you see one big file, the ISO, you've done it wrong.

---

### Post by Jack-UK on 2005-08-21
When i explored the CD I see all the directories 

.disk
dists
doc
install    etc

So if i see that ..... have i done it right? As when i did on nero i burnt ISO as an image.

Really appreciate the help guys,

Jack

---

### Post by lothar_m on 2005-08-21
[QUOTE=Gary Powers]Forgive the obvious question Jack, but you did check the md5sum on the download?  That can prevent a boot of the .iso disk.

Gary[/QUOTE]


@jack-uk: did you check the md5sum of the iso?

---

### Post by Jack-UK on 2005-08-21
whats the 'md5sum' i cant say i checked it as i have no idea what is it. 

jack

---

### Post by heimo on 2005-08-21
[QUOTE=Jack-UK]whats the 'md5sum' i cant say i checked it as i have no idea what is it. 

jack[/QUOTE]

It's a way to make sure your file is ok (checksum value). Compare the output of md5sum to the value listed in MD5SUMS file in the same directory you downloaded the iso file from, it should match.

[http://www.linuxiso.org/viewdoc.php/verifyiso.html]("http://www.linuxiso.org/viewdoc.php/verifyiso.html")
[http://www.md5summer.org/]("http://www.md5summer.org/")
[http://www.openoffice.org/dev_docs/using_md5sums.html]("http://www.openoffice.org/dev_docs/using_md5sums.html")
[https://wiki.ubuntu.com/VerifyIsoHowto]("https://wiki.ubuntu.com/VerifyIsoHowto")
[http://www.kana.homeip.net/index.php?i=45]("http://www.kana.homeip.net/index.php?i=45")
[http://www.nullriver.com/index/products/winmd5sum]("http://www.nullriver.com/index/products/winmd5sum")

---

### Post by Jack-UK on 2005-08-21
md5sum - i see that file as a text file in the main directory, what value do i check to make sure it matches and to what other file do i need to match it with.

Jack

---

### Post by xmastree on 2005-08-21
That text file contains the checksums of all the files on the CD. You need to find a windows/dos version of md5sum to actually check your files against that list.

A quick google for md5sum will help here.

---

### Post by Jack-UK on 2005-08-21
i downloaded md5sum.exe opened it up.... and it automatically shuts down as soon as i open it.

jack

---

### Post by Mark Bolton on 2005-08-21
How to burn a CD image from the download file.
I just learned a noob lesson.

I downloaded the image ubuntu-5.04-install-i386.iso file.

I copied the FILE onto a cd and tried to boot it. I boots to a DOS prompt and the only wwhw.exe is a disk partionioner in German.

Mistake ?

The CD IMAGE needs to be burned.

A cool program to do this is [http://isorecorder.alexfeinman.com/Beta.htm](http://isorecorder.alexfeinman.com/Beta.htm)

just right click on the ubuntu-5.04-install-i386.iso file after installing it at you are away.

On with the Install :^)

---

### Post by lothar_m on 2005-08-21
[QUOTE=Jack-UK]i downloaded md5sum.exe opened it up.... and it automatically shuts down as soon as i open it.

jack[/QUOTE]


if i'm not mistaken that file has to be run from the cli. otherwise won't work jackie boy

---

### Post by xmastree on 2005-08-21
Yeah, open a command prompt, switch to your CD, and type```
 md5sum -c md5sum.txt
``` and sit back to see what happens.

---

### Post by Jack-UK on 2005-08-21
[QUOTE=Mark Bolton]How to burn a CD image from the download file.
I just learned a noob lesson.

I downloaded the image ubuntu-5.04-install-i386.iso file.

I copied the FILE onto a cd and tried to boot it. I boots to a DOS prompt and the only wwhw.exe is a disk partionioner in German.

Mistake ?

The CD IMAGE needs to be burned.

A cool program to do this is [http://isorecorder.alexfeinman.com/Beta.htm](http://isorecorder.alexfeinman.com/Beta.htm)

just right click on the ubuntu-5.04-install-i386.iso file after installing it at you are away.

On with the Install :^)[/QUOTE]


Ok i burnt it again using that program... burnt ok so i have a fresh copy, 

Whats the cli file?? Now its on the CD what would be an easy of installing?

Jack

---

### Post by Jack-UK on 2005-08-21
[QUOTE=xmastree]Yeah, open a command prompt, switch to your CD, and type```
 md5sum -c md5sum.txt
``` and sit back to see what happens.[/QUOTE]


i typed that in... and it said the md5sum wasn't recognised in the command prompt.

Jack

---

### Post by lothar_m on 2005-08-21
[QUOTE=Jack-UK]

Whats the cli file??

Jack[/QUOTE]

step by step guide to check md5sum

cli is not a file man. cli stands for command line..... to get to the command line in xp you must look in the start menu for something like msdos prompt i guess.....


once there just do 
```

md5sum c:/my crappy documents/or whatever/something.iso

```

the command will return a number.... then all you have to do is check if that number is the same as the one in the text file.

if it is so, then the download of the iso went ok. 
if the numbers don't match the you got a corrupted iso file.

hope this helps

for more on md5sum sintax check this link
[click](http://www.delorie.com/gnu/docs/textutils/md5sum.1.html)

---

### Post by Jack-UK on 2005-08-21
i put in the code

[http://www.einteractive.org/images/sceenshot.JPG](http://www.einteractive.org/images/sceenshot.JPG)

It may be like not very difficult for you guys but i have no idea like what im doing.

Jack

---

### Post by lothar_m on 2005-08-21
don't worry man .... we're here to give you a hand..... i came from 5 years with windows..... i didn't know shit about computers either..... just be patient.


unlike ubuntu, windows doesn't come with md5sum installed... so download it from
[md5sum](http://etree.org/cgi-bin/counter.cgi/software/md5sum.exe) 

then try it out and give us some feed back

---

### Post by Jack-UK on 2005-08-21
i downloaded it.... and im really dumb..... but its the .exe that opens then shuts itself straight away.

Jack

---

### Post by lothar_m on 2005-08-21
but have you tried it from the command line??

---

### Post by TristanMike on 2005-08-21
As heimo suggested, this [http://www.nullriver.com/index/products/winmd5sum](http://www.nullriver.com/index/products/winmd5sum) md5 checksum program has a nice GUI (graphical user interface) and it works, my buddy used it the other nite to verify his. If you are having trouble, try this one out.....

Sorry to jump in like that.......

---

### Post by Jack-UK on 2005-08-21
after i find that the files are not currupted how do i go about the download?

---

### Post by lothar_m on 2005-08-21
so you checked the md5sum and the iso is ok....

you allready said that burned the iso as an image....

you also said that you changed your bios settings to boot from cd drive.....

at this point i'm out of ideas... maybe your hardware has some kind of problem.... have you checked if it is supported?

---

### Post by Jack-UK on 2005-08-21
Hey - I just keep wondering is there any boot disk that can be used as i know for a fact when thats workin it will trigger it...

I just dont know if there is a boot disk for ubuntu

---

### Post by RastaMahata on 2005-08-21
found this on google.
[http://btmgr.sourceforge.net/3.7/sbminst.exe](http://btmgr.sourceforge.net/3.7/sbminst.exe)
It's a floppy boot manager that will let you boot your Ubuntu Install CD.
Good Luck.

---

### Post by Jack-UK on 2005-08-21
[QUOTE=RastaMahata]found this on google.
[http://btmgr.sourceforge.net/3.7/sbminst.exe](http://btmgr.sourceforge.net/3.7/sbminst.exe)
It's a floppy boot manager that will let you boot your Ubuntu Install CD.
Good Luck.[/QUOTE]


Hmm that just seemed to open straight away then close its self.. That would have been a massive help

---

### Post by RastaMahata on 2005-08-21
[QUOTE=Jack-UK]Hmm that just seemed to open straight away then close its self.. That would have been a massive help[/QUOTE]
 then follow these instructions... they seem more simple :P
[https://wiki.ubuntu.com/SmartBootManagerHowto/](https://wiki.ubuntu.com/SmartBootManagerHowto/)

---

### Post by Jack-UK on 2005-08-21
Thank you ever so much!! I got it to work now and Im sooo happy.... this is better than England beating Austrailia for the Rudgy World Cup!!!!

And to everyone else thank you so so much for all the help and things as im sure you all know im not very good at this stuff.... so if i can understand this ..... a dog can!!

WOOOO

Jack

---

### Post by Jack-UK on 2005-08-22
Hey guys - Me again

When I was on XP in my cmputer it use to list like all my drives and things, I had a D drive with all my photos and meida on...I cant seem to figure out how to access it. I was just wondering if anyone knew how to get it back?

Thanks Guys
Jack

---

### Post by xmastree on 2005-08-22
Well, what is that drive? is it a second partition on your main hard drive? where is ubuntu installed?
Wherever that drive is, you need to mount it, [**this**](http://ubuntuguide.org/#mountunmountntfs) tells you about it, but remember, if its ntfs you can't write to it, you can only read fron it.

If it's a partition, it will probably be /dev/hdb5

---

