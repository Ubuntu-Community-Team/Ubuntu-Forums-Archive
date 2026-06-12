---
title: "help--still can't find a reliable ubuntu download mirror"
date: 2006-02-12
forum: Absolute Beginner Talk
---

### Post by lenny45 on 2006-02-12
ok----i went to 2 different sites and downloaded the ubuntu 5.10-live-i386 for cd. twice i burned them to cd's in Nero. the CD's burned fine. i tried both on my desktop. i tried them both on my laptop. Nada....:confused: 

i put the Mepis disk i burned last night in and it works fine.

can anybody pinpoint a location for a reliable download of ubuntu live? thanks....

---

### Post by heimo on 2006-02-12
I expect you do burn the images using "burn from disk image" or similar functionality and not just the .iso file as is to the disk? So what happens, does it try to boot at all or do you run into some kind of errors / warnings? 
[https://wiki.ubuntu.com/BurningIsoHowto](https://wiki.ubuntu.com/BurningIsoHowto)

Verify the iso file so you know it's not the cause for problems:
[http://www.linuxiso.org/viewdoc.php/verifyiso.html]("http://www.linuxiso.org/viewdoc.php/verifyiso.html")
[https://wiki.ubuntu.com/VerifyIsoHowto]("https://wiki.ubuntu.com/VerifyIsoHowto")

Burn the CD using slow speed, like 4x.

---

### Post by lenny45 on 2006-02-12
thanks heimo....

i downloaded the iso to my c drive. i put a cd in and pointed my Nero to the file. i reduced the speed to 24x (last night i got a good Mepis cd at 32x). 

so your saying i should go ultra slow on the burn and check the verify burn box?

is there anything else i should add or do? these coasters are getting un-sitely.....:)

---

### Post by engla on 2006-02-12
You should definitely check the md5sum on the files after you downloaded them. In Linux it's "md5sum filename.iso" to calculate it, but I have no idea about window, sorry.

---

### Post by lenny45 on 2006-02-12
i found the isorecorderv2rc1 file. do i unzip this file on windows. THEN add it and the Unbuntu files to my cd burn?

---

### Post by vialick on 2006-02-12
If you can't get it working, maybe you should consider going through shipit and getting some free ones sent to you (it does take a few weeks though)

---

### Post by cyangecko on 2006-02-12
I had trouble burning the ISO originally.  I was using a really cheap generic CD-R.  I switched to a Memorex CD-R and that did the trick.  Also ordered the cd's to be shipped to me. Took a little while, but well worth it.

---

### Post by Bartender on 2006-02-12
lenny -
I've been researching the md5 issue for a coupla weeks now.  I thought this would be easy but nothing ever is...
The download will be one monolithic file.  Checking md5 at this point is relatively easy.  If you go back to the download website and scroll down the page you'll get to a long list of files.  The md5's are the second or third file.  Here, just so we don't get mixed up...

7fbe948be484ba2f4740ab6113890652  ubuntu-5.10-install-amd64.iso
126751a2dc5528c2f9044d9e4ee36d61  ubuntu-5.10-install-i386.iso
8886a26a1da1daa3669ed6e1253bd93b  ubuntu-5.10-install-powerpc.iso
8523ee4b5490c9b77ac4ec5e5a12b2f5  ubuntu-5.10-live-amd64.iso
49f36f8aef009d6403360de23b5a47d4  ubuntu-5.10-live-i386.iso
752c8d641ca486955c7747cac1c8a305  ubuntu-5.10-live-powerpc.iso

See that 2nd one?  That's the md5 for your download.  Do you have the donwload still saved in a folder?

If so, the next step is finding an md5 checker that works for you.  Although this one has been poo-poohed by some Linux aficionados it worked for me...

[http://www.md5summer.org/](http://www.md5summer.org/)

Just download/install, when u click on it you get a familiar-looking directory tree showing your folders. Hilite (left-click) on the folder where your download is and click "Create Sums".  You get a new window showing what md5summer sees in that folder. Hilite the ubuntui-386.iso file, and click "Add".  It moves the file to the right column.  Click "OK", a new window pops up showing progress.  If md5Summer was able to generate a checksum you'll get a little green globe next to the file name and a long checksum on the right side.  Compare that number to the one from the download website.  If it matches EXACTLY then your download was OK.  If anyone's gloating that they've got a better md5 checker please contribute.  

On to phase 2.  When you burn that .iso it'll look different.  Explore the CD and you'll see 8 folders and 2 files.  One of the 2 files is just a short README file.  The other is a list of HUNDREDS of md5's, apparently for every single file on the CD. The 8 folders are, as far as I can tell, the actual Ubuntu program, waiting to be installed.

OK, here's the only thing I've been able to come up with so far, but it entails having a "known good" Ubuntu CD.  I pointed md5Summer to the Ubuntu install CD and asked it to Create Sums.  When it went to the second window I told it to Select All.  It made 43 checksums.  When it's done it asks if you want to Save the results.  I saved them to the desktop.  (EDIT: I had to change the file to .txt in order to attach it, got errors if saved in the native format)  md5Summer gave the file a name.  Then I took another Ubuntu CD and tossed it in the tray.  

This time I asked it to Verify Sums.  Md5Summer will check a folder against whatever records it has of a previous scan.  This is so you can check a file or folder that you transferred to a different computer or whatever. So, when you click Verify, it asks for a file to verify against.  I pointed it to the file it made from the first CD, then let it run.  It came back with zero errors, so I *think* what happened here is it says both CD's are identical.  As I said, that only helps you if you have a known good CD.  You could use this method to check the two CD's you already made, which doesn't necessarily do much for you either.  

OK, new plan -I just tried saving a text file of md5Summer's results to this post - I've never attached before so sorry if it didn't work.  This is a low-tech way to do it but you should be able to manually compare the 40+ checksums to the results from your CD.  In other words, you ask Summer to Create from your CD, print out the results, then compare by hand to my list.  Unless you can figure out a way to import my list and get Summer to recognize it??

Good luck

I made that list by pointing md5Summer to the CD and clicking on Select All, so it verified dumb stuff like the README file, but I figured better to get it all than leave something undone that might create questions at your end.

24X is way too fast.  Try 2X.  We're not burning a music file where a few misplaced bits won't make a dif.  This is a data CD that must be exactly the same as the original.

I've gotta work on making smaller posts

---

### Post by lenny45 on 2006-02-12
thanks bartender and the rest of yall.....

yea, actually the first thing i did was order the cd's through the mail.....! And i'm using sony cd-r's. so the media is good. i'll slow the burn waaay down next time to 2x.

lot's of good info bartender. will digest and give it another try. i'm just surprised that the "Mepis live" cd was such an easy burn on the first try.:-k 

will be back later...

---

### Post by lenny45 on 2006-02-12
well i got the little green globe on the check sum.....

so this file appears to be good......i guess i'll burn it again real slooooow!:-|

---

### Post by lenny45 on 2006-02-12
ok---re-burned ubuntu as slow as my cd burner would go. which is 8x.....

i still can't get it to work. that's 3 coasters. i would like to jump in here with a good copy of U but it ain't happening.:cry:  i'll just wait for the disk's to arrive in the mail and work with Mepis in the meantime.[-(

---

### Post by Bartender on 2006-02-13
Hi lenny - 
When you say you got the green globe, I don't think the job is done yet.  Did you make sure the checksum number or numbers matched?  If checking the download, it'll just be one number and must match the "Ubuntu i-386 install" number early in my long-winded post, if you're checking the CD it'll be a much bigger task to check all of those checksums in my attachment to the checksums you make with your CD.
It'd take some time to manually compare the CD's checksums.  I'm thinking there's probably a way to import the attachment back into md5Summer, but I haven't taken the time to figure out how.  Maybe you did?
Yeah, you should use the 'verify' or 'test' function in your burn utility.  I don't know how reliable that is.
BTW, my old Linux testbed accepts all 10 of the stamped CD's.  My new PC refuses to spin any of them.  Some basic incompatibity with the DVD drive?  Don't know and haven't taken the time to swap drives.  But since your 2nd PC won't do anything either that kinda sounds like the CD's eh?

---

