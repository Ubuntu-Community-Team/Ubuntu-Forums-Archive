---
title: "CD/DVD Creator won't add to CDRW??"
date: 2006-02-15
forum: Absolute Beginner Talk
---

### Post by Yleeyas on 2006-02-15
Hi folks,

I copied some data files to a CDRW using CD/DVD Creator, no problem. When I tried adding more files to the disc I get an error message saying "You do not have permissions to write to the folder". How can this be? I just created the disc. :mad: 

Is this a CD/DVD Creator configurataion problem, or is it actually a 'permissions' problem? In either case, how do I use CD/DVD Creator to add files to a CDRW?

I have looked around in various documentation and other resources but there's no clear answer :confused:

TIA
Yleeyas
:cool:

---

### Post by Ocxic on 2006-02-16
this depends, CD/DVD is a windows program no?
cd's don't have a packet writing support you can't just drag files onto a cd-rw, scince they are mounted read-only.

---

### Post by Yleeyas on 2006-02-16
Hello Ocxic,

CD/DVD Creator is the default CD burning software that came with Ubuntu.

I don't understand your second sentence? I already wrote to the CDRW by dragging and dropping files to it.  :-k

Yleeyas :confused:

---

### Post by psusi on 2006-02-16
Are you trying to drop files onto the cd, or onto the cd creator window?

It should allow you to add more sessions to the cd ( a limited number of times ), but if you delete or replace files, the space won't be reclaimed unless you blank the disc.

---

### Post by Yleeyas on 2006-02-16
Hello psusi,

Well that's half my problem solved. ;)  I WAS dragging to the CD :oops: . Thanx for that correction.

However I still have a problem adding files. I open a Creator window, location 'burn///', and drag a file into it. When I select 'Write to disc', I get the following;
"Erase information on this disc?
This CD-RW appears to have information recorded on it already."

There's no option to 'add' files!
As I recall, when I wrote the disc originally, it did not give me the option of 'multisessions', ie; it 'finished' the disc when the write was done. Is there a way of configuring CD/DVD Creator to allow for handling a CDRW correctly?

Thanx again for your help psusi.

Yleeyas

---

### Post by psusi on 2006-02-16
Hrm... I thought that it used multi session mode.  Maybe your drive doesn't support session at once recording?  I'll have to test it when I get home.

---

### Post by damianubuntu on 2006-02-16
I have a similar problem with trying to write to a 4.7 Gb DVD.  Trying to write 2.1 Gb of data, (prior to an XP delete :-)) but CD/DVD creator says not enough space to store disc image (2150 Mib needed).  New Empty disc, so space should not be a problem.
Being new to writing to CD/DVD as well as Linux, I'm a little confused here.  Do I have to do some kind of disc format first, or something?

---

### Post by Yleeyas on 2006-02-16
Hey there psusi,
(damianubuntu see below)

I've come up with a VERY kludgy way of 'adding' files to previously burned CDRW. First copy (drag and drop) the 'original' contents of the CDRW to a temporary location on your hard drive. Open the Creator window, making sure it's empty to start with, then drag and drop the 'original' files back into the Creator window. Now drag and drop the additional files to the Creator ("burn:///") window. Select "Write Disc", and allow Creator to erase the disk, before re-writing the original files and the new files.

If you can find a way to configure CD/DVD Creator to handle 'multisessions' then  please let me know, cuz this becomes a PAIN :evil: 


Hello there damianubuntu

I don't burn DVDs, but, as psusi mentioned, are you sure you've got the CD/DVD Creator window open? (That's the first thing I had wrong :oops: )
In the browser window for the CD/DVD select from the toolbar at top; GO > CD/DVD Creator then GO > location  ... which should open a location area containing "burn:///".  The window itself should be empy ie; no previously burned files. If there are files in this area, what I've been doing is moving them to trash ( I can't see another way of clearing the window :-? ) Now drag and drop your files into this window, and select 'Write Disc' from the toolbar.
If that's not it then maybe someone else will chip in :p 

Well now to tackle the mysteries of 'ownerships' and 'permissions' ;) 

Yleeyas

---

### Post by damianubuntu on 2006-02-16
Hey Yleeyas
thats more or less what I've been doing.  A few differences: when I put the dvd in the drive, up comes a dialog asking what i want to do with it, burn data, video etc.  when I select burn data, it opens the burn:/// location, which always opens up empty.   So I dump in the files I want to burn and hit write disc.  Thats when it tells me there isnt enough space....

All I can guess at so far is that since I'm running on a small hdd (6gb), by the time I've copied 2gb of files into the burn:/// locations, I've only got about 1 gig left on the hdd, and perhaps thats not enough to get to grips with burning the 2gig to dvd?  Doesn't seem much of an explanation though really...have you tried any other burning software?  Automatix?

Cheers

D

---

### Post by theturner on 2006-02-16
[QUOTE=damianubuntu]I have a similar problem with trying to write to a 4.7 Gb DVD.  Trying to write 2.1 Gb of data, (prior to an XP delete :-)) but CD/DVD creator says not enough space to store disc image (2150 Mib needed).  New Empty disc, so space should not be a problem.[/QUOTE]

Do you have enough *hard disk* space free? The CD/DVD Creator first creates an image file, then burns it to the disk, then deletes the image.

---

### Post by psusi on 2006-02-16
Hrm... blast, I thought this was supported but it looks like it won't use session at once writes.

---

### Post by Yleeyas on 2006-02-16
Hi folks,

Hey psusi;

Well then, looks like I'll have to use my kludged up way of 'adding' files, which is fine by me. I was only backing up small files so it doesn't take that long. I suppose if it gets too painful I can always trackdown more sophisticated s/w :rolleyes: 
But THANK YOU for looking into it for me! :-D 

Hey there damianubuntu;

As I mentioned before, I don't burn DVD's, and for now I'm content with using CD/DVD Creator for my purposes. I haven't tried any other s/w (like K3b or Gnomebaker, etc) As far as your burn problem goes, it looks like **theturner** agrees with you, that it might be an available space problem on your hard drive. I'm not sure what you can do about that, or how to determine if that's the real problem. Sorry, but good luck! ;) 

Thanx for dropping by folks, I'm a newbie, but I think I'm gonna like it here \\:D/ 

Yleeyas

---

### Post by damianubuntu on 2006-02-17
Yleeyas,
I just installed gnomebaker, and everythings works fine now:-)
Gnomebaker let me specify thta the disc was a 4.7 gb dvd instead, and then it said there was enough space.
whether it would solve any of your problems, I don't know, but it might be wroth a crack, it certainly looks a bit more robust than the default creator.
later

D.

---

### Post by Yleeyas on 2006-02-17
Hi damianubuntu,

Well that's good news. \\:D/  I'll keep Gnomebaker in mind for more serious burning than what I'm doing. Thanks for the info. :-D 

Yleeyas

---

