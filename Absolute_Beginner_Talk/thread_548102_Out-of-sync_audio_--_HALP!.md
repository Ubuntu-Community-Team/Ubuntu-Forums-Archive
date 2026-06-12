---
title: "Out-of-sync audio -- HALP!"
date: 2007-09-10
forum: Absolute Beginner Talk
---

### Post by Canew on 2007-09-10
Hi:

I've read other posts on this subject, but I feel like I've tried everything and still nothing. I'm running Edgy and I can't get the audio and video to sync up right with my DVDs. It's only off by a few miliseconds, but it's driving me crazy, and I don't know what I'm doing wrong. I installed xine, and it still didn't fix it, not even in the xine player itself. I've posted on this before and gotten no help. Could someone PLEASE clue me in? I feel like I've tried everything.

---

### Post by ijason on 2007-09-11
the only advice i have is what i read when i was trying to figure out why my sound was being funky inside Wolfenstein ET. if you're viewing the dvds from a stand-alone program, and not just viewing them with the standard media player this might help you. open a console and type : killall etd

that resets the sound devices and frees them up for your application. after you run the dvd player, if system sound doesn't restore itself you'll need to open a terminal again and type : etd

you should hear a tone beep from your speakers letting you know your system sound has been restored.

/good luck! wish i had more specific advice :)

---

### Post by Canew on 2007-09-11
Thanks, but maybe the error messages are telling me something.

When I do killall edt, it says, "no process killed."

When I type edt, it says, bash: command not found.

WTF?

---

