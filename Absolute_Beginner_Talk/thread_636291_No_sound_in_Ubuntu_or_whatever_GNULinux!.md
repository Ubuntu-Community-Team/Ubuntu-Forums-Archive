---
title: "No sound in Ubuntu or whatever GNU/Linux!"
date: 2007-12-09
forum: Absolute Beginner Talk
---

### Post by MsWin3.1x on 2007-12-09
I dual-booted Vista and Ubuntu with Wubi on my HP laptop - all including sound worked ok!
After that I decided to try different distros and installed openSUSE! Again everything worked perfectly, however I liked Ubuntu better so I deleted suse and installed it again! First time I started Ubuntu everything worked fine, but after restarting there was NO SOUND! I tried reinstalling it and it didn't help!
Then I tried different distros - Kubuntu, opensuse, but still - NO SOUND! I have always made sure that my speakers aren't muted and in BIOS I couldn't find anything related to sound that could have been changed... What could be the problem? BTW: Sound works on Vista!

---

### Post by Kingsley on 2007-12-09
What sound card do you have?

---

### Post by MsWin3.1x on 2007-12-09
Where can I look that up?

---

### Post by Natr0n on 2007-12-09
In Wubi go to Applications->Accessories->Terminal and type```
lspci
```your sound card should be listed if it is recognized. In fact, you should post the output of that command here to help people diagnose the problem. In Windows XP, you would right-click "My Computer", select the "Hardware" tab and then click the Device Manager button and the sound card should be listed under "Sound, video, and game controllers." I realize you're using Vista but I suspect the procedure might be similar.

---

### Post by MsWin3.1x on 2007-12-09
OK, I found it!

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)

---

### Post by Natr0n on 2007-12-09
I wonder if this might work for you: [bash script to automate compiling alsa in Ubuntu]("http://www.antonywilliams.com/2007/10/bash-script-to-automate-compiling-alsa.html"). You might also try this: [HDA ATI SB / INTEL Sound card problem [SOLUTION!]]("http://ubuntuforums.org/showthread.php?t=616845&highlight=sound")

---

### Post by MsWin3.1x on 2007-12-09
Thanks, I'll try them, although I might be having trouble installing tarballs(never been succesful before)... But one thing I really want to understand is why did that sound just stop working if it worked before?

---

### Post by Natr0n on 2007-12-09
[QUOTE=MsWin3.1x]why did that sound just stop working if it worked before?[/QUOTE]I don't know exactly why that would happen but I'm fairly certain I've heard of of that behavior before. Maybe someone with more knowledge would care to chime in?

---

