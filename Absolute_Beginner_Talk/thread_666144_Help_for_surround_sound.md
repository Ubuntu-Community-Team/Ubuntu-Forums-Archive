---
title: "Help for surround sound"
date: 2008-01-13
forum: Absolute Beginner Talk
---

### Post by talsemgeest on 2008-01-13
I have inbuilt Realtek   ALC883 sound with the usual stereo out, microphone in and line in. 
Using windows and the software from the asus website I used those three jacks for 5.1 surround sound (front L&R to stereo out, rear L&R to Line in, and centre and sub woofer to the microphone in). 
Is there any way that I can reproduce the same effect through Ubuntu?
Any help would be appreciated, so thanks in advance.

---

### Post by Lostincyberspace on 2008-01-15
Try out pulse audio link [here.]("http://www.pulseaudio.org/")

---

### Post by talsemgeest on 2008-01-16
Ok I installed it so what do I do now?

---

### Post by talsemgeest on 2008-01-18
I give up on that program. It destroyed mu audio completely but Ive got it back to the way it was. So does anyone else have any ideas? I would like to find out where the audio configuration files are stored if anyone knows that...

---

### Post by talsemgeest on 2008-01-18
I found some audio config files in /proc/asound/ anyone know how I should change them?

---

### Post by talsemgeest on 2008-02-02
I think I should be able to do it with JACK, I just dont know how. For a quick recap, I want to rout front L&R to stereo out, rear L&R to Line in, and centre and sub woofer to the microphone in. Any ideas?

---

### Post by talsemgeest on 2008-02-06
Time for a bump...

---

### Post by talsemgeest on 2008-03-15
Maybe another bump...?

---

### Post by talsemgeest on 2008-03-25
Is there anybody out there?

---

### Post by rajeev1204 on 2008-03-25
> **talsemgeest said:**
> I have inbuilt Realtek   ALC883 sound with the usual stereo out, microphone in and line in. 
Using windows and the software from the asus website I used those three jacks for 5.1 surround sound (front L&R to stereo out, rear L&R to Line in, and centre and sub woofer to the microphone in). 
Is there any way that I can reproduce the same effect through Ubuntu?
Any help would be appreciated, so thanks in advance.


Changing jack to mic instead of line in got rear sound working for me in ubuntu.

---

