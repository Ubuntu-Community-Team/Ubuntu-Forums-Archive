---
title: "Network/filesharing wuit working."
date: 2008-03-08
forum: Absolute Beginner Talk
---

### Post by timforlinux on 2008-03-08
I had Ubuntu happily networking with another ubuntu and a windows computer.  Something updated itself and it quit working.

  I got the network pinging again, then tried to share files.  First, the icons for networking that were previously displayed (when it worked originally) are still there.  I can't delete them, AND, they will not open, saying "The folder contents could not be displayed.  Sorry, couldn't display all the contents of "Windows Network: noone-desktop".

  When I tried marking the folders on the main computer to be shared, I was first told something about usershares.  I wasted a lot of time tracking that and having to work in terminal and config.  The user share error went away.  But now when I right click the folder and mark to share it says error#255; do not have permission.

  I tried running a thing reffered to SWAT; which does not do anything but after a long while returns in the terminal - the words ALARM CLOCK.

  IT IS NOW TIME FOR  A PROPER RANT.  I am a programmer.  Being a programmer means - making things work for the people you are writing the program for, whether it is a utility for my kids to use on the home computer or something to serve the entire corp at work.  This attitude is still seriously missing in the Ubuntu development.  
  WHY?  EVER!?  would you take something that was working (samba/networking/filesharing) and  - just make it quit?  And do so without adding a gui that pops up and handles all the changes that might be required for the new 'feature?'
  It's nice seeing Ubuntu grow; I love it and tout it - but unless the core of it starts getting handled  a little more professionally CONSISTENTLY, the growth will remain slow.
  Even though i am a programmer, doesn't mean I know all the cryptic (needless to know) inner workings of everything.  So my 'free' Ubuntu has cost me many billable hours - very needlessly.
  The developers really need to take a customer oriented attitude to the core.  If necessary, remove terminal, and gedit and such from your computers, so you are forced to deal with your own software results as a typical customer.  If you can't be bothered with a gui, you shouldn't be writing and releasing to Ubuntu repository, AND Ubuntu - you shouldn't be using geeky stuff.

  I know it is easy to loss sight 'of the customer' when we get too immersed in our technical world, but there's no point to the technical world unless it produces pleasant useable results.  No, it is not sufficient to say 'just gedit ... or just terminal ...'  Those tools should not even (have to be) be known to the typical user.  It is just our arrogant little egos that like our (old) cryptic special worlds.  I've learned I can retrain my ego to get it pleasure from producing easily useable programs instead of gloating over the ignorance of the masses who aren't all so savey (not to mention handsome) as me.  I'd like to offer - it is a much more rewarding feeling in the end to produce truely useful and helpful code than it is to gloat over partial, cryptic, complicated fragments of code that only other geeks will praise with me.  

  I praise - when I click on a link, the program downloads, install and runs and does what it was intended to do - quiding me for input when necessay, but never expecting me to know more than what I happen to at the moment - to install and configure itself.  

  END OF RANT
 
  So, if someone knows a real clean and simple fix to get file sharing working again, please point me to it.  

  Thank you,
tim

---

### Post by herbster on 2008-03-08
Regarding your challenge, are you simply trying to mount Windows shares so you can read/write to and from Ubuntu?

Regarding your rant, check the Recurring Discussions forum here somewhere.

---

### Post by timforlinux on 2008-03-08
I'm not sure what the word 'mount' is completely, but I want another computer to see the folders on main computer (#1) and be able to read and write the files in them.
  I got part of this working on #1 computer; I got swat working and messed around with some values.  The last action was deleting an existing usershares file in .../lib/usershares.  Then the next time I tried to make a shared folder it worked.
  But on computer #2, ubuntu also, same as #1 as far as I can tell, there is no file created under usershares after I have clicked the Share Folder option.
  Also, On computer # 1 there are two options, Share Folder AND Sharing Options.  The folder was not marked as shared until I used Sharing Options.  However, Sharing Options does not exist in right-click menu for folders on computer #2.  (I wonder why it is on the one and not the other.  Both are Gutsy updated to current.)  Computer #2 does not report seeing the folder marked Shared on #1, but can ping it ok.

thanks for the reply
tim

---

### Post by herbster on 2008-03-08
Mount = making the filesystem available to access via a mount point, which would be simply a directory. Each drive/partition has a point on the filesystem where it can be read if it is mounted.

I have no idea what you are talking about with the share folder options-- are you referring to the nautilus file browser (the Explorer-like file manager you get when you click Places > Home, etc.)? Are you clicking Places > Network?

You have two computers apparently, both are running Ubuntu and Windows or are both running Ubuntu and one running Windows? If you just want to access folders to/from computers you can hit Places > Network and you'd see Windows Network, go into that and you'd see the workgroup(s) and shares.

---

### Post by kwacka on 2008-03-08
I do hope that you, with your valuable experience as a programmer, will contribute the time and effort that thousands have given to bring Linux to where it is today and help overcome niggling little problems like Microsoft making it as difficult as possible for other operating systems by changing their file systems. .

Regarding your problem, are you sure the problems lie with your Ubuntu setup - were there no changes to your Windows machine or the network?

Mount means make available to the system basically. E.g. if I place a USB stick in a computer running Windows it automatically 'mounts' it and I get a box saying do I want to look at the pictures or see what's on the disk. To 'unmount' the USB stick I click on the safely remove arrow and it tells me I can remove it.

Hope that helps.

---

### Post by Nythain on 2008-03-08
ok, lets start back at square one... first, lets see if we got some things clear here... from what im gathering:
You have at least 3 computers... 2 of them running Ubuntu, and at least 1 running Windows?
Everything was working absolutely perfectly up untill the point of updating?
Did you update through synaptic, adept, update manager, or apt-get/aptitude?
Did you happen to catch very much of wich packages were going to be updated?
You are running Samba on BOTH Ubuntu machines hopefully if you want to share anything from them with both each other and the windows computer?

now for a bit more info... first, any corrections to the above comments?
next... lets see if i understand things so far... you have managed to get shares semi working again, in the sense that they are showing up on some of the machines, possibly not others, and no matter wether they show up or not, you cant write to them due to a permission problem in one way or another... like this
A. Ubuntu sharing /home/me/Stuff ---> B. Ubuntu can see share "/home/me/Stuff" but cant write to it ---> C. Windows can't see or access share "/home/me/Stuff"

Now, what is the output of
```

cat /etc/samba/smb.conf

```when typed into an open terminal session on both of the Ubuntu machines?

and lastly, as mentioned, are you SURE that the only thing that has changed is the Ubuntu updates... none of the ip addresses on any of the machines have changed... windows didnt do any updates... Folder names didnt change on any of the machines, even in the slightest, possibly just uppercasing one letter???

i know all of this seems pretty obvious but it was sherlock holmes who once said..[B].
"eliminate all other factors, and the one that remains must be the truth"
and
"eliminate the impossible, and whatever remains, however improbably, must be the answer"
[/B]

---

