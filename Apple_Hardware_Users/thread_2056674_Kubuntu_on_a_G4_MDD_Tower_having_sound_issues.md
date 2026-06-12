---
title: "Kubuntu on a G4 MDD Tower having sound issues"
date: 2012-09-11
forum: Apple Hardware Users
---

### Post by traylor1 on 2012-09-11
G4 Tower and I installed Kubuntu. Everything seems to be running fine except the sound. It is very quiet, but if I raise the volume all of the way, it is quiet, but distorted and with static.
 
Suggestions?

---

### Post by 2blue on 2012-09-12
Have you checked settings in alsamixer? They are often way off and need to be ajusted on a new install. It should launch when you type "alsamixer" in terminal; and you maneuver it with arrows, tab- and F-keys.

---

### Post by traylor1 on 2012-09-13
> **2blue said:**
> Have you checked settings in alsamixer? They are often way off and need to be ajusted on a new install. It should launch when you type "alsamixer" in terminal; and you maneuver it with arrows, tab- and F-keys.
 
 
Cool, I will give it a shot, I appreciate it!

---

### Post by traylor1 on 2012-09-13
OK, so I went in to make adjustments.  What does it mean when everything works but the F Keys?

---

### Post by 2blue on 2012-09-13
Not sure, you mean non of the F-keys work? Alsamixer sometimes list features the computer might even not have, and it would not work of course. F1 should give you a list of all functions, and they should work.

---

### Post by traylor1 on 2012-09-13
Yeah I can not get the keyboard to respond using any F keys.  esc works and so does the tab and arrow keys, but no F keys.

From what I have been able to adjust, I still have very muted yet distorted sound.

---

### Post by 2blue on 2012-09-13
When I installed 12.04 on my G4 iBook I had to fuzz a bit to get alsamixer to launch at all. What I did was following this advice from a poster on the forum: I ran "sudo rm /etc/modprobe.d/blacklist.local.conf"" in terminal and rebooted. Then I reinsalled alsamixer packages from package manager and it was up and running. It is a bit of a shot in the dark, but reinstalling packages in this case has helped.

---

### Post by traylor1 on 2012-09-13
Well it was a good idea.  I tried it and nothing.

The one thing I notice is that every time I reboot, everything goes to muted and the sound levels all go to zero.

Could the sound card be a bad fit with Umbutu?

---

### Post by 2blue on 2012-09-13
I'm not sure alsamixer not working properly is a soundcard issue. It should launch and work fairly well regardless of loading sound card and driver properly? F6 should let you choose sound card manually. Hopefully someone who knows alsamixer better will read your post.

---

### Post by traylor1 on 2012-09-13
I did just find out that the Apple Aluminum keyboards have a issue with Ubuntu.  F keys do not work on them.

Going to try a keyboard from work tomorrow.  Thx for your help though!

---

### Post by este.el.paz on 2012-09-17
Folks:

I'm a few weeks into a new Xu/Lu 12.0.4 install on my iMac G4, and after a few updates my "nv" powered display is still working so that's the most important hurdle.  But, I have discovered a lack of sound thru the ext speakers . . . I toggled the "automute" feature in Alsamixer to "off" but I am using a newer aluminum keyboard and over the last year have noticed that indeed the f-keys don't work . . . which explains why when I tried to follow advice on various forums to use the f-keys to get into the CLI . . . it never worked.  OK, reason for posting, in the Ubuntu PPC FAQ I went to the "Why doesn't sound work?" section and see what appears to be two conflicting options provided??  One is telling me to "rm" the "modprobe.local.conf" (forget exactly) and the other is telling me to add the very same items to a new file that are the same items that are blacklisted in the modprobe.conf file??  I navigated to the /etc/modprobe.d  directory and found the local file, and saw the "snd" items listed there.  In OSX the user can drag such files to the desktop and then log out/back in to test out how the results of "rm"-ing would work *before* doing the command line approach to delete the file.  But from past experience I've seen that for many such files in Linux the user can't "drag and drop" the file "manually" like that, could I try that here?  Or, I guess I could right-click "send to trash" but could I then drag it back out of the trash?  The sound issue isn't enough to motivate me to do a reinstall of the system, as this is the 6th system installation on the iMac, I'm more interested in what's working, but sound, if easy, is sort of basic.  One further note, the annoying log-out/reboot BEEP does work, just when I try to play "Silence" from is it "MusicPlayer" . . . nothing happens, the progress bar doesn't move and no sound is heard . . . .

Thanks for any help or direction,

e.e.p.

---

