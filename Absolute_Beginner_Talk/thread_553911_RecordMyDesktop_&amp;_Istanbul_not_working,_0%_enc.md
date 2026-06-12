---
title: "RecordMyDesktop &amp; Istanbul not working, 0% encoding process"
date: 2007-09-18
forum: Absolute Beginner Talk
---

### Post by nb123 on 2007-09-18
Hi, I'm having problems with recordmydesktop and istanbul that I got from synaptic. I installed the GUI frontend for recordmydesktop and am able to set all the options correctly and get it to record, but when I stop it, it doesn't seem to be encoding the file. It just stays at 0% complete. So I tried Istanbul and the same thing is happening. I have beryl effects installed but I read that it works with beryl right? I'm not sure what's wrong?

---

### Post by overdrank on 2007-09-18
> **nb123 said:**
> Hi, I'm having problems with recordmydesktop and istanbul that I got from synaptic. I installed the GUI frontend for recordmydesktop and am able to set all the options correctly and get it to record, but when I stop it, it doesn't seem to be encoding the file. It just stays at 0% complete. So I tried Istanbul and the same thing is happening. I have beryl effects installed but I read that it works with beryl right? I'm not sure what's wrong?

Hi I too had this happen and I removed the apps and then reinstalled. Then everything worked. :)

---

### Post by nb123 on 2007-09-18
I tried removing and reinstalling, but unfortunately it didn't work. It said: --- 

Recording is Finished.
recordmydesktop has exited with status: 768
Description: Could not open/configure sound card. 

I can't seem to find any information about this through google, what do I do?

---

### Post by supergrover1981 on 2007-12-19
Hi nb123,

Is it possible that Audio capture isn't enabled? Try the following:

1.) Open up a terminal & type "gnome-volume-control"

2.) Edit -> Preferences

3.) Check "capture"

4.) A "recording" tab should pop up. Click on that, slide the volume up if it's set to zero and click the microphone icon so that it doesn't have a red "x" through it

5.) Try RecordMyDesktop again. With any luck it should be working.

Hope this helps,
                          - SuperGrover

---

