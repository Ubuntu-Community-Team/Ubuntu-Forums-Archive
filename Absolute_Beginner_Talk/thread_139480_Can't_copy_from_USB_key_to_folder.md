---
title: "Can't copy from USB key to folder"
date: 2006-03-04
forum: Absolute Beginner Talk
---

### Post by The Pinny Parlour on 2006-03-04
Hi all,

I am trying to copy music from my USB key to /home/ian/My Music.  No luck though, I keep getting the following:

Error while copying to "/home/ian/My Music".
You do not have permission to write to this folder.

I'm dropping and dragging and it soesn't work, is there another way that I don't know about.

Any ideas on how I can just copy some music files to my ubuntu box from a USB key?

Thank You


P.S>  I have just noticed a little padlock on My Music folder, how did that get there? and how do I remove it?  I beleive this is causing the issue. 

EDIT,  I just right clicked and checked write permission and it works.   

Cheers,

---

### Post by lyndon on 2006-03-04
[QUOTE=The Pinny Parlour]Hi all,

I am trying to copy music from my USB key to /home/ian/My Music.  No luck though, I keep getting the following:

Error while copying to "/home/ian/My Music".
You do not have permission to write to this folder.
[/QUOTE]
It's probably a bit presumptious of me to reply as I'm a complete newbie, but I had the same problem and seemed to be able to sort it (sometimes) throught the GUI rather than the Terminal.

Open your My Music folder, go to Edit/Select all. Right-click and select Properties, then right-click on any of the selected files and choose the Permissions tab. You'll find three categories on the left - Owner, Group and Others. What you *want* is OWNER - Read, Write, Execute      GROUP - Read, Execute   OTHERS - Read, Execute. Check the appropriate boxes. If the little check boxes are greyed out, go to the menu bar and select Applications/Accessories/Terminal.
Type (after ian@ubuntu$ or whatever prompt comes up) 

sudo chmod 755 /home/ian/My Music/*

The '755' gives the same result as the box-checking above - only the owner can write, but the others can read and execute.

As far as I know, the * wildcard will mean the chmod (change of permissions command) will be applied to all the files inside the folder, and that if you then run the chmod command again, leaving out the *, it will then apply to the folder itself. When I did this, I was frustrated to find that the 'padlock' - in my case, a pen with a red circle round it, crossed out - was still there. I logged out and back in again and it had gone away.

If this is total rubbish, I hope I'll be suitably corrected (though not flamed, I hope :cry:) by people who really know what they are talking about - I thought it might help me to learn if I had a go at helping someone else, and I don't think I've told you anything potentially disastrous! 

Hope this helps,

Lyndon

---

