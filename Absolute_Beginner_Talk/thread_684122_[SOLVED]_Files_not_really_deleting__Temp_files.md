---
title: "[SOLVED] Files not really deleting?  Temp files?"
date: 2008-01-31
forum: Absolute Beginner Talk
---

### Post by Syndacate on 2008-01-31
Hey, I'm having this weird problem when I deleted this one thing...

I had a movie series on my computer - bought legitly and ripped of course - it was like 15 episodes of something, whatever.  I just ripped 'em to my cpu for ease of use then popping in a new disc every 4 episodes.  In any event, I was done, watched 'em all, they were all on an external USB Hard Drive.  I select 'em all, hit delete - they go away, nothing in the trash bin.  Look at the space on my USB Hard drive and there's still only 188MB free - now I know these were like 5GB of stuff so how is this possible?  I even deleted the folder they were in for good measure in case there was hiddens or temps..

It deleted - bu it didn't give me space back - any idea why?  The only thing I could conjur up was that it stored temporaries some place - but that many - that long ago?  It would have flooded my computer now?

I used kaffeine to watch them - any idea? 

Summary:  I removed them but it didn't give me my space back.

=(

---

### Post by taurus on 2008-01-31
Which trash bin are you looking at?  If you looked in ~/.Trash, try the trash bin on the USB drive.

---

### Post by nhandler on 2008-01-31
> **taurus said:**
> Which trash bin are you looking at?  If you looked in ~/.Trash, try the trash bin on the USB drive.

Just to clarify, if you delete a file on a removable drive, it will not be placed in ~/.Trash. Instead, it will be placed in a .Trash folder in the root of the drive. For me, when I eject the drive, I am prompted to empty the trash. If you aren't prompted, just hit Ctrl+H to enable the viewing of hidden files/folders. Then go into the .Trash folder on the removable drive and delete the files.

---

### Post by seventhc on 2008-01-31
My usb has it's own trash folder try looking in your usb and have it show hidden files <ctrl-h> if it's there that will make it show.

---

### Post by oedha on 2008-01-31
may i ?
in dealing with flashdisk....it's better to erase by using shift+del
but..when i upgrade from 7.04 to gutsy....GG will ask you to remove trash on flashdisk....what version are you ?

regards;
~E~

---

### Post by nhandler on 2008-01-31
> **oedha said:**
> may i ?
in dealing with flashdisk....it's better to erase by using shift+del
but..when i upgrade from 7.04 to gutsy....GG will ask you to remove trash on flashdisk....what version are you ?

regards;
~E~

His profile says he has Kubuntu Gutsy. I'm not sure if kubuntu prompts you to empty the trash.

Here is a tip for other people that may be reading this thread. You can add a Delete option to the right click menu in nautilus. This will delete the file instead of just moving it to the trash. To add it, go to Edit->Preferences->Behavior->Include a Delete Command That Bypasses The Trash.

---

### Post by Syndacate on 2008-01-31
> **Cheater said:**
> Just to clarify, if you delete a file on a removable drive, it will not be placed in ~/.Trash. Instead, it will be placed in a .Trash folder in the root of the drive. For me, when I eject the drive, I am prompted to empty the trash. If you aren't prompted, just hit Ctrl+H to enable the viewing of hidden files/folders. Then go into the .Trash folder on the removable drive and delete the files.

Thanks, that's the fix, omg, I can't believe it did that ****.

I feel like I got boned by my computer.

I went to cancatinate a file just now -a nd I ran FRESH Outta hard drive space (space free = 0 bytes) - just cleared out the hidden trash folder - freed up 41GB and 14 on the other.

****, now it did it for the externals - what about my local disks?  Because they don't seem to be deleting anything either - it's just filling up - deleted stuff but no room is being made.

---

### Post by nhandler on 2008-01-31
The local disk should store the deleted files in ~/.Trash. That means that each user will have their own trash folder. You should be able to delete files from the trash the same way you did with the external drives.

---

### Post by Syndacate on 2008-02-01
> **Cheater said:**
> The local disk should store the deleted files in ~/.Trash. That means that each user will have their own trash folder. You should be able to delete files from the trash the same way you did with the external drives.

It's not, there is no folder in **/home/user_name/.Trash** or **.trash**.

Any other ideas?

---

### Post by Syndacate on 2008-02-01
> **Syndacate said:**
> It's not, there is no folder in **/home/user_name/.Trash** or **.trash**.

Any other ideas?

Okay, I have no idea what the **** is going on here.

It doesn't show up in nautilus (and yes, hidden files (control + H) are shown) but when I do a **ls -la** in konsole it shows it.

Anybody want to explain to me what in the blue hell is going on?  And what's the purpose of having a trash bin if you have a .Trash folder?  And what designates if it goes into the .Trash folder or the trash bin?

---

### Post by oedha on 2008-02-01
are you sure.....i have one ( /home/oedha/.Trash )
open your nautilus.......click view - show hidden files....or ctrl+h
you will see it
if you're talking about NTFS disk....it will be there too
on the root .Trash-username

regards;
~E~

---

### Post by oedha on 2008-02-01
may i ? again....

blue **** indicates that it is a folder
i saw you also use windows right ?
did you notice that winblows also had recycler folder and also recycle bin
i think the answer will be like this........recycle bin / trash in only a shortcut to the trash/recycler folder itself

~E~

---

### Post by Syndacate on 2008-02-01
> **oedha said:**
> are you sure.....i have one ( /home/oedha/.Trash )
open your nautilus.......click view - show hidden files....or ctrl+h
you will see it
if you're talking about NTFS disk....it will be there too
on the root .Trash-username

regards;
~E~

Yeah, I hit control + H and no go - nothing showed up in terms of .Trash - the other hidden files showed up though, but when I typed it in manually into nautilus path and it opened up - nothing inside it.  Which is possibly why it didn't show up - but still, weird that it showed up in Konsole but not in the GUI.

Though I think I have to agree with the recycle bin being a shortcut to that - I don't know why my system said it was full but apparently it wasn't all trash stuff.  My computer ate itself and I restarted and upon boot I have 5GB (what I had before) instead of 0mb - Not sure what happened during that re-boot but it straightened something out.  Can somebody confirm oedha's belief of the .Trash folder being the folder that the "bin" links to?

---

