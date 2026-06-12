---
title: "DVD keeps playing audio even though both VLC and Kaffeine are closed."
date: 2007-05-27
forum: Absolute Beginner Talk
---

### Post by kevdog on 2007-05-27
Using Ubuntu Feisty with Automatix codecs.  When sticking DVD into player, audio begins immediately after disc automatically mounted, although there is no chosen program up and running.  If I open disc with Kaffeine or VLC, movie plays fine, although when closing viewer program, audio of disc continues to play.  Only way Ive found to stop the audio is to either unmount disc or eject disc.  Some program continually tries to read disc since I can still see drive light flicker from time to time.

Help?

---

### Post by thousandrobots on 2007-06-13
i am having the same problem. it also happens when i am playing a video_ts folder that has been copied to the hard drive.

i once opened VLC while this was happening and got a X Window that I could close. But that behavior seems to be inconsistent.

You could probably use the Terminal to figure out what process was running and kill that process, rather than ejecting the disk. That worked for me:

In Terminal, I ran "top", then saw that a process called "wxvlc" was running with process id 18415. So i ran "kill 18415" and it immediately terminated the process and the audio.

---

