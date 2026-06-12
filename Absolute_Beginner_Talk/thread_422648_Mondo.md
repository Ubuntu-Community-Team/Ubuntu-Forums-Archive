---
title: "Mondo"
date: 2007-04-25
forum: Absolute Beginner Talk
---

### Post by TayzGpa on 2007-04-25
I am trying to install Mondo to do a system backup.
I did an "apt-get install mondo" and it appears to have ran ok.  No errors anyway.
But I cant find where it put the icon for me to launch the program.
I looked in the Synaptic Package Manager and it shows Mondo 2.21 as being installed.
Can someone tell me how to launch the application?
:confused:

---

### Post by whitefort on 2007-04-25
Hi,

I'm an almost total newbie, but until someone comes who can give a better answer...

I really like Mondo - without it, Ubuntu updates would have totally trashed my laptop on several occasions.

But there's no icon.  I can only tell you how it works for me.

Like I say, there's no icon.  Open the terminal and type 'mondoarchive'.

That sets it running, and you need to make some choices -  I've not been able to get it to backup directly to DVD, so I choose the option to backup to hard drive.  From memory, I think it goes into the root directory - I forget the exact folder name, but it should be easy to find.  i think it's something like images/mondo/something.iso

From there, you can burn it to a CD or DVD.  To test it, boot from the CD/DVD, and you'll be presented with several options, one of which is to test the archive.

It won't be an EXACT copy of your hard drive by now, because some non-important system and temp files will have changed, but it should be OK.

You can then use your backup disk to either restore individual files, or to do a bare-metal restore of your entire system.

I hope this is some help.  if you're still stuck, let me know and I'll post a more exact description.

This program has saved me SO many times - It's well worth figuring it out!

---

