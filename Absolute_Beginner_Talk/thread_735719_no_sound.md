---
title: "no sound"
date: 2008-03-25
forum: Absolute Beginner Talk
---

### Post by RyviusRan on 2008-03-25
A while back I installed ubuntu then decided to run a dual boot.

I had ubuntu on first then added windows xp

the dual boot worked and I was able to use windows and linux, but when I first booted windows up I did notice one thing wrong.

There was no sound. I checked my audio driver and it seemed it wasn't installed so I used my cd with the software for my drivers and in the middle of installing the installation windows closes and presents me with the message

audio driver device fail error -001

I tried also getting the audio driver from the website, but I still get the same problem.

anyone know how to solve this?

---

### Post by abo_shreek11 on 2008-03-25
Tell me more about your system hardware, and your sound card manufacturer ?. I think you have a conflict with one of windows updates. You must imagine such a things since Microsoft decided to provide it's own hardware updates!!

---

### Post by c-ron on 2008-03-25
Hi, try installing the driver manually. the exact procedure will vary depending on your hardware.
Take a look at this link:
[http://www.infopackets.com/channels/en/windows/gazette/2002/20020201_the_ultimate_program_and_driver_install_guide.htm](http://www.infopackets.com/channels/en/windows/gazette/2002/20020201_the_ultimate_program_and_driver_install_guide.htm)

The basic steps are to download the newest driver, extract the files from it to a folder using winzip or winrar, use the Device Manager under the hardware tab in Control Panel -> System to locate your audio hardware, go into the properties for the sound card, click on the drivers tab, click update driver, specify the location of the driver to wherever folder you extracted the driver files to.

---

### Post by RyviusRan on 2008-03-25
what information would u like?

my audio device is by the company called realtek I tried them out, but get the same problem.

well when i bought this computer i seemed to misplace my windows discs so i used a friends mine was originally windows media center 2005. Now I am using windows XP home edition with only SP1 pack installed.

---

### Post by superprash2003 on 2008-03-26
try this [http://prash-babu.blogspot.com/2008/02/sound-problems-in-ubuntu-gutsy-710.html](http://prash-babu.blogspot.com/2008/02/sound-problems-in-ubuntu-gutsy-710.html)

---

### Post by c-ron on 2008-03-26
> **superprash2003 said:**
> try this [http://prash-babu.blogspot.com/2008/02/sound-problems-in-ubuntu-gutsy-710.html](http://prash-babu.blogspot.com/2008/02/sound-problems-in-ubuntu-gutsy-710.html)

This article in that link is for fixing sound issues in linux. The original post is about driver issues in MS Windows.

---

### Post by northern lights on 2008-03-26
> **RyviusRan said:**
> what information would u like?
Please post the output of ```
cat /proc/asound/cards
```

> **c-ron said:**
> [QUOTE=superprash2003;4590686]try this [http://prash-babu.blogspot.com/2008/02/sound-problems-in-ubuntu-gutsy-710.html](http://prash-babu.blogspot.com/2008/02/sound-problems-in-ubuntu-gutsy-710.html)This article in that link is for fixing sound issues in linux. The original post is about driver issues in MS Windows.[/QUOTE]
If you were to check out Prashanth's latest posts, you'll notice 18 out of 20 are > **superprash2003 said:**
> try this <URL to his own blog>So I'm guessing this guy is simply scanning all threads for the word "sound" and then pastes his blog URL...

@Prashanth, OT: SA is hammering you guys in Chennai, eh?!

---

