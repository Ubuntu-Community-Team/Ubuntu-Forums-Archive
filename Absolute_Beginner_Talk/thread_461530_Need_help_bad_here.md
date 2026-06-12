---
title: "Need help bad here"
date: 2007-06-01
forum: Absolute Beginner Talk
---

### Post by Ripfox on 2007-06-01
I tried to move a file from my home folder to a folder within my home folder, nothing out of the ordinary...all of a sudden theres a file called nautilus-debug-log.txt that seems to keep growing and I can't delete it. I'm worried about this is it a bug?

thanks all

---

### Post by Lucifiel on 2007-06-01
Why don't you open the nautilus-debug-log.txt and see what it says?

---

### Post by Ripfox on 2007-06-01
ok here goes...

===== BEGIN MILESTONES =====
0x8187110 2007/06/01 18:58:26.7300 (GLog): destroyed file has call_when_ready pending
0x8187110 2007/06/01 18:58:31.6143 (GLog): nautilus_file_get_uri: assertion `NAUTILUS_IS_FILE (file)' failed
0x8187110 2007/06/01 18:58:31.6144 (GLog): nautilus_file_get_mime_type: assertion `NAUTILUS_IS_FILE (file)' failed
0x8187110 2007/06/01 18:58:31.6163 (USER): debug log dumped due to signal 11
0x8187110 2007/06/01 18:58:31.6172 (USER): debug log dumped due to signal 11
0x8187110 2007/06/01 18:58:31.6176 (USER): debug log dumped due to signal 11
0x8187110 2007/06/01 18:58:31.6179 (USER): debug log dumped due to signal 11
0x8187110 2007/06/01 18:58:31.6182 (USER): debug log dumped due to signal 11
0x8187110 2007/06/01 18:58:31.6185 (USER): debug log dumped due to signal 11
0x8187110 2007/06/01 18:58:31.6188 (USER): debug log dumped due to signal 11
0x8187110 2007/06/01 18:58:31.6191 (USER): debug log dumped due to signal 11
0x8187110 2007/06/01 18:58:31.6194 (USER): debug log dumped due to signal 11
0x8187110 2007/06/01 18:58:31.6197 (USER): debug log dumped due to signal 11
0x8187110 2007/06/01 18:58:31.6200 (USER): debug log dumped due to signal 11
0x8187110 2007/06/01 18:58:31.6203 (USER): debug log dumped due to signal 11
0x8187110 2007/06/01 18:58:31.6206 (USER): debug log dumped due to signal 11
0x8187110 2007/06/01 18:58:31.6209 (USER): debug log dumped due to signal 11
0x8187110 2007/06/01 18:58:31.6212 (USER): debug log dumped due to signal 11
0x8187110 2007/06/01 18:58:31.6215 (USER): debug log dumped due to signal 11
0x8187110 2007/06/01 18:58:31.6218 (USER): debug log dumped due to signal 11
0x8187110 2007/06/01 18:58:31.6221 (USER): debug log dumped due to signal 11
0x8187110 2007/06/01 18:58:31.6231 (USER): debug log dumped due to signal 11
0x8187110 2007/06/01 18:58:31.6234 (USER): debug log dumped due to signal 11
0x8187110 2007/06/01 18:58:31.6237 (USER): debug log dumped due to signal 11
0x8187110 2007/06/01 18:58:31.6240 (USER): debug log dumped due to signal 11

ect...
ect...

---

### Post by Lucifiel on 2007-06-01
It sounds like Nautilus is suffering a crash and/or a string of errors. Perhaps you can also try looking at .xsession-errors in your /home/<user> directory.

Sorry I can't help much. :( Perhaps the more experienced users can have a look at this thread.

---

### Post by Ripfox on 2007-06-01
Reinstalled nautilus through synaptic...seems to have fixed the bug, as I was able to delete the error file.

---

### Post by Lucifiel on 2007-06-01
Oh and you could try restarting X Server and see if you still get these errors.

Alt + Ctrl + Backspace 

I've been looking for information on this issue but it seems the only really credible link I could find was at some forum on Opensuse. 

Jonmartin: Last first, all those errors and warnings from nautilus occurs all the time, it's just that you don't get to see them unless you start nautilus from the command line. Same goes for konqueror.

[http://suseforums.net/lofiversion/index.php/t18600.html](http://suseforums.net/lofiversion/index.php/t18600.html)

So, maybe you can just restart X and go on with life if nothing else happens.

---

### Post by Kuoi on 2007-06-01
I've tried to search the internet about it , and didn't found much.

Like Lucifiel says , It seems Nautilus is crashing when you start it, or even start your computer.

I suggest you look in "Edit > Preferences" (at the menubar in Nautilus) , and change some settings .

First I should try to change the settings in "example" first ( translated from Dutch )

My settings there are the following :
You see 5 settings you can change , ... I'll write them from top to bottom :

Only local files
Only local files
5 MB
Only local files
Only local files

Hope it helps , Kuoi

---

### Post by Lucifiel on 2007-06-01
> **ripfox said:**
> I tried to move a file from my home folder to a folder within my home folder, nothing out of the ordinary...all of a sudden theres a file called nautilus-debug-log.txt that seems to keep growing and I can't delete it. I'm worried about this is it a bug?

thanks all

> **ripfox said:**
> Reinstalled nautilus through synaptic...seems to have fixed the bug, as I was able to delete the error file.

Oh that's good for you! :D 

Sorry I couldn't do anything to help. However, I recommend to keep the file somewhere in case such errors occur again. Because, trust me... if anything goes wrong, you want to keep as much information as possible. Fixing Ubuntu is not fun. :p

---

### Post by Ripfox on 2007-06-01
quik format and reinstall heheheh

---

