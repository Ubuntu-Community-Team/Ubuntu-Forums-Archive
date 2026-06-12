---
title: "my pc just crashed"
date: 2007-09-06
forum: Absolute Beginner Talk
---

### Post by kubilaycan on 2007-09-06
hi i have been using feisty for over a month now. everything was fine but just 5 minutes ago my pc just crashed. 

i was just browsing (opera) and listening to music (amarok) and it just stopped responding and the song it was playing got stuck repeating the same frame. 

so i reset the pc and when i wanted to run amarok it just stopped at the splash screen. so i forced it to quit and then wanted to restart the pc. but it didnt restart and just showed the desktop, but it wasnt frozen cuz the cursor responded..

so i had to cold reset once again but now everything seems to be ok. 

how do i check what happened.. where are the logs and necessary info?

thx

---

### Post by Crafty Kisses on 2007-09-06
> **kubilaycan said:**
> hi i have been using feisty for over a month now. everything was fine but just 5 minutes ago my pc just crashed. 

i was just browsing (opera) and listening to music (amarok) and it just stopped responding and the song it was playing got stuck repeating the same frame. 

so i reset the pc and when i wanted to run amarok it just stopped at the splash screen. so i forced it to quit and then wanted to restart the pc. but it didnt restart and just showed the desktop, but it wasnt frozen cuz the cursor responded..

so i had to cold reset once again but now everything seems to be ok. 

how do i check what happened.. where are the logs and necessary info?

thx

When it hangs, you can boot into verbose mode, and see where it hangs.

---

### Post by alienexplorers on 2007-09-06
I would not worry to much about it.  It may have just been a random hiccup.  If it keeps happening then I would get worried that something is failing on the system.  First thing I would check if it happens again would be to run memory test to see if a ram chip is dying.

---

### Post by Sef on 2007-09-06
Do you have your files backed up?

---

### Post by kubilaycan on 2007-09-06
it was the first time it happened... my important files are all on my external usb drive, including my music. this actually worries me because the drive is ntfs and if this freezing happens while it is writing on the drive, i have a feeling ugly things will happen, because it is ntfs.

and it is ntfs because i use dualboot with xp. 
and i use dual boot because i think i need a slow but solid transition to linux. 
and for games.

once a folder just disappeared from my external hdisk. it was a music folder. i think it happened because amarok was updating some id3tags and it was really slow and then it stopped responding so i had to quit it. and then when i booted into windows it ran a chkdsk and i think there it got deleted because amarok could not finish the writing process to the ntfs and windows found it corrupt.

anyways thats another issue.

what is this verbose mode? how do i do that?

is there no logging of system errors or messages in ubuntu? like in services.msc in windows?

---

