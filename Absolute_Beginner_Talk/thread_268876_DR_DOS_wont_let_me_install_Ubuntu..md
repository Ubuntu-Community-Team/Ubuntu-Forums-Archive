---
title: "DR DOS wont let me install Ubuntu."
date: 2006-09-30
forum: Absolute Beginner Talk
---

### Post by tomtomtom on 2006-09-30
I downloaded Ubuntu the other day, and so far I still haven't gotten it to work. The closest I've got so far is to get something in German to come up.

I burned the Ubuntu image thing to a disk, and then rebooted my machine. As usual, DOS comes up and has a look around. It looks in my CD Drive and starts to boot up Ubuntu. All well and good. Then it decides to boot up DR DOS, which then proceeds to do absolutely nothing.

A few hours spent tonight surfing the web led me to try typing 'dir.' into DR DOS, then typing in the file name of the only executable file there. All this did, however, was get me a load of German.

I would honestly love to be done with Windows, but I'm running out of patience with DR DOS. If someone would tell me how I can bypass it or boot up Ubuntu through it, it would be very much apreciated.
Edit/Delete Message

---

### Post by tagra123 on 2006-09-30
> **tomtomtom said:**
> I downloaded Ubuntu the other day, and so far I still haven't gotten it to work. The closest I've got so far is to get something in German to come up.

I burned the Ubuntu image thing to a disk, and then rebooted my machine. As usual, DOS comes up and has a look around. It looks in my CD Drive and starts to boot up Ubuntu. All well and good. Then it decides to boot up DR DOS, which then proceeds to do absolutely nothing.

A few hours spent tonight surfing the web led me to try typing 'dir.' into DR DOS, then typing in the file name of the only executable file there. All this did, however, was get me a load of German.

I would honestly love to be done with Windows, but I'm running out of patience with DR DOS. If someone would tell me how I can bypass it or boot up Ubuntu through it, it would be very much apreciated.
Edit/Delete Message

This link might help

[http://support.microsoft.com/support/kb/articles/q80/5/70.asp](http://support.microsoft.com/support/kb/articles/q80/5/70.asp)

---

### Post by linear on 2006-09-30
Are you sure you burned the iso as an image? If you burn it as a file, and tell Nero to make it bootable, you'll end up with DR DOS on the CD. This is not what you want.

---

### Post by meng on 2006-09-30
> **linear said:**
> Are you sure you burned the iso as an image? If you burn it as a file, and tell Nero to make it bootable, you'll end up with DR DOS on the CD. This is not what you want.
This is absolutely correct. If you are getting a DR-DOS prompt, then you have used the incorrect method of burning an ISO.

---

### Post by rccharles on 2006-09-30
> **tomtomtom said:**
> I downloaded Ubuntu the other day, and so far I still haven't gotten it to work. The closest I've got so far is to get something in German to come up.

I burned the Ubuntu image thing to a disk, and then rebooted my machine. As usual, DOS comes up and has a look around. It looks in my CD Drive and starts to boot up Ubuntu. All well and good. Then it decides to boot up DR DOS, which then proceeds to do absolutely nothing.

Have you gone into your bios and set the PC to boot from the CD?  Is the cd drive set to boot before the harddrive?

To get into your system bios, you press some key on the keyboard just after the PC starts.  some common keys are esc, f1, f6, del
> **tomtomtom said:**
> 
A few hours spent tonight surfing the web led me to try typing 'dir.' into DR DOS, then typing in the file name of the only executable file there. All this did, however, was get me a load of German.


I have not tried this, but I read it in another post in this forum.  ( Credit goes to the author which my memory has forgotten. )
If your PC doesn't allow you to boot from the CD drive, you can try a slackware install floppy disk.  The slackware floppy allows you to install any version of Linux. See:
[http://www.slackware.com/install/bootdisk.php](http://www.slackware.com/install/bootdisk.php)
> 
bare.i 	 This is the disk to use for installation on most IDE based PCs, with support for nearly all IDE controllers and support for IDE/ATAPI CD-ROM/DVD drives. Most CD-ROM drives made today fall into this category.

There is also another floppy for older cd drives.

Robert

---

### Post by meng on 2006-10-01
The DR-DOS prompt confirms that the system is booting from the CD, but that the CD was not burned correctly, most likely the OP chose the "burn bootable disk" option which installs DR-DOS on the CD, as linear has already mentioned.

This is a common problem, caused by a poor interface on Windows CD-writing software. The solution is well documented, and has nothing to do with BIOS settings.

---

### Post by arkangel on 2006-10-01
use  this 

[http://www.cdburnerxp.se/](http://www.cdburnerxp.se/)

is free and simple just  press  the button or selct the option for  burning iso,  select your ubuntu.iso  and it will do the rest

---

### Post by tomtomtom on 2006-10-01
I tried that, it had two types of ISO. I tried both. The first disk , ISO 1, didn't burn correctly, and the second disk, ISO 2, comes up with DR DOS

---

### Post by tomtomtom on 2006-10-01
What I'm getting from this, by the way, is that I need to burn the disk with ubuntu as an ISO Level 1, and have it non-bootable. Is that correct?

Bootable ISO Level 2 didn't work.

---

### Post by meng on 2006-10-01
I don't understand what ISO level 1 and 2 are, but definitely you should not be making a "bootable" disk; burning the ISO properly will make the CD inherently bootable. What program are you using to burn? Look here, this may clear things up for you.
[http://psychocats.net/ubuntu/iso](http://psychocats.net/ubuntu/iso)

---

### Post by arkangel on 2006-10-01
no you dont have to specify the type , the iso have the right type on it  

in the welcome screen  select option 1  (burn iso image )
then  File >Write disk from Iso ...


select a low speed  to ensure a proper burning 


Edit :
I found  this tutorial, 
[http://www.psychocats.net/ubuntu/iso](http://www.psychocats.net/ubuntu/iso)
good luck  this time

---

### Post by tomtomtom on 2006-10-01
I am using CDBurnerXP Pro 3 to burn the disks. I just tried an ISO Level 1, non-bootable, and it said "Booting from CD/DVD" or something like that, but then Windows loaded!

If I don't find any other method, I'm going to try ISO Level 2, non-bootable, and see if that works. If that doesn't work, I'm just going to have to ask my IT teacher in college tomorrow, and hope he isn't as dim-witted as he seems.

---

### Post by harry555 on 2006-10-01
If you have no luck burning an ISO what about looking for a cheap magazine with a Ubuntu cover disk.  Ubuntu is very popular and you'll prob have no problem finding one with a fully bootable CD.   I have a data cap so I never d.l many cd iso's and I have no DVD burner.

---

### Post by arkangel on 2006-10-01
> **meng said:**
> I don't understand what ISO level 1 and 2 are, but definitely you should not be making a "bootable" disk; burning the ISO properly will make the CD inherently bootable. What program are you using to burn? Look here, this may clear things up for you.
[http://psychocats.net/ubuntu/iso](http://psychocats.net/ubuntu/iso)

dont pull your hair out ;)  just read the [tutorial]("http://www.psychocats.net/ubuntu/iso") that meng and I posted , also check the integrity of the iso using MD5 sum as in the tutorial

EDIT:

there is an official [Howto]("https://help.ubuntu.com/community/BurningIsoHowto") and basically does the same

---

### Post by garicao on 2007-08-05
Hello.  I'm having the same problem as tomtomtom.  I've tried cdburner-xp-pro-3 and roxio easy cd.  I've tried setting the cd-burn as bootable and as non-bootable, and a variety of burn speeds.  The resulting cds all boot (boot sequence starts with cd) to DR-dos and show as a single iso file.  No doubt I have made some mistake.  But I shouldn't have to play guessing games with multiple arcane settings.

Staying with Windows is looking pretty good right about now.

Rant off. Goodnight.

---

### Post by Jerry N on 2007-08-06
I don't know about other CD burning programs but in Nero Burning ROM you select Recorder and Burn Image - from there you just select what ISO or IMG file you want to burn.

I keep seeing this comment about burning at a slow speed. All of the 4 CD/DVD writers I commonly use burn image files just fine at whatever default speed comes up.  I did have a burning speed problem with a Plextor CD/DVD a while back so I replaced it with a Samsung Writemaster (CD/DVD, Dual Layer, Lightscribe) and threw away the Plextor (just barely out of warranty!).  

Jerry

---

### Post by HieroPosche on 2007-08-06
I think I'll be the 5th person in the thread to say this, but the problem seems to be in either the way you burned the ISO image, or the actualy image you're attempting to use.  
First thing I'd do is redownload the ISO file from another source.  Then you want to make sure you're burning it correctly.  If you can get a copy of Roxio easyCDcreator, or Nero (Any one of your friends with a prebuilt PC got one of these free with thier software package) Find the option that either specifically says burn ISO, or just burn image. Drag the new file in there and burn.  There shouldn't need to be any other options you need to worry about.  
I doubt that it matters, but I used DVD's for all of my distro's.  I only did that because some were so bloated they couldn't fit on 2 cd's nevermind 1. 

If none of this works, I'd say order some bootable discs off the web or heading down to a book store and picking up a howto: linux book for ubuntu that comes with an install CD and just update from that. 

Good luck :)

---

### Post by jrusso2 on 2007-08-06
I have used CD burner XP Pro before and it works fine.  Make sure you burn as .iso image.  don't have to pick bootable.

Don't burn as data cd

---

### Post by garicao on 2007-08-06
Thanks for the fast replies!  After a few more coasters, I got a good burn with roxio easy cd & dvd creator, using the following setting:  creator classic --> record disc from image (at half speed).  Do not use "record disc", "finalize disc", or "create disc image".

Sorry to be so grumpy/frustrated last night, but how is someone supposed to know that (for example), to make a bootable ubuntu disc, you can't click the "make bootable" button in CD burner XP Pro?  Or not burn as data cd?

Anyhow, it's done.  Now, to see what it does....

Thanks again.

--garicao

---

### Post by p_quarles on 2007-08-06
> Sorry to be so grumpy/frustrated last night, but how is someone supposed to know that (for example), to make a bootable ubuntu disc, you can't click the "make bootable" button in CD burner XP Pro? Or not burn as data cd?
Because once you click "Download Now" it takes you to a FAQ/help page. One of the links is this one:
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

I do understand your frustration, but it's not due to Ubuntu's lack of good and reliable instructions. After using Windows for a long time, people tend to just get in the habit of skipping the instructions.

---

### Post by garicao on 2007-08-06
Hello, me again. Not to be picky, but i did read the instructions and the relevant faq page.  It suggests burning at a slower speed if there's a problem---type of problem unspecified.  I did that.  It also recommends and gives directions for using Infra Recorder.  Since i have three cd burning programs, i didn't want a fourth. 

The Infra Recorder action "burn image" doesn't exactly match the language used in CDBurner-XPPro3 or Roxio.  Perhaps i should somehow know the difference between "record disc" and "record disc from image"  or that "make bootable" seems not to, but i don't.

The people who gave their time to write the ubuntu burn-to-disc instructions can't be expected to anticipate every newbie problem that might arise.  However, providing instruction for using 2 or 3 of the most commonly used burning programs might be a Good Thing in this case.

Over and out.

--garicao

---

### Post by j3rt on 2007-08-11
well, after banging my head for an hour, I found clues to what I had been doing wrong in here.
Absolutely if you see [dr-dos] you dun burn'd it wrong.
Anyways, just wanted to say great write ups very helpful an intermidiate newbie.

(btw, my mistake was unpacking the .iso AND burning a bootable not an image, fixed both mistakes the second time around).

---

### Post by anewguy on 2007-08-11
I've been a little confused by some of this thread that says burning as an ISO of type x and worrying about it being bootable.  You just want to burn an image, period.  The option should be something like "burn a CD from an image file"  or "burn a CD from an ISO image".  It shouldn't have to prompt about the type or if bootable or not - it is an image that is going to be burned to the disk.

Another very clear indicator that you burned as data and not as data is shown in the how-to mentioned previously.  After you have burned your disk, just reload the CD in Windows and see if the Ubuntu screen shows up.  If you don't see the screen, and if you use Windows Explorer to view the CD, if you see a single large file, and not a bunch of files, you recorded the ISO file as DATA not as an actual CD image.  Perhaps a small clarification is needed for people just starting out who may not know:

The image you download of Ubuntu is an ISO image of a CD.  This means the file you download CONTAINS the ENTIRE CD image, not just the files.  You CANNOT just use your normal burning directions for this type of file - doing so will only COPY the file to the disk.  What needs to happen is to BUILD THE IMAGE of the CD from the file that was downloaded.  That is why you see so many people saying you MUST burn it as an ISO image.  Somewhere in your burning software will be an option like burn from ISO image or burn from image file.  These are the options you want, not the normal "burn a CD" option (may say something like burn a data CD).

So remember when you have a .ISO file, use the "burn from ISO image" or "burn from disk image" option of your CD burning software.  There is no need to worry about it being a bootable disk - the IMAGE that you BUILD the CD from is bootable.  Put the CD back in the drive and let Windows recognize it and see if it starts the Ubuntu window.  If you don't see that window, start Windows Explorer and look at the CD.  If there is only 1 big file on it you did it wrong. :)

---

### Post by HermanAB on 2007-08-11
Yup, an ISO image pretty much *is* a CD (minus the plastic).  So to burn an ISO image, all you got to do is add the plastic to the image...

This is very fast - no need to read all the data and prepare an image then burn to disk, which is what the 'Create a Data CD' process does, since then you will end up with an ISO image inside an ISO image, which is kinda stupid.

One of the reasons why Linux users distribute lots of things as ISO images, is because it is possible to mount an ISO image from a hard disk and make the system believe that it is a CD.  This is incredibly handy sometimes.  Effectively an ISO image makes a very nice super huge archive container that can also be conveniently married with a round piece of plastic.

---

### Post by lemske on 2007-10-19
Old topic, I realize, but I just had this problem myself today and am glad I found the answer here!  

Burned it as an image in Nero and good to go now.  

Thanks again!

---

