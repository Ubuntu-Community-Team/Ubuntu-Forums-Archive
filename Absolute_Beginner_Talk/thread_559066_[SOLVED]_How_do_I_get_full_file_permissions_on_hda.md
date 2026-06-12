---
title: "[SOLVED] How do I get full file permissions on hda1 from a live cd -  need to rescue"
date: 2007-09-24
forum: Absolute Beginner Talk
---

### Post by philinux on 2007-09-24
Need to reinstall hence question cos some files are locked from the live cd. 

I need to copy my home folder, all files, before reinstall

---

### Post by EchoBeach on 2007-09-24
Have you tried Knoppix?
Echo

---

### Post by philinux on 2007-09-24
Yes I need to do this from ubuntu live cd

---

### Post by philinux on 2007-09-24
Come on guys this must be easy

---

### Post by SpiritIsReality on 2007-09-24
howdy
ok. this is how it went for me.
to copy the files from /home, including hidden files, to a cd, using the ubuntu live cd.
edit : major oops. I said gksudo nautilus. wrong!! it's gksu nautilus. right!!
(fixed up the code below)
got live cd up and running
click applications>accessories>terminal
type
```
sudo mkdir /mnt/hd__
```
enter
hd__the partition your ubuntu is installed on, or the partition your /home is mounted on, I suppose.
in this case, the /home is a part of the / partition of ubuntu. hda1 right?
then
```
sudo mount /dev/hd__ /mnt/hd__
```
now leave that window.

hold down Alt key and press the F2 key
in the run box type
```
gksu nautilus
```
enter or click run.
wait for it.
in nautilus window, click the up.
double click mnt
double click hd__
couble click home
double click username

click view (top of window)
click show hidden files
you should see files with names starting with a . (dot) if you scroll down the window.
move this window over to the right side of the screen, but not off the screen. 
keep it so you can see the whole window including the scroll bar on  the right side of it.

(I should be saying what i did, not what you do, but bare with me, please)

make sure the scroll bar is right at the top of it's track. or drag it there.
drag=move the mouse pointer over the scroll bar. click and hold down the left mouse button.
move the mouse pointer and the captured bar up till it hits the top of it's track.
let the mouse button up.

move the mouse pointer to the top left corner of the box in the window that contains the icons.
left click mouse and hold down, 
move the pointer down the window to the bottom and a bit further.
the window should begin to scroll
keep going to the bottom of the icons, to the bottom right hand corner.
all the icons should be highlighted now. a different color
let up the left mouse button.
icons should still be highlighted.
leave that window.

hold down the Alt key, and press the F2 key. (Alt-F2)
in the run box, type
```
gksu nautilus
```
enter or click go

in the window that opens, click Go (it's at the top of the window)
click CD/DVD Creator
a CD/DVD Creator window will open

go to the window over at the right of the screen, the /mnt/hd__/home/username window,
where all the icons are highlighted.(selected)
take your time on this next step when you're dragging and dropping or it may not work.

left click on a folder that is highlighted, any one, and hold down the mouse button.
slowly move the mouse pointer and icon over to  the empty box of the CD/DVD Creator window.
when the icon is in the clear box of the CD/DVD Creator window, let the mouse button up.
that's called a drag and drop (drag 'n drop)
(dragon droppings?!!) no...
the files should copy into the CD/DVD Creator window.

now what do you do? No, I'm asking. I usually use k3b. haha!
click on any clear or empty  part of the CD/DVD Creator window to bring it to the top, so you
can see the whole window. maybe try the bar at the top. go ahead try it.(or not)
click on Write to Disc. or click on File, then click on Write to Disc.

I got an error message saying that I needed 25 MiB more space to create the image.
If you don't get any error messages, carry on.
Error: File image creation failed. The selected location does not have enought space to store
the disc image. (25 MiB needed)

In the CD/DVD Creator window, I clicked on Edit, 
clicked on Select All,
clicked on Edit 
clicked on Move to Trash.

I went back to the /home/username window, 
left clicked on a clear spot  in the box to clear the selection.
I held down the Ctrl key, and clicked on the folder and file icons that I wanted to back up (copy to cd)
and tried to leave out about 30 MiB.
(just a note:the image I was trying to create was 186 MiB. so I guess I can burn about
160 MiB at a time to CD. Your mileage will probably vary)
Could maybe repeat the steps, if you need to copy more to CD than it will burn at a time.
Would have to keep track of which files your burning each write.

after the write to cd is done,
go to the terminal window, and type
```
sudo umount /dev/hd__
```
hd__ being the ubuntu partition on the hard drive.
that's a umount, with only one n. not u n mount, but u mount (no spaces in umount)
that unmounts (umounts..) the partiton so we can safely shutdown, restart.

when writing to disc, there was a window asking if it was alright whatever about
joliet windows files names, I said ok, yes, burn , baby burn.
I can fix this up if you have trouble at that window.

hopefully
Bob's your uncle!
and
You're in the saddle!

trails

[http://psychocats.net/ubuntu/backup](http://psychocats.net/ubuntu/backup)
EchoBeach ...I tried the
[http://knoppix.org](http://knoppix.org) live cd and k3b. It works.

---

### Post by philinux on 2007-09-25
Back from town with cdrw's and a 4gig usb drive.

Feel a fool now gksu nautilus. :lolflag:

Forget to look in media for my stuff. :)

on with the home folder copying. This could take a bit of time. But step 1 in progress.

---

### Post by SpiritIsReality on 2007-09-25
howdy
cheerin' for you
trails

---

### Post by philinux on 2007-09-25
Had to use sudo nautilus, however cd writer starts but everything is greyed out and it hangs. :confused:

Going to put home folder on usb stick instead.

---

### Post by SpiritIsReality on 2007-09-25
howdy
an attached screenshot! wow. 
I ran thru the blarney of post #5, and tried to burn the home folder.
it looks like it would do it, only I don't have enough something...maybe memory..
to copy it all at once.

when I clicked on the 
Post Reply 
button
I saw below the Message box that there were some Additional Options.
I clicked on the Manage Attachments button...
figured ok, I gotta try this.
Applications>Accessories>Take Screenshot.
saved to Desktop.
back to clicked Manage Attachments
it asks for the file type. ? If I was paying more attention when I saved them to
desktop, I wouldn't have had to click on show desktop and check out the icons.
the names end in .png
oh, and when I was saving the shots, I had to name each one a little different.
I messed around long enough, I had to highlight the message in this box and click
copy, log back in and click paste.
the Manage Attachment button doesn't open a window for me anymore.
probably because I closed it a couple times to type along in here.
I'll have to try it again some other time. haha! rats!
I thought I was soooo close, too.

trails

---

### Post by SpiritIsReality on 2007-09-25
one more try 
it turns out that I had the window hidden behind the forums window.
in the panel at the bottom of the screen, there were two windows listed.
one named Ubuntu Forums - Reply to Topic -Mozilla Firefox
and the other named [Http://ubuntuforums.org](Http://ubuntuforums.org) - Manage Attachments - Ubuntu Forums - 
Mozilla Firefox
clicked on the second one and bing! there's the window.
DOH !

clicked on Browse button
double clicked Desktop in the left hand pane of the window
clicked on the image,
clicked open.
clicked the Upload button.
finished off this note, and clicked Submit Reply button.
hope they're there

trails

edit : yeeehaaa!! there they are.
when I click on them to view them, I get a better focus 
if I click it once with the enlarge mouse pointer.
wow! this is great. what a place! what an os!
Philinux ...how are you makin' out .
a usb stick. have to click System> Preferences> Removeable Drives and Media ?

---

### Post by philinux on 2007-09-25
update.

Ubunti live cd failed
1. cd write - greyed out app box
2. properties on home folder reported 40 files 10mb - laughable.
3. failed to mount my usb drive- had to use gthumb to do it.
4. failed to copy to usb - kept going on about certain files unable to copy during operation.

Now in knoppix livecd this has so far been going well

1. recognised usb stick out of box
2. properties on home file showed 5181 files and 1.3 gig
3. can burn to cd but will need two and it says files names over 64 characters will be truncated :(
4. can copy to usb but  it cant create symlinks :(
5. Permissions were easier just right clik on media change to writeable :)

Not sure if or what  3 & 4 or how it will affect a restore after reinstallation.

---

### Post by SpiritIsReality on 2007-09-25
howdy
I've been using k3b to burn cd/dvd.
once you get your system runnin' you can install it and it
will run on a gnome setup. (I use sudo aptitude to install it) or
```
sudo aptitude install k3b
```
synaptic might work just as well, I don't know.
k3b explains the joliet and truncated questions, click on filesystem,
after you click on burn.
in fmat slang whatchamacallit paraphrasing
what it's doing is truncating (shortening) the unix file names, so that the
Microsoft operating system will be able to read them . Mic being limited to 64
characters joliet. which is ok.
better links around than this, but this will help maybe
[http://www.google.ca/search?hl=en&q=linux+truncated+joliet&btnG=Google+Search&meta=](http://www.google.ca/search?hl=en&q=linux+truncated+joliet&btnG=Google+Search&meta=)
[http://www.ibm.com/developerworks/linux/library/l-cdburn.html](http://www.ibm.com/developerworks/linux/library/l-cdburn.html)
edit: link here to symlink, so if you find out all about it, you can probably ignore my witless blabber haha!
edit: [http://www.google.ca/search?hl=en&q=site%3Arute.2038bug.com+symlink+symbolic+link&btnG=Search&meta=](http://www.google.ca/search?hl=en&q=site%3Arute.2038bug.com+symlink+symbolic+link&btnG=Search&meta=)
edit: there's probably links in the /home folder that link to the rest of the / partition, which you're not copying,
so the links are going to be broken?
my guess at the symlink question is that knoppix can't or by default doesn't want to
link the files on your ubuntu partition to the copied files on your usb drive.
I figure that's ok since you don't really want them linked anyway.
you want to copy them onto your new install, or leave them on your usb as backup...
should be ok I figure.
I think it sounds like your close to ridin' the ubuntu horse installed on your hard drive
I'm gettin' kind of an attachment for this ubuntu live cd mustang.
being a new boy, (newbie) these linux cayuses are like ridin' a mustang with a string in it's mouth, lot's of power and not much control. haha!
But What A Ride !!! YeeeHaaaaw!! Let 'er rip!

trails

---

### Post by SpiritIsReality on 2007-09-25
ya
I didn't know truncated from a post hole.
I clicked on
Applications > Accessories > Dictionary
in the Look Up box, typed
truncated
and pressed the enter key

trails

---

### Post by philinux on 2007-09-25
Now burning woohoo  =D>

---

### Post by SpiritIsReality on 2007-09-25
howdy
I don't have the smarts yet to know the details of 
-copying the whole /home folder
-copying only the contents of the /home folder.
-copying the /home folder to a cd and copying that to a /home partition on the hard drive.
etcetera

but I guess we're gonna find out.
I had trouble once, when I copied a  root partition from one place and copied it back to a different partition
on the same drive. I got into some kind of space time warp. haha!
there's much to learn about backing up., he says.
so go ahead,  he hears.  haha!
[https://help.ubuntu.com/community/?action=fullsearch&context=180&value=backup&titlesearch=Titles](https://help.ubuntu.com/community/?action=fullsearch&context=180&value=backup&titlesearch=Titles)

trails

---

