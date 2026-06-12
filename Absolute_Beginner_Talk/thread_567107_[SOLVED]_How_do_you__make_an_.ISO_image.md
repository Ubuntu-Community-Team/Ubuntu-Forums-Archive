---
title: "[SOLVED] How do you  make an .ISO image?"
date: 2007-10-04
forum: Absolute Beginner Talk
---

### Post by gshockxc on 2007-10-04
Okay, this can't be good if I'm already having trouble burning a CD.  I'm talking about Windows XP here.  I realize this is a Ubuntu forum, but I'm sure that most of us were Windows users at one point or another.  I can't even get OUT of Windows, nevermind getting IN to Ubuntu.  :frown:

  I'm hoping that someone here can  help me.  I downloaded Ubuntu 7.04, and I'm trying to burn an image CD.  The laptop I used to burn the disk was running Windows XP and didn't have any special CD software.  

How can I burn an .ISO image?  What do I have to do in Windows to be able to do this?  Or can I?  Do I need another program to be able to burn the image?

I just dragged and dropped the file I wanted to burn.  But the 'wizard' (stupid name, it's only as smart as it's user) didn't give me any options to select a different format.  I've done this with other CD burn programs a number of years ago.  But I didn't have that option on this machine, and I didn't have the time to download something else.

If you're not put off by my apparent lack of knowledge, I would appreciate any help that anyone can provide.  

(Don't be misled.  I'm a mechanical engineer, and pretty comfortable around computers.  I just don't know the details to a lot of things.  I know the basics.)

---

### Post by alwiap on 2007-10-04
try downloading a program like magicISO ([http://www.magiciso.com/download.htm](http://www.magiciso.com/download.htm))

and then dragging the file onto the program, or opening it with the program, then you should be able to burn it I believe.

---

### Post by AliL on 2007-10-04
Here's a page from the Ubuntu wiki, it's how I got an ISO onto a CD so I know it works:
[https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28burn%29%7C%28iso%29](https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28burn%29%7C%28iso%29)

Hope this helps,
AliL

---

### Post by gshockxc on 2007-10-04
> **alwiap said:**
> try downloading a program like magicISO ([http://www.magiciso.com/download.htm](http://www.magiciso.com/download.htm))

and then dragging the file onto the program, or opening it with the program, then you should be able to burn it I believe.

Awesome, thanks.  I can't wait to get started.  I appreciate the help.

---

### Post by RussianVodka on 2007-10-04
Firs make sure that your computer has a CD burner.

I haven't had to burn an ISO in Windows in a long time, and in Linux I just use K3b, but you can google "burning ISO windows" and look for a guide that makes sence to you.

Windows by defult doesn't come with ISO burning software, so you will need to download a special program. You can either get one that only burns ISO's, or one that is capable of burning anything and everything, it's up to you.

I've used Nero Burning ROM ([http://en.wikipedia.org/wiki/Nero_burning_rom](http://en.wikipedia.org/wiki/Nero_burning_rom)) and it works great. But it's commercial software and will cost you a pretty penny. But you're free to try the tial version if they have one.

---

### Post by h2gofast on 2007-10-04
[http://www.petri.co.il/how_to_write_iso_files_to_cd.htm](http://www.petri.co.il/how_to_write_iso_files_to_cd.htm)
[http://isorecorder.alexfeinman.com/isorecorder.htm](http://isorecorder.alexfeinman.com/isorecorder.htm)

those links should do the trick. 
For most questions you will have google is your friend, or search these forums.

An iso is a disk image, it is not a file folder or directory.  The disk image isn't readable until your computer knows to look at the image as a cd/dvd.  Two ways of getting your your computer to read it.  Use the correct program to burn the image to a cd, or use the correct program to look at the iso.  For your purposes follow the links above and use isorecorder or another program like it burn the iso to disk and you're off.
cheers,
h2.

---

### Post by gshockxc on 2007-10-04
You guys are great.  Thanks for all the help.

---

### Post by buntunub on 2007-10-04
There is always the good 'ol command line...

First, cd to the directory that contains the files you wish to burn to an ISO image, then

[PHP]$ mkisofs -R -J * | cdrecord -v dev=/dev/sr0 -[/PHP]  (or whatever the path to your cd recorder is)

If you dont know for sure what your cd recorder path is, then just run 

[PHP]$ cdrecord -scanbus[/PHP]

Which will give you something like 0,0,0 which you would then substitute in place of the dev=/dev/sr0 part above.

---

