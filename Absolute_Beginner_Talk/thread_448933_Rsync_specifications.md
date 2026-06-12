---
title: "Rsync specifications"
date: 2007-05-19
forum: Absolute Beginner Talk
---

### Post by l951b951 on 2007-05-19
I tried reading the man page for rsync, but it either didn't mention my situation or I didn't understand what I was reading.  

I have been using rsync to put a backup copy of important folders on a Network Attached Storage Device.  I have used this command:


> rsync -av --delete /media/linuxstore/"home pics"/ /media/vault/FileShare/Pictures/

Here is my question.  The NAS device is mounted as an NFS folder.  However, it is still visible to other computers.  If someone were to put extra files in the "Pictures" folder, would my rsync erase them when I back up using the above command.  Also, will this particular command copy pictures from the NAS back to my harddrive folder "home pics"?

---

### Post by steve0921 on 2007-05-19
I know very little about rsync and can't (directly) answer your question, but why don't you test whether or not the command will delete other files by adding test files yourself.

If it doesn't erase them then great. If it does, you can try to improve the rsync command, but I personally  am a fan of using extra folders for things like this. If other users put their files elsewhere, then rsync will leave them alone. You could even be fancy and play with permissions so that different users can't destroy each other's files.

---

