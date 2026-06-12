---
title: "Deleting windows files from ubuntu"
date: 2007-12-11
forum: Absolute Beginner Talk
---

### Post by vasa1 on 2007-12-11
Hi All:

Caution on hitting “delete”!

Since I use WinXP to access the internet via dial-up (till I get broadband when I'll be able to use Ubuntu), files I download are stored in “My Documents” in my MS Windows ntfs partition. When I boot up Ubuntu, I mount the MS Windows disk and then read and edit these files perfectly. I can also ***delete*** them too perfectly. They vanish forever if I select them in Nautilus and hit ctrl+T or “delete”. They don't go to the trash on my Ubuntu desktop. Why?

Files I create and delete from my Ubuntu directories go to the trash and give me a chance to recover them.

Experienced WinXP-Ubuntu dual-booters please throw some light  on this!

Thanks,

AE Souza

---

### Post by meborc on 2007-12-11
hmm... i am not sure about this, but the files should be moved to the .trash folder... since we are talking about different partitions, maybe nautilus created a .trash folder under your win partition? check if anything appears when you hit ctrl+h it your mydocuments nautilus dir

i might be wrong, haven't used gnome for a while

---

### Post by viking777 on 2007-12-11
Just checked it with my system and sure enough folders deleted from my windows folder do go to the Ubuntu trash.

I cant think of a reason for this, I can only suggest that when you don't want a windows file to be permanently deleted you move it to Ubuntu first and delete it from there.

Ugly I know, but until somebody else comes up with a solution it should work.

---

### Post by rkd on 2007-12-11
Perhaps the deleted files on the Windows partition are put into the Recycle Bin directory on the Windows partition?  That is what happens when you delete a file using the Windows GUI.  Maybe the folks who implemented the NTFS driver made it do that.

---

### Post by JillSwift on 2007-12-11
On the "root" folder of the NTFS partition you will probably find a hidden folder called .Trash-[username] (Where [username] is your username... not that it wasn't obvious :P )

Deleting NTFS files via Nautilus gets the file moved there. For whatever reason, files in *that* trash folder don't show up in a Nautilus trash: window.

(Wow, lookit all the trash talk =o.0= )

---

### Post by vasa1 on 2007-12-11
Hi & thanks to all who posted.

Ubuntu does give MS Windows Trash a second chance. 

Ubuntu creates a .trash file in the C: drive main directory which has all the files I delete from the WinXP partition via Ubuntu's Nautilus. Since I haven't set Nautilus to show hidden files I didn't see it. When  I start a Windows session I get to decide on sending them to the recycle bin or restoring them (as is normal with deleting files in Windows).

AE Souza

---

