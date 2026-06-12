---
title: "sound is too quiet!"
date: 2007-02-26
forum: Apple Intel Users
---

### Post by jbob286 on 2007-02-26
I am running Ubuntu 6.10 on my macbook core duo. I have the sound mixer at maximum volume but the speakers are still very quiet. I do not have this problem in OS X. I have also had this problem in Fedora so I do not think it is unique to Ubuntu.

Any ideas? Thanks!

---

### Post by garlito on 2007-02-27
> **jbob286 said:**
> I am running Ubuntu 6.10 on my macbook core duo. I have the sound mixer at maximum volume but the speakers are still very quiet. I do not have this problem in OS X. I have also had this problem in Fedora so I do not think it is unique to Ubuntu.

Any ideas? Thanks!

I've got the same problem with an intel mac mini. I installed Ubuntu a few days ago and I've just noticed that. I'm sill shocked because I read some reviews about linux in mactel before ordering one and neither of them talked about this kind of hardware problems. It's unusable for me in that way. :-(

I will try to find some information. Any mactel owner here?

Thanks.

---

### Post by johnw188 on 2007-03-02
> **jbob286 said:**
> I am running Ubuntu 6.10 on my macbook core duo. I have the sound mixer at maximum volume but the speakers are still very quiet. I do not have this problem in OS X. I have also had this problem in Fedora so I do not think it is unique to Ubuntu.

Any ideas? Thanks!

By sound mixer, do you mean the little menubar dropdown volume control, or the actual mixer panel. I had these problems once; you have to go into alsa-mixer (I believe? alsamixer? something like that) and play around with the settings in there.

---

### Post by jbob286 on 2007-03-02
alsamixer did the trick. Just ran it in the terminal and turned the volume to max for the 'Front'.

Why on earth is the actual system volume tucked away in some command line program?

---

### Post by johnw188 on 2007-03-03
> **jbob286 said:**
> alsamixer did the trick. Just ran it in the terminal and turned the volume to max for the 'Front'.

Why on earth is the actual system volume tucked away in some command line program?

It really isn't. The easy to access volume control doesn't go to the absolute max of your soundcard, or you could damage your equipment. I assume whoever coded it made it stay within the constraints found in the alsamixer panel.

---

### Post by saxin on 2007-03-03
You can do this with GUI also. Just double-click the volumeicon and fix the settings :)

---

### Post by jbob286 on 2007-03-03
No, you can't. No where in any GUI setting, be it the volume icon on the panel, or in the system sound settings, can you turn the volume all the way. The only way I could do it was in alsamixer.

---

### Post by garlito on 2007-03-04
> **johnw188 said:**
> It really isn't. The easy to access volume control doesn't go to the absolute max of your soundcard, or you could damage your equipment. I assume whoever coded it made it stay within the constraints found in the alsamixer panel.

I did the same than jbob286 and the speakers sound high enough now, do you think it could be dangerous for the card? But why is so quiet?

---

### Post by garlito on 2007-03-04
> **jbob286 said:**
> No, you can't. No where in any GUI setting, be it the volume icon on the panel, or in the system sound settings, can you turn the volume all the way. The only way I could do it was in alsamixer.

You can, go to the volume control (double click on the volume panel icon) and then in preferences select the tracks you want to appear, "front" in this case.

What confused me was the operative control in the mini is not PCM as I'm used to, but front.

You can do something similar with the volume in the panel, in preferences choose "front" as the track to be controlled.

Regards.

---

