---
title: "Help me understand this please!"
date: 2007-07-08
forum: Absolute Beginner Talk
---

### Post by kavon89 on 2007-07-08
[http://forum.goteamspeak.com/showpost.php?p=133902&postcount=20](http://forum.goteamspeak.com/showpost.php?p=133902&postcount=20)

I got the alsa-oss thing but I can't run the darn script he included. TS is running in OSS and causing major problems with other apps, it doesn't allow any other apps with sound to work, not even system sounds.

Here is what errors I get when I test the sound and TS is open. 
[http://i14.tinypic.com/4q72oeh.png](http://i14.tinypic.com/4q72oeh.png)

I think that thing in the TS forum would fix the problem, wrapping OSS Teamspeak and playing through ALSA.

---

### Post by shrift on 2007-07-09
You have to make the script executable. So creat a new file, copy that script into it, save it, and then from the command line enter "sudo chmod +- scriptfile" replacing "scriptfile" with whatever the name of your file is. Then you can execute the file by typing "sh scriptfile".

Doing this may or may not get your sound working how you want it. Alsa is for sure better than oss, which always requires full control of your audio hardware, but alsa is a bit flaky here too. If this doesn't work i'd look into installing pulseaudio.

---

