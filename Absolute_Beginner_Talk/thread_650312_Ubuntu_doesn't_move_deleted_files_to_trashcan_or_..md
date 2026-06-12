---
title: "Ubuntu doesn't move deleted files to trashcan or .Trash folder"
date: 2007-12-26
forum: Absolute Beginner Talk
---

### Post by thaulow on 2007-12-26
Hey there,

So this is my first post, so bear with me if it has been placed in the wrong directory.


So here's the deal:

I'm dual booting with Ubuntu 7.10 and Windows Vista Ultimate, with Ubuntu as my primary OS.


Now the problem: Every file that hasn't been created through Ubuntu, when I move them to the trashcan, they just disappear. I tried looking in the .trash folder with no luck.

I booted into windows to see if they were someplace there, but no. I have a lot of music and stuff on my computer, that I placed in windows when I install both OS, and I then used Ubuntu to find them. But now, they're just gone if I try to move them to the trash.

I hope this makes sense and someone can help, because it's very annoying!

---

### Post by Tux.Ice on 2007-12-26
um when you move them to the trash therye supposed to be gone.

why are you moving needed files to the trash?

---

### Post by thaulow on 2007-12-26
No I don't think you understand, or maybe I just don't make sense :)

I noticed this problem when i accidentally pressed my delete button, when 20 files was marked. And so, they were deleted. And I was unable to locate them in the trash bin.

Unless I've misunderstood something with Ubuntu since I updated it last time, deleted files usually end up in the trash bin, and from there I have the opportunity to empty it.

This time I didn't, and I find that to be a problem. Also if someone else borrows my computer, and by mistake deletes a file.

---

### Post by laidback on 2007-12-26
Could it be that you had the shift key depressed as well, shift + delete really does delete, no trash can back up.

OR...is there some shift lock on your keyboard, so every time you press delete you've really pressed shift + delete?

---

### Post by thaulow on 2007-12-26
No unfortunately that can't be it.

I tried just before to right click a file, and told it to drop it in the trash bin, and again the file did not show in the trash, it was just gone??? :(

---

### Post by laidback on 2007-12-26
I'm lost too...sorry. 
Try deleting ~/.trash to force a new copy. Or create one yourself.

---

### Post by thaulow on 2007-12-26
:(

Deleting the .trash folder didn't work.


How do I create one myself? Just make a new folder myself instead of having Ubuntu do it for me?

---

### Post by Martje_001 on 2007-12-26
Hmm.. and in your root trash folder?

/root/.Trash

oh. btw: it's **.Trash** not **.trash**

---

### Post by thaulow on 2007-12-26
Either it's just me, or no trash folder is in my: /root/.Trash

I suddenly feel like a complete newbie :)

The one I deleted was in /home/*user*/.Trash

---

### Post by laidback on 2007-12-26
You can create .Name type folders the same as others, right click> create folder, name it with a preceeding dot. It is called .Trash not .trash.
I was referring to the one in your home directory, not any other at ~/root level.

Never looked at root Trash. All my deleted files end up in ~/home/mydir/.Trash, which is the dir that the trash-can bottom right of the screen refers to.

Recreating it is only an idea, I don't really know what's wrong.

---

### Post by thaulow on 2007-12-26
Nope - doesn't work :(

*sigh*


Isn't there anyone who've experienced this before??

---

### Post by Martje_001 on 2007-12-26
If you create a new user and log in to it, and then remove a file; does it go to the Trash Bin?

---

### Post by laidback on 2007-12-26
Sorry; running out of ideas
What about the Permissions on the folder. My .Trash has :-
Folder access..Create and Delete Files for myself only, no other access allowed.

I'm beginning to think that there is something wrong with the routine that deletes things, i.e. the script that is run when you press delete, assuming that there is one.

---

### Post by Martje_001 on 2007-12-27
> **laidback said:**
> I'm beginning to think that there is something wrong with the routine that deletes things, i.e. the script that is run when you press delete, assuming that there is one.
Well.. that's nautilus. Maby you could reinstall it.

---

### Post by popch on 2007-12-27
Linux makes a trash can on every device, I believe. Try and find a folder named .trash in the root directory of your Windows drive. Remember to turn on 'show hidden files'.

---

### Post by JillSwift on 2007-12-27
On NTFS drives, the trash directory is usually called .Trash-<user> where <user> is your Ubuntu login name. For whatever reason, items moved to that folder aren't listed in the usual trash app.

---

### Post by c0met on 2007-12-27
Hi,

I don't know if this information will help. 

After reading your post, I was inspired to experiment and so started playing around with Nautilus (Ubuntu's file manager) and the Trash Can.

I made an interesting discovery :)

When you delete a file, it will only send it to Nautilus's garbage bin if you delete it from the Ubuntu partition. If (say) you delete a file on the Windows partition, Nautilus will create a directory called ".Trash-(possibly some identifier)" on the Windows partition. Deleted files are then moved to this location. Although they don't show up in the Garbabe Bin, you can navigate to the .Trash-### file on the appropriate drive or partition and the files should be located there. At least that is how it worked for me.

I take it that you have already worked out that it's necessary to checkmark " View Hidden Files" - under <VIEW> in Nautilus - if you want to see the .Trash files.

I'm by no means an expert on this stuff because I'm relatively new to Ubuntu, it might give you some ideas, though.

Regards,
c0met

---

### Post by laidback on 2007-12-27
Isn't the Forum great, amazing what you can find out. As I don't use Windoz with dual boot the above is all new to me. Useful non the less as one day I might come across this issue.

---

### Post by c0met on 2007-12-27
Hey Laidback,

I totally agree. I've been spending time just going through the forums here and learning heaps.

---

### Post by ma65p on 2008-05-10
I was having problems finding the trash folder too. But what I did was adding another shortcut on my menu bar. Then opened it. And I made a very important discovery. All I have to type in the address bar when I want to access my Trash folder is 

trash:

There, it took me to the trash folder immediately.

---

