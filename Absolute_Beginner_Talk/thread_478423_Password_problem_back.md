---
title: "Password problem back"
date: 2007-06-19
forum: Absolute Beginner Talk
---

### Post by henthorn on 2007-06-19
After posting about my lost username/password problem yesterday I thought I was in the clear.  I booted up Ubuntu several times and everything worked fine.  This morning when I booted up and got to the username/password screen I typed in my username, hit enter and the prompt line returned to blank.  I typed in the username again and the dots appeared, but when I hit enter I got the incorreect username message. I tried a restart and when it started to boot I got a screen which said that pv/hda2/ had been mounted 25 times without bring checked and a check was being forced.  It went through the check and then rebooted.  I still got the same results when the log-in screen came up.  So I am back to not being able to get into Linux.  I tried going to the  Grub prompt and typing in "passwd don" and got the "error27 passwod must be authenticated" message. This appears to be a problem that can't be solved on this forum.  It seems every computer problem I experience is is one like this.(G) Any ideas?

---

### Post by Alex&amp;Linux on 2007-06-19
You said :

"i typed in my username, hit enter and the prompt line returned to blank, I typed in the username again and the dots appeared but when I hit enter I got the incorrect username message"

This is perfectly normal, because if you were being completely accurate in your description of the problem, you have entered your username for the password as well.

Your username is not visually encrypted, you will see the actual characters, however, when you hit "enter" on that, it will blank out and the input will be reprisented as dots, because thats where you place your PASSWORD!

---

### Post by lazyart on 2007-06-19
I concur... the first time it wouldve been asking for your username.  After hitting enter it clears out the box so that you can enter your password, which is shielded with the dots.

---

### Post by dfreer on 2007-06-19
> **henthorn said:**
> After posting about my lost username/password problem yesterday I thought I was in the clear.  I booted up Ubuntu several times and everything worked fine.  This morning when I booted up and got to the username/password screen I typed in my username, hit enter and the prompt line returned to blank.  I typed in the username again and the dots appeared, but when I hit enter I got the incorreect username message. I tried a restart and when it started to boot I got a screen which said that pv/hda2/ had been mounted 25 times without bring checked and a check was being forced.  It went through the check and then rebooted.  I still got the same results when the log-in screen came up.  So I am back to not being able to get into Linux.  I tried going to the  Grub prompt and typing in "passwd don" and got the "error27 passwod must be authenticated" message. This appears to be a problem that can't be solved on this forum.  It seems every computer problem I experience is is one like this.(G) Any ideas?

When you say you went to the Grub Prompt and typed in passwd don, did you mean the Recovery Mode? If not, then try booting to recovery mode which will bring you to a root shell. From there, type your passwd don. you should be able to change your password then.

---

