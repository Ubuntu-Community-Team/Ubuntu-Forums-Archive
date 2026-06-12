---
title: "Unsettling behavior in terminal with tabs"
date: 2007-05-11
forum: Absolute Beginner Talk
---

### Post by BobLand on 2007-05-11
I had to reconfigure my sound card a few times.  When I type in "sudo modprobe snd-" then press the tab key,  the open FF page blinks black, a beep is sounded and I have to hit the tab key again to get the correct prompt.  This is repeatable.

While this is no showstopper, I'd like to know if this is symptomatic of something else.

Thanks,
bobland

---

### Post by Ianman on 2007-05-11
In the terminal the tab key is used to autocomplete file/directory names. Or are you already aware of that?

---

### Post by Rescue9 on 2007-05-11
If I understand the condition correctly, this is normal. The first beep is telling you that there are more than one choice for snd-[SOMETHING HERE]. After pressing tab again, it lists the available choices.

---

### Post by BobLand on 2007-05-11
I'm aware of autocomplete and using the up/down keys to select past commands.  As the behavior is normal for this particular command then every things good!

Thanks,
bobland

---

### Post by BobLand on 2007-05-13
Revisiting this problem.  I was researching why my sound card was not producing output.  A poster suggested I add a new user to see if an .asouncrc file was generated.  I did a little tweaking here and there using a terminal.

Specifically, "sudo modprobe snd-".  In my sessions, the first tab hit will make the browser blink black.  Then I have to hit it again to get the prompt.

With the added user no such thing happened.  The prompt came up instantly with no blinking.  In my sessions, the blinking is becoming more frequent with different commands.

Another thing I noticed was the added user's session was substantially faster then mine.  I have my toolbar loaded with a few items.  The added user had none other then the defaults.

Since this problem seems to be worsening in my world I wouldn't mind some suggestions about fixing this.

Thanks,
Bobland

---

