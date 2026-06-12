---
title: "Error message : Cannot mount Volume?"
date: 2007-10-09
forum: Absolute Beginner Talk
---

### Post by The Frozen Mage on 2007-10-09
Hello.

Sorry if I have missed a previous thread on this, I have used the search command and Google and have not found an answer that either a) Works or b) understand. From this you will quickly deduce that I am a complete beginner to Linux, Ubuntu being my first ever attempt at a Linux OS.

My problme is this. I am trying to install World of Warcraft. I have used the guide on the game forum and everything was running smoothly until it came to the actual installation of teh game. If I insert any of the original discs into the CD drive I get the message;

Cannot Mount Volume
Invalid Mount Option when attempting to mount the volume.

This happens on all 8 WOW discs and three other Commercial CD's. Yet the drive reads my own burnt Ubuntu CD-r and two other burnt CDR and CDRW.

Attempted to play Audio CD, which it did then put WOW disc in cd drive. This time no error message but still no appearance of the cd either on desktop or in Places>computer.

Can anyone help me please, remembering that I will need it explained pretty basically.

Thank you for any help and again sorry if I have asked something answered before, I did check lots of posts Honest <smiles>

---

### Post by phidia on 2007-10-09
Hi, I think we need to start from the begining. Do you have wine installed and working?
There actually is a gentoo how-to on what you want to do [here]("http://gentoo-wiki.com/HOWTO_Install_and_update_World_Of_Warcraft_with_wine").
That link could be a helpful guide,

---

### Post by The Frozen Mage on 2007-10-10
Hello <smiles> and thank you for the reply.

Yes I do have wine installed. I have been using the Ubuntu guide (Htttp://ubuntuforums.org/showthread.php?t=312482) so far.

I have (I believe) successfully got to the installation part using discs. (part 3 on Ubuntu forum))

And putting the "windows" commercial discs still gives me the same Cannot mount error message and no icon on desktop or in Places>computer.


According to all four guides I have read at this stage I should be able to put the disc in to the cdrom drive and copy the files to the specified file in Home, but every commercial produced disc comes back with Cannot mount message.


Thank you for your help and I do apologise if it seems you are talking to a complete novice, my main computer for the last *coughs* years have been Mac's and I'm used to things just working *laughs*

Looking forward to hearing your suggestions



PS Forgot to mention in case it's needed I am using Feisty 7.04 (downloaded on Monday so hopefully up to date *laughs*)

---

### Post by The Frozen Mage on 2007-10-10
Just in case it is of any use in helping identify the problem ((seen lots of people ask for it in other queries) here is the /ect/fstab report

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=fb2e9d17-1fc5-4417-84b9-c27dbb29ab11 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=ada18390-728e-4916-9534-6d3b60087d3a none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0

Also here is a copy of response to a terminal line suggested on these forums that apparently worked for someone with a similar problem. Sadly no joy here

~$ sudo mount /dev/scd0 /media/cdrom0
Password:
mount: block device /dev/scd0 is write-protected, mounting read-only
mount: you must specify the filesystem type


As a complete novice I don't understand why it's blocking device when it's read only as all I want to do is for it read the disc, but obviously I'm missing something here <smiles>

Really looking forward to using this laptop properly again, with Ubuntu rather than Windows.

---

### Post by The Frozen Mage on 2007-10-10
Just to add more information, it is obviously a problem with Windows discs as I put a Mac OSX commercial disc in and it showed up on Desktop and in Places>computer.

So I'm guessing it must be something to do with Wine?

Can anyone confirm this and if so any hints on the Wine Guide for complete beginners?

If not any ideas on what to do next?

Once again Thanks for any and all help trying to sort this out.

---

