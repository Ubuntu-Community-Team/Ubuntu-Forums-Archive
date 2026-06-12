---
title: "Audio Not Working -- Ubuntu 10.04 Lucid Lynx on iMac"
date: 2010-06-10
forum: Apple Hardware Users
---

### Post by TechnoEagle on 2010-06-10
I have installed Ubuntu 10.04 on my iMac through Bootcamp. Unfortunately, any time a sound file should play, it doesn't.
I have confirmed that my sound is not on mute and is set to a sufficiently high volume. :KS

No error message appears; I simply cannot hear anything being played. This happens whenever I try to play a sound file, play a game with music, etc. :confused:

If anyone knows what I should do, I would really appreciate the help! ):P

---

### Post by ZeroLinux on 2010-06-10
Take a look [here]("http://ubuntuforums.org/showthread.php?t=1439009")

---

### Post by TechnoEagle on 2010-06-10
> **ZeroLinux said:**
> Take a look [here]("http://ubuntuforums.org/showthread.php?t=1439009")

I tried that, but it still doesn't work.

---

### Post by ZeroLinux on 2010-06-10
What is in alsamixer output? Can you make screenshot to see?
Was your soundcard recognized? Did you unmute sound from alsamixer with "m" in "Front Speaker"? Sound usually works out of box with unmuting alsamixer.... Your situation is really strange.

---

### Post by TechnoEagle on 2010-06-10
I put a screenshot of the terminal window below. As far as I can tell, my sound card is being recognized.


[IMG]http://ubuntuforums.org/attachment.php?attachmentid=160013&stc=1&d=1276213920[/IMG]

---

### Post by hollowtd on 2010-06-11
download alsamixer from the software store and then unclick the mute button there for the mac and it should work for that and for the mic if you're having trouble. It will be the same alsamixer but work better and easier.

---

### Post by ZeroLinux on 2010-06-11
Ok. Try to apply [these]("http://ubuntuforums.org/showpost.php?p=9393397&postcount=20") instructions. It installs new new version of alsa. And then unmute alsamixer if it is necessary.

---

### Post by TechnoEagle on 2010-06-11
It still isn't working. I followed the instructions from the other thread. Once my computer restarted, I typed alsamixer into Terminal and it was still unmuted.

---

### Post by Lisimelis on 2010-06-11
`my friend I got the same problem and i found the solution. Here is my problems thread. Good luck!!!

[http://ubuntuforums.org/showthread.php?p=9410532#post9410532](http://ubuntuforums.org/showthread.php?p=9410532#post9410532)

---

### Post by TechnoEagle on 2010-06-11
I followed the instructions on the thread that was linked to on the thread that Lisimelis had a link to, but to no avail. I still can't get the audio to work. :confused:

---

### Post by ZeroLinux on 2010-06-12
What is your soundcard?

---

### Post by thalliwell on 2010-06-12
Same situation here but the sound is very low, I have to turn it full to just hear it. Yes all levels are turned fully up in alsamixer

---

