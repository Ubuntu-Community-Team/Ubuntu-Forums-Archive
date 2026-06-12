---
title: "How do I get my audigy2 ZS working?"
date: 2005-07-05
forum: Absolute Beginner Talk
---

### Post by gammyhand on 2005-07-05
I have disabled my onboard sound and rebooted and I have the option to choose between the Audigy2 (ALSA mixer) and some sigmatel (OSS) mixer...how do I get my Audigy2 to give me any sound. It just doesn't want to give it up :(

I can't hear anything from system sounds to audio cd's to mp3 files.

---

### Post by poofyhairguy on 2005-07-05
[QUOTE=gammyhand]I have disabled my onboard sound and rebooted and I have the option to choose between the Audigy2 (ALSA mixer) and some sigmatel (OSS) mixer...how do I get my Audigy2 to give me any sound. It just doesn't want to give it up :(

I can't hear anything from system sounds to audio cd's to mp3 files.[/QUOTE]

Ubuntu has a bug where audigys are muted by default. Search the forum for "alsamixer"

---

### Post by gammyhand on 2005-07-05
[QUOTE=poofyhairguy]Ubuntu has a bug where audigys are muted by default. Search the forum for "alsamixer"[/QUOTE]
 Thanks :)

---

### Post by gammyhand on 2005-07-05
Hmm...I am not finding anything particularly useful...?

---

### Post by jrobcet on 2005-07-05
The  "Audigy Analog/Digital Output Jack" in alsamixer is usually the culprit with Audigy cards - it is usually muted by default.

Open alsamixer and scroll to the right while watching **"Item:"** (toward the top). When you see "**Audigy Analog/Digital Output Jack**", press the "**m**" key to enable it.

---

### Post by gammyhand on 2005-07-06
[QUOTE=jrobcet]The  "Audigy Analog/Digital Output Jack" in alsamixer is usually the culprit with Audigy cards - it is usually muted by default.

Open alsamixer and scroll to the right while watching **"Item:"** (toward the top). When you see "**Audigy Analog/Digital Output Jack**", press the "**m**" key to enable it.[/QUOTE]
 I opened volume control. I then went to preferences and turned on Audigy Analog/Digital Output Jack so I could see that option but as soon as I click it the dialog box disappears but no option appears on the mixer. Reopening the dialog box shows that the option is now supposed to display. Have I got the wrong volume control or something? It says it is the audigy2 (as the selected device).

---

### Post by jrobcet on 2005-07-06
I don't think you can enable it from the volume control. Open a terminal and type in "alsamixer" (without the quotes), and then follow the directions I posted above. With any luck you should then have sound.

---

### Post by gammyhand on 2005-07-06
[QUOTE=jrobcet]I don't think you can enable it from the volume control. Open a terminal and type in "alsamixer" (without the quotes), and then follow the directions I posted above. With any luck you should then have sound.[/QUOTE]
 Thanks, will try that when I get home.

---

### Post by gammyhand on 2005-07-06
[QUOTE=jrobcet]I don't think you can enable it from the volume control. Open a terminal and type in "alsamixer" (without the quotes), and then follow the directions I posted above. With any luck you should then have sound.[/QUOTE]
You are the MAN! That worked fine  :)  :)

---

### Post by poofyhairguy on 2005-07-06
[QUOTE=gammyhand]You are the MAN! That worked fine  :)  :)[/QUOTE]

[https://bugzilla.ubuntu.com/show_bug.cgi?id=6892](https://bugzilla.ubuntu.com/show_bug.cgi?id=6892)

> This has been resolved in Breezy.

So at least this will be the last time.

---

### Post by gammyhand on 2005-07-06
[QUOTE=poofyhairguy][https://bugzilla.ubuntu.com/show_bug.cgi?id=6892](https://bugzilla.ubuntu.com/show_bug.cgi?id=6892)



So at least this will be the last time.[/QUOTE]
 Breezy = new version of ubuntu? I have just put hoary on :( Will I be able to upgrade without reinstalling?

---

### Post by poofyhairguy on 2005-07-06
[QUOTE=gammyhand]Breezy = new version of ubuntu? I have just put hoary on :( Will I be able to upgrade without reinstalling?[/QUOTE]


Breezy is the upcoming version. Its not released yet...and when it is you can easily upgrade.

---

### Post by gammyhand on 2005-07-06
[QUOTE=poofyhairguy]Breezy is the upcoming version. Its not released yet...and when it is you can easily upgrade.[/QUOTE]
 phew lol.

---

### Post by jrobcet on 2005-07-06
Glad it worked for you   :)  

And I'm also glad to see this won't be a problem with Breezy  \\:D/

---

