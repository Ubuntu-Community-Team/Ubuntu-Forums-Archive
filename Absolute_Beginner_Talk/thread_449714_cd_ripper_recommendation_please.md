---
title: "cd ripper recommendation please"
date: 2007-05-20
forum: Absolute Beginner Talk
---

### Post by paker on 2007-05-20
I need to convert CD to 96 kbps mp3. Sound Juicer Extractor seems to convert to higher quality mp3 only. Am I mistaken? What program will do this for me?

---

### Post by Bachstelze on 2007-05-20
abcde : A Better CD Encoder. It's a command-line program though so forget it if you're scared of the terminal. I like it because it's simple, easy, and gets the job done. No more, no less.

---

### Post by paker on 2007-05-20
Thanks for the reply. I will use the recommended program. Please tell me what command I have to use to rip the entire CD (all tracks) to 96 kbps mp3. Thanks.

---

### Post by Bachstelze on 2007-05-20
```
sudo apt-get install abcde
```

Then to rip the CD in mp3

```
abcde -o mp3
```

I don't remember the parameter which sets the bitrate but the man page should be able to tell you.

---

