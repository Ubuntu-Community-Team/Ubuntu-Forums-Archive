---
title: "Completley lost...."
date: 2005-12-28
forum: Absolute Beginner Talk
---

### Post by DarkDancer on 2005-12-28
I started this in the wrong section and am moving the text here, I need help.....

Hi!

I have a NetGear wg311v3 wireless card and a nice fresh install of Unbutu. I know I need ndiswrapper-util, and I think I have it (I downloaded ndiswrapper-utils_1.1-4_i386.deb). I went to the wiki and read what it said there and that all went way over my head, what do I do?

Response:
Once you have downloaded a .deb file, you can open a terminal, browse to the directory where you have downloaded it using the cd command, and then when you reach the directory containing the .deb file, simply type this:
Code:

sudo dpkg -i name-of-deb-file.deb

This will install the deb package.

My response:
Ok, tried that, and failed. I think it is because Ubuntu is loaded on hda3, and ndiswrapper is on hda 5, and I don't know how to get to hda5. I tried cd /hda5, but it errored on me.

Now what do I do???

---

### Post by Nate53085 on 2005-12-28
From you post, you DID try:

sudo dpkg -i ndiswrapper-utils_1.1-4_i386.deb correct?

I have never needed to copy to a specific drive to install a debian package, but the correct syntax to do so is:

cp file_location/file new_location/

or

mv file_location/file new_location/

(the first Copies the second Moves, there IS a difference, copy leaves the original, move does not)



EDIT

You do have to browse to the drive though (that may have been what you were asking??)

cd /mnt/hda5

or maybe

cd /media/hda5

(I'm not sure which)

---

### Post by DarkDancer on 2005-12-28
Thanks, I think I got it working, I think, now I need to figure where to put the hex code for the WEP......

---

### Post by DarkDancer on 2005-12-28
Ok, not so sure now, I got the version of ndiswrapper that came with ubuntu installed, then got the version that I dl/ed installed, but not sure that it is seeing my card, when I go into network, all it says there is "loopback".

How can I tell if it is seeing my card?

---

### Post by ecto on 2005-12-28
well just yesterday i was trying to fix my mbr and a friend told me how you can mount certain partions
First you need a live cd.
Next you boot up the cd.
Once booted open a terminal and type
> mkdir /media/proc
This will create a folder called /media/proc or something like that. By doing this you are creating a temporary mount point.
Now sudo su (or sudo -i whichever you perfer) and type
> mount /dev/hda#yourtryingtomount /media/proc/
From their do what you need to do.
Alright hope this helps.

---

### Post by DarkDancer on 2005-12-28
Um, sorry, but I don't see how that has anything to do with my problem?

---

### Post by DarkDancer on 2005-12-28
bump

---

### Post by cwaldbieser on 2005-12-28
[QUOTE=DarkDancer]Ok, not so sure now, I got the version of ndiswrapper that came with ubuntu installed, then got the version that I dl/ed installed, but not sure that it is seeing my card, when I go into network, all it says there is "loopback".

How can I tell if it is seeing my card?[/QUOTE]
If it is only showing loopback, the drivers probably aren't loaded.  If you open a terminal and type "lsmod", you can see whether or not the  driver you are trying to use was loaded.  If not, you can try to manually load them with "modprobe".

I am not sure what directions you are following, so I can't really be more specific than that at this point.

Hope that helps you.

---

