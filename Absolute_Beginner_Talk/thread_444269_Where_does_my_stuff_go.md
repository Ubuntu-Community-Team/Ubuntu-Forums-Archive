---
title: "Where does my stuff go?"
date: 2007-05-15
forum: Absolute Beginner Talk
---

### Post by the lemming on 2007-05-15
Could somebody please tell me a little about file management?

If I have a load of music, JPEG's and other such interesting stuff where would I put it?

Comming for a windows environment I would put all my stuff into a seperate folder away from my operating system and usually on a seperate hard drive in case I wanted to re-install XP or if it died of a virus.  However I have apsolutely no idea what I am looking at on my Ubuntu filing system.

Any chance of somebody giving me an idiot's explenation of how best to store my 56gb of MP3, 50gb of JPEGS/RAW images and everything else that I have accumilated?

Is there such a way that I can access this info in both ubuntu and XP depending on which system I boot into at the start of the day?

Sorry to ask such fundamentally green questions but this is all alien to me at the moment.

Cheers

---

### Post by srt5 on 2007-05-15
I tend to save my files onto an external hard drive. Because it is NTFS, I can easily switch between my XP desktop and my Ubuntu laptop through USB. Also keeping my files away from the operating system prevents Windows from slowing down as much - this isn't an issue on Ubuntu ;)

Edit: Since your dual booting, why don't you use the same hard drive to store your files on both operating systems?

---

### Post by silent1643 on 2007-05-15
i usually put everything in the home folder, mainly because you dont need root to edit those files

for your ubuntu sharing folders with xp, look [here]("http://ubuntuforums.org/showthread.php?t=340386&highlight=share+folder")

---

### Post by tact on 2007-05-15
Where to put stuff...  :)   You have asked a very intelligent question.  And one that does mystify linux newcomers so don't feel so "green".  

In windows people usually stick stuff in the "My Whatever" folders (My music, My Documents etc).  Or they create folders on C:\ or D:\ etc... to get "data" away from the operating system for the reasons you mention - in case they have to reinstall.

In a purely Linux installation you have a totally different organisation concept.   It is a fully multi-user system and all user files are stored in each individual "home" folder.  This would (should if you break the old habits) be where all your files are organised.  Linux programs do store all their configuration files in the user's home directory by default.

So do try to get into the habit of organising all your files in folders inside your "home" directory.  Forget about C:\ or D:\ or trying to set up partitions just for MP3's etc.  Use a folder in "home" instead.

This then opens the way for some clever organisation.  Backing up your "home" directory means ALL your documents, program configurations, data etc  is so much easier.  

You can also do things like put your root directory "/" in a partition of it own.  The home folders can also be on their own partition  etc etc.   Whether or not you put root "/" on its own partition or not - you can still do an  Operating System reinstall without losing all your configs!  All your data in "home" is also safe.

In windows, even if you install windows to C:\ and all your data on D:\ you will STILL lose all your configs (registry etc) if you format C: and reinstall.  In Linux this is not an issue at all.

Of course it still may make sense on a dual boot system (ie not a pure linux only as mentioned above) to to put certain data on external drives or separate partitions so it can be shared between different operating systems.    But that said - still try to get into the mindset of storing at least your linux only files in "home".

---

### Post by LaRoza on 2007-05-15
Making a new partition, or getting an external drive, will be useful for storing things that you'll want to share. Also, in your /home directory, you can make other folders, Documents, Music, Video, WindowsViruses...

---

### Post by rich.bradshaw on 2007-05-15
I have a seperate partion for home, then symlink some directories in my old Windows directory into home.

So in Home I have Pictures, Music, Videos, Documents, which are where I keep everything. I don't ever touch the rest of the system - that would be like saving mp3s in somewhere like C:\Windows\System32.

The pictures, music folders etc are symlinked with the corresponding folders on the NTFS partition, as that is bigger on my PC.

---

### Post by the lemming on 2007-05-15
> **LaRoza said:**
> Making a new partition, or getting an external drive, will be useful for storing things that you'll want to share. Also, in your /home directory, you can make other folders, Documents, Music, Video, WindowsViruses...



Thanks for the good advice chaps.  From reading all the advice I should only worry about a folder called "home".

Hopefully my next question has a simple answer.  At the moment ubuntu is dual booting on my laptop but for some reason I have conflicting issues getting ubuntu onto my PC and to get around this I am going to install another linux operating system that is not based around ubuntu  :( .  That is once the DVD arrives from the USA.

My PC has two hard drives, both of which are 120gb.  I also have two external hard drives to play with.  I am hoping to have the master drive for dual booting and put all my stuff onto the second drive.   Putting aside which flavour of Linux that I eventually choose to put onto my PC how can I get a "home" folder onto my second hard drive and get the Linux operating system to recognise that it exists and put my data into it?

I would really love to have this folder formatted as NTFS so that my XP operating system could access it as well.  Would this be possible?

---

